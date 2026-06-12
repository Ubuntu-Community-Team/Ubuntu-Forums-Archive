---
title: "Citrix Reciever installed no error, but not starting"
date: 2012-05-10
forum: Security
---

### Post by wannabegeek on 2012-05-10
Hi all,

I need to install Citrix Reciever on my Ubuntu 10.10  64 bit system.
 
My first attempt at installing openmotif was to use the repo to get the  motif lib which I did. THen I  decided that was going to confound things....I  purged the install of the lib3motif  (somethinglike that) and  installed openmotiff  64 bit by using alien to convert the .rpm to .deb and
installing with dpkg.


Then I downloaded the citrix 64 bit software. At first it wouldn't complete the post install script due to a shell script bug that didn't detect the architecture properly. However, the icon for the main menu was created.

I hacked the script and ran dpkg --configure on the unpacked .deb files. NO ERRORS reported 
at this point.

I try to start citrix from the main menu and nothing happens.
I tried the command line with $wfica and nothing.

I will try to purge the citrix install and try again...I think I did that once already but the menu start icon didn't go away.

Any ideas ?

---

