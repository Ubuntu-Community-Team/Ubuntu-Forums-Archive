---
title: "Ubuntu needs to change their swap space calculation!"
date: 2010-05-02
forum: The Cafe
---

### Post by kavon89 on 2010-05-02
First off, I'm not sure if this thread belongs in the Community Cafe but I couldn't think of a better place for it (although I may look into submitting a bug report).

Currently, I've got 6GB ram and a 12GB swap, I used the easy/automatic installer in Ubuntu 10.04. This flat "Swap = 2 x Ram" is not a good rule of thumb anymore now that ram is plentiful, it's wasting hard drive space.

Ubuntu needs to be following a better standard, like the one Red Hat has:

> 
Swap should equal 2x physical RAM for up to 2 GB of physical RAM, and then an additional 1x physical RAM for any amount above 2 GB, but never less than 32 MB.

```
IF  Ram < 2
    Swap = Ram * 2
ELSE
    Swap = Ram + 2
```

For systems with really large amounts of RAM (more than 32 GB) you can likely get away with a smaller swap partition (around 1x, or less, of physical RAM).


[Source]("http://www.redhat.com/docs/manuals/enterprise/RHEL-5-manual/Deployment_Guide-en-US/s1-swap-what-is.html")

With that rule in effect I'd have an 8GB swap, which is perfectly acceptable (although if I cared enough I'd have a 1:1 with ram and swap because I've never seen my swap be used for more than 10MB before).

---

### Post by Lensman on 2010-05-02
Hmmm...that is interesting, because my 10.04 install with 8GB of RAM, auto configured itself a 6.1GB Swap, which I consider is just fine given the amount of RAM.

---

### Post by speedwell68 on 2010-05-02
I agree.  I have 4GB of ram and Ubuntu has allocated 9GB of swap.  I was thinking that 5GB would be sufficient.  Is there anyway that I can reclaim the un-needed 4GB of disk space.

---

### Post by Chrysantine on 2010-05-02
> **kavon89 said:**
> First off, I'm not sure if this thread belongs in the Community Cafe but I couldn't think of a better place for it (although I may look into submitting a bug report).
The problem is swap is used to hibernate the system as well so if you don't have enough swap, you won't be able to hibernate so you'll have to factor that to your equation. 

Have seperate partition setup for laptop/desktop/server.

---

### Post by kavon89 on 2010-05-02
> **Chrysantine said:**
> The problem is swap is used to hibernate the system as well so if you don't have enough swap, you won't be able to hibernate so you'll have to factor that to your equation. 


You would only need a 1:1 so that everything in RAM (should it be completely full) can be completely dumped to the hard disk. Following Red Hat's standards there'd be enough for the entire system's ram plus 2GB.

The only cautionary thing I can think of is if the user upgrades his/her ram and has more than the amount of swap, and then happens to fill it all up and wants to hibernate the system.

---

### Post by Lightstar on 2010-05-02
4gb of ram
made my own partitions, gave myself 1gb of swap.

I have never filled my 4gb of ram in linux anyway.
In windows, that's another story.

---

### Post by snowpine on 2010-05-02
What is the size of your hard drive? I wonder if the Ubuntu installer considers that as a variable in the calculation...

---

### Post by toupeiro on 2010-05-02
Are you SURE that else statement is accurate?  I have a RHEL4 server with 32GB of ram in it, and its default swap-size is 8GB, which would be RAM / 4.  Linux uses RAM FAR more efficiently than windows desktop or server.  From what I've seen, my memory usage has to go well into 90-95% utilized to start swapping and it only swaps very little until it gets to 100%.  I don't claim to know what redhats equation is, but I think it changes a bit more than your explanation depending on the amount of physical ram you have.  It would be horrifically wasteful to have a 34GB swapfile.  At some point, the owner/sysadmin has a job to do: reassess and reconfigure the hardware...

---

### Post by Sam on 2010-05-02
How is it possible to hit swap with more than 4 GB or RAM ??

---

### Post by kavon89 on 2010-05-02
> **toupeiro said:**
> Are you SURE that else statement is accurate?  I have a RHEL4 server with 32GB of ram in it, and its default swap-size is 8GB, which would be RAM / 4.  Linux uses RAM FAR more efficiently than windows desktop or server.  From what I've seen, my memory usage has to go well into 90-95% utilized to start swapping and it only swaps very little until it gets to 100%.  I don't claim to know what redhats equation is, but I think it changes a bit more than your explanation depending on the amount of physical ram you have.  It would be horrifically wasteful to have a 34GB swapfile.  At some point, the owner/sysadmin has a job to do: reassess and reconfigure the hardware...

Well, my source (link in main post) is directly from Red Hat's RHEL 5 manual. It does mention for systems with a large amount of RAM that less than 1x amount of RAM is fine also.

---

### Post by FuturePilot on 2010-05-02
> **kavon89 said:**
> This flat "Swap = 2 x Ram" is not a good rule of thumb anymore now that ram is plentiful,


So is hard drive space. Just sayin'. ;)

---

### Post by NMFTM on 2010-05-02
> **Sam said:**
> How is it possible to hit swap with more than 4 GB or  RAM ??
I have 8GB of RAM and used swap space for the first time just last night, actually. I made the mistake of not turning off Wireshark while I was torrenting.

...millions of packets later

---

### Post by Sam on 2010-05-02
> **NMFTM said:**
> I have 8GB of RAM and used swap space for the first time just last night, actually. I made the mistake of not turning off Wireshark while I was torrenting.

...millions of packets later

Well that was more an incident that a normal computer usage. Otherwise did you ever fill all your RAM and start swapping?

---

### Post by chriswyatt on 2010-05-02
> **speedwell68 said:**
> I agree.  I have 4GB of ram and Ubuntu has allocated 9GB of swap.  I was thinking that 5GB would be sufficient.  Is there anyway that I can reclaim the un-needed 4GB of disk space.

Use partitioning software to resize the swap partition:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by JDShu on 2010-05-02
> **FuturePilot said:**
> So is hard drive space. Just sayin'. ;)

Indeed, but RAM is better.

Anyway, I agree... 12GB swap is overkill.

---

### Post by NMFTM on 2010-05-02
> **Sam said:**
> Well that was more an incident that a normal computer usage. Otherwise did you ever fill all your RAM and start swapping?
When I had 4GB of RAM and would go to transfer several hundred GB between internal and external hard drives I would start to use swap space. But since I've upgraded to 8GB of RAM I've never touched it except for that once instance last night.

---

### Post by juancarlospaco on 2010-05-02
Just dont use RAM if its your problem,
anyways some apps needs big swaps to work properly...

---

### Post by LepeKaname on 2010-07-13
I don't know if its a bug or not, but I'm installing Ubuntu Server edition (10.04) in a 500GB HDD and 8GB RAM. When I choose any of the "guided" options (to let Ubuntu choose the values for me), it set a swap space of 40GB!!!! I just think there is something wrong there...

---

