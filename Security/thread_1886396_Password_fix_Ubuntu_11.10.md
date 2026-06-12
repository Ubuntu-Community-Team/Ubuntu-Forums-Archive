---
title: "Password fix Ubuntu 11.10"
date: 2011-11-24
forum: Security
---

### Post by utahman1971 on 2011-11-24
This is a perfect fix for problem like this.

I deleted my password for administration, and realized that when using terminal, it would ask for password and it would not take it at all. So I tried numerous attempts to reinsert the password.

Well, this is my step by step fix. Before this fix I got an Authentication token manipulation error. 

First thing to do is reboot the computer and use holding 'shift' key while booting. It will the go into recovery.

Do not select anything or hit enter. Select 'e'.

This will take you to a box with code in it. The code that says 'ro quiet splash' replace with 'rw init=/bin/bash' and do not hit enter.

hit F10 to reboot.

Wait for it to give command line.

type 'passwd <username>'  with username with real username that you are trying to fix password for. 

After changing password with new and retyping it again.

Use 
Sync
reboot -f

Once it is back into system you have your password back to normal.:)

---

### Post by univer on 2011-11-29
Good work!

---

### Post by seattle vic on 2012-01-25
My goodness; I would not have thought this was possible, but it saved my bacon today.  I was afraid I'd have to reload the who OS.

Thanks for the tip!

---

