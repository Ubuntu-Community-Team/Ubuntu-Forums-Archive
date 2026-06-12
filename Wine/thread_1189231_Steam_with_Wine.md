---
title: "Steam with Wine"
date: 2009-06-16
forum: Wine
---

### Post by BlackRat90 on 2009-06-16
Hey all i just changed to linux and im a big fan of the Half Life series. i managed to get steam installed on my computer using wine, but it doesnt seem to work properly. I went to try to install half life with steam and it says it worked, but now its been trying to download the files for 3 days now with no end in sight.
other problems i have been having is that my mouse doesnt seem to click right, it always thinks the cursor is at one place when its not?

Any help at all would be great, i really want to play my games again!
Nate~

---

### Post by ZackM on 2009-06-16
I, in all honesty, wouldn't suggest trying to run Steamengine games with wine. You'd run into a lot of issues.

---

### Post by BlackRat90 on 2009-06-16
is there any other way??

Also i restarted steam and it seemed to fix al the the problems, but i doubt there gone for good.

---

### Post by ZackM on 2009-06-16
> **BlackRat90 said:**
> is there any other way??

Also i restarted steam and it seemed to fix al the the problems, but i doubt there gone for good.

Yeah, you're bound to run into more problems, unfortunately. Even if you get the application to run, it'll probably be laggy. That also depends on your computer specs. But, I'm guessing anything, especially on any source server, is going to limit your fps and probably just make you mad.

---

### Post by BlackRat90 on 2009-06-16
well its worth a try, i dont think it will be my computer limiting the game (4gb ram, 1gb video card, 3GHz processor)

---

### Post by ZackM on 2009-06-16
Oh, well no... Your computer is definitely strong enough. Try it out with wine, and see if it's real laggy or not. A couple of choices you have are dual booting Ubuntu and XP, or running XP as a virtual machine from Ubuntu. The latter is going to also be pretty slow, but may be quicker, given your specs, than wine.

---

### Post by Bios Element on 2009-06-16
> **ZackM said:**
> I, in all honesty, wouldn't suggest trying to run Steamengine games with wine. You'd run into a lot of issues.

This is not helpful as it 'is' possible. And there's no such thing as a "Steamengine". There's either HL1 or Source Engine for most of the big Steam games.


Steam can run pretty well via Wine. Read the [WineHQ Page]("http://appdb.winehq.org/appview.php?versionId=1554") for tips on how to get it running well.
[http://appdb.winehq.org/appview.php?versionId=1554](http://appdb.winehq.org/appview.php?versionId=1554)
Note that there are separate pages for each Steam game for how to get a particular game working well.

I've had great luck with HL2, EP1, EP2, GMod, CS:S and HL1.

---

### Post by SBFC on 2009-06-16
> **Bios Element said:**
> 
I've had great luck with HL2, EP1, EP2, GMod, CS:S and HL1.

I second that for HL2. Granted this was over a year ago and I haven't really tried since then; but I played through all of HL2 using only Wine. Had great performance with it as well.

Again though, this was definitely not with the current builds of Wine so I have no idea how it runs now. I would hope just as well if not better. I recommend you give it a shot though.

---

### Post by BlackRat90 on 2009-06-17
ok update!
i got the game to run! sorta
i went into the setting of wine and tried starting steam in a virtual desktop, and i think its running way better! *knocks on wood*

thanks for all your help/input on my matter
Nate~

---

### Post by SBFC on 2009-06-17
I did remember a few things that helped me when I was playing HL2. In the 'My Games' window you can right-click on a game (HL2 in my case) and choose 'Properties'. From there click the 'Set Launch Options' button.

I used *-novid* to prevent the opening Valve movie from playing (at the time it lagged horribly). I think I also used *-gl* to run in opengl but looking for it now I can't see that it is actually a valid flag. Must have just pulled it out of no where.

[This page has more of the flags you can play with.]("http://www.tweakguides.com/HL2_7.html")

---

