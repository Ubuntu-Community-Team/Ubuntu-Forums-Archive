---
title: "VMware and Feisty 7.04"
date: 2007-07-24
forum: Server Platforms
---

### Post by sefs on 2007-07-24
Does anyone has Feisty running in VMWare successfully?  

p.s. whats the best forum for VMWare with Feisty guest questions.

---

### Post by elst on 2007-07-24
I'm currently running VMware Workstation 6 on Feisty, and one of the guests is a Feisty (Server Edition) VM.

As commercial and proprietary products, the best support is direct from the manufacturer, or their forums:

[http://www.vmware.com/community/index.jspa]("http://www.vmware.com/community/index.jspa")

VMware staff actually do read and answer posts on those forums, which is great.

---

### Post by unixhead on 2007-07-24
If VMWare does not work out you may try [Virtual Box](http://www.virtualbox.org/) which is GPL.

---

### Post by sefs on 2007-07-29
Elst that is my scenario...feisty server running as a guest on a fiesty host..  Do you have have vmware tools installed?  If so do you have any troubles with the mouse? That is every thing works fine but single clicking, whereby If you single click,  about 30 percent of the time you get an actual single click event, but mostly the fesity server guest interprets a single click as a double click.  So for instance when you single click on a folder it opens on what appears to be a single click.  But somehow feisty is translating it as a double click.  Behavior also present in Gusty.

> **elst said:**
> I'm currently running VMware Workstation 6 on Feisty, and one of the guests is a Feisty (Server Edition) VM
.

---

### Post by elst on 2007-07-31
> **sefs said:**
> Elst that is my scenario...feisty server running as a guest on a fiesty host..  Do you have have vmware tools installed?  If so do you have any troubles with the mouse? That is every thing works fine but single clicking, whereby If you single click,  about 30 percent of the time you get an actual single click event, but mostly the fesity server guest interprets a single click as a double click.  So for instance when you single click on a folder it opens on what appears to be a single click.  But somehow feisty is translating it as a double click.  Behavior also present in Gusty.

I'm afraid it's just a CLI guest system, and so I haven't bothered with VMware Tools.

---

### Post by OpteornGuy on 2007-07-31
I've got VMWare Server up and running on my Feisty, which is actually inside of VMWare Server on a Win2k3 box.  However I am having a few funny issues with mine.  This the spot to post these or is there another section on this board?

---

### Post by Frak on 2007-07-31
Just remember to cd to the directory where its at then run
```
./vmware-install.pl
```
If you mean installing Feisty in VMWare, I couldn't tell you why it couldn't work. Try Virtualbox if you can't get it with VMWare.

---

### Post by OpteornGuy on 2007-07-31
I'm not sure if your post is one regarding mine, however installing Fiesty in a VM using VMWare server is not the problem.  

Here's the situation....

Currently the company I work for is cycling our servers out in the field.  These servers are only 3 years old and pretty robust.  What I want to do is run Ubuntu ( possibly Server ) on one of these servers with VMWare Server running inside of that with multiple different servers running inside of VMWare for testing different things.  I want to be able to manage the Server remotely which for the most part isn't a problem.  The problem that I am having right now with testing is that I can get the VMWare Server Console from Ubuntu to connect remotely to my Windows Server 2k3 Host, however I can NOT get my Windows Server 2k3 VMWare Server Console to connect remotely to VMWare Server Console running on Ubuntu ( which is actually a VM running on the Server 2k3 host ).  The error I get is that there is a Username/Password failure.  I've tried using my Ubuntu username/pass however this won't connect.  I've tried root, doesn't work.  I'm not sure where else to head on this since the Ubuntu side will connect to the Windows side, but not vice-versa.  Ubuntu is 7.04 w/latest update and the Windows side is 2k3 SP2.  Thanks!

---

### Post by Opteronguy on 2007-08-01
Well I went through and got VMWare Server setup on Ubuntu server.  It's going mostly well at this point, however after doing a restart all of the VMWare Server services have failed to start.  This happened after I installed the Management Interface w/patch.  Back to working on this again I guess.

---

### Post by saserlite on 2007-08-07
> **sefs said:**
> Elst that is my scenario...feisty server running as a guest on a fiesty host..  Do you have have vmware tools installed?  If so do you have any troubles with the mouse? That is every thing works fine but single clicking, whereby If you single click,  about 30 percent of the time you get an actual single click event, but mostly the fesity server guest interprets a single click as a double click.  So for instance when you single click on a folder it opens on what appears to be a single click.  But somehow feisty is translating it as a double click.  Behavior also present in Gusty.

Workarounds for this issue can be found in the following thread:

[http://www.vmware.com/community/thread.jspa?messageID=716756](http://www.vmware.com/community/thread.jspa?messageID=716756)

---

