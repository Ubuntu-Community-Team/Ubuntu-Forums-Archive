---
title: "question about remote login to ubuntu server"
date: 2008-10-14
forum: Server Platforms
---

### Post by devin0 on 2008-10-14
I would like to be able to remotely connect to my ubuntu server from my windows computer to start and stop programs that are running on it. How would i do this?

---

### Post by tonyh6243 on 2008-10-14
You can download VNC onto your windows computer access it over your LAN with your internal IP address or remotely as long as you know your external IP address and it does not change.

---

### Post by clcollins on 2008-10-14
Install openssh-server ($ aptitude install openssh-server) on your Ubuntu system, and you can connect to it from an SSH client installed on your Windows box.  I use Putty for a Windows SSH client.

[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

This will give you command line access on the machine, if that's what you're looking for.

---

### Post by jamesrfla on 2008-10-14
If you are using Ubuntu Server Edition then you should use openssh-server ```
sudo apt-get install openssh-server
``` Then use putty [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) to SSH into your server using windows.

---

### Post by devin0 on 2008-10-14
I just got it kind of working by installing open ssh and am using putty. I can connect, login and run commands (trying to remotely start or stop ventrilo server from running), but when i close putty on windows ventrillo server is no longer running. Am i doing something wrong?

---

### Post by lazyart on 2008-10-15
When you close the terminal all programs launched from it will close with it.  Add an & at the end of the command:```
ventrillo &
```and the app will live on after the terminal goes away.

(I don't know if that is the actual command to run ventrillo-- it was just an example)

---

### Post by happyhacker on 2008-10-15
Does this just give a command line screen or the full Ubuntu graphical access?

---

### Post by devonps on 2008-10-15
> **cantthinkofanickname said:**
> Does this just give a command line screen or the full Ubuntu graphical access?

I assume you're talking about using Putty, if so then as stated earlier in the thread...

> **clcollins said:**
> Install openssh-server ($ aptitude install openssh-server) on your Ubuntu system, and you can connect to it from an SSH client installed on your Windows box. I use Putty for a Windows SSH client.

[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

This will give you command line access on the machine, if that's what you're looking for.

---

### Post by azazel656 on 2008-10-15
I use RealVNC Free on my windows PC and just enabled remote on my Ubuntu machine. 

It hasfull graphics support etc.

---

### Post by hyper_ch on 2008-10-15
instead of running it as "application &" you could also run it in a screen session. That way, with some servers like ventrilo you can easily watch it... detach/reattach session from any computer... have a look here:

[http://jmcpherson.org/screen.html](http://jmcpherson.org/screen.html)

---

### Post by timcredible on 2008-10-15
you're already running xdm on your ubuntu machine, it's similar to rdp (terminal services) on windows, easiest thing is to just use that, then you get the exact same environment as logging in locally.  click on the link in my sig for a how-to on that.

---

### Post by devin0 on 2008-10-15
ok, it's working great now. Thanks for helping me :)

---

