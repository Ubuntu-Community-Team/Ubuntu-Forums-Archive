---
title: "Recommended Server Hardware"
date: 2013-01-15
forum: Server Platforms
---

### Post by Toriku on 2013-01-15
I am running several servers of my own for my own experiments and services, old computers are sufficient; but now I am setting up a business server at the company I work at... It will need to handle [COLOR="Green"]**a few Terabytes of media**[/COLOR], and a couple of websites; can anyone recommend some [COLOR="DarkRed"]**reliable and stable**[/COLOR] business strength hardware?
 Tower servers, rack servers, building is also an option...

 Any kit I should avoid using? I've had a good history with Seagate hard drives, and my main server is an old DELL office computer that runs pretty well...

---

### Post by Grenage on 2013-01-15
We generally use HP rack-mount servers, with hardware raid controllers and SFF SAS discs.  Beware the entry-level servers, as they all use crappy fakeraid.  I've only used a couple of Dell servers, but I'm sure they're fine.

When looking at a new server (such as the G7 line), I'll normally do some basic searches in google, just to make sure that there are no driver issues.  I've only had driver issues once, and that was about 8 years ago.

---

### Post by Toriku on 2013-01-15
> **Grenage said:**
> We generally use HP rack-mount servers, with hardware raid controllers and SFF SAS discs.  Beware the entry-level servers, as they all use crappy fakeraid.  I've only used a couple of Dell servers, but I'm sure they're fine.

When looking at a new server (such as the G7 line), I'll normally do some basic searches in google, just to make sure that there are no driver issues.  I've only had driver issues once, and that was about 8 years ago.

yes, I did like the hardware RAID controllers I've been seeing, I think its a must for the task; I've seen some systems with out of band active management, I liked the look of that feature too;
 SAS disks are new to me, I've been trying to read up on them for a while but its not clear to me how they are different from SATA

---

### Post by Grenage on 2013-01-15
> **Toriku said:**
> I've been trying to read up on them for a while but its not clear to me how they are different from SATA

There is actually not that much difference; they have more advanced internal functions, and in my experience are generally better built and have better bandwidth performance.  Of course, given the price difference, one really expects nothing less.

A good server isn't cheap, but the price can easily triple once you've added drives.

---

### Post by darkod on 2013-01-15
> **Toriku said:**
> yes, I did like the hardware RAID controllers I've been seeing, I think its a must for the task;

Since this will be a server I assume dual booting is out of the question, so this will be a linux only server. Since linux software raid works very well, why would a HW raid controller be a must?

If it goes down, you need to attach your array to the same model controller or very similar, and it's still a question whether it will work.
You can attach linux SW raid array to any linux/ubuntu server and it will keep going.

Not that the above is the main criteria for your server selection, but I just thought it deserves mentioning. In fact, few people have mentioned on the forum that they have left HW raid cards precisely after problems getting your array running without destroying it after their card died.

On another note, and depending how experienced you are with making your own build, you can easily buy server grade hardware (especially in the USA) and make it yourself. But consider both options, since big brands can usually make the server much cheaper than you paying retail for all components. But sometimes the math might go the other way and your own build to be cheaper/better, plus it will be hand picked component by component, not what HP/Dell decided to install. One of the brands covering cases and boards is Supermicro, I have also seen Norco mentioned for cases. For memory you can go with Kingston, and CPU of course Intel unless you are Opteron fan.

---

### Post by spynappels on 2013-01-15
Depending on whether you have rack infrastructure already in place or not, I'd look at either DL or ML Proliants from HP.

Personally, I'd go for good quality SATA3 drives and mdadm RAID unless you've managed to get some serious budget allocated. If the server is critical, have at least 1 but preferably 2 Hot-Spare drives and a good off-site backup plan.

Out of band access is good if you have independent Internet connections, and if you use Ubuntu server, you don't need to get the expensive RDP license for the out-of-band controller, serial console access is fine.

It will largely come down to budget and personal preference, but I've always preferred HP hardware to Dell, YMMV.

---

### Post by Grenage on 2013-01-15
Hardware RAID is faster, and in my experience, more reliable; nobody ever got fired for choosing hardware RAID.  Software is ok on a budget, or when there is minimal overhead.

RAID isn't a backup solution, and in most business environments it is not treated as such.  One basically looks at performance, and possibly disc redundancy.  It never hurts to unsure you have a spare RAID card knocking around, although failure rate is damn low.

When price isn't a major factor, one would have to have a very good reason to choose software RAID.

---

### Post by Toriku on 2013-01-15
A lot of servers are advertised to be available with SuSe and Red Hat, are the drivers for those distros going to be transferable to Ubuntu?

---

### Post by tgalati4 on 2013-01-15
Generally yes, but you may have to "reroll" some driver packages from rpm to deb.  Usually, someone has done this already, you just have to do some searching to find a blog of someone who has already done this.  For brand-new hardware, you may have to do the "rerolling" yourself, but there are guides available.  Normally, just load Ubuntu server and see what works and what doesn't, then start searching.

---

### Post by Toriku on 2013-01-18
thanks for your help guys!

I've still not decided on Hardware or Software RAID just yet, can you recommend any hardware RAID controllers?

---

### Post by vDevices on 2013-06-24
@Toriku,

I find myself in the same boat (as your original post).  I'm curious to learn what you ended up going with (and why) and how it's been working out for you?

---

### Post by Toriku on 2013-06-26
The project has been postponed, but it will most likely be a HP ProLiant once I get back to it, a lot of people have been recommending the HP's, including Grenage at the beginning of the thread;
sorry I can't be any more help

---

