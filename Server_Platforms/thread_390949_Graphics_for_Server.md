---
title: "Graphics for Server"
date: 2007-03-22
forum: Server Platforms
---

### Post by StingSlang on 2007-03-22
Is there any way to have a graphical interface with Ubuntu server?

---

### Post by hkgonra on 2007-03-22
Yes you can download the regular ubuntu desktop.

sudo aptitude install ubuntu-desktop

---

### Post by cyberdork33 on 2007-03-22
> **StingSlang said:**
> Is there any way to have a graphical interface with Ubuntu server?

Why did you install server in the first place?

```
sudo apt-get install ubuntu-desktop
```

EDIT: Beat me to it...

---

### Post by StingSlang on 2007-03-22
wait, so what is the difference between Ubuntu Desktop and Server addition?

---

### Post by Nikron on 2007-03-22
> **StingSlang said:**
> wait, so what is the difference between Ubuntu Desktop and Server addition?
Server comes with the bare minimum with the ability to install a LAMP and/or DNS server during the install process.  Desktop edition installs ubuntu-desktop and a few other things it deems necessary.

---

### Post by StingSlang on 2007-03-22
so basically you can use normal ubuntu as a server?

---

### Post by Nikron on 2007-03-22
> **StingSlang said:**
> so basically you can use normal ubuntu as a server?

You could do that, yes.

---

### Post by steveneddy on 2007-03-24
> **StingSlang said:**
> so basically you can use normal ubuntu as a server?

I actually use normal Ubuntu Dapper as my web server - 

and I VPN into it for maintenance and because that's where I store everything - 

and it is a file server and print server for the home network.

Download apache2 from Synaptic. It's a beautiful piece of code that works perfectly out of the box.

Just FYI - my IP address is dynamic - so I had to go to DYNDNS.org to sign up for the free service. This uses a utility on my Linksys router to report to DynDNS whenever my IP address changes, and I get a real address to type into any web browser, and the same address for the VPN also, BTW. 

Maybe this is too much info, but I like to type a lot.

lol

-SE

---

### Post by pppetter on 2007-03-24
Don't forget the fact that gnome, kde and everything uses alot of system resources, and since you are running a server, you don't actually want that. 

If you want a graphical interface for your server, try install webmin for example, and log in to your server from your desktop.

---

### Post by Kissack on 2007-03-24
> **hkgonra said:**
> Yes you can download the regular ubuntu desktop.

sudo aptitude install ubuntu-desktop

What does this install?  I am looking to add a light desktop (like xubuntu) to my server install too.  Then I can vnc in for an occasional graphical desktop.  I find this usefull for initiating commands that may take a while to run, as I can then close vnc on the client and resume it later to check progress

-- 
Allan

---

### Post by steveneddy on 2007-03-24
xubuntu would be a great choise because it is so light. 

I just run a web server that gets very little traffic, so the headroom is negligable.

And yes - I also have webmin installed - a great utility. Most of my remote admin tasks can be done through webmin.

---

### Post by silurius on 2007-03-28
> **steveneddy said:**
> xubuntu would be a great choise because it is so light. 

I just run a web server that gets very little traffic, so the headroom is negligable.

I'm inclined to install KDE on a new LAMP web server just because it's what I'm used to.  It's dev now but may grow to become a production server later.  How is 'light' defined in this context?  Are we talking just disk space and GUI responsiveness, or would KDE bog down my server in some other way?  The machine in question is a Dell PowerEdge 2650.

---

### Post by Brazen on 2007-03-28
> **StingSlang said:**
> wait, so what is the difference between Ubuntu Desktop and Server addition?

The Dapper server edition gets 5 years of security and bugfix support, where-as the desktop version only gets 3 years.

---

