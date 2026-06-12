---
title: "secure linux laptop for business"
date: 2011-02-02
forum: Security
---

### Post by jlparsons on 2011-02-02
Hi folks, I need to set myself up with a laptop which must be reliable and also secure enough to hold clients' financial data.  I would be the only user but the laptop would come out and about with me so there's always the remote possibility that it might get lost or stolen.  I'm reasonably familiar with ubuntu and have setup and used ubuntu, xubuntu, lubuntu and kubuntu on a few computers over the last five years or so, but although I'm competent I'm no pro.

I'm considering going with either a lenovo or a dell as I believe these machines are well reputed in terms of linux compatibility?   I'm thinking I'll buy a small SSD drive for better shock protection and battery life and then install a fully encrypted k/ubuntu64 10.04LTS system from the alternate CD.  I'm hoping the speed of the SSD might counter some of the system overhead from running an encrypted fs.

So... anyone see any flaws in this plan?  Are there any issues with encrypted file systems and SSD drives?  Would it be reasonable to consider this adequate security for financial data?

Is there much or a difference when it comes to stability and security between kubuntu and ubuntu?

Lastly, if I have 4gb of ram, will only ever use openoffice/firefox/chrome together, have never managed to fill my system ram and have no need to hibernate the system (i either suspend or shutdown) is there any reason to have a swap partition and hence worry about encrypting it?

Many thanks folks,

James

---

### Post by jbrice on 2011-02-02
Hi James,
I use a Dell 1525 with a fully encrypted hard disk - set up with the alternate CD. I'll let others comment on security and the suitability of an SSD with encryption, but I see no noticeable speed loss with the encrypted HD. It's fine even doing things like playing videos - where the video card is the limiting factor, not getting the encrypted video stream off of the disk.

James B.

---

### Post by jlparsons on 2011-02-02
Thanks mate.  Any issues getting anything to work on the 1525?  Suspend/wireless/hotkeys etc?

---

### Post by olepi on 2011-02-02
I have a fully encrypted ubuntu 10.10 install and have found there is little impact to overall speed. I can't comment on the SSD though. I would mention that if you're keeping important information on your laptop, it is not protected by whole disk encryption if you suspend it.  You should always either have it on or off.

---

### Post by jlparsons on 2011-02-02
Interesting... would someone still be able to get in if I set the system to ask for a password on resume?

If set to hibernate instead to an encrypted swap partition would the same apply?

---

### Post by cariboo on 2011-02-02
You're still logged in when using sleep or hibernate, so you partition is unencrypted.

---

### Post by Kirboosy on 2011-02-02
Encrypting the home directory is a good move but I think if you made a Truecrypt container as well you could store all the sensitive files in it. Then it would still be locked whenever the rest of your computer is unlocked. Only time it would be unlocked is when you are accessing the files and have it mounted in Truecrypt. :)

Lenovo is a good business laptop. Its not flashy and it works well. I have a Dell Duo which works well but its flashy and not very business looking.

---

### Post by KegHead on 2011-02-02
Hi!

I use truecrypt and USB drives for sensitive info.

I always have the USB drives secure w/me.

KegHead

---

### Post by jbrice on 2011-02-02
> **jlparsons said:**
> Thanks mate.  Any issues getting anything to work on the 1525?  Suspend/wireless/hotkeys etc?

Yes, it (Lucid a.k.a. V10.4 that is)works well - wireless re-connects in moments, suspend and hibernate work fine also. 

However, bear in mind that after hibernate you will need to use both the encryption password and the login password, just as if you were booting up. Maybe a good thing tho. as it means your hibernated session is securely hidden away by the hard disk encryption.

---

### Post by jlparsons on 2011-02-02
> **jbrice said:**
> However, bear in mind that after hibernate you will need to use both the encryption password and the login password, just as if you were booting up. Maybe a good thing tho. as it means your hibernated session is securely hidden away by the hard disk encryption.

Sounds like a very good thing to me!  Will this happen by default when hibernating with a standard encrypted disk installation from the alternate CD?

---

### Post by jbrice on 2011-02-02
> **jlparsons said:**
> Sounds like a very good thing to me!  Will this happen by default when hibernating with a standard encrypted disk installation from the alternate CD?

