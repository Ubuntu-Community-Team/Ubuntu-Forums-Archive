---
title: "gitosis asks for some password"
date: 2011-02-09
forum: Server Platforms
---

### Post by baltic on 2011-02-09
[FONT=Arial]Hi!

I am trying to follow the instructions at [https://help.ubuntu.com/community/Git](https://help.ubuntu.com/community/Git) but after the [/FONT]
git clone [EMAIL="gitosis@yourserver.com:gitosis-admin.git"]gitosis@yourserver.com:gitosis-admin.git[/EMAIL]
[FONT=Arial]
step, i'm getting a prompt, asking for a password. What is the password could be, and why would it ask it at all?

Thanks[/FONT]

---

### Post by juicybananas on 2011-09-20
I just followed the instructions from the link you gave and have come across the same problem. I assumed when I setup gitosis with my pub key that the password was the actual "passphrase" for my key but that is not the case.

I have created a key on my Mac to ssh into my ubuntu server and initialized gitosis with that pub key I copied over to no avail.

I then created a pub key locally on my ubuntu server and initialized gitosis with THAT pub key (with no passphrase) to no avail.

I then changed the password (passwd gitosis) as root for user gitosis to no avail.

No avail = prompted for password when cloning gitosis-admin as user gitosis and password not accepted.

BTW: putting "AllowUsers gitosis" in your sshd_config; not a good idea. Broke my openssh server. Fixed it by removing that line.

---

### Post by juicybananas on 2011-09-20
Crap, I just noticed the instruction say "...local machine..." so I am cloning the git-admin FROM the ubuntu server TO my Mac (in this case). Hence the use of the pub key from the mac.

Wow....that part should be bolded for us after hours geeks.

---

