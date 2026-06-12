---
title: "Shred or wipe an old hard drive?"
date: 2013-03-01
forum: Security
---

### Post by KegHead on 2013-03-01
Hi!

I'm recycling my old 140 gb hd.

I want to completely wipe the data off.

Which is better;

Wipe or shred

or something else?

Thanks!

KegHead

---

### Post by ptn107 on 2013-03-01
```
shred -fuvz -n 3 /dev/sda1
```
substituting your target disk or partition of course.

---

### Post by Ms. Daisy on 2013-03-01
Unless you work for the NSA, the quick mode of wipe would be more than sufficient. 

I haven't used shred but it seems from the man page that it's designed to erase files more than the whole system (although it has options to do the whole disk). Make sure to read the man page if use shred.

dd would be effective by writing 0s or random 1s and 0s over the whole disk.

---

### Post by KegHead on 2013-03-01
> **Ms. Daisy said:**
> Unless you work for the NSA, the quick mode of wipe would be more than sufficient. 

I haven't used shred but it seems from the man page that it's designed to erase files more than the whole system (although it has options to do the whole disk). Make sure to read the man page if use shred.

dd would be effective by writing 0s or random 1s and 0s over the whole disk.

Hi!

What would be the terminal commands?

KegHead

---

### Post by Ms. Daisy on 2013-03-01
Ideally you want to issue the commands from a live CD, not from the disk that you're erasing (in case you weren't aware).

also I would recommend ensuring that you don't have any external / additional hard drives attached or mounted to prevent erasing the wrong disk.

I'm on my phone right now and would just Google the commands, I suppose you could probably do that just as well as I could. 

If you want to post the commands here to ensure you've got the right ones before executing them, that would be prudent.

---

### Post by Soul-Sing on 2013-03-01
wipe is more timeconsuming. If its your entire harddisk: -> dban

---

### Post by KegHead on 2013-03-01
Hi!

Is it possible to wipe/shred just unused space via terminal?

Thanks!

KegHead

---

### Post by CharlesA on 2013-03-01
> **Soul-Sing said:**
> wipe is more timeconsuming. If its your entire harddisk: -> dban

+1. I used dd instead of dban the last time I did it cuz I couldn't get dban to boot.

```
sudo dd if=/dev/urandom of=/dev/sdX bs=1M
```

> **KegHead said:**
> Hi!

Is it possible to wipe/shred just unused space via terminal?

Thanks!

KegHead

See here:
[http://superuser.com/questions/19326/how-to-wipe-free-disk-space-in-linux](http://superuser.com/questions/19326/how-to-wipe-free-disk-space-in-linux)

---

### Post by KegHead on 2013-03-01
Wow!

Great info!

KegHead

---

### Post by kurt18947 on 2013-03-01
Excellent advice about doing it from a live install and disconnect everything but the target disk.  These procedures are not recoverable by mere mortals, or even minor deities, I'd guess.

---

### Post by KegHead on 2013-03-04
Hi!

Bleach Bit has a wipe option.

Does anyone know how many passes it makes?

Any other info about Bleach Bit?

Thanks!

KegHead

---

### Post by KegHead on 2013-03-07
Hi!

So, if I use Bleach Bit 5 times in a week, does that mean it's like running wipe to do a five time wipe at one setting?

KegHead

---

### Post by CharlesA on 2013-03-07
Doubt it, but I don't use Bleachbit, so I cannot confirm or deny that for sure.

---

### Post by KegHead on 2013-03-08
Hi!

I reinstalled Ubuntu after using wipe. I was asked if I wanted to wipe the hd before installing.

I said yes, was this really a wipe?

KegHead

---

### Post by Paqman on 2013-03-08
> **KegHead said:**
> 
Is it possible to wipe/shred just unused space via terminal?

```
sudo sfill -l -l -v -z /target
```
This will write a single pass of zeros to all the free space on that partition, which is fast and a completely permanent wipe. You'll need to install [secure-delete]("apt:secure-delete") to get the tool sfill.

---

### Post by KegHead on 2013-03-08
Hi!

Thanks Paqman.

What if I wanted to do more than one pass with zero's?

Thanks!

KegHead

---

### Post by HermanAB on 2013-03-09
These erase threads always amaze me.  A secure erase facility has been built into all disk drive controllers for at least ten years, yet no-one seems to be aware of it.  Use hdparm to activate it.

---

### Post by unspawn on 2013-03-09
Sure enough these erase threads amaze me as well but more for the fact that nobody ever tells 'em to *actually verify the end result* (regardless of DBAN being able to verify passes). Even w/o practical forensics experience it should be just a common sense thing. Else why make an effort in the first place?..

---

### Post by KegHead on 2013-03-09
Hi!

I'm just trying to figure out the correct terminal command using wipe three (3) times and an final wipe with zeros, only for free space.

Can anyone advise, I don't want to make a mistake!

Thanks!

KegHead

---

### Post by sudodus on 2013-03-09
You can use ***zerofree ***for ext file systems (and I think it is enough with one pass, unless you need military level security).

```
sudo apt-get install zerofree
``` See ```
man zerofree
```
for example
```
sudo umount /dev/sda1
sudo zerofree /dev/sda1
```

You can use dd for fat and ntfs file systems. Also in this case you should unmount them before the zeroising.

So now you have several tips:

shred, quick mode of wipe, dban (for while drive), dd (with if=/dev/urandom or if=/dev/zero), BleachBit, sfill, zerofree.

... but of course, no pay, no guarantee ;-)

