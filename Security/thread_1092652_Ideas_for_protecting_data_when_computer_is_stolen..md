---
title: "Ideas for protecting data when computer is stolen."
date: 2009-03-10
forum: Security
---

### Post by lavinog on 2009-03-10
I had a couple of desktops stolen at work recently.
For the most part we didn't loose much, they were cheap computers, and easily replaceable.
The problem is that one of the computers has things like payroll data (quickbooks), contracts, and other data that could be considered sensitive.
I feel pretty confident that the drives are going to get wiped, since the login is password protected, and we know that it was stolen by kids.

I am looking for future protection of the data that will be on the replacement machine.
Sure I can use encryption, but that is only as secure as the user using it (the boss who i don't trust with passwords) I am thinking of using the network to tell if the system was stolen:

The problem is that the computer will be running windows (quickbooks, and the boss are not compatible with linux)
So I am thinking I can dual boot, and boot into linux shell with networking by default (no grub menu.) Do some tests like testing for a network connection, pinging known servers, checking external ip. If the tests pass, then grub is configured to boot into windows, and the system reboots. If the tests fail, then the system is considered compromised and the drive gets wiped. In the slim chance that the system has a network connection, it could try and report its location.

The questions are:
How can I get grub to automatically boot to windows, and keep the linux boot as default?
It seems like I would have to have a script in windows to change menu.lst back to default...maybe using ext2ifs. (could grub be installed on a fat partition?)
I hear grub2 has some scripting support...could i use a grub script to check existence of a file to determine what to boot to, then remove the file?

I was also considering damaging the bios so the system doesn't even boot (what good is a stolen computer if it cant boot.)  There are so many warnings about destroying bios...is there a surefire way of doing this? (this might have to work by theory, since I don't have the funding to test out any ideas ;) )

On a side note: we normally have a good backup setup...everything was getting backed up multiple times a day to a file server...except last month: My bosses computer was recently updated to vista. We filled up the server during the transition, so we setup an external drive for backups temporary until I had time to add more space to the backup server...They stole the external drive...so we are missing a month of stuff.
I am bringing this up because I come across alot of people that use flash drives for backups and leave the flash drives connected to their computer.

---

### Post by noelvh on 2009-03-10
I use trucrypt from [http://www.truecrypt.org/](http://www.truecrypt.org/) to protect my data.
Installs to ubuntu, and works great to creat a protected storage ares on a hard drive.

Noel

---

### Post by slowth5 on 2009-03-10
Hi lavinog,

I can only address a couple of your questions since I don't know much about networking.  

I wouldn't take the risk of data theft lightly, since cracking a Windows password is trivial, especially if the password is alphanumeric and less than 14 characters.  If the data is sensitive, then I second noelvh's recommendation of encrypting the entire drive with Truecrypt.  Using Truecrypt in Windows is a rare pleasure.  Here's a guide for Windows whole-drive encryption from Tom's Hardware:

[http://www.tomshardware.com/reviews/truecrypt-security-hdd,2125-3.html](http://www.tomshardware.com/reviews/truecrypt-security-hdd,2125-3.html)

As for damaging the BIOS, this will destroy the machine.  I'm almost positive that once the BIOS is damaged, the system is unusable.  You would have to send the manufacturer the chip so it could be reflashed, or you could order another BIOS chip from the manufacturer.  It's an interesting thought, but I don't think it's practical.

---

### Post by lavinog on 2009-03-10
I will have to give truecrypt a try. Thanks for the info

---

### Post by abn91c on 2009-03-10
besides BIOS passwords, there are  Free Lowjack type programs 'available, can't think of the names but you can google them and install them

---

### Post by Tubes6al4v on 2009-03-11
In the end, it is all about the data. Bios passwords and other lowjack stuff will not prevent you from pulling the drive and pluging it in elsewhere. Also, if you do the Grub networking thing, it may work, but if the theif were thinking of how to best get the data, they would use a Live CD before booting into the system, thus bypassing it.

To reinforce the point, your best bet is full disk encryption.

---

### Post by lavinog on 2009-03-11
Bios passwords are pretty worthless since reseting them just requires a jumper.

I had another idea, to bolt down the computers.

The information on our computers wasn't really anything that someone would actively seek out. The issue is that I would sleep better knowing that some kid isn't doing a detailed search of the filesystem for anything interesting (For instance: A document I wrote to explain how to add wireless clients to our AP when I am not available.) I think truecrypt will be the way to go.

I think the issue with full disk encryption is that you lose your chance at recovering your computer. Not everyone has insurance to replace their computer. I think there are thieves that will connect to the internet with a stolen laptop, or at least sell it to someone who will. If there is a password on it, they will just wipe it, and any measures you have in place to find it.

As far as destroying the bios. It could be possible to just flash it with a bad rom. Even then, some of the more modern mobos have dual bios for those times when you mess them up. 
The point of destroying the bios was to make the computer worthless (or at least semi-worthless) to the thief...this way they don't get rewarded if they don't get caught...Apparently there are many thieves that don't know much about computers, or know just enough to wipe hds and install pirated copies of windows. In our case, they stole a computer that we bought brand new a couple of years ago for $300, while leaving behind the computer with better specs, probably because it didn't have a fancy blue light, and shiny case.

---

### Post by hyper_ch on 2009-03-11
for windows, use truecrypt full disk encryption mode

for linux go with dm-crypt/luks for full disk encryption

for usb sticks use truecrypt as get support for windows, mac and linux

---

### Post by Nxion on 2009-03-11
I had to get my 2 cents in here :)

Full disk encryption is one way. Another to consider is GnuPG or PGP. You can encrypt data on a file by file basis. I know with FDE (full disk encryption) there is a performance hit in some cases, but if they aren't doing anything resource intensive, then it shouldnt matter.

---

### Post by hyper_ch on 2009-03-11
> **Nxion said:**
> I know with FDE (full disk encryption) there is a performance hit in some cases

What are those cases? And what about truecrypt/gnupg? Do you get there also performance hit?

What about file left-overs due to temporary storage or journaling filesystem?

---

### Post by Nxion on 2009-03-11
> **hyper_ch said:**
> What are those cases? And what about truecrypt/gnupg? Do you get there also performance hit?

What about file left-overs due to temporary storage or journaling filesystem?

Whoops, I was talking about a different FDE software that we use where I work. The one we use gives us performance issues. I have had no problems with truecrypt. My bad, had to much stuff on the brain :)

