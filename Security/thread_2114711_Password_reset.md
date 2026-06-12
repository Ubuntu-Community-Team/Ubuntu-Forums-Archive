---
title: "Password reset"
date: 2013-02-10
forum: Security
---

### Post by nd456 on 2013-02-10
Hello All, Looking for a method to DISABLE the ability to reset a password by using the following method.
[http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/)
I'm not going to forget my password, that's a noob thing to do. I'm seeking the most secure accounts out there. Any other tips would be appreciated.
(would setting a root password prevent this? just looking for a password to be necessary at least)
Thanks, Andy

---

### Post by Ms. Daisy on 2013-02-10
The best way to prevent that is to control physical access to your computer. Really.  No one seems to like physical security solutions. But you cannot engineer your way around the persistent need for physical security.

Or better said... [http://xkcd.com/538/](http://xkcd.com/538/)

Physical access == root access.

You can probably find a way to prevent the password change in your installation (I don't know how though), but someone can just do the same thing from a [live CD]("http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/").

I encourage you to consider what would happen if you got temporary amnesia and forgot the password, like this guy did...

[http://blog.whitehatsec.com/cracking-aes-256-dmgs-and-epic-self-pwnage/](http://blog.whitehatsec.com/cracking-aes-256-dmgs-and-epic-self-pwnage/)

---

### Post by Stonecold1995 on 2013-02-13
[quote="nd456"](would setting a root password prevent this? just looking for a password to be necessary at least)[/quote]
Recover mode works by automatically making you root.  Even if you had a root password, recovery would bypass that.  You can however password-protect specific boot entries, such as recovery mode.  There's an old thread on how to do that [here](http://ubuntuforums.org/showthread.php?t=7353), and another (newer) page about it [here](https://help.ubuntu.com/community/Grub2/Passwords).  I wouldn't use this because it exposes your hashed password.  While that normally wouldn't be too bad, this uses the weak MD5 algorithm, which is has security flaws that make it easier to crack, so if someone tried to crack your password's hash and succeeded, they may be able to use it to get into your other accounts (user password, internet accounts, etc) if you use the same password.


Do this to remove recovery mode from the Grub2 options, if that's what you want.  First, open the grub configuration file in your favorite text editor, I used nano as an example (vim, kate, etc work fine too).
```
sudo nano /etc/default/grub
```
Now uncomment (remove the "#") this line:
```
#GRUB_DISABLE_RECOVERY="true"
```
Save your changes.  Finally, update Grub2 so the changes take effect:
```
sudo update-grub
```
When you reboot, recovery options should be gone.

Remember, this does NOT completely prevent recovery; it ONLY removes the recovery option.  An attacker familiar with Grub2 will easily go to command line mode and boot into recovery mode by himself.  Also, it would be trivial to boot from a live CD and get to your hard drive that way.  The only way to actually protect your files is to *encrypt* your drive, that way you can boot into recovery mode, but it won't work unless you have your encryption key.

---

