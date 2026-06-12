---
title: "how to burn a bootable Windows XP cd via K3B?"
date: 2007-01-15
forum: Windows
---

### Post by kcy29581 on 2007-01-15
Hi all,

I'm trying to burn a bootable Windows XP Professional cd. I have all the cd files with Service Pack 2 slipstreamed, and the bott image extracted from my non-SP2 cd.

I tried setting the Load Segment to: 0x7c0 and the Loaded Sectors to 4 as I would in Nero; but this hasn't worked.

Any ideas?

---

### Post by kcy29581 on 2007-01-15
bumping...

---

### Post by kcy29581 on 2007-01-16
Anyone?

---

### Post by TheRingmaster on 2007-01-16
> **kcy29581 said:**
> Anyone?



I don't think what you are doing is even legal. Did you even pay for it?

---

### Post by bodhi.zazen on 2007-01-16
Best way to burn a Windows XP Professional cd is with a blow torch or small atomic :p

You should be able to burn the iso with K3b like any other ios, but be careful with that thing. Bad enough if it comes form microsoft, but in your case who knows where it's been ? Who knows what malignant code it may harbor ?

Bad omen if you ask me.

---

### Post by Sef on 2007-01-16
Moving to jail since this thread violates the forum guidelines.

---

### Post by matthew on 2007-01-19
We apologize for the confusion. We misread the original post...totally missed the fact that the poster was doing something legal for people who own a legally licensed copy of WinXP and that is described on Microsoft's web site. Slipstreaming is a valid topic.

We blew it this time...sorry. We're restoring the thread to its proper location and we hope an answer is found to the original question.

---

### Post by irish_flu on 2007-01-19
> **kcy29581 said:**
> Hi all,

I'm trying to burn a bootable Windows XP Professional cd. I have all the cd files with Service Pack 2 slipstreamed, and the bott image extracted from my non-SP2 cd.

I tried setting the Load Segment to: 0x7c0 and the Loaded Sectors to 4 as I would in Nero; but this hasn't worked.

Any ideas?

What's not working?  Does the ISO burn?  If it burns, does it begin to boot (yet fail) or can your machine not boot to the CD at all?

Can your machine boot OK to other CDs (like the Ubuntu CD)?

---

### Post by Frak on 2007-01-19
Just burn as an iso, but if you ever can, use WINE and use the program [nLITE]("http://nliteos.com/index.html"), it is the best slipstreamer ever (Totally Legal!)

---

### Post by kcy29581 on 2007-01-20
I have only tried booting the ISO I created in a Virtual Machine; it didn't work. A non-SP2 (original) Windows XP Professional disk does boot in the same Virtual Machine.

Maybe it's the settings: In Nero I would use "07C0" as the Load Segment, but in K3B I use "0x7C0". Maybe I need to replace the "4" for the Number of Loaded Sectors for something else?

Admins: Thanks for reinstating this thread.

Trolls: Thanks for the jokes.

---

### Post by the.dark.lord on 2007-01-22
> **bodhi.zazen said:**
> Best way to burn a Windows XP Professional cd is with a blow torch or small atomic :p

You should be able to burn the iso with K3b like any other ios, but be careful with that thing. Bad enough if it comes form microsoft, but in your case who knows where it's been ? Who knows what malignant code it may harbor ?

Bad omen if you ask me.

:lolflag: 
I absolutely agree. And, how about nukes on Redmond?

---

### Post by affi on 2007-02-15
I had an error meaning CDBOOT: NTLDR is missing (or something).

After "googeling" for that error I found out that this error appears if the bootloader can't find the
"I386/SETUPLDR.BIN".

Then I renamed the files and folders for the CD to uppercase and burned the cd via:
# mkisofs -D -b BOOT.IMG -no-emul-boot -v -N -l -no-iso-translate -relaxed-filenames -o cd1.bin orig/ 
and tried with:
#  qemu -cdrom cd1.bin -boot d
it worked!


Sorry for my bad english... I hope it's understandable :-)

Marco

---

### Post by affi on 2007-02-15
> **Frak said:**
> Just burn as an iso, but if you ever can, use WINE and use the program [nLITE]("http://nliteos.com/index.html"), it is the best slipstreamer ever (Totally Legal!)

nLite needs .NET 2.0 that wont work at all...

---

### Post by Lucifiel on 2007-08-13
> **affi said:**
> I had an error meaning CDBOOT: NTLDR is missing (or something).

After "googeling" for that error I found out that this error appears if the bootloader can't find the
"I386/SETUPLDR.BIN".

Then I renamed the files and folders for the CD to uppercase and burned the cd via:
# mkisofs -D -b BOOT.IMG -no-emul-boot -v -N -l -no-iso-translate -relaxed-filenames -o cd1.bin orig/ 
and tried with:
#  qemu -cdrom cd1.bin -boot d
it worked!


Sorry for my bad english... I hope it's understandable :-)

Marco

Hmmm... I'm wondering how this poster managed to burn his cd and to get it to run.

---

### Post by lptr on 2007-12-17
> **Lucifiel said:**
> Hmmm... I'm wondering how this poster managed to burn his cd and to get it to run.

Yes, me too.

