---
title: "upgrade to Ubuntu 17.10 or not?"
date: 2017-11-04
forum: Ubuntu, Linux and OS Chat
---

### Post by because7892 on 2017-11-04
Hello i am currently using Ubuntu 16.04 LTS. i installed 17.10 in a virtual machine to test it out. i really like the gnome desktop environment and how the new design of the OS works. but i want to know if it is stable and reliable. i need my system to be up and running all the time for school and business. on Ubuntu 16.04 i only haft to restart every 1 to 2 months. it is really stable so i was wondering if 17.10 is worth upgrading to or will i have issues with stability.
thanks.

---

### Post by sudodus on 2017-11-04
If your current  Ubuntu 16.04 LTS works well, I suggest that you wait for the next LTS version to be not only released, but also debugged and polished. So wait until August 2018 and install Ubuntu 18.04.1 LTS, the first point release.

Ubuntu 17.10 is very nice and interesting, but there are several things that are not quite mature yet. Use it only if your hardware needs it to work (because the previous versions of Ubuntu are too old for the hardware in your computer).

---

### Post by mörgæs on 2017-11-04
I think you have done a smart choice keeping 17.10 in a virutal machine. 17.04 was stable but 17.10 (representing some fundamental changes) is not.

> **because7892 said:**
> On Ubuntu 16.04 i only haft to restart every 1 to 2 months.
Are you applying security updates on a daily basis?

---

### Post by because7892 on 2017-11-04
OK i will keep Ubuntu 16.04 installed until 18.04.1 is released. and usually when i check for updates it either says system is up to date or it finds updates, installs them but doesn't require a restart. but yes the system does install updates quite regularly but has never prompted for a restart.

---

### Post by vasa1 on 2017-11-04
Hmmm... each kernel update requires a restart to be effective which is why, I think, mörgæs asked.

What does```
uname -a
```show?

And, just to be clear, at least *some* kernel updates are security updates. For example: [https://usn.ubuntu.com/usn/usn-3443-1/](https://usn.ubuntu.com/usn/usn-3443-1/) which has> After a standard system update you need to reboot your computer to make
all the necessary changes.

---

### Post by Bucky Ball on 2017-11-04
> **because7892 said:**
> i need my system to be up and running all the time for school and business.

In that case, I can only concur with the rest and agree that 16.04 LTS it is. In fact, LTS it is. Your situation is exactly what they're designed for.

Stability cannot be expected if you are jumping from release to release every six months (interim releases have nine months support so you need to upgrade every six to stay ahead of the EOL curve). LTS releases are for production machines that need to be reliable and stable (like machines that can't have downtime due to being used for school or business) and have five years support.

My advice, for what it's worth: stick with 16.04 LTS and stick with LTS releases, period. 18.04 LTS is the next LTS and you can upgrade LTS releases via online to the next LTS, skipping the interim releases in between. This avoids a full install if you want to go that way, although many will only go a clean install and never use the online upgrade.

Play around with interim releases in virtualbox or install on a spare partition. That's what I do if I'm curious as I don't have time or inclination to screw around with broken interim installs every five minutes (or even every five weeks!).

Install 18.04 LTS when that arrives next April and you will recieve all the goodness that is 17.10 and more I'd say (and it should be rock solid in no time and has five years to get there, not nine months).  

Good luck.

---

### Post by monkeybrain20122 on 2017-11-04
> **Bucky Ball said:**
> 
Install 18.04 LTS when that arrives next April ..

.


I would wait a few months for the post release bug fixes, why the rush? I wouldn't advise trading in your well tweaked and working system when something new is release right the way, all new releases are buggy.

---

### Post by because7892 on 2017-11-04
yes i think staying with 16.04 for a while would be best, to answer Vasa1's question when i type that command into the terminal i get.

Linux mitchell-System-Product-Name 4.10.0-38-generic #42~16.04.1-Ubuntu SMP Tue Oct 10 16:32:20 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by mörgæs on 2017-11-05
Don't trust people who claim they can predict if and when a future release is stable or not. There are so many decisions to be made, many of which come from outside the Ubuntu community. Trust only your own testing and adapt your plans to it.

Status is: Xubuntu and Lubuntu 17.10 are highly stable releases. Lubuntu has got a new unstable sibling, Lubuntu Next, and it will be interesting to follow him growing up in the future. 

Ubuntu 17.10: Unstable on Nvidia hardware and on Intel Atom. I haven't heard of problems elsewhere. 

There is no clear pattern. Do your testing and draw conclusions.

---

