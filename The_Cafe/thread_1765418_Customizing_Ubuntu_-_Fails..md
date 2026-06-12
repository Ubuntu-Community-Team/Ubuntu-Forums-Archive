---
title: "Customizing Ubuntu - Fails."
date: 2011-05-23
forum: The Cafe
---

### Post by karimruan on 2011-05-23
Hi, I am working on customizing ubuntu 9.04 to have an ISO that is just the way I like it right after install. I am having a few issues though, using remastersys.

One, I decided to make it my own 'distro' ( I am mostly just doing it for craps and giggles actually'). Just learning a bit of something i know nothing of. My goal was to 1. Modify Gnome (have my favorite theme preinstalled) 2. Modify the ubuntu installer (off of the live cd, basically just to translate the text into my parents language (it isn't available yet) 3. Include all of the software that I use most out of the box.

So for the ubuntu installer, i modified the Glade files in /etc/share/ubiquity/ to change as much as the text as possible. I opened these files as root, without root, i do not have permission to modify the files. I have Gnome the way i like it. So, having installed all my apps, translated the glade Ubiquity files (remember I am trying to use 9.04), i use remastersys to create the iso. 

First I tried to make a distributable ISO. Problems were that my gnome theme was not used by default on the live cd, and the installer was still in english. Using remastersys to backup my ISO works ok. My theme is default on the live CD, but the installer is still in english. 

Anyone have any advice on how to remaster ubuntu 9.04 (i'll even use any version between 9.04 and 10.10) with a customized installer and custom gnome theme?

---

### Post by 3Miro on 2011-05-23
You do know that 9.04 is no longer supported, right? Nothing before 10.04 is supported anymore.

---

### Post by Quadunit404 on 2011-05-23
> **3Miro said:**
> You do know that 9.04 is no longer supported, right? Nothing before 10.04 is supported anymore.

This.

---

### Post by timZZ on 2011-05-23
Besides the point the distribution version isn't supported.

Why wouldn't you just make a backup?

---

### Post by xakepa on 2011-06-09
see how [U-Customizer]("http://u-customizer.sourceforge.net/") will do the job fo you ;)

---

### Post by BrokenKingpin on 2011-06-09
Here is a tutorial that might help you:
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

I think the issue you are having with the dist creation is that you need to copy your users preferences /etc/skel for the LiveCD to use them (covered in the above tutorial).

EDIT:
@xakepa... can you only customize things through the U-Customize GUI? If so it seems very limited. The benefit of remastersys is that you just install and tweak your system how you normally would, then create and ISO from that (allowing endless modifications and customizations).

---

### Post by xakepa on 2011-06-17
it's not limmited at all, the GUI only sets the configuration and the most important things are done by the scripts (which you can modify very easy if something doesn't suits you) :

1. download ubuntu-mini-remix (if you don't have it already) to start from the bare minimal
1. select the iso you want to use
2. edit the sources list, install/remove packages via synaptic
3. install deb packages by selecting them from the hosts filesystem
4. install minimal desktop environment/window manager (gnome, kde, openbox etc.)
5. start terminal which is chroot-ed to the extracted filesystem of the iso
6. start a nested desktop session to modify your distros look in realtime without the need to edit configs
7. set distroname, hostname and live user name 
8. create/import snapshots just in case you messed up something and you don't want to start all over again
9. populate a file with commands commands which can be executed to automate some changes to the distro (very useful when building multiple times or rebuilding)

and more...

PS: i'm working on a new version which will come with a lot of improvements

---

