---
title: "XP-&gt; Ubuntu/Vmware: My rocky experience"
date: 2007-11-18
forum: Testimonials &amp; Experiences
---

### Post by lenticular on 2007-11-18
I've been running Ubuntu since Dapper as an dual boot with XP on my home PC  and Sony TR1 and T340P laptops with good results.  So when I bought a Sony TZ130 laptop, I decided to bag the dual boot altogether and run with Ubuntu.  Since I still needed XP for a few applications at work, I would run it as a VMware guest (which I had done on my desktop with few problems).  Eventually, when I found a way to migrate off of Eudora (and 10 years of email), learned to use OpenOffice products as handily as MS Office, and found a way to sync my Treo 680 with MeetingMaker under Ubuntu, I would delete the VM and live in a pure Ubuntu world.  I'm about a month into this, and the experience has been a bit rocky.

Wireless Doesn't Work
My laptop has the Intel 4965 wireless chipset which is not supported under Feisty without ndiswrapper or doing more messing with the kernel that I wanted to take on.  No problem, since Gutsy (in beta at the time) supported 4965.  Since installing Gutsy, though, wireless in intermittent at best, with connection drops happening eventually.  Most of the time, though, I can't get connected at all.  Searching through all the posts on this topic, I've tried the common advice with no luck.  Eventually, this will get fixed in Gutsy and in the meantime, my work connection is through ethernet, so I'll just wait.

VMware Screen Resolution Problematic
I have read documentation, followed threads in the Ubuntu and VMware forums, yet still can't get the screen resolution in my VM set the way I would like it.  Ubuntu knows how to use my display at 1366x768, but VMware does not.  I've tried about 10 versions of xorg.conf  but no luck.  Does the VMware SVGAII  driver need its own device section in xorg.conf?  That doesn't work.  Nowhere have I find a good explanation about what VMware needs and how that is provided in xorg.conf.   The xorg.conf documentation is not all that clear anyway. Devices, monitors, screens -what is the relation between all of them?  But for now, I can get a usable resolution on the external monitor I use at work, and, without wireless, I'm using my desktop at home, I guess that I'll just live with this for now.  Or try VirtualBox.

Ubuntu and VMware: Not syncing with my Treo
 I want to sync my Treo with the XP VM using conduits to MeetingMaker (our group calendar).  Sure, I've added the Palm to the VM.  I can even run a thumbdrive emulator on the Palm that gets seen right away.  But when I try to sync the device it is never noticed.  Again, I've followed documentation and suggestion in forums with no luck.  What's more, Ubuntu doesn't want to sync with my Treo.  Sure, there are about 7 different ports to try in the gpilot setup, but it never sees it.  But for now, I'll just print my schedule and carry it with me.

Since things are mainly working, I guess the frustrations are more inconveniences than deal-killers.  I've accepted that Ubuntu is an OS for people who like to tinker with stuff (as I do), and that to live in this world I must accept some rough edges.  I have also learned even more about Ubuntu and VMware by trying to surmount problems. 

-John

---

### Post by jdrodrig on 2008-01-12
I would normally disagree with "I must accept some rough edges"; especially because it seems you already have bought all the proprietary software to run your tasks under XP, so the usual "free software" argument seems weak at best. 

However, it seems that *you* have weigthed costs and benefits and decided for linux. I should say that in a business environment the information you provided would have made me decide for XP.

---

