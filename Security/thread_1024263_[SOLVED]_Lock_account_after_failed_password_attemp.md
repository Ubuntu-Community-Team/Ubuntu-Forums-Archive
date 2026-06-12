---
title: "[SOLVED] Lock account after failed password attempts"
date: 2008-12-28
forum: Security
---

### Post by Kissell on 2008-12-28
Anyone can attempt to login to my computer Ubuntu machines as many times as they want...  ewww...  Ideally, I'd like to limit users to three login attempts and then lock out their account until an administrator unlocks it or the server is rebooted.  

Google appears to suggest it's possible, but all the information I find seems to suggest editing a /etc/pam.d/system_auth file.  I have the /etc/pam.d folder with files in it, but no system_auth file.

Can someone list out the steps necessary to accomplish this in Ubuntu?

---

### Post by Dave_Connor on 2008-12-28
If it is ssh access there is denyhosts and you can configure it to only allow 3 times before there ip is placed into hosts.deny and denied access until there ip changes or the administrator edits the denyhosts logs and unblocks them.

---

### Post by Kissell on 2008-12-29
No, I meant to say when someone is physically sitting in front of a terminal and logging into Ubuntu gnome desktop...  I want to kill their account if they keep guessing at the password.

---

### Post by Dave_Connor on 2008-12-29
With some help with google. This may be what you are after ?
[http://www.cyberciti.biz/tips/lock-unlock-set-number-of-login-attempts.html](http://www.cyberciti.biz/tips/lock-unlock-set-number-of-login-attempts.html)

---

### Post by Kissell on 2008-12-29
Yeah, that's what I was talking about in the orignal post...  All the google answers seem to say it can be done, by editing this system_auth file...  but on Ubuntu version of linux there is no system_auth file in the /etc/pam.d folder.

---

### Post by Kissell on 2008-12-29
Ah, got it working...

In Ubuntu, the file is named:
> /etc/pam.d/common-auth

instead of:
> /etc/pam.d/system-auth

I had guessed this earlier...  but it failed to work as a substitute...  this is because I followed the directions and appended this code to that file.
> auth required pam_tally.so onerr=fail deny=5 unlock_time=21600

however, that isn't what you need to do to make it work...  that code must appear BEFORE the other codes in the file...  so don't append it to the end, instead put it at the beginning, and now it works!

Thanks for holding my hand, I couldn't find a clear answer on this anywhere.

---

### Post by Dave_Connor on 2008-12-29
Your welcome. Glad you got it to work. Don't worry about it, at one point all of us needed some help with one thing or another with Linux.

---

### Post by Kissell on 2008-12-29
Just a few more helpful notes, for future readers.

I added "even_deny_root_account" to the line in the common-auth file, because if you don't do this, then anyone can sit there and hack away at the root account with unlimited guesses.  

Also, you can see how many failures on your user by using
> pam_tally --user root

and you can reset the failures to 0 with 
> pam_tally --user root --reset

NOTE: I have Hardy and Intrepid machines, and have tested this on both...  it appears that in Hardy when you login successfully the count gets reset to zero (as it should).  But in Intrepid it doesn't, even though the "no_reset" flag is not set.  

Ubuntu Hardy and Ubuntu Intrepid are a little different in a few other respects...  The default Hardy common-auth file is much smaller that Intrepids... 

One last thing, this is PAM's common-auth, so it doesn't just secure against incorrect login attempts from the gnome login at the PC..  it protects against failed login attmepts on anything that uses PAM.  So if you do "su - root" and you guess it wrong it will increment the failed login tally for root, and a very interesting thing, that tally seems to remain (at least on Intrepid) after you reboot...  but, even if root is locked, you can still use sudo.  So this doesn't seem to add much danger or complexity, but certainly does add a lot better security than the defaults.

---

### Post by Kissell on 2008-12-29
Oh, and one other important thing...  these changes are LIVE.

When you edit the common-auth file you don't need to logout or reboot, as everytime something needs a password and asks PAM to handle it, the common-auth file is read at that point...  so rebooting or logging out to test this is a pointless waste of time.  (unless your trying to see if the tally remains after reboot, i haven't tried that with hardy yet)

---

### Post by bodhi.zazen on 2008-12-29
don't forget, that unless you encrypt your installation, physical access means I can change your password with a live CD.

And as others will point out, not even encryption is perfect, but it goes a long ways.

---

### Post by Kissell on 2008-12-30
Yeah, I would like to learn more about how to encrypte the boot partition...  currently I've just recently gotten into encrypting my data partition with cryptsetup (luksformat and AES encryption)... but your right, that just protects my data...  someone could come along with a live CD and gain access to my system, and I'd prefer they didn't.

---

### Post by bodhi.zazen on 2009-01-01
The boot partition is not encrypted and that is probably OK.

IMO the easiest way to install an encrypted system is to use the alternate CD.

---

### Post by needlez6 on 2011-03-14
Hi, i need to know if I can make it so it doesn't reset automatically after the correct password has been input. The reason for this is I have a script that runs at startup that grabs the pam_tally for the user and puts it to a log file. I would like this to work correctly, so I need for it not to reset til after I tell it to, not automatically. Thanks for any advice.

---

### Post by user2037 on 2012-06-28
This doesn't seem to work with Ubuntu 12.04. Anyone know how to do it?

---

### Post by oldos2er on 2012-06-28
Old thread closed. Instead of bumping old threads, please start a new one if you have a question or problem.

---

