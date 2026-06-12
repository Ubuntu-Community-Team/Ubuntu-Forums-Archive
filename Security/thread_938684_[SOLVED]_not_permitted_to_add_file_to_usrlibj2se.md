---
title: "[SOLVED] not permitted to add file to usr/lib/j2se"
date: 2008-10-05
forum: Security
---

### Post by abhinav90 on 2008-10-05
I am a linux newbie working on ubuntu 7.10 

I am trying to run a java program on linux but am coming across the following issue. When i try and paste a file in to the usr/lib/j2se/1.4/bin folder where my javac file is, i am not getting permission to do so. I tried changing the permission of this particular folder but a not permitted error is coming in the terminal when i try and use chmod. What should i do as to run my java programs i need to load the file in that folder next to the javac files so that they can be compiled.

Pleas help!

---

### Post by Idefix82 on 2008-10-05
Don't change permission to this folder. Instead, begin all commands that need to change the content of this folder with
```
sudo
```
if they are run in the terminal or
```
gksudo
```
if they are GUI applications. You will then be prompted for your password.
for example to paste a file into the folder you were talking about:
```
sudo cp path_to_file/file /usr/lib/j2se/1.4/bin
```
or to open nautillus and do it from there:
```
gksudo nautilus
```

---

### Post by issih on 2008-10-05
First of all, you do not need to have the *.java files you are compiling in the same folder as the javac compiler.

Ubuntu will almost certainly have put the javac command's location into the system path (i.e. the list of folders searched for a command if it isn't found in the current directory). Therefore you can easily run javac from the directory where your source code files currently are, and the compiler will work perfectly and produce .class files in the same directory as the original .java files.

Even if the command wasn't in the system path, you could run it be prefaceing the commands name with the full path to it regardless of the current working directory, e.g:


```
/lib/j2se/javac
``` 
(assuming thats the right location)

In the same way you could specify the full path to the input java files rather than relying on them being in the current directory, and that will work perfectly too.

You do not need to copy things into /lib/j2se to achieve this.


The reason you can't copy things there is because that directory is owned by root (the superuser or administrator) and you as a normal user do not have rights to change it.

If you really need to change something owned by root you use the sudo command to temporarily acquire super user privileges..

```
sudo cp file1 file2
```

that command will ask for your login password (to check you really mean to use root power) and then copy file1 to file 2 regardless of if the location of file1 is owned by root.

General rule though, don't use sudo unless you know what you are doing, chances are you don't need to.

Hope that helps

---

### Post by abhinav90 on 2008-10-05
hey thanks a lot for the help guys, it worked out.

Just used usr/lib/j2se/javac for my commands.

Another quick question where can i get the ubuntu version for Bluej which is a java ide i generally used when i was on windows??

---

### Post by Idefix82 on 2008-10-05
If you really want to you can download it as a java application, then it will run on any OS.
However, under Linux there are other alternatives like Eclipse, Netbeans or even just Gedit with a couple of plugins. There are lots of other alternatives as well.

I just noticed that there is even a BlueJ plugin for Netbeans which is supposed to make the transition to the more powerful ide smoother for beginners.

---

### Post by issih on 2008-10-05
Assuming you mean this:

[http://www.bluej.org/](http://www.bluej.org/)

then it is a java program, and the system specific bits are just wrapper programs..

[http://www.bluej.org/download/download.html](http://www.bluej.org/download/download.html)

just grab the executable jar file from that site.

Once you have that, change the permissions so that it is executable (just right click on the file to find the options).

the file will then run when you double click on it.

Alternatively just run the command:

```
java -jar filename.jar
```

to run the jar file..obviously filename is the name of the jar file you download :)

Hope that helps.

P.S. do check whether javac is in the system path, as you probably don't need to type the whole /usr/lib/j2se bit...just type java in a terminal and hit tab twice, and you will get a list of all commands starting with java that are found in the path. any of those can be run without needing to specify the location, regardless of your position in the directory tree.

---

### Post by abhinav90 on 2008-10-05
okay thanks that all really helped guys.

One more thing i also loaded LAMP (linux, apache, mysql, php) onto my ubuntu 7.10 to use. Now in the case of lamp all the files loaded by lamp have to be in the /var/www/ folder. Now again i dont have the relevant permissions to copy onto this folder but using the cp command for individual files and even editing these files would become a very tedious job since i manage about a hundred pages on them. What is the best work around for this problem??

---

### Post by Idefix82 on 2008-10-05
Actually, using the cp command is usually the quickest way. But if you want to do it with the GUI then start nautilus with the command
```
gksudo nautilus
```
as I wrote in my first post. Now you will have all the necessary permissions.

---

