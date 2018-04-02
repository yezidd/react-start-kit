# react-start-kit

## 满足日常react脚手架的使用

#### 使用postcss-loader加载autoprefixer

> 官方已经 不推荐使用插件[webpack.loadOptions.plugin](https://doc.webpack-china.org/plugins/loader-options-plugin/)

> 所以在webpack配置文件中使用了内联方式申明postcss配置文件信息

```
    {
                loader: "postcss-loader",
                options: {
                  plugins: () => [autoprefixer({browsers: ['last 2 versions']})]
                }
              }
```

> 写在webpack.loadOptions.plugin中声明

```
    new webpack.loadOptionsPlugin({
            options: {
                            postcss: function() {
                                return [require('autoprefixer')];
                            }
                        }
    })
```

#### 关于url-loader和file-loader关系

> file-loader：解决引用路径的问题;

> url-loader：如果图片较多，会发很多http请求，降低页面性能，url-loader将引入的图片编码，生成dataURL；

> url-loader会提供一个limit参数（单位B），小于limit字节的图片会被转为dataURL，大于limit的会使用file-loader进行copy；outputPath是图片分离后的路径；

> !最新版url-loader不自带file-loader需要自行安装