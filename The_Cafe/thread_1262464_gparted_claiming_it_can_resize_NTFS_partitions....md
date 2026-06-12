---
title: "gparted claiming it can resize NTFS partitions..."
date: 2009-09-09
forum: The Cafe
---

### Post by earthpigg on 2009-09-09
...but we all know it can't. not reliably. certainly not reliably if there is data or Windows on that NTFS partition, anyways. source and proof [here]("http://ubuntuforums.org/showpost.php?p=7924951&postcount=9") and [here]("http://ubuntuforums.org/forumdisplay.php?f=326").

should this broken functionality be removed (or ask for super-duper-are-you-really-sure-confirmation) from gparted prior to it being packaged for inclusion in Ubuntu until such time as gparted/ubuntu can do it reliably and properly?

i know, i know... "its an upstream problem, gparted is not an ubuntu product!"

well, great. its *still* an upstream problem that affects *a whole ton of potential future Ubuntu users.*

the installer would simply say:

"hey chief, Ubuntu sees that you are attempting to tell it to resize a partition with Windows on it. If you want Windows to continue to function, please resize it in windows first, then come back to this LiveCD. are you positive you want to risk a 50/50 chance of borking Windows by letting Ubuntu attempt to resize it's partition?"

---

### Post by kk0sse54 on 2009-09-09
I've never had a problem resizing NTFS partitions with gparted

---

### Post by FuturePilot on 2009-09-09
I've resized NTFS partitions with Gparted. Always worked fine for me.

---

### Post by earthpigg on 2009-09-09
with Windows Vista or 7 on it?

shrunk it to 49% or less of its origional size?

without defragging?

---

### Post by starcannon on 2009-09-09
Resizing partitions is now, and for as long as I've been around, been a risky venture. Generally everything goes as planned, occasionally they do not, this is the truth regardless of what file system your resizing, and with no regard to the software your using to get the job done. Best bet, if you don't know what your doing, practice on something that doesn't matter; and, as always, BACKUP FIRST, then move forward. Everyone who is considering messing with partitions that contain valuable data should first meditate on Data Sutra.
Ed Gruberman meditate with me;
> 
 Ohm, eSata, usb, dvd, hard disk, removable, redundant, partition, backup, ohm. 

In this sutra inner and outer peace is found.

---

### Post by FuturePilot on 2009-09-09
> **earthpigg said:**
> with Windows Vista or 7 on it?
Yes

> shrunk it to 49% or less of its origional size?
Yes

> without defragging?
Yes

---

### Post by Newuser1111 on 2009-09-09
> **earthpigg said:**
> with Windows Vista or 7 on it?

shrunk it to 49% or less of its origional size?

without defragging?Yes, with Vista on it.

---

