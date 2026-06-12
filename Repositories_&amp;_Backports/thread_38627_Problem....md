---
title: "Problem..."
date: 2005-06-01
forum: Repositories &amp; Backports
---

### Post by cream on 2005-06-01
I got a problem when i installed ubuntu it came up that X couldn't work and that going to try and fix it or something .. but when i finnished i just come to "dos" where you should write your name and then your password then i dont know what do to ? Is't just me that are stupid..couse i don't know what to do frome there  :? .
Thanks for replays ;).. By the way i running on a 64bits amd cpu and i downloaded ubuntu-5.04-install-amd64.iso

---

### Post by bluecode77 on 2005-06-03
Hi pal,
I am new to linux as well. But first of all i can say that its terminal screen or bash where you have arrived after the install.
Hope its Ubuntu you have installed, cause i fail to make a clear install with kubuntu, if its kubuntu you have installed, try to install ubuntu instead.

there are many things you would try to resolve that...

1- try
sudo fglrxconfig

2- try
/var/log/Xorg.0.log    to see whats up
and than 
sudo -configure

3-try
sudo apt-get install rcconf
sudo rcconf

---

### Post by az on 2005-06-03
Obviously, that is not what is supposed to happen.  Luckily, with linux, you have all the power from the comman line.  Use the command line to find out what happened and fix it.  

First log in and run this command:

sudo apt-get -f install

That will tell the package manager to try to fix any package that may not have been properly installed.  If it says nothing interesting (zero packages to install) that is not the problem.

Did you just hit enter at the install prompt?  Because if you entered something else, you may have stopped the installation before the graphical stuff got installed.  Try

sudo apt-get install ubuntu-desktop

This installs the ubuntu-desktop package which installs all the other packages.  

Still no luck?  Try looking at the output of

sudo lspci


This will list all the hardware on your pci bus.  Try to look for the entry regarding your video card.  Please post whatever informationabout your graphics card you can find.  Someone may point out a workaround a known problem with certain graphics cards....

---