---

### Post by sudodus on 2013-03-09
> **unspawn said:**
> Sure enough these erase threads amaze me as well but more for the fact that nobody ever tells 'em to *actually verify the end result* (regardless of DBAN being able to verify passes). Even w/o practical forensics experience it should be just a common sense thing. Else why make an effort in the first place?..
Do you mean that DBAN is the only good choice?

---

### Post by Ms. Daisy on 2013-03-09
No. He has a point- it's good practice to verify that the wipe successfully wiped the drive regardless of which you use.

---

### Post by sudodus on 2013-03-09
> **Ms. Daisy said:**
> No. He has a point- it's good practice to verify that the wipe successfully wiped the drive regardless of which you use.

I see :-)

Which method would you suggest?

It's easy if using dd to write a file named blank until the partition is full and inspect it before wiping it. But the other wiping methods are said to be more efficient.

---

### Post by Ms. Daisy on 2013-03-09
> **sudodus said:**
> I see :-)

Which method would you suggest?Thermite. ;)

As with most things in Linux there are numerous ways to accomplish the same thing. Just pick one you like.

---

### Post by sudodus on 2013-03-09
> **Ms. Daisy said:**
> Thermite. ;)

As with most things in Linux there are numerous ways to accomplish the same thing. Just pick one you like.

You can use an axe and/or sledgehammer too :P

But I meant a method to verify any of the suggested non-destructive methods to wipe. Maybe DBAN would be the best of those mentioned in this thread. I've heard of information retrieved from harddisks that have burned in a fire. Maybe that's a fairy-tale, maybe not ;-)

---

### Post by Paqman on 2013-03-09
> **KegHead said:**
> 
What if I wanted to do more than one pass with zero's?


You can check the instructions for any command by prefixing the command with man (for "manual"). So:
```
man sfill
```
Will tell you what the various options do. Most man pages also have a fairly current version available on the net, just Google for it.

As for sfill, omitting one of the -l switches makes it do two passes instead of one. There's absolutely no point in doing so, it won't make it wipe any better and just makes it take twice as long. A single pass renders your data unrecoverable to any software tool.

---

### Post by Ms. Daisy on 2013-03-09
> **sudodus said:**
> You can use an axe and/or sledgehammer too :P

But I meant a method to verify any of the suggested non-destructive methods to wipe. Maybe DBAN would be the best of those mentioned in this thread. I've heard of information retrieved from harddisks that have burned in a fire. Maybe that's a fairy-tale, maybe not ;-)Oh lol I misunderstood. 

