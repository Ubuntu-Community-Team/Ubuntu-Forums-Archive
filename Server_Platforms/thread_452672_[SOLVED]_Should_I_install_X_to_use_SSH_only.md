---
title: "[SOLVED] Should I install X to use SSH only"
date: 2007-05-23
forum: Server Platforms
---

### Post by victorbrca on 2007-05-23
Hi guys,


  Quick and easy. 

  I have an Ubuntu server that I'm using to SSH home and also as a [Jinzora]("http://www.jinzora.com/") server (which I tell you, is awesome). I'd like to forward X through SSH (I'm not so prominent in CLI), but I do not want to slow down my already slow old computer. I will only access the server remotely.

  What should I do? Is there any way of seeing programs like Nautilus, remotely, without installing X?

  Which install should I use if I decide to install X

```

apt-get install ubuntu-desktop
or
aptitude install x-window-system-core gnome-core
or
apt-get install xserver-xorg-core
```

  Thanks a lot for any input!!!


Vic.

---

### Post by Soybean on 2007-05-23
> **victorbrca said:**
> I have an Ubuntu server that I'm using to SSH home and also as a [Jinzora]("http://www.jinzora.com/") server (which I tell you, is awesome). I'd like to forward X through SSH (I'm not so prominent in CLI), but I do not want to slow down my already slow old computer. I will only access the server remotely.

  What should I do? Is there any way of seeing programs like Nautilus, remotely, without installing X?

If you want to do the type of X forwarding you're describing, where Nautilus is running on the server but its window is showing up on your client system, you'll need X running on the server. I've never done it, though, so I can't answer the second part of your post. ;)

The other thing you could do, though, is make the server's filesystem (or, safer but less flexible, just part of the filesystem) network accessible. You could use NFS for that, or Samba if you want to get at it from Windows. Then you could use the graphical tools on your client system (Nautilus, Windows File Manager, whatever) to do whatever you were trying to do on the server. This way, you don't need X on your server, and you should still be able to do most things.

It should be possible to tunnel NFS or Samba over SSH, too, although it might be a bit trickier to set up.

---

### Post by turinglabs on 2007-05-23
> **victorbrca said:**
> Hi guys,
  What should I do? Is there any way of seeing programs like Nautilus, remotely, without installing X?


Yes, if you are trying to run X apps remotely, you just need the X libraries and apps on the remote box - they'll use your local X server. So rather than installing the full-blown desktop, just install the app you want, it will pull in the libraries it needs to run. For nautilus, it has tons of dependencies, but at least it doesn't require an X server. Just do 'apt-get install nautilus' on the remote server, then ssh to it with the '-X' switch, and run nautilus from the remote shell. It may take a while to pop up, especially over a WAN link, but it will work.  An easy way to test this is just to install something light, like 'xterm' or 'xclock', which have relatively few dependencies, and try running them first.


Doug

---

### Post by victorbrca on 2007-05-23
Hi guys,


  Thanks a lot for the info....  :)



Vic.

---

### Post by victorbrca on 2007-05-30
Sorry to bring this back....  I looked over the options and found that they did not meet my expectations 100%...

  I was wondering if anyone would know by experience if X would really slow down a server with the specs bellow? The server is used as a SSH, sound streaming and backup server....



[IMG]http://wazem.dyndns.org/temp/jinzora-temp.jpg[/IMG]



  I'll take performance over the easiness of X in case it will slow down the server too much....


Thanks a lot,  :)


Vic.

---

### Post by turinglabs on 2007-05-30
Keep in mind that X server/client is backwards, so your server will be running X apps, but not the X server itself. The only noticeable slowdown you will see will be from trying to run X traffic over a WAN, I know from experience that it can be painfully slow. Use something like FreeNX if that is the case, but I would recommend just doing everything from command-line if you are comfortable with it.

---

### Post by victorbrca on 2007-05-30
> **turinglabs said:**
> Keep in mind that X server/client is backwards, so your server will be running X apps, but not the X server itself. The only noticeable slowdown you will see will be from trying to run X traffic over a WAN, I know from experience that it can be painfully slow. Use something like FreeNX if that is the case, but I would recommend just doing everything from command-line if you are comfortable with it.

  Thanks a lot Doug!!! X forwarding will be for LAN use, and only once in a while. I try to use shell as much as I can, but I'm still a noob.....  (BTW, nice site)

  Would anyone know what would the commands be to install X with only the necessary packages to SSH X forward? I found like 3 or 4 different commands to install the full package, and I'm also not sure which one to use...

```
apt-get install x-window-system-core xserver-xorg gnome-desktop-environment
or
apt-get install ubuntu-desktop
or
aptitude install x-window-system-core gnome-core
or
apt-get install xserver-xorg-core 
```


Thanks,


Vic.

---

### Post by macogw on 2007-05-30
To X forward, I don't think you need to have X installed.  You just have the *programs* installed and they'll use the X that's on the computer you're using to ssh from (not the one you ssh into)

---

### Post by victorbrca on 2007-05-31
> **macogw said:**
> To X forward, I don't think you need to have X installed.  You just have the *programs* installed and they'll use the X that's on the computer you're using to ssh from (not the one you ssh into)

  I tried doing that with xclock but it ddn't work...


Vic.

---

### Post by victorbrca on 2007-06-04
Ended up installing vsftpd and restricting access to my LAN only....   


 Vic.

---

### Post by kennythegeek on 2007-06-23
You DON'T need an x server!

I'm basicly doing the same as you (old comp, used for many weird server programs, such as sound server, samba server, nfs server, ssh X forwarding server, http server, ftp server...)

That pc's stats are as follows (Found it, someone threw is out :S):
CPU:
  AMD Athlon XP 2000+, 1,6 GHz

RAM:
  512 MB DDR SDRAM

HDD:
  10 GB ATA

And i run a X Forwarding server for random stuff, i always got it running, no matter if i use x apps or not. i haven't noticed any slowdowns yet, it's the sound server that kills the mem with it's caches...

To run the X Forwarding server do this:
On the server, go into /etc/ssh
```
cd /etc/ssh
```
Edit the sshd_config file
```
sudo nano sshd_config
```
Scroll down to X11Forwarding and uncomment these lines:
```
X11Forwarding yes
X11DisplayOffset 10
```
Then edit the ssh_config file (this should be done BOTH on server and client)
```
sudo nano ssh_config
```
Uncomment these lines (and make sure they are set to yes)
```
ForwardX11 yes
ForwardX11Trusted yes
```
Then restart the ssh server
```
sudo /etc/init.d/ssh restart
```
Now, connect from the client to the server
```
ssh -X user@server
```
And now, last step, run your app! I usually use this for nicer editing, so lets install and run nedit
```
sudo aptitude install nedit; nedit 1>/dev/null 2>/dev/null &
```

Thats that, now nedit should be running! also, you probably noticed the 1>/dev/null 2>/dev/null &, the 1>/dev/null and 2>/dev/null sends all - normally debug - output to /dev/null which is just... yeah a device with the constant value of NULL. The & just means it should run in the background. with thoose set, you can continue using the same shell while running your app, otherwise you'll get alot of gtk+ messages, and this will make it almost impossible to use that shell for anything else...

---

