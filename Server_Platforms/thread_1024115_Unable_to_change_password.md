---
title: "Unable to change password"
date: 2008-12-28
forum: Server Platforms
---

### Post by ooobooontooo on 2008-12-28
Hi,

So I recently downloaded the server version of Ubuntu. I had a couple questions I wanted to ask about it... First, I seem unable to change the password on my server. Whenever I type passwd, it just prints out
> passwd: password updated successfully
It doesn't wait for any input, that's what it prints out.

Also, whenever I log on to the server by use of keyboard and screen (not ssh), it doesn't ask for my user's password and I can sudo stuff without putting in my password. Is that because I didn't set the password for the root? Because in my desktop version, it asks the password of the user with administrative powers before it sudoes anything. Thanks in advance.

---

### Post by spiderbatdad on 2008-12-28
are you logged into the root account? Sorry I have not seen this behaviour

---

### Post by ooobooontooo on 2008-12-28
Yes I can su...but it lets me in without prompting me for a password and when I try the passwd command as the root, it says the same thing.

passwd: password successfully updated.

EDIT: I am not logged in as root. What do you think reinstall?

---

### Post by joebeasley on 2008-12-28
Did you try sudo?

sudo passwd username

---

### Post by ooobooontooo on 2008-12-28
Yes I did.

EDIT: Also, if you're changing your own password, I thought you didn't need to put sudo?

---

### Post by RealPSL on 2008-12-28
Something is definitely broken there. Changing your own password does not require the use of sudo. There may be something wrong with the configuration of PAM in /etc/pam.d. Please provide the output of ```
cat /etc/pam.d/passwd /etc/pam.d/common-password
```

---

### Post by Iowan on 2008-12-28
If you're changing your own password, you *shouldn't* need **sudo**.  My server has no root account enabled, it requires **sudo** to do "root" things.  It _will_ remember **sudo** being issued for awhile (not every back-to-back command requires **sudo**), but the first attempt requires a password entry.

---

### Post by melojo on 2008-12-28
I had the same problem one time but it was because I unlocked the root account and gave root the same password as my user name.

can you post the contents of the file /etc/group

you can change your username in the file with characters.

---

### Post by ooobooontooo on 2008-12-29
@RealSPL
Yeah you're probably right. Something has to be wrong with the passwd program. /etc/pam.d/passwd just includes /etc/pam.d/common-password.
For /etc/pam.d/common-password:
```
# here are the per-package modules (the "Primary" block)
password [default=1] pam_permit.so
# here's the fallback if no module succeeds
password requisite pam_deny.so
# since the modules above will each just jump around
password required pam_permit.so
```
The rest of the file is just comments

@Iowan
Good that's what I thought. Thanks.

@melojo
I didn't assign any password to root at this point and they really have nothing in common. Why did you want me to post /etc/group?

Thanks all for looking into this. I think I might just reinstall if this doesn't get fixed soon. I mean I just installed the Server, so it won't take much work to just start from beginning. Thanks.

---

### Post by Iowan on 2008-12-29
Re-installing is an option... [This]("http://ubuntuforums.org/showthread.php?t=1010875") thread/post discourages us "advice-givers" from using re-install as a first line of defense.

---

### Post by ooobooontooo on 2008-12-30
Haha. Excellent post. It's just that if passwd program failed to install properly, other things could have also failed. That's why I want to reinstall. I mean it broke out of the box...that's a good sign for reinstall isn't it? Hehe. I'm from the Microsoft world. Oh how I wish I had Ubuntu for my first OS.

---

### Post by grep65535 on 2009-01-05
I'm having this same exact issue with Ubuntu 8.10 x64
My root password was set to something that is *not* the same as a user account.  I'm able to use sudo to *be* root, but I can't change the password not matter what I do for the same reason, it doesn't ask for one.

I had Ubuntu 8.10 x64 installed previously on this computer without issue, so something is different obviously.

Still 'reinstall' as the only suggestion?

---

### Post by ooobooontooo on 2009-01-05
Seems like it. I did post my pam.d files, but no one answered much. I haven't actually reinstalled, so I don't know how it will work out.

---

### Post by madsath on 2009-04-08
well came across the same problem
if u have likewise-open installed u will not be able to enter any new local passwords.
solved it by removing the server from domain
remove likewise 
passwd works fine
reinstall likewiser

hope it helps

---

### Post by zeki893 on 2009-04-10
I ran into the problem too. Listen to the post above. 
To make it easier for the nubs go into recovery mode and run this
```
apt-get remove likewise
```

---

### Post by ooobooontooo on 2009-04-11
Thanks. I'm not sure if I had likewise installed though because it was clean install except opensshd. Anyway, I reinstalled and it worked. Like I said before, I was afraid that some other parts might've broke on the initial installation. Thanks for the advice though.

---

