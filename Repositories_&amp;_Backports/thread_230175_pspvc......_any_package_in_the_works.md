---
title: "pspvc...... any package in the works?"
date: 2006-08-05
forum: Repositories &amp; Backports
---

### Post by thx_1138 on 2006-08-05
Hello
I was wondering if anyone was working on getting a package for the pspvc program offered by sourceforge
[http://pspvc.sourceforge.net/](http://pspvc.sourceforge.net/)
I never seem to have any luck with installing tarballs, Im not quite a newbie to linux but I can never seem to them to install properly. I was hoping to use this program since Im trying to finally get rid of windows in my computing life and this program sounds like a good replacment for pspvideo9

Thanks in advance to anyone whom may be able to help

---

### Post by JNasci7906 on 2006-10-29
i second that, ive been messin with that tarball for days and cant get any luck....

---

### Post by pacificdrums on 2006-11-30
Me too! I really want to get this program to work but I have no idea how to install it.

---

### Post by thx_1138 on 2006-12-02
Well I have definetely gained some knowledge with linux since this was my first post to the forums and I still havent gotten this program to work... but then again I havent played around with it in almost two monthes. I will load it up again and see if I have any luck and I will try and post anything else I find out, if I have success I will post the step I took to use to intall this program onto my linux boxes. I will be able to test it on dapper (6.06) as well as on edgy (6.10)](*,)

---

### Post by thx_1138 on 2006-12-14
Just wanted to give a quick update, after doing a little more forum searching and installing I managed to get pspvc up and running on my laptop (running 6.10). The most simplistic explanation for the install would be as follows...
:eek: 
I used post #7 from this page in the forums
[http://www.ubuntuforums.org/showthread.php?t=273578](http://www.ubuntuforums.org/showthread.php?t=273578)

Using synaptic you should install
-libgtk2.0dev
-libfaac-dev
-libxvidcore4-dev
-nasm
-build essential

Once that is done open up the pspvc tarball using tar -xvzf or using the gui archive manager and set it in your home folder, I found I had to extract the x264 tarball and run the configure and make files before I ran the install shell script. When I did run it I found I was getting an error about writing so I had to run it using sudo (which I hated doing but I got it working). I found the easiest way to run it was to use the alt-F2 and punch in pspvc to launch it. I have yet to test it to see how it encodes, I will post again once I have had more time to test it out and how it installs on 6.06 (my desktop machine).

---

