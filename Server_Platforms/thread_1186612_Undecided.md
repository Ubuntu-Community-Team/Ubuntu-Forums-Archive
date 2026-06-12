---
title: "Undecided"
date: 2009-06-13
forum: Server Platforms
---

### Post by Grafixx01 on 2009-06-13
Hello all...
 
I'm going to build my first Linux Server with a Dell PowerEdge 1600SC Server I bought off eBay. (1.8ghz [2-processor capable], 1.5gb ram, 2 - 36gb hdds for raid).
 
However, I'm tossed up between Ubuntu or RedHat. I know I should probably post this but I'm trying to get opinions. I already have Ubuntu on my Dell desktop and Mini, but didn't know if RedHat would let it connect or which is actually better.
 
Yes, I'm a noobie at the server side of Linux but have been using Linux for about 9 months.

What are your thoughts?

---

### Post by Vegan on 2009-06-13
The server has no GUI so its all command line. It really is meant for dinosaurs who have used mainframes etc.

The other distro has some corporate features, but Ubuntu has those too.

---

### Post by Grafixx01 on 2009-06-14
Oh. I thought that I read in the Official Ubuntu book (included version 8LTS) that there was a gui that could be installed?

---

### Post by cariboo on 2009-06-14
If you need a gui, you would be better off installing Redhat, as Unbuntu server doesn't have any gui server setup tools. All the configuration files are text files, so all you need is a text editor, nano which is installed by defult, is what I use.

---

### Post by arstanj on 2009-06-15
Installing Ubuntu server is pretty much easy nowadays with all the good info and tutorials over the internet.

One thing you should understand, why admins don't like GUI. If you install GUI(yes you can) you will end up having lots of packages to update and secure. More headache.

CLI(command line interface) has all the commands and it's more safe, coz you'll be managing less stuff.

You can try out CLI based server using VMWare or VirtualBox on your laptop before jumping into real server.

---

### Post by HermanAB on 2009-06-15
It depends on what you need.  The main difference between distributions is the quality of the configuration wizards.  Deep down, they are all the same.

The Ubuntu/Mint/Debian Server edition is meant for a machine that will spend its days doing something unspeakable in a dark corner of a dank data centre, headless, with no keyboard, mouse or screen (or below your desk amongst the dust bunnies). You can install graphical programs on the server without having to run X (run the server in run level 3) and connect to it from another machine and run any graphical X programs using SSH with X forwarding.  If you are learning Linux and time isn't an issue, then this is a good distribution to use.

The Redhat/Centos/Mandriva/Suse/PCLOS distributions have lots of wizards to make configuration a snap.  Using any of these, you can set up a sophisticated corporate server in seconds with a few mouse clicks.  You can also run these in runlevel 3 and manage them remotely over SSH of course.  If you don't have time to waste (if time == money) then these ones are what you have to use.

Hope that helps!

---

