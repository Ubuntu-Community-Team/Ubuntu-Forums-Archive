---
title: "BIOS - compromised by viruses"
date: 2010-12-27
forum: Security
---

### Post by mistypotato on 2010-12-27
Hi,

I would like to discuss the possibility of viruses infecting BIOS.  It is on a WinLux Dual boot machine so while Windows is totally affected, I'm also concerned about any effect it may have on my Linux install.

I have a computer which will not work properly (except under Linux).  Linux still works perfectly on this machine.

However, It absolutely refuses to allow any Microsoft product to even get started.
At the Boot level, any attempt to boot any Microsoft product results in a stall and black screen and then slow, steady blip of the hard drive light....ad infinitum.

There is only one hard drive attached to the machine and it has been low level formatted with Western Digitals Disk Diagnostics Tools numerous times.  The computer has been disconnected from the network and there are no USB devices attached, no discs or CD/DVD's in the machine etc.

Yet, even with various software sources (ie OEM Reinstall disk sets from various places at various times) the computer becomes re-infected almost immediately AFTER REBOOTING.

I am nearly certain it is not a MBR infection as low level formatting should get that (if not, harddrives wouldl be useless after MBR infection.

It has also been tested with other hard drives.  No matter what hard drive is used, the same end result occurs.

Currently, I'm trying to find a way to re-flash the BIOS WITHOUT Windows (I find it absurd that almost all the BIOS updates depend on your being IN WINDOWS to flash the BIOS !!)   What's needed are ISO files that can be burned to disc and operate from their own boot process.

So, while this is largely affecting Windows, it is also affecting dual boot machines with Linux installed so it seems to be a worthy and relative topic.

A "BIOS Reset" using the jumpers will not do.  That usually only resets "USER" data such as the clock and other user settings.  NOT the core BIOS programming.

Anyone have a suggestion as to how you might re-flash a BIOS if you cannot run the OS needed to run the re-flash utility ?

The Machine is an HP Pavillion a6230n with Phoenix Award BIOS.

thx

---

### Post by msandoy on 2010-12-27
Well, I'm not used to HP products, since I usually buy Asus main boards. In recent years, Asus have shipped their bios'es with an EZflash utility from Bios itself. As long as you have the rom file on floppy or HD, you can do the bios upgrade directly.
Have a look around to see if HP might have included something similar.

---

### Post by CharlesA on 2010-12-27
How do you know that it's "reinfected" right after install?

---

### Post by mistypotato on 2010-12-27
> **CharlesA said:**
> How do you know that it's "reinfected" right after install?

Because the virus is present again...it writes itself from BIOS (I'm thinking) back to Pagefile.sys

There's nowhere else I can think of it could be coming from.

Totally ZERO wiped harddrive...no USB, no Disks or CD's...no network connection.

Can you think of anywhere else it could be coming from?  CPU maybe?

---

### Post by nevius on 2010-12-27
Run memtest to check your RAM. I've had similar problems caused by bad memory. When troubleshooting you should check the mundane possibilities before the exotic.

Occam's Razor for computers:

'viruses must never be postulated without necessity'

---

### Post by mistypotato on 2010-12-27
> **nevius said:**
> Run memtest to check your RAM. I've had similar problems caused by bad memory. When troubleshooting you should check the mundane possibilities before the exotic.

Occam's Razor for computers:

'viruses must never be postulated without necessity'

I think all the "mundane" bases have been adequately covered thank you.

Memory test - Ran that when all this began. (did you read no problems with Linux OS?)
Also - Full harddrive diagnostics (long version)
All non essential devices disconnected
Network disconnected

Only 3 common possibilites remain....

1 & 2). Virus or malfunction in BIOS or CPU (CPU event being very, very rare)
3). Bad MB

Hardware Malfunction seems less likely since Linux runs perfectly on the same machine making it appear to be a Windows Specific event.

Also. Antivirus has in fact already detected one virus present on the harddrive....but antivirus also does not scan BIOS.

Granted the way Ubuntu manages memory and hardware resources is different than the way Windows will, there are still parallels....both utilize the same resources...just differently.   If a resource were malfunctioning, I would probably correctly assume that under most circumstances, there would be a problem in BOTH OS's

Finally, the exact same virus re-appears in the exact same place no matter how meticulously the procedure to ensue it's elimination from all but the BIOS or CPU.

I won't place 100% confidence in it, but there are few other possibilities.

---

