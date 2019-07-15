---
sidebarDepth: 2
---

# Linux

Linux作为目前主流的服务器操作系统具有诸多优势，贯彻一切皆文件的哲学。无论是生态(指为服务端开发的软件生态)，安全性，稳定性，兼容性都要比Windows更加优秀。唯一的缺点大概就是缺少人性化的交互以及好看的GUI(图形用户界面)，所有大部分开发者都会选择Mac进行开发，同时兼具好看的GUI，以及强大的shell。

## 常用命令

熟练使用Linux的第一步便是熟练它的常用命令，大部分Linux的系统是没有GUI的，我们只能够通过命令来操控系统。对于前端开发来说，我们无需掌握大部分的高难度命令，只需掌握工作开发中常用的命令即可。

### 文件相关命令

熟练使用Linux下的复制 移动命令可以帮助我们写一些小的自动化shell脚本。例如在前端构建完毕后，将构建产物移动到指定目录或者重命名

```
$ cp ./a.txt ../b.txt // 将当前目录下的a.txt文件复制到上级目录并更名
$ mv ./a.txt ../b.txt // 将当前目录下的a.txt文件移动到上级目录并更名
$ mv ./a.txt ./b.txt // 重命名当前目录下的a.txt文件
```

### find

使用`find`命令可以帮助我们查找符合要求的文件

```
$ find ./ -iname "*.js" // 查找当前目录下的所有js文件, 忽略大小写
$ find ./ -size +25k  // 查找当前目录下文件大小大于25kb的文件
```

### grep

使用`grep`命令可以帮助我们筛选符合要求的内容

```
$ grep "browserRouter" -i ./src/entry.tsx // 在当前src目录下的entry.tsx文件中查找browserRouter关键字忽略大小写
```

### awk 

通过awk命令我们可以筛选出符合要求的行或者列数据

```
$ cat /etc/passwd |awk -F ':' '{print $1}'  // 以:为分隔符，将passwork分为多列，并且提取出第一列的内容
```

### 进程相关命令

```
$ lsof -i:8000 // 查看端口占用情况
$ ps // 查看当前正在运行的进程，ps命令选项众多这里不一一介绍
$ kill -9 pid // 根据进程pid来将进程强制退出
```

### 管道符

管道符可以将上一个命令的stdout输出，作为下一个命令的stdin输入。通过管道符我们可以实现一些稍微复杂的自动化的脚本功能

```
$ ps | grep -i "node" | awk '{print $2}' | xargs kill -9 // 查找当前正在运行的Node进程并提取出pid传给kill命令来退出进程
```