I'm using the standard encrypted disk installation from the alternate CD, which includes the swap and the home/system virtual partitions on the encrypted partition. 

Since - as I understand it - the hibernated session is dumped onto the swap partition so:
a) you will need a suitably sized swap file (>RAM size) to enable hibernation, even if you have more than enough RAM for your applications.
b) I would imagine that the only way anyone can hack into your system is by breaking the disk encryption, unless they have the technology to sniff the ghost traces of your session and data from the system RAM.

---

### Post by DodgeV83 on 2011-02-02
I have a Dell and I always turn on as many BIOS passwords as I can.  One to boot, one to allow access to the harddrive and one to enter the BIOS and make changes.

I then lock the ability to boot via USB or CD in the BIOS, so they can't use a LiveCD to analyze things without opening up the computer and finding then removing the CMOS battery.

---

### Post by jlparsons on 2011-02-02
> **DodgeV83 said:**
> I have a Dell and I always turn on as many BIOS passwords as I can.  One to boot, one to allow access to the harddrive and one to enter the BIOS and make changes.

I then lock the ability to boot via USB or CD in the BIOS, so they can't use a LiveCD to analyze things without opening up the computer and finding then removing the CMOS battery.

Good suggestions, thanks.  I suppose they could flash/replace the bios to get around this?  Or does the BIOS password this option too?  Getting to mega-paranoid mode at this stage however...

---

### Post by tgm4883 on 2011-02-02
> **DodgeV83 said:**
> I have a Dell and I always turn on as many BIOS passwords as I can.  One to boot, one to allow access to the harddrive and one to enter the BIOS and make changes.

I then lock the ability to boot via USB or CD in the BIOS, so they can't use a LiveCD to analyze things without opening up the computer and finding then removing the CMOS battery.

At that point, if I wanted to look at your data I'd just slave the drive in another system.

+1 for full disk encryption

---

### Post by jlparsons on 2011-02-02
> **tgm4883 said:**
> At that point, if I wanted to look at your data I'd just slave the drive in another system.

+1 for full disk encryption

Perhaps the solution is all the above plus an encryption key based on a function of the standard user key plus multiple system specific data ie component serials?  Effect might be that to take it out of its machine is to effectively increase the bit depth of the encryption used?  Or am I just being daft now? ;)

Anyway... anyone know anything about encryption/security with SSDs?  I'm assuming a fully encrypted filesystem is going to work fine on one of those...?

---

### Post by DodgeV83 on 2011-02-02
> **tgm4883 said:**
> At that point, if I wanted to look at your data I'd just slave the drive in another system.

+1 for full disk encryption

Definitely, you should still encrypt, but don't make it easy on them :)

Make it so they absolutely need a screwdriver to get in your system, and even then they wouldn't be able to decrypt it.

---

### Post by tgm4883 on 2011-02-02
> **DodgeV83 said:**
> Definitely, you should still encrypt, but don't make it easy on them :)

Make it so they absolutely need a screwdriver to get in your system, and even then they wouldn't be able to decrypt it.

Sorry, but that is laughable. Maybe if everyone didn't have a drawer full of screwdrivers or if you had to have a license to own one, but if you think that is going to slow anyone down you are kidding yourself.

The idea behind any type of security we talk about for this scenario is to slow down a thief from stealing your data. In the case of using encryption (good encryption that is) you have made it take so long to actually crack the encryption that it is nearly impossible to do so. (eg. thousands of years.) Adding measures that are easy to bypass (BIOS password, locking down boot order, etc) doesn't really add any real benefit on an encrypted system. At best, you have added 10 minutes to the time it takes to get, and now every time you boot your system you have to enter multiple passwords. Sure you feel like your date is safer, but it simply doesn't pass the logic test. 

Locking down boot order, bios, etc is more for people that don't want others installing another OS on their system, reformatting their system, etc. It isn't to prevent people from stealing your data.

---

### Post by DodgeV83 on 2011-02-03
> **tgm4883 said:**
> Sorry, but that is laughable. Maybe if everyone didn't have a drawer full of screwdrivers or if you had to have a license to own one, but if you think that is going to slow anyone down you are kidding yourself.

