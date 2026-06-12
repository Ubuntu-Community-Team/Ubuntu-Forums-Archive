---
title: "RAID5 usage"
date: 2005-07-25
forum: Server Platforms
---

### Post by poptones on 2005-07-25
I'm currently in the process of getting two maxtor drives replaced under warranty. My first impulse has been to ditch them when they come back and buy Seagates, but I'm planning to use them in a RAID5 this time anyway and, since they have about 18 months left under warranty I'm wondering if it might be practical to just keep them until they're no longer covered and trash them then.

They're 160GB drives which I am planning to configure as 3x120GB or so with "scratch" area on each. Because my experience with maxtors has been very poor I am going into this expecting a failure within the next year. What I am wondering is, because these are error correcting and "self healing" at least so long as it is only one drive, when a drive is beginning to fail and just starting to lose sectors will it still be able to "correct" and provide read access to otherwise corrupt areas? IOW will the same facility that allows it to heal itself when rebuilding also allow it to reconstruct the data on the fly as it is requested while sending a message about the failure to the log? Or will I just get the same "unable to access..." error when sectors start dropping?

---

### Post by LordHunter317 on 2005-07-25
[QUOTE=poptones]They're 160GB drives which I am planning to configure as 3x120GB or so with "scratch" area on each.[/quote]Why?  Just use the whole disk for the array, the performance will be better.

> What I am wondering is, because these are error correcting and "self healing" at least so long as it is only one drive,What's these in that sentence?  The RAID array?  The drives?

>  when a drive is beginning to fail and just starting to lose sectors will it still be able to "correct" and provide read access to otherwise corrupt areas?If the drive fails in the RAID array, it's marked as such and no longer used.  Data is reconstructed from the rest of the array until the drive is replaced.

>  IOW will the same facility that allows it to heal itself when rebuilding also allow it to reconstruct the data on the fly as it is requested while sending a message about the failure to the log?If I understand what you're saying, yes.

---

### Post by poptones on 2005-07-25
> Just use the whole disk for the array, the performance will be better.

Well, I was going to do it like this for two reasons: one, the partition will be encrypted and I don't need 320MB of encrypted space. Two, I need some unencrypted workspace for video editing and capture and as a temp storage area for my existing data while I migrate it to the RAID. If I use the entire disc I will have to add another drive for these functions and that means another controller card and a lot more heat in a tiny box, which is impractical - so  essentially it means adding a whole new computer just to house my RAID.

---

### Post by LordHunter317 on 2005-07-25
[QUOTE=poptones]Well, I was going to do it like this for two reasons: one, the partition will be encrypted[/quote]Why?  Dobutful you have that much data that really needs to be encrypted.  Loopback file for what needs to be encrypted will be much better for performance.

>  Two, I need some unencrypted workspace for video editing and capture and as a temp storage area for my existing data while I migrate it to the RAID.Better would be to backup and restore off other medium for the migration.

DVD+-RW drive and a lot of DVD-Rs can be had for relatively cheap.

---

### Post by poptones on 2005-07-25
> Dobutful you have that much data that really needs to be encrypted. Loopback file for what needs to be encrypted will be much better for performance.

FWIW I have about 150GB of data that will go into this partition and more being added all the time. I keep *everything* on my system encrypted except for raw video captures and projects in post. Once it's finished, it goes into the encrypted space along with all my music, images, scripts, fonts - everything. I will eventually run out of space on this raid but I am only trying to put off buying a dedicated server for another few months.

Loopback files are not as convenient or serviceable as dm-crypt. Loopbacks are a single file - one wrong move and the entire archive is broken and has to be restored. dm-crypt works on a sector by sector basis which makes the data much more recoverable in the event of error. It also makes troubleshooting and repair easier because the sectors map - any tools you can use for recovery (like debug) will work whether you mount the partition as /dev/hdx or /dev/mapper/hdx. I can also make encrypted DVDs using dm-crypt and mount them just as easily as any other by altering a single line in my etc/fstab - in short, it's just a much better technology than the old fashion loopback device. Loopback devices have their uses, but encrypting drives isn't one of the better ones.