### Post by RabbitWho on 2009-09-09
I think that feature is fine if you know what you're doing. I don't know what I'm doing so I don't try it ('cept with swap drives)

I think it's an important function and it's silly to take it out just because most of us can't use it effectively. No one should never narrow down our choices,  just warn us when what we are doing is dangerous.

---

### Post by earthpigg on 2009-09-09
i certainly find these first responses interesting.

consider, from [gparted's website:]("http://gparted.sourceforge.net/faq.php")

> The following article by the How-To Geek contains useful information regarding resizing your Vista partition, **_and getting it to boot again_**.
[Using GParted to Resize Your Windows Vista Partition]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/")

and from [that link]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/"), recognized by gparted developers as the definative answer:
> Once it&#8217;s done, quit, remove the live cd and then reboot your computer. **_Unless you are very lucky, you&#8217;ll be greeted with this horrible error message_** saying &#8220;Windows Failed to start. A recent hardware or software change might be the cause.&#8221;

---

### Post by earthpigg on 2009-09-09
> **RabbitWho said:**
> I think it's an important function and it's silly to take it out just because most of us can't use it effectively. No one should never narrow down our choices,  just warn us when what we are doing is dangerous.

i agree, ergo option 3 of the poll :D

---

### Post by juancarlospaco on 2009-09-09
Microsoft don't recommend to resize NTFS without without defragging.
*Linux toturials too...*

Since Filesystem can be damaged*(logical level)* by unclean shutdown or something.

---

### Post by Exodist on 2009-09-09
> **earthpigg said:**
> ...but we all know it can't. not reliably. certainly not reliably if there is data or Windows on that NTFS partition, anyways. source and proof [here]("http://ubuntuforums.org/showpost.php?p=7924951&postcount=9") and [here]("http://ubuntuforums.org/forumdisplay.php?f=326").

should this broken functionality be removed (or ask for super-duper-are-you-really-sure-confirmation) from gparted prior to it being packaged for inclusion in Ubuntu until such time as gparted/ubuntu can do it reliably and properly?

i know, i know... "its an upstream problem, gparted is not an ubuntu product!"

well, great. its *still* an upstream problem that affects *a whole ton of potential future Ubuntu users.*

the installer would simply say:

"hey chief, Ubuntu sees that you are attempting to tell it to resize a partition with Windows on it. If you want Windows to continue to function, please resize it in windows first, then come back to this LiveCD. are you positive you want to risk a 50/50 chance of borking Windows by letting Ubuntu attempt to resize it's partition?"

When resizing ANY partition with ANY file system there is ALWAYS RISK.
I dont recall GParted saying anything was SAFE and I have used this program a good few times.

So dont get your feathers is a bunch if you was to lazy to back up all your files on DVD/CD before you crapped them all.

---

### Post by earthpigg on 2009-09-09
> **Exodist said:**
> When resizing ANY partition with ANY file system there is ALWAYS RISK.
I dont recall GParted saying anything was SAFE and I have used this program a good few times.

So dont get your feathers is a bunch if you was to lazy to back up all your files on DVD/CD before you crapped them all.

absolutely correct, no disagreement.

which has absolutely no affect on the fact that most potential future Ubuntu users know none of this and do none of this.

and even if they do -- wouldn't a warning be nice, for those that dont know, that windows is an order of magnitude or so more likely to be borked than a simple data partition, or a partition containing a Linux distribution?

as i demonstrated above, gparted *officially recognizes* that you are "*very lucky*" if windows boots normally after resizing a partition with windows installed using gparted.

---

### Post by murderslastcrow on 2009-09-10
Defragment the partition and run a disk check in Windows before you try to resize or partition. This is a primary feature that's integrated with installation, it would be foolish to remove it.

Again, I think the majority case is that there are no problems, and if it has bad sectors it already prevents you from modifying the partition.

I really don't see what the big problem is.

---

### Post by Icehuck on 2009-09-10
> **murderslastcrow said:**
> 

Again, I think the majority case is that there are no problems, and if it has bad sectors it already prevents you from modifying the partition.


According to the developers of GParted you are incorrect.

---

### Post by gn2 on 2009-09-10
I've only once re-sized an NTFS partition that held a Vista installation using Gparted.
It failed to boot afterwards, but I fixed it with a [Vista Recovery CD]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") easily enough.

---

### Post by lisati on 2009-09-10
I've only ever had one problem which *might* have had some connection with using gparted resizing an NTFS (Vista)  partition. Notice the emphasised "might". It was so easily fixed that I did not make the connection at the time and didn't bother investigating.

---

### Post by mcduck on 2009-09-10
Resizing NTFS has always worked for me perfectly.

But then again, I defrag my windows partitions and maintain proper backups of my important data even without anybody telling me to do so. That's just a common (and important) part of using a computer.

---

### Post by MGaddict2000 on 2009-09-10
just resized an NTFS w/ windows 7 on it. Shrunk 40% off the drive. Then I moved the partition down 100MB. Win7 didn't like it at first, had to use the install CD to repair the bootloader. Not really a problem went fine. Now I've got Win7 and Ubuntu on the same drive with no problems. I lost no data what so ever. Always remember to defrag before you resize a partition. If you don't defrag first and you shrink it smaller then the last bit of data on the drive, you will loose that data. Thats true for any file system, not just NTFS.

---

### Post by -grubby on 2009-09-10
I've tried resizing NTFS partitions in gparted a couple times. For some reason, it took upwards of 5 hours each time. I vote option 3.

---

