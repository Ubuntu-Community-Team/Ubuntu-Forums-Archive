---
title: "Ubuntu gets me depressed"
date: 2012-06-05
forum: The Cafe
---

### Post by userub on 2012-06-05
I've been using Ubuntu for years and I barely know how to use it.

I just upgraded to 11.10 after something went wrong with something I tried to do on 11.04, and now I'm trying to reinstall things that were lost during the installation.

I don't even know how to install something through the tar.gz file.

I barely know any commands for the Terminal.

I just don't know.

What can Ubuntu do for me? How can I learn these things? There is just too much and I don't know where to start.

---

### Post by DingusFett on 2012-06-05
I've just started learning myself recently. AFAIK most tar.gz files you'd download should have a .deb file in them? Most of the time I've installed things is through the Software Centre or sites have shown me the exact commands to add the PPA and install the program via terminal. Don't get overwhelmed, just start with one thing at a time that you want to do and do some googling or ask here to learn how to do it. It's a learning curve, but if you take it one step at a time it's really not that hard to pick up.

---

### Post by Paqman on 2012-06-05
> **userub said:**
> 
I don't even know how to install something through the tar.gz file.


You shouldn't ever need to do this, and it's about the worst possible way to install software anyway. Don't confuse "difficult" with "important".

> 
I barely know any commands for the Terminal.


You don't necessarily need to know any. Chances are that if you actually needed to use the terminal, you would have picked this up by now.

---

### Post by CharlesA on 2012-06-05
> **Paqman said:**
> You shouldn't ever need to do this, and it's about the worst possible way to install software anyway. Don't confuse "difficult" with "important".

Indeed. Unless you are installing from source or need a program not in the repos, you should stick with Software Center.

> You don't necessarily need to know any. Chances are that if you actually needed to use the terminal, you would have picked this up by now.

+1. I am at the terminal probably 95% of the time, unless I am working on something in BlueFish. ;)

In any case, if you really want to learn how to use a terminal - practice, practice, practice.

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by hakermania on 2012-06-05
Hello userub :)
Welcome to the forums! Stay calm and step-by-step you will learn many things that will help you.

Installing something through a tar.gz file isn't the 'default' way of doing an installation! A tar.gz file contains the source code of the application, this means that it contains all the files needed for a program to be build and result in a single executable file, which you will run so as to launch the application. The tar.gz file also contains important data for the application, information about it etc. In order to install a program through a tar.gz file you will have to compile the code so as to generate the executable(s) and then run some commands so as the files to go the proper directories - nothing impressive.

The 'default' way so as to install programs is to use .deb files. Ubuntu Software Center downloads these files and installs them automatically, but you can find and download .deb files created by users. You can install these files by double clicking on them. Ubuntu Software Center will open them and will let you to install them.

Terminal is your friend, nothing to be afraid of. You can imagine terminal as a file browser that lets you browse through your folders and run programs in them. I will do a brief opening here, so as to whet your appetite!
When you open a terminal by hitting the combination Ctrl+Alt+T you will be in your home directory by default. This is /home/username/, where 'username' is your username, e.g. 'alex'. In the terminal, you will see something like this:
```

alex@MaDpc:~$ 

```
If you type the command
```

pwd

```
you will see in which directory you are currently in:
```

/home/alex

```
The 'ls' command let's you list the files in the directory you are in:
```

lalex@alex-kde:~$ ls
a               Documents  gnome-terminal.desktop  Pictures  spiral     wallch_testing
cachestats.cgi  Downloads  ka9arise                plasma    Templates
Desktop         Dropbox    Music                   Public    Videos

```
while the 'cd' command lets you change directory. For example, if I want to head to the Desktop/ folder and see what files are there, then I will have to do the following:
```

alex@alex-kde:~$ cd Desktop
alex@alex-kde:~/Desktop$ ls
a.jpg         cry   snapshot2.png  Spiral Knights.desktop  Text File
Alex.desktop  cry~  snapshot3.png  Teamspeak.desktop       turnoff.desktop

```
Another useful command is the 'echo' command:
```

alex@alex-kde:~$ echo "To be or not to be?"
To be or not to be?

```
which prints to output everything that comes after the echo command!
You can redirect any output to a file, for example this:
```

alex@alex-kde:~$ echo "To be or not to be?" > shakespeare.txt

```
will print 'To be or not to be?' inside the file shakespeare.txt, which will be created, if it doesn't exist!
The last command that I am going to talk about here, is the 'cat' command.
The 'cat' command let's you see what there is inside a file.
For example, if I do a:
```

alex@alex-kde:~$ cat shakespeare.txt 

```
I will get:
```

To be or not to be?

```
There are many sources online that will help you learn useful things about the terminal! A good link is this: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) , but I guess you will be able to find many many things using google and other search engines. There are infinite commands that can do amazing things! Also, the most exciting thing about Linux (in my opinion) is bash scripting! It let's you do awesome things and you should totally check it out after you learn some basic things about the terminal!