Moving all this data to DVDs means creating 40 DVDs. I could just as easily restore it from the 100+ CDs and not have to make new backups at all. But that would be silly, since I need about 80GB of unencrypted workspace anyway and copying from drive to drive is a lot easier than days swapping and unounting discs. The other 30GB on the third (OS) drive I will likewise partition as a separate, encrypted, /home space once I am finished with the move. It's way easier to restore that last 40GB of video from DVDs than 140GB of scattered data spread across hundreds of folders and tens of thousands of files..

Thanks for the info on the raid failures. This is turning into quite an interesting project...

---

### Post by LordHunter317 on 2005-07-25
[QUOTE=poptones]I keep *everything* on my system encrypted except for raw video captures and projects in post.[/quote]And that's your problem: you shouldn't be doing this.  The amount of data you have of actual sufficent value to be encrypted is probably a few tens of megabytes, at most.

For most people, it's not even a few tens of **kilo**bytes.


> dm-crypt works on a sector by sector basis which makes the data much more recoverable in the event of error.No, not really.  Guess how I do forensics?  dd(8) the raw drive to an image file and loopback mount it.

> Loopback devices have their uses, but encrypting drives isn't one of the better ones.Yes, but you're missing the point.  The point is, you don't need (nor should) to encrypt a whole drive.  You need to encrypt a few files.  And having a loopback image is more flexiable for that than encrypting the whole drive.

Actually, the most flexiable solution is probably to GPG encrypt whatever you need, and just leave it in the filesystem.  I have trouble swallowing that you need to encrypt that much data.

If you want to, that's your decision, but I think you'd have a much eaiser time with this whole project if you abandoned the need for encrypting your data.

---

### Post by poptones on 2005-07-25
"My problem?" The only "problem" I have pertaining to this discussion is two bad Maxtor drives and a resulting worspace that is so confined I'm hardly able to get any new work done until they return. 

I appreciate you answering the question I asked, but I'm **not** asking for your advice about data security - and, frankly, I find your advice **terrible** for a variety of reasons and anyone who really knows about data security is much more likely to agree with my approach than yours. You **cannot** have meaningful security if you only encrypt "packets" of data - so long as security is something that exists "over there" it's simply far too easy to have that trail of data leak - to a swap space or a temp file or even to a .conf file where some programs store their own MRUs for your convenience. Having "this and that" encrypted forces you to always have to think "ok is this data supposed to be encrypted or isn't it?" 

Encryption should not be an "option," viewed as a technology only for "special things." It's far *easier* to use once you make it an integral part of the way things work. I use GPG sigs in my mail and encrypt everything to friends who are likewise willing to adopt it and even them that don't get to look at my ten line key at the bottom of every message. Having the additional prompt to enter a passphrase before hitting the "send" button has prompted me to several revisions that I did not regret. My home space is encrypted: usr. var. swap - all of it. Politically, encryption should become a part of all our lives as fundamental as air; it's a minimally invasive way of safeguarding our privacy and treating it as an exogenous element of our being only makes it that much easier for someone to remove it and lock it away.

Loopbacks are handy for CDs as you can create a volume of exactly the right size to fit a CD and burn it when it gets full - this is how I manage my interval backups, in fact - but other than that dm crypt is much more maintainable.

If you really want to debate encryption and safe practices I'll be happy to, but I really was only asking about this from a RAID usage and error recovery perspective. And for that I thank you again for your response.

