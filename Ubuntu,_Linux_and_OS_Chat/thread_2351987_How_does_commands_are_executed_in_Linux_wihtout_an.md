---
title: "How does commands are executed in Linux wihtout any prefix or other command?"
date: 2017-02-08
forum: Ubuntu, Linux and OS Chat
---

### Post by mishraprashant1811998 on 2017-02-08
In linux everything is in the form of a file. So if you want to do anything you need to have a reference of the file where you want to perform a task
Like in shell scripting if you want to execute a script you need to write 'sh myscript.sh' or './myscript'
I am not sure but I think there must be some script or code written for each and every command in linux 
So if you want to run a command like "mkdir" you can directly write and execute without the reference of the directory or without a prefix cammand like 'sh' in shell script
So can anyone please tell me how this actually works

---

### Post by deadflowr on 2017-02-08
Good explanation here:
[http://www.linfo.org/path_env_var.html]("http://www.linfo.org/path_env_var.html")

---

### Post by TheFu on 2017-02-08
Welcome to the forums.

PATH environment variable.  Almost every other OS (Windows/OSX/Unix/iOS/Android/ ..... MVS) uses this method too.

There are many books that cover this.  [The Linux Command Line]("http://linuxcommand.org/tlcl.php") is a book which explains this and hundreds of other things about the way Linux really works. Free, no-hassle, download.  There are also beginning Linux/Unix training classes for free at EdX and LinuxFoundation.

And just to clarify ... everything is not "a file", there are "processes" too.  Files and processes - that's the ticket. ;)

---

### Post by ajgreeny on 2017-02-08
Any executable file, binary or shell script, which is sitting in one of the system $PATH directories, will work when the name is typed in terminal; you do not then have to give the full pathway to the executable file.

You can see which are your $PATH directories with command ```
echo $PATH
``` which in Ubuntu family OSs will be
**/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin** 
plus **/home/username/bin** folder in your home if you have created it and have put any executables in that folder.

---

### Post by mishraprashant1811998 on 2017-02-09
Thanks for the help 
Very nice explaination  &#128513;&#128513;
Got the answer of my query

---

