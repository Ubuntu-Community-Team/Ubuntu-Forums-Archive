---
title: "Root password for security?"
date: 2011-09-02
forum: Security
---

### Post by caffeinated blood on 2011-09-02
Okay, I'm aware this is an aged question and I know it is not recommended to enable the root account. But the physical location of my desktop is in a room that has the potential for people to access it in my absence(not likely, but the possibility remains). 

So under these circumstances would it be better to set a root password(thereby enabling the account) or leave it locked(default setting and not having a password)? 

Also, couldn't someone with physical access to an Ubuntu machine access root anyway using a Live-CD?

---

### Post by haqking on 2011-09-02
> **caffeinated blood said:**
> Okay, I'm aware this is an aged question and I know it is not recommended to enable the root account. But the physical location of my desktop is in a room that has the potential for people to access it in my absence(not likely, but the possibility remains). 

So under these circumstances would it be better to set a root password(thereby enabling the account) or leave it locked(default setting and not having a password)? 

Also, couldn't someone with physical access to an Ubuntu machine access root anyway using a Live-CD?

Physical access is root access always.

If it is aged question then you have read about it so answered your own question ;-)

Disabled for a reason, not recommended to enable it, not just about crackers (malicious hackers) but also scripts and services etc running under admin privelege when logged into it.

Leave it locked and use Sudo which supports the canonical model.

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

rootsudo
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

security stickies (5 stickies)
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

### Post by walt.smith1960 on 2011-09-02
Could you put a password that would keep it from booting at all?  Wouldn't even do a POST without a password?  That'd be a BIOS function, obviously.

---

### Post by haqking on 2011-09-02
> **walt.smith1960 said:**
> Could you put a password that would keep it from booting at all?  Wouldn't even do a POST without a password?  That'd be a BIOS function, obviously.

yes you could but Physcal access hell bent on damage can in some systems reset the BIOS with a jumper or battery removal etc.

HDD can be removed and accessed with specialist software.

Or just smash the thing to pieces !

Obviously this is all possibilities depending on the intent of the individual.

every thing helps, including not enabling the ROOT ;-)

I have a boot password and HDD access password, and no one ever goes near my machine.

Anywhere you can add a layer of security the better, the best approach to security is layered !

---

### Post by ajgreeny on 2011-09-02
> **walt.smith1960 said:**
> Could you put a password that would keep it from booting at all?  Wouldn't even do a POST without a password?  That'd be a BIOS function, obviously.
That would still not stop someone who knows what they are doing from compromising the machine.

As haqking said, physical access is root access always, and there is probably nothing you can do other than choosing a very good password.  Even so, given enough time to reboot, anyone can get root access, and then cause mayhem, if they really want to.

---

### Post by agillator on 2011-09-02
I'll emphasize that physical access is root access. Another avenue to invesitgate, though, might be TrueCrypt. You wouldn't be able to encrypt your entire drive, obviously, but you could keep anything sensitive encrypted. When you are not physically at your computer you dismount the encrypted portion. Then, even with root access, someone cannot get at your sensitive data unless they know your passphrase and your user password.

---

### Post by caffeinated blood on 2011-09-02
Unfortunately, I can't use a BIOS password to secure booting. Another household member needs daily access to Windows on this dual-boot desktop. And this person lacks concern of "having to remember" another password. At the least, I do have a BIOS password for system changes. Yes, someone could use the jumper and clear CMOS, but a cleared/changed password would be obvious.

My thinking on a root password is that if the root account is "protected" with a password, anyone with physical access would have to clear/change this password to do their wrong. This would be an obvious red flag. But with no root password in effect, I would never know. So, which course of action would be the lesser of two evils?

---

### Post by ajgreeny on 2011-09-03
A password protected root account is not more secure than a disabled root account surely?

All this has been discussed over and over again,and in my opinion is pointless.  If you want a root accout on your system, enable it.  If you don't know how to do that, you are not in a good position to argue the sense, or nonsense, of having the root account enabled.

---

