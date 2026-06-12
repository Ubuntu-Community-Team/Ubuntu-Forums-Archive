---
title: "back to 8.10 intrepid ibex"
date: 2009-11-12
forum: Testimonials &amp; Experiences
---

### Post by hurtstotalktoyou on 2009-11-12
Six months ago, I wasted a great deal of time attempting to upgrade from 8.10 to 9.04.  In the end, I couldn't deal with random freezes, among other serious issues, and so I had to downgrade back to 8.10.

Last week I was very excited to try again.  After all, 8.10 has much to be desired, and I wanted to reap the benefits of new features and presumed improved stability.  But now, several days later, I can no longer deal with the headaches.  It's back to 8.10 for me---again!

Now, as six months before, I tally a list of reasons why I cannot stay with 9.10.

**serious issues:**

REASON #1:  I use gxine while I sleep, and every 30-60 minutes it freezes up.  This would be incredibly annoying if it only happened during the day.  When I'm in bed, it's intolerable.  If I could fix this, I might stay with 9.10 even despite all my other problems.  However, the fact is I can't fix it, and so that's that.

REASON #2:  My Samba network will not function properly.  Although I can access 9.10 from other OSes just fine, I cannot access any of my other WORKGROUP computers from 9.10.  So, in order to transfer files, I have to boot into Windows.  Printer sharing is right out.

**minor issues:**

REASON #3:  I use vlc to watch videos during the day, and every five minutes the screensaver appears.  The only solution is to disable it, leaving me without a screensaver.  This in turn makes me very uncomfortable about the safety of my monitor.

REASON #4:  I dual-boot with Windows XP (Vista) on my desktop (laptop), and at least once (twice) in the last week, after having been in Windows, Ubuntu freaks out and tells me that the file system is corrupted.  So I have to run fsck in a text console to fix it before I can boot.  That is both extremely annoying and highly unsettling.

REASON #5:  Probably related to #4 above, my laptop gives me constant warning messages that my hard disk is corrupted, when I know it's just fine.  My desktop thinks my hard disk is corrupted, too, but it doesn't bother me about it unless I run sudo fdisk -l.  This too makes me very uncomfortable.

REASON #6:  From Windows I am unable to access the Ubuntu partition with ext2fsd.


**final thoughts:**

Probably at least half of the above problems have solutions, but I'm afraid I just don't have the time to spend finding them.  I'm very disappointed in Ubuntu, and I'm not sure what to do about it.  Also, I'm extremely upset to have wasted so much time.  I see threads in this section emphasizing stability over style, and I can't agree more.  I hate Windows, but at some point 8.10 is going to be too out of date.  If nothing can take its place, then I will have no choice but to return to the dark side.

---

### Post by 3rdalbum on 2009-11-12
#1. I don't use Gxine - I can't comment sorry. Try removing the Gxine preferences file. (it's in a hidden file in your home directory).

#2. I'm not having any troubles with Samba, so I can't really comment - I did see a Samba update a while back so try applying your system updates. I tested 9.10 on almsot my whole home network when it was beta and if I'd had issue with Samba I would have reported them; do you want to file a bug at launchpad.net? If the Ubuntu devs don't know your problem, then they can't fix it.

#3. Screensaver inhibit also works fine for me in all video players. In VLC, the precise setting is:

Tools > Preferences
Under the "Show Settings" pane, hit "All".
Click on "Advanced" in the left pane, if it's not already selected. Choose "Inhibit the power management daemon during playback".

#4 No idea, I don't dual-boot.

#5 What exactly is saying that your disk is corrupted? Is it a SMART warning, or a message printed to dmesg?

#6 I can't remember what I used to use to access the Ubuntu partition; all I can remember is that it worked. Try a different ext2 driver on Windows?

---

### Post by Glucklich on 2009-11-12
Have you tried 9.04, now? After that long period of testing, all it's bugs might be fixed.
Or 8.10 is the latest LTS? If it is, I'd say for you to stick with the LTS's.

---

### Post by Tamlynmac on 2009-11-12
Just use what works and don't worry about or invest time/energy on what doesn't. IMHO, we often waste time convincing ourselves things are more important than they actually are.

IMHO, life is to short to be wasted on meaningless and trivial endeavors. Just focus on what's important in your life and let the rest fall to the wayside.

