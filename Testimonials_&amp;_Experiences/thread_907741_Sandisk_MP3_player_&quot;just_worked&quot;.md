---
title: "Sandisk MP3 player &quot;just worked&quot;"
date: 2008-09-01
forum: Testimonials &amp; Experiences
---

### Post by HDave on 2008-09-01
Bought a $50 Sansa Clip 2GB mp3 player today, despite the fact it said on the box that it "Requires Windows XP or Windows Vista".

Nontheless, I came home, plugged it into my laptop, and within 2 seconds nautilus opened it right up having immediately recognized the exact model.

I them clicked on the link in Nautilus to open up Rhythmbox.

Next thing I knew I was dragging and dropping albums in Rhythmbox to the player.  When the progress bar was finished, I looked at the player, it also indicated the transfer was complete.  After unplugging the device, it told me it was "scanning new files"...this lasted about 30 seconds.

Only 3.5 minutes after plugging it in, I was listening to music.

HOW AWESOME IS UBUNTU!!!!!!

---

### Post by aysiu on 2008-09-02
Same here. I'm very happy with my Sansa Clip.

---

### Post by windozehater on 2008-09-02
i also bought a 1gb clip and love it, works perfectly except,(theres always a but) when its plugged into my hub, and i do a couple reboots or file backups to my external HDD the clip locks up. no big deal though, just hold the power slider on for 20sec. and it resets without any data loss

---

### Post by HDave on 2008-09-02
I just wish that Ubuntu would help Sandisk and the other vendors adjust the text of their box to say:  "Requires Windows XP, Windows Vista, or Ubuntu 8.04 or beyond."

How cool would that be....

---

### Post by 3rdalbum on 2008-09-03
I hate to break up the party, but:

1. Your Sandisk MP3 players sound like they're designed as "mass storage" devices; you could load those things with MP3s on any USB-compatible operating system

2. It would be risky for Sandisk to advertise Linux compatibility - Ubuntu 8.04 originally broke support for some mass storage-type devices, possibly including your Sandisk ones. It's been fixed now of course, but such an incident worries any hardware manufacturer.

---

### Post by Keyper7 on 2008-09-03
> **3rdalbum said:**
> 1. Your Sandisk MP3 players sound like they're designed as "mass storage" devices; you could load those things with MP3s on any USB-compatible operating system

...as a mass storage device. But the system recognizing them as MP3 players and Rhythmbox working with them, like the OP described, is a different story.

My current Sony MP3 player is only recognized as a mass storage device. Rhythmbox does not list it and the model is not detected.

My previous player (forgot the model) was recognized as a player and Rhythmbox opened up when it plugged it in.

---

### Post by aysiu on 2008-09-03
Even if they're "compatible" as mass storage devices, I think that at least is worth mentioning.

---

### Post by HDave on 2008-09-05
I would agree with you Keyper7, except that Rhythmbox "knew" it was a music player somehow.  I could drag and drop files to it and everything worked.

If I inspect it in Nautilus, it has a folder structure on the storage device.  Somehow Ubuntu knows where the music files are located.

Re compatibility:  I'm not looking for Linux compatibility, but "Ubuntu 8.04 and beyond" compatibility.  Shame on us for breaking that compatibility with a new release...that should NEVER happen.  Perhaps the folks at Ubuntu and the community at large could create a hardware testing database with an entry for every single device...and use it during beta testing.

---

### Post by notbitmonk on 2008-09-10
I bought one for my daughter because it was at a very good price.  Before that, I mailed Sansa to ask (I bought the Clip before the response cam though).  Here is what they said:
[INDENT]> Thank you for contacting SanDisk Technical Support. It is our goal to make sure you have all the resources you need to get the most from your product.

Please be note that the minimum system requirement for the Sansa Clip is Windows XP and a Windows Media Player 10. These are required for transferring subscription music which requires the player to be in "MTP" mode and the "MTP" drivers from the computer.

The player would recognize and play .ogg files and also can have the "MSC" mode (non-subscription music) by updating its firmware.

You may see how to update firmware on a Linux platform through this link:

[http://forums.sandisk.com/sansa/board/message?board.id=clip&thread.id=6720](http://forums.sandisk.com/sansa/board/message?board.id=clip&thread.id=6720)

MSC functions as a mass storage device, and will show up on your computer as an external drive (eg "E:\"), just like a USB key or portable hard drive. You can simply drag and drop your music files directly to the drive or folder of the player without using any application such as Windows Media Player.

MTP enables Windows XP, Vista and any other supported OS to recognize the device as a standard media device. If you are transferring music that you have purchased or music that are licensed and/or protected, then you need to use the MTP mode with the use of an application like Windows Media Player 10.

Should you have any further inquiries or concerns, please do not hesitate to reply to this message or send another inquiry via an Email.

Best regards,
Christine B.
SanDisk Technical Support[/INDENT]
When I plugged it in the first time, Rhythmbox recognized it and during transfer, it converted my ogg files to mp3.  The clip was not able to recognize the tags (artist, title, etc.).  I did the update as explained in the link from Sansa support and was able to have the Clip play the ogg files correctly and show the correct tags.  The update was done manually.  I tried the Sansa firmware updater in Wine (1.1.4) but it didn't work.  If you transfer ogg files from Rhythmbox to the Clip, it will convert the files to mp3 and any spaces in the names are converted to underscores.  I ended up making folders dragging the files in Nautilus.  I think this is something for the developers to look into.  I will try mailing Sansa to ask them about this behavior.

---

### Post by Crafty Kisses on 2008-09-10
Nice to hear. :)

---

### Post by HDave on 2008-09-11
Yeah - I am impressed they actually addressed Linux on their website.  They should put that on the box.

Regarding the ogg problems, I store all my music as FLAC, but use the gnome "sound converter" app to automatically convert them to mp3 on a backup drive.  I used the mp3 files to transfer to the sandisc, the wife's ipod, my laptop, etc.  so I didn't see this problem.  Thanks for the info.

---

