---
title: "How to download stuff gui-less to my server."
date: 2010-04-22
forum: Server Platforms
---

### Post by Extol11 on 2010-04-22
I just installed ubuntu server on a spare pc I have and I plan on hosting forums on it. I don't want to install the gui on it and waste resources as the pc is not all that new. But I don't know how to download things into the pc and store them in folders through the CLI. I just want to know an easy way to at least download webmin into it and I think I can figure out the rest. I know how to install webmin from CLI. Thanks in advanced.

---

### Post by arrrghhh on 2010-04-22
> **Extol11 said:**
> I just installed ubuntu server on a spare pc I have and I plan on hosting forums on it. I don't want to install the gui on it and waste resources as the pc is not all that new. But I don't know how to download things into the pc and store them in folders through the CLI. I just want to know an easy way to at least download webmin into it and I think I can figure out the rest. I know how to install webmin from CLI. Thanks in advanced.

Well if you want to download stuff from the web directly to the server, wget.

I use samba and NFS to communicate with my server otherwise on my LAN.

---

### Post by 1clue on 2010-04-22
Lots of ways to do this.  My favorite is secure copy, scp.

scp <my local file> [email]me@my.host.com[/email]:/remote/directory/file
scp <my local file> [email]me@my.host.com[/email]:file (puts it in my home directory)
scp [email]me@my.host.com[/email]:/remote/dir/file .

---

### Post by Extol11 on 2010-04-22
> **arrrghhh said:**
> Well if you want to download stuff from the web directly to the server, wget.

I use samba and NFS to communicate with my server otherwise on my LAN.

Do I have to know the exact url to do this? I mean, I have to know the exact download link for wget to work, right? And is Samba something to use on a server?

---

### Post by Extol11 on 2010-04-22
> **1clue said:**
> Lots of ways to do this.  My favorite is secure copy, scp.

scp <my local file> [email]me@my.host.com[/email]:/remote/directory/file
scp <my local file> [email]me@my.host.com[/email]:file (puts it in my home directory)
scp [email]me@my.host.com[/email]:/remote/dir/file .

is this for downloading something from the web or to get it from somewhere like a usb and copy it to the hdd? I'm not getting it. And thanks for helping me out.

---

### Post by arrrghhh on 2010-04-22
1clue's solution is a way to get things from one server to another - both of which you control.

My solution (wget) is to download from the internet, but you must know the exact url of what is being downloaded, yes.

Samba is just a way to share files between a server and (typically) a client.  Works well with Windows, NFS works well with Linux but you can use Samba in Linux boxes as well, I just prefer NFS if I'm working with a Linux server and client.

---

### Post by Extol11 on 2010-04-22
> **arrrghhh said:**
> 1clue's solution is a way to get things from one server to another - both of which you control.

My solution (wget) is to download from the internet, but you must know the exact url of what is being downloaded, yes.

Samba is just a way to share files between a server and (typically) a client.  Works well with Windows, NFS works well with Linux but you can use Samba in Linux boxes as well, I just prefer NFS if I'm working with a Linux server and client.

Ok, thanks a lot. I'm going to try it with wget after I'm done with homework. I can just check the url on windows and then run that command in the server. Thanks a hole lot.

Edit: Where does it download the file to by default? And how can I specify a different directory?

---

### Post by beren.olvar on 2010-04-22
If what you want to do is to surf the web and download stuff from it, I would recommend the "links web browser" ([http://links.sourceforge.net](http://links.sourceforge.net)).
It has an option (-g) that (may) allow you to even see the graphical contents of web pages without a GUI (it uses the framebuffer)

---

### Post by Iowan on 2010-04-22
I have "elinks" on my LAMP server. It's an interesting challenge to use...

---

### Post by volkswagner on 2010-04-22
> **Extol11 said:**
> Ok, thanks a lot. I'm going to try it with wget after I'm done with homework. I can just check the url on windows and then run that command in the server. Thanks a hole lot.

Edit: Where does it download the file to by default? And how can I specify a different directory?

wget will download to the current directory.  I just change to the directory I want to download it to.  Chances are I'll be working on the file right after downloading it via wget anyway.

```
cd /path/directory/forFileDownload/
```

```
wget http://prdownloads.sourceforge.net/webadmin/webmin_1.510-2_all.deb
```

You may want to look into ebox.  Ubuntu users have steered clear of Webmin because it can have adverse affects, and it's in the repos.


You can read more about wget.
```
man wget
```

There you will see how to set the --directory-prefix=/path or -P

like

```
wget -P /path/to/download http://prdownloads.sourceforge.net/webadmin/webmin_1.510-2_all.deb
```

---

### Post by pixelact on 2010-04-22
My favorite way to transfer files from a windows pc to a ubuntu server is with core ftp using the ssh protocol. it's like using a gui to the ubuntu server, but without using bash commands for creating dir's and such. And it's free.

---

### Post by Extol11 on 2010-04-22
> **volkswagner said:**
> wget will download to the current directory.  I just change to the directory I want to download it to.  Chances are I'll be working on the file right after downloading it via wget anyway.

```
cd /path/directory/forFileDownload/
```

```
wget http://prdownloads.sourceforge.net/webadmin/webmin_1.510-2_all.deb
```

You may want to look into ebox.  Ubuntu users have steered clear of Webmin because it can have adverse affects, and it's in the repos.


You can read more about wget.
```
man wget
```

There you will see how to set the --directory-prefix=/path or -P

like

```
wget -P /path/to/download http://prdownloads.sourceforge.net/webadmin/webmin_1.510-2_all.deb
```

Ok. I'm giving it a try now. And I didn't know there was webmin in ubuntu's repositories. Since this is just an experiment to get myself used to managing servers more than anything else I'll still go with webmin and find the problems it causes and then decide if I'll keep it or not. I only use webmin for configuring apache and shorewall (if I decide to use it this time). I hope it doesn't have any problem with those two since I like webmin and I'm familiarized with it.

---

### Post by Extol11 on 2010-04-22
> **pixelact said:**
> My favorite way to transfer files from a windows pc to a ubuntu server is with core ftp using the ssh protocol. it's like using a gui to the ubuntu server, but without using bash commands for creating dir's and such. And it's free.

I did it once with an ftp program, but I don't remember which one I used for the server. I don't feel like using it on this server though, I'll keep ftp and SSH closed on this one.


Edit: And thanks to everyone who's helped out so far. I already have webmin up and running and I think I can figure the rest out. This is where the frustration, learning and fun starts.... but hopefully not in that order.

---

### Post by HermanAB on 2010-04-23
Howdy,

You should try the text browsers 'links' and 'lynx'.

---

