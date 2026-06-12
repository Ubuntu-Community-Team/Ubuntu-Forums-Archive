---
title: "Ubuntu on VM with XP host"
date: 2007-12-15
forum: Virtualisation
---

### Post by livestrong on 2007-12-15
Hi,

I am new to Ubuntu.

I created a VM on my XP host and installed the Ubuntu 7.10 server edition. 

I have two issues here:

a) I realized that the root account on Ubuntu is disabled. How do I enabled that? I have tried using the following commands and none of them work:
  1 - sudo passwd root
  2 - su root
  3 - sudo xterm

b) The second issue is, when I enter the above commands, I get the error: 
  sendmail: fatal: open/postfix/main.cf: No such file or directory
  <myownusername> is not in the sudoers file. This incident will be reported.

I can't edit the sudoers file because I don't have the permissions for it.

During the installation of Ubuntu, I also realized that I wasn't asked for the root password. I created <myownusername> with my password, but apparently, I am not the root of my own machine.

Any help? :(

---

### Post by funrider on 2007-12-15
i doubt it has anything to do with VM. You can get more response in this forum: 

[http://ubuntuforums.org/forumdisplay.php?f=73](http://ubuntuforums.org/forumdisplay.php?f=73)

---

