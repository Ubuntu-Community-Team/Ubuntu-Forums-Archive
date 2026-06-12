---
title: "Any technique to copy video files from a dvd with a lot of scratches?"
date: 2009-08-11
forum: The Cafe
---

### Post by praveesh on 2009-08-11
After copying upto about half of the video, nautilus displays error message that it can't read from the source  . I am able to copy the video upto that part . Did you encounter any situation like this . Do you know any hack or technique to copy video files (or any file)from a dvd(or cd)with a lot of scratches?

---

### Post by koshatnik on 2009-08-11
You can buy wipe clothes that help to fix scratched optical media. They work well.

---

### Post by realzippy on 2009-08-11
..you can try "isobuster".
Its windows software,but runs under wine:

[http://appdb.winehq.org/appview.php?iAppId=1384](http://appdb.winehq.org/appview.php?iAppId=1384)

---

### Post by qazwsx on 2009-08-11
Use ddrescue.

Actually some DVDs are "prescratched" for copy protection (since css is pretty useless) while there are no issues with standalone players.

If you are familiar with mplayer and mencoder use -ss and -endpos switches in order to get whole movie playable (as much as possible).

---

### Post by realzippy on 2009-08-11
> **qazwsx said:**
> Use ddrescue.

Actually some DVDs are "prescratched" for copy protection (since css is pretty useless) while there are no issues with standalone players.

If you are familiar with mplayer and mencoder use -ss and -endpos switches in order to get whole movie playable (as much as possible).

ddrescue does not try to restore broken bits,it replaces them with zero;
but of course you could try it:
Type in terminal:

ddrescue if=/dev/cdrom of=~/myscratcheddvd.iso

---

### Post by praveesh on 2009-08-11
> **qazwsx said:**
> Use ddrescue.

Actually some DVDs are "prescratched" for copy protection (since css is pretty useless) while there are no issues with standalone players.

If you are familiar with mplayer and mencoder use -ss and -endpos switches in order to get whole movie playable (as much as possible).

I have mencoder installed. What command should I use?

---

### Post by Grenage on 2009-08-11
Try a non-coloured card polish and gently massage it into the disc using a soft cloth.  Leave it to dry for about an hour then try again.

That's a last-ditch solution, because the resin tends to eat away the CD over time.  I'd personally give dd_rescue a try.

---

### Post by cariboo on 2009-08-11
I have the hand powered version of [this]("http:///www.walmart.com/catalog/product.do?product_id=4062503"), I've saved a lot of cd/dvd's using it.

---

### Post by mcduck on 2009-08-11
> **cariboo907 said:**
> I have the hand powered version of [this]("http:///www.walmart.com/catalog/product.do?product_id=4062503"), I've saved a lot of cd/dvd's using it.

That's a good option. I have a bottle os some strange stuff meant for this purpose, it looks like a mix of solvent and plastic combined with some small granules. Couple of drops on a disk and few minutes of serious wiping with a soft cloth and even deep scratches seem to disappear.

Also some video game stores offer disk repair services..

---

### Post by wojox on 2009-08-11
Scratched Cd's I use toothpaste on.

---

### Post by Grenage on 2009-08-11
I personally find toothpaste to be as effective as jam, or sausage fat.  if it works, it's pot luck.  You want to use something that dries clear.

---

### Post by praveesh on 2009-08-11
Thanks to all the isobuster works great

---

### Post by forrestcupp on 2009-08-11
> **realzippy said:**
> ddrescue does not try to restore broken bits,it replaces them with zero;
but of course you could try it:
Type in terminal:

ddrescue if=/dev/cdrom of=~/myscratcheddvd.iso

But if you're trying to save files from a dvd that won't even open up at all, ddrescue can be a lifesaver to extract the salvageable files.  It's come through for me in the past.

---

### Post by Chronon on 2009-08-11
> **Grenage said:**
> I personally find toothpaste to be as effective as jam, or sausage fat.  if it works, it's pot luck.  You want to use something that dries clear.

:confused:

Toothpaste contains silica particles which can polish any surface of equal or lesser hardness.  Neither jam nor sausage fat contains abrasive particles that would give similar polishing action.  The idea is not to leave the toothpaste on the DVD -- it's to polish the scratches out and then rinse and dry it.

Edit:
It occurs to me that the fat may act as a kind of solvent and soften the scratches a bit.  I have never tried this and am curious about whether Grenage was being serious and is speaking from experience.

---

### Post by swoll1980 on 2009-08-11
> **Grenage said:**
> I personally find toothpaste to be as effective as jam, or sausage fat.  if it works, it's pot luck.  You want to use something that dries clear.

Toothpaste, and creamy peanut butter, both work pretty good in my experience.

---

### Post by starcannon on 2009-08-11
> **praveesh said:**
> After copying upto about half of the video, nautilus displays error message that it can't read from the source  . I am able to copy the video upto that part . Did you encounter any situation like this . Do you know any hack or technique to copy video files (or any file)from a dvd(or cd)with a lot of scratches?
Edit: Swoll beat me to it, I'll leave my own technique up for you to consider anyway.

Okay, this will sound strange, but I swear it works.
Buff the DVD out with peanut-butter and a wet paper towel, go until the scratches are not deep enough to refract light in a meaningful way, but be careful not to go clear through the plastic and into the media. I usually look at it, and stop, rinse, pat dry, and attempt playback, skipping around the dvd to make sure it appears to all work; when I can see the opening credits, skip to the middle and see some of that, and the closing credits, then I'm reasonably sure that I've done enough; begin ripping. 

This is a bit tedious, but it does work, peanut butter is a fine abrasive, with the benefits of coming with its own oil; the wet paper towel will work as an abrasive as well, but do try to let the peanut butter do most of the work.

GL

---

