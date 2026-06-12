---
title: "Broadband Dongles (3)"
date: 2009-10-11
forum: The Cafe
---

### Post by Swagman on 2009-10-11
*I was going to post this in the "Karmic Koala" thread but decided it probably warrants it's own Life !!*
************************************************************************

   My mate had 9:04 on his lappy (I installed it) but yesterday we went over the Carphone Warehouse in Bretton Centre, Peterborough to buy a **3** broadband dongle for him as he has no net access where he lives.

We took his lappy with us so we could "Live Test" before buying. Surprisingly the guy behind the desk didn't spout the "That's not supported" line but was quite helpful and used his very limited knowledge of Ubuntu to the max. He inserted the dongle and up it popped on the desktop. I should've took over from here but as this was new to me also I let him take the reins.  He  (wrongly as it turned out) assumed we should install under WINE, which he did. Unfortunately, even though the GUI came up ok it just wouldn't connect.

After getting quite a queue behind us I said we'd buy it anyway as it's a dual boot machine ( His eyes roll !! ..haha). We moved to one side and installed ok in windowsXP.. Horror moment when we realised the reason everything was happening so slowly was because Windows had just "Auto-updated".. Fortunately it had connected to their Wi-Fi to do this. (Point to self.. Switch off Auto install Updates in Windows... He can update round my house).

I Was that pleased with the guys service I purchased a LG cookie phone for the wifes Chrimbo pressie. It was a shame however that we couldn't get the dongle running in Ubuntu whilst everyone else was "Sneaking a Peak".

At home... I googled and faffed about a bit before reading someone say that Karmic sorts it out.

"sudo update-manager -d"

That person was right. **SUCCESS**.. Job sorted. Don't like the Login in screen though as it lists users.

Just thought I'd share with you all.

---

### Post by 3rdalbum on 2009-10-11
That's a good story... but when I got a 3 prepaid broadband modem it was one of the E160s that works out-of-the-box on Intrepid, and a friend of mine has a similar modem that was also out-of-the-box on Intrepid.

Looks like they've changed their preferred modem, but at least it works on Karmic!

---

### Post by Swagman on 2009-10-11
> **3rdalbum said:**
> That's a good story... but when I got a 3 prepaid broadband modem it was one of the E160s that works out-of-the-box on Intrepid, and a friend of mine has a similar modem that was also out-of-the-box on Intrepid.

Looks like they've changed their preferred modem, but at least it works on Karmic!

Yeah.. It's a huawei modem stick thing. Karmic picked it up no probs.  Maybe the guy installing via WINE b0rked something ? I uninstalled at home though and it still wasn't picked up. After the dist upgrade  network manager picked it up no probs.


[**THIS**](http://threestore.three.co.uk/payg/dealsummary.aspx?offercode=DSLPP494) is the plan he's  on. (PAYG)

---

### Post by markbuntu on 2009-10-13
Some of those broadband dongles need to be initialized on a windows machine to set up the account etc before they will work on a linux machine. Virgin actually tells you to do this and you can do it with any windows machine.

---

### Post by SomeGuyDude on 2009-10-13
Heeheehee. Dongle.

---

