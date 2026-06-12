---
title: "Need The Help Of Someone More Techie Than Myself *Sniff* (Noob in trouble)"
date: 2006-04-20
forum: The Cafe
---

### Post by Kernel Sanders on 2006-04-20
Hi Everyone! :D 

I have a problem.... :( 

I have [**This Computer**]("http://support.packardbell.com/uk/item/?sn=038957920132&g=1400")

The first CD/DVD Drive on the tower was [**This**]("http://support.packardbell.com/uk/item/index.php?i=spec_DVD_LiteonDVD166S&psn=038957920132")

The second CD/DVD Drive on the tower was [**This**]("http://support.packardbell.com/uk/item/index.php?i=spec_nec_nd2510a&psn=038957920132")

But, due to the first one breaking, I decided to splash out, and replace the both of them with two of [**This**]("http://www.microdirect.co.uk/ProductInfo.aspx?ProductID=12074&GroupID=42")

The way I did this was just to do a straight swap. I made sure the jumper settings on the one's going in exactly matched the one's coming out, and I used the same cables as the old ones.

But, the result is, both my brand spanking new DVD-RAM drives are performing extreamly poorly. For example, i'll insert a CD, and 30 seconds will pass before they autorun.

Anyone have any idea's of why this could be?

Did I do something wrong? (Bearing in mind I am certainly not the most techie of people :( )

My OS is Windows XP Pro SP2, as i'm still using the Ubuntu Live CD at this stage, as I dont plan to dual boot until Dapper goes final. :)

However, I dont think that this is an OS issue? More like a hardware one? Because when I reformatted the computer, the install CD's had poor performance too?

In short....... HELP! I am in real trouble here! :cry: 

I would be ever so greatful for ANY help ANY/ALL of you could provide! [-o< 

Thanks again!

John :)

---

### Post by slipk487 on 2006-04-20
y need to turn dma on them for them to run better u can get [automatix]("http://ubuntuforums.org/showthread.php?t=138405")
and it can enable it

---

### Post by Randomskk on 2006-04-20
Perhaps new drivers under Windows XP would help?

See if the drives came with a driver disk.

---

### Post by Kernel Sanders on 2006-04-20
[QUOTE=slipk487]y need to turn dma on them for them to run better u can get [automatix]("http://ubuntuforums.org/showthread.php?t=138405")
and it can enable it[/QUOTE]

Automatix doesnt work with the Live CD :(

[QUOTE=Randomskk]Perhaps new drivers under Windows XP would help?

See if the drives came with a driver disk.[/QUOTE]

Windows installed them itself, no drivers came with them. And tbh, the fact that  the poor performance was present during the Windows XP install leads me to believe that its maybe a hardware problem. :(

Anyone have any ideas?

Thanks for your help!

John :)

---

### Post by Randomskk on 2006-04-20
Make sure only the CD drives are on the IDE cable, and set both their jumpers to Cable Select (google for the position, I can't remember it right now - sorry), and then in the BIOS check things like DMA - as mentioned above - are on, and look for any other options that may impact performance.

---

### Post by Kernel Sanders on 2006-04-21
[QUOTE=Randomskk]Make sure only the CD drives are on the IDE cable, and set both their jumpers to Cable Select (google for the position, I can't remember it right now - sorry), and then in the BIOS check things like DMA - as mentioned above - are on, and look for any other options that may impact performance.[/QUOTE]

Is that true? Both jumpers on the DVD RAM drives must be set to "cable select"?

Because the drives that came out (That the manufacturer installed) wernt set up like that?

John :)

---

### Post by l4v4_f10w on 2006-04-21
Not much help, but placing them on cable select wont resolve the problem, all it is saying is that you dont know whether if the drives shud be master or slave. If you havent try setting the drives on your ID2 slot and place one as master and ther other as slave. Not sure if it will help, if anything you can try to upgrade the firmware.

---

### Post by Mr_J_ on 2006-04-21
If I got this right you had 2 CD drives and you replaced each with 1 DVD drive.

If you have two drives, you should:
- On each IDE cable 1 of the connectors has to link to the motherboard
- 1 has to link to a drive with SLAVE jumper chosen
- 1 has to be linked to a drive with MASTER jumper chosen

This is how it's normally done!
Not all drives have these jumpers in the same spot.

The performance.
Do you have DMA turned on in Ubuntu? If not the speed might be normal.
Windows does this by default I believe.

Is it the CD? Do others perform better? Is it the type of CD? DATA, Sound or Video perform diferently?
Does it happen with DVD?

If it's with all CD and DVD, in Windows and Ubuntu, than you might want to take those puppies to the shop and request replacements. At least try them in another PC...

---

### Post by Stormy Eyes on 2006-04-21
I'd like to help, but I don't have any experience with Packard-Bell gear.

---

### Post by Kernel Sanders on 2006-04-21
[QUOTE=Mr_J_]If I got this right you had 2 CD drives and you replaced each with 1 DVD drive.

If you have two drives, you should:
- On each IDE cable 1 of the connectors has to link to the motherboard
- 1 has to link to a drive with SLAVE jumper chosen
- 1 has to be linked to a drive with MASTER jumper chosen

This is how it's normally done!
Not all drives have these jumpers in the same spot.

The performance.
Do you have DMA turned on in Ubuntu? If not the speed might be normal.
Windows does this by default I believe.

Is it the CD? Do others perform better? Is it the type of CD? DATA, Sound or Video perform diferently?
Does it happen with DVD?

If it's with all CD and DVD, in Windows and Ubuntu, than you might want to take those puppies to the shop and request replacements. At least try them in another PC...[/QUOTE]


I had: 

1 CD/DVD player/reader/whatever drive
1 DVD=RW +/- DL Drive

Now I have:

1 DVD-RAM Drive
1 DVD-RAM Drive

IIRC, the cable went from the motherboard into the 2nd CD/DVD Drive, and from that drive into the 1st CD/DVD Drive.

So the 2 CD/DVD Drives were connected to the motherboard via the same cable.

My BIOS has DMA turned on too....

Could I need new cables or something? Would the old cables be good enough to run 2 DVD-RAM drives??

Thanks very much for your help!

John :)

---

### Post by Mr_J_ on 2006-04-21
I've had a dude that had to change his cables to new ones otherwise his Optical Drives would not work at all.

Try some new cables or some cables from another computer. Friends might be able to get you some.

Sounds like a bad drive, except it's happening to both... Software sounds most likelly, although it could just as easilly be showing some more symptoms you're not noticing.

Strange noises are usually no good. Computers aren't suposed to make those...

Straws!? Anyone?

---

### Post by blueturtl on 2006-04-21
> The way I did this was just to do a straight swap. I made sure the jumper settings on the one's going in exactly matched the one's coming out, and I used the same cables as the old ones.

Now usually when you use incorrect jumper settings the system refuses to boot at all, but in this case I have to ask if you took into consideration that the drives aren't always identical in their settings? I know that hard-drives from different manufacturers definately don't use same jumper placement for the same settings, so you may want to doublecheck those to see if that has anything to do with the problem.

Re-check the jumper-settings!

Also I know this isn't very helpfull at all, but I've noticed while performing tech support on a Packard Bell system that a lot of the hardware and software seems oddly tied together and customized. Some things are not standard and might be hard to replace with anything other than what Packard Bell has to offer. You may want to contact them for support, flash your BIOS etc.

---

