---
title: "Problems with booting and login on Ubuntu 12.10"
date: 2012-11-12
forum: Virtualisation
---

### Post by bostjanv on 2012-11-12
Hello,
I've started using Ubuntu 12.10 on a VMware Workstation 9, and I am encountering TWO significant problems:

(1) The boot process is AWFULLY slow. Frequently it gets stuck somewhere in the middle,
      and I have to reset the (virtual) computer. Usually, the boot succeeds after the reset;
(2) Today I have encountered an even worse problem: on login, after entering my    
      password, the computer's response was to return to the login screen (no message
      about bad password appeared). I am absolutely certain that I used the correct
      password

Any help would be appreciated.
Regards,
bostjanv

---

### Post by Bucky Ball on 2012-11-12
*Thread moved to **Virtualisation***

---

### Post by gerowen on 2012-11-12
> **bostjanv said:**
> Hello,
I've started using Ubuntu 12.10 on a VMware Workstation 9, and I am encountering TWO significant problems:

(1) The boot process is AWFULLY slow. Frequently it gets stuck somewhere in the middle,
      and I have to reset the (virtual) computer. Usually, the boot succeeds after the reset;
(2) Today I have encountered an even worse problem: on login, after entering my    
      password, the computer's response was to return to the login screen (no message
      about bad password appeared). I am absolutely certain that I used the correct
      password

Any help would be appreciated.
Regards,
bostjanv

As far as the performance issue goes, how much of your system resources did you allot to the virtual machine?  Out of the box, Ubuntu is pretty resource intensive since the introduction of Unity, and is intended for machines with a good amount of RAM.  Double check and make sure you've allotted the proper amount of resources to your virtual machine for it to run smooth.

Also, during the boot process, try hitting the "Escape" key.  It used to cause the OS to boot in verbose mode so you can see if anything fails during the boot process.  This could show you what is happening when the startup hangs.

---

### Post by bostjanv on 2012-11-13
Thanks for the recommendation regarding "Escape" key. I'll try to get more information.

Regarding issue (2) in my original post, it turned out to be unrelated to both virtualisation and Ubuntu. It resulted from a syntax error in my .profile file, and it appeared on Debian 6 as well. One would expect to see some message in a case like this (i.e., syntax errors in .profile); but none appeared, the log in screen just kept reappearing.

Regards,
bostjanv

---

