---
title: "Leopard Extreme drive hot swap and LSI controller"
date: 2013-11-05
forum: System76 Support
---

### Post by Skaperen on 2013-11-05
The Leopard Extreme supposedly has hot swap drives.  But the pictures fail to show how this is set up.  The front of the box has no bays for it.  Is there a door to open to access the drives?  There are a couple pictures showing what looks like 4 internal drive bays.  I do not see any drive trays so is this a trayless system?  It would be nice to see pictures of how this works.

There is a problem I have found in a number of RAID controllers on the market.  That problem is, even when you disable RAID and have JBOD, the controller still takes some space at the front of the drive and presents the rest of the drive space after that to the system.  This makes the drive data incompatible with non-RAID controllers and ordinary PCs.  I would like to know if the LSI controller used on the Leopard Extreme has this issue, or if it can format and populate a drive that can be used on other non-RAID systems.

I sent email to [EMAIL="sales@system76.com"]sales@system76.com[/EMAIL] to ask this, and it was rejected as not an existing email.

---

### Post by houstonbofh on 2013-11-06
It looks like an internal drive tray system, so removing the side cover and unscrewing them is required.  However, in the default config, there is no raid, so removing a drive crashes the system.

As for the LSI, you are correct.  IT mode (just a drive passthrough) is not supported.  While it is a nice card, your data is absolutely dependent on it.  If you want a raid that can be read elsewhere, you will need to build it yourself.

You may want to look at the nas4free project and forums.  Even if you do not want to build a NAS, they have very good technical info on hardware that gets out of the operating systems way.

