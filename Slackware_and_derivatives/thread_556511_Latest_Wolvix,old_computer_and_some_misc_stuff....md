---
title: "Latest Wolvix,old computer and some misc stuff..."
date: 2007-09-21
forum: Slackware and derivatives
---

### Post by Embrance on 2007-09-21
I recently started downloading and testing out all the latest Linx based distros,and liked Wolvix the most.As it seems,the latest version is on more based on Slax but on Slackware.

So what I wanted to ask:
1)Will I be able to still "drag-and-drop" module files in the module dir and they will be installed automatically?
2)I read on a site that ATI drivers suck on linux PCs.Their average performance is(as the site stated)about 50% of what it should be.And the thing is I have a kick *** ATI card,and I want it to work on Wolvix so I could play some games form time to time(I play mostly emulators and sometimes a 3D game,but nothing that would hog up a whole PC).
3)Is Linux'es memory management like Windoze's?For no apparent reason,after about an hour or so,the whole system takes 250+ MB of ram without any applications running.Is this the case for Linux?
4)I will need an antivirus.Could someone suggest me a good one for Linux.A firewall would come in hand as well.

Have in mind,Im not completely new into this.I have ran linux(SuSe 8.2 Pro)in the past,know some basic stuff,and just in case,I got myself a hell of book with all commands and how-to guides,so I wont switch back to Win.

Thanks for the help.

---

### Post by bonzodog on 2007-09-21
hrm--

1) No, not to my knowledge. Although, you shouldn't need to, as most hardware now should Just Work

2)There are known problems with ATI drivers, but they are getting better. Some people report that games run better under the linux drivers than the windows ones. Only way to find out is for yourself.

3)No, Linux does not manage memory like windows. It's a little complicated, but it caches programs in memory even when they aren't running to enable fewer reads/writes to the hard disk, and faster start-ups. Google/wikipedia this for a more complete answer.

4)Why do you need an antivirus? Viruses are close to non-existant in linux. (the last known published virus schedule listed 31 known viruses, only 2 in the wild). The only time you might need one is if the linux box talks directly to a windows box.
On firewalls: There are plenty around. Either use and design a custom IPTables script, or something like firestarter would be good.

---

### Post by Embrance on 2007-09-23
I tried Wolvix as LiveCD on my Desktop PC but nothing worked! :P
No sound,no video,no nothing.Anyway,I will try Slackware 12 to see if its any good,maybe Xubuntu as well...

---

### Post by Embrance on 2007-09-24
btw,if i install it to my HDD,to run some test,and try to fix all the issues(GFX and sound namely)will I be able to remove it completely if I dont want it anymore?
I mean after installation,if I dont want it anymore,will I be able to remove the bootsection screen and load only WinXP?

---

### Post by bonzodog on 2007-09-25
yes, you can restore the MBR if you want to, it's fairly easy.

Slackware should work on your PC, but be warned, it's not for those wanting a friendly presentation to Linux. 
It's for those wanting to *really* learn linux at it's core and become a Linux power user.
The GUI friendly spin off from Slackware is [Zenwalk Linux]("http://www.zenwalk.org"). Even then, it might not see everything. To be honest Ubuntu is about as hardware friendly as you get in the linux world, as it has all the little modules built in for all the extra new hardware. Slackware and it's derivatives run what is called 'Vanilla'. i,e unpatched straight from the source code.

---

### Post by Embrance on 2007-09-25
I'm willing to learn,hence I dont really care how hard it is as long as thee are resources and how-to;s.The first thing I will have to do though,is to make my ol' Speedtouch modem work(as I know that the whole series has problems with Linux),so I could access the net and fix the Wolvix's or Slackware parameters on the air.THanks for the help.

---

### Post by Embrance on 2007-10-27
Ok,now I put the LiveCD in the drive boot up,and when trying to install,I see only 3 HDDs(there should be 4,because I cut the first in 2 pieces,one 70gb and the other 5gb for the system only)

I choose haad(which is the 1st hdd which i partitioned)but cannot select in which of the 1 parts to install Wolvix(there should be 2 options,one for the 5gb part and the other for the 70gb)

I will try some other distros to see if I can find somehting as easy and out-of-the-box multimedia=ready.

---

