---
title: "Laptop Tracking Software"
date: 2008-05-25
forum: The Cafe
---

### Post by Black Mage on 2008-05-25
Hey,
Is there any software that tracks your laptop if it is stolen?

---

### Post by Johnsie on 2008-05-25
If I stole a laptop the first thing I would do is boot it up while not connected to anything and look for valuable data. Then I would wipe it. That is if I was ta theif(which I am not). Not sure how any software would prevent this, other than having some kind of mobile chip that communicates via mobile wireless.

---

### Post by uraldinho on 2008-05-25
If the thief was using dhcp, I suppose some sort of script could be added to the boot up that communicates with a certain address. That way thief's current IP address could be tracked. 

If the right channels are followed, knowing the IP address might lead to the thief. The ISPs keep track of phone number to IP address mappings, but you need a court order to release such information. However, as Johnsie in the previous message said, if I were the thief, I probably wouldn't boot into an unknown system. I'd rather take the hard disk out and see what's in it first. 

Another solution would be to install a GPS chip into the computer that works independent of the rest of the computer.  I don't know of any commercial laptops with built in GPS chips, but I don't see why this shouldn't be possible. On the other hand, GPS doesn't work very well indoors.

---

### Post by Black Mage on 2008-05-25
> **uraldinho said:**
> If the thief was using dhcp, I suppose some sort of script could be added to the boot up that communicates with a certain address. That way thief's current IP address could be tracked. 

If the right channels are followed, knowing the IP address might lead to the thief. The ISPs keep track of phone number to IP address mappings, but you need a court order to release such information. However, as Johnsie in the previous message said, if I were the thief, I probably wouldn't boot into an unknown system. I'd rather take the hard disk out and see what's in it first. 

Another solution would be to install a GPS chip into the computer that works independent of the rest of the computer.  I don't know of any commercial laptops with built in GPS chips, but I don't see why this shouldn't be possible. On the other hand, GPS doesn't work very well indoors.

How about adding something to the BIOS that gets an IP address before the computer is even booted?

---

### Post by diablo75 on 2008-05-25
Well, let's pretend something like WiMAX was more common than it is right now, or some similar wireless Internet technology.  I suppose you could set your OS up so as to force it to connect to the net while loading up to the point of the login screen.  A thief might hit this screen and attempt a to login, likely failing in his attempts.  If he's clever, he'll find a way to reset the password through recovery mode, but in the end, he might just whip out a bootable CD and format the hard drive before installing a new OS, likely wiping out the software responsible for phoning home and keeping you aware of the laptops location.

I could go on and on... but to tell you the truth, if you lose a laptop in public and the first thing you worry about is the potentially confidential data on the hard drive being stolen, you've learned a lesson the hard way.  And that is to say that you should NEVER keep information on the laptop that you consider to be invaluable.  The laptop itself is just a piece of hardware.  If you lose it in public, it's akin to someone stealing your car.  Whatever happens in the end, you'll get a new one eventually and life goes on.  But what if the car was stolen with your pet dog in the backseat and you never saw him/her again?  You'd probably go, "Why did I leave the dog in the back seat in the first place?"

---

### Post by keetowah on 2008-05-25
My dell xps came with LoJack by computrace.  It's a homing program that you load and runs in the background.  I never bothered to install it, as the first thing I'd do if I stole a laptop is pull the drive, copy it then wipe it.

---

### Post by Black Mage on 2008-05-25
So on the computer, what is not easily removable or erasable? I'm thinking of the bios because I would think most thiefs would not erase the bios. But can information be written to the bios,  like a program that loads up from bios at the start of the computer, no matter what?

---

### Post by Steve413z on 2008-05-25
> **keetowah said:**
> My dell xps came with LoJack by computrace.  It's a homing program that you load and runs in the background.  I never bothered to install it, as the first thing I'd do if I stole a laptop is pull the drive, copy it then wipe it.


IBM/Lenovo thinkpads have LoJack for laptops built into the bios if you want it.

You can write a boot script that will send a signal to a server every time the computer connects to the internet, but usually recovering the laptop would involve paying a private investigator, because people who have written their own scripts like that have found that the police usually don't care, and to investigate it yourself would involve court subpoenas and a lot of legal work. 

