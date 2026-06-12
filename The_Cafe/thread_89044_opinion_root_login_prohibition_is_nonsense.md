---
title: "opinion: root login prohibition is nonsense"
date: 2005-11-11
forum: The Cafe
---

### Post by jeffjanzen on 2005-11-11
i don't understand why no one is supposed to log in as root for everyday computer usage.  i log in as 'jeffjanzen' (partly because ubuntu's default is to PROHIBIT me from logging in as root) and it seems like i have to enter my password 20 times every day, to do *normal*, everyday things like downloading updates.  i do it every time i'm prompted to, without giving much thought to it.  it's automatic.  if i'm going to break something, i'm going to break something.  this nagging prompting doesn't protect me.  this nonsense of discouraging everyone from logging in as root MUST STOP!

---

### Post by TravisNewman on 2005-11-11
there are countless studies and articles showing why logging in as root for everyday usage is a very, very bad idea.

Read this, for a start:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by blastus on 2005-11-11
If you need to or must run apt-get everyday, then setup a cron job to do it. I've only been using Linux now for about 3 months and honestly haven't had the need to have root credentials for much of anything on a daily basis. There is a way to enable root login in Ubuntu though--I don't remember what the procedure is.

---

### Post by 23meg on 2005-11-11
If you want trouble, here's the way: System / Administration / Login Screen Setup / Security / Allow root to login with GDM.

---

### Post by TravisNewman on 2005-11-11
the procedure is "sudo passwd root"

but it's a bad idea.

---

### Post by Sheco on 2005-11-11
If you run ALL of your apps as root, you deserve to be owned, using a user account and not root is like "guilty until proven otherwise", don't trust any app unless you really want it to have full control on your PC (just saying that sounds dangerous)

Security on linux dwells on the fact that you can't run apps and have them write all over the place, if you get infected, your user account will be infected and it wont propagate. That's one of the reasons linux doesnt have viruses running wild (the other reason beeing that windows has most of the marketshare and virus writters focus on them)

---

### Post by stimpack on 2005-11-11
There are 380+ distros where you can do that, why choose one where no root is an integral feature? Its like going onto gentoo forums and saying emerge has to go.

---

### Post by drogoh on 2005-11-11
[QUOTE=jeffjanzen]i don't understand why no one is supposed to log in as root for everyday computer usage.  i log in as 'jeffjanzen' (partly because ubuntu's default is to PROHIBIT me from logging in as root) and it seems like i have to enter my password 20 times every day, to do *normal*, everyday things like downloading updates.  i do it every time i'm prompted to, without giving much thought to it.  it's automatic.  if i'm going to break something, i'm going to break something.  this nagging prompting doesn't protect me.  this nonsense of discouraging everyone from logging in as root MUST STOP![/QUOTE]

If you read about sudo you can solve all of your gripes.  I won't tell you how, but you can edit your sudoers entry to not ask for a password.  Just, uh, don't expect any warranties, and you're on your own.  I'm just letting you know something exists.

---

### Post by Kvark on 2005-11-11
If you surf the web as root and a website would manage to hijack Firefox, that website would have complete control over your whole computer. Or if you read a word document with a macro virus (ok Open Office prolly doesn't get pwned by word viruses but if it did) it would aslo have just as much control over your computer as the kernel does. Some cool xchat script a chat buddy gave you would aslo have full rights. And whatever silly low quality game you try when you're bored too.

To log in as root for daily useage and thus give all apps unlimited power over your computer seems like an open invitation to viruses and trojans.


So the password nags wouldn't make you think twice before breaking something, what would make you think twice?

---

### Post by majikstreet on 2005-11-11
[QUOTE=Kvark]If you surf the web as root and a website would manage to hijack Firefox, that website would have complete control over your whole computer. Or if you read a word document with a macro virus (ok Open Office prolly doesn't get pwned by word viruses but if it did) it would aslo have just as much control over your computer as the kernel does. Some cool xchat script a chat buddy gave you would aslo have full rights. And whatever silly low quality game you try when you're bored too.

To log in as root for daily useage and thus give all apps unlimited power over your computer seems like an open invitation to viruses and trojans.


So the password nags wouldn't make you think twice before breaking something, what would make you think twice?[/QUOTE]
Exactly.

There are **TONS** of articles on why not to log in as root. Google it.

Anything that you get on your computer would have COMPLETE CONTROL!

---

### Post by aysiu on 2005-11-11
Dude, use *any* other distro. Almost every other Linux distro has a separate login you *can* use. If you use Linspire, you don't even have to create a single regular user account. Ubuntu does things a certain way and I (and others) are happy with that way. If you want to change it, you can change it. If you don't, use another distro.

---

### Post by Brunellus on 2005-11-11
No, it mustn't stop.  

Think about it like this.  When you run a program as a user, that program has access only to those resources the user is permitted to access.  Should anything go horribly wrong, it is easy to terminate that program (and only that program) or log off that one user;  the rest of the system keeps on ticking.

This has a further benefit of preventing programs from using resources they have no business using.  

Think of processes as servants in a big house, which is your computer.  The gardener has no business in the master's study, reading his bank statements.  But when you run as root, you're giving a motley lot of servants the run of your estate.  Many of those servants are good, loyal, reliable types, who carry on cooking, cleaning, dusting, gardening, and so forth without worries.  But without keys, locks, or even rules restricting who is supposed to be where, it is entirely possible for the gardener to walk into your study and make off with your bank details, and possibly buy himself a stately home of his own after he's bled your accounts dry.

In actual, daily use, I very seldom have to do anything with root permissions, anyway.  Once I have the computer set to how I intend to use it, it stays stable.

---

### Post by fuscia on 2005-11-11
[QUOTE=panickedthumb]the procedure is "sudo passwd root"

but it's a bad idea.[/QUOTE]

it can be done. so, just do it.

---

### Post by poptones on 2005-11-11
folks... the OP in this discussion has all of seven posts here... it's not prudent to be **too** emphatic in your replies.

And I will point out one fallacy: this whole thing about "being owned." Of course there is a risk of it, but most of the cracks I have seen exploited in the wild don't care one whit if you are loged in or not, or what your permission is - because they enter the system via "back doors" and install rootkits and other subversive management tools. 

Not logging in as root protects your system from you, not from someone who intends you harm. But what's the big deal with having to type your passphrase a few times a day?

---

### Post by jeffjanzen on 2005-11-12
i guess it helps to think of the security issue in terms of the privileges granted to the *programs*, instead of the privileges granted to the *user*.  thanks, everyone, for your replies.
i hope i never use a program that bypasses the root login through a 'backdoor' to do something malicious.
p.s. i wouldn't think of switching distros over this small problem.  i'm generally very pleased with ubuntu.

---

### Post by Qrk on 2005-11-12
Sorry for the flames.
I didn't like it at first, but now I respect the status of root in ubuntu. When I tried Ubuntu, the first thing I did was enable root to log in, (warty). Now I use the default behavior. 

It can be a little anoying, but its still better than running three different antivirus and spyware programs in windows. Also, its much better to be asked for a password because you know that whatever your doing next is a system wide change. Logging in as root, even once in a while to change your system, can be very dangerous if your new.

---

