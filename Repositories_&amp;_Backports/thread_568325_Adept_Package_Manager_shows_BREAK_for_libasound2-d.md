---
title: "Adept Package Manager shows BREAK for libasound2-dev"
date: 2007-10-05
forum: Repositories &amp; Backports
---

### Post by lbriner on 2007-10-05
I am trying to build Ardour2 for Feisty (running a Gutsy kernel for wifi support!!). One of the required packages for ardour2 is libasound2-dev.

When I choose to install this in Adept it says that the install would break something. It is the only package being installed (it is also not pulling in anything else).

On the file details it says it conflicts with alsa-headers and libasound-dev, neither of which is even in my lists. The only thing it might be is that libasound2-dev says it requires libasound2 = 1.0.13-lubuntu5 and the one I have installed (the only one there) is 1.0.14.

Can anyone help? Should the dev package require libasound2 >= 1.0.13 instead of only =?

Bit of pain because ardour2 looks sweet.

THanks

Luke

---

### Post by lbriner on 2007-10-05
Fixed!! 

I had brought in an upgraded libasound2 package when bringing in the gutsy kernel. This was too new for the libasound2-dev package. I ran sudo apt-get install libasound='1.0.13-1ubuntu5' from the command line and it replaced the new one with the correct one.

Sweet.

---

