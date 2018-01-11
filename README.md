# github入门

git,代码管理

---

###1.在Windows上安装Git

msysgit是Windows版的Git，从https://git-for-windows.github.io下载（网速慢的同学请移步国内镜像），然后按默认选项安装即可。
安装完成后，在开始菜单里找到“Git”->“Git Bash”，蹦出一个类似命令行窗口的东西，就说明Git安装成功！
安装完成后，还需要最后一步设置，在命令行输入：

    $ git config --global user.name "Your Name"$ git config --global user.email "email@example.com"
 
 因为Git是分布式版本控制系统，所以，每个机器都必须自报家门：你的名字和Email地址。你也许会担心，如果有人故意冒充别人怎么办？这个不必担心，首先我们相信大家都是善良无知的群众，其次，真的有冒充的也是有办法可查的。

注意git config命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。

###2.创建版本库

初始化一个Git仓库，使用git init命令。
添加文件到Git仓库，分两步：

	* 第一步，使用命令git add <file>，注意，可反复多次使用，添加多个文件；
	* 第二步，使用命令git commit，完成。
###3.时光机穿梭

	* 要随时掌握工作区的状态，使用git status命令。
    * 如果git status告诉你有文件被修改过，用git diff可以查看修改内容。
	* HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id。
	* 穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。
	* 要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。

###4.总结
场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。
场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD file，就回到了场景1，第二步按场景1操作。
场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。
###5.将本地项目上传至github步骤：
1. git init //初始化仓库

2. git add .(文件name) //添加文件到本地仓库

3. git commit -m "first commit" //添加文件描述信息

4. git remote add origin + 远程仓库地址 //链接远程仓库，创建主分支

5. git push -u origin master //把本地仓库的文件推送到远程仓库(-u 第一次推送master分支的所有内容；此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改；)