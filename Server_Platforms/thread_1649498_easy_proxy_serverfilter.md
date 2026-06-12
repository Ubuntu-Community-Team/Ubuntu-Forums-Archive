---
title: "easy proxy server/filter"
date: 2010-12-20
forum: Server Platforms
---

### Post by lykwydchykyn on 2010-12-20
I have a scenario at work where someone wants a proxy server set up to block employees from certain web sites, probably in the end it will be more of a whitelist situation (all but a few things blocked).  I've been asked to configure one of my Debian servers to do this, so I'm trying to figure out the best approach.

I've got squid running on the system, but I want it to be easy for my coworkers (read non-Linux admins) to make changes to the system.  Squid's a bit esoteric for this.  I've checked out the webmin interface, but it only marginally makes things understandable.

What I need is something with a web interface that will make blocking or unblocking web sites relatively simple.  Anyone have a suggestion.

ps - it's got to run on Debian, these servers do other things as well.

---

### Post by BbUiDgZ on 2010-12-20
its a shame you don't have a dedicated machine for this [http://www.advproxy.net/](http://www.advproxy.net/) 


have you tried the webmin interface for squid?
[http://www.webmin.com/screens/squid.html](http://www.webmin.com/screens/squid.html)

---

### Post by lykwydchykyn on 2010-12-20
> **BbUiDgZ said:**
> its a shame you don't have a dedicated machine for this [http://www.advproxy.net/](http://www.advproxy.net/) 


have you tried the webmin interface for squid?
[http://www.webmin.com/screens/squid.html](http://www.webmin.com/screens/squid.html)

It's at a remote location, the fewer hunks of iron we have running out there the better.  

The webmin interface for squid isn't workable for us, really.  It's too low-level for what we want to do.

I've installed Dansguardian and downloaded a blacklist, and I can do what I need with that.  I just wish there were a better web-based admin for Dansguardian.  I've tried the webmin module for it off sourceforge but it just seems clunky and broken (to be fair, it's beta).

---

### Post by elico on 2010-12-20
well i think you should consider another approach.
in a way as i remember you can build some text file or mysql database that will store the whitelist\blacklist so you realy dont need anything else then basic understanding of how to write text files with some basic domain naming understanding and maybe an ftp\samba share to update the text file.

for what do you need web-based admin if text is the best thing?(as long as i remember it's quite simple.)

---

### Post by lykwydchykyn on 2010-12-20
Text is fine for me.  It's not for my coworkers, and I don't want to be the only one who can admin this thing. 

If it comes to text files, dansguardian does what we need and it's scalable when the inevitable requests come in for finer-grain control of filtering (so-and-so needs access to blah, can we open it up during lunch, etc).  

I'm just kind of surprised nobody has yet produced a good, general use interface for Dansguardian.  From my searching, there are a few specialty distributions that ship with custom interfaces, a few failed attempts to build an interface that now either don't work or aren't available, and one half-baked webmin module that seems to muddle the issue more than anything else.

---

### Post by BbUiDgZ on 2010-12-20
> **lykwydchykyn said:**
>  
The webmin interface for squid isn't workable for us, really.  It's too low-level for what we want to do.

yeah and i should really read full posts before i reply

---

### Post by elico on 2010-12-21
so with a text file you can definitely get what you want...
you just have to figure it out somehow by yourself cause i dont have much time to touch it now.
with dash guardian it's one of the most basic stuff you can do.
you may get into some scripting but not something that unbreakable by couple of minutes on dash guardian settings files.

---

### Post by lykwydchykyn on 2010-12-22
> **elico said:**
> so with a text file you can definitely get what you want...
you just have to figure it out somehow by yourself cause i dont have much time to touch it now.
with dash guardian it's one of the most basic stuff you can do.
you may get into some scripting but not something that unbreakable by couple of minutes on dash guardian settings files.

I have no idea what you're trying to communicate, but thanks for your desire to help.

Like I said, I don't have any problems working with config files, the command line, scripting, etc.  I'm the Linux geek of my organization. 

What I'm trying to set up is a system my coworkers can feel good about and be able to administrate easily.  They aren't sold on the CLI/config file/scripting thing.  They want a GUI.  They want clickety-clickety-click-Done.  I am hoping against hope for a solution of that nature that I can install on Debian.

For now I'm going with DG.

---

