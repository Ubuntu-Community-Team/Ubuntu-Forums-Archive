---
title: "Hosting more than one website on a server"
date: 2011-12-29
forum: Server Platforms
---

### Post by TFroehlich3 on 2011-12-29
I was wondering how to setup my web server to host multiple websites on one web server?:confused: I currently have my website hosting from my server, I have a few small businesses wanting me to host their websites in an attempt to cut costs, because I am going to host them for free since they are friends of mine. Any help would be awesome! :)

---

### Post by Doug S on 2011-12-29
try this thread: [http://ubuntuforums.org/showthread.php?t=1887649](http://ubuntuforums.org/showthread.php?t=1887649) . In particular, posting #2.

---

### Post by harveyd on 2011-12-30
I find these guides great, select your ubuntu version. Follow the section titled 'Configure Name-based Virtual Hosts'

[http://library.linode.com/lamp-guides](http://library.linode.com/lamp-guides)

---

### Post by Habitual on 2011-12-30
[http://www.server-world.info/en/note?os=Ubuntu_11.04&p=httpd&f=4](http://www.server-world.info/en/note?os=Ubuntu_11.04&p=httpd&f=4)

---

### Post by Lars Noodén on 2011-12-30
You'll probably want to use Apache's [name-based virtual hosts](http://httpd.apache.org/docs/2.3/vhosts/).  That is the best way to manage multiple web sites on the same server.  Apache is set up that way.  Apache2 is more modular and allows substantial amounts of system administration to be delegated.

---

### Post by TFroehlich3 on 2012-01-02
> **harveyd said:**
> I find these guides great, select your ubuntu version. Follow the section titled 'Configure Name-based Virtual Hosts'
 
[http://library.linode.com/lamp-guides](http://library.linode.com/lamp-guides)
 
Very nice! Thank you all for the help! Everyone's posts were great! I will be trying this when I get off of work!

---