### Post by tgalati4 on 2010-12-27
Grab a spare hard drive and put it in the machine.  Try to install a clean copy of Windows (using either a retail CD or an HP restore CD).  See if your machine is stable and allows normal Windows operation.

It's possible that the virus has placed itself somewhere else on the drive, or it's a hard disk problem that is acting like a virus infection.

Even easier, disconnect the current drives and boot using the Windows CD.  See how long the machine runs.

---

### Post by CharlesA on 2010-12-28
+1 to spare hard drive.

Also, what AV are you using and what's the name of the virus it is detecting?

---

### Post by The Cog on 2010-12-28
My feeling is that a BIOS virus is theoretically possible but unlikely. Two more mundane explanations spring to mind:

1: Corrupt BIOS. 
It is possible that part of the BIOS has become corrupt somehow - a part that Windows relies on but that Linux doesn't. I know that Linux tends to use its own drivers rather than rely on the inbuilt BIOS drivers.

2: Missing windows drivers:
Could it be that the standard windows installer is missing a vital driver? I know for instance that some of the servers we use at work can't install standard windows - they say no hard disk found. You have to jump through hoops to supply an additional driver to the installer - not easy when there's no floppy drive and the installer can't see the USB ports either.

---

### Post by bouncingwilf on 2010-12-28
Bios viruses/rootkits do indeed exist or more to the point are deliberately installed in the PC bios by manufacturers under the guise of anti-theft mechanisms; the following paper explains
[http://www.coresecurity.com/content/Persistent-Bios-Infection](http://www.coresecurity.com/content/Persistent-Bios-Infection)

Thankfully at the moment they seem to assume that Windows will be the OS - just another reason to use Linux. 

A few remedies are offered via the paper and associated blurb but another alternative may be to see if your MoBo is supported here [http://www.coreboot.org/Welcome_to_coreboot](http://www.coreboot.org/Welcome_to_coreboot)


Bouncingwilf

---

### Post by bouncingwilf on 2010-12-28
Apologies, linked to wrong research paper. Try this one

[http://www.coresecurity.com/content/Deactivate-the-Rootkit](http://www.coresecurity.com/content/Deactivate-the-Rootkit)

Bouncingwilf

---

### Post by runeh76 on 2010-12-28
Omg :/


Try this bios-boot-CD to flash ur bios:
[http://www.biosflash.com/e/bios-boot-cd.htm]("http://www.biosflash.com/e/bios-boot-cd.htm")

(Havent tried it, just googled it)

Good luck  :)

---

### Post by unknownPoster on 2010-12-28
> **runeh76 said:**
> Omg :/


Try this bios-boot-CD to flash ur bios:
[http://www.biosflash.com/e/bios-boot-cd.htm](http://www.biosflash.com/e/bios-boot-cd.htm)

(Havent tried it, just googled it)

Good luck  :)

That's terrible advice. If the bios update fails it may render the computer unusable, you should never just do random BIOS updates from random websites. That's how inexperienced Windows users get viruses. It's a better idea to go to your manufacturer's website and look for BIOS support there.

---

### Post by pricetech on 2010-12-28
Agreed.   BIOS updates, as well as the program used to update with, should only come from the MoBo manufacturer.

---

### Post by runeh76 on 2010-12-29
well guy said  "Currently, I'm trying to find a way to re-flash the BIOS WITHOUT Windows (I find it absurd that almost all the BIOS updates depend on your being IN WINDOWS to flash the BIOS !!) What's needed are ISO files that can be burned to disc and operate from their own boot process."

so get ur bios from ur manufacturer and follow those instructions...

just trying to help  ;)

---

### Post by mistypotato on 2010-12-29
> **runeh76 said:**
> well guy said  "Currently, I'm trying to find a way to re-flash the BIOS WITHOUT Windows (I find it absurd that almost all the BIOS updates depend on your being IN WINDOWS to flash the BIOS !!) What's needed are ISO files that can be burned to disc and operate from their own boot process."

so get ur bios from ur manufacturer and follow those instructions...

just trying to help  ;)

Being ridiculously obvious is not very helpful.

Don't you think that was the very first thing a person would try ?   ):P

People that jump into threads with their self certified "awesomely brilliant" yet almost insulting replies when it's obvious they have not taken the time to even read the OP is a fact of forum life.

Had you read the OP, the OP stated that she/he was not able to run Windows (of ANY) flavor on the machine.
The manufacturer (ASUS in this case) will not support the product as they now call it an HP product...even though it's an ASUS board.
*(If ASUS did not manufacture the M2N68-LA board for HP then I am grossly mistaken and will update this post accordingly)

Here is the Response FROM ASUS - David Ludwig
> **Asus Support]
[B]Asus does not handle any support for HP said:**
> myemail@yahoo.com[/email]
Sent : 12/28/2010 3:54:11 PM
To : "tsd@asus.com.tw"
Subject : <TSD> Motherboard M2N68-AM [/B]