> To verify that our wiping program wrote zeros to the drive we will use the xxd command with the autoskip option.  The output of the command on a drive that has been written with zeros should be only three lines.  The first line should be the starting offset followed by row of zeros, the second line will be an asterisk (*) to indicate identical lines, and the third line should be the starting offset of the final line, also followed by a row of zeros.  If the drive contains anything other than zeros, the data will be displayed.  Type the following into the terminal to verify that the target drive was properly wiped.
```
sudo xxd -a /dev/sda
``` from this 
[http://www.epyxforensics.com/node/44](http://www.epyxforensics.com/node/44)

---

### Post by coldcritter64 on 2013-03-09
> **Ms. Daisy said:**
> <snip>...> To verify that our wiping program wrote zeros to the drive we will use  the xxd command with the autoskip option.  The output of the command on a  drive that has been written with zeros should be only three lines.  The  first line should be the starting offset followed by row of zeros, the  second line will be an asterisk (*) to indicate identical lines, and the  third line should be the starting offset of the final line, also  followed by a row of zeros.  If the drive contains anything other than  zeros, the data will be displayed.  Type the following into the terminal  to verify that the target drive was properly wiped. ... <code snipped>

Thanks for posting that Ms. Daisy, I'll never again have to sit with eyes glued to the surface scanner viewer window of Spinrite 6 (from [noparse]grc.com[/noparse]) :lol: I was actually doing surface scans for drive maintenance, not for verifying, but it is great to know that when I use shred or dd on a drive I can now check the end results.

Hexdumping a complete drive and autoskipping the empty space in a terminal, impressive. Many thanks and regards from coldcritter64.

---

### Post by sudodus on 2013-03-09
> **Ms. Daisy said:**
> Oh lol I misunderstood. 

 from this 
[http://www.epyxforensics.com/node/44](http://www.epyxforensics.com/node/44)

Thank you :-)

So for example

1. for the first drive (when totally wiped)
```
sudo xxd -a /dev/sda
```

2. for the free space (when dd is used to create the file blank)
```
sudo xxd -a blank 
```
and then blank is removed
```
sudo rm blank
```
*Edit*: and the output should look like this
```
0000000: 0000 0000 0000 0000 0000 0000 0000 0000  ................
*
00ffff0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
```

---

### Post by WasMeHere on 2013-03-09
> **KegHead said:**
> Hi!

I'm just trying to figure out the correct terminal command using wipe three (3) times and an final wipe with zeros, only for free space.

Can anyone advise, I don't want to make a mistake!

Thanks!

KegHead

Hi Jim :-)

Boot from another drive, for example your Ubuntu install CD or USB drive. Mount the partition with your file browser.

Assume it is partition [FONT=Courier New]**/dev/sda1**[/FONT] and that it is mounted on [FONT=Courier New]**/media/ubuntu**[/FONT]

```
cd /media/ubuntu
```
Check with ```
df .
``` and when OK write to the file [FONT=Courier New]**blank**[/FONT] until the partition is full with
```
sudo dd if=/dev/urandom of=blank bs=4096
```
Now you have one random write. Then use shred for two random writes and one zero pass on the file **[FONT=Courier New]blank[/FONT]** with
```
shred -n 2 -z blank
```
Now check (if you like) with
```
sudo xxd -a blank
```
You should get something like this output (the last address is probably different, but the content should be zeros all the way)
```
0000000: 0000 0000 0000 0000 0000 0000 0000 0000  ................
*
00ffff0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
```
Finally remove [FONT=Courier New]**blank**[/FONT]
```
sudo rm blank
```
and that's it :-)

> **Ms. Daisy said:**
> Oh lol I misunderstood. 

 from this 
