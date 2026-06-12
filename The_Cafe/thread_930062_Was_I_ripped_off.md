---
title: "Was I ripped off"
date: 2008-09-25
forum: The Cafe
---

### Post by 4th guy on 2008-09-25
I have bought an external hard disk which supposedly has a 500gb capacity. The problem is that it only has 465gb. I know that some manufacturers prefer to show straight shiny numbers, like 500gb as opposed to 465gb, but right now I can not help but feel as if I have somehow have been ripped off. There was no number on the box other than 500gb.
Any ideas or advice?

(for those who were wondering, it's "only" 7% less, but I paid money for those missing 35gb as well)

EDIT: even if we take 1gb as 1000mb (as "defined" on the box), I still would have 488gb as opposed to 465gb.

---

### Post by DrMega on 2008-09-25
It is common for manufacturers to quote the unformatted capacity. That said, if it doesn't mention 500mb anywhere, then maybe you've been had.

---

### Post by lisati on 2008-09-25
It does seem rather a big difference for something "right out of the box" which hasn't been used, even allowing a little bit for what the OS grabs for its overheads and hidden files.

---

### Post by hessiess on 2008-09-25
manufactures treet a gigabyte as 1000 MB, when it is actualy 1024 MB. the filesystem will also be using some of the drive.

---

### Post by chris4585 on 2008-09-25
Depends, always look to see what they define as 1 GB, most manufactures define 1 GB as 1000mbs and not the correct 1024mbs.

---

### Post by lisati on 2008-09-25
> **hessiess said:**
> manufactures treet a gigabyte as 1000 MB, when it is actualy 1024 MB. the filesystem will also be using some of the drive.

Ah, I forgot that in my response.

---

### Post by a-converted-sparky on 2008-09-25
Exactly as stated above, the issue is formatted capacity vs. unformatted capacity see [http://www.hardwaresecrets.com/article/482](http://www.hardwaresecrets.com/article/482)

---

### Post by billgoldberg on 2008-09-25
> **4th guy said:**
> I have bought an external hard disk which supposedly has a 500gb capacity. The problem is that it only has 465gb. I know that some manufacturers prefer to show straight shiny numbers, like 500gb as opposed to 465gb, but right now I can not help but feel as if I have somehow have been ripped off. There was no number on the box other than 500gb.
Any ideas or advice?

(for those who were wondering, it's "only" 7% less, but I paid money for those missing 35gb as well)



No, that seems right.

They are using 1000mb = 1gb, when in reality it's 1024mb = 1gb.

And then some of the space will be taken up by some other stuff, so 465gb seems ok. I have around the same space on my WB digital 500gb external drive.

So actually it is a rip-off. But they are ripping off everyone, not just you.

---

### Post by Nepherte on 2008-09-25
> **hessiess said:**
> manufactures treet a gigabyte as 1000 MB, when it is actualy 1024 MB. the filesystem will also be using some of the drive.
1GB (1*10^9) = 1000MB (1*10^6)
The difference lies in bytes versus bits. A capital B indicates bytes, whereas a b indicates bits. If it said 1Gb, as you suggested, it is correct and the operating system just uses another measure unit (bytes).

Note: 1 byte = 8 bits.

---

### Post by yelsn on 2008-09-25
You weren't ripped off.  Basically the HDD manufacturer uses a different definition of GB than your OS.  You can see this wikipedia page for more information:  [http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)

[QUOTE="wikipedia.org"]This means that a 500 GB hard disk drive would appear as "465 GB".[/QUOTE]

---

### Post by markp1989 on 2008-09-25
my 500gb sata only has 463gb when formated, its just a marketing con

---

### Post by Bölvaður on 2008-09-25
may I remind you that ext3 uses small % of the hdd for "jugling" or what ever it is called. Atleast it uses some space that isn't summed up as the available disk space. Without it you would need to defragment your harddisk like you would do in any other inferi... no wait let me stop here.

---

### Post by lukjad on 2008-09-25
> **4th guy said:**
> I have bought an external hard disk which supposedly has a 500gb capacity. The problem is that it only has 465gb. I know that some manufacturers prefer to show straight shiny numbers, like 500gb as opposed to 465gb, but right now I can not help but feel as if I have somehow have been ripped off. There was no number on the box other than 500gb.
Any ideas or advice?

(for those who were wondering, it's "only" 7% less, but I paid money for those missing 35gb as well)

EDIT: even if we take 1gb as 1000mb (as "defined" on the box), I still would have 488gb as opposed to 465gb.
This is standard. When they say 500GB, they mean 5,000,000,000 Bytes, not the 536,870,912,000 bytes you should get. I know the pain.

---

### Post by spupy on 2008-09-25
Gigabyte = 1000 Megabytes
Gibibyte = 1024 Mebibytes
Also, as said, formatting takes space, too.

---

### Post by klange on 2008-09-25
> **spupy said:**
> Gigabyte = 1000 Megabytes
Gibibyte = 1024 Mebibytes
Also, as said, formatting takes space, too.
Um... what? I've never heard of any such term.
Gigabyte = 1024 Megabytes
Megabyte = 1024 Kilobytes
Kilobyte = 1024 Bytes
Byte = 8 Bits

Then there's the *Drive Manufacturer's Gigabyte*...

---

### Post by blastus on 2008-09-25
It's just one of those subtle marketing scams, I mean spins. This is why I never believe what is stated on any product because there is always some misrepresentation of facts, some stretching of the truth or something that is clearly open to multiple interpretations.

---

### Post by spupy on 2008-09-25
> **WindowsSucks said:**
> Um... what? I've never heard of any such term.
Gigabyte = 1024 Megabytes
Megabyte = 1024 Kilobytes
Kilobyte = 1024 Bytes
Byte = 8 Bits

Then there's the *Drive Manufacturer's Gigabyte*...
Giga=1000*mega
Mega=1000*kilo
Gibi=1024*mebi
Mebi=1024*kibi
Giga, mega, kilo are SI units, meaning 10^9, 10^6 and 10^3 respectively. Giga is 10^3 * mega, mega is 10^3 * kilo.
"Kibi" comes from "kilobinary", meaning "kilo" in Base 2. Kilo in base 2 is 2^10 = 1024. Same goes for gibi- and mebi-.
Source: [http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
The confusion comes from the fact that disk manufacturers are using one of the prefixes, the user expects another and the OS reports something else.

---

### Post by klange on 2008-09-25
> **spupy said:**
> Giga=1000*mega
Mega=1000*kilo
Gibi=1024*mebi
Mebi=1024*kibi
Giga, mega, kilo are SI units, meaning 10^9, 10^6 and 10^3 respectively. Giga is 10^3 * mega, mega is 10^3 * kilo.
"Kibi" comes from "kilobinary", meaning "kilo" in Base 2. Kilo in base 2 is 2^10 = 1024. Same goes for gibi- and mebi-.
Source: [http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
The confusion comes from the fact that disk manufacturers are using one of the prefixes, the user expects another and the OS reports something else.

They do not apply as such for byte representations, which are specifically base 2. Again, I've never heard of a gibi.

Google concurs:
Q: 1 gigabyte in megabytes
1 gigabyte = 1024 megabytes
Q: 1 megabyte in kilobytes
1 megabyte = 1024 kilobytes
Q: 1 kilobyte in bytes
1 kilobyte = 1024 bytes
Q: 1 byte in bits
1 byte = 8 bits

**e**: From the looks of it, you didn't read the entire article.

---

### Post by FranMichaels on 2008-09-25
You could google gibibyte too right?
I hadn't heard of it either until somewhat recently.

[http://en.wikipedia.org/wiki/Gibibyte](http://en.wikipedia.org/wiki/Gibibyte)

The tip off for me was the Gnome System Monitor.

It uses GiB, MiB, etc.

---

### Post by jdong on 2008-09-25
> **Bölvaður said:**
> may I remind you that ext3 uses small % of the hdd for "jugling" or what ever it is called. Atleast it uses some space that isn't summed up as the available disk space. Without it you would need to defragment your harddisk like you would do in any other inferi... no wait let me stop here.

To clarify on this point:

(M)**ANY** filesystem filled near the brim (i.e. the last 5-10% of its capacity) will behave very poorly as it struggles to find empty holes to place new data. This includes taking a horrific amount of time (on the orders of minutes) to write a 1MB file hanging the system in the process at the most extreme, but almost certainly writing extremely fragmented files that severely degrade the read performance.

EXT3 does a favor for you by reserving that last 5% or so of disk capacity to root so that a user cannot accidentally or intentionally fill the disk to its capacity and degrade IO performance. In addition, this also means that malicious users cannot lock out root because of a disk-full condition trying to log in!

It is a feature and is good for you, but if you have to have that last 5% you can remove this limit with tune2fs.

---

### Post by tdrusk on 2008-09-25
> **FranMichaels said:**
> You could google gibibyte too right?
I hadn't heard of it either until somewhat recently.

[http://en.wikipedia.org/wiki/Gibibyte](http://en.wikipedia.org/wiki/Gibibyte)

The tip off for me was the Gnome System Monitor.

It uses GiB, MiB, etc.
interesting

---

### Post by jdong on 2008-09-25
Just to point out, Gibibyte and the similar (Metric) **bi**nary byte prefixes were invented after this base-10 vs base-2 confusion was well established.


Pop quiz: On 1.44MB labeled 3.5" diskettes, MB refers to:

(a) Megabytes
(b) Mebibytes
(c) Neither/Both

---

### Post by FranMichaels on 2008-09-25
> **jdong said:**
> Just to point out, Gibibyte and the similar (Metric) **bi**nary byte prefixes were invented after this base-10 vs base-2 confusion was well established.


Pop quiz: On 1.44MB labeled 3.5" diskettes, MB refers to:

(a) Megabytes
(b) Mebibytes
(c) Neither/Both

a) :)

---

### Post by jdong on 2008-09-25
> **FranMichaels said:**
> a) :)

Incorrect.

---

### Post by Bölvaður on 2008-09-25
b) as MB (,KB and GB) was renamed because of this confusion about 4 years ago I belief.

Btw you forgot to say that there is a log and "backup" of things you are doing so if there will be power cutoff no data will be lost between processes. And that is included in the ~5%

*EDIT* MB KB GB
*Addition*
Also 5 years ago the difference was sometimes represented in capital and lovercase but it never caught on I guess

---

### Post by Bölvaður on 2008-09-25
double post

---

### Post by jdong on 2008-09-25
> **Bölvaður said:**
> b) as MB (,KB and GB) was renamed because of this confusion about 4 years ago I belief.


Incorrect. Which only leaves one answer: The 1.44MB floppy consists of 1440 Kibibytes. Since floppy tracks were better numbered by base-2 units it's been a convention to go by 1024 bytes per kilobyte. However, only 720*2 (1440) of them are available on a dual-side high-density floppy but the marketing guys called it 1.44MB. Now is that a MB-KiB? MB/KB*KiB? Go figure :D


> 

Btw you forgot to say that there is a log and "backup" of things you are doing so if there will be power cutoff no data will be lost between processes. And that is included in the ~5%


That's not an accurate description of the ext3 metadata journal (ls ~/.journal) which is only 16-32MB given the size of the volume and version of mke2fs used. The metadata journal also only protects filesystem structure changes in transit, not general data. It doesn't turn EXT3 into a fully atomic filesystem like ZFS or reiser4.

> 
*Addition*
Also 5 years ago the difference was sometimes represented in capital and lovercase but it never caught on I guess
Well back in the days the lowercase "b" stood for bit, and was used to denote RAM module capacities a lot. i.e. you'd buy a 8Mb RAM module (8 megabit) which gives you 1 megabyte (or by today's terms, mebibyte) of RAM. Today, some ISPs still use this terminology. It is handy in communications systems where data is handled on a bit-by-bit basis.

---

### Post by FranMichaels on 2008-09-25
> **jdong said:**
> Incorrect.

Well googling doesn't yield much here.
What was MB supposed to stand for on these disks?

I know the old single 5 1/2 at best held 720 kilobytes, and these 3.5 guys could supposedly hold 1440 kb. Which would be 1.44 megabytes. These are the marketed values at least. I have loads of these floppies, but no more drives to test them with. I'm just sure I could fit over 1mb on these things, as splitting data was common when I used them...

EDIT: NM You've answered. However, if the marketing guys messed up, the MB on the disk did stand for megabyte. It was just plain wrong, but in that case the acronym was indeed a)

---

### Post by jdong on 2008-09-25
They used the base-2 definition of kilobyte combined with the base-10 definition of megabyte, yielding some weird hybrid of the two.

---

### Post by FranMichaels on 2008-09-25
Yes, very problematic, but the use of kibi and mebi came well after these floppies did. More than a decade in fact. It's been confusing, and continues to be, why is my X GB drive actually Y GB or GiB or whatever. This would still have problems even without acronyms, as some use GB and GiB interchangeably... I'm sure someone out there with a terrabyte drive is pissed they have 990 gigs or something... :popcorn:

---

### Post by zekopeko on 2008-09-25
try formating a disk with ext3 then you are gonna see wasted space.
i formated my 320gb disk

NTFS 298gb
ext3 292gb (after i removed the root reserved 5%)

that's why i use ntfs for all of my storage

---

### Post by jdong on 2008-09-25
> **FranMichaels said:**
> Yes, very problematic, but the use of kibi and mebi came well after these floppies did. More than a decade in fact. It's been confusing, and continues to be, why is my X GB drive actually Y GB or GiB or whatever. This would still have problems even without acronyms, as some use GB and GiB interchangeably... I'm sure someone out there with a terrabyte drive is pissed they have 990 gigs or something... :popcorn:

Haha 990, if I remember correctly they BARELY break the 900GiB barrier!

---

### Post by jdong on 2008-09-25
> **zekopeko said:**
> try formating a disk with ext3 then you are gonna see wasted space.
i formated my 320gb disk

NTFS 298gb
ext3 292gb (after i removed the root reserved 5%)

that's why i use ntfs for all of my storage

Bad news: NTFS counts the MFT reserved zone as free space. You can have a NTFS volume with a few gigs of free space but copying to it results in disk full :)

