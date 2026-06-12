---
title: "Basic LAMP Server Tutorials?"
date: 2008-07-10
forum: Server Platforms
---

### Post by z.s.tar.gz on 2008-07-10
Here's where I'm at:

I have a junk computer that I want to pool together with a friend's junk computer and create a very small server. All I want this server to do is host a small website and/or allow me to upload/download files remotely.

However, I have no idea what to do after I would install ubuntu server on it. I know how to install US, and what to install, I just don't know how to use it. I have no idea about how to use apache or what MySQL really is. (something about a database?) I do know a little PHP though, but I never actually used it.

Could someone please point me to a good LAMP tutorial **for ubuntu**?

I can not buy any books at all though, but I may have to put this project off for now if that's what it comes to.

---

### Post by scragar on 2008-07-10
There is no fantasticly good guide to LAMP servers at all as far as I know, but luckily there's not much to it.
**install**
Firstly, the install procedure if you miss the option during the main install:```
sudo apt-get install php5-mysql apache2 mysql-server
``` After that it should be installed and you can test, if you've got a browser handy point it to [http://localhost](http://localhost/) or [http://127.0.0.1](http://127.0.0.1), they are both the same(if you are on the command line and don't have a browser install lynx```
sudo apt-get install lynx
```), you should see a message telling you of the success.

**start and stop**
```
sudo /etc/init.d/apache2 **start**
```
replace **start** with **stop** or **restart** as required.

**Writing files**
You can write files either in [url=http://www.nano-editor.org/docs.php]nano[/
url] or [vim](http://vimdoc.sourceforge.net/) like so:```
sudo **nano** /var/www/**index.php**
```replacing index.php(the file to edit) and nano(editor to use) as required.



Can I ask though, that since you are still learning you use a gui for a while, the command line can be confusing in large amounts(and these tips are all from the command line).

---

### Post by cmileto on 2008-07-11
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Old_Grey_Wolf on 2008-07-11
> **cmileto said:**
> [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

I will give that a try.

Thanks.

---

### Post by z.s.tar.gz on 2008-07-12
cmileto: Thank you a lot.

scragar: For one thing, I'm not a noob when it comes to the command line.
Secondly, and more importantly, I already know how to install the things I need. (as I specified in my first post) I really only need to learn how to ***use*** LAMP. I didn't see anything in you post that answered my question, so why did you post at all?

---

### Post by latna on 2008-07-12
> so why did you post at all?

Come on now that wasn't nice. He was being nice trying to answer your question, and it didn't meet your needs. Big deal. At least he tried. Would you prefer to get no answer at all?

---

### Post by scragar on 2008-07-12
> **z.s.tar.gz said:**
> so why did you post at all?

The only things not covered in almost any PHP guide, tutorial or manual are, as far as I can see, how to start or stop apache, where the www folder is(it's **/var/www/** ) and how to access the root perms you'd need to write to that directory. All of which I answered all though not exactly as well as you required, but I tried.

---

### Post by z.s.tar.gz on 2008-07-14
Alright! Alright! Thanks, I guess. I've just been having a hard time setting up my junk server (hardware), so I guess I was mad.

Anyways, all my stuff is working now, and it is great. Thanks.

---

### Post by gdlx on 2008-07-14
Your response has been helpful to me. I have been struggling with the apache2 configuration for some time. I keep getting an error "cannot resolve hostname gg1". I can't seem to find a correction. Also the tutorial will help me configure for two virtual hosts. I like to build my websites on my desktop and then upload to the ISP. I have not had success in setting up two or more vhosts on my server.
Thanks for pointing me to the LAMP tutorial.

Grady

---