I today ran into a similar problem. ((For the trolls here:  we would not try illegal things - we do own real XP licences - we cannot do it illegally because ourselves & our customers existence would be harmed otherwise, so... for the dudes not believing this: Come by I will show U))

I currently do some testings from inside vmware. I did create a legalwinxxpro.iso with NERO using WindowsXP. But I cannot believe, why in K3B it should not be as easy as with NERO / XP. 

Did anyone got this working. I would have used exactly same files I did use, when I successfully created that **legal**[COLOR=Red]xppro.iso[/COLOR] from Windows (this does boot inside vmware wksta - so raw data files are ok).

My tries when booting that k3bgenxp.iso inside vmware-wksta are resulting in:

```
CDBOOT: Couldn't find NTLDR
```any ideas?

rob*

---

### Post by r0cks0ul on 2008-01-07
Hey according to this site you cant use 0x7c0 as a load segment

[http://www.tacktech.com/display.cfm?ttid=297](http://www.tacktech.com/display.cfm?ttid=297)

[IMG]http://www.tacktech.com/images/articles/297/create10.png[/IMG]

:guitar::lolflag:

---

### Post by lptr on 2008-01-07
> Hey according to this site you cant use 0x7c0 as a load segment

[http://www.tacktech.com/display.cfm?ttid=297](http://www.tacktech.com/display.cfm?ttid=297)This source probably used a hacked version of NERO. :lolflag:

Seeing is believing. I did it with this offset 7c0 and it DOES boot. Important is the number of sectors to load. 

I could not get this settings (see the picture) well known and tested by myself with NERO working in K3B.

Any real (working) comments?

rob*

---

### Post by inversekinetix on 2008-01-07
When naming the disk did you use the correct LABELS for your version of windows?  without them it will not work.

---

### Post by lptr on 2008-01-08
> **inversekinetix said:**
> When naming the disk did you use the correct LABELS for your version of windows?  without them it will not work.

Burned a CD with NERO named it simply & non standard 'XPP_DE'. This definitively does boot (I have to admit this is a developer version of XPp provided by MSDN subscription back in 2003. Maybe this makes the difference - don't know). 

The same raw data dropped into K3B with any settings that came into my mind did not work.

Again my question: Did anyone successfully create a WindowsXP boot CD using K3B (NOT NERO!). If so, could you please describe in detail what settings you did apply?

Thanks.

rob*

---

### Post by Andreas.k on 2008-04-04
Ok,

affi is right, I just tried what he did, I first had to copy the 'Microsoft Cooperation.img' into the directory (which I call XP with all the slipstreamed files inside) and make and iso:

mkisofs -D -b Microsoft\ Corporation.img -no-emul-boot -v -N -l -no-iso-translate -relaxed-filenames -o cd1.iso XP/

Then I used k3b to burn this iso 'cd1.iso'. It works. Thanks

---

### Post by phantaszm on 2008-04-25
After much testing (using VirtualBox) and comparison (using isoinfo, Retail WinXP Pro SP2 CD), I've found the proper settings for k3b. 

But first, allow me to present my findings.

Settings that DON'T matter
- load segment
- volume name

Settings that DO matter
- file system

So now, k3b settings.
In "edit boot images"
- Boot Load Segment: 0x0 (My retail CD actually shows 0x0, but you can use 0x7C0 if you really want)
- Boot Load Size: 0x0

In "Properties" -> "Filesystem"
- Select "DOS Compatibility" then click "Custom..." (I selected DOS... just cause it's the cleanest template)

Then make sure the following are checked
- Generate Joliet extensions
- Omit version numbers...
- Allow 31 characters...
- Allow ~ and #...
I left everything else unchanged

Now burn and you're good to go.


Actually, if you're really lazy, all you really have to do is 
- Select DOS Compatibility then click "Custom..."
- Check Allow untranslated  ISO9660 filenames.


Have fun!

---

### Post by it-frog on 2008-05-01
Hi phantaszm,

thanks a lot for your testing.

It was exactly I'm looking for.

---

### Post by changedsoul on 2008-05-10
I too was struggling with this and I thank you for figuring out the K3b settings to get the image to burn...I found some other help full info as well.

I personally dont really trust boot images from places I dont know, so I would prefer to extract my own usind dd, but could not figure it out...untill I came across this site:

[http://linuxtuneup.blogspot.com/2006/01/slipstreaming-windows-cd-under-linux.html](http://linuxtuneup.blogspot.com/2006/01/slipstreaming-windows-cd-under-linux.html)

he makes use of the isoinfo command.
I used isoinfo -d dev=/dev/sr0 and looked for my 'bootoff' value.
I have an xp home sp1 cd and it has a bootoff value of 222 for the second number. not sure if its all the same or what, but I used 222 to get my image and bured it with K3b with settings found from above and it workd great

isoinfo -d dev=/dev/your_cdrom
dd if=/dev/your_cdrom of=boot.img bs=2048 count=1 skip=your_bootoff_value

cheers :guitar:

---

### Post by svgt on 2008-11-17
Hi,

I tried to burn a bootable cd with K3B. I was not successful. I got the message:

CDBOOT: Couldn't find NTLDR

I did not find at which place I should edit k3b setting > edit boot images, or change 

Select DOS Compatibility then click "Custom..."

I use the last K3B in Ubuntu 8.04.

Regards,

Svgt

---

