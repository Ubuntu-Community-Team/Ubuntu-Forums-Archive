---
title: "Xen guest (ubuntu) time issue"
date: 2011-09-21
forum: Virtualisation
---

### Post by MACscr on 2011-09-21
i dont know if its a newer kernel issue or an ubuntu issue, but my ubuntu guests seem to always have the wrong time (might be off as much as 30 minutes) even after being corrected. These are pvm's using pvgrub and the other guests (centos) on the hosts (centos) are just fine. The hosts time is correct as well. Any ideas/recommendations? All guests (centos and ubuntu) both have their clocksource set as jiffies.

---

### Post by Dangertux on 2011-09-21
> **MACscr said:**
> i dont know if its a newer kernel issue or an ubuntu issue, but my ubuntu guests seem to always have the wrong time (might be off as much as 30 minutes) even after being corrected. These are pvm's using pvgrub and the other guests (centos) on the hosts (centos) are just fine. The hosts time is correct as well. Any ideas/recommendations? All guests (centos and ubuntu) both have their clocksource set as jiffies.

Wow - 30 minutes is a little extreme the most I've seen them drift is a minute or 2 , and that's considered large.

I would suggest recoupling your DomU clocks to your Dom0 if they are drifting that far. Obviously that increases the odds for random hangups.

I would definitely spend some time looking into the kernel as often times it is the source of clock drift related issues. I'm just still in a state of shock that it's drifted that far. Have you recently migrated the VM's in question?

---

### Post by MACscr on 2011-09-21
> **Dangertux said:**
> Wow - 30 minutes is a little extreme the most I've seen them drift is a minute or 2 , and that's considered large.

I would suggest recoupling your DomU clocks to your Dom0 if they are drifting that far. Obviously that increases the odds for random hangups.

I would definitely spend some time looking into the kernel as often times it is the source of clock drift related issues. I'm just still in a state of shock that it's drifted that far. Have you recently migrated the VM's in question?

The issue has been going on a lot longer than since my last migration and i do live migrations all the time with my guests with no problems. All the dom0's are synced through ntp. Again, this issue is completely unique to ubuntu guests, though obviously there is a large difference in kernel versions between centos and ubuntu. I definitely dont want a solution that could lead to more hangups and i definitely want the guests to be getting their time from the hosts. I dont want to run ntp on each guest.

---

### Post by Dangertux on 2011-09-21
Well if they are set to jiffies they aren't getting the time from dom0 they are getting it from their own clock cycles again, linking it to dom0 can cause hang ups though. The xen documentation explains the setting for linking the clock to dom0 if you want to do that. I dont have the link ATM I am on my cell.

---