---

### Post by hyper_ch on 2009-03-11
> **Nxion said:**
> Whoops, I was talking about a different FDE software that we use where I work. The one we use gives us performance issues. I have had no problems with truecrypt. My bad, had to much stuff on the brain :)

Well, dm-crypt has "performance" issues if you have large file operations --> reading/writing large files... you'll notice normally at a rate of about 100mb that it's getting slower. Below that you (well, at least I) don't notice any impact on performance.

---

### Post by Nxion on 2009-03-11
I really wish I can convince my company to switch to truecrypt. I lost count on how many presentations and testimonials I have brought to them saying that truecrypt is better then what we have...

---

### Post by noelvh on 2009-03-11
In my company we have gone with full drive encryption and have not really seen a per hit after the first boot. Once the hard drive is open then it works very well. The one big issues I have with full drive encryption is if the drive has issues you can not fix them. I like truecrypt for the fact i can create a file and mount the file as a drive. Once mounted I can use this for storage, and this file can live on other machines. Now if the drive has issues I can copy the file off and open it on another machine using truecrypt. Now I have opened truecrypt file from other machines under my ubuntu machine as a test, so it dose not need to be with the machine it was created on.

Noel

---

### Post by bodhi.zazen on 2009-03-11
I have not noticed a performance hit with "full encryption" (/boot is not as of yet encrypted ;) )

I am sure if you ran metrics you would find a difference, but I do not notice it much as I use the box.

---

### Post by hyper_ch on 2009-03-11
noevl: regular backups are a must. if you fully encrypt your system then you can still do a backup from a unlocked system to another unlocked fully encrypted system. That way you make backups.

---

### Post by noelvh on 2009-03-11
> **hyper_ch said:**
> noevl: regular backups are a must. if you fully encrypt your system then you can still do a backup from a unlocked system to another unlocked fully encrypted system. That way you make backups.

Very true, but only if the end users take the time and backup there data. We provide our users with synced networked drive but the users refuse to use this as a means of safeguarding there data. What they do is save the data to folder on there desktop. So if you are in a perfect world ware users take care with there data you are correct. As this world is not perfect I like the Idea of being able to get to the data even if the drive fails, as I am the backup process in the end users mind.

In the end as long as the data that needs to be safeguarded is protected then it dose not matter what approach one uses.

Noel

---

### Post by cryogen on 2009-03-12
Since nobody has mentioned this yet, before going to the trouble of deploying full disk encryption, make sure you're aware of the cold boot attack and the risks:

[http://citp.princeton.edu/memory/]("http://citp.princeton.edu/memory/")
[http://en.wikipedia.org/wiki/Cold_boot_attack]("http://en.wikipedia.org/wiki/Cold_boot_attack")

Last I heard TrueCrypt was vulnerable along with everyone else and as far as I know this has not been mitigated yet.

---

### Post by hyper_ch on 2009-03-12
> **cryogen said:**
> Since nobody has mentioned this yet, before going to the trouble of deploying full disk encryption, make sure you're aware of the cold boot attack and the risks:

that's old news... there's no real protection against that... maybe with an on-harddisk encryption module that just gets set once... but not even sure about that. While cold boot attacks are "simple" one first has to know that you'd take according actions.

---

### Post by lavinog on 2009-03-13
If I use truecrypt to encrypt the whole drive, will I be able to install ubuntu from the live cd afterwards?

Do I have to wait until after ubuntu is installed to encrypt the whole drive?

Also will it affect upgrading to jaunty when it is released?

---

### Post by bodhi.zazen on 2009-03-14
If you wish to encrypt your entire installation, use the Alternate CD, encryption is an option as you are installing.

I do not think you can use Truecrypt.

---

### Post by hyper_ch on 2009-03-14
> **lavinog said:**
> If I use truecrypt to encrypt the whole drive, will I be able to install ubuntu from the live cd afterwards?

you can't use truecrypt to fully encrypt linux. You need to use luks/dm-crypt from the alternate/server edition.

---

### Post by lavinog on 2009-03-14
> **hyper_ch said:**
> you can't use truecrypt to fully encrypt linux. You need to use luks/dm-crypt from the alternate/server edition.

Ah, Truecrypt has linux listed as a supported os, but not listed as supporting system encryption...kind of misleading when they list this info on two different pages

If I can't do full disk encryption, what benefit does truecrypt offer over vista's built-in encryption?

---

### Post by hyper_ch on 2009-03-14
can you audit the windows built-in encryption and veryify there's no backdoor?

---

