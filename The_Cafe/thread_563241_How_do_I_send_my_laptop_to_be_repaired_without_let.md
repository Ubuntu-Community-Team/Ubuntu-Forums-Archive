---
title: "How do I send my laptop to be repaired without letting the company snoop on my data?"
date: 2007-09-29
forum: The Cafe
---

### Post by CSMatt on 2007-09-29
So for a while now my laptop's power LED has been turning on and off and random intervals, until it eventually stopped illuminating altogether.  While I'm fine with the lack of a power LED (especially considering that there are two other LEDs on my machine that indicate when the power is on), I just recently also had the misfortune to drop my laptop.  Although it landed closed on the back of its screen with the only visible problems being that the hard drive case popped out and the LCD screen appearing to be very lightly "stained" in several places, I would feel better if I got the laptop checked out by the OEM (ASUS in this case).  While I am still under warranty and said warranty should certainly cover the power LED, I know that it won't cover user-caused things like falls.  That's not a problem; I don't mind paying for the repairs for the fall.  However, I'm concerned that the repair shop might snoop around my hard disk and browse through my private files.  I would encrypt the drive, but there are three problems:
[LIST=1]
[*]I don't see how the laptop would boot for the repair shop if the drive is encrypted.
[*]I don't know if I can effectively encrypt my NTFS partition
[*]It may actually be illegal to encrypt my drive. (See [http://yro.slashdot.org/article.pl?sid=07/07/27/2310247](http://yro.slashdot.org/article.pl?sid=07/07/27/2310247))
[/LIST]

What should I do about this?

---

### Post by cogadh on 2007-09-29
If the problems are just with hardware other than the hard drive, then give them the laptop with the hard drive removed. Any good repair shop keeps extra drives around for just such occasions.

---

### Post by CSMatt on 2007-09-29
Wouldn't it look weird though that I sent the laptop in without a hard drive?

Also, I'm not 100% sure that the hard drive didn't get some amount of damage as well.  The label on the drive indicates that it should not be dropped.  Is there some tool I can run on it to check for physical defects?

---

### Post by Polygon on 2007-09-29
can you back everything  up and just do a fresh install of whatever your using on it? (xp?)

if not you can use truecrypt to encrypt all of your important stuff (google it)

---

### Post by cogadh on 2007-09-29
> **CSMatt said:**
> Wouldn't it look weird though that I sent the laptop in without a hard drive?
Probably not, I used to do it all the time. I just used to just have to tell them in advance and give them an excuse like the drive has sensitive and confidential business data on it.

---

### Post by CSMatt on 2007-09-29
So is there a way that I can test the whole hard drive for physical defects then? The only thing that comes to mind is ChkDsk, and that of course won't work with ext3.

---

### Post by cogadh on 2007-09-29
There any number of drive testing utilities available, Google it, I'm sure you'll get quite a few useful hits.

---

### Post by popch on 2007-09-29
You can certainly send your computer in without the disk. Add a note to the the computer saying 'disk intentionally removed' or some such.

If your disk was damaged by the drop, I would presume that it would not work at all. To be on the safe side, I would buy a replacement disk and copy the dropped one.

And there certainly are commands to check your disk, though I do not know them. Better ask someone who knows commands.

---

### Post by holiday on 2007-09-29
> **CSMatt said:**
> So is there a way that I can test the whole hard drive for physical defects then? The only thing that comes to mind is ChkDsk, and that of course won't work with ext3.

The best drive check for physical defect will be available through the manufacturer. Most have utilities you can download. They may be a bit spooky to use, but take a deep breath and work through the docs.

---

### Post by HermanAB on 2007-09-29
The Linux equivalent of chkdsk if fsck.

I also suggest removing the HDD before sending it in for repair.  Just add a note saying that the drive has been removed since it contains sensitive data.  The repair shop won't even blink.  In fact they will likely think better of you for being a clueful user!

Cheers,

H.

---

### Post by CSMatt on 2007-09-29
I know about fsck, but I don't think that it checks for physical errors, and I know that it won't check NTFS partitions.

> **holiday said:**
> The best drive check for physical defect will be available through the manufacturer. Most have utilities you can download. They may be a bit spooky to use, but take a deep breath and work through the docs.
ASUS, or the actual HD manufacturer?

---

### Post by Polygon on 2007-09-29
> **HermanAB said:**
> The Linux equivalent of chkdsk if fsck.

I also suggest removing the HDD before sending it in for repair.  Just add a note saying that the drive has been removed since it contains sensitive data.  The repair shop won't even blink.  In fact they will likely think better of you for being a clueful user!

Cheers,

H.

or curse you because they cant search your HD for porn xD

---

### Post by regomodo on 2007-09-29
use 2 hdds.

Done. Simple

---

### Post by Spike-X on 2007-09-29
Get an external HD and move all your por...er..."sensitive files" to that.

---

### Post by macogw on 2007-09-29
> **CSMatt said:**
> I know about fsck, but I don't think that it checks for physical errors, and I know that it won't check NTFS partitions.


ASUS, or the actual HD manufacturer?

fsck can do ntfs, i think.  it can do a lot of different file systems.  definitely does fat, thought it did ntfs too

probably the actual mfgr

---

### Post by JBAlaska on 2007-09-29
My neighbor just sent his sony viao back to have a replacement KB installed (the esc key was shorted) unfortunately he had some "scene" tagged AVI's on the laptop..

He got it back with a re-imaged HD. when he called to complain, they told him re-imaging was a "standard procedure " on all repairs..wtf?

---

### Post by Depressed Man on 2007-09-29
They probably do have some standard repair process. 

Ugh, makes me dread sending my VAIO back. I'd hate to redo everything in Gutsy and Vista yet again. I'd probably remove the HDD or backup everything to re-re-image it.

---

### Post by cogadh on 2007-09-29
"standard procedure"!? In what Bizarro universe would re-imaging a drive *ever* be considered "standard procedure"? Especially for a simple hardware replacement like a keyboard. On most laptops, that is actually a modular part that could be swapped out by most end users with half a brain and a Phillips head screwdriver (while drunk, in the dark, with one hand tied behind your back...).

---

### Post by Depressed Man on 2007-09-29
Haha I know, it sounds stupid. But from what I've seen and heard in IT, it's possible.

---

### Post by cogadh on 2007-09-30
Yeah, I know. Speaking as a former IT manager, I can tell you IT departments and their policies can be just as messed up as the *lusers* they are supposed to support. Still, I don't think I've ever heard anything as messed up as making re-imaging a standard procedure. Crap like that never would have flown in my shop.

Yet another reason to send your machine in for repairs with the drive removed...

---

### Post by laxmanb on 2007-09-30
Put your critical documents in a folder, zip the folder with encryption, delete the original folder.

when you get your laptop back, unzip your files and you're set!

---

### Post by odiseo77 on 2007-09-30
laxmanb's suggestion seems good. Don't know if this has been mentioned here, but there's a little app (a freeware) I remember I used some years ago, when I was a windows user, named camouflage, which allows you to hide some data inside a simple file (you can hide a private document inside a picture, for example, and the only thing visible from the outside would be the picture; of course, if it's a simple, small picture with 4 mb's it would be suspicious). The only downside is that it only runs on windows, so you must have windows installed.

Oh, and I guess you don't have a cd/dvd writer, because, otherwise you could easily backup all your private data into some cd's/dvd's, delete it from your HD, and restore it again when they give you your laptop back. :)

Greetings.

---

### Post by popch on 2007-09-30
When privacy concerns are the whole point of the thread, then deleting those files will not do. Deleted files can be recovered quite easily, in quite a few cases.

---

### Post by CSMatt on 2008-01-10
I just got the RMA from ASUS with shipping instructions and it seems like they want or need the drive.  I was told to give them my Windows password so that they can use the OS for "testing purposes."  While I am certainly not going to give them my password, it sounds like they don't have any alternative way to boot up the computer without the original OS.  They did however send me a sheet to list the components of my laptop and their quantity and capacity, so I guess I could just say "0" for the quantity of the hard drive and send them a LiveCD if they really don't have any other way to boot the computer, but would they really be able to fix my machine without a hard drive?  This sounds like a standard procedure e-mail sent out to every customer who RMAs them, but I'm not sure that they won't refuse to fix the machine because of the lack of a hard drive.

Another thought occurs: ASUS says something along the lines of their computer being guaranteed to work with the factory install, but that it would become void if "third-party" software were to be installed.  This is just a software guarantee and not related to the warranty, right?

---

### Post by Jimmey on 2008-01-10
Perhaps opening your laptop and removing the drive will void the warranty anyway. I know my Dad's desktop has a warranty that will disappear the second you open the case yourself.

If backing up is an option, I'd do that. 

My setup ( I have a laptop connected to a desktop via a x-over cable ) allows me to make backups of data on either machine quite easily. Maybe you could look into that?

---

### Post by CSMatt on 2008-01-10
My laptop has a separate cover for removing the hard drive, so I doubt that opening that would void the warranty.

And what kind of desktop warranty is voided if you open the case?  Sounds like your dad got screwed.

---

### Post by Mateo on 2008-01-10
just install windows and set it as default in grub.

---

### Post by user1397 on 2008-01-10
> **CSMatt said:**
> I just got the RMA from ASUS with shipping instructions and it seems like they want or need the drive.  I was told to give them my Windows password so that they can use the OS for "testing purposes."  While I am certainly not going to give them my password, it sounds like they don't have any alternative way to boot up the computer without the original OS.  They did however send me a sheet to list the components of my laptop and their quantity and capacity, so I guess I could just say "0" for the quantity of the hard drive and send them a LiveCD if they really don't have any other way to boot the computer, but would they really be able to fix my machine without a hard drive?  This sounds like a standard procedure e-mail sent out to every customer who RMAs them, but I'm not sure that they won't refuse to fix the machine because of the lack of a hard drive.

Another thought occurs: ASUS says something along the lines of their computer being guaranteed to work with the factory install, but that it would become void if "third-party" software were to be installed.  This is just a software guarantee and not related to the warranty, right?did you install ubuntu on this said laptop?

---

### Post by user1397 on 2008-01-10
> **CSMatt said:**
> My laptop has a separate cover for removing the hard drive, so I doubt that opening that would void the warranty.

And what kind of desktop warranty is voided if you open the case?  Sounds like your dad got screwed.Actually, this is quite common nowadays; I think both Gateway's and HP's warranties are like that.

---

### Post by BLTicklemonster on 2008-01-10
I think it's creepy that repair people snoop when working on a person's computer.

At least I get a creepy feeling every time I do it; I don't know about you all. But man, you can find some really neat stuff!!!

---

### Post by blastus on 2008-01-11
> **BLTicklemonster said:**
> At least I get a creepy feeling every time I do it; I don't know about you all. But man, you can find some really neat stuff!!!

Yet you don't feel creepy enough not to do it. :) Seriously, I don't think there is a single repair technician on the planet, who having time to waste, would not snoop and scour the personal data on someone's machine.

The suggestion that you can protect individual files by encrypting them is completely ridiculous. The simple fact is that the original unencrypted files probably exist somewhere on the hard drive and can be recovered or if not they may exist in some cache somewhere. The only way to protect data is to encrypt every partition on every drive. Nevertheless you should remove every hard drive before handing over your computer.

---

### Post by Ocxic on 2008-01-11
most hard disk can withstand a drop force of 360 G's when turned off and 60 G's while in operation, so if your laptop was turned off when you droped it, then you should be fine so long as the drop was not large. second encrypting data is not illegal. security agencies just don't like that you can do it cause it can hide evidence.
if your that worried remove the drive, or backup your data and format.

---

### Post by bobbob94 on 2008-01-11
While its true that just encrypting a folder or file is not foolproof because of the possibility of  recovering data from an unencrypted swap file or whatever, we're talking about sending it in for repair, not protecting data from an FBI forensic analysis lab. I doubt bored repair shop employees are gonna scour the hard drive for fragments of files instead of just poking around in the next laptop in the queue thats probably got no encryption problem for them at all...

---

### Post by popch on 2008-01-11
> **bobbob94 said:**
> While its true that just encrypting a folder or file is not foolproof because of the possibility of  recovering data from an unencrypted swap file or whatever, we're talking about sending it in for repair, not protecting data from an FBI forensic analysis lab. I doubt bored repair shop employees are gonna scour the hard drive for fragments of files instead of just poking around in the next laptop in the queue thats probably got no encryption problem for them at all...

... unless they become irked because they can not read your stuff und for that reason try harder.

---

### Post by bobbob94 on 2008-01-11
> **popch said:**
> ... unless they become irked because they can not read your stuff und for that reason try harder.

Don't these people have jobs to do? :rolleyes: If they have enough spare time to start trying to dig up file fragments from swap just to look at people's porn collections maybe I'm in the wrong job:wink:

---

### Post by PartisanEntity on 2008-01-11
I bought a new hard drive for my laptop, so when/if I need to send my laptop in for repairs, I simply pop the original HDD back in to the laptop which contains the original OS that came with the it. Since I do not use it, it remains completely void of any personal data or software.

If possible, I recommend you do the same.

---

### Post by jken146 on 2008-01-11
With regard to warranties and whatnot, I guess it depends on which country you're in, but you should still have rights to repair or replacement or refund on your purchase if the hardware is defective, from the place that sold it to you (not the manufacturer), regardless of the software on it.

---

### Post by nocturn on 2008-01-11
Use PGP to encrypt the files, keep the key on a USB disk.
Or just use encrypted containers ([http://www.mayrhofer.eu.org/Default.aspx?pageindex=6&pageid=34](http://www.mayrhofer.eu.org/Default.aspx?pageindex=6&pageid=34))

---

### Post by CSMatt on 2008-01-11
Well, I've decided to send it in without the hard drive and hope for the best.  Thanks to everyone for their replies.

---

### Post by rrwo on 2008-01-11
Just remove the hard drive.

I once sent an HP laptop in to be fixed after a BIOS update broke it, and hte company decided to (re)install Windows for me, wiping my Windows and NetBSD partitions.  Since then, I'm more concerned about a company destroying my data than snooping.

---

### Post by BLTicklemonster on 2008-01-11
> **blastus said:**
> Yet you don't feel creepy enough not to do it. :) Seriously, I don't think there is a single repair technician on the planet, who having time to waste, would not snoop and scour the personal data on someone's machine.

The suggestion that you can protect individual files by encrypting them is completely ridiculous. The simple fact is that the original unencrypted files probably exist somewhere on the hard drive and can be recovered or if not they may exist in some cache somewhere. The only way to protect data is to encrypt every partition on every drive. Nevertheless you should remove every hard drive before handing over your computer.

Yes, remove the hard drive, because you really shouldn't trust these people to be competent enough to actually repair what they need to repair in the first place, so what good is it to let some yahoo mess up your hard drive anyway? Or something like that. Got a phone to my ear while I'm trying to type this.

---

### Post by Bruce M. on 2008-01-11
> **JBAlaska said:**
> He got it back with a re-imaged HD. when he called to complain, they told him re-imaging was a "standard procedure " on all repairs..wtf?

> **cogadh said:**
> "standard procedure"!? In what Bizarro universe would re-imaging a drive *ever* be considered "standard procedure"? Especially for a simple hardware replacement like a keyboard. On most laptops, that is actually a modular part that could be swapped out by most end users with half a brain and a Phillips head screwdriver (while drunk, in the dark, with one hand tied behind your back...).

 1. What is a "re-imaged" hard drive?

 - Is this like: My computer goes to the shop with drive "A", they make an image of it and put it on drive "B" and put "B" in my computer?  If so, what happens to drive "A"?

 2. How would someone know that they have one?

I hope we find out what happened when the computer comes back.

Bruce

---

### Post by CarpKing on 2008-01-11
> **odiseo77 said:**
> Don't know if this has been mentioned here, but there's a little app (a freeware) I remember I used some years ago, when I was a windows user, named camouflage, which allows you to hide some data inside a simple file (you can hide a private document inside a picture, for example, and the only thing visible from the outside would be the picture; of course, if it's a simple, small picture with 4 mb's it would be suspicious). The only downside is that it only runs on windows, so you must have windows installed.

You don't really need an application to do that.  Even in windows you can do it from the command line.  In Linux it's:

```
cat picturefile.jpg rarfile.rar > newfilethatisNOTtherarfileorpicturefile.jpg
```

But yes, an unusually large picture file would look suspicious.  I also can't imagine it would be too hard to find out what kind of file it really was (to open the rar or zip or whatever you have to know the original extension and change it to that).

---

### Post by macogw on 2008-01-11
> **Bruce M. said:**
> 1. What is a "re-imaged" hard drive?

 - Is this like: My computer goes to the shop with drive "A", they make an image of it and put it on drive "B" and put "B" in my computer?  If so, what happens to drive "A"?

 2. How would someone know that they have one?

I hope we find out what happened when the computer comes back.

Bruce

It means they used their default installation image (so like Windows XP + some trialware junk) and reinstall it on your hard drive so all your stuff is gone...it'll be just like when you bought it.

---

### Post by macogw on 2008-01-11
> **Jimmey said:**
> Perhaps opening your laptop and removing the drive will void the warranty anyway. I know my Dad's desktop has a warranty that will disappear the second you open the case yourself.
but...but...but...the dust!!!  How do they expect you to clean out the dust?  You must clean out the dust or it will overheat and break!  Are they stupid?!  I just saw a computer that had a Pentium 4 and ran slower than my Pentium 2 because the heatsink/fan were so clogged with dust and the thermal compound so hardened that it just overheated instantly and kept scaling the CPU further and further down (slower and slower) to try to cool off.

---

### Post by Bruce M. on 2008-01-12
> **macogw said:**
> It means they used their default installation image (so like Windows XP + some trialware junk) and reinstall it on your hard drive so all your stuff is gone...it'll be just like when you bought it.

Excuse me!  And that's legal?

I'll fix my own, to h*** with the guarantee (my edit of the word)

Bruce

---

### Post by popch on 2008-01-13
> **Bruce M. said:**
> Excuse me!  And that's legal?

It's "legal" if it's in the contract you got when buying the thing. Usually, you can try and have them waive that clause before buying. In some countries, you have even a chance after the sale when you can plausibly claim that your contract violates more basic right and thus is not applicable to you. That's - by the way - not so unusual in countries which protect consumers' rights.

It is even possible that you have a case after the fact (i.e. after they restored your disk to pristine condition). You could argue that someone deleting the files from someone else's computer is committing an act punishable by law, and that the shop did indeed destroy the files on your computer entrusted to them. But then, it comes back to the contracts of the sale and of the repair, again.


Better safe than sorry, and a stich in time saves nine.

---

### Post by popch on 2008-01-13
> **Presto123 said:**
> Or, am I being too dramatic here?

No, just silly. Not appreciated.

---

### Post by Bruce M. on 2008-01-13
Hi popch

> **popch said:**
> It's "legal" if it's in the contract you got when buying the thing. Usually, you can try and have them waive that clause before buying. In some countries, you have even a chance after the sale when you can plausibly claim that your contract violates more basic right and thus is not applicable to you. That's - by the way - not so unusual in countries which protect consumers' rights.

Even more reason to "build your own", but I don't think that can apply for a laptop.  I've never seen or heard of an empty laptop case that you can buy to "build" your own.

> **popch said:**
> It is even possible that you have a case after the fact (i.e. after they restored your disk to pristine condition). You could argue that someone deleting the files from someone else's computer is committing an act punishable by law, and that the shop did indeed destroy the files on your computer entrusted to them. But then, it comes back to the contracts of the sale and of the repair, again.

After the fact still means that your files are gone!  But in the case above you may have a chance of "monetary" compensation.  Not always a solution.

> **popch said:**
> Better safe than sorry, and a stich in time saves nine.

Therefore: Read the fine print.  (with my eyes, I'd have to carry a magnifying glass.)

Bruce

---

### Post by popch on 2008-01-13
> **Bruce M. said:**
> Even more reason to "build your own", but I don't think that can apply for a laptop.  I've never seen or heard of an empty laptop case that you can buy to "build" your own.

I don't know about empty cases, as they would need a motherboard especially made for the case, anyway. There are suppliers who sell 'barebone laptops' to be embellished by the customer. ASUS comes to mind.

> **Bruce M. said:**
> After the fact still means that your files are gone! But in the case above you may have a chance of "monetary" compensation. Not always a solution.

Therefore: Read the fine print.  (with my eyes, I'd have to carry a magnifying glass.)

I have been known to ask for a magnified copy of a contract or - if in a shop which carries them - for a magnifying glass. In some respects I am very strict, and one of those is accessibility of printed matter. If they are not able to present readable stuff, I make them suffer for it.

However, that only works if you're not overly eager to close the deal. You have to be able to refuse to do business under the conditions imposed on you.

---

### Post by Bruce M. on 2008-01-13
> **popch said:**
> I don't know about empty cases, as they would need a motherboard especially made for the case, anyway. There are suppliers who sell 'barbone laptops' to be embellished by the customer. ASUS comes to mind.

Oh, I'll have to check that out. I had no idea.

> **popch said:**
> I have been known to ask for a magnified copy of a contract or - if in a shop which carries them - for a magnifying glass. In some respects I am very strict, and one of those is accessibility of printed matter. If they are not able to present readable stuff, I make them suffer for it.

=D> Good for you!  I can imagine myself going into a store, coffee and collapsible chair in hand and saying, "I want to read the contract before I buy the computer."
 "Excuse me?"
 "I said, I want to read the contract before I buy the computer!"
 "You can do that at home!"
 "Great, give me the contract, and I'll return tomorrow with my decision."
 "No, I meant after you buy the computer."
 "Yea, right!" as he sees my back-end leaving the premises.
 
> **popch said:**
> However, that only works if you're not overly eager to close the deal. You have to be able to refuse to do business under the conditions imposed on you.

I'm never in that much of a rush unless it is a life and death situation.
Reminds me of an exchange I over heard in a Credit Union years ago:

Teller: "Here you are sir.  Sorry it took so long."
Customer: "That's OK, I have to breathe until the day I die, I have no problem doing some of it here."

Talk about a great attitude!
Bruce

---

### Post by popch on 2008-01-13
> **Bruce M. said:**
> Oh, I'll have to check that out. I had no idea.

I've mispelt it. It's barebone or even bare bone, not barbone. Nothing to do with barbeque.

> **Bruce M. said:**
> I can imagine myself going into a store, coffee and collapsible chair in hand and saying, "I want to read the contract before I buy the computer."

The only problem I have with that scenario is the collapsible chair. Those things have a way of doing exactly that.

I have yet to see a member of sales staff refusing to let me see the contract (or 'terms of sale' or whatever they happen to call them). They are perfectly aware that they have no chance of selling anything if they make a fuss about disclosing their conditions.

If you handle yourself the right way, some of them even will assume that there was some kind of inspection or testing going on and might offer the coffee to you which you neglected to bring along. Accepting that, however, would be quite dishonest and is not to be endorsed.

---

### Post by Bruce M. on 2008-01-13
> **popch said:**
> I've mispelt it. It's barebone or even bare bone, not barbone. Nothing to do with barbeque.

It's normal to make typos every now an then.  I understood what you meant.
I'll have my steak medium-rare please!

> **popch said:**
> The only problem I have with that scenario is the collapsible chair. Those things have a way of doing exactly that.

:) I meant it figuratively speaking, but I know what you mean, they can be nasty at times.

> **popch said:**
> I have yet to see a member of sales staff refusing to let me see the contract (or 'terms of sale' or whatever they happen to call them). They are perfectly aware that they have no chance of selling anything if they make a fuss about disclosing their conditions.

If you handle yourself the right way, some of them even will assume that there was some kind of inspection or testing going on and might offer the coffee to you which you neglected to bring along. Accepting that, however, would be quite dishonest and is not to be endorsed.

Not being in the business of buying for a company or others, I've never really had a problem like that. Most of the computers I've bought (up until I started building my own) were from people I knew and trusted, and were still custom built with parts I chose.

---

