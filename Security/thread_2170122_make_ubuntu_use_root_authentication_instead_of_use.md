---
title: "make ubuntu use root authentication instead of user"
date: 2013-08-25
forum: Security
---

### Post by AENHYQp on 2013-08-25
i know this might raise a lot of eyebrows from ubuntu fans (a lot of  "why"s), but i was wondering if it were possible to make ubuntu use root  authentication instead of user, for administrative access (such as  software installation and system administration), like fedora does.

 i  like ubuntu's software selection and LTS, but i'm a die hard fan of  "users are users and only root can do certain things". i ALREADY have it  setup so that i can "su -" into root, but i would love it if all of the  authentication popups asked for ROOTs pwd instead of MINE. i've been  using xubuntu for a couple/few years now, and i STILL type  root's pwd to  grant access to dialogs, only to realize that i'm not in  kansas any  more.

i miss the "server admin" feel. i was thinking about switching back to fedora, now that i know that i don't need compiz any more for a desktop cube etc (thanks to KDE's tremendous progress), and now that fedora has caught up in terms of software package offerings, but, i still like th LTS support of *buntu, so, i figured i'd see if this were possible before giving fedora more consideration.

thanks in advance.

---

### Post by carl4926 on 2013-08-25
AFAIK [FONT=sans-serif][COLOR=#000000]sudo has completely supplanted the superuser login for administrative tasks in ubuntu.[/COLOR][/FONT]
[FONT=sans-serif][COLOR=#000000]Which makes it inherently less secure than say: Fedora or openSUSE, that have different passwords for users and root.
Which means you should absolutely make sure that your Ubuntu password is not shared
What exactly do you think you can't do, that you could otherwise given your suggestion[/COLOR][/FONT]

---

### Post by 1clue on 2013-08-25
Yes it is possible.  You're not going to get help on this forum though, because I believe that helping somebody run in that way is against forum terms of service.

Speaking as somebody who has used literally dozens of Linux distributions, the way Ubuntu sets you up to never have to log in as root is one of the top 5 reasons I use Ubuntu.

Personally I'm of the school that nobody should know the root password.  Ever.  This comes from years of administering systems where more than one employee who had root access was fired for some sort of bad behavior.  With Ubuntu we just disable one user, with anything that does it old school you have to change all the root passwords they had access to, and then tell the people who need access what the new one was, and probably explain why the guy was fired in the first place, and why they shouldn't share the password with anyone.

I suggest that if you want the "server admin" feel then you should go load Debian.  Or Fedora.

---

### Post by CharlesA on 2013-08-25
I don't know of any way to do that for the gui. It looks like you are already using su to run as root for other things, but I don't know if Ubuntu is coded to let you do what you want to do.

I'm not even sure if Debian can do that.

With that being said, I run debian boxes on my server, so I deal with the whole su to root stuff all the time. It gets messy when more than one person has root access and even messier when one of them gets fired, as 1clue pointed out.

---

### Post by 1clue on 2013-08-25
You could undo all the work Ubuntu did to make it work without the root user.  The source code is available in Debian repo, if you know what packages are involved and know how to use diff appropriately then you can get there.

So yes you can do it.

---

### Post by Bucky Ball on 2013-08-25
***Thread closed***

***Reason (from the forum guidelines):***

> Never instruct users to do anything that might break their system.

Instructing you how to login as root definitely falls into this category. Besides, you will find that you can easily break your system (without trying too hard) beyond repair by using sudo as a regular user.

<snip>

---

