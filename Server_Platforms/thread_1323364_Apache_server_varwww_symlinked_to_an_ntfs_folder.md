---
title: "Apache server /var/www/ symlinked to an ntfs folder"
date: 2009-11-11
forum: Server Platforms
---

### Post by Jcink on 2009-11-11
Hi,

I've been a user of Ubuntu since 7.10 and just completed a fresh install a few days ago of 9.10. I decided to put this in the server section since it basically is a server based problem.

I'm dual booting with 9.10 and Windows and I like to create symlinks to my windows content. I already populated my desktop with symlinks to what I need - everything seems to work fine. I can't get apache working though.

When I create a symlink to my www folder on ntfs, I can't access it anymore from apache. 

> [Wed Nov 11 16:38:29 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www

I don't really know what to do. 

-> FollowSymLinks seems to be enabled in the apache conf - and I tested other symlinks (on my linux fs) and they work fine.

-> Tried messing with permissions, but there isn't much I could do. My normal user 'owns' the symlink I think. The strange thing is that I have no problem clicking on it in gnome and editing/dragging/dropping files into it. 

Apache just can't read it. I have done this since 7.10 so I'm not really sure what changed or what I'm missing here. Any ideas?

Thanks in advance,
jcink

---

### Post by Lars Noodén on 2009-11-12
Change the **Directory** and **DocumentRoot** directives to point to the new location.  If you don't want to do that, then use **Alias**, along with Directory.

[http://httpd.apache.org/docs/2.2/mod/core.html#directory](http://httpd.apache.org/docs/2.2/mod/core.html#directory)
[http://httpd.apache.org/docs/2.2/mod/core.html#documentroot](http://httpd.apache.org/docs/2.2/mod/core.html#documentroot)
[http://httpd.apache.org/docs/2.2/mod/mod_alias.html#alias](http://httpd.apache.org/docs/2.2/mod/mod_alias.html#alias)

NTFS is a very poor file system.  Is there a reason you have to have it instead of JFS or EXT?

---

### Post by Jcink on 2009-11-26
Hi,

I'm really sorry for being so late on getting back to this... I got busy and was unable to do much of anything. 

I'm back and I'm still having this issue though.

Changing the document root didn't help, it also doesn't seem to me like it would matter.

What I did last time was simply delete the current /var/www folder

and /var/www simply became a symbolic link to the folder on my windows partition. I didn't have to touch anything in apache at all before to make it work. This was for all versions prior to 9.10.

I tried adding an alias anyway to /win/ to see if it would work. Apache gives me a similar error.

```
[Thu Nov 26 01:21:53 2009] [error] [client 127.0.0.1] (13)Permission denied: access to /win/ denied
[Thu Nov 26 01:21:59 2009] [error] [client 127.0.0.1] (13)Permission denied: access to /win/ denied
```

It doesn't *have* to be ntfs - but I alternate between systems and have always kept things symlinked like this. If this is really too much trouble to do here now I may try to figure out a way to keep my /www/ content on Linux then, and use the drivers I have to access it from Windows.

If anyone's got any ideas, let me know - thanks.

---

### Post by Vegan on 2009-11-26
I do not suggest NTFS on a Linux machine as the driver is not very stable.

If you need Windows access, use Samba to make the Linux box look like a Windows server where you can make the /var/www a share if you want.

---

