---
title: "Help pick virtualization method?"
date: 2008-04-10
forum: Virtualisation
---

### Post by jd@smokin-barrel.com on 2008-04-10
Hi all,
  I am fairly new to using linux and need some advice to make my home pc a workable solution.  My current windows pc recently had a hd failure and now I have the wife onboard to spend a little cash on getting a new pc.  I want to go linux, but when I tried that before it failed in my household.  She needs the ease of use and ease of support for all the strange files and formats from her school and also doing online classes, etc.  We cant spend days trying to get support under linux for the never ending obscure things she always needs, especially when i work long hours and she is basically pc illiterate.  The 2nd issue is my kids have a bunch of windows based educational apps, games, etc that dont work under wine and i really dont have time to try to make little kid focused apps to work.

What I need from the box:

- Solid OS to keep pc on 24/7 without needing reboots, etc
- Media (music) mass storage and streaming for squeezbox
- easy security (i.e. set something basic so i dont get hacked, but not monkey with accounts and permissions all the time)
- easy support for any formats and apps my wife and kids may need
- easy support for periphs (i.e. my laser jet doesnt have linux drivers)
- remote access via ssh
- a shell would be nice, so i can learn bash, etc


Here is where I am a little lost.  I know i can load windows and load ubuntu using vmware.  I just dont feel like it is very integrated as 1 package.  I.e. having a windows window box with another desktop inside that seems a bit clunky when using.  The mouse/keyboard just feel like they are not 100% integrated as you cant just click in and out of that window without first "engaging" the vm'd box.

I have not tried running windows inside of a linux vm solution, but am very open to it.  Is there a nice solution that will make linux run windows apps virtually but a little more integrated vs a whole new desktop inside a window?  

I do really like andLinux, which allows me to run a full linux distro inside of windows natively (or at least looks natively to end user).  I can launch linux apps just like they were windows apps, no desktop in a box to deal with.  I would just go this route, but there are some things i cant handle with andLinux...i.e. no icmp support.  I am a network engineer and rely on simple shell scripts that rely on icmp support for network troubleshooting, etc.

I hope you guys can help me move forward on a nice solution that will allow me to integrate linux into my household gracefully.

Thanks all,
JD

---

### Post by Fire_Chief on 2008-04-10
You may want to try the WUBI installer for Ubuntu 8.04 when it comes out (currently in Beta but should be released in 2 weeks). Read more [here]("http://www.ubuntu.com/testing/hardy/beta#head-b0182be4e8920f642f70a23d88fbd131301c694c")

---

### Post by piousp on 2008-04-10
You can investigate [Xen]("http://en.wikipedia.org/wiki/Xen"). Its a good virtualization software.

---

### Post by jd@smokin-barrel.com on 2008-04-10
Thanks for the advice.  Xen is best if you want to have VM's that run completely isolated correct?  I.e. just like having 2 diff computers?  This may be an option, but I would really rather have tight integration into 1 pc/desktop.  I looked at the wubi, but it appears to be for the purpose of testing the ubuntu system out and seen some comments that it runs pretty slow, etc and not really meant for long term use.   

Hmmm...I guess its not an easy straightforward deal.  

Thanks so far,
JD

---

### Post by piousp on 2008-04-10
Indeed.

Maybe you are reffering to something as an API for windows apps.... yes, thats right: [Wine]("http://winehq.org/").

Wine is a Windows API to run windows apps "natively" under linux. No desktops, no "startmenus", no nothing.
There is a problem with wine right now. It does not run 100% all of windows apps.

You can try [CrossOver]("http://www.codeweavers.com/") or [Cedega]("http://www.transgaming.com/") too.
Finally, maybe you can take a good look to [ReactOS]("www.reactos.org"). Its a linux distro which intends to be compatible with windows at binary level.

As far as i understand your situation, you dont need/want a virtual machine, just a way to run windows apps from linux. If thats really the case, wine, crossover or cedega are the way. ReactOS may be good also.

---

### Post by jd@smokin-barrel.com on 2008-04-10
Thanks, that makes sense.  Is it possible to have simple icons for things sit on a desktop, so my wife and kids just click the icon to launch their app?  I tried wine for something a long time ago and i remember having to launch the app via cli. 

Thanks again, this is very helpful to me.

-JD

---

### Post by piousp on 2008-04-10
Well, now-a-days, wine makes a "menu entry" -in gnome or kde at least-
Personally, i dont like desktop icons, so i dont know how to make them. Maybe you can try another post, or search the forum:
"How to make desktop icons" or something like that.

---

