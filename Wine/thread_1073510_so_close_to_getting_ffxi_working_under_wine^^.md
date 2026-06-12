---
title: "so close to getting ffxi working under wine^^"
date: 2009-02-18
forum: Wine
---

### Post by NeferalCrossfireX on 2009-02-18
just 1 problem!
whenever i get past the agree screen it just gos black. ive followed all the steps on the ffxi appdb page, and ive tried wine version 1.1.6 1.1.12 1.1.13 and 1.1.14, but the same thing happens!!! heres the terminal read out of the problem.

fixme:imm:ImeSetCompositionString PROBLEM: This only sets the wine level string
fixme:imm:ImmGetOpenStatus (0x12d1d0): semi-stub

theres gotta be a fix right :D

---

### Post by hikaricore on 2009-02-18
Hate to tell you but there are no errors in that output, it's hard to "fix" something that isn't essentially broken.
What you're seeing is just debug output which probably has little to do with your issue.

Is/are your video hardware/drivers working properly?

---

### Post by NeferalCrossfireX on 2009-02-18
> **hikaricore said:**
> Hate to tell you but there are no errors in that output, it's hard to "fix" something that isn't essentially broken.
What you're seeing is just debug output which probably has little to do with your issue.

Is/are your video hardware/drivers working properly?

it dosent matter anyway cos i found the fix and now it works perfectly!

---

### Post by fluxrider on 2009-02-24
What was your fix?

I had the same issue that it would go black after the agree screen.

Found a patch:
[http://www.nabble.com/0001-Sanity-Check-in-ImmSetCompositionStringA-and-ImmSetC.patch-td18769013.html](http://www.nabble.com/0001-Sanity-Check-in-ImmSetCompositionStringA-and-ImmSetC.patch-td18769013.html)

And instructions:
[https://help.ubuntu.com/community/BuildingWineFromSource](https://help.ubuntu.com/community/BuildingWineFromSource)

But now I get a black screen with music after I select my character, and a loading is done. (right before it should transition to the game world)

Any help would be appreciated.

Best,

---

### Post by fluxrider on 2009-03-12
Follow up: I was using wine 1.1.15 and 1.1.16, but after reading more about my problem, I found that version 1.1.13 works fine. Regressed.

---

### Post by axelroo on 2009-04-04
There are a couple things which need to be done to get around the blank screen problem.

#1 dxdiagn.dll: If you have a working copy of Windows, browse to WINDOWS\system32\, then run "regsvr32 dxdiagn.dll". Once successful, run winecgf and add pol.exe as an application (if you haven't already), select it, then under the Libraries tab, select and add dxdiagn.dll in Native mode. After that, give it the OK and close.

If you do NOT have a working copy of windows.  Download winetricks and run it. You will see directx9; install it. It will add its generic dxdiagn.dll automaticly. Follow the steps above afterwards.

#2 MMC Sanity Check -  This is the part which remedies the blanking after either the Agreement or Character Select.  This is a patch. Go here: [http://appdb.winehq.org/commentview.php?iAppId=1992&iVersionId=2739&iThreadId=40305](http://appdb.winehq.org/commentview.php?iAppId=1992&iVersionId=2739&iThreadId=40305)

You can try to drop imm32.dll.so into /usr/lib32/wine or patch it manually.  You should now be able to play at ease.

---

