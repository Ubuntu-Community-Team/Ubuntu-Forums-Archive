---
title: "Changed password but didn't update passphrase - am I toast?"
date: 2011-04-19
forum: Security
---

### Post by cforput on 2011-04-19
When I set up an ID in Ubuntu, I encrypted it. I did a print screen of the passphrase and put it on the desktop. I'm just learning how to use the encryption so don't fault me for putting it right on the desktop. There is no important data in this ID. 

Now, I went and changed my password to the account. On the next boot, I got a few error message:

Could not update ICEauthority file /home/mickymouse/.ICEauthority

There is a problem with the configuration server /usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256

In researching these, it looks like the problem is that I changed the password but didn't update (or something) my passphrase.

I can't boot into the GUI but I have figured out how to boot to a command prompt. I don't have access to my home directory because I don't have my passphrase.

Am I toast or is there a way to recover / update the passphrase?

---

### Post by bodhi.zazen on 2011-04-19
How did you change your password ?

boot to recovery mode, this will be command line only.

As root, change your password back to the old password.

In the future, change your password with the graphical tools or as a user (not root).

---

### Post by cforput on 2011-04-19
> **bodhi.zazen said:**
> How did you change your password ?

boot to recovery mode, this will be command line only.

As root, change your password back to the old password.

In the future, change your password with the graphical tools or as a user (not root).

I already tried booting into recovery mode and changing it back. That didn't work. I used the graphical tool but I was logged in as another user when I made the change.

---

### Post by bodhi.zazen on 2011-04-20
> **cforput said:**
> I already tried booting into recovery mode and changing it back. That didn't work. I used the graphical tool but I was logged in as another user when I made the change.

That is a new one on me, I have not seen that before.

If it did not work to reset the password, you can try to recover the data from either recovery mode or a live CD. You should be able to decrypt your home directory with the old password.

[http://bodhizazen.net/Tutorials/Ecryptfs#Live](http://bodhizazen.net/Tutorials/Ecryptfs#Live)

---