---

### Post by kernelhaxor on 2008-09-26
In the commercial world 500GB = 500 * (1000 * 1000 * 1000) = 500,000,000,000 bytes

But operating systems use 1024 instead of 1000 .. so 
500,000,000,000 bytes = 500,000,000,000 bytes / (1024 * 1024 * 1024)  = 465.661 GB which is exactly what any OS shows ..


I dont consider it a rip off because I am aware of this difference.  May be manufacturers should make customers aware of this difference.

---

### Post by 4th guy on 2008-09-26
All right, fair enough. However the box *does* define 1GB as 1000MB.

So: 500GB * 1000MB / 1024MB = 488.28125GB, which is still a leap from 465GB I'm sure the MTF does not take up those missing ~20GB

---

### Post by kernelhaxor on 2008-09-26
> **4th guy said:**
> All right, fair enough. However the box *does* define 1GB as 1000MB.

So: 500GB * 1000MB / 1024MB = 488.28125GB, which is still a leap from 465GB I'm sure the MTF does not take up those missing ~20GB

Commercial manufacturers also define 1MB = 1000KB and 1KB = 1000 bytes ..
while for an OS, 1MB = 1024KB and 1KB = 1024 bytes ..

so, while doin the conversion, convert all the way into bytes and then convert back .. u will land at 465 ..