[http://www.epyxforensics.com/node/44](http://www.epyxforensics.com/node/44)

Thank you :KS for your valuable link to
```
sudo xxd -a /dev/sda
```

---

### Post by HermanAB on 2013-03-11
Good grief, this thread will never end it seems.

The hdparm utility can invoke a secure erase command that is built into the device driver of all hard disk controllers for the past ten years or more.  Only the disk drive controller itself can erase the whole disk - including the spaces between tracks.  Ordinary software cannot do that.

So if you want to really erase the data (short of melting the disk with a torch) then use hdparm.  Any other method is just playing.

---

### Post by sudodus on 2013-03-11
> **KegHead said:**
> Hi!

I'm just trying to figure out the correct terminal command using wipe  three (3) times and an final wipe with zeros, only for free space.

Can anyone advise, I don't want to make a mistake!

Thanks!

KegHead

> **HermanAB said:**
> Good grief, this thread will never end it seems.

The hdparm utility can invoke a secure erase command that is built into the device driver of all hard disk controllers for the past ten years or more.  Only the disk drive controller itself can erase the whole disk - including the spaces between tracks.  Ordinary software cannot do that.

So if you want to really erase the data (short of melting the disk with a torch) then use hdparm.  Any other method is just playing.

HermanAB, you can state your opinion, but you need not ***mock*** people who want help with a particular task, and people who help with this particular task.

---

### Post by WasMeHere on 2013-03-12
> **KegHead said:**
> Hi!

I'm recycling my old 140 gb hd.

I want to completely wipe the data off.

Which is better;

Wipe or shred

or something else?

Thanks!

KegHead

> **KegHead said:**
> Hi!

I'm just trying to figure out the correct terminal command using wipe three (3) times and an final wipe with zeros, only for free space.

Can anyone advise, I don't want to make a mistake!

Thanks!

KegHead

> **HermanAB said:**
> Good grief, this thread will never end it seems.

The hdparm utility can invoke a secure erase command that is built into the device driver of all hard disk controllers for the past ten years or more.  Only the disk drive controller itself can erase the whole disk - including the spaces between tracks.  Ordinary software cannot do that.

So if you want to really erase the data (short of melting the disk with a torch) then use hdparm.  Any other method is just playing.

@*HermanAB*,

I guess you are writing about the 'ATA Security Feature Set' described in ```
man hdparm
```

This manual is rather intimidating with a lot of warnings: DANGEROUS, USE AT YOUR OWN RISK, VERY  DANGEROUS, EXCEPTIONALLY DANGEROUS. DO NOT USE THIS OPTION!! You cannot expect people to use it without a lot of hand-holding. It is not enough to write a general comment about hdparm. If you want people to use it, you need to explain in detail how to do it or at least link to a good tutorial. 

I have a few questions to you:

- What you think of the following link (is it good enough to recommend in this thread)?

[[COLOR="#FF0000"]https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase[/COLOR]]("https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase")

- Is this method with hdparm good for the first quoted post (the OP), asking for completely wiping a hdd?

(I would think so, but I want your opinion.)

- Is there a method with hdparm for the second quoted post, asking for wiping only the free space?

I can't find any way to do that except indirectly: first make an image of the drive with for example Clonezilla, then wipe the whole drive and finally restore the partition(s) from the image. So I suggested the old way with dd. Please explain what you would advice in this situation!

- And finally, do you think it is worth the time and wear to check if the wipe was successful?

---

### Post by Soul-Sing on 2013-03-12
i agree with Olle Wiklund

---

### Post by HermanAB on 2013-03-12
If you find hdparm intimidating, then get the free Windows utility here:
[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

---

### Post by roten on 2013-03-13
> **Olle Wiklund said:**
> - What you think of the following link (is it good enough to recommend in this thread)?

[[COLOR=#FF0000]https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase[/COLOR]]("https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase")

- Is this method with hdparm good for the first quoted post (the OP), asking for completely wiping a hdd?
(I would think so, but I want your opinion.)
...
- And finally, do you think it is worth the time and wear to check if the wipe was successful?

I wiped a drive successfully using that ata wiki link (at least I think so). View my thread and give feedback, if you wish :-)

[[COLOR=#ff0000]http://ubuntuforums.org/showthread.php?t=2124829[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2124829")

I checked with xxd but I won't do it again, at least not the whole drive. It is very slow.

---

### Post by HermanAB on 2013-03-13
Yup, that is the right way to do it.

---

### Post by WasMeHere on 2013-03-14
After a couple of days I'll summarize my findings about these questions

> **Olle Wiklund said:**
>  ... about the 'ATA Security Feature Set' described in ```
man hdparm
```
...
[[COLOR="#FF0000"]https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase[/COLOR]]("https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase")

- Is this method with hdparm good for the first quoted post (the OP), asking for completely wiping a hdd?


***Yes***
> 
- Is there a method with hdparm for the second quoted post, asking for wiping only the free space?

***No***
> 
- And finally, do you think it is worth the time and wear to check if the wipe was successful?
Maybe the first time to learn, or maybe you interrupt it after a while, or *if you need to be 100% sure* it's all wiped, otherwise ***no***.

Finally, thank you for sharing your experiences, *roten* :KS

---

