---
title: "How to get a desktop on Ubuntu 10.10"
date: 2011-06-28
forum: Server Platforms
---

### Post by cowboyup6983 on 2011-06-28
Hello,

I ordered a VPS service with a Ubuntu 10.10 template. My host PC is Windows 7 and I am looking to get a GUI for running Firefox. 

I'm reading online about using VNC on my server. I don't know what to do.

I use Putty to connect to my server but it's all terminal based. Are there some simple steps to get a desktop so I can view from my host. I only for now need to run Firefox. 


Thanks and please forgive me if I sound stupid.

---

### Post by cowboyup6983 on 2011-06-28
Here's all I have accessed.


[CENTER][IMG]http://img40.imageshack.us/img40/2898/captureben.png[/IMG][/CENTER]

---

### Post by bettaproger on 2011-06-28
on you wanting to run firefox on the machine localy? if so

sudo apt-get install ubuntu-desktop

you can set up vnc if you wish to see the desktop remote, or just use it localy

---

### Post by collisionystm on 2011-06-28
you don't need firefox on your server ;p just use the web browser on your computer!

If you want to download a file to your server, use wget

wget [http://website/file.zip](http://website/file.zip)

You can also enable ftp to send files directly from your computer to it.

---

