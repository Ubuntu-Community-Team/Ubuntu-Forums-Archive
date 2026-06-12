---
title: "kernel 3.2.0-3 keeps loading in synaptic"
date: 2011-12-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2011-12-08
I have done updates from synaptic on a few machines and I noticed that the 3.2.0-3 kernel keeps loading with synpatic. 

Anyone else ?

---

### Post by Harry33 on 2011-12-08
> **ventrical said:**
> I have done updates from synaptic on a few machines and I noticed that the 3.2.0-3 kernel keeps loading with synpatic. 

Anyone else ?

What exactly do you mean "keeps loading". The loading does not finosh or?

I did an upgrade to the newest (in PP repos) linux_3.2.0-3.9 without any issues today.

---

### Post by ventrical on 2011-12-08
> **Harry33 said:**
> What exactly do you mean "keeps loading". The loading does not finosh or?

I did an upgrade to the newest (in PP repos) linux_3.2.0-3.9 without any issues today.

The kernel in the repos is 3.2.0-3 (I think) and it keeps loading up after I run <reload> in synaptic, then <mark> all upgrades. When I choose <apply> the linux 3.2.0-3 image and headers are all there waiting to be downloaded again (but that kernel is already installed). All the systems I have (6) are loading from the standard repos (not PPAs)

hmmmm...

lets try again.. ok .. no such kernel 3.2.0-3.9 found....err .. ok .... yes .. got the 3.2.0-3.9 but it did not notify of this in synaptic .. just 3.2.0-3 ....

false alarm..
addons

---

### Post by bluexrider on 2011-12-08
sudo apt-get clean && sudo apt-get update

---

### Post by ventrical on 2011-12-08
> **bluexrider said:**
> sudo apt-get clean && sudo apt-get update


No.. I got it . Thanks anyways.  Just pointing out that this is Precise and it should tell us Precisley :) what is coming down the pipe. :)

um.. I'm going to try that code anyways  :)

---

### Post by ventrical on 2011-12-08
> **bluexrider said:**
> sudo apt-get clean && sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en
Error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Reading package lists... Done
madame@madame-ME051:~$ 

Ok.. that didn't work .. but it's alright.

---

### Post by bluexrider on 2011-12-08
try changing the server location in software sources

---

### Post by jfernyhough on 2011-12-08
There's not a problem - it was just a different version of 3.2.0-3. :)

Mark it as solved, quick, before more people offer solutions! :lolflag:

---

### Post by bluexrider on 2011-12-08
> **jfernyhough said:**
> there's not a problem - it was just a different version of 3.2.0-3. :)

mark it as solved, quick, before more people offer solutions! :lolflag:
[size=4](solved)


[/size]

---

