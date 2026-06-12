---
title: "Improve installer to offer hard disk encryption"
date: 2007-10-21
forum: Ubuntu Brainstorm
---

### Post by schallstrom on 2007-10-21
I think it  would be great, if the default installer would offer the possibility to encrypt the file systems. The Debian installer already includes this option, so it shouldn't be too difficult to include the feature into the Ubuntu LiveCD installer, so non-geek-users could benefit from it.

---

### Post by AlexenderReez on 2007-10-21
it is already exist in gutsy...but only command line installer...

[http://news.softpedia.com/news/Encrypted-Ubuntu-7-10-68383.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-7-10-68383.shtml)

---

### Post by schallstrom on 2007-10-21
> **AlexenderReez said:**
> it is already exist in gutsy...but only command line installer...

[http://news.softpedia.com/news/Encrypted-Ubuntu-7-10-68383.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-7-10-68383.shtml)

I know that it's already possible. I wrote that the feature exists in the Debian installer. So you could just use the "Alternate Install" CD of Ubuntu, which uses the Debian Installer, to encrypt the file systems. But that's what my posting is all about: I think it would be cool, to make the feature available for the everyday-user through the LiveCD installer, cause a non-geek-user will not use the alternate install CD.

---

### Post by High Roller on 2007-10-21
> **schallstrom said:**
> I know that it's already possible. I wrote that the feature exists in the Debian installer. So you could just use the "Alternate Install" CD of Ubuntu, which uses the Debian Installer, to encrypt the file systems. But that's what my posting is all about: I think it would be cool, to make the feature available for the everyday-user through the LiveCD installer, cause a non-geek-user will not use the alternate install CD.

I'm not so sure that Ubuntu devs would be willing to make the investment into the partition manager that is offered on the LiveCD.  If for some reason the Alternate installer was to be phased out I would agree that the ability to encrypt on install be maintained in the LiveCD.  But most people (in my mind anyways) that would encrypt their drive would likely be using the Alternate installer to begin with.

If this feature was to be implemented I would hope it was tucked away nicely in an "Advanced Options" section and provided some sort of a failsafe "boot disk creator" so if a user's MBR or /boot was borked they'd have something to roll back on and at least get a command line.

---

### Post by schallstrom on 2007-10-22
> **High Roller said:**
> I'm not so sure that Ubuntu devs would be willing to make the investment into the partition manager that is offered on the LiveCD.  If for some reason the Alternate installer was to be phased out I would agree that the ability to encrypt on install be maintained in the LiveCD.  But most people (in my mind anyways) that would encrypt their drive would likely be using the Alternate installer to begin with.


I think it would be good to give the average user an easy way to greatly enhance their privacy.
This is the big problem with email encryption: GnuPG is a great system from the technical point of view, but it is used almost exclusively by pretty advanced users, cause it's just too hard to use for the average user. So 99% of all email traffic is still plain text.
OTR messaging is a great step into making private instant messaging available for the ordinary user.
And isn't that what Ubuntu is all about: Making the great, sophisticated open source software available to the average computer user, so they can benefit from it and not only the geek elite and IT professionals?
Easy file system encryption would be a big benefit for the the privacy of the average user.

---

### Post by drf_av on 2007-10-22
+1. Encryption option should be given alsoto Live CD users. I mean, a person with no experience with Linux could still have the need to have his data encrypted.

---

### Post by Xbehave on 2007-10-22
adding as an unsupported option is fairly easy.
currently using the liveCD you can create an encrypted partition on the installer picks it up, the only change that would be needed would be to detect that its being installed to an encryptedrive and run though the scripts that the alternate CD uses to install to an encrypted partition

---

### Post by High Roller on 2007-10-22
> **schallstrom said:**
> I think it would be good to give the average user an easy way to greatly enhance their privacy.
This is the big problem with email encryption: GnuPG is a great system from the technical point of view, but it is used almost exclusively by pretty advanced users, cause it's just too hard to use for the average user. So 99% of all email traffic is still plain text.
OTR messaging is a great step into making private instant messaging available for the ordinary user.
And isn't that what Ubuntu is all about: Making the great, sophisticated open source software available to the average computer user, so they can benefit from it and not only the geek elite and IT professionals?
Easy file system encryption would be a big benefit for the the privacy of the average user.

I agree, it should be available.  The only thing I see being a problem is making sure the "average user" is made aware of the inherent risks of encrypting their machine.  It might make it harder for people to help them out if their drive is encrypted and something breaks.  Maybe a big warning screen stating suggested dos and don'ts?  Either way, it should be off the beaten path so that people don't somehow accidentally choose this option without knowing what *could* happen.

---

### Post by schallstrom on 2007-10-23
> **High Roller said:**
> I agree, it should be available.  The only thing I see being a problem is making sure the "average user" is made aware of the inherent risks of encrypting their machine.  It might make it harder for people to help them out if their drive is encrypted and something breaks.  Maybe a big warning screen stating suggested dos and don'ts?  Either way, it should be off the beaten path so that people don't somehow accidentally choose this option without knowing what *could* happen.

You're right. There should be a warning. Maybe it would also be a good idea that the installer just encrypts the users home directory instead of creating a boot partition and encrypting everything else.

---

### Post by High Roller on 2007-10-23
> **schallstrom said:**
> You're right. There should be a warning. Maybe it would also be a good idea that the installer just encrypts the users home directory instead of creating a boot partition and encrypting everything else.

If the user intends to encrypt only their /home directory then there is no need to have encryption available in the installer.  The major reason why encryption is available through the installer is to overcome the difficult task of encrypting the entire machine.  There are some windows encryption applications that will encrypt your entire machine while it is running, but so far I've not found any easy "guided" methods for Linux.  If the option to encrypt at install were to be implemented in the LiveCD it might be good to have an option just to encrypt /home and then a separate one to encrypt everything under LVM as the Alternate install does (without /boot of course).

---

### Post by foerdi on 2007-11-17
I know there is a blueprint for hardy for ubiquity-integrated encryption... The encryption from gutsy alternate install is nice. 

Encryption must be default in my opinion

Additionally, when you look for a seperate /home partition (there is a blueprint somewhere with this), this must be encrypted, too.

And Swap, too.

And all the keys stored in root, like a keyring.

---

### Post by 23meg on 2007-11-17
Merged.

---

### Post by cferthorney on 2008-04-05
+1
I would like to see this.  Installing off the alternatives CD is all well and good - but I am a sysad for a large number of machines - most of which the people would want to see a visual install where they could see the thing working.  If I could install an encrypted HDD from the live CD I could show my users everything working prior to giving them their shiny new ubuntu laptop.

---

