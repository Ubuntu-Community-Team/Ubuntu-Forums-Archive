---
title: "X.Org 6.9/7.0 RC1 available.."
date: 2005-10-19
forum: Requests
---

### Post by darius779 on 2005-10-19
RC1 has been released (announcement pending).  I would really like to see this as a backport for breezy to test some of the nifty new features. 

Im fairly certain that I would break my machine if I tried to install it from scratch. :)

---

### Post by JuanC on 2005-10-19
I also like to include these packages into breezy backports , because i couldn't get 3d accel into my ATI card with actual xorg packages ....

---

### Post by SSTwinrova on 2005-10-19
I think this is far too important to the stability of the system to get a Backport for. Not saying they won't do it, but your best bet is to grab it from the Dapper reps (and pray nothing big breaks) or just do a full upgrade to Dapper. (Note that as of right now, the Dapper reps aren't open, but they should be soon).

---

### Post by darius779 on 2005-10-19
[QUOTE=SSTwinrova]I think this is far too important to the stability of the system to get a Backport for. Not saying they won't do it, but your best bet is to grab it from the Dapper reps (and pray nothing big breaks) or just do a full upgrade to Dapper. (Note that as of right now, the Dapper reps aren't open, but they should be soon).[/QUOTE]

I expect that you are right.  I was thinking of the backports as something like a "testing" repository, but that isn't really accurate.

---

### Post by Jingo on 2005-10-20
I would very much like to test it too.

It would be very great to have a repository with .deps for testing.

---

### Post by mariux on 2005-10-20
WIll this bring composition (exa acceleration) to my radeon 9700?

---

### Post by theh0g on 2005-10-20
Anyone manager to get it running?

---

### Post by Jingo on 2005-10-20
Anyone know the steps to build this?

Any special configuration I need to do?

---

### Post by Manny C on 2005-10-20
Too many people jumping the gun here. Give this some time. Drapper repositories aren't even open yet. This is the proper outlet for something like this. X is far to critical for system stability to be unleashed on the unsuspecting stable user that is now Breezy user. 

Don't need it in the backports either. These packages should typically be stable and definitely not critical.

---

### Post by Jingo on 2005-10-20
[QUOTE=Manny C]Too many people jumping the gun here. Give this some time. Drapper repositories aren't even open yet. This is the proper outlet for something like this. X is far to critical for system stability to be unleashed on the unsuspecting stable user that is now Breezy user. 

Don't need it in the backports either. These packages should typically be stable and definitely not critical.[/QUOTE]

So what now, when I am a stable Breezy user who wants to help testing this RC on Breezy, so I can file bug-reports and otherwise help this becoming stable. As a benefit for me I get some bug-fixes I have been waiting 4 month for. Do you mean I must wait until 6.04 ? Even microsoft corrects faults faster than this!

Xorg uses a configuration file. Where can I find the one Ubuntu used for compiling Xorg 6.8.2 ?

---

### Post by darius779 on 2005-10-20
[QUOTE=Jingo]So what now, when I am a stable Breezy user who wants to help testing this RC on Breezy, so I can file bug-reports and otherwise help this becoming stable. As a benefit for me I get some bug-fixes I have been waiting 4 month for. Do you mean I must wait until 6.04 ? Even microsoft corrects faults faster than this!

Xorg uses a configuration file. Where can I find the one Ubuntu used for compiling Xorg 6.8.2 ?[/QUOTE]

I was tinkering with getting the modular X built yesterday and found that is fairly complex, and I am far too lazy to figure it out on my own. ](*,)   Im hoping there will be some build guides, or better yet, a script coming out within the next week so I can try it on breezy.

Otherwise, I guess the best bet will be to wait and try to manually backport it from dapper when it is available.

---

