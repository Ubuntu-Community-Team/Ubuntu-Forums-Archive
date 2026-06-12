---
title: "Problem with sudo"
date: 2008-08-21
forum: Security
---

### Post by farmdve on 2008-08-21
I tried removing the password prompt for anything i do with these commands ```
export EDITOR=/usr/bin/nano
sudo -E visudo
```

And changed the last line ```

%admin ALL=(ALL) ALL
to
%admin ALL=(ALL) NOPASSWD:ALL
```

Now everytime i wanna do something that wants admin rights it doesnt let me :(
How do i revert this back to its normal self? as now it does not let me open the nano file at all, **and cant use the sudo anymore** because i have no access :(

---

### Post by HalPomeranz on 2008-08-21
That's the correct syntax for the NOPASSWD: statement, so an error must have gotten introduced someplace else in the file.  I'm surprised visudo didn't alert you to the problem, but whatever.

To fix your sudoers file you're going to have to boot from CD.  That should allow you to access the sudoers file on your hard drive and make whatever changes are necessary to fix things.

---

### Post by farmdve on 2008-08-21
I have the live cd but i have to restart pc and then do it or boot from the loaded OS ?

P.S
And yes now visudo also gives error but i am in windows now so i cant remember what it is

---

### Post by xeth_delta on 2008-08-21
> **farmdve said:**
> I have the live cd but i have to restart pc and then do it or boot from the loaded OS ?

P.S
And yes now visudo also gives error but i am in windows now so i cant remember what it is

Yes, you will have to make the changes from the CD environment. But as a word of caution, I really do not think that removing the root password prompting is a good idea to start with, if only from security point of view. By the other hand, it might also prevent severe damage to the system cause by a wrong command or inadvertent mistakes. Accidents can happen to anybody.

More info here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Titan8990 on 2008-08-21
Not only that, the forums are not supposed to help with this kind of thing, at all.

---

### Post by snowpine on 2008-08-21
> **Titan8990 said:**
> Not only that, the forums are not supposed to help with this kind of thing, at all.

We are allowed to help people fix their mistakes. :)

---

### Post by farmdve on 2008-08-21
Well it was no security issue its just that i cannot execute commands with sudo or if i by any chance do it without sudo it says i am not admin :(

---

### Post by snowpine on 2008-08-21
Yes, reboot your computer with the Live CD in the drive. Then, you should be able to fix the file. Good luck!

---

### Post by farmdve on 2008-08-21
I did not need the CD i went into recovery mode and rewrited sudoers's last line to the original state and it worked
It is **SOLVED** :)
Thanks anyway

---

