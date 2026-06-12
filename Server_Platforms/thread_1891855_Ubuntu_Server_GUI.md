---
title: "Ubuntu Server GUI"
date: 2011-12-06
forum: Server Platforms
---

### Post by collisionystm on 2011-12-06
FYI

[http://ubuntuservergui.com/](http://ubuntuservergui.com/)

---

### Post by bluexrider on 2011-12-06
Thanks

I was using WEBMIN

> **collisionystm said:**
> FYI

[http://ubuntuservergui.com/](http://ubuntuservergui.com/)

---

### Post by samosamo on 2011-12-06
It could work, if done right

---

### Post by lykwydchykyn on 2011-12-06
The link doesn't work for me.

---

### Post by arrrghhh on 2011-12-06
> **collisionystm said:**
> FYI

[http://ubuntuservergui.com/](http://ubuntuservergui.com/)

I guess I don't get the point.  Is it not ready yet or something?

I'd like to check it out, Webmin works well for me.

---

### Post by Mia1990 on 2011-12-07
Ubuntu server really doesn't need a gui but if you need a gui to administrator the server with [ISPConfig]("http://www.ispconfig.org/") is a great tool for doing that.or do a Google search and if you need a full desktop then just install gnome 3 or unity or any of the desktops out there.

---

### Post by arrrghhh on 2011-12-07
> **Mia1990 said:**
> Ubuntu server really doesn't need a gui but if you need a gui to administrator the server with [ISPConfig]("http://www.ispconfig.org/") is a great tool for doing that.or do a Google search and if you need a full desktop then just install gnome 3 or unity or any of the desktops out there.

Yea, for the most part I agree.  Some things are quite difficult to setup without a GUI (but 99.9% of the time possible) and I definitely prefer not running one.  Forwarding X apps over ssh makes up the .01% needed to fill the gaps.

---

### Post by andrea000 on 2011-12-07
+1 A Ubuntu Server does not need a gui.All you are going to do is set it up and then put the Server back somewhere out of the way.webmin is good for Administrating the Server if need.This can be done using openssh-server and webmin for remote access.No gui needed.

---

### Post by HugoSerrano on 2011-12-07
> **andrea000 said:**
> +1 A Ubuntu Server does not need a gui.All you are going to do is set it up and then put the Server back somewhere out of the way.webmin is good for Administrating the Server if need.This can be done using openssh-server and webmin for remote access.No gui needed.


+1

With gui, that do the job for you, you won't gonna be able to solve problems, because you don't know how stuff it's done. 
With gui's comes more packages, more possible failures, bugs, etc. 
A perfect server will only have the minimum services available. Always avoid gui's. 

:-) Best Regards!

---

### Post by zeljkojagust on 2011-12-07
Absolutely agree with Hugo! There is no need for anything else on the server but what that server is serving. And especially not GUI.

---

### Post by Morbius1 on 2011-12-07
It's not that I disagree with the position of not requiring a desktop environment and I suppose it depends on what your machine is "serving" but even with a DE you don't have to login and use it.

If I have a Samba file server running on a machine with a DE all I have to do is boot the machine ( and not login ) to have the shares available to the LAN.

---

### Post by volkswagner on 2011-12-07
Has anyone confirmed what this actually is?

From the minimal screenshot-like images, it appears to resemble a web based solution.  It may be a webmin alternative.

Whatever it is, it's getting attention in this thread, without even existing yet.

---

### Post by haqking on 2011-12-07
> **volkswagner said:**
> Has anyone confirmed what this actually is?

From the minimal screenshot-like images, it appears to resemble a web based solution.  It may be a webmin alternative.

Whatever it is, it's getting attention in this thread, without even existing yet.

[http://ubuntuservergui.com/announcements/welcome#comments](http://ubuntuservergui.com/announcements/welcome#comments)

---

### Post by volkswagner on 2011-12-07
haqking: thanks for the link.  I'm not sure that is a definitive answer, I'm still leaning towards this is not a desktop environment.  Do you agree?

---

### Post by haqking on 2011-12-07
> **volkswagner said:**
> haqking: thanks for the link.  I'm not sure that is a definitive answer, I'm still leaning towards this is not a desktop environment.  Do you agree?

yeah it looks like a project by someone to develop a webmin type interface.

Personally it holds no interest for me.

ssh 
webmin or ISPConfig if your lazy
or install a light GUI such as Lxde or XFce if you really need one

---

### Post by collisionystm on 2011-12-07
:popcorn:> **haqking said:**
> yeah it looks like a project by someone to develop a webmin type interface.

Personally it holds no interest for me.

ssh 
webmin or ISPConfig if your lazy
or install a light GUI such as Lxde or XFce if you really need one

I think its going to blow away webmin. It is being developed specifically for Ubuntu and I have a feeling its going to ROCK :guitar:

---

### Post by collisionystm on 2011-12-07
here is something else to have a look at

[http://www.openpanel.com/](http://www.openpanel.com/)

---

### Post by collisionystm on 2011-12-07
and another

[http://www.artica.fr/](http://www.artica.fr/)

---

### Post by lykwydchykyn on 2011-12-07
> **collisionystm said:**
> :popcorn:

I think its going to blow away webmin. It is being developed specifically for Ubuntu and I have a feeling its going to ROCK :guitar:

Who can say what it's going to be?  So far it's a website with a blog.

 - No screenshots
 - No feature plan
 - No code(!!)
 - No way to get involved and contribute

Not much promise for a project that apparently started 9 months ago.  It smacks of vaporware.

---

### Post by collisionystm on 2011-12-07
another gui that seems interesting 

[http://www.untangle.com/](http://www.untangle.com/)

---

### Post by CharlesA on 2011-12-07
> **haqking said:**
> yeah it looks like a project by someone to develop a webmin type interface.

Personally it holds no interest for me.

ssh 
webmin or ISPConfig if your lazy
or install a light GUI such as Lxde or XFce if you really need one
Same here IMO. I think the only thing I use a web interface for is VirtualBox and that's cuz I'm too lazy to SSH in and run a load of commands just to create a VM.

---

### Post by collisionystm on 2012-01-03
Dont know if I mentioned it already, but I think everyone should check out 

[http://ajenti.org/](http://ajenti.org/)

Its nothing short of awesome.

---

### Post by lykwydchykyn on 2012-01-04
> **collisionystm said:**
> Dont know if I mentioned it already, but I think everyone should check out 

[http://ajenti.org/](http://ajenti.org/)

Its nothing short of awesome.

That *does* look awesome, and they have a repository.  I'll have to check that one out.

EDIT: I checked it out, it has a lot of potential and sure has a nicer feel than webmin, but it's still very young and lacks a lot of features.  I ran in to several bugs as well.  Hopefully they stick with it and make something useful out of it.

---

### Post by spynappels on 2012-01-04
I do like the look of the Ajenti one, I've just installed it and am playing with it now.

I'm not sure where I'd use it if at all, but it does look quite nice.

---

### Post by HugoSerrano on 2012-01-04
Must agree with the good look of that... 

**But you won't get me into a gui!!!** But I may try that one... :-$

:-)

Regards!

---

### Post by collisionystm on 2012-01-04
And if you want to have a nice alternative to Xbmc

[https://www.amahi.org/](https://www.amahi.org/)

---

### Post by rubylaser on 2012-01-04
> **collisionystm said:**
> And if you want to have a nice alternative to Xbmc

[https://www.amahi.org/](https://www.amahi.org/)

How is Amahi an alternative for XBMC?  They serve different purposes.  If you mean using Amahi for Greyhole storage + XBMC, that makes sense to me.  But, maybe I missed some of Amahi's feature set :)

---

### Post by dirtrider1 on 2012-01-04
It looks promising. Anything that can help new users more easily adapt and provides more choices is a good thing. But with that said, IMHO as of now a production server should never be running a GUI except in very specific circumstances.

---

### Post by Phixion on 2012-01-07
Why anyone would want to run a GUI on a server is beyond me.

You can do everything via terminal easily enough...

---

### Post by collisionystm on 2012-01-07
> **Phixion said:**
> Why anyone would want to run a GUI on a server is beyond me.

You can do everything via terminal easily enough...

Except ldap

---

### Post by CharlesA on 2012-01-08
> **collisionystm said:**
> Except ldap
*twitch*

I was thinking of Virtual Machines, but there is always virt-manager.

---

### Post by med1972 on 2012-01-18
> **HugoSerrano said:**
> +1

With gui, that do the job for you, you won't gonna be able to solve problems, because you don't know how stuff it's done. 
With gui's comes more packages, more possible failures, bugs, etc. 
A perfect server will only have the minimum services available. Always avoid gui's. 

:-) Best Regards!

Sure, totally. I've been managing Linux boxen since 1994 and I totally suck cause I've used X Windows so much. If only I had forgone X for all those years ...

A perfect server does exactly what you want to it do. If you want it to run X, then it should run X. Because if you wanted it to run X, and it didn't run X, then it wouldn't be perfect.

- Mark

---

### Post by HugoSerrano on 2012-01-19
> **med1972 said:**
> Sure, totally. I've been managing Linux boxen since 1994 and I totally suck cause I've used X Windows so much. If only I had forgone X for all those years ...


You know yourself better then everyone else. :-P

> 
A perfect server does exactly what you want to it do. If you want it to run X, then it should run X. Because if you wanted it to run X, and it didn't run X, then it wouldn't be perfect.

- MarkLike I said... A perfect server only runs the services that should run to accomplish the task. If it's to serve X, run a X. Nothing new. Avoid run services that you don't need. But if you need X, run it.

---