This is true for all hard disks of all sizes .. I have manually calculated several times ..

---

### Post by 4th guy on 2008-09-26
I'm still going to give them a piece of my mind. I paid money for a *500GB* drive.
I'm sure that when you buy 5 pints of beer, you get 5 pints and not 4. Likewise when you buy 10 liters of petrol, you get 10 liters and not 9.

Is there a filing system that I can use to maximise the available space?

---

### Post by tylerspaska on 2008-09-26
> **jdong said:**
> Haha 990, if I remember correctly they BARELY break the 900GiB barrier!

I thought there was a class action lawsuit involving all of this, which lead to manufacturers actually being honest about the size of their drives...

Anyway, the last TB drive i bought actually had 1000.1 GB. I was pleased. It was a 'Green' WD drive.

[http://www.neowin.net/index.php?act=view&id=33874](http://www.neowin.net/index.php?act=view&id=33874)

edit: I just double checked to make sure and it actually turned out to be 1000.2 GB

---

### Post by 4th guy on 2008-09-26
New find: the box states that you can hold 110 movies (of 4.5GB each). Now they're just being cheeky.:mad:

---

### Post by tylerspaska on 2008-09-26
delete

---

### Post by NovaAesa on 2008-09-26
500 GB = 500,000,000,000 bytes.

divide by 2^30 to convert to GiB. You end up with 465.66 GiB.

The problem is not with manufacturers, it is with the operating systems. Most OSs insist on reporting the number of GiB but actually labelling it as GB. This is where the confusion lies. You are not being ripped off, you just don't understand the meaning of binary and decimal prefixes.

---

### Post by 4th guy on 2008-09-26
Actually I do understand the difference between 101 base 2 and 5 base 10 (just a different numbering system).

If the box says 500GB, why was I given 500GiB?

---

### Post by Kvark on 2008-09-26
> **NovaAesa said:**
> 500 GB = 500,000,000,000 bytes.

divide by 2^30 to convert to GiB. You end up with 465.66 GiB.

The problem is not with manufacturers, it is with the operating systems. Most OSs insist on reporting the number of GiB but actually labelling it as GB. This is where the confusion lies. You are not being ripped off, you just don't understand the meaning of binary and decimal prefixes.
GiB??? :frown:

GB has always been 1024 MB which is 1024 kB which is 1024 B, easy. A new acronym for the same thing is a pretty useless change as it doesn't actually improve anything.

It is deception to use multiples of 1000 instead of 1024 to make drives look bigger than they really are. Just as using Mb/s instead of MB/s to make internet connections look faster than they really are. I've had to explain the difference between bits and bytes to several of my non-geek friends when they complained that their 2Mb/s connections never downloaded anywhere near 2MB/s.

---

### Post by NovaAesa on 2008-09-26
> **4th guy said:**
> Actually I do understand the difference between 101 base 2 and 5 base 10 (just a different numbering system).

If the box says 500GB, why was I given 500GiB?If the box says 500GB, you received 500GB. 500GB = 465.66GiB. The problem is, when your OS is reporting the size of the hard drive, it is reporting the GiB value but instead of labelling it with "GiB" is is labelling it with "GB". 

[quote=Kvark]
GB has always been 1024 MB which is 1024 kB which is 1024 B, easy. A new acronym for the same thing is a pretty useless change as it doesn't actually improve anything.[/quote]It was like that until 1998 when IEC introduced the new binary prefixes.

[quote=Kvark]
It is deception to use multiples of 1000 instead of 1024 to make drives look bigger than they really are. Just as using Mb/s instead of MB/s to make internet connections look faster than they really are. I've had to explain the difference between bits and bytes to several of my non-geek friends when they complained that their 2Mb/s connections never downloaded anywhere near 2MB/s.[/quote] Not decepiton. Drive manufacturers actually use the correct prefix! It's the fact that (some) OSs report the value incorrectly. And when it comes to the internet, it has always been like that. It's not a marketing scam or anything like that. Whenever data is transferred in a bit stream, it is almost always measured in the number of bits (or kilobits, or megabits if you are lucky) per second. "Bytes" don't make sense semantically when you are transferring data like that so there is no use in measuring it in the number of bytes per second.

---

### Post by 4th guy on 2008-09-26
> If the box says 500GB, you received 500GB. 500GB = 465.66GiB. The problem is, when your OS is reporting the size of the hard drive, it is reporting the GiB value but instead of labelling it with "GiB" is is labelling it with "GB".So I actually have 500GB? :confused: Can you explain more (or at least direct me to a good explanation)?

---

### Post by Kvark on 2008-09-26
> **NovaAesa said:**
> 
It was like that until 1998 when IEC introduced the new binary prefixes.

 Not decepiton. Drive manufacturers actually use the correct prefix! It's the fact that (some) OSs report the value incorrectly. And when it comes to the internet, it has always been like that. It's not a marketing scam or anything like that. Whenever data is transferred in a bit stream, it is almost always measured in the number of bits (or kilobits, or megabits if you are lucky) per second. "Bytes" don't make sense semantically when you are transferring data like that so there is no use in measuring it in the number of bytes per second.
I'd never be able to explain that to ordinary people so they remember it and do things 'correctly' and even if they got everything right they wouldn't get anything useful out of that knowledge. It's much easier to stick with the same good old 1024 byte kB everyone is used to.

By ordinary people I mean my mom who still needs help to send an SMS after I've explained it 10+ times and my neighbor who refuses to believe me when I say it's possible to change the operating system to something else than what came preinstalled. He seems to think PC with XP and PC with Vista are like PS2 and PS3, impossible to turn one into the other.

---

### Post by linuxguymarshall on 2008-09-26
The filesystem is taking up some space but no way that much space. 

Yes you got ripped.

Let's start class-action

---

### Post by jdong on 2008-09-26
> **linuxguymarshall said:**
> The filesystem is taking up some space but no way that much space. 

Yes you got ripped.

Let's start class-action

WAY too late. Seagate already lost one of these and now every box says 1GB is 1 billion bytes. There's no case anymore.

---

### Post by aaaantoine on 2008-09-26
> **4th guy said:**
> So I actually have 500GB? :confused: Can you explain more (or at least direct me to a good explanation)?

In those exact terms, yes.  You have 500GB.  Your hard drive should be able to hold 500,000,000,000 bytes of data.  If it were anything substantially less than that, you would have grounds for an RMA.

Your OS reports less because it's reporting it in binary.  It's still 500 billion bytes.

Gnome appropriately labels its data numbers as GiB, MiB, etc. (sometimes.  I see Nautilus 2.22 doesn't, which is weird because I could have sworn it used to.)  So if you're using Gnome, it should already be telling you 465.6 GiB.  I know Windows doesn't make this distinction.  I don't know if KDE does or doesn't.

---

### Post by Kabezon on 2008-09-26
It is a ripoff. They say 1GB = 1000MB when it's actually 1024MB. If you do the math, it is actually 488GB, but it is normal for the formatted drive to be a bit smaller. Don't worry, they do it to everyone :S

---

### Post by 4th guy on 2008-09-26
> **aaaantoine said:**
> Gnome appropriately labels its data numbers as GiB, MiB, etc. (sometimes.  I see Nautilus 2.22 doesn't, which is weird because I could have sworn it used to.)  So if you're using Gnome, it should already be telling you 465.6 GiB.  I know Windows doesn't make this distinction.  I don't know if KDE does or doesn't.It says GB, which is weird, because memory on the System Monitor is reported in GiB.
I've still contacted them via email. I don't care how they define storage space, they didn't point out the fine grey print on the white box. Aren't those things supposed to be written in minute contrasting colour?

---

### Post by jdong on 2008-09-26
> **4th guy said:**
> It says GB, which is weird, because memory on the System Monitor is reported in GiB.
I've still contacted them via email. I don't care how they define storage space, they didn't point out the fine grey print on the white box. Aren't those things supposed to be written in minute contrasting colour?

The box does not say "1GB is 1 billion bytes" somewhere on it? It's standard terminology these days after Seagate lost.

---

### Post by 4th guy on 2008-09-26
The box says 1GB is 1000MB. Nothing more, nothing less.

---

### Post by zekopeko on 2008-09-26
> **jdong said:**
> Bad news: NTFS counts the MFT reserved zone as free space. You can have a NTFS volume with a few gigs of free space but copying to it results in disk full :)

Good news: You are wrong. I had that happen a few time (fill the disk completely) and it wasn't a problem. If it says 10GB free it has 10GB free. Running chkdsk gives around 100MB reserved for indexes and filesystem stuff. Considering that i have around 1.5TB of storage if i was to use ext3 it would it like 30-35GB and thats a lot of space.

---

### Post by jdong on 2008-09-26
> **zekopeko said:**
> Good news: You are wrong. I had that happen a few time (fill the disk completely) and it wasn't a problem. If it says 10GB free it has 10GB free. Running chkdsk gives around 100MB reserved for indexes and filesystem stuff. Considering that i have around 1.5TB of storage if i was to use ext3 it would it like 30-35GB and thats a lot of space.

What evidence do you have that ext3 claims 30GB in filesystem data structures? At any rate, at 1.5TB using ext3 is probably a bad idea in general, it's better suited to a dynamic inode allocation B*-tree filesystem.

---

### Post by 4th guy on 2008-09-28
Anyway, I fired an e-mail to them on Friday
> Yesterday I came to the store and bought two external 500GB hard disks ([http://tinyurl.com/3gn6ur](http://tinyurl.com/3gn6ur)). The problem is that when I plug them into the back USB2 hub (after setting everything as illustrated in the manual), I only get a maximum of 465GB, a difference of 35GB on both of them (which is 70GB). I paid the money for all of the storage space advertised on both the website and on the box, yet none of them state that it was actually 465GB that I would be getting, and not the promised 500GB.
What are you going to do about it?

Sincerely,
I have tried to balance it out between being polite and firm, and I recieved this reply
> Good Afternoon,

 

Thank you for your e-mail.

 

Regarding your enquiry, the harddisks are of a capacity of 500GB and in order to confirm this you need to check using this procedure:

 

    * Click on My Computer
    * Right Click on the Icon of the harddisk, and click Properties
    * In the Window that opens there is a picture of a PieChart, right above it there is a value in GB and there is a value in Bytes.

 

The true value of the capacity of the harddisk is shown in the value with Bytes.

 

 

If you need any more help, please do not hesitate to contact us,

 

 

Regards,Not only do they assume I am using Windows (for a hard disk that is both Windows and Mac compatable [and obviously Linux as well]), but they give me copy/paste instructions that don't answer my query. At this point I was pissed off, and I fired the following reply.> The number of bytes is 500000000000
The number of actual bytes in 500GB is 536870912000 (500*1024*1024*1024). The box states 500GB not 500GiB or 500000000000bytes. There is a discrepancy of 36870912000 bytes.

Sincerely,So far they have yet to reply. Any pointers on how I should continue this?
I thought I'd tell them that since they have not given a satisfactory answer or solution, I will demand a particular solution. Either refund the money for the missing space, or exchange the drives with two *real* 500GB drives.

PS: I only got one drive, but my friend bought the exact same model with me, so I decided to connect the two issues.

---

### Post by jdong on 2008-09-28
> 
The number of bytes is 500000000000
The number of actual bytes in 500GB is 536870912000 (500*1024*1024*1024). The box states 500GB not 500GiB or 500000000000bytes. There is a discrepancy of 36870912000 bytes.


You are confusing yourself there. 500GiB is 500*1024^3 bytes; 500GB is a legitimate term for 500*10^9 bytes

---

### Post by Frak on 2008-09-28
They use decimal system, not the actual byte system. It rounds from 1024 to 1000.

---

### Post by 4th guy on 2008-09-28
> **jdong said:**
> You are confusing yourself there. 500GiB is 500*1024^3 bytes; 500GB is a legitimate term for 500*10^9 bytesOops, damn. Still, they have to justify the use of grey fine print, on a white background and covered in plastic. It's not what I'd call readable, especially with all the bright lights in the store. Regardless, didn't we learn at school that 1mb is 1024kb? Where did the sudden change in the convention happen?> **Frak said:**
> They use decimal system, not the actual byte system. It rounds from 1024 to 1000.I did not realize that it would justify misinformation.

---

### Post by Frak on 2008-09-28
> **4th guy said:**
> Oops, damn. Still, they have to justify the use of grey fine print, on a white background and covered in plastic. It's not what I'd call readable, especially with all the bright lights in the store. Regardless, didn't we learn at school that 1mb is 1024kb? Where did the sudden change in the convention happen?I did not realize that it would justify misinformation.
It's almost like how ISP's show bits instead of bytes.

*"We offer 1.5Mb/s download!"*

The regular consumer thinks 1.5MB/s while in actuality, it rounds off to around 150KB/s

---

### Post by xnef1025 on 2008-09-28
I had a similar thing happen in reverse when I bought a Compaq desktop last year.  The specs said it had a 200GB HDD, but when I actually got it home, I found it had a 250GB HDD in there instead.  Compaq was kind enough to not count the recovery partition and the system files area when reporting the system specs.  It was nice to recover that extra space when I wiped Vista and the recovery partition off the system to install a Linux distro.

---

### Post by jdong on 2008-09-28
> **Frak said:**
> It's almost like how ISP's show bits instead of bytes.

*"We offer 1.5Mb/s download!"*

The regular consumer thinks 1.5MB/s while in actuality, it rounds off to around 150KB/s

Well communications systems are more easily tracked in bits than bytes, as most of the times data is not really quantized into bytes as much as it is quantized to bits, making it only natural to measure bits-per-timeslice or timeslices-per-bit.

---

### Post by Frak on 2008-09-28
> **jdong said:**
> Well communications systems are more easily tracked in bits than bytes, as most of the times data is not really quantized into bytes as much as it is quantized to bits, making it only natural to measure bits-per-timeslice or timeslices-per-bit.
Think about it from a customer point of view.

*"Wow, 1.5Mb/s must be really fast. Mine is only 350KB/s..."*

Think of it from a business standpoint.

*"We could increase the number of subscribers if they see a larger number and expect just that."*

I also recall AT&T and Comcast being caught doing this in their commercials. You can increase profits from people that don't know the lingo.

---

### Post by jdong on 2008-09-28
I disagree. Megabits per second are the correct unit for measuring transmission throughput. If they just wanted bigger units, they could've gone with signaling rate (like 802.11G's "54MBit' = 21MBit does) or an even more inflated unit.

---

### Post by Frak on 2008-09-28
> **jdong said:**
> I disagree. Megabits per second are the correct unit for measuring transmission throughput. If they just wanted bigger units, they could've gone with signaling rate (like 802.11G's "54MBit' = 21MBit does) or an even more inflated unit.
In a technical paper, yes. In a release to the public, maybe. In a television commercial, I doubt it. Remember, companies will do whatever it takes (hopefully within the law) to make a point, even if it is exagerated.

---

### Post by jdong on 2008-09-28
Again, why don't they just use signaling rate of the channel or analog bandwidth to make their claims then, if you are so sure the purpose is to inflate the numbers?

---

### Post by 4th guy on 2008-09-29
Yes, but in computing we're used to seeing GB not Gb or anything else.

---

### Post by jdong on 2008-09-29
> **4th guy said:**
> Yes, but in computing we're used to seeing GB not Gb or anything else.

Not really; it's only with binary data structures (i.e. operating systems organizing data) that the base-2 definition is used. Officially GB refers to the base-10 SI unit, or at least the IEC says so.

Either way, cases like this have been waged in court again and again, and the outcome is always the same... you don't really have much grounds to complain about here.


EDIT: I should also note that flash media today are sold by base-2 storage units. Again, the medium's construction lends to base-2 organization.

---

### Post by NovaAesa on 2008-09-29
Look, you had lots of people in this thread explain to you the meaning of giga (G, 10^9) and gibi (Gi, 2^30). Didn't you listen to them or something? There's lots of literature out there backing up their claims. Then you go off getting cranky at the HDD company when it is pretty obvious you are in the wrong and they are in the right. You had the option to read into and do some research on what people were saying and stop yourself from being an ignorent consumer. Instead, you just ignore it and decide to stay as the ignorent consumer...

Get real here, seriously. :S

---

### Post by mips on 2008-09-29
> **jdong said:**
> I disagree. Megabits per second are the correct unit for measuring transmission throughput. If they just wanted bigger units, they could've gone with signaling rate (like 802.11G's "54MBit' = 21MBit does) or an even more inflated unit.

I have to agree with you. Digital communications have always been measured in bits/second.  It is the best way to measure the 'speed'.

B/s just make no sense in a communications environment.

---

### Post by bartos on 2008-09-29
When I ordered my laptop, i seen they had a recovery partition but the numbers didn't add up to 80 gig.So I phoned their tech support and they couldn't figure out why I had a 75 gig drive so they sent me another 80. Now I have one with all the original formatting that i can put back in for whoever buys it off me and one for linux.
Good tech support they had.

---

### Post by 4th guy on 2008-09-29
> **NovaAesa said:**
> Look, you had lots of people in this thread explain to you the meaning of giga (G, 10^9) and gibi (Gi, 2^30). Didn't you listen to them or something? There's lots of literature out there backing up their claims. Then you go off getting cranky at the HDD company when it is pretty obvious you are in the wrong and they are in the right. You had the option to read into and do some research on what people were saying and stop yourself from being an ignorent consumer. Instead, you just ignore it and decide to stay as the ignorent consumer...

Get real here, seriously. :S
Why, thank you for your support. No matter how wrong I am about GB, GiB and Gb, the fact that the hard disk was obviously misleadingly advertised on the website and barely legible fine print (I'd like to see anyone reading grey text on a white background with spotlights shining over the shrink wrap).
I am not being an ignorant customer, I'm being a very angry customer who happens to be an unemployed student that had to either buy an external hard disk with his limited funds or fail his course.

---

### Post by jdong on 2008-09-29
I don't really think you were somehow victimized here. The binary GB is just as legitimate as the base 10 GB with standards bodies advocating both. Every hard disk maker uses this convention and every disk buyer is getting the same size discrepancy so I don't see why you think you are victimized in particular. 

We have been trying to tell you this but you always read it as someone wronged you as shown by your incorrectly worded email to the manufacturer.

---

### Post by Canis familiaris on 2008-09-29
Actually the companies do "inflate" the figures. Seriously they should use GiB for measuring storage rather than GB. Most People think GB = GiB and they think they have 80GiB in their 80GB hard disks. I'm sure if say in a theoritical case if 1 GiB would have been lesser than 1000 in value, they would have used GiB. After all the companies do like to inflate their figures.

---

### Post by 4th guy on 2008-09-29
> **jdong said:**
> I don't really think you were somehow victimized here. The binary GB is just as legitimate as the base 10 GB with standards bodies advocating both. Every hard disk maker uses this convention and every disk buyer is getting the same size discrepancy so I don't see why you think you are victimized in particular.If it's really that standard, Operating Systems and CD manufacturers would use said standard, no? Obviously, everyone else is getting the same, but that won't stop me from trying to at least make my voice heard of as an unsatisfied customer. I certainly *won't* buy anything from that computer store again (based on numerous other dissatisfactions, this is just the cherry) unless they give me a valid reason why I should today.

---

### Post by jdong on 2008-09-29
> **4th guy said:**
> If it's really that standard, Operating Systems and CD manufacturers would use said standard, no? Obviously, everyone else is getting the same, but that won't stop me from trying to at least make my voice heard of as an unsatisfied customer. I certainly *won't* buy anything from that computer store again (based on numerous other dissatisfactions, this is just the cherry) unless they give me a valid reason why I should today.

Operating system blocksizes are a completely different concept also. Why should disk/RAM manufacturers care? For example, my BSD server measures available RAM and disk space in 4K blocks. I have ~2000000000 blocks of RAM ( = 1GB).

Please find me **one** non-SSD disk manufacturer that sells hard disks in base-2 measurement units.

---

### Post by 4th guy on 2008-09-29
> **jdong said:**
> Please find me **one** non-SSD disk manufacturer that sells hard disks in base-2 measurement units.Sorry, I don't have more money to spend. Blasted hard disk took most of it.

---

### Post by jdong on 2008-09-29
I'll save you some time: Nobody.

---

### Post by Canis familiaris on 2008-09-29
The fact that every one follows an incorrect unit of measurement is NOT its justification.
On ther other hand Consumers should educate themshelves:
1 GiB != 1 GB.

---

### Post by 4th guy on 2008-09-29
Thanks for saving me the time. ;)
> We have been trying to tell you this but you always read it as someone wronged you as shown by your incorrectly worded email to the manufacturer.
By the way, I wasn't communicating with the manufacturer. I was communicating with a computer store, who has a reputation for ripping people off on software. I was under the impression that they did that on hardware as well. Obviously I am still going to investigate the matter further, and the fact that I'm not very good when it comes to hardware is hindering in this case.

---

### Post by jdong on 2008-09-29
I think the bottom line here is buyers should stay educated on what they are purchasing. This is no different than 802.11G's "false" 54MBit advertisement (the max theoretical data throughput given perfect transmission is about 22MBit) or the "133MB/s" ultra ATA bus (in reality there are 4 channels that transmit at a rate 1/4 of the advertised limit).

The fact of the matter is that two-letter units can only explain so much -- it's up to the consumer to figure out exactly what it means. In the field I've had to deal with far more frustrating unit discrepancies than this when dealing with spec sheets for parts, which are filled with interesting units, rates, and temperatures that turn out to mean something very different than what appears at the surface once you look deeper into it.

---

### Post by jdong on 2008-09-29
```

[jdong@jdong:~]$ df -BMB                                          (09-29 13:41)
/dev/sdb1             249923MB  151660MB   98264MB  61% /srv

```

Gasp, a 250GB hard drive :). (64MB of that is the XFS journal, purposely made large for metadata performance. The other 13MB is a combination of filesystem structures, partitioning off-by-one-cyl error, and bad blocks reserved area.

---

### Post by Canis familiaris on 2008-09-29
> **jdong said:**
> i think the bottom line here is buyers should stay educated on what they are purchasing. This is no different than 802.11g's "false" 54mbit advertisement (the max theoretical data throughput given perfect transmission is about 22mbit) or the "133mb/s" ultra ata bus (in reality there are 4 channels that transmit at a rate 1/4 of the advertised limit).

The fact of the matter is that two-letter units can only explain so much -- it's up to the consumer to figure out exactly what it means. In the field i've had to deal with far more frustrating unit discrepancies than this when dealing with spec sheets for parts, which are filled with interesting units, rates, and temperatures that turn out to mean something very different than what appears at the surface once you look deeper into it.

+1

---

### Post by 4th guy on 2008-09-29
> **jdong said:**
> ```

[jdong@jdong:~]$ df -BMB                                          (09-29 13:41)
/dev/sdb1             249923MB  151660MB   98264MB  61% /srv

```

Gasp, a 250GB hard drive :). (64MB of that is the XFS journal, purposely made large for metadata performance. The other 13MB is a combination of filesystem structures, partitioning off-by-one-cyl error, and bad blocks reserved area.

I've yet to see journals and filesystem structures that take up 35GiB, unless I'm a total idiot and I'm not getting what you said. (if that's the case I'd appreciate a reply explaining more on this; I'm extremely interested)

---

### Post by jdong on 2008-09-29
Use the **df -BMB** or **df -BGB** commands to show the size of the drive in MB and GB, respectively. This value should be extremely close to the advertised capacity of the drive, as you are specifically requesting the size in units of MB and GB rather than the OS's default organization level (which is base-2 due to the convenience of the data structures within the OS)

---

### Post by dannyboy79 on 2008-09-29
as many others have already stated. Marketing uses tricky labels and what not. For example, you can by a formatted FAT32 external drive that states it's 300GB (doesn't state that the formatting took hard drive space away though) when you plug it in and do a df -h in linux, it'll say it only is 280GB.
I bought a unformatted Seagate 500gb hard drive and formatted it ext3 and it only shows 469GB, so I lost 31GB. Just the way it is.

Here's also a great explanation on the matter, look under the Consumer Confusion section: [http://en.wikipedia.org/wiki/Gigabyte#Gigabytes_vs._gigabits](http://en.wikipedia.org/wiki/Gigabyte#Gigabytes_vs._gigabits)

---

### Post by ubuntpetbe on 2011-09-02
> **4th guy said:**
> I have bought an external hard disk which supposedly has a 500gb capacity. The problem is that it only has 465gb. I know that some manufacturers prefer to show straight shiny numbers, like 500gb as opposed to 465gb, but right now I can not help but feel as if I have somehow have been ripped off. There was no number on the box other than 500gb.
Any ideas or advice?

(for those who were wondering, it's "only" 7% less, but I paid money for those missing 35gb as well)

EDIT: even if we take 1gb as 1000mb (as "defined" on the box), I still would have 488gb as opposed to 465gb.

Have read this thread and decided someone should explain it easy and clear.

What's on the box is wrong, it's not taking 1 GB as 1000 MB but taking 1 GB as 1*(1000^3) B.
And the operating system using 1 GB as 1*(1024^3) B.

The calculation itself is: 500*( (1000^3)/(1024^3) )
500 GB = 465.66 GiB
This checks out. 

Let's see what numbers this calculator gives us:
[http://www.dr-lex.be/info-stuff/bytecalc.html]("http://www.dr-lex.be/info-stuff/bytecalc.html")
Again 500 GB = 465.66 GiB.

Why don't you show the unprefixed amount of bytes that your operating system sees on the disk? 

(I notice that you don't understand the prefixes because of the wrong advice on the box.  This means that people who decide what came on that box doesn't have a good understanding of math and prefixes.





This is a misunderstanding because of confusion. It sucks but these things happen.
If you really need to point a finger.
You're being bullshitted by the Operating System.
Notice the companie about their wrongly explanation. Ask them to just put the actual number on it. Like this: 1 GB = 10^9 B.

Some idiot, a while back, didn't wanted to do memory calculations. Because he was careless and lazy he just not changed the units or added any indication of it's non-standard use. (The meaning of a few decimal prefixes where standardized long before the first computer.) 

This resulted in an Operating System using binary prefix calculations in combination with showing decimal prefixes. 
Other OS makers copied that behaviour resulting in the mess and confusing nowadays. 
We're slowly going away from that because of the confusion. The new IEC prefixes are new and suppose to help show the difference.
Mac OS X 10.6 already uses the new meanings and corrects the old meanings. Others will follow.

And people, get your math right!
Seriously!

---

### Post by overdrank on 2011-09-02
Thread is 3 yrs old. Back to sleep. Thread closed. :)

---

