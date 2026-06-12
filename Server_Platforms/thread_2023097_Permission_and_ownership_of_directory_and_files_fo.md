---
title: "Permission and ownership of directory and files for server"
date: 2012-07-12
forum: Server Platforms
---

### Post by leegold on 2012-07-12
Hi,

I've installed and been using Ubuntu Server 10.04 on my home LAN, and have not be too worried about security configuration because it's at home behind a router with a NAT firewall and no open ports set in the router.

But now I'd like to get help with the thing I found hardest to figure out - proper dir and file permissions/ownership for /var/www/ and beyond. I have just made things "work" but haven't paid attentions to this. 

Ubuntu Server 10.04 LTS
Web Server: lighttpd, the user for it is www-data
PHP Version 5.3.2
It's a video and audio server that serves .flv and .mp3 files. 


I just wanted to follow part of the /var/www tree and see if any permissions or ownership could be improved. 

Doing ls -l along path "/var/www/uploaded_vids/how_to/Above Ground Pool Install.flv"

drwxr-xr-x  17 root root   392 2011-06-17 14:19 var

drwxr-xr-x  9 root root   624 2012-06-18 13:55 www

drwxr-xr-x 41 www-data www-data   1184 2011-07-04 13:58 uploaded_vids

drwxr-xr-x 2 root     root     10136 2011-06-19 13:32 how_to

-rwxr-xr-x 1 root root  11805960 2011-06-19 13:29 Above Ground Pool Install.flv

Is this OK?

Thanks

---

### Post by SeijiSensei on 2012-07-12
One option is to make the entire tree owned by root with "sudo chown -R root:root /var/www".  What really matters is whether the www-data user has read permissions on the files it needs to serve.  To ensure that, follow the chown command with "sudo chmod -R a+r /var/www".

Another, often more convenient approach, is to redefine the default DocumentRoot (if that's what it's called in lighttpd) to point to a directory under your home directory.  Then you could own and manipulate the files directly.  In apache, I'd do this:

1) Create /home/username/web.  Then fix the permissions so www-data can see the directory like this:

```

cd /home
sudo chmod 711 username
cd username
mkdir web
chmod 755 web

```

2) Redefine the DocumentRoot to point to /home/username/web.

The "chmod 711 username" step is required to let www-data see into your home directories.  By default, Ubuntu gives all home directories 700 permissions so only the user can access files within /home/username.

---

