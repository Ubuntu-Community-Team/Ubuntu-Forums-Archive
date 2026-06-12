---
title: "Web Based File Server"
date: 2009-04-04
forum: Server Platforms
---

### Post by Tactical Fart on 2009-04-04
I'm trying to set up a file server that can be accessed through a web browser. I've used a program called HFS on windows and it works wounderfully. Is there an equivalent of this program in ubuntu that I could set up that would allow me to serve files through a web interface? This is mainly so that I can serve files to my ps3, but also for when I build my dedicated media server, my folks will be albe to access it with no problem.

---

### Post by ugm6hr on 2009-04-04
For the dedicated media server, look at freenas.

It has a web-based file manager, although you can only download and delete files (not upload).

It also has FUPPES UPnP media server, as well as CIFS/SMB (and NFS) file sharing.

For serving media to PS3, mediatomb is a good choice (and in the Ubuntu repos).

---

### Post by bigbearomaha on 2009-04-04
Do you plan to have this server accessible over the web or just locally using browser?

---

### Post by Tactical Fart on 2009-04-05
> **bigbearomaha said:**
> Do you plan to have this server accessible over the web or just locally using browser?

I'm only planning to use it for my home network and nothing else. If I can secure the web interface, then I will make it available to the web as well, but it will be used for smaller files, like school assignments or photos. I don't want to get any copy right letters.

---

### Post by Yashiro on 2009-04-05
For a LAN what you are looking for is a UPNP Media Server. This is the normal way to share files with a PS3 correctly. You can add a media server in the XMB like this. 
For this functionality you want stuff like Tversity, Xbmc, Fuppes, FreeNAS and others.

Now, HFS ([http://rejetto.com/hfs/](http://rejetto.com/hfs/))** is not this**. It's just a web server.
So if you want to copy this you are only looking for simple web server software. 

If you really like HFS, just install WINE (Windows 'emulator') and install the HFS windows program on Linux.

---

### Post by bigbearomaha on 2009-04-05
I think pretty highly of ajaXplorer for a web file server.

[http://www.ajaxplorer.info/](http://www.ajaxplorer.info/)

if you have LAMP up and running, just download and unpack in your webroot. ( remember to make the unpacked dir writable before trying to log in. )
I always rename the unpacked dir to AX or something short like that for easier url entry in your browser.

It can also be run in ssl/https environment if you have that setup.

all you do is create and/or select a directory on your hd you want to allow access to. log into admin for the first time ( default is admin/admin.  change that right away)

go into tools and setup your 'repository'  that's what AX calls a directory, you can use the default and be good to go right off the bat or link to the dir you want to use from hard drive.

create a regular user and your off.

very easy to use.

though, there is a 2mb upload limit.

for most regular files, that shouldn't be an issue.

you can also add files to the dir you share anytime you want via your file manager.

AX will find them.

Big Bear

---

### Post by ugm6hr on 2009-04-08
> **Yashiro said:**
> Now, HFS ([http://rejetto.com/hfs/](http://rejetto.com/hfs/))** is not this**. It's just a web server.
So if you want to copy this you are only looking for simple web server software. 

Can HFS stream media to a PS3?  It doesn't look like it can from that website.

@TF:
I still think FreeNAS will achieve what you want with minimal fuss.

---

### Post by HermanAB on 2009-04-08
Hmm, OpenDocMan and Webmin come to mind as relatively simple web based solutions.

---

### Post by Cheesemill on 2009-04-08
+1 for AjaXplorer

Cheesemill

---

### Post by Tactical Fart on 2009-04-08
@ugm6hr
No It can't. The purpose is so that I can transfer stuff to and from various wireless devices through a web browser. Like I said, when I get my ducks in a row and my dedicated server built and running, I'll be able to make the media available to my folks. They're not exactly computer literate. My dad's trying, but my mom learned to program phone numbers into her cell phone last month... the same phone she's had for 3-4 years... (I think the only reason I haven't been kicked out is because I'm like free tech support.)

I looked into freeNAS, but it looks like it doesn't install to HD, plus, uses a web interface for administration, which I've never had a good experience with. 

I want to make a server that I can upload media to, convert it at will, then serve it up with a side of french fries. I got FTP running perfect so that's out of the way. I have handbrake So I can convert (sort of). So far I'm 2 for 3.

I took Yashiro's advice and used wine on HFS. Assuming it works, there is no problem. But when I boot the machine w/o a display, and try to launch it through vnc, it messes up (the connection closes before any error message appear.) But I already started a new thread on that issue, so I don't really expect to resolve it here.

@bigbearomaha, I looked around about installing LAMP, but the easiest way is with Ubuntu Server. This won't work because it won't recognize my network card (strangely, desktop does). I'm gonna try and experiment with different web servers tomorrow. If Ajax works that way I think it does, It might be the answer to my problems.

---

### Post by Cheesemill on 2009-04-08
To install the LAMP server packages on your desktop, type the following into a terminal:
```
sudo apt-get update && sudo apt-get -y install lamp-server^
```

And yes, the ^ is meant to be there.

Cheesemill

---

