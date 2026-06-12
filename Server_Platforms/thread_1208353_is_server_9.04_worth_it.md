---
title: "is server 9.04 worth it?"
date: 2009-07-09
forum: Server Platforms
---

### Post by abraham.varricatt on 2009-07-09
I have been tasked with selecting a distribution for use on our company server. We're a small firm with about 20 people or so.

What attracts me to Ubuntu is the GUI environment. If I understand things right, the difference between the server edition and desktop edition is (in a simplified way),

desktop edition = server edition + GNOME window manager

We need our new server to be reliable, so I'm in a fix about what to install. Should I install Ubuntu (Desktop) 8.04 or should I use Ubuntu (Desktop) 9.04 ?  (If it helps, our company does NOT have any association with Canonical)

Is there any important point I'm missing here?

---

### Post by Cheesemill on 2009-07-09
I stick with 8.04 LTS Server on all my machines at work because of the Long Term Support (it's currently supported until 2013). If you go for a non-LTS release then you are going to have to upgrade every 18 months instead of 5 years.

So unless there's a feature/app that you need that's not available then go for 8.04 (or hold off until 10.04 which is the next LTS release).

As for server/desktop I **never** install a GUI on my servers. If a server was meant to have a GUI then Canonical would have made it that way.

---

### Post by dragos2 on 2009-07-09
Server edition contains server specific optimizations, read the manual.
It is on the main page !

You can apply a GUI to yoyr server: 

sudo apt-get install xfce4

or 

sudo apt-get install xorg gnome-core gdm

But you should not install a gui.

---

### Post by abraham.varricatt on 2009-07-09
dragos2,

What do you mean by GUI and gui ?

I have heard about security issues with using GUI on a server. But, my experience is with the Desktop. 

How big of a matter is it? i.e. Desktop vs bash shell ?

Also, is it easy to use virtualization software with the bash shell? Specifically VirtualBox ?

---

### Post by windependence on 2009-07-09
Agree with the two previous posters. If you want a GUI stick with Windoze or better yet buy a Mac server. 

BTW desktop edition != server edition + GNOME window manager

The server kernel is very different and optimized for things like virtualization. There is no GUI on purpose. 

> **No X server by design**

  By design, Ubuntu Server Edition does not include an X server or any graphical desktop applications. This is a deliberate choice as we believe that most servers should be serviced remotely, are safer without the addition of code that needs direct communication from user space to hardware, and should not be used as a desktop by their administrator. 
 [INDENT] 	 	"*So I applaud the Ubuntu team&#8217;s common sense (and courage) in keeping the X Window System out of the default installation of Ubuntu Server.*"
	--Mick Bauer in April 2008 Linux Journal - "Security Features in Ubuntu Server"   	
 [/INDENT]

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security)

-Tim

---

### Post by abraham.varricatt on 2009-07-09
Cheesemill,

When you mean support, do you mean the free updates we get? i.e. on 8.04 we'll keep getting updates till 2013, but with 9.04 it will be much shorter?

Won't those updates upgrade me from 8.04 to 9.04 ? (At least, that's how I used to think of them. I've never tried it, I just reformat my desktop every 6 or 8 months, but I can't do that on a server!)

---

### Post by abraham.varricatt on 2009-07-09
> **windependence said:**
> 
The server kernel is very different and optimized for things like virtualization. There is no GUI on purpose. 
[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security)
-Tim

That's most useful. Thank you. Any ideas where I can get some info about using virtualization software (preferably open-source or freeware) with the bash prompt ?

---

### Post by Cheesemill on 2009-07-09
> **abraham.varricatt said:**
> Cheesemill,

When you mean support, do you mean the free updates we get? i.e. on 8.04 we'll keep getting updates till 2013, but with 9.04 it will be much shorter?

Won't those updates upgrade me from 8.04 to 9.04 ? (At least, that's how I used to think of them. I've never tried it, I just reformat my desktop every 6 or 8 months, but I can't do that on a server!)


Normal releases only get support for 18 months from their release, so support for 9.04 will run out in 10.10

Every 2 years a LTS version is released which is supported for 3 years on the desktop and 5 years on the server. This is so that businesses that use Ubuntu don't have to continuously update their machines.

Just applying updates to a machine will not bring it to the latest version, you have to manually **upgrade** to a new release.

---

### Post by Wim Sturkenboom on 2009-07-09
> **abraham.varricatt said:**
> ... But, my experience is with the Desktop. 

How big of a matter is it? i.e. Desktop vs bash shell ?

A GUI does not belong on a server (in my humble opinion). Time to learn bash and commands. And yes, it is different.
Having said that, you should be able to install the graphical environment but do not boot into it by default. When you need it, you can run startx to get it. At least that way it will not chew resources 100% of the time.

When I tried Ubuntu 6.06 server, it was lacking some important programs (sshd if I remember correctly was one of them) that had to be installed afterwards. Without an internet connection, that s.cks. So I threw it off and went back to trusted Slackware.

---

### Post by Thirtysixway on 2009-07-09
I'd go with 8.04 server edition.  You can install gnome on it if you want, personally I don't think you'll be compromising your security as long as you have passwords set.  If that makes it easier to manage, then go ahead with the gui.

Instead of installing the gui, you could go with something like webmin.

---

### Post by juancarlospaco on 2009-07-09
For Virtualization:
On Server *(without GUI)*: **sudo apt-get update && sudo apt-get install kvm openssh-server**

On Desktop Administration Console *(GUI)* : [Convirt ]("http://www.convirture.com/wiki/index.php?title=Installation#Ubuntu_8.10_.2F_9.04")

---

### Post by abraham.varricatt on 2009-07-15
Thanks for the replies guys!

---

### Post by windependence on 2009-07-15
I have been meaning to write a VMware ESXi tutorial, but I am bogged down with work. Sorry everyone, it's top on my list when I get a breather.

-Tim

---

