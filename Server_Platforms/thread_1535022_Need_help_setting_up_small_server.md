---
title: "Need help setting up small server"
date: 2010-07-20
forum: Server Platforms
---

### Post by Admiral Yi on 2010-07-20
Hi all,
I need a little help setting up my first web server. Basically I need to be able to download a few files on the server wherever I am over the Internet, and also to view a couple of webcam feeds. I was planning to do this using Apache. I know a stand alone server is probably overkill for this, but I may expand in the future and would also like it as a small project. I've got a few questions:

1) What hardware is best? I was thinking Intel Atom, with a couple of gigs of decent ram, but having no experience with this I don't whether that's not much power or too little or what. 

2) Is Apache the best thing for this? Also, would it be fairly easy to set up for someone with no web server experience but plenty of linux/command line/programming experience?

3) This is a really nooby question, but where can I find a decent tutorial on port forwarding? I understand I'll probably have to forward port 80, and port 21(?) for FTP so I can get files off of it. I've searched and searched, but I can't find anything about setting it up which is written for someone with very little knowledge of this field. 

Help with any of all of these questions is appreciated.

---

### Post by Bachstelze on 2010-07-20
> **Admiral Yi said:**
> 
1) What hardware is best? I was thinking Intel Atom, with a couple of gigs of decent ram, but having no experience with this I don't whether that's not much power or too little or what.

Looks like any hardware will do, even a Pentium 100 with 32M of RAM.  Don't lose too much sleep over the hardware. ;)

> 2) Is Apache the best thing for this? Also, would it be fairly easy to set up for someone with no web server experience but plenty of linux/command line/programming experience?

The default settings are sensible, just

```
sudo apt-get install apache2
```

Then copy your files into /var/www, voilà.

> 3) This is a really nooby question, but where can I find a decent tutorial on port forwarding?

It depends on the model of your router, so the only real answer is here is to RTFM that came in the box. ;) Most have nice step-by-step pictures.

> I understand I'll probably have to forward port 80, and port 21(?) for FTP so I can get files off of it.

FTP is a royal pain to use behind a router, use SFTP instead (it also automatically encrypts traffic, without complicated setup needed).

---

### Post by zorglubx on 2010-07-20
I have just set up my second web server in ubuntu myself, so I am no expert! But to start with your server, I think what you are talking about sounds fine for this. Basically, you do not want a monster machine that uses lots of power.

1 or 2GB ram is more than enough for a little site. But the only thing I can think off that will be hardest to accommodate, is redundancy/raid. If you choose a small form factor pc, with few expansion slots like the atom.

Most likely the best option is to use an external usb drive (or nas/remote share etc.) to make regular backup's on. Then u can run the lot off a 2'5" drive :)

Another even smaller but most like perfect for the job type of pc you could use is one like this: [http://www.linuxshoppen.dk/products.php?showvariant_id=7170](http://www.linuxshoppen.dk/products.php?showvariant_id=7170)

If you install a Lamp server via the server install, you are good on your way to have a running apache server, from there, you should probably use some apache guides. An there should be plenty!

regarding port forwarding, you can probably find some guides on the routers manufacturer website? otherwise, someone else might be able to answer that question better :)

edit: actually just stick an SSD in that tiny pc, and you got a little super pc, using <10 W power.

---

### Post by haydenh on 2010-07-20
> **Admiral Yi said:**
> Hi all,
I need a little help setting up my first web server. Basically I need to be able to download a few files on the server wherever I am over the Internet, and also to view a couple of webcam feeds. I was planning to do this using Apache. I know a stand alone server is probably overkill for this, but I may expand in the future and would also like it as a small project. I've got a few questions:

1) What hardware is best? I was thinking Intel Atom, with a couple of gigs of decent ram, but having no experience with this I don't whether that's not much power or too little or what. 

2) Is Apache the best thing for this? Also, would it be fairly easy to set up for someone with no web server experience but plenty of linux/command line/programming experience?

3) This is a really nooby question, but where can I find a decent tutorial on port forwarding? I understand I'll probably have to forward port 80, and port 21(?) for FTP so I can get files off of it. I've searched and searched, but I can't find anything about setting it up which is written for someone with very little knowledge of this field. 

Help with any of all of these questions is appreciated.


1) I just threw some old parts together and mine seems to be working fine. I will upgrade later.

2) Not sure.

3) [http://portforward.com/](http://portforward.com/) is a pretty good resource. Even though it's ugly, it has a step-by-step guide for pretty much every router.

---

### Post by Admiral Yi on 2010-07-21
Thanks for all the advice guys! I'll mark this solved as that answers all my questions.

---