As for the problem you have with your Ubuntu Installation, I suggest doing a fresh install of Ubuntu 12.04 LTS through a USB stick, if you have no files to lose! On the other hand, if you have important files, then you should describe as more what is the exact problem that you faced.

---

### Post by Erik1984 on 2012-06-05
You should not feel bad, you are the reason why Ubuntu once was dubbed 'Linux for human beings': People being able to use Ubuntu for years without knowing how to compile source is a good thing.

---

### Post by snowpine on 2012-06-05
Ask 1 question a week and really focus on practicing what you have learned. At the end of each year you will have 52 new Ubuntu concepts under your belt. :)

I found this site very helpful: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

As mentioned eloquently above, the average Ubuntu user doesn't need to know advanced Linux concepts to surf the web, listen to music, watch videos, play games, edit documents, etc. Do you need to know how to rebuild a transmission in order to drive your car to the market? :)

---

### Post by smellyman on 2012-06-05
what are you installing with tar.gz?   I bet it is in the repos...................

I would say 99% of Ubuntu users never install them.

---

### Post by forrestcupp on 2012-06-05
I've been using Ubuntu since its second release. I hardly ever use the terminal. Why worry about having to use the terminal when you can do most things with a GUI? If you *want* to learn it, that's one thing. But you don't really need it for day to day use.

