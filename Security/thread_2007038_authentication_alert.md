---
title: "authentication alert"
date: 2012-06-20
forum: Security
---

### Post by Shakey Hands on 2012-06-20
ok two problems, they may be related.
[COLOR=Red]
1[COLOR=Black]- first i downloaded a bunch of ubuntu updates[/COLOR][/COLOR] (via the automatic notifier). Now my operating password does not work. 

i made this discovery when attempting to download a new software package. i was asked for my password, but it didnt work. i tried several times. then tried other packages, then tried to open the synaptic package manager. at all points i was asked to type my password, the computer failed to recognize it. 
'Your authentication attempt was unsuccessful'.

ok, i know my password. ive used it for years. it was authenticating fine before the updates occurred. 

[COLOR=Red]2[/COLOR]- evertime i turn on my computer/login i am given this message from ubuntu. 

'Enter password to unlock your login keyring

The login keyring did not get unlocked when you logged into your computer'

to which i type my password. it happens about 30 30 seconds after ubuntu has finished start up, and im free to do what i like. its been happening for a few days.

are the two related? etherway they are both very serious issues.

---

### Post by OpSecShellshock on 2012-06-20
Problem 2 occurs usually when people have their system set up to log in automatically OR when the login/user account password is different than the keyring password. This can happen when people change their passwords using the "passwd" command because the keyring will still be using the old password.

The first problem I'm not so sure about, unless the user account password was somehow changed (which usually wouldn't happen without you knowing) or you are logged in with an account that is not privileged.

---

### Post by Shakey Hands on 2012-06-20
ok thanks [SIZE=3]OpSecShellshock[/SIZE] your answer to the second prob sounds like it could be right. i do auto log in. ill look into it.

but what about the first prob. its a pretty serious matter. is their a official ubuntu support?

---

### Post by Ms. Daisy on 2012-06-22
If the password was somehow changed or you don't know it, then you could reset the password in Ubuntu:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

That should fix the problem.

---

### Post by Shakey Hands on 2012-06-26
> **Ms. Daisy said:**
> If the password was somehow changed or you don't know it, then you could reset the password in Ubuntu:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

That should fix the problem.

tthanks for the suggestion ms. Daisy

i tried your idea and everything went fine up to a point. 
- i entered the knew password
- then re-entered it
- at this point the process failed, i received the message. 

passwd: authentication token manipulation error

???

---

### Post by steeldriver on 2012-06-26
did you remember to include this step?
> In recent versions of Ubuntu, the filesystem is mounted as read-only, so  you need to enter the follow command to get it to remount as  read-write, which will allow you to make changes: 

```
mount -o rw,remount /
```If that's not it, there are a few more suggestions here:

[http://askubuntu.com/questions/91188/authentication-token-manipulation-error](http://askubuntu.com/questions/91188/authentication-token-manipulation-error)

---

### Post by Shakey Hands on 2012-06-26
haha! yes your right. i did forget that step, yep im an blind idiot.

everything worked. now i actually have control of my own computer again.\\:D/

thanks heaps, your all geniuses! =D>

so should i be worried/consider it important to change the read/write back to read only? or WAS the problem that somehow the read write was changed to read only?

---

### Post by steeldriver on 2012-06-26
no that's fine - as soon as you restart into regular mode the filesystem is mounted read-write - it's only in the recovery console that "/" is read-only

---

