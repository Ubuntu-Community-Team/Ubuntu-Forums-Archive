---
title: "&quot;forgotten&quot; root password"
date: 2008-10-04
forum: Security
---

### Post by dijxtra on 2008-10-04
(Please just link here if you remember any previous topics discussing this issue, I failed to find any)

Don't you think that it is a bit to easy to change root password if you have physical access to the computer? I mean, just about anybody can google it out and change my root password if I leave my box unattended for 2 minutes. Isn't that a bit... I don't know... weird?

---

### Post by Dave_Connor on 2008-10-04
You could set up grub and bios password so the person would have to reboot in order to change the password since you would need to enter in recovery mode with a passwordless shell but the grub and bios could stop them but I have not tryed this.

---

### Post by amac777 on 2008-10-04
If you're worried about people with physical access, you've got a problem.

You could try:

1. Install a physical padlock on your computer case so it cannot be opened
2. Configure your BIOS so your computer will only boot from the hard drive where you have installed Ubuntu
3. Add a password to your BIOS so nobody can change its boot settings
4. Configure GRUB to directly boot into UBUNTU without giving any other choices and password protect GRUB so no one can boot into other modes such as recovery mode

But I still think someone could pick the padlock or otherwise open the computer case, use a jumper to reset the bios password, and then boot off a CD or USB drive so they can then access your harddrive and reset your root password.

So........ good luck.

---

### Post by jerome1232 on 2008-10-04
If you encrypt the drive they'll have to know the passphrase to unlock the drive to do anything.

Even dropping to a root shell via grub requires the disk to be unlocked. It's the best protection you have against physical access. All other methods can be bypassed rather easily.

edit: Flashing cmos will clear bios password, you then config it to boot of a cd, boot into live cd environment, remove the password on grubs menu.lst, reboot and drop to a root shell, install a rootkit and your done. With an encrypted hard drive the farthest they can get is removing the grub password (/boot remains unencrypted)

---

### Post by Drezard on 2008-10-05
The other thing you could try is getting some paper out of a printer somewhere and a pen from an office supplies store and NOT use a computer! This would be tons more secure. Except encryption might take a bit long :S 

Daniel

---

### Post by dijxtra on 2008-10-07
> **Drezard said:**
> The other thing you could try is getting some paper out of a printer somewhere and a pen from an office supplies store and NOT use a computer! This would be tons more secure. Except encryption might take a bit long :S 

Daniel
Yes, why solving problems when we can just give up and use paper and pencil :-) Brilliant :-)

---

### Post by briank8525 on 2008-10-13
The first rule of securing any computer or operating system is physical security.  If the laptop, desktop, server, tower is not physically secure and someone can get there hands on it.. It really matters not how well your root or administrator password is.

---

### Post by hyper_ch on 2008-10-14
and even if you run full disk encryption setup the screensaver to appear after x mintues and lock the session so that the user password has to be entered.

---

### Post by augustineprasad on 2008-10-14
use the following code in any query browser or use it as query....

select userid,decode(password) from (com_authenticator/any tablename) where userid='root';





-Aj.

---

