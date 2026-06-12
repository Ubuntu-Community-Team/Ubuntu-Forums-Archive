---
title: "Online Backup Services"
date: 2011-12-30
forum: The Cafe
---

### Post by lile001 on 2011-12-30
I am trying to pick out an online backup service.  My standards are: up to 100 GB of storage, price $3 - $10 per month, robust servers, works easily with Linux.  I don't care if it is a nuts-and-bolts rsync type or proprietary software type of interface, although rsync is "good enough" for me.  I don't care about file syncing across computers (I use Ubuntu One for that, but this thread is about offsite backup in case of disaster)  Cost isn't the only consideration - I'd pay more for a more robust solution.  

I'd like a site that is "robust" - i.e. fault tolerant, so my stuff doesn't dissappear when their stuff loses a computer/drive/utility grid/etc.

I'd like a reasonable level of security


 Here is a brief bit of research:

Ubuntu One   
  Cost for 100 GB:  20 GB $30/year  100 GB = $150/Yr
  Robust?   - Poor?  Ubuntu One Website does not address this AFAIK.  Wikipedia reports Ubuntu One is NOT stored on a peer-to-peer network.  
  Security - Medium.  Files are stored unencrypted
  Interface: Proprietary GUI 
  Around since: 2009

SpiderOak
    Cost for 100 GB: $100/Yr
    Robust:  Extremely. [ https://spideroak.com/engineering_matters#fault_tolerant]("https://spideroak.com/engineering_matters#fault_tolerant")
    Security - High  [https://spideroak.com/engineering_matters#true_privacy](https://spideroak.com/engineering_matters#true_privacy)
    Interface:  Proprietary GUI
    Around since:  2007

Dropbox
   Cost:  100GB: $240
   Robust: ?  Wikipedia lists "Partial" encryption - Can't find info on fault tolerance. 
        Presumed to be high since this is the leading brand? 
   Security - Some [concerns:]("http://www.techrepublic.com/blog/security/dropbox-convenient-absolutely-but-is-it-secure/5618") and [URL="http://paranoia.dubfire.net/2011/04/how-dropbox-sacrifices-user-privacy-for.html"]more concerns
[/URL]   Interface: Proprietary GUI
   Around since: 2008

Datastorageunit.com
   Cost: 100GB: $50/yr
   Robust: Apparently this is one server running RAID 50, possibly also a 
       one man show
   Security:  Depends on how you set up Rsync
   Interface:  Rsync (Nuts and Bolts)
   Around since:  ?  



Right now, Spideroak seems to be winning the price/value war, with high security and a medium price.  

Any other contenders you'd recommend?  Can you add any information in these five categories - Cost, Robustness, Security, Interface, Around since?

---

### Post by oldos2er on 2011-12-30
Moved to Community Cafe.

---

### Post by PhilGil on 2011-12-30
I haven't tried it yet, but the one that's intrigued me lately is CrashPlan ([http://www.crashplan.com/](http://www.crashplan.com/)). The backup client is free and you can back up to a local disk, network share or over the internet with a friend or relative. The paid plan is $60/year for unlimited storage.

Another consideration (particularly if you have a low-resource machine) is that Spider Oak and CrahPlan use Java for cross-platform development, so their clients are more resource-intensive than Ubuntu One or Dropbox.

A low-tech way of doing off-site backups (and the method I'm currently using) is to keep a portable hard drive at an off-site location and bring it on-site once a week to do an rsync backup. For added security, you can encrypt the portable drive (I use TrueCrypt).

---

### Post by cbowman57 on 2011-12-30
I just use the free 2GB from SpiderOak but if I were going to purchase storage I'd use them.

Their software is solid, easy to use & they keep it up to date.

Might be a little resource intensive but I doubt you'll notice on most modern computers.

---

### Post by inobe on 2011-12-30
i think online backup is madness.

---

### Post by PhilGil on 2011-12-30
> **inobe said:**
> i think online backup is madness.
How so?

---

### Post by inobe on 2011-12-30
there are way too many backup solutions over a lan that are simply simple.

i understand if it's someone with a chrome book or smart phone, but then someones gonna think micro sd, external hd, printer.....\

it's madness to trust anyone but yourself with such valuable data.

this thread reminds me of spam, sell me online storage...

---

### Post by PhilGil on 2011-12-30
@[inobe]("http://ubuntuforums.org/member.php?u=706098")

For on-site backups, a USB drive or LAN-to-server is sufficient, and everyone should be doing that.

What does the average user do about off-site backups, though? They can hand-carry a hard drive to and from off-site storage, they can set up their own backup system using something like SSL or FTP to an offsite server, or they can use one of the internet backup services.

I know my limitations and I'm not a computer security expert. Different backup services use different security models, and you can also encrypt your data before backing up. I figure the guys that are in the online backup business are going to do a better job on security than me. And I feel the risk of using online backup is less than the risk of losing all my data in a fire, flood or earthquake.

People pay monthly fees for all kinds of stuff. Online backup seems like a reasonable expense to me. Oh, and I don't work for an online backup service :)

---

### Post by inobe on 2011-12-30
not being sarcastic or rude, what's the cost of a 32gb micro sd card?

this tiny little card can go in a wallet, under skin if folks are that paranoid!

now imagine 20/ 30 of those little sd cards, keep them in some little box, in some safety deposit box, or in your house too, make duplicates :P   

your data if your isp goes down, your data at a much more efficient bandwidth, your data in your own hands.

---

### Post by PhilGil on 2011-12-30
How big is your backup set? Mine is over 200GB and I don't think that's all that unusual. The last thing I want to do is faff around with SD cards.

I do agree with you that on-site backup is easy. Just buy yourself a USB hard drive, install backintime (or another backup application) and you're good to go. Before the Thai floods 1TB drives were $60-$80, and they'll be inexpensive again soon.

Where I disagree is with off-site backups for disaster recovery. I can absolutely guarantee that (except for a handful of IT geeks like us), no one is going to keep an off-site backup set fresh if they have to hand-carry the media and do the backups manually. That's why I still think there's value in online backup, it's a set-and-forget service that requires little to no ongoing intervention from the end user.

It's true that it can take a considerable length of time to get your files back (especially if your ISP is down temporarily). You can, however, choose which files you'd like to restore first. And if you're recovering from a disaster you probably have bigger problems than worrying about how fast your MP3 collection is being restored.

---

### Post by aysiu on 2011-12-30
I don't get this whole "data in your hands" business, at least for my situation. My data isn't top secret. Its primary value to me is that it exists. I'd far prefer that a company I'm paying to keep backups of my things have my personal family photos than to lose those photos altogether, should a fire burn down our apartment (including our laptops and all our external hard drives), than to say "Well, at least the data was in my own hands."

I *do* keep local backups, too, but off-site backups are a must for me.

---

### Post by sammiev on 2011-12-30
I just use a 2 TB USB drive to hold my backups. :)

---

### Post by PhilGil on 2011-12-31
> **sammiev said:**
> I just use a 2 TB USB drive to hold my backups. :)
That's fine, but what if your house burns down? I's important to have a second backup set stored away from home.

---

### Post by inobe on 2011-12-31
> **PhilGil said:**
> How big is your backup set? Mine is over 200GB and I don't think that's all that unusual. The last thing I want to do is faff around with SD cards.



phil, sd cards were an exaggerated example of what i really meant.

you can put that 200+ gigs of data on a hard drive in minutes, no one never heard of e-sata, fill one up and stick it in the closet, or in a fire proof safe.

online backup useless with Tb drives laying around, imagine when a storm comes through and tares down those isp cables, what would you do then, hook up an external drive:P

---

### Post by sammiev on 2011-12-31
I guess we need a backup for the backup for the backup. :confused:

---

### Post by PhilGil on 2011-12-31
> **inobe said:**
> 
you can put that 200+ gigs of data on a hard drive in minutes, no one never heard of e-sata, fill one up and stick it in the closet, or in a fire proof safe.

online backup useless with Tb drives laying around, imagine when a storm comes through and tares down those isp cables, what would you do then, hook up an external drive
If you had read my original post in this thread, that's exactly how I do my backups: nightly to a usb HDD at my desk, and weekly to a USB drive I keep at my office.

I think we're going to have to agree to disagree about the value of online backup services, though. Obviously, it could take some time to get the backups back (particularly if there is infrastructure damage), but that's better than not having the backups at all. And, IMHO, that's what is likely to happen to most users if they have to do manual off-site backups.

---

### Post by PhilGil on 2011-12-31
> **sammiev said:**
> I guess we need a backup for the backup for the backup. :confused:
Yes, as silly as it sounds, you should always keep a backup of your backup stored in another location.

---

### Post by sammiev on 2011-12-31
> **PhilGil said:**
> Yes, as silly as it sounds, you should always keep a backup of your backup stored in another location.

Glad I have a life away from my computer then.

---

### Post by PhilGil on 2011-12-31
> **sammiev said:**
> Glad I have a life away from my computer then.
And this is exactly why online backup services are useful :) . Most users don't want to be bothered with off-site backups, so maybe making them as painless as possible will get more folks using them.

sammiev, maybe you don't have anything on your computer that can't be easily replaced, but I'd be pretty bummed about losing 10 years of family photos and all my financial records.

---

### Post by inobe on 2011-12-31
> **sammiev said:**
> I guess we need a backup for the backup for the backup. :confused:

it would be a backup of a backup of a backed up backup:P

---

### Post by BrokenKingpin on 2011-12-31
I use SpiderOak mainly because the application does not rely on Nautilus or any Gnome crap and has a nice standalone application that works great with any WM/DE/OS.

---

### Post by inobe on 2011-12-31
tomorrow a wind advisory will be in affect all day, wind gusts of 60mph.

we had 40mph gusts and the entire region lost internet for days maybe spideroak will lose their internet:P

---

### Post by sammiev on 2011-12-31
> **inobe said:**
> tomorrow a wind advisory will be in affect all day, wind gusts of 60mph.

we had 40mph gusts and the entire region lost internet for days maybe spideroak will lose their internet:P

Hope you make a backup of your backup of your backup then. :biggrin:

---