The idea behind any type of security we talk about for this scenario is to slow down a thief from stealing your data. In the case of using encryption (good encryption that is) you have made it take so long to actually crack the encryption that it is nearly impossible to do so. (eg. thousands of years.) Adding measures that are easy to bypass (BIOS password, locking down boot order, etc) doesn't really add any real benefit on an encrypted system. At best, you have added 10 minutes to the time it takes to get, and now every time you boot your system you have to enter multiple passwords. Sure you feel like your date is safer, but it simply doesn't pass the logic test. 

Locking down boot order, bios, etc is more for people that don't want others installing another OS on their system, reformatting their system, etc. It isn't to prevent people from stealing your data.

I can come up with a dozen scenarios where adding a significant amount of time, along with increasing both the tools and the knowledge necessary to accomplish the task, can completely negate a thief's attempt to steal my data.  Sure it's paranoia time, but don't say it gives 0 benefit.

---

### Post by tgm4883 on 2011-02-03
> **DodgeV83 said:**
> I can come up with a dozen scenarios where adding a significant amount of time, along with increasing both the tools and the knowledge necessary to accomplish the task, can completely negate a thief's attempt to steal my data.  Sure it's paranoia time, but don't say it gives 0 benefit.

/me waits for 12 scenarios tailored to meet your criteria

---

### Post by HermanAB on 2011-02-03
BTW, Dell, Lenovo, HP and Acer laptops are generally OK with Linux, while Toshiba and Sony are best avoided.

---

### Post by jlparsons on 2011-02-03
> **HermanAB said:**
> BTW, Dell, Lenovo, HP and Acer laptops are generally OK with Linux, while Toshiba and Sony are best avoided.

Thanks for that.  Probably add samsung to the "maybe" pile in my experience too.

---

### Post by Kirboosy on 2011-02-03
Probably the best laptop if you are concerned about compatibility is [System 76]("http://www.system76.com/")

They are a bit pricey but they make good computers and its designed for Ubuntu :D

Here is a list of [Certified Hardware]("http://www.ubuntu.com/certification/")


As for the other guys discussing security...
> I can come up with a dozen scenarios where adding a significant amount of time, along with increasing both the tools and the knowledge necessary to accomplish the task, can completely negate a thief's attempt to steal my data. Sure it's paranoia time, but don't say it gives 0 benefitI'm just gonna say this. (It used to be my signature.) Once a hacker has physical access to a computer, any security measures are useless. 

Meaning your system will be compromised one way or another. Sure your Data might never be leaked but the data could still be destroyed

If you are really worried about security of data. Buy 2 or 3 external Hard Drives and encrypt them fully with Truecrypt. Then every day swap out the externals and store your backups to it. The one thats not in use, put it in a safe or take it offsite. That way you have redundant data (give or take a day)

If the office burns down if you have a fireproof safe all of your data will be safe. I recommend 3 so you can have 2 on site and one off site..

---

### Post by spynappels on 2011-02-03
> **HermanAB said:**
> BTW, Dell, Lenovo, HP and Acer laptops are generally OK with Linux, while Toshiba and Sony are best avoided.

That's funny, both Toshiba Portege models I've had work fine with Ubuntu, including my current M750 Tablet PC. Which have you had problems with?

---

### Post by movieman on 2011-02-05
> **spynappels said:**
> That's funny, both Toshiba Portege models I've had work fine with Ubuntu, including my current M750 Tablet PC.

Yeah, I'm using a Toshiba Qosmio here with no real problems; it used to dislike rebooting into Windows (would hang after shutting down Ubuntu) but that appears to be a BIOS bug that they seem to have fixed.

---

### Post by jlparsons on 2011-03-06
Update - have bought a Lenovo T410, installed ubuntu 10.10 via alternate CD with full encryption.  Everything works out of the box, no additional tweaks necessary, no proprietary drivers.  Have installed mint-x theme for eye-candy, looks very professional.  

Full encryption doesn't appear to have any noticeable performance penalty (i installed without encryption first to check compatibility) but the HD is a bit slow either way so I may upgrade to an SSD when they come down in price a bit.  

So - all good!  Many thanks for everyone's contributions.

---

