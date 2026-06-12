---
title: "WHere do I start?"
date: 2008-11-04
forum: Server Platforms
---

### Post by andLowe on 2008-11-04
Approached a help forum looking for a guide on how to set up a home network server (or just the network). The first line of the help uses three words that I don't understand:
"Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome,"

Where do I start, in order to gain the baseline knowledge necessary to read the help forum posts?

---

### Post by cdenley on 2008-11-04
If you want to learn the basics of ubuntu, a good place to start would probably be [https://help.ubuntu.com/](https://help.ubuntu.com/). There is also a "help center" if you click the question mark in the top menu bar.

If you want to get a more detailed explaination about a guide posted on a forum, maybe you could ask your questions on that thread.

I didn't know what wicd was until I googled it. It looks like just another network manager. I wouldn't recommend installing third party software. Stick with the official, trusted ubuntu repository.

All the software in ubuntu is organized into packages. Every file on your system came from a package. When you add software, the packages are usually downloaded from a repository. For the official ubuntu repository which is already configured, packages are authenticated to ensure they haven't been altered since the package maintainer signed it. Packages often rely on other packages in order to function properly. This is called a dependency. When you use a package manager, dependencies are resolved automatically.

There are many different desktop interfaces which can be run on Linux. The most common and the default for ubuntu is gnome. Other ubuntu varieties (kubuntu, xubuntu) will use a different desktop interface, so the package manager would be opened in a different way.

What kind of server are you trying to setup? There are all kinds.

---

### Post by andLowe on 2008-11-04
Thanks for the reply. I have been a Win user for many years, but, not a programmer.
I am trying to set up a HomerUser OS Server from PC User Mag based on Xubuntu.
I think that my lack of knowledge is so wide that I really need a book or a course from which I can learn the basics.
With HELP files and reference lists you still need to know what questions to ask.
I do know my way around a computer but the Ubuntu terminology defeats me.

---

### Post by cariboo on 2008-11-05
You don't have to stick with Ubuntu tutorials to set up a home network. Almost all Linux distributions are set up the same way. I wuold suggest looking here:

[http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)

This is for an older version of Ubuntu, but it is still valid.

I don't know where everybody gets the idea you have to be a programmer to setup a server, but if it was my server I know from experience not let a programmer anywhere near it. :)

One warning, the sever does not install a gui. If you need a gui, then I would suggest installing the desktop version and then using Synaptic Package Manager to  install the server packages you need. To do this, go to System-->Administration-->Synaptic Package Manager-->Edit-->Mark Packages by Task, and select the services you want to install.

Jim

---

### Post by mike010 on 2008-11-06
here is a tutorial that explains how to turn an old PC into a simple home file server.

[http://www.rootprompt.org/article.php3?article=11489](http://www.rootprompt.org/article.php3?article=11489)

"friends don't let friends use windows"

---

