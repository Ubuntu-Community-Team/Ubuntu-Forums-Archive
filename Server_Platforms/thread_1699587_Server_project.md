---
title: "Server project"
date: 2011-03-03
forum: Server Platforms
---

### Post by steaksauce on 2011-03-03
Okay, so I want to do a "home server" project to play around a little and I have some software questions.

I can get Ubuntu Server Edition, but since I'm going to use an older desktop for the project (old enough to come with XP SP1), should I use this or an older version or something?

Also, do the software packs that show on the software center have programs maximized to run off of a network, or are they the same as the desktop version, and if so, what are some good programs to run off of the network to play around. 

Thanks :)

---

### Post by James78 on 2011-03-04
> **steaksauce said:**
> I can get Ubuntu Server Edition, but since I'm going to use an older desktop for the project (old enough to come with XP SP1), should I use this or an older version or something?
As long as you have 512mb RAM you're good, but the more RAM the better everything is. The Server Edition is not as hard as the Desktop Edition is on a computer, because it's much lighter. I'm running a P4 (~2.6GHz, but overclockable to ~3.01GHz) server with 2GB DDR RAM and it's going good. And my main Desktop is an old Dell with another P4 at 3.4GHz, with 4GB DDR2 RAM, and onboard video. It works perfectly fine. It's not the best computer in the world, but it does work.
> **steaksauce said:**
> Also, do the software packs that show on the software center have  programs maximized to run off of a network, or are they the same as the  desktop version, and if so, what are some good programs to run off of  the network to play around.
Separate question unrelated to the server? If not, remember that the Server Edition is a stripped down version of Desktop Edition optimized for servers, meaning there's no GUI. And if not, I don't fully understand your question here, but I'll try to answer it anyways. The Server Edition packages, and the Desktop Edition packages all come from the same repository, and for that matter the programs on the software center are the same as the ones in the repositories as well.

---

### Post by amauk on 2011-03-04
you can run ubuntu server in 256MB of RAM, but depending on your server's workload, may have performance bottlenecks

For servers, the more RAM the better
Server daemons will use RAM to cache things

Just examples, but a file server will use RAM to cache frequently accessed files and a database server will use RAM to cache frequently run SQL queries
All these caches mean the server does not have to constantly retrieve stuff from disk (which is very slow compared to accessing from RAM)

---

### Post by steaksauce on 2011-03-04
> **James78 said:**
> Separate question unrelated to the server? If not, remember that the Server Edition is a stripped down version of Desktop Edition optimized for servers, meaning there's no GUI. And if not, I don't fully understand your question here, but I'll try to answer it anyways. The Server Edition packages, and the Desktop Edition packages all come from the same repository, and for that matter the programs on the software center are the same as the ones in the repositories as well.

I was referring to the file repositories. So the server edition has not GUI what soever? 
Is it used like the terminal on the desktop edition, and I use it to access files and what not?

---

### Post by James78 on 2011-03-04
Correct. The Server Edition has no GUI. You do everything from the command line. But this allows the server to be the most minimalistic it can with what you have installed, plus, remember that GUI's require more resources/installed packages, so it wastes CPU cycles and RAM. But even if those are not a big problem for you, the biggest problems are the potential security risks having a GUI on a server invokes, and all the packages installed (makes everything more messy).

For this reason, it's completely recommended to learn to be dependent on the command line. Trust me, it's worth it. But if you do need help, there's Webmin/Virtualmin (web interface GUI). If you're not doing anything related to Apache2, or [LAMP]("http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29") (**L**inux-**A**pache-**M**ySQL-**P**HP), then you don't need Virtualmin, however Webmin is still useful. I don't recommend using the one in the repositories, for good reasons.

[http://ubuntuforums.org/showthread.php?t=1197883](http://ubuntuforums.org/showthread.php?t=1197883)

---

### Post by steaksauce on 2011-03-04
Thanks! So my last question is this--
If I wanted to remotely control my server using Vinegrin (sp?) on my laptop to eliminate the need of an extra keyboard, mouse, and monitor, how would I install and configure it on the server?

---

### Post by amauk on 2011-03-04
you typically connect to a server from another machine using SSH

```
ssh username@server-name
```
or```
ssh username@server-ip-address
```

---

### Post by aeiah on 2011-03-04
> **amauk said:**
> you typically connect to a server from another machine using SSH

```
ssh username@server-name
```
or```
ssh username@server-ip-address
```

to elaborate on that, ssh stands for Secure SHell. it'll give you remote access to the servers command line.

i think your next step is deciding what you want your server to do. once your server is set up, you may never interact with it directly on the command line.

for a home server, the most common thing to set up is file sharing, either with NFS (for linux and mac clients) or samba (which works better with windows clients, and also works with linux and mac ones). by clients i mean other machines on your network.

another service that's quite common is bittorrent, so you can leave it running (or schedule it to run only at night etc). you can run deluge, transmission or rtorrent 'headless' (ie, on the server without a monitor) and interact with them via webpage control panels or clients on your desktop/laptop machines.

---

### Post by steaksauce on 2011-03-04
Thanks, I now know what I want to do, and after a bash tutorialI should be able to do it. I'll let you know how it goes (which could be a while before I get around to it :p)

Solved :D

---