If Ubuntu/Linux didn't work on my system, I'd waste no time finding an OS that did and move on to more important issues. Such as why the BCS hates Bosie State or why my 4 year old granddaughter thinks she needs a horse for her birthday, the list goes on. ;)

Good Luck

Just my $0.02

---

### Post by hurtstotalktoyou on 2009-11-12
> **Tamlynmac said:**
> Just use what works and don't worry about or invest time/energy on what doesn't. IMHO, we often waste time convincing ourselves things are more important than they actually are.

IMHO, life is to short to be wasted on meaningless and trivial endeavors. Just focus on what's important in your life and let the rest fall to the wayside.

If Ubuntu/Linux didn't work on my system, I'd waste no time finding an OS that did and move on to more important issues. Such as why the BCS hates Bosie State or why my 4 year old granddaughter thinks she needs a horse for her birthday, the list goes on. ;)

Good Luck

Just my $0.02

All true.  However, I feel like maybe if enough people talk about how a particular, specific problem completely ruins the experience, the Ubuntu team will get the message that little things do add up.  I mean, consider that the major issue for me was an incompatibility with gxine---a program that most people probably never use.  What other seemingly small issues can become very big deals for certain people?

Oh, and of course it's nice to vent.  I feel a lot better now.

---

### Post by hurtstotalktoyou on 2009-11-12
> **3rdalbum said:**
> #1. I don't use Gxine - I can't comment sorry. Try removing the Gxine preferences file. (it's in a hidden file in your home directory).

#2. I'm not having any troubles with Samba, so I can't really comment - I did see a Samba update a while back so try applying your system updates. I tested 9.10 on almsot my whole home network when it was beta and if I'd had issue with Samba I would have reported them; do you want to file a bug at launchpad.net? If the Ubuntu devs don't know your problem, then they can't fix it.

#3. Screensaver inhibit also works fine for me in all video players. In VLC, the precise setting is:

Tools > Preferences
Under the "Show Settings" pane, hit "All".
Click on "Advanced" in the left pane, if it's not already selected. Choose "Inhibit the power management daemon during playback".

#4 No idea, I don't dual-boot.

#5 What exactly is saying that your disk is corrupted? Is it a SMART warning, or a message printed to dmesg?

#6 I can't remember what I used to use to access the Ubuntu partition; all I can remember is that it worked. Try a different ext2 driver on Windows?

Thank you for the suggestions, but I don't think there's much hope.  For example, the vlc issue is already [official](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/428884), insoluble through changing player settings.  I'm going to maybe stick it out for another day or two, with the gxine bug as my priority.  If I can fix that, then I'll probably see it through.  If not...  well, I'll be very unhappy.  Time will tell, I suppose.

---

### Post by solwic on 2009-11-12
> **Tamlynmac said:**
> Just use what works and don't worry about or invest time/energy on what doesn't. IMHO, we often waste time convincing ourselves things are more important than they actually are.

IMHO, life is to short to be wasted on meaningless and trivial endeavors. Just focus on what's important in your life and let the rest fall to the wayside.

If Ubuntu/Linux didn't work on my system, I'd waste no time finding an OS that did and move on to more important issues. Such as why the BCS hates Bosie State or why my 4 year old granddaughter thinks she needs a horse for her birthday, the list goes on. ;)

Good Luck

Just my $0.02

+1 to all that, especially the part about the BCS hating Boise State.  I'm starting to think the BCS is the Microsoft of the NCAAF.  

Anyway, @OP:  Good luck.  :biggrin:

---

### Post by Zoot7 on 2009-11-12
Intrepid (based on what I've read) seems to have been the best Ubuntu so far, as in people had the least amount of problems with it.
I actually skipped Intrepid and almost skipped Jaunty because i was so happy with Hardy, the only reason I upgraded was that I found Jaunty recognized my home built desktop's wireless card, and I didn't have to use ndiswrapper anymore.

Anyway, @OP stick with what works for you. :)

---

### Post by Tamlynmac on 2009-11-12
> hurtstotalktoyou
All true. However, I feel like maybe if enough people talk about how a particular, specific problem completely ruins the experience, the Ubuntu team will get the message that little things do add up.

Unfortunately, from what I understand the devs don't play here much. So if your intention is to inform the team - it probably isn't going to happen here.

However, if by venting here helps you to accept the situation and cope - I wish you the best.

As for getting "enough people" in the T&E to talk (without bias) about a specific problem. :)

As I said earlier - Good Luck

---

