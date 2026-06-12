---
title: "mod-mono and apache2 installation"
date: 2008-05-12
forum: Server Platforms
---

### Post by BillDozer on 2008-05-12
Hi,

I'm trying to get mod-mono to work on my apache2 web server on 8.04 but have had no luck so far.

I followed [this guide]("https://help.ubuntu.com/community/ModMono"), to install mod-mono (2.0 version I would like to use). And after restarting apache the page responds with *503 Service Temporarily Unavailable*. Looking through the error I files I found out that I had to change the following line in **/etc/mono-server2/mono-server2-hosts.conf** from:
```
MonoServerPath default /usr/lib/mono/2.0/mod-mono-server2.exe
```to
```
MonoServerPath default /usr/bin/mono-server2
```
to get it running without errors in /var/logs/apache2/error.log

But after restarting apache, my normal index.html is not served automatically more, I can get it shown by writing the complete path but it does not get served automatically.

When I want to serve an .aspx file, firefox just wants to download it.

Anyone has a clue of how to go from here? This is my first of setting up an apache server, so any help will be greatly appreciated :-)

---

### Post by vhawk on 2008-05-13
Hi,

Have you managed to solve this problem.  I am experiencing the exact same problem i.e. aspx files are not served but wants to download ?

Regards
Vhawk

---

### Post by BillDozer on 2008-05-13
No, not yet. It doesn't look like there are too many that are using this apache mod.

I am a C# developer for a living and it would be nice to have the opportunity to be able to program in it in my Ubuntu environment as well. ;-)

---

### Post by vhawk on 2008-05-13
My exact sentiments.

I want to develop a rather large system to run on linux and using C# will be great.  I can do java but I know C# 100x better.  

I'm currently trying to work out what to do by looking at the OpenSuse VM image on the Mono site. That installation installs a very different version of Apache2 and mono though.  I will let you know if I somehow succeed.

:cool:

---

### Post by vhawk on 2008-05-14
Hi,

Managed to get it working - here is a Doc with the 'how to'.

Enjoy

---

### Post by BillDozer on 2008-05-15
Thanks,

I'll try i tonight...

---

### Post by BillDozer on 2008-05-16
Got it working, :) but not the way I want it. :(

I have created a virtual host for my domain but I only can get mono to work with Virtual paths that are valid for all the virtual hosts. For example the sample is available both on the default apache and for my host system, and this is not the way I want it.

I had created a .webapp file in the /etc/mono-server2 folder, but I think I have forgotten something there. Will try to figure it out over the weekend and will get back to the thread when there is more news.

---