So David Ludwig with Asus declines to offer help on an ASUS product "because", they now call it an HP product.
(granted there may be legal agreements between HP and ASUS, but from a consumer's perspective this is not helpful).
HP (as far as I know) does not manufacture Motherboards, nor does HP offer a workable solution in this case to my knowledge, so his reply was a bit insulting as well.
If this is Asus's stance on customer support, I don't think I will purchase from them.
I'm sure he had access to information on this Mainboard since his company made it.*

Never the less....the Problem is........

HP ONLY provides a Windows based BIOS flash / update....it is not possible to boot into windows or any variation of it on the machine in question.

---

### Post by mistypotato on 2010-12-29
> **CharlesA said:**
> +1 to spare hard drive.

Also, what AV are you using and what's the name of the virus it is detecting?

Hi Charles,

**Things Tried**
Ram tested with Memtest.
Harddrive thoroughly tested with Manufacturers Disk utils
Low Level Formatted drive (Zeros written to full drive)
Network disconnected
Tried several different Harddrives
All Non Essential devices disconnected (USB, all CD/DVD drives etc)
Computer runs perfectly fine on Linix OS - chokes on any Windows product
Tried booting with WinXP OEM disks, OEM HP Recovery disks, BartPE - same stall and/or boot failure
Checked cooling fans (ok)

 

**Symptoms**
Hangs at Windows boot - will sometimes finally resume boot after half hour delay (no exaggeration)
Boots and runs 100% good on Linux Operating System
During all stalls, hard drive light pulses slowly...blink.....blink....blink....blink (this is on several different hard drives some LL formatted some not)
The feel I get is that the computer is hung waiting for something
Same computer works PERFECTLY if booted to Linux but refuses ANY Microsoft product
After a totally sanitary reinstall (drive wiped with Zeros), OEM CD's, I still get a re-curring virus in pagefile.sys and extreme delays in booting and operation.
This appears to be a Windows Specific event

---

### Post by mistypotato on 2010-12-29
> **tgalati4 said:**
> Grab a spare hard drive and put it in the machine.  Try to install a clean copy of Windows (using either a retail CD or an HP restore CD).  See if your machine is stable and allows normal Windows operation.

It's possible that the virus has placed itself somewhere else on the drive, or it's a hard disk problem that is acting like a virus infection.

Even easier, disconnect the current drives and boot using the Windows CD.  See how long the machine runs.

This has all been methodically ruled out.  :KS

This is DEFINITELY NOT related to a hard drive issue.

---

### Post by mistypotato on 2010-12-29
There is another very interesting topic brought to light from this incident.

Someone I assume representing HP told me that Windows and Ubuntu are so different, that the way they use any given PC's resources would make it so that a computer that is unable to run Windows, still might be able to run Linux.

This is a VERY abstract proposal.

Most (if not all) computers work similarly, they have hardware that utilizes interrupts and data channels to fetch, process, manipulate, transfer and present data as requested. (vastly oversimplified).

Filesystem layouts may differ, but the way information flows across the data channels and the final format of data wanting to access hardware on any system, it would seem, needs to conform to specific standards.

Using "drivers" specific to hardware, all computers and their Operating Systems must follow similar paths and procedures to function properly within the parameters of the hardware therein and external.  For example, If you have an AMD CPU, both Linux and Windows must "speak" to that CPU in a way that the CPU can understand....using the correct "Language" or instruction set for that CPU.  Similarly, the BIOS and chipsets follow the rules and require following a set of standards.  In fact, as far as I know, every single piece of hardware used in a PC or notebook must adhere to those pre-determined guidelines.

So, I'm not so certain that one can say carte blanc that a machine running Linux is so different from the same machine running Windows that Linux would be effectively exempt from issues causing a Windows OS to falter...if it's specifically hardware related.

I'm sure some of the Ubuntu coders would be far more knowledgeable on something like this.  My knowledge is very limited and being corrected by someone with this knowledge would be a privilege

---

### Post by pricetech on 2010-12-29
Following this thread as best I can, it's almost to the point where you're "hunting and pecking" for a cause.  I hate to say that because I prefer a much more logical approach, but ......

A couple of things I'll suggest, but only because I feel like you're at that hunt and peck stage;

Is there any chance the BIOS flash might work from a DOS disk ??  I haven't seen it, so I don't know.  I'm just asking.

You mentioned barts pe, have you tried windows PE ??  They are a little different, so it might be worth a try.

Do you have any spare parts you can "test by substitution" ??  Again, that's not my preferred method, but sometimes it comes to that.

Is your BIOS removable or soldered ??  Any chance you can swap it, assuming you can get your hands on one ??

Just some things that come to mind that I might try if it was on my workbench.

Good luck with it, and let us know.

---

### Post by mistypotato on 2010-12-29
> **pricetech said:**
> Following this thread as best I can, it's almost to the point where you're "hunting and pecking" for a cause.  I hate to say that because I prefer a much more logical approach, but ......

A couple of things I'll suggest, but only because I feel like you're at that hunt and peck stage;

Is there any chance the BIOS flash might work from a DOS disk ??  I haven't seen it, so I don't know.  I'm just asking.

You mentioned barts pe, have you tried windows PE ??  They are a little different, so it might be worth a try.

Do you have any spare parts you can "test by substitution" ??  Again, that's not my preferred method, but sometimes it comes to that.

Is your BIOS removable or soldered ??  Any chance you can swap it, assuming you can get your hands on one ??

Just some things that come to mind that I might try if it was on my workbench.

Good luck with it, and let us know.

Hi,

Thanks for the reply.  I guess you just like to use the words "Hunt & Peck" because having worked in the computer field for about 25years + for many different companies, I have no idea what you mean.  One thing I do know, is that it's a never ending, always evolving learning experience.  If you have anything of value to teach, I will be your student.

Would you be so kind as to clearly detail the "correct" way to go about diagnosing a situation such as this?  If you actually have one.  Perhaps your "method" will help me find something I missed.  I seriously doubt it however to be frank.

With regard to your suggestions.......

No, there is no ROM available for the MoBo from either the manufacturer NOR HP, the distributor that will run from DOS.   The only BIOS updates are from HP and they are ROM's wrapped in a Windows installer.   I could conceivably use a hex editor to remove the wrapper / installer but that would be very dependent on finding the boundaries of the ROM itself within the hex code.  However, it may be possible...if extremely difficult.

This board refuses to load ANY file containing core Windows instructions.  So, WindowsPE would not work any more than BartPE or OEM Windows disks.

I am really interested to hear "your preferred method"........REALLY.

No, the BIOS is not removable.  Checked that....or should I say..."pecked that" ?

I really do appreciate your trying to help, but your first line was a bit colorful if not dramatic.

Again, please PLEASE rescue me from this "hunt and peck" stage and enlighten me with your "preferred" and "logical" approach.
I am such an eager student of those with experience and knowledge.  

:popcorn:

):P

