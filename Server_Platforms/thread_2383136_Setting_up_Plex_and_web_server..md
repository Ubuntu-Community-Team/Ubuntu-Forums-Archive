---
title: "Setting up Plex and web server."
date: 2018-01-21
forum: Server Platforms
---

### Post by shaneee on 2018-01-21
Hello. I currently run a local plex server for myself and family on an old laptop running Mavericks. I've since upgraded my desktop so I'm going to repurpose my old setup for this now. I plan on using Ubuntu 17.10 as the OS. What I want to do though is run the plex server as I currently do and also host a small web server with a dedicated second HDD. Is this possible to do and if so could someone point me in the right direction. 

So it'll be the Desktop install of Ubuntu (not the server version) with Plex installed and Remote Desktop so I can access from my main PC.
A small web server installed on Ubuntu directing the htaccess folder onto a separate HDD.

Thanks.

---

### Post by wildmanne39 on 2018-01-21
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by darkod on 2018-01-21
I would use only LTS versions, not non-LTS like 17.10. By the time you tweak and tune the OS it will be almost out of support because it has only 9 months of support starting from Oct '17 when it was released.

And I would use the server version since that is what you are setting up, a server... Not a desktop.

But the final choise is yours as always...

---

### Post by Singular on 2018-01-21
I have that *exact* setup on my network with some slight mods.

Downloading and installing Plex from their website works just fine.

XRDP install on 17.10 can be a bit complicated - I recommend using the mate desktop as an alternative for xrdp sessions - don't try to do the Ubuntu-Desktop hack, it doesn't work reliably.

You can then configure Plex to use your 2nd drive as the media location through the web interface.

Plex is actually put together very professionally...I don't recall having any issues getting it set up.

---

### Post by shaneee on 2018-01-21
Thanks for the tips guys. I was going for the Desktop version for the GUI rather than SSH. Is there a way to do that on the server version? I've only ever dabbled on Linux.

---

### Post by TheFu on 2018-01-22
+1 for everything Darkod says.

If you can't/won't reinstall the OS every 6 months, stick with LTS systems, period. Being on a supported and patched OS is critical for security. That especially matters for things connecting to the internet, like Plex. Then you have 4 yrs (effectively) to move to a new release.  Newer is the enemy of stable and 17.10 has some issues and huge changes on the GUI side which inexperienced Linux users are best to avoid.  IMHO.

Plex has an idea of "libraries." These are split between Movies, TV, Music, Photos, and Home Videos so that different content metadata processes are run against the content to fill in the metadata.  Each of those "libraries" can have multiple storage locations on 1 or 5,000+ disks.  Just keep the content in separate directories.  Adding multiple directories into "Movies" is fine and doesn't impact how they are displayed/organized in the Plex GUI or in Plex Client applications.  As I add a new 4TB disk to my Plex server, I'll create Mx and TVx directories, then add those to the Movies "library" and the TV "library.  {x} is a number. M1, M2, M3, M4, M5 .... you get the idea.  Each new disk is effectively numbers 1, 2, 3, 4, 5 .... to keep me sane (well, as sane as possible).

As for a web server, placement of file for it is completely up to you. There are multiple techniques to control that.  3 off the top of my head.

1) You could just use a symbolic link from /var/www/html --->  /opt/my/new/directory/storage/for/web/files  if you like. That would mean the apache/nginx/whatever config file doesn't need to be non-standard, since it would still point to the normal places.  Symbolic linking is a basic skill for Linux/Unix people.  It can cross file systems and physical disks.  Hard links cannot.   

2) Or you could just mount a partition from the disk you want directly to /var/www/html.

3) Or you could change the web server root directory to be /opt/my/new/directory/storage/for/web/files and restart the service.

I've used all 3 in my 20+ yrs.  I'm using all 3 today, actually, just on different systems.  

Examples:
1.
```
/var/www$ \ls -lF
total 4
drwxr-xr-x 2 root root 4096 Jan 15 09:08 html
lrwxrwxrwx 1 root root   28 Sep 15 13:04 if.example.com -> /misc/Stuff/InstallFest/html
```

2.
```
$ \df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1       7.1G  3.8G  3.0G  57% /
/dev/vda2       2.3G  1.3G  926M  58% /var/www

```

3.  From an apache conf file in sites-enabled/ . Other config changes are needed too.  
```
005-alaska.conf:        DocumentRoot /export/www/vhosts/alaska.example.com
005-alaska.conf:        <Directory /export/www/vhosts/alaska.example.com/ >
``` This is a read-only NFS mount. Part of my layered security for a web server.  If someone hacks in, I'd rather they not be able to change content without any more effort. ;)
Another example:
```
003-nepal.conf: DocumentRoot /export/www/vhosts/nepal.example.com
```
There are about 20 more of these on that machine. ;)  You get the idea.

nginx can do the same things, but I generally use nginx mainly as a reverse proxy to back end dynamic pages created on different systems.

---