And if you want trays, look for things like these...
[http://www.norcotek.com/item_detail.php?categoryid=8&modelno=ss-300](http://www.norcotek.com/item_detail.php?categoryid=8&modelno=ss-300)
[http://www.norcotek.com/item_detail.php?categoryid=8&modelno=ss-500](http://www.norcotek.com/item_detail.php?categoryid=8&modelno=ss-500)

---

### Post by Skaperen on 2013-11-06
What I am wanting is to be able to swap the drives from the front.  I already have frames like those you linked to.  There are also tray-less ones out there.  But these frames won't fit in the Leopard Extreme since only one bay is exposed in the front.

The company that made the frames I do have quit making that model and went to tray-less ones.  So I will need to switch something eventually.  I don't know if the Norcotek ones are tray-compatible with the SNT ones I have.  If they are, they may also be an EOL product since 2 other makers of compatible ones quit, too.  My guess is the trayless ones are becoming the popular ones.

So drive transparency is called "IT mode"?  But why do the controller makers fail to support that?  I know they are focusing on RAID, but this would be trivial to support.  I first ran into this with 3ware.  LSI bought 3ware.  I guess they both have the same limited philosophy.

A NAS is not what I want.  I'm not doing RAID of any kind.  These are rotated backup and archive drives.

And it's too bad System76 seems to be shunning communication from potential customers.  I tried them on Twitter last night and will see if they eventually answer there.

---

### Post by houstonbofh on 2013-11-06
Why?  Vendor lock in...  Laziness...  Who knows.  There is a card from LSI that is OEMed by IBM.  It will not do IT mode, but if you flash it with an LSI firmware, it will...  Craziness.  Lately, I have just been going with Syba cards that have well supported Marvel or Sis chipsets.  (The fact that they are a lot cheaper is just bonus)

Or, try this blog for your shopping pleasure...  [http://blog.zorinaq.com/?e=10](http://blog.zorinaq.com/?e=10)

---

### Post by Skaperen on 2013-11-06
Well, there are TWO dings against the Leopard Extreme for me.  One is the unusable controller, and one is that it doesn't swap drives through the front.  The former might be doable but the latter is not.  Would have been OK if that box had a door in front.  So now I need to look for a box with something built-in but working through the front, or a box with 3 or 4 bays on the front.

---

### Post by jbelmonte on 2013-11-07
> **Skaperen said:**
> Well, there are TWO dings against the Leopard Extreme for me.  One is the unusable controller, and one is that it doesn't swap drives through the front.  The former might be doable but the latter is not.  Would have been OK if that box had a door in front.  So now I need to look for a box with something built-in but working through the front, or a box with 3 or 4 bays on the front.

The default Leopard Extreme configuration has Operating System Storage (not swappable) and Hot Swap - No RAID additional storage options. So you don't need the LSI controller to be able to hot swap your data drives.

"Pull and replace drives without skipping a beat. The Leopard Extreme features a fully hot swappable backplane for your independent drives or storage array."

Swapping drives through the front is a server feature that I have not seen on a desktop computer. System76 has servers with hot swappable drives with front access. [https://www.system76.com/servers/model/elav4](https://www.system76.com/servers/model/elav4) or [https://www.system76.com/servers/model/elap4](https://www.system76.com/servers/model/elap4) But both of those systems are RAID enabled with the LSI controller, so they may not meet your needs.

Concerning your sales email issue, it looks like System76 has gone to a form for sales questions. [https://www.system76.com/contact/](https://www.system76.com/contact/) or you can call them at 888.468.6482 Option 1.

---

### Post by Skaperen on 2013-11-07
> **jbelmonte said:**
> The default Leopard Extreme configuration has Operating System Storage (not swappable) and Hot Swap - No RAID additional storage options. So you don't need the LSI controller to be able to hot swap your data drives.

"Pull and replace drives without skipping a beat. The Leopard Extreme features a fully hot swappable backplane for your independent drives or storage array."
Without a controller, only 3 drives can be used.  Apparently the mainboard only has 4 SATA ports. But the big killer is the fact that I would have to open the side panel, which in my setup would mean taking the computer off the table since where I work does not have enough room to do that.  The other option would be adding a different controller.  I am trying to get away from doing the machine building.  And the side panel opening is the big show stopper (cannot do it with 4 machines side by side).

> **jbelmonte said:**
> Swapping drives through the front is a server feature that I have not seen on a desktop computer. System76 has servers with hot swappable drives with front access. [https://www.system76.com/servers/model/elav4](https://www.system76.com/servers/model/elav4) or [https://www.system76.com/servers/model/elap4](https://www.system76.com/servers/model/elap4) But both of those systems are RAID enabled with the LSI controller, so they may not meet your needs.
Yeah, the LSI would be a show stopper there.  And these don't seem to have any decent graphics.

The class of machine that has both decent graphics and server like storage is called "Workstation" typically.  But this can be done by putting the right combination of features inside a server box, OR adding a drive bay enclosure to the front of a desktop box with enough bay openings.  Currently, I do the drive enclosure thing on 3 machines, using a system with trays.  I've been thinking of moving to a trayless system, and thinking of doing some machine upgrades at the same time.

---

### Post by isantop on 2013-11-07
Hot swap on the Leopard doesn't require RAID. The built-in SATA controller supports hot swap natively. 

Swapping the drives does require opening the system. The chassis is toolless, so there aren't any screws to remove.

---

### Post by Skaperen on 2013-11-07
> **isantop said:**
> Hot swap on the Leopard doesn't require RAID. The built-in SATA controller supports hot swap natively. 

Swapping the drives does require opening the system. The chassis is toolless, so there aren't any screws to remove.

I do know the mainboard SATA ports can do hot-swap.  But only 3 drives can be supported this way since one of the ports is needed for the system drive ... unless one is wanting to have the system drive in the hot-swap bay (to be able to do cold-swap of systems).

If it could have been a door opening at the front giving access to the hot-swap bay, that would have worked.  I did not see a way to do that in the photos, but I asked because the photos did not cover enough to totally rule it out.  But it has been ruled out, now.  One must open the side panel to access the drives.  I do not have space for that.

---

### Post by isantop on 2013-11-07
The OS will come installed on an SSD, installed below the main drive cage. If you order RAID or additional drives, they then populate the drive cage.

---

### Post by Skaperen on 2013-11-07
> **isantop said:**
> The OS will come installed on an SSD, installed below the main drive cage. If you order RAID or additional drives, they then populate the drive cage.

Add the option on ordering to not have that SSD installed.  The the first cage drive will be the first probed drive and the OS can be on there.  Or the BIOS can be configured to boot that drive anyway.  But that's only for people like me who are switching OSes around for testing them against real hardware.

---