Best Regards

---

### Post by rookcifer on 2010-12-29
> **nevius said:**
> Occam's Razor for computers:

'viruses must never be postulated without necessity'

:lolflag:

I might use that as my sig.

---

### Post by dgw on 2010-12-29
> **mistypotato said:**
> Hi Charles,
Tried booting with WinXP OEM disks, OEM HP Recovery disks, BartPE
Did you create the BartPE disk with your OEM disks? I'm not familiar with BartPE, but from the website it looks like that's what people do with BartPE. I'm wondering if your OEM disks are faulty. Can you try some other Windows install disks?

> I still get a re-curring virus in pagefile.sys and extreme delays in booting and operation.
What is the virus called and how did you determine that there's a virus at all? What anti-virus software are you using?

---

### Post by fbnaia on 2010-12-29
Interesting problem proposed in this thread. A computer not being able to boot into windows properly, does not mean it has a virus at the Bios level. I do have several "junk" computers laying around that don't boot properly in windows (cant use a keyboard/stalls) but on linux all works well. 

The specific model of HP computer you mentioned, the HP Pavilion a6230n, is a Windows Vista only computer. In fact the whole a6200 PC series-Models are Vista only. There are no Windows XP drivers at least officially from HP.

Other things you could try, would be to try specific vista pe tools, winbuilder based on vista etc. Or even provide specific error messages about the problems you get. In previous posts you say that you get errors, it would be great if you post the exact error messages or even better, if you get problems booting bartpe on your specific computer, try the bartpe forums, maybe someone has already experienced your problem with the same computer model.

Also if you said you get a virus on "pagefile.sys" it would really help if you were able to post the details of what virus you get in that file or even better upload the whole file so we all could check the file.

