---
title: "Upgrade from 32-bit to 64-bit"
date: 2012-04-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jimned on 2012-04-05
I attempted to upgrade from 32-bit 11.10 to 12.04 64-bit, but after upgrade system info shows that I'm still at 32-bit.  Do I need to reinstall or install 12.04 from scratch?  I'd like to move to a 64-bit OS.  Not sure if it matters, but I dual boot with Windows 7 64-bit.  Machine is a Dell 1564

---

### Post by dcstar on 2012-04-06
> **jimned said:**
> I attempted to upgrade from 32-bit 11.10 to 12.04 64-bit, but after upgrade system info shows that I'm still at 32-bit.  Do I need to reinstall or install 12.04 from scratch?  I'd like to move to a 64-bit OS.  Not sure if it matters, but I dual boot with Windows 7 64-bit.  Machine is a Dell 1564

There has never been an "upgrade" from 32 to 64-bit. It requires a fresh install.

There are already many detailed instructions in the forums on how to save your data before doing this.

---

### Post by jimned on 2012-04-06
Thanks for the prompt response.  I'll do a fresh install of 12.04.  Based upon the sites I've looked at I assume that since I dual boot, I need to reset the MBR to enable loading of Windows and then install Ubuntu.  Some sites are clearer on this than others.  

Do you have a recommended or preferred site for instructions? I've been using Ubuntu since 9.04 and tinker quite a bit, but am not a guru.  I want to make sure I don't loose access to Windows in the process. Partitions are already set up. I want to dual boot and not use Wubi.  Again any recommended site from a well-versed user is most welcome.

---

### Post by ubuntu27 on 2012-04-07
If you have the partitions ready, that is, you have paritition that you will like to install ubuntu on. Then, it should be straigh forward.

The installer should detect the other operating systems and add it to GRUB.


Right now, Ubuntu 12.04 has not been released yet. The common advise if for new users to wait until it is released officially, or [even better] to wait a few weeks after release date to have a more stable system. (The more time passes, the more the OS becomes stable through bug fixes).


If you are adventurous or have courage, you can install Ubuntu Precise Pangolin from the daily iso.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)


Please remember to have backup of your files. :popcorn:

---

### Post by shuttleworthwannabe on 2012-04-07
> **dcstar said:**
> There has never been an "upgrade" from 32 to 64-bit. It requires a fresh install.

There are already many detailed instructions in the forums on how to save your data before doing this.

This.

---

