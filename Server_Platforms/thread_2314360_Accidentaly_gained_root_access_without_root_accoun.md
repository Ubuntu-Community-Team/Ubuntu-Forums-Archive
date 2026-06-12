---
title: "Accidentaly gained root access without root account login enabled."
date: 2016-02-20
forum: Server Platforms
---

### Post by hoboCoder on 2016-02-20
Hello Ubuntu community.  I have stumbled across an issue and i'm not exactly sure how to go about it.  I'm gonna give some details and hopefully someone can point me in the right direction as to what to do next.

I recently installed ubuntu server in VirtualBox as an experimental home server (Windows 10 host). and it had been a few years since I have even seen a terminal login let alone use one or keep up with the changes (last linux installation was feisty fawn!).  So I was trying to research how to login as root so I could do some post install tasks as root instead of sudo everything.  I found out that root is not enabled by default so I decided to just adapt to that because its obviously good practice so I didn't change anything.  However I made a mistake running a command with sudo and next thing I know I see ```
root@server-name ~$
``` 
Now imagine my surprise as I couldn't 'sudo su' or login as root with any old fashioned ways because the user account isn't enabled! I'm not going to publicly post how to replicate the procedure, so I'm wondering a few things:

[LIST=1]
[*]is it even a bug or is it default behavior?
[*]Now that it has logged on as root is the root account enabled now? (I just shut the server and VM down and came over here to ask before even doing anything else)
[*]Is there a more appropriate place to report it or post how to reproduce it?
[/LIST]
Thanks in advance for reading, I apologise for not being sure what I should do without involving more people than are necessary.

---

### Post by potato5 on 2016-02-20
I did not quite understand.
 Maybe you are talking about *sudo -i*?

---

### Post by hoboCoder on 2016-02-20
No, I'm talking about root user not being enabled so I was trying sudo su because I thought I remember using that in the past to login as root. Like I said it has been years since Ive used linux so my commands are rusty and I wasnt very experienced at my peak! Either way I couldnt login as root from my memory so i started googling how, thats when I found out that Ubuntu 14.04 lts has root login disabled by default.  The main point is I couldn't login as root when I was trying to, then accidentally logged in as root not even trying to change users or run any complex commands.

---

### Post by darkod on 2016-02-20
Well, I don't know what you actually did but the root account can be enabled. It comes disabled by default in ubuntu but it still exists in a way. Otherwise you couldn't be able to run commands as sudo either.

So if what you did is the same or similar to that procedure, yes, you enabled the root account (even without wanting to)...

---

### Post by steeldriver on 2016-02-20
I think perhaps you're just misunderstanding what "disabled" means in this context. As noted in the manpage for 'shadow':

```

           If the password field contains some string that is not a valid
           result of crypt(3), for instance ! or *, the user will not be able
           to use a unix password to log in ([B]but the user may log in the
           system by other means[/B]).

```

In this case "other means" includes things like 

```

sudo -i

sudo -s

```

and 
```

sudo su

```

and even login via SSH if an alternate authentication mechanism (such as RSA keys) is configured (although it *does *prevent plain su)

---

### Post by hoboCoder on 2016-02-20
Thanks for the replies, I'm sorry for my poor use of vocabulary, when I was saying the root account was disabled, what I really meant was root login was disabled, as in I can't/shouldn't be able to gain control of the root account and directly access the system AS root and not THROUGH root i.e. sudo. (or sudo su, or sudo -i)
because the root account shouldn't be able to login to the machine directly, but instead indirectly through another user with elevated privileges.

[Ubuntu wiki page RootSudo]("https://help.ubuntu.com/community/RootSudo") says:
> **By default, the root account password is locked in Ubuntu.** This means that you cannot login as root directly or use the su command to become the root user.

However I did without enabling the root password, using the shutdown command, but after reading more about the command I learned that it did what it is supposed to, however I was under the impression that it wasn't supposed to be able to login as root, but the the init(0) signal to the system and watch it go!

Also on that wiki page it says it is possible (with init(8)?) and "setting a root password, a boot loader password and a BIOS password" will be necesary to increase security and/or prevent automatic (no password as is default) root login.

Whew! anyways I'm glad I jumped down this rabbit hole and followed it! Thanks all for your replies. This was just pure ignorance on my end and thanks all for helping me understand what was happening.

---

