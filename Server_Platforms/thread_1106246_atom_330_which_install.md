---
title: "atom 330 which install?"
date: 2009-03-25
forum: Server Platforms
---

### Post by lummie on 2009-03-25
If just purchased a tranquilpc bbs2 which has the atom 330 processor which is "64bit ready".  I want to put ubutnu server on and was thinking of the jaunty release as it is so close.

I'll only be exposing https to the internet via port forwarding on the router, so I would have thought jaunty's apache would be as secure as intrepid. Do you think the risk is minimal for putting such a late alpha on?

Also x86 or amd64, which would be better on the atom330 considering it can do 64bit?
I did notice in jaunty a atom specific build but I assume that is a desktop install for the netbooks. Are there any cpu optimizations in there etc which would benefit the low power bbs server? If so, should there be an atom build of ubuntu server as atom servers seem to becoming more common?

Any thoughts appreciated.

Regards

Matt

---

### Post by windependence on 2009-03-25
8.04 LTS with AMD 64. 

8.10 did not work for me on that board.

-Tim

---

### Post by lummie on 2009-03-26
> **windependence said:**
> 8.04 LTS with AMD 64. 

8.10 did not work for me on that board.

-Tim

Thanks for you reply Tim.
I don't supppose you can remember what the issues were with 8.10.

Matt

---

### Post by windependence on 2009-03-26
Yeah, I had graphics issues. I probably could have fixed it but it was easier to just try 8.04 since I had the ISO. Worked like a charm. 

Now that was on the desktop version. On sever, it would get so far into the boot and then just drop to busybox. I really didn't work too long at getting it going, just used the LTS version which is absolutely fine for servers, in fact I think it's a better choice.

-Tim

---

### Post by lummie on 2009-03-29
I have put ubuntu 9.04 Alpha 6 amd64 on apart from an issue with KACPID running at 100% (which is supposed to happen in 8.04 as well) when the auto fan control settings are turned on in the bios, it works a treat.

---

### Post by tkaeregaard on 2009-06-08
> **lummie said:**
> I have put ubuntu 9.04 Alpha 6 amd64 on apart from an issue with KACPID running at 100% (which is supposed to happen in 8.04 as well) when the auto fan control settings are turned on in the bios, it works a treat.
Thank you for this most valuable nugget of information. I have the same problem, but I had not figured out the link between my BIOS setting and the kacpi problem.
 
FYI, I have installed Ubuntu Server 9.04 64-bit on my machine, and it works very well apart from this kacpi problem which now appears to be solved :-)

---

