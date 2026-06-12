---
title: "Screensaver unlock won't accept password"
date: 2008-10-12
forum: Security
---

### Post by Oracle_The_Blind on 2008-10-12
I'm having a rather annoying problem with my Ubuntu system that has just arisen 2 days ago.

Whenever my screen saver activates (after 10 minutes idle or after Ctrl+Alt+l) the password dialogue is displayed when I try to use the computer.  This dialogue looks just the same as it always has, except that it is completely unwilling to accept my password.  It prints "checking" for about 3 seconds then vibrates a bit and prints "incorrect password."

I am however certain that my password is correct as I am able to click "switch user", type in the same username and same password and it works.  Also, I am able to log into a tty with the account.

The only related change that I can recall making to my system in the past few days is changing the login screen theme.  But this should not effect the screen saver unlock dialogue.

Any help on getting my unlock box to accept my password would be much appreciated

---

### Post by Oracle_The_Blind on 2008-10-16
Bump?

The problem remains and it is really bugging me that an integral part of my operating system (the password authentication part) is not working.
There may be an underlying security issue that I **must** correct.

If anyone has any ideas, please post.

---

### Post by chuckp123 on 2008-10-16
This just started happening recently for me as well.  Must be caused by one of the recent updates.  It is EXTREMELY annoying.

---

### Post by gtdaqua on 2008-10-17
could it be a keyboard error? when using vmware-server-console, the shift/control/alt keys stop working. So if you accidentally lock-up and try unlocking it wont accept the password if it has special characters. You have to run the 'setxkbmap' command to reset your keyboard.

---

### Post by Oracle_The_Blind on 2008-10-18
Interesting theory, and yes my password did contain special characters.
However, after running the command, the problem remained.  Also, once the screen is locked, there is an optional titled "leave message" (or something to that effect) and when I click than and then type out my password, it comes out correctly in clear text.
Furthermore, I set my password to 12345678 in an attempt to see whether the error was indeed caused by a complex password, and once again the unlock dialogue did not accept the password.

Any more ideas would be much appreciated.  I still have all Hardy updates applied.

---

### Post by victorgreen on 2009-05-06
This just happened to my laptop, newly upgraded to Jaunty 64. The dialog is stuck on "checking" for several minutes and then, without saying wrong password, returns the blank enter password dialog again, upon hitting swtich user i try to log in with the same user and its still stuck on the gdm login screen. and now it just turned itself off wiht no explanation

Im very confused- this is makign my laptop unusable

---

### Post by skksuf on 2009-10-10
From a different thread - here is what worked for me and kind of makes sense - the /etc/shadow file needs the right permissions to allow the /sbin/unix_chkpwd to read it.

[http://ubuntuforums.org/archive/index.php/t-804647.html](http://ubuntuforums.org/archive/index.php/t-804647.html)

I quote:
Rogerborg
September 15th, 2009, 04:57 AM

Yup, this bug is still extant in 9.04. The stock install was fine, but somewhere along the way, my /etc/shadow has become root:root and 0400.

I'm not sure what's causing it.  Running useradd sets the permissions to 0440, but doesn't touch the permissions.

sudo chown root:shadow /etc/shadow
sudo chmod 440 /etc/shadow

fixes the screen unlock problem for me in 9.04.


 <li class="empty">

---

### Post by victorgreen on 2010-04-22
Some of the time this happens is cause I have it switched to my Hindi keyboard layout... but that one time, it did indeed simply refuse to recognize my legitimate password.

---

### Post by garvinrick4 on 2010-04-23
> **Oracle_The_Blind said:**
> I'm having a rather annoying problem with my Ubuntu system that has just arisen 2 days ago.

Whenever my screen saver activates (after 10 minutes idle or after Ctrl+Alt+l) the password dialogue is displayed when I try to use the computer.  This dialogue looks just the same as it always has, except that it is completely unwilling to accept my password.  It prints "checking" for about 3 seconds then vibrates a bit and prints "incorrect password."

I am however certain that my password is correct as I am able to click "switch user", type in the same username and same password and it works.  Also, I am able to log into a tty with the account.

The only related change that I can recall making to my system in the past few days is changing the login screen theme.  But this should not effect the screen saver unlock dialogue.

Any help on getting my unlock box to accept my password would be much appreciated Password incorrect I do not know but go to screen saver and
uncheck the box "lock screen when screen saver is active and that will cure that.

---

### Post by garvinrick4 on 2010-04-23
Wow is this and old thread or what!! How did I get here.

---

### Post by CharlesA on 2010-04-24
Someone resurrected it, of course.

---

### Post by yolucid on 2010-06-06
> **skksuf said:**
> 
sudo chown root:shadow /etc/shadow
sudo chmod 440 /etc/shadow
 

its work for lucid, thanks.

but just curious, the thread [http://ubuntuforums.org/showthread.php?t=1006366](http://ubuntuforums.org/showthread.php?t=1006366)

states chmod 640 instead of 440, what's the different?

---

### Post by FemmeFatale on 2010-06-07
I had the same problem, however, it was not desktop-lock issue, rather initial login one. I fixed that by closing gdm and login using console.

---

### Post by haulbag on 2010-11-28
> **skksuf said:**
> 

sudo chown root:shadow /etc/shadow
sudo chmod 440 /etc/shadow

fixes the screen unlock problem for me in 9.04.



I could be wrong, but I believe that both the /etc/shadow and the /etc/gshadow files need to be owned by root:shadow and they need to be chmod 640. Otherwise, with the permissions at 440, root won't be able to update passwords for users. 640 is the original setting for the files when Ubuntu gets installed.

This same problem came up for me after I installed several new machines and copied (as root) the /etc/passwd, /etc/shadow, /etc/group, and /etc/gshadow files from an old machine to the others. When you copy a file as root, the file ownership changes to root. The solution, of course, is to use "cp -a" instead of plain "cp" when you copy the files in order to preserve the file ownerships.

---

