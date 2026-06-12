---
title: "Login does not work with usual password."
date: 2015-07-19
forum: Security
---

### Post by janeku2 on 2015-07-19
I must upgrade this situation regarding latest security info breaches.
Yesterday (18.july.2015) 14.04 made some upgrade and I was working some Internet search.
I did not nothing regarding my passwords or similar.
This afternoon (19.july.2015) after boot, at login sequence I just couldn't log in with my usual password.
I tried everything even with my root password. I just couldn't log in.
I use my active (now inactive) Guest login to check how to bypass this problem. 
After managing this I tried to see what was the cause for this searching for web but no answer.
So, I disabled guest login for secure reasons but did not disable guest user (make it inactive).

When I type cut -d: -f1 /etc/passwd in terminal i got a list of users that has already passwords.

It is interesting that login user has 5-6 users as listed:
guest-P47Uco
guest-M6i2OP
guest-Rt0ABD
guest-P9tfEJ
guest-LY2E2A
guest-KvN08K
guest-5qGX3Y
guest-pQxWJw
guest-JnnnS4


Is it possible that somebody has been using these users to enter my computer or somehow latest update made mess in passwd data ???

Regards,

---

### Post by NoWayWin8 on 2015-07-19
Those are normal looking guest account names, it's a new one every time you use guest.

---

### Post by janeku2 on 2015-07-20
If they are normal loging user accounts, how it happened I can;t login to my account without change anything ?

---

### Post by Dreamer Fithp Apprentice on 2015-07-20
You ignored all but my first question.
_________________________________________________________
INSERTED LATER WITH EDIT FUNCTION:
Mea  culpa. I'm mistaken. I confused janeku2 with the original OP. See  Coffeecat's post immediately following this. What follows is still relevant to this thread. Thanks to Coffeecat for de-confusing me.
----------------------------------------------------------------------------------------------------

But if the situation has deteriorated further since then, as you describe:> **janeku2 said:**
> This afternoon (19.july.2015) after boot, at login sequence I just couldn't log in with my usual password.
I tried everything even with my root password.it may be easier to reinstall than to fix this. Nevertheless:
1. If this is a normal 'buntu installation you shouldn't even HAVE  a root password. If you enabled it, I don't blame you, but anything out of the ordinary should be clarified.
2. If you are failing to login with the "display manager" (a graphical thing - not a command line) you might try control-alternate-F3. If that gets you a console with "login:" prompt, you can login there and correct things from there. If you can get that console (and I'm not sure you can) and you can either login as your normal user and then use sudo with your sudo password, or, if you indeed have the root password enabled, login as root instead, you should be able to add a new user account and set its password. If you get that far, you can find the proper commands easily enough with a search engine. Try "ubuntu create user set password command line" as a search string. If that doesn't fix it, it could be that the display manager is corrupted and you could try reinstalling it.

In any case, if this all came up spontaneously, with no other plausible cause, I'd be worried about the hard drive. You might want to be extra careful to back up your data.

---

### Post by coffeecat on 2015-07-20
@janeku2, I have moved your posts and their replies to their own thread. Please do not hijack another person's thread, but start your own, even if you think the problem is the same. Often it isn't and helping more than one person with different issues becomes very confusing.

@Dreamer Fithp Apprentice, the questions you asked were directed to the OP of the original thread, here:

[http://ubuntuforums.org/showthread.php?t=2286774](http://ubuntuforums.org/showthread.php?t=2286774)

---

