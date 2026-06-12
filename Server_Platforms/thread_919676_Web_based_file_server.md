---
title: "Web based file server"
date: 2008-09-14
forum: Server Platforms
---

### Post by ThaddeusW on 2008-09-14
Hello everyone, 

I am looking to implement a web based file server. I want to be able to share files like a directory browse but I don't want to allow a directory browse. Instead I would like to be able to customize the interface, and also have permissions in place. So anonymous users could access some directories and files but not others. Also the ability for a user to upload files is very important also. I thought about FTP but I want something that is easy for my friends and family to use. Anyone have any ideas?

---

### Post by HermanAB on 2008-09-14
[http://www.rejetto.com/hfs/](http://www.rejetto.com/hfs/)

---

### Post by skunkbad on 2008-09-14
Probably the easiest thing to set up would be simple .htpasswd protected folders that you make for special users.

For instance, if your site is [www.yoursite.com](www.yoursite.com), and you need a place for your grandma to look at files, then make a directory

[www.yoursite.com/grandma/](www.yoursite.com/grandma/)

put a .htpasswd file in it and a corresponding .htaccess file somewhere outside.

When granny goes to her folder, she authenticates, and can browse the folder because you let Apache index the content for her.

---

### Post by ThaddeusW on 2008-09-14
Skunkbad
Good point but that still leaves me with no upload capability. 

HermanAB  	
That is very close to what I need but its Windows only and I already have apache running. 

I have Torrentflux up and running and that gives me the ability to control access and it also gives me the ability to remotely download the torrent when it is finished. That gave me the idea to setup a web based file server so I can have access to my stuff from anywhere with little hassle. Remember X drive? That was pretty darn cool and I want to setup something similar myself. It also must use apache because I don't want to have two different ports for one system.

---

### Post by heavyt on 2009-02-16
> **ThaddeusW said:**
> Skunkbad
Good point but that still leaves me with no upload capability. 

HermanAB  	
That is very close to what I need but its Windows only and I already have apache running. 
....
Yes and no, HFS is for windows but runs very well with Wine or CrossOver  [http://www.rejetto.com/forum/index.php?topic=4469.0](http://www.rejetto.com/forum/index.php?topic=4469.0)

---

### Post by bigbearomaha on 2009-02-16
Take a look at AjaXplorer.  it offers a lot of what you describe.

[http://www.ajaxplorer.info/](http://www.ajaxplorer.info/)

have fun, learn lots,

Big Bear

---

### Post by HermanAB on 2009-02-16
See OpenDocMan: [http://www.opendocman.com/](http://www.opendocman.com/)

Cheers,

Herman

---

### Post by ThaddeusW on 2009-02-17
HermanAB, 

Thank you so much for that link! It looks like it is exactly what I am looking for.

---

### Post by mozkill on 2009-02-18
I agree with HermanAB

> [http://www.rejetto.com/hfs/](http://www.rejetto.com/hfs/)

---

