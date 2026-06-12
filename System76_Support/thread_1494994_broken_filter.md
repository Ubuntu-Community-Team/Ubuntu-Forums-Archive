---
title: "broken filter"
date: 2010-05-27
forum: System76 Support
---

### Post by Eyore15 on 2010-05-27
I recently installed 10.04 UNR from scratch.  I then went to install the updates.  I started the install procedure, then was given a dialogue box that said I had I needed to to run the "broken" filter (actually, they message was longer than that, but I can't remember it now). I simply ignored the message and went on to install the upgrades as normal.

Now, I've never seen this reference to "broken filter" before, and I can't narrow a search down on-line to anything that looks reasonable.  

Anyone want to take a stab at explaining what I am supposed to do next?

tnx

mcm

---

### Post by thomasaaron on 2010-05-27
Not exactly sure (yet).

But try establishing an Internet connection and running...

sudo dpkg --configure -a
sudo apt-get install -f

Then run sudo apt-get update && sudo apt-get --assume-yes dist-upgrade

Did that fix it?

---

