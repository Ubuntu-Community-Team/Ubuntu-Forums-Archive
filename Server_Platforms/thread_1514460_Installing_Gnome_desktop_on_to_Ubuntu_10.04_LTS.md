---
title: "Installing Gnome desktop on to Ubuntu 10.04 LTS"
date: 2010-06-21
forum: Server Platforms
---

### Post by Warbandit on 2010-06-21
I have a ubuntu server install 10.04 LTS, and I want to install the gnome desktop but I don't know how. Can someone explain to me how to install it?

---

### Post by LockeEx on 2010-06-21
Well, I wouldn't take my own word for it, but I believe it's something along the lines of 

```
sudo apt-get install gnome-desktop-environment
```

I'm not too sure about this though, so I'd wait for a second opinion, if I were you. How much of the Gnome desktop do you want? (i.e. web browsing, document editing, etc?)

---

### Post by mituw16 on 2010-06-21
do you want the entire ubuntu desktop? or just a slimed down version. take a look at this forum link, pretty useful i thought...

[http://www.ubuntugeek.com/3171.html]("http://www.ubuntugeek.com/3171.html")

---

### Post by brettg on 2010-06-21
```
sudo apt-get install ubuntu-desktop
```

---

### Post by ps57 on 2012-06-05
old thread.  But for Ubuntu 12 brettg solution restores the 'new' default (not gnome).  

To get gnome for v12:
sudo apt-get install gnome-session-fallback   

Then logout and select gnome for the session type.  

I found this at ubuntugeek.com  (search classic gnome desktop)

---

### Post by overdrank on 2012-06-05
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