[The Blue Suit perspective](http://www.cio.com/archive/071501/et_revisit.html) 
[And the other guys...](http://www.kuro5hin.org/story/2002/5/8/114540/8364)

---

### Post by dataw0lf on 2005-07-26
[QUOTE=poptones]
 Politically, encryption should become a part of all our lives as fundamental as air; it's a minimally invasive way of safeguarding our privacy and treating it as an exogenous element of our being only makes it that much easier for someone to remove it and lock it away.
[/QUOTE]

Whew.  Hey, your tin foil hat is about to fall off!!! GRAB IT!

---

### Post by poptones on 2005-07-26
Oooh aren't you clever. You seem to be a "mastur" at something, but it ain't roasting.

Since when do they make trolls "moderators?"

welcome to my twit list, "mr moderator."

---

### Post by dataw0lf on 2005-07-26
Apparently 'humor' to 'lighten' a potentially 'lockable' thread is a 'trollish' symptom. See, 'I' can use 'quotes' too.  I'll let someone else deal with this, I'm too tired and not in the mood to destroy this guy again, in a 'debate' or 'anything' else.

---

### Post by LordHunter317 on 2005-07-26
> **poptones]"My problem?" The only "problem" I have pertaining to this discussion is two bad Maxtor drives and a resulting worspace that is so confined I'm hardly able to get any new work done until they return.[/quote]Yes, and your decision to encrypt everything still has bearing on that, because it makes it more difficult to move data around and will affect your array performance when you rebuild it.

Moreover, it sounds to me, though it's not total clear from what you've described, that having a large encrypted partition is going to make moving your data difficult.  Though it'd be eaiser to determine that if you'd say where your data is now, and how much needs to be moved to the array.

>  and, frankly, I find your advice **terrible** for a variety of reasons and anyone who really knows about data security is much more likely to agree with my approach than yours.Elaborate, then.  And oh, you should call the NSA and tell them to encrypt all their classified data, now then, I guess.

>  You **cannot** have meaningful security if you only encrypt "packets" of data -Utter and total rubbish.  Most data isn't encrypted.  We encypt only what we need and only as much data as is necessary to encrypt.  Encryption is complicated and expensive.  

> so long as security is something that exists "over there" it's simply far too easy to have that trail of data leak - to a swap space or a temp file or even to a .conf file where some programs store their own MRUs for your convenience.That's just as true using dm-crypt.  You have to trust the applications you're using.  dm-crypt doesn't protect the data once a program gets it's hands on it.

> Having "this and that" encrypted forces you to always have to think "ok is this data supposed to be encrypted or isn't it?"And isn't that what I suggested?

> Encryption should not be an "option," viewed as a technology only for "special things."Yes, it should, because most data isn't important enough to require it.

Your line of reasoning is simply silly:  The government should classify all data TS/SCI then (meaning it never leaves the room it's created in) obviously, because keeping only some data secret isn't an option.

It's just not a workable solution for most applications.

Moreover, the cost of being able to encrypt data and retain performance is much higher, generally making it inacessible.  Even you have that problem: you have to have an unecrypted disk stripe in order to retain enough performance to edit your videos.

> It's far *easier* to use once you make it an integral part of the way things work.Nonsense again.


> Having the additional prompt to enter a passphrase before hitting the "send" button has prompted me to several revisions that I did not regret.Wonderful.  Perhaps you should learn to revise everything before you send it out?  This benefit is ancillary at best and useless at worse.  It's certainly not a justifable reason to encrypt everything you send, or even use GPG for most e-mails.

[quote]Politically, encryption should become a part of all our lives as fundamental as air said:**
> No, it shouldn't.  The cost is too high for the benfit in most cases.

[quote] it's a minimally invasive way of safeguarding our privacyIt's not.  It's very invasive.  It denies me easy access to my data.  And for most of my data, I really don't care if someone else gets it.  Hell, I give most of my data away for free *cough*.

And that precious bit of data that I don't want people to have, beyond those that need it?  Yeah, it's encrypte,d or stored in some other safe manner.  But that's essentially my credit card numbers, a few passwords, and that's it.  
Some people might have some private documents to go with that.  But that's still a tiny fraction of most people's data.

What do I gain by encrypting my music?  What do I gain by encrypting my movies?  This is the problem: you can't show any actual gain.  The data isn't more secure: you likely send over the network using unsecure protocols or give it to anyone who asks.  Convience?  Inarguably less convient for everyone.  Makes encrypted other data easier?  No, it doesn't.  So I see all negatives, and zero positives.

Hrm.  Guess I won't be encrypting most of my data anytime soon.

---

