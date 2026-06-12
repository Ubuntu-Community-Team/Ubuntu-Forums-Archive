---
title: "Grub (quantal secureness)"
date: 2012-10-25
forum: Security
---

### Post by twipley on 2012-10-25
I am fiddling with Grub trying to make it so that its recovery-mode feature, among others, does not pose a security threat.

Although physical intrusions are not to be worried about, users (teenagers -- they sometimes are curious, aren't they?) only have access to "standard" accounts, and the BIOS and boot order have both been taken care of, in terms of secureness.

All is left to do is concerning Grub. I have spent the past hours reading blog and forum posts, and resources like:
[https://help.ubuntu.com/community/Grub2/Passwords](https://help.ubuntu.com/community/Grub2/Passwords)
[http://www.gnu.org/software/grub/manual/html_node/Security.html](http://www.gnu.org/software/grub/manual/html_node/Security.html)

However, I cannot afford spending such time, and am resorting to this wonderful forum so that people can share their experiences, and I hope shed some light on the various issues.

First off, about the sole sensible thing I have found out is that password encryption in this case seems unjustified, as whenever "sudo update-grub" is ran while an unencrypted (plaintext) password was inputed to the "/etc/grub.d/40_custom" file, the grub.cfg file (rightly) is rendered unreadable to standard users (lacking administrative passwords).

I must note that the system is a sole-Quantal one. A fresh install was performed, and I am simply trying to secure Grub in such a way that there is no way for standard users to fiddle with its terminal, edit its command lines, or enter the recovery mode.

Currently I have gksudo-edited the "/etc/grub.d/40_custom" file through gedit this way:

set superusers="admin_username"
password admin_username admin_password

But it seems a standard username and a corresponding password also has to be set up so as for standard users to be able to enter the default "Ubuntu" entry. I am looking for a future-proof-enough method to edit the 40_custom file, so that official Ubuntu Grub and kernel updates would not be breaking anything, or in other words so that the system continues both to be bootable and to be protected against the most curious minds.

---

### Post by twipley on 2012-10-26
Again, the goal would be to make it as easy-going as possible... even, if possible, to make it boot straight to Ubuntu, without even prompting for a password at the Grub level, although password-protecting non-default entries, i.e. anything else than the default Ubuntu boot entry.

I'm sure some of you people have any experience with Grub since recent Quantal changes? I'd *greatly* appreciate any help from you, for it to be said!

Thanks in advance!
twipley

---

### Post by twipley on 2012-10-26
Probably this is not an acceptable action, but I took the initiative of posting a similar, if not identical, topic in a sub-forum that had more chance to attact readers and knowledgeable people.

Here is that thread: [http://ubuntuforums.org/showthread.php?t=2076594](http://ubuntuforums.org/showthread.php?t=2076594)

Although nothing too-worthwhile has yet been said, even if a few posters have at the moment replied.

---

### Post by oldos2er on 2012-10-26
> **twipley said:**
> Probably this is not an acceptable action, but I took the initiative of posting a similar, if not identical, topic in a sub-forum that had more chance to attact readers and knowledgeable people.

Here is that thread: [http://ubuntuforums.org/showthread.php?t=2076594](http://ubuntuforums.org/showthread.php?t=2076594)

Although nothing too-worthwhile has yet been said, even if a few posters have at the moment replied.

I am closing this thread. Discussion should be pursued in your other thread [http://ubuntuforums.org/showthread.php?t=2076594](http://ubuntuforums.org/showthread.php?t=2076594)
Thanks for your understanding.

I also want to say, physical access = root access. You can set passwords on grub, in BIOS, but these passwords can be circumvented with no much trouble.

---

