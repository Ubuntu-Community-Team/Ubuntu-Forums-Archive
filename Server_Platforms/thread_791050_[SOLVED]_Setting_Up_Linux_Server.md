---
title: "[SOLVED] Setting Up Linux Server"
date: 2008-05-11
forum: Server Platforms
---

### Post by evolving_monkey on 2008-05-11
Hello All,
I want to set up a Linux server but I want to use a GUI. I realize I can use either KDE or Gnome, however, I am not sure if one is better suited for this.

I have been using GNOME for some time now but there are a few items that I would like to try for KDE. I know you can run most KDE apps in GNOME if you load the qt libraries (I just install kde-core) but I have trouble with some crashing. Loading full blown installs of Ubuntu and Kubuntu has never worked out well for me.

So back to my original question. Of the two desktops, is one better suited to use as a GUI for a server. This is pretty much for fun and learning so the extra security concerns of having a GUI on a server aren't an obstacle. I just want something to use as I get more proficient with the command prompt.

Thanks for your time

---

### Post by Dr Small on 2008-05-11
Servers are best off without a GUI, as they only use un-needed resources. You are best off to either go without an interface and manage the server from the command line via SSH, or install a simple window manager such as IceWM, Fluxbox or Openbox.

Server != GUI

Dr Small

---

### Post by evolving_monkey on 2008-05-11
You are absolutely correct. Your proficiency at the command prompt is what I would like to achieve. 

I'm doing this to learn about using Linux/UBUNTU as a server and to master the command prompt. The GUI will help me understand how its done in the Linux world and at the same time learn how to do it from the command prompt. 

This would be at home and all of the normal concerns attached to having the  GUI are a mute point. This is just how I plan to teach myself. For now, it's just for fun.

I do intend to make a virtual machine of the server version of UBUNTU. Something to practice on until I'm good enough put it on a real box.

Thank you.

---

### Post by windependence on 2008-05-12
It wasn't until I forced myself to install a machine without a GUI that I became  really proficient at the command line. I did it because I HAD to do it, and anything I needed help with I googled or used the forums. Of course YMMV.

-Tim

---

### Post by ikt on 2008-05-12
> **evolving_monkey said:**
> So back to my original question. Of the two desktops, is one better suited to use as a GUI for a server. This is pretty much for fun and learning so the extra security concerns of having a GUI on a server aren't an obstacle. I just want something to use as I get more proficient with the command prompt.

Thanks for your time


It doesn't really matter, KDE or Gnome, there are a ton of people out there using ubuntu desktop as a server, and having no problems.


I started on ubuntu desktop, referencing this guide a lot:

[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

Once I got good enough with the command in the desktop version I switched to the server version.

---

### Post by evolving_monkey on 2008-06-14
I decided to install the UBUNTU 7.10 Desktop on my server and I'm really happy with the results. I've been using UBUNTU on my desktops for the last couple of years so it seemed like a logical choice.

I realize that this is not how a true server should be set up but it has been an excellent learning tool. 

Thank you ikt for the site. That and a few others I've found in the threads have helped a great deal.

Also thank you Dr Small. I have looked around an decided to try Webmin. Most of what I need to do on the server can easily be accomplished through Webmin alone. I plan to give IceWM, Fluxbox and Openbox a try also. Ultimately, I still hope to learn how to do everything from the command line.

I was previously using Windows 2000 Server and had been for some time. I definitely prefer UBUNTU by far. The server is now much faster and much more reliable. I've also found some amazing tools in the repositories. Any hesitations I had about switching the server to UBUNTU/Linux are completely gone.

---

### Post by windependence on 2008-06-18
<snip>

Suggestion: Go load Windoze back on all your machines and then you will be happy again. Make sure to pay the Micro$haft tax while you are at it.


Linux losing ground on servers? What planet are YOU on? By the way, it's losing not loosing.

-Tim

---

### Post by FAO56 on 2008-06-18
> **windependence said:**
> <snip>

Suggestion: Go load Windoze back on all your machines and then you will be happy again. Make sure to pay the Micro$haft tax while you are at it.


Linux losing ground on servers? What planet are YOU on? By the way, it's losing not loosing.

-Tim

Do you see what I am talking?

---

### Post by FAO56 on 2008-06-18
> **windependence said:**
> <snip>

Suggestion: Go load Windoze back on all your machines and then you will be happy again. Make sure to pay the Micro$haft tax while you are at it.


Linux losing ground on servers? What planet are YOU on? By the way, it's losing not loosing.

-Tim

Your are missing the point. I am not talking about Windows. I am talking about a GUI in Linux Server. And I am not talking about grammar of a language that is not my first one. Your comment only proof my point.

---

