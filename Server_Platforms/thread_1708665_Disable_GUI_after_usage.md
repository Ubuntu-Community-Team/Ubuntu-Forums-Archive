---
title: "Disable GUI after usage"
date: 2011-03-17
forum: Server Platforms
---

### Post by Tumex on 2011-03-17
Hey there, I hope you're doing great!

So I got myself a VPS with the Ubuntu Server Edition installed on it but since I am not a big fan of SSH, I decided to install ubuntu-desktop on it.

However, I know that ubuntu-desktop is HIGHLY resource intensive and thus a total waste of resources in the end, but I would like to know if there is a way to disable the GUI once we are finished with using it? Of course, I would like to be able to again enable the GUI once I want to get back on it through an NX Client.

Thank you very much for your help and I would like to wish you a wonderful day!

Tumex

---

### Post by stlsaint on 2011-03-17
>  I am not a big fan of SSH 
Pure insanity!! :rolleyes:

Are you looking to install gnome but prevent it from running on startup? Do you want to manually start gnome from cli when you login to server? If the latter than you are probably going to have to login to server, start xorg (startx command, after setting up gnome) but when you want to stop gnome the quickest way would be to kill the gnome process after dropping to a tty. Now im not 100% on any other method but i HIGHLY suggest getting up close and personal with SSH since you run a server. Security features, resrouce management, etc. SSH has alot of capabilites for remote functions.

---

### Post by wongo888 on 2011-03-17
If you want GUI-based admin, then you want [MacOS Server]("http://www.apple.com/ca/macmini/server/") or Windows Server.

Web based admin? You probably want Webmin, Landscape or something else.

By the time you figure out how to do whatever it is you want to do, you could have been learning how to properly manage your system or read halfway through the server docs. I'm not trying to be pedantic when I say your question (or a variant) comes up almost every week on this board. The discomfort you feel when trying to do something the UNIX way is called cognitive dissonance and it is a normal part of learning.

I encourage you to stick with ssh (but MacOS is pretty nice too).

PS. Here is the thread from last week on this topic

[http://ubuntuforums.org/showthread.php?t=1699028](http://ubuntuforums.org/showthread.php?t=1699028)

---

### Post by BkkBonanza on 2011-03-17
Besides there are several ways to do server management over ssh using gui tools. For one, Nautilus works over ssh (using sftp, abeit a bit slow) so you can manage and edit files using that. Webmin gives pretty decent basic server control. PhpMyAdmin is a decent mysql manager and there are gui mysql tools that can operate remotely over an ssh secure tunnel. I'm sure there's more but these come in mind as ones I've regularly used.

The efficient way to run gui tools across the web is to look into X windows and X forwarding built in to ssh that allows you to connect to a remote desktop and do gui stuff.

---

### Post by wolfbuddy on 2011-03-17
Just use Webmin, it's brilliant and uses little resources. I decided to use it while learning the UNIX stuff but I'm keen to keep it on now.

---

### Post by Tumex on 2011-03-17
Haha, thank you very much for your replies guys! Surely I felt lazy at the moment I posted this thread because I've been messing around with SSH in the last few hours and I must say that it's quite the learning experience! ;)

So forgive my newbness and let's bury this thread to the ground!

---

