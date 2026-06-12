---
title: "x11 - development"
date: 2007-12-18
forum: Repositories &amp; Backports
---

### Post by KPexEA on 2007-12-18
I've just installed Ubuntu 7.10 last week so I am starting with a fresh machine. I have installed build essentials already and have no problem compiling and linking c++ programs so far.

I'm now trying to install the necessary items for X11 development, according to what I have found I should use:

sudo apt-get install xorg-dev

When I try that I get the error:

E: Couldn't find package xorg-dev

Am I doing something wrong?

Thanks
Kevin

---

### Post by diatribe on 2007-12-18
use synaptic and search for xorg dev, you have the correct general idea but it is a different package name I believe, you can also search with apt-get if you like

---

### Post by KPexEA on 2007-12-19
I did a little Google searching and finally came across a solution.

I needed to go to "System / Administrator / Software Sources " and then enable the "Download from the Internet" for the Open Source software and Source Code" ( my system defaulted to having them all unticked ).

For the next version perhaps the apt-get install command can detect that you don't have any downloadable sources enabled and when it can't find the package you are looking for, it could suggest turning on the download ability when it gives an error message. That might help out future users who come across the same issue.

Cheers,
Kevin

---

