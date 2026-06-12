---
title: "Has anyone tried my tutorial/install ubuntu on a pendrive? whats your experience ?"
date: 2015-05-01
forum: The Cafe
---

### Post by newbie14 on 2015-05-01
Is there anyone install ubuntu using my steps? ([http://ubuntuforums.org/showthread.php?t=2272475](http://ubuntuforums.org/showthread.php?t=2272475)). Or has anyone install ubuntu on a flash drive. And boot said ubuntu from flash drive? What are your experiences in working with flash-drive-booted ubuntu? what is your story?

I experience many slow responses, like when I hover the cursor over the "files" program on the desktop sidebar, the "files" label appear after 1 or 2 seconds. When I left click a file in the "files" program, the orange highlighter appears 2-2.5 seconds later. And when I press enter when a text file is highlighted on the "files" program, the text editor program appears 4-5 seconds after. And the "files" program turns grayscale for a few moments... I don't blame anyone though... because I believe ubuntu.iso image file is designed to be installed on hard disk or virtual desktop environment with larger and faster data transfer bandwidth rate to ram, instead of flash drives which are a lot lot slower. There are some more experiment I want to do with my current flash-drive-booted ubuntu though... after that, I'll consider buying another hard disk for the ubuntu to be installed on. And then I expect faster responses from ubuntu o.s.

---

### Post by ian-weisser on 2015-05-02
> **newbie14 said:**
> I believe ubuntu.iso image file is designed to be installed on hard disk or virtual desktop environment with larger and faster data transfer bandwidth rate to ram, instead of flash drives which are a lot lot slower.

Sort of. You should indeed experience a (frustrating) lag on a USB 1.1 or USB 2.0 (but not on USB 3.0). The lag is indeed due to the too-slow data transfer. And HDD/SSD data transfer is indeed faster still.
But the system design or image design has nothing to do with it. The system is designed to run as fast as the hardware will permit it to run.

---

### Post by gordintoronto on 2015-05-03
With a 32 GB USB 3.0 flash drive plugged into a USB 2.0 port, performance was OK most of the time. Sometimes there would be a delay of four or five seconds, with nothing useful happening. However, I think my flash drive has failed, as it gives an error message instead of booting.

---

### Post by sammiev on 2015-05-03
I did one up about 3 weeks a go before I saw your post. Will try it again using yours but it is much as I used. :)

---

### Post by newbie14 on 2015-05-05
I am glad.

---

### Post by MoebusNet on 2015-05-05
One of the features of Puppy Linux I've always likes is the ability to load the entire OS into RAM. That really speeds up response times! I wonder whether or not one of the *buntu variants could pull a similar stunt (stares off dreamily into the distance)...

I've got 32Gb RAM, that should be able to hold a 1.3 Gb iso image of Ubuntu, or an 8Gb installation image in memory. Sure would speed things up!

---

### Post by fkkroundabout on 2015-05-06
^ yes RAM speeds are significantly faster than solid state, of course. but unfortunately it seems most operating systems don't/didn't utilize this entirely, but probably because of the pitfalls of RAM volatility.

EDIT: it could also be for reasons of economics that RAM disks never really took off big time. because, as RAM began to fall in price, SSDs also did, and the latter i'd expect is far easier to transition to from HDDs, for all the software that already existed

```
hdparm -t /dev/sdb
```
you can use this to find a general idea of the read speed of any kind of drive.
a USB 3 flash drive i bought is three times slower on a USB 2 port, than a HDD over SATA. so ubuntu was pretty slow. of course, ubuntu with unity is not a light distribution, though

---

### Post by sudodus on 2015-05-06
It can work quite well with installed Ubuntu systems booted from USB devices. I agree with what has been said already in this thread, and I want to add some links with more details,

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

and this link (particularly post #6) [Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

*Edit*: There is also the following link, describing a system that you might want to try, if you have a lot of RAM
[URL="http://ubuntuforums.org/showthread.php?t=1594694"]
Making Ubuntu Fast using RAM (updated and simplified)[/URL]

---

### Post by newbie14 on 2015-05-06
> **MoebusNet said:**
> ... load the entire OS into RAM.

Would you care to make the tutorial of it?

---

### Post by sudodus on 2015-05-06
See the last link in post #8

---

### Post by Sableyes on 2015-05-09
Have not tried your guide. I did however run Ubuntu of a flash drive as a main PC for 6 months.

Reason being netbook had a Wndows 8 drive that didn&#8217;t like me dicking about with it, but I wanted to keep it as we had no other Windows installs in the house. I shoved a Sandisk USB3 Cruser Fit into a USB3 port. When I installed Ubuntu onto it it treated it like any other hard drive. A change in boot order and I was away with 14.04. Ran smoothly, no pauses or delays, only really used for photo editing and web browsing with odd games like Swords & Sorcery and Broken Sword.

After 6 months of not booting Windows 8, I found out upgrading Ram and Hard Drives in my netbook was easy as popping off the keyboard, so 8gb ram went in with a 128gb Sandisk SSD sata drive and now I have a super speedy netbook and no longer use USB3.

---

### Post by robsoles on 2015-05-09
valium [s]required[/s] [COLOR=#0000ff]most desirable[/COLOR].

---

### Post by newbie14 on 2015-05-10
> **Sableyes said:**
> Have not tried your guide. I did however run Ubuntu of a flash drive as a main PC for 6 months.

Reason being netbook had a Wndows 8 drive that didn’t like me dicking about with it, but I wanted to keep it as we had no other Windows installs in the house. I shoved a Sandisk USB3 Cruser Fit into a USB3 port. When I installed Ubuntu onto it it treated it like any other hard drive. A change in boot order and I was away with 14.04. Ran smoothly, no pauses or delays, only really used for photo editing and web browsing with odd games like Swords & Sorcery and Broken Sword.

After 6 months of not booting Windows 8, I found out upgrading Ram and Hard Drives in my netbook was easy as popping off the keyboard, so 8gb ram went in with a 128gb Sandisk SSD sata drive and now I have a super speedy netbook and no longer use USB3.

What steps did you use for installing ubuntu to the flash drive?

---

### Post by Sableyes on 2015-05-10
Exactly the same steps as I install Ubuntu on a normal hard drive. I need 2 USB drives, first used as an installer, secound as a hard drive.

Put the ISO onto 1 USB drive as the installer using UnetBootin.

Boot from that USB drive. Run the installer. Select to install on to a secound USB drive.

Finish installing, and reboot booting off secound drive. 

That is it. Nothing else. I have only Sandisk thumb drivers, 2 cruzers and 3 cruzer fits. Never need any additional steps.

---