---

### Post by CharlesA on 2010-12-30
> **mistypotato said:**
> 
So David Ludwig with Asus declines to offer help on an ASUS product "because", they now call it an HP product.
(granted there may be legal agreements between HP and ASUS, but from a consumer's perspective this is not helpful).
HP (as far as I know) does not manufacture Motherboards, nor does HP offer a workable solution in this case to my knowledge, so his reply was a bit insulting as well.
If this is Asus's stance on customer support, I don't think I will purchase from them.
I'm sure he had access to information on this Mainboard since his company made it.*

You sure about that? The point is that if the system is an HP system, you need to deal with HP, not Asus - it doesn't matter who manufactured the components, it's still a system assembled by/for HP and has support thru HP.

You still haven't posted any details about this "virus" that you keep saying you are running into.

---

### Post by mistypotato on 2010-12-30
> **dgw said:**
> Did you create the BartPE disk with your OEM disks? I'm not familiar with BartPE, but from the website it looks like that's what people do with BartPE. I'm wondering if your OEM disks are faulty. Can you try some other Windows install disks?


What is the virus called and how did you determine that there's a virus at all? What anti-virus software are you using?

Hi,

The non writeable CD disks were created about a year ago.   They are clean.

Yes, I tried 4 distince sets of Windows based software/

1). OEM Vista recover for the machine in question
2). OEM Windows XP SE 2
3). New set of HP recovery disks
4). Bart PE

One virus was Win32AdLoader but there were others.  They were regenerated randomly from the malicious code inside the BIOS chip, or by a call to a website from which the virus was called by code in the BIOS.  Whatever the event origin, it was / is definitely the BIOS chip.

---

### Post by mistypotato on 2010-12-30
> **CharlesA said:**
> You sure about that? The point is that if the system is an HP system, you need to deal with HP, not Asus - it doesn't matter who manufactured the components, it's still a system assembled by/for HP and has support thru HP.

You still haven't posted any details about this "virus" that you keep saying you are running into.

Nor do I intend to.  That is a waste of time for me.

How many brickwalls can one person handle?

The virus is irrelevant and not the subject of this thread.   Re-flashing the BIOS outside of Windows is the topic.  Because it seems paramount to you,  I saw several...one was Win32:adloader but there were others.  I do not care what viruses they were at this point.
I did not care the names of the viruses as my goal is to re-flash the bios, not clean them up.

HP doesn't have what I need....a non windows based BIOS re-flasher for my MoBo.   Asus made the board but since it's spinoff (corporate games) Pegatron, actually made the board, Asus cries fowl and will not offer support...even though the TRUTH is that Asus made the board....albeit under a corporate game where they create a new company for liability and profit reasons.

---

### Post by mistypotato on 2010-12-30
Most people replying in this thread seem to reject the notion of a BIOS virus.

Please, do some research.   For professional hackers, it is a perfect target and other than the CPU, is probably the next playground for hackers to target.

What's so top secret about hacking a BIOS?   You can flash it right?  So introduce a virus that includes code to flash the bios with hacked code.   IMO, it's happened to HP systems already.  Their support forum is flooded with computers freezing and having BIOS issues.

Why bother putting a virus on your hard drive that can be cleaned off.  Everyone knows how to wipe a drive clean now and start over.

But....putting a virus in BIOS is new territory.  One that even Ubuntu users are having a hard time believing could exist.

I have been researching this issue non stop now for a week.

My research and experiments have thus far concluded it is a BIOS virus.

Could I be wrong?  

But again...."Charles"...I am interested in how to re-flash a BIOS when the only available BIOS flash the manufacturer has put out is Windows based and for whatever reason, windows is not available or accessible.   Let's say the BIOS is just corrupted...no virus.
And said corruption prevents booting into Windows....yet the only bios flash offered by the manufacturer REQUIRES windows to run the flash...

What do you do ?

THAT "Charles" is the important issue here.

Stay on topic folks and the bus will make progress.

):P

---

### Post by bouncingwilf on 2010-12-30
Apologies if you've already considered this as you have obviously researched the problem deeply and fully understand what you're trying to achieve but if DOS/ FreeDOS solutions won't work because of the Windows wrapper in the flashing file What can you lose by trying reactOS?

Bouncingwilf

---

### Post by Elfy on 2010-12-30
I think perhaps that you should remind yourself that people are volunteers - if you're not happy with the help you get - look elsewhere.

You'll at least need to start again on here. This thread is closed.

---

