---
title: "exim4 installed when not wanted"
date: 2009-07-31
forum: Server Platforms
---

### Post by R_Lopez on 2009-07-31
I installed Ubuntu 9.04_64 on three servers. I did not (as far as I understand) do anything to install exim because I am going to use postfix (for email gateways only). I did the exact same steps to install on each server.   At "Choose Software to Install" I tabbed to "Continue" with NO blocks checked.

One server had four extra packages compared to the other two. They were all exim4 packages. 

I did apt-get remove exim... on each of them. The files installed stayed in place. I then tried apt-get purge... and apt-get remove --purge and I kept being told they were not installed. Finally I removed all the files by hand.

apt-get clean had no complaints but dpkg -l still shows


rc  exim4                                     4.69-9ubuntu1                     metapackage to ease Exim MTA (v4) installati
rc  exim4-base                                4.69-9ubuntu1                     support files for all Exim MTA (v4) packages
rc  exim4-config                              4.69-9ubuntu1                     configuration for the Exim MTA (v4)
rc  exim4-daemon-light                        4.69-9ubuntu1                     lightweight Exim MTA (v4) daemon

Can I clean this up or should I reinstall again?

Any idea how they could have been installed?

---