I also never install things from a tar.gz. Those are just compressed files, like a zip file, that contain other files for installation. Once they are untarred, you usually end up with source code that needs to be compiled. With all the software in Ubuntu's repositories, and all the 3rd party PPAs out there that support Ubuntu, you shouldn't ever have to compile anything, if you don't want. But on the off chance that you run into some obscure program that doesn't have a deb or PPA for Ubuntu, [here is a good HowTo](https://help.ubuntu.com/community/CompilingSoftware) on how to compile software from source code that is compressed into a tar.gz file.

But like I said, you should hardly ever need the terminal or tar.gz files, unless you just want them.

---

### Post by stalkingwolf on 2012-06-05
you can install alien then install your tar balls with it.[http://askubuntu.com/questions/14219/how-to-create-deb-installer-from-tarballs]("http://askubuntu.com/questions/14219/how-to-create-deb-installer-from-tarballs")

---

### Post by userub on 2012-06-05
I lost Jdownloader during the upgrade.

I've tried a reinstallation, but it seems like it needs Java to go through. And Java doesn't seem to be in the Ubuntu Software Center, so I don't know what to do. Java's webste has the tar.gz files, but their instructions don't work.

---

### Post by snowpine on 2012-06-05
> **userub said:**
> I lost Jdownloader during the upgrade.

I've tried a reinstallation, but it seems like it needs Java to go through. And Java doesn't seem to be in the Ubuntu Software Center, so I don't know what to do. Java's webste has the tar.gz files, but their instructions don't work.

First Google hit for "ubuntu java":

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

If you don't search help.ubuntu.com and wiki.ubuntu.com when you have a question, then it's not Ubuntu's fault you're confused. ;)

---

### Post by Paddy Landau on 2012-06-05
Java should be installed by default. Due to new licensing restrictions on Oracle's part, Ubuntu comes with Icedtea, a full and working replacement for Oracle's Java.

Read the [Ubuntu manual]("http://ubuntu-manual.org/"). This one is for 11.10; the 12.04 is still being updated. However, most of it is still valid.

---

### Post by userub on 2012-06-05
I already tried JDE and it didn't make a difference. Jdownloader gave me the same error when I tried to install it. I think it wants JRE, but the instructions don't work.

---

### Post by trivialpackets on 2012-06-05
[http://bikramkawan.com.np/how-to-install-jdownloader-in-ubuntu-12-04/](http://bikramkawan.com.np/how-to-install-jdownloader-in-ubuntu-12-04/)

I would recommend that you go with option 2.  Best of luck!

---

### Post by chamber on 2012-06-05
> **userub said:**
> I already tried JDE and it didn't make a difference. Jdownloader gave me the same error when I tried to install it. I think it wants JRE, but the instructions don't work.

What are the instructions that they gave you?

---

### Post by BarfBag on 2012-06-05
I hate to refer you away from Ubuntu, but what helped me become "Linux literate" was Arch.  You basically have to build your OS from packages of your choice.  I didn't stay with Arch, but it taught me a lot.  I can do anything in Ubuntu now.

---

### Post by forrestcupp on 2012-06-05
If you're using this thread for support, then you should really start new threads, one per problem, in the support areas of the forum. The Cafe is mainly for off topic chit chat, and the post hogs don't get credit for helping you here. :)

---

### Post by wolfen69 on 2012-06-06
> **userub said:**
> I've been using Ubuntu for years and I barely know how to use it.

I just upgraded to 11.10 after something went wrong with something I tried to do on 11.04, and now I'm trying to reinstall things that were lost during the installation.

I don't even know how to install something through the tar.gz file.

I barely know any commands for the Terminal.

I just don't know.

What can Ubuntu do for me? How can I learn these things? There is just too much and I don't know where to start.
That's funny, I feel the same way about windows. Good luck.

---

### Post by c2tarun on 2012-06-06
> **wolfen69 said:**
> that's funny, i feel the same way about windows. Good luck.
 
+1

---

### Post by Gone fishing on 2012-06-06
To use Ubuntu you don't need the terminal - the terminal is handy if something goes wrong as it's easer on the forums to instruct a user to sudo apt-get install xxxx than to explain using the GUI but lots can be done using the GUI.

However, if you want to learn Ubuntu I suggest you give yourself a project - say build a server that does XYZ using Ubuntu. Or if its Linux that  you want to learn pick a distro like Slackware and set it up as you want by the time you've finished the project you will know more much more.

---

### Post by Bandit on 2012-06-06
> **Paqman said:**
> You shouldn't ever need to do this, and it's about the worst possible way to install software anyway. Don't confuse "difficult" with "important".

I wouldnt say its worst way to install anything. Although for the OP and many getting used to linux its not what I would recommend until someone has got used to compiling programs and most importantly handling dependences & the package manager (dpkg in our case). 

I do this frequently and without any issues, but then again I been using Linux for over 13 years.

---

### Post by philinux on 2012-06-06
> **forrestcupp said:**
> If you're using this thread for support, then you should really start **[COLOR="Red"]new threads, one per problem,[/COLOR]** in the support areas of the forum. The Cafe is mainly for off topic chit chat, and the post hogs don't get credit for helping you here. :)

Indeed.

@userub please start a thread in General Help or Absolute beginner forum with an appropriate title and remember one thread per problem

Please see this. [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

Thread closed.

---

