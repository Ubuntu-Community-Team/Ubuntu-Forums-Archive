---
title: "Driver seems to have changed wireless"
date: 2011-02-12
forum: System76 Support
---

### Post by gamerchick02 on 2011-02-12
I'm running the 2.6.1 version of the System76 driver on my Starling 1.  I updated it from the previous version of the driver, and it now seems like the range is reduced.

Has anyone else been able to confirm this?  I only realized this because I was messing around with Xubuntu and it didn't connect to my wireless network in my room (upstairs, probably 60ft from the access point, maybe?).

It's connected before up there with no problems.  As it stands now, I can't use my netbook anywhere but the room where the wireless router is located.

What changed in the driver to reduce my wireless range?

Amy

---

### Post by isantop on 2011-02-14
Hi Amy.

After you installed the driver, did you go to System > Administration > System76 Driver, then use the Install function? Otherwise, the driver may not have been applied.

---

### Post by gamerchick02 on 2011-02-14
Yeah, I did.  I'll give it another shot though.

Thanks.

Amy

---

### Post by isantop on 2011-02-15
Let us know how it turns out. Good luck!

---

### Post by gamerchick02 on 2011-02-15
Ok, so I ran an update, then the driver again and rebooted.

I get decent connectivity directly above the router in my house, but not across the house and upstairs.

I wonder if it's a router setting?  Though I haven't mucked with the router or it's settings in awhile (a year or more).

I'll look into this some more.

Amy

---

### Post by vttay03 on 2011-02-17
I've got a star1 and the range isn't all that great unless you're directly above the router or in the same room (like you said above).  I live in a 3-level townhome and my router is in the basement.  When I sit in my bedroom (on the 3rd level), the connectivity drops in and out.  I eventually got tired of it and didn't feel like buying another router so I ended up just running an ethernet cable from the basement to the bedroom.  I would assume this is isolated to the wireless card inside the Starling because my wife doesn't have any problems with her laptop.

That being said, I wouldn't spend too much time messing with router settings....

---

### Post by gamerchick02 on 2011-02-17
Well, I've got a workaround:  A Belkin USB wireless adapter.

It ain't pretty, but it works, and I'll be using it til the drivers update again.

:)

Amy

---

### Post by vttay03 on 2011-02-17
> **gamerchick02 said:**
> Well, I've got a workaround:  A Belkin USB wireless adapter.

It ain't pretty, but it works, and I'll be using it til the drivers update again.

:)

Amy

There ya go

---

### Post by jml on 2011-02-19
Amy, your solution gives me a sense of deja vu.  When I first bought my STAR1, I used a Belkin USB wireless adapter until System 76 issued their driver fix.  Hopefully a new fix will come soon.

Joe

---

### Post by macabrem on 2011-02-20
A good work around is to build a new wireless driver with compat wireless using the bleeding edge package:

[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

I thought I would have to buy a USB wireless adapter until somebody on another forum told me about this easy solution.  Just follow the directions step by step and even a beginner can have their wireless working in about 15 min. or less.

ETA:  I'm currently using a Debian based distro on my Starling.  I'm not sure if compat wireless is debian only or not.

---

### Post by isantop on 2011-02-21
There is compat-wireless in Ubuntu, provided by linux-backports-modules-wireless

---

### Post by gamerchick02 on 2011-02-21
> **isantop said:**
> There is compat-wireless in Ubuntu, provided by linux-backports-modules-wireless

Really?  Sweet; I'll enable the backports.  Thank you very much!!

Amy

---

