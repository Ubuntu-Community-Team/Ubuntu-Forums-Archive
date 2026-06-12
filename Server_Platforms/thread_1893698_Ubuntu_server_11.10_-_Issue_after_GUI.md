---
title: "Ubuntu server 11.10 - Issue after GUI"
date: 2011-12-10
forum: Server Platforms
---

### Post by Mr.N00bLaR on 2011-12-10
Its been a while since I have used Ubuntu =( Apparently the last time I was here was 2009 lol..

I just downloaded 11.10 32 server. As far as I can tell it worked correctly. No memory/hdd/disk issues as far as I can tell.

I ran:

sudo apt-get update
sudo apt-get xubuntu-desktop


And now the OS is not loading properly. It says:
mountall: Plymouth command failed

I have not done anything to this computer other than what I have explained here. Can I not run the desktop on a computer this old?

---

### Post by yeats on 2011-12-11
These links may help:

[http://ubuntuforums.org/showthread.php?t=1357117](http://ubuntuforums.org/showthread.php?t=1357117)

[http://ubuntu.igameilive.com/2010/07/how-to-fix-plymouth-command-failed.html](http://ubuntu.igameilive.com/2010/07/how-to-fix-plymouth-command-failed.html)

---

### Post by Mr.N00bLaR on 2011-12-11
I see.. Does this happen to everyone that runs the commands I did? Can I grab the desktop and specify a different driver or something? If I reinstall and I run the commands that I have listed above but try to remove the nvidia drivers before the first reboot, will that work?

---

### Post by arrrghhh on 2011-12-11
> **Mr.N00bLaR said:**
> I see.. Does this happen to everyone that runs the commands I did? Can I grab the desktop and specify a different driver or something? If I reinstall and I run the commands that I have listed above but try to remove the nvidia drivers before the first reboot, will that work?

No offense, but why are you installing Ubuntu Server, and then installing xubuntu-desktop meta package?  Just install Xubuntu, and if you want to save resources occasionally stop XFCE/xDM when you're not using it...

If you want Ubuntu Server, you don't want a GUI ;).

---

### Post by Mia1990 on 2011-12-11
Are you using this for a desktop or server?OK for the desktop install [lubuntu]("http://lubuntu.net/") and if this is a server it shouldn't have a desktop to start with.I have used Ubuntu server for a few year's now and it works nice with only 512 mb of ram on a p4 box.

---

### Post by Mr.N00bLaR on 2011-12-11
I wanted to use this old dell for a file server and maybe a print server. Maybe more but nothing that I can think of now. Maybe I should just install the desktop edition..lol.

---

### Post by arrrghhh on 2011-12-11
> **Mr.N00bLaR said:**
> I wanted to use this old dell for a file server and maybe a print server. Maybe more but nothing that I can think of now. Maybe I should just install the desktop edition..lol.

You don't need a GUI for file/print server.  Webmin helps with the samba (or NFS but I find that config much easier) configuration... a GUI is just unnecessary overhead ;).

---

### Post by Mr.N00bLaR on 2011-12-11
Oh, I didn't know you could use that without the gui, lol.

---

### Post by arrrghhh on 2011-12-11
> **Mr.N00bLaR said:**
> Oh, I didn't know you could use that without the gui, lol.

You can do pretty much anything.  Even browse the web, if you're crazy...

But for a server that just runs services like web server, torrent server, media server, file server, etc etc there's no reason to have a GUI.  I setup my server and don't really interact with it much except the occasional update and tweak if I find something that's awkward, maybe check disk utilization every now and then ;).

---

### Post by Nick_NS on 2012-02-11
I am trying to do the same thing with my server and am running into the same obstacle. Basically my reasoning behind the decision is that I don't do well with the CLI beyond the basics. 99.9% of the time I want the server to run headless without a GUI. But for those times when I have to go and fix things I prefer it. I'd like to be able to just start the xserver when I want to use it and other than that rely on the basic headless server install.

---

### Post by arrrghhh on 2012-02-11
> **Nick_NS said:**
> I am trying to do the same thing with my server and am running into the same obstacle. Basically my reasoning behind the decision is that I don't do well with the CLI beyond the basics. 99.9% of the time I want the server to run headless without a GUI. But for those times when I have to go and fix things I prefer it. I'd like to be able to just start the xserver when I want to use it and other than that rely on the basic headless server install.

So install Ubuntu Desktop and kill X/gdm when you're not using it.

Honestly, I would recommend trying to learn the CLI.  It will be a lot better in the end.

---

### Post by starz677 on 2012-05-31
> **arrrghhh said:**
> So install Ubuntu Desktop and kill X/gdm when you're not using it.

Honestly, I would recommend trying to learn the CLI.  It will be a lot better in the end.

Someone in this thread said something to the effect that they don't really look at their server that often.

 How can anyone say they dont like to mess with their server that often? How does this make for a secure server?   People don't stop trying to breach your server just because you're not paying attention :confused:

Shouldn't you be constantly vigilant and checking logs and other tools for signs of intrusion attempts?

---

### Post by arrrghhh on 2012-05-31
> **starz677 said:**
> Someone in this thread said something to the effect that they don't really look at their server that often.

 How can anyone say they dont like to mess with their server that often? How does this make for a secure server?   People don't stop trying to breach your server just because you're not paying attention :confused:

Shouldn't you be constantly vigilant and checking logs and other tools for signs of intrusion attempts?

Why did you quote my post?  :confused:

I don't see what your comment has to do with mine, at all, whatsoever.

With that said, there's a lot of automated tools that help with security - but if you truly want to be sure, checking up on it and being generally vigilant is the only way...

---