Your best bet is to encrypt the entire drive, and get some insurance for it.  (some homeowners policies will even cover your laptop even if it's stolen from someplace other than your home, but it might cost an extra fee)  

and never let your laptop out of your sight!! if you are at a coffee shop, pick up your laptop and bring it with you when you order your coffee, don't just leave it sitting on the table.  I don't know how many times i've seen a laptop left behind, with the owner out of sight and nowhere to be found.

---

### Post by jpeach on 2008-07-14
Has anyone tried Adeona?  I have not installed it but from what I read on the site it looks like an ideal solution.

[http://adeona.cs.washington.edu/](http://adeona.cs.washington.edu/)

---

### Post by KingTermite on 2008-07-14
There is also LocateMyPc (windows only)
[http://www.iconico.com/locatePC/](http://www.iconico.com/locatePC/)

But from a quick glance, I think I like the look of Adeona that jpeach posted better.

---

### Post by nhasian on 2008-07-14
i tried to install Adeona but dont have much experience compiling sourcecode.  i tried following the instructions but when i got to "sudo make install" i received the error "make: *** [install] Error 1"

too bad there wasnt an easy to install package for ubuntu.

---

### Post by OldGamer on 2008-07-15
I figured that the best thing for me was to install a fully encrypted ubuntu, with the boot on a usb.  If someone steals my laptop, I'm out a few bucks, but at least I don't have to worry about any of my personal info.  That's a little more important to me than the laptop itself, which I think would probably be almost impossible to get back.

---

### Post by amlucent23 on 2008-07-15
I took the liberty of creating a launchpad enty to get Adeona in the repos. 

[https://bugs.launchpad.net/ubuntu/+bug/248782]("https://bugs.launchpad.net/ubuntu/+bug/248782")

---

### Post by barbedsaber on 2008-07-15
all you that say a theif would take out the hardrive first, overestimate the intelligence and computer knowledge of thieves (IMHO)

---

### Post by MJN on 2008-07-30
Has anyone had any joy with Adeona? I've compiled it without error however when running the client it will usually run for a few minutes before failing with a Segmentation Fault. I've reported this to the authors but I am unsure whether I will hear back from them.

Mathew

---

### Post by Biochem on 2008-07-30
:-k
If all you want is the ip address ( and I think all those software will only be able to get that information) a dyndns acount with a working ddclient will do the trick. free, reliable and no need to compile.

---

### Post by MJN on 2008-07-31
It was the historical aspect that interested me - of course the last known address is the most useful, however those leading up to it is of benefit also. Furthermore, Adeora can provide a little more info such as the local IP (necessary for helping pinpoint an individual behind a NAT) and the WLAN SSID (could be useful if it's, say, a public wireless hotspot with local CCTV). The application is in the very early stages of development and may include further local details in due course - indeed the Mac version already can take a photo using the built-in camera.
 
Of course there are no guarantess that this sort of tool will prove any benefit whatsoever but for something so simple it's a no-brainer to have it 'just in case'. For this reason I agree that a simple dynamic IP client still has some value.
 
Mathew

---

### Post by picopir8 on 2008-07-31
Question 1: How effective would some software program be?  A smart criminal is probably going to defeat any type of software that might find them.  A stupid criminal is likely going to get caught by much simpler means.

Question 2: Do you really want such a program?  For a program to be effective, it needs to run even when you are using the program.  That means potential performance decrease while you use the computer and the possibility that someone could abuse the software to keep track of you.

Question 3: Do you want something back after it has been stolen?  Many goods are damaged in the process of stealing, also the item is likely not as valuable to a thief than to you (and if they break it they will just steal another).  So its likely that the item will be damaged if returned.  However, if it is not found, you can just make a claim to your insurance and get a new one.

Data is what is the most valuable thing for most people.  If you make sure you back things up and encrypt both the originals and backups against unauthorized use, then your data should be save yet recoverable.

---

### Post by MJN on 2008-07-31
> **picopir8 said:**
> Question 1: How effective would some software program be?  A smart criminal is probably going to defeat any type of software that might find them.  A stupid criminal is likely going to get caught by much simpler means.Read my post again - there are no guarantees with any security tool, particularly ones of this nature. Its value is in the fact there is a chance that it *might* work. Neither you nor I know the calibre of the thief that will steal my machine and so I'm taking a zero-risk (to me) chance that it *might* just work. To use your logic, what if my thief is somewhere between 'smart' and 'stupid'?

> Question 2: Do you really want such a program?  For a program to be effective, it needs to run even when you are using the program. That means potential performance decrease while you use the computer and the possibility that someone could abuse the software to keep track of you.It runs continuously in the background, most of the time just sleeping - only every so often does it update the remote server with location information. There are no performance issues whatsoever with this level of resource requirement with a modern computer. I'd save considerably more resources by putting a simpler photo on my desktop background. The possibility of someone tracking me is minimal given the encryption involved - that is exactly one of the drivers behind this particular application that sets it aparts in this field.

> Question 3: Do you want something back after it has been stolen?  Many goods are damaged in the process of stealing, also the item is likely not as valuable to a thief than to you (and if they break it they will just steal another).  So its likely that the item will be damaged if returned.  However, if it is not found, you can just make a claim to your insurance and get a new one.I want to make that choice - and this tool may help me to that. The point you are missing is that there is every chance my laptop won't be the only thing stolen - if they take the laptop and I happen to get lucky with this tool then I increase my chances of also recovering the jewellery and other sentimental items that they might also take - stuff whose value to me is not measurable in £'s nor is replaceable through any insurance policy.

> Data is what is the most valuable thing for most people. If you make sure you back things up and encrypt both the originals and backups against unauthorized use, then your data should be save yet recoverable.I agree, however I couldn't care less about the contents of my laptop - all my data is held securely on the server.

Mathew

---

### Post by markaron on 2008-09-05
There is this great [laptop tracking]("http://www.inspice.com/en/Trace.htm") from inspice. Check it out at [http://www.inspice.com](http://www.inspice.com)

---

### Post by tom66 on 2008-09-05
Are many criminals smart? Quite a lot of thefts are opportunistic crimes, and I don't think it's likely that someone will remove the HDD from a laptop if they had stolen it, to them it's just a computer. They might wipe the drive but I think they'd boot it just to try it out. Software solutions may be effective.

---

### Post by Tindytim on 2008-09-05
Why not something hardware? Seems like the most fool proof thing to do. Solder a device to the inside of the case that's only connected to the power and nothing else.

The thief may not be connected to the internet, may remove, replace, or reformat the hard drive. Or the thief may immediately sell it to someone who knows about these things.

A Hardware solution means the machine doesn't have to be one, doesn't need the same hard drive.

---

### Post by PartisanEntity on 2008-09-05
not sure of any such application for ubuntu, but there is a great one for osx called orbicule, too bad there isnt one for ubuntu

---

### Post by airtonix on 2009-12-02
anything that loads after bios is not good enough.

solution needs to exist after a re-install of the operating system or change of hardware.

ideally a custom bios.

---

