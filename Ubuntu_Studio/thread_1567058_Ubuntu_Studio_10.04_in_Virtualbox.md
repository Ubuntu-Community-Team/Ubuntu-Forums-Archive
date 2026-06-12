---
title: "Ubuntu Studio 10.04 in Virtualbox"
date: 2010-09-03
forum: Ubuntu Studio
---

### Post by robertschmitzberlin on 2010-09-03
Hi, there, I had a problem and solved it, and I really want to share the experience.

I have installed Ubuntu Studio 10.04 in Virtualbox 3.8.2 on an Windows machine.
Everything worked fine. 

Then I tried to install the guest additions and kept running into the error 
"Error: unable to find the sources of your current linux kernel". The important guest additions (resizing the window to any possible size, using the shared folder) could not be installed.

I googled and found the answer to 
sudo apt-get install build-essential linux-headers-'uname-r'
but of course that doesn't work.

First you must 
uname -r
and I had to realize that the number I got was not the one I expected.

So I had to use the packet management to install the linux-headers of the kernel version, and afterwards the guest addition installation worked just fine.

I wanted to rant a little: Why on earth didn't the creators of this wonderful Ubuntu Studio distro NOT include the linux headers for the very version of the kernel? Why?!?

Anyway, maybe this'll help somebody else.


Robert

---

### Post by bbboB on 2010-09-12
Robert,
A big THANK YOU!
Spent a couple of hours yesterday trying to puzzle this one out.
Same problem as you described and the guest additions installed well, except a restart was necessary for everything to play nice together.

Now, if I can get the shared folders problem licked, I'll be running well.

Thanks again.

boB

---

