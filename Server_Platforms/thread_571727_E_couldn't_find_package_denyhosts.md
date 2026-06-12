---
title: "E: couldn't find package denyhosts"
date: 2007-10-09
forum: Server Platforms
---

### Post by putz3000 on 2007-10-09
I have not spotted anything in the previous threads regarding installing denyhosts that can answer my problem so I am posting it here.  I have an older server running 2 Intel PIII 933MHz processors.  For some goofy reason, I was unable to get 7.04 to install so I finaly had to install 6.06 LTS.  I did this then when it was all said and done I had updated, dist-upgraded, changed the sources.list (added # to every instance of CD Rom, changed all drapper to feisty) and yet I still am unable to install denyhosts.  previous to denyhosts (also prior to upgrading the dist) I had installed ssh openssh-server.  When I tried to install denyhosts both before the updates and dist-upgrade as well as after, I get the same thing:

Sudo apt-get install denyhosts (I get the following: Reading Package 
lists....Done / Building dependency tree....Done / E: couldn't find package denyhosts).

I have even tried it as root just in case the Sudo didn't cut it.  I have rechecked my sources.list and all the changes I made are still listed.  Any idea's?  I assume it is still trying to go to the E: drive to get this file although it had no problem with ssh openssh-server (no cd in drive) nor did it have any problems going out for update and dist-upgrade.  I can not figure out a work around or why it is refusing to do this.

Thank you,

---

### Post by MJN on 2007-10-09
Post your /etc/apt/sources.list as it may well be you've missed the repository (universe) out, or perhaps another error has slipped through (easy not to see the wood for the trees in there!).

(Note: 'E:' is referring to 'error'. The use of drive 'letters' is a Windows thing and best left that way... ;))

Mathew

---

### Post by bodhi.zazen on 2007-10-09
Deny hosts is in Universe. You likely need to enable a few repositories :

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by putz3000 on 2007-10-10
> **bodhi.zazen said:**
> Deny hosts is in Universe. You likely need to enable a few repositories :

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Thank you kindly.  You were dead on and with your links I was able to figure out the repository problem and fix it.  Thank you very much.

Anyone know how to change the title of my post so it now reads solved?

---

