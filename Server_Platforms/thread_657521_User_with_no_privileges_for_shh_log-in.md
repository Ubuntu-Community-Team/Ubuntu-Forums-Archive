---
title: "User with no privileges for shh log-in"
date: 2008-01-03
forum: Server Platforms
---

### Post by cOmOneO on 2008-01-03
Hello :)
I have just gotten myself a new dedicated server!!!! :D (sry just needed to get it out, its so nice :P )

Well, as most of you know it is not a good idea to allow root to login via shh and the idea of forcing any bad-guy to brute-force two password instead of one is making me smile a little, but I came to think of what the bad-guy could do with just the normal user, if he got that far. It would certanly not be as bad as if it were the root account, but still...

So since i normally only work on my server as root (as i suspect must others do to) why not make a user that can do absolutely nothing except su into root?
I have googled araound but cant seem to find anything, so I thought that maybe some of the bright heads at ubuntuforums had the answer.

So boys and girls... Is it a good idea and is it even possible, and if so, how?

:)

---

### Post by Rizado on 2008-01-03
First thing to do if you are concerned about ssh security is to use public key authentication: [http://ubuntuforums.org/showthread.php?t=137746](http://ubuntuforums.org/showthread.php?t=137746)

---

### Post by cOmOneO on 2008-01-03
Ah... ofc, well its late :S

Was just a thought I had when setting up the new server, and got so excited that i totally forgot about that (not that I am an expert, but I have been thinking about using such a key for a while).

In fact, I got so excited that 20 seconds after posting here, I managed to disable root ssh login and reboot the server without creating a new user to log in with first :S

Not my best of days today...

But thanks for the reply :D

/me crawls to bed mumbling something about already hating dediacted servers, and not being able to just throw a new ubuntu cd in the beast and GO!

---

