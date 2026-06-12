---
title: "Resetting a Forgotten Password - I Have a Problem with This"
date: 2012-02-25
forum: Security
---

### Post by lefo on 2012-02-25
I was reading this article:

[http://www.noobslab.com/2012/02/reset-your-forgotten-password-quickly.html](http://www.noobslab.com/2012/02/reset-your-forgotten-password-quickly.html)

This makes Linux seem totally unsecure. I switched from Windows to Linux with the impression that Linux was a LOT more secure than Windows.

With that in mind, what would you need to do to prevent this from happening? I do not want this option available on my laptop.

I'm relatively new to Linux, but not "that" new.  So, please understand that while I'm a relative "noob", I'm a noob that really wants to learn.

Thanks!!! :)

---

### Post by CharlesA on 2012-02-25
physical access == root access. That is how it is no matter what OS you run.

---

### Post by lefo on 2012-02-26
Thanks. I'll read up. I see there's a lot of information. I just wish that there was a way to keep the system locked down to one user if that's what's needed. Maybe I'll find it in this info.

Thanks. This is really interesting stuff.

---

### Post by secret resistor on 2012-02-26
If you want protection against somebody with physical access reading your data, use encryption with a strong password. To protect against somebody destroying your data, back up anything important to a remote location (preferably after encrypting it first).

---

### Post by lefo on 2012-02-26
> **secret resistor said:**
> If you want protection against somebody with physical access reading your data, use encryption with a strong password. To protect against somebody destroying your data, back up anything important to a remote location (preferably after encrypting it first).

Is there a way to keep anyone from changing the Password from physical access? If you can encrypt your data, that's great. But, it's going to be useless if someone changes your password...sort of. I mean, yes...I could go back in and do the same thing to regain control, but wouldn't it be great if you could control physical access as well?  I can see so many ways to negate that statement, but I'm hoping my intent is read into it.

---

### Post by CharlesA on 2012-02-26
They would need to know the passphrase to gain access to the encrypted data.

In any case, if physical access is going to be a problem, you can always lock the machine up, which isn't that ideal if it's a desktop or laptop.

---

### Post by Jonathan L on 2012-02-26
Hi Lefo

If controlling physical access is a problem, you might also consider using a server in the cloud.  (Cloud operators have thick walls, barbed wire, and sometimes men with guns.)  Then you don't have to keep anything of value on your own computer.

Of course you're pretty much stuffed if you forget your passwords, and so you'd need to make sure you don't.

Just a thought.

Kind regards,
Jonathan.

---

### Post by lefo on 2012-02-26
Thanks, everyone. I appreciate the help. We'll call this one, "SOLVED".

---

### Post by oldos2er on 2012-02-26
> **lefo said:**
> Thanks, everyone. I appreciate the help. We'll call this one, "SOLVED".

Please use the Thread Tools menu at the top to mark it as 'Solved.'

---

### Post by lefo on 2012-02-26
> **oldos2er said:**
> Please use the Thread Tools menu at the top to mark it as 'Solved.'

Oops! Missed a step.  Thanks.

---

### Post by D&#322;ugi Chudy Lolo on 2012-12-16
But it is not SOLVED.

You said:

> **lefo said:**
> I was reading this article:

[http://www.noobslab.com/2012/02/reset-your-forgotten-password-quickly.html](http://www.noobslab.com/2012/02/reset-your-forgotten-password-quickly.html)

This makes Linux seem totally unsecure. [...]

With that in mind, what would you need to do to prevent this from happening? I do not want this option available on my laptop.



I haven't tried this option to change the password, but it seems that the solution is wrong. You can't change root's password without root's password. Am I wrong?
In comments of above article there are a lot of users complaining that they can't change password. So?

---

### Post by snowpine on 2012-12-16
> **D&#322 said:**
> But it is not SOLVED.

You said:



I haven't tried this option to change the password, but it seems that the solution is wrong. You can't change root's password without root's password. Am I wrong?
In comments of above article there are a lot of users complaining that they can't change password. So?

Welcome to the forums!

Ubuntu does not use a "root password" and I encourage you to read this FAQ: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

And here is a good tutorial how to reset a forgotten password: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Possibly the readers in the comments section of the link have not read the helpful links above? If they want to post here on ubuntuforums, we will help them. :)

---

### Post by D&#322;ugi Chudy Lolo on 2012-12-16
And this is it.
Thx ;)

---

### Post by owenontheforums on 2013-04-02
Im having problems on my linux machine. Today one of my dads businessmen brought over 2 computers, 1 linux 1 windows xp, I tryed running the linux machine and it had a password. Im trying to bypass the password but it doesnt work. Im using a XP machine at the moment until I can bypass the password. Any suggestions?

---

### Post by Cheesemill on 2013-04-02
> **owenontheforums said:**
> Im having problems on my linux machine. Today one of my dads businessmen brought over 2 computers, 1 linux 1 windows xp, I tryed running the linux machine and it had a password. Im trying to bypass the password but it doesnt work. Im using a XP machine at the moment until I can bypass the password. Any suggestions?

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by CharlesA on 2013-04-02
> **owenontheforums said:**
> Im having problems on my linux machine. Today one of my dads businessmen brought over 2 computers, 1 linux 1 windows xp, I tryed running the linux machine and it had a password. Im trying to bypass the password but it doesnt work. Im using a XP machine at the moment until I can bypass the password. Any suggestions?

Why not just ask them for the password? Assuming they own the computers, of course. :)

---

### Post by KaosuX on 2013-04-05
> **CharlesA said:**
> physical access == root access. That is how it is no matter what OS you run.

Your comment is not entirely true. While physical attacks are difficult to combat, it is not an impossible feat. I believe most people still repeat "physical = root" because it was a very popular notion a decade ago when security became "mainstream" because of our global dependence on technology. Here are some common methods a person could use to harden their system(s) against an attacker with physical access:

1) Set a supervisor password in your BIOS and remove the option to boot from removable media (flash drive, CD/DVD, etc). This in conjunction with correct OS-level access restrictions would help prevent most (common) physical attacks. I mean, if you let them run as a privileged user then they could easily circumvent this by flashing the firmware, brute forcing the password, etc. So, in a real-world situation it would be possible for an attacker to take advantage of an exploit to gain access to a super-user account and perform such actions, but this would be unlikely if you're properly maintaining your system (and the fact that if they already have super-user rights through an exploit then they would be stupid to waste their time trying to modify your boot order). You could also force users to need to know a password set within the BIOS to even boot at all if you were really worried (assuming your BIOS supports it).

2) Encrypt your entire hard drive using the Advanced Encryption Standard. Several distributions make this easy by offering to perform the task during an installation and the performance hit is a non-issue on semi-modern hardware, so there is no real reason not to utilize a technology that is specifically designed to protect your sensitive data against an attacker with direct access to it. Just be cautious when using full-disk encryption with an SSD, flash drive, etc. because of the built-in wear leveling on such devices.  In a practical sense, I am sure your data would remain safe. However, when faced against a skilled forensic examiner, you might leak a lot more information than one would realize. There is a lot more to this whole sub-topic, but I won't go into it. Also, I wouldn't opt-in to use other popular ciphers (Serpent, etc) because they are not as well tested. 

3) Use DDR3 memory. Cold Boot Attacks are found to only be effective on older types of memory that stored voltage over longer periods of time. DDR3 should only store enough voltage for a few seconds of data retention after the machine has been powered down (clean or unclean). I won't go into counter-measures here if you're running older memory types just because I seriously doubt you would encounter such an attack. 

4) Keep your boot loader on removable media and never let it out of your sight. /boot should be the only unencrypted part of your hard disk, and you can further reduce your risk of physical attack by storing it on removable media. If you choose to store this unencrypted on your disk, then don't be surprised when you boot into a hostile environment.

5) Utilize smart cards and/or fingerprint scanners. My personal favorite is the FS88 fingerprint scanner. This can be used as a strong two-way authentication system (Something you have and something you know). Also, on an unrelated note, look into learning more about Pluggable Authentication Modules. You would be amazed at the neat things you can achieve.

6) Use common sense. Keep your machine properly updated, store off-site logs in case you ever need to deal with a disaster response and recovery scenario, heavily restrict access to guest users (far more than the guest account currently does. try to only give them access to what they need for their specific tasks and nothing else) and follow all of the other basic security principals.

There you go. Six easy steps to dramatically increase your security, even if you're dealing with someone that has physical access to the machine. If you perform all six steps correctly, then it would be very unlikely that anyone you know would be able to circumvent your restrictions. Even if they could, it would be a pain and probably not something they would invest their time into.

From now on, please don't automatically assume that physical access is the same as root access. As you can see, that simply isn't the case these days on a properly configured machine. I mean, it is more than possible to compromise a machine with physical access even if they perform all six steps, but it would not be a trivial task nor something just any attacker could achieve.

---

### Post by Cheesemill on 2013-04-05
> **KaosuX said:**
> 1) Set a supervisor password in your BIOS and remove the option to boot from removable media (flash drive, CD/DVD, etc).

It's a trivial task to bypass BIOS password protection, you just need to reset the BIOS by using the motherboard jumper or removing the CMOS battery.
Either that or you just remove the drive altogether and use it in a different machine.

I think people have already mentioned that physical access = root access ***unless*** you use encryption, which is still the case.

---

### Post by KaosuX on 2013-04-05
> **Cheesemill said:**
> It's a trivial task to bypass BIOS password protection, you just need to reset the BIOS by using the motherboard jumper or removing the CMOS battery.
Either that or you just remove the drive altogether and use it in a different machine.

I think people have already mentioned that physical access = root access ***unless*** you use encryption, which is still the case.

This is true for older hardware. However, dual-BIOS chips are common when using modern hardware. One is suppose to remain "stock" so if something goes wrong with the primary chip (or settings) then the system can recover from it. However, most of them do mirror password settings so the old jumper/battery method no longer works on them. I am sure this might still be the case in a lot of situations, but the proper selection of hardware can fortify against such trivial attacks. Also, I am unsure if I failed to convey myself correctly, but I was meaning for people to take all 6 steps as a whole and not treat each individual step as a method of strong security within itself. A simple push of a button can clear your settings in an instant since that is now what newer motherboards use to replace old jumper settings, but your mileage will vary depending on the motherboard you're dealing with. That is not me trying to be argumentative, just something I have took note of when working out in the field.

Also, while I agree it would be trivial in most cases, it at the very least stops a clueless attacker from putting a LiveCD in the tray and using an automated tool to reset account passwords.

With anything security-related it is best to work in layers. That suggestion was just one layer that is the part of a whole. So, please treat it as such.

Thanks for the response, though.

---

### Post by CharlesA on 2013-04-05
> **KaosuX said:**
> 1) Set a supervisor password in your BIOS and remove the option to boot from removable media (flash drive, CD/DVD, etc). This in conjunction with correct OS-level access restrictions would help prevent most (common) physical attacks. I mean, if you let them run as a privileged user then they could easily circumvent this by flashing the firmware, brute forcing the password, etc. So, in a real-world situation it would be possible for an attacker to take advantage of an exploit to gain access to a super-user account and perform such actions, but this would be unlikely if you're properly maintaining your system (and the fact that if they already have super-user rights through an exploit then they would be stupid to waste their time trying to modify your boot order). You could also force users to need to know a password set within the BIOS to even boot at all if you were really worried (assuming your BIOS supports it).

As Cheesemill already covered, it is trivial to reset the BIOS to get around a boot password or bios password. Some systems don't let you do that, but most of the time I have only seen that type of security in business class laptops.

> **KaosuX said:**
> 2) Encrypt your entire hard drive using the Advanced Encryption Standard. Several distributions make this easy by offering to perform the task during an installation and the performance hit is a non-issue on semi-modern hardware, so there is no real reason not to utilize a technology that is specifically designed to protect your sensitive data against an attacker with direct access to it. Just be cautious when using full-disk encryption with an SSD, flash drive, etc. because of the built-in wear leveling on such devices.  In a practical sense, I am sure your data would remain safe. However, when faced against a skilled forensic examiner, you might leak a lot more information than one would realize. There is a lot more to this whole sub-topic, but I won't go into it. Also, I wouldn't opt-in to use other popular ciphers (Serpent, etc) because they are not as well tested. 

Sure, encryption is one method, but what happens if someone decides to attack your machine while it is powered on and the encryption key is in memory?

> **KaosuX said:**
> 3) Use DDR3 memory. Cold Boot Attacks are found to only be effective on older types of memory that stored voltage over longer periods of time. DDR3 should only store enough voltage for a few seconds of data retention after the machine has been powered down (clean or unclean). I won't go into counter-measures here if you're running older memory types just because I seriously doubt you would encounter such an attack. 

Are we talking home users or business users here? The price I work at is still running Pentium 4 machines with their epic DDR memory, but new technology is not really budgeted in. Other companies might be different, but from my experience if a piece of hardware works fine, there is no reason to replace it with something newer/more advanced.

> **KaosuX said:**
> 4) Keep your boot loader on removable media and never let it out of your sight. /boot should be the only unencrypted part of your hard disk, and you can further reduce your risk of physical attack by storing it on removable media. If you choose to store this unencrypted on your disk, then don't be surprised when you boot into a hostile environment.

Again, home user vs business user? Storing your boot loader on a removable media sounds like a good idea, but what if you misplace the disk or thumb drive? What about booting to a livecd and installing GRUB to the main drive?

> **KaosuX said:**
> 5) Utilize smart cards and/or fingerprint scanners. My personal favorite is the FS88 fingerprint scanner. This can be used as a strong two-way authentication system (Something you have and something you know). Also, on an unrelated note, look into learning more about Pluggable Authentication Modules. You would be amazed at the neat things you can achieve.

Home or business user again? I doubt a home user would be using a smartcard. They might have a fingerprint reader on a laptop or another device, but how well does it work with Linux?

> **KaosuX said:**
> 6) Use common sense. Keep your machine properly updated, store off-site logs in case you ever need to deal with a disaster response and recovery scenario, heavily restrict access to guest users (far more than the guest account currently does. try to only give them access to what they need for their specific tasks and nothing else) and follow all of the other basic security principals.

I'll assume you are talking about business users, judging from tip #3, #4, #5 and #6. Are you talking about workstation or server logs? I have never seen logs stored offsite. Backups (which probably contain logs) yes, but not logs by themselves. If you have everyone running as a standard user, use apparmour or selinux and limit what those standard users have access to, you should be fine.

I can only speak for myself, but when the place I work at hired a consultant, they made them a "normal" user with access to the tools they needed. I don't really see a reason to use the guest account unless the person is actually a guest (which is highly unlikely unless you have open wifi or something).

---

### Post by KaosuX on 2013-04-05
> **CharlesA said:**
> As Cheesemill already covered, it is trivial to reset the BIOS to get around a boot password or bios password. Some systems don't let you do that, but most of the time I have only seen that type of security in business class laptops.



Sure, encryption is one method, but what happens if someone decides to attack your machine while it is powered on and the encryption key is in memory?



Are we talking home users or business users here? The price I work at is still running Pentium 4 machines with their epic DDR memory, but new technology is not really budgeted in. Other companies might be different, but from my experience if a piece of hardware works fine, there is no reason to replace it with something newer/more advanced.



Again, home user vs business user? Storing your boot loader on a removable media sounds like a good idea, but what if you misplace the disk or thumb drive? What about booting to a livecd and installing GRUB to the main drive?



Home or business user again? I doubt a home user would be using a smartcard. They might have a fingerprint reader on a laptop or another device, but how well does it work with Linux?



I'll assume you are talking about business users, judging from tip #3, #4, #5 and #6. Are you talking about workstation or server logs? I have never seen logs stored offsite. Backups (which probably contain logs) yes, but not logs by themselves. If you have everyone running as a standard user, use apparmour or selinux and limit what those standard users have access to, you should be fine.

I can only speak for myself, but when the place I work at hired a consultant, they made them a "normal" user with access to the tools they needed. I don't really see a reason to use the guest account unless the person is actually a guest (which is highly unlikely unless you have open wifi or something).

1) A lot of newer consumer-level motherboards are actually made using the same materials and in the same factory as server/enterprise-level hardware. While they will differ in obvious areas, a lot of new consumer-level hardware is taking directly from stable enterprise-level design (Dual-BIOS chips, TPM, stronger security against trivial attacks like removing the battery or using a jumper/button to clear system settings). However, I am willing to concede and agree that this would indeed work in most normal conditions across several real-world situations. However, I can't stress enough (as I did in a previous post) that this is merely 1 of 6 steps. Individually they have obvious strengths/weaknesses, but together they can help make up for the others shortcomings to provide better overall physical security. If you really want to take each suggestion and only base them on their own merit and not within a layered implementation then I believe that is a slightly biased and flawed way of thinking. Anything in terms of security can be compromised on some level or in some time, and that is why defense-in-depth is the overall goal, not individual "solutions". Think of this step at the first line of defense, meant to stop clueless attackers (which is what most employees or friends/family will be, IMHO).

2) In suggestion six I specifically warned about leaving the machine powered on. Don't get me wrong, it is a viable concern, but one a user/enterprise could easily correct with proper usage policies in place. Also, what stops the end-user/enterprise from encrypting the whole disk and partitioning another part of the disk to store sensitive information that is also encrypted? Then the user/employee/whoever could simply decrypt/mount the partition when they need access to the data and encrypt/unmount the partition then they are finished. If you really wanted to argue just for the sake of argument, then nothing on this planet is truly secure and you could go down an infinite rabbit hole that is a never ending echo of what if's, theoretical possibilities, etc. These are steps increase physical security, not make you completely immune to all forms of attack. With anything, user habit and policy is the most important factor when paired with reasonably strong encryption.

3) I understand that a lot of offices across the globe use outdated hardware. However, how often do you expect someone to be able to perform a Cold Boot Attack in the required time frame? It isn't overly complex, and can certainly be done with commonly found (cheap or free) items/software, but it isn't something to really get worked up over. Offices with confidential data should already be utilizing strong physical security policies (security, CCTV, locked computer chests, etc) and was simply outside the scope of these suggestions and not directly related to the discussion, this is a huge reason why I didn't go into details regarding counter-measures, as most are unrelated. Also, I don't see a home user having to worry about this type of attack. Sure, it might be possible they would encounter a CBA, but it is also possible they could win the lottery twice - doesn't mean it will actually happen in their lifetime (and home users are more likely to be using newer hardware also).

4) Why would it matter if an attacker installed a boot loader on an encrypted drive? If you used this suggestion then you would not be booting from it, it would give you one heck of an obvious clue that someone was tampering with your system, would not give them access to the encrypted contents of the drive, etc. If anything, all it would do is give them away since you wouldn't even be booting from their malicious new boot loader to begin with. Also, not losing removable media is not all that hard. If you managed to lose it, then that is simply the price of security and why recent/secure backups are very important.

5) I don't specifically target enterprise or home users with my advice. You would be surprised how many home users do use smart cards and fingerprint scanners. Both are not very difficult to set up, are fairly inexpensive these days and offer increased security. For example, the FS88 fingerprint scanner can be bought for under $100 USD in a lot of locations. There are also a lot of decent smart card readers out there for under $100 USD also. To answer your other question, it isn't too difficult to set up the fingerprint scanners that come with laptops. Some might require you to use documented API to create the required modules/software to utilize the devices, but projects like fprint can help make such things possible for end-users with no programming experience. Heck, even in cases where you need to use the documented API, they almost always include an example that only needs slight modifications to meet most home user requirements.

6) That is what I was driving at. I meant to say that you shouldn't be using the guest account and instead use a standard user account that is heavily restricted to only the software/access they need to perform a specific role/task. My fault, though. I didn't really convey that point correctly. Also, I have seen many people/organizations store off-site logs. It can be really nice to have an off-site logserv. It makes centralizing live log analysis easier in addition to hindering an attackers ability to hide nefarious actions by simply removing the log entries. Running as a standard user with SELinux, etc. was (I thought) implied by: "I meant to say that you shouldn't be using the guest account and instead use a standard user account that is heavily restricted to only the software/access they need to perform a specific role/task", so I do agree with that overall sentiment.

Again, please take all of my suggestions as a whole and not individually. When they are all added together and properly implemented, do you really argue the overall physical security of your machine would not be **improved**?

---

### Post by CharlesA on 2013-04-05
Improved, yes, but you'll run into the whole convenience vs security thing again.

---

### Post by KaosuX on 2013-04-05
> **CharlesA said:**
> Improved, yes, but you'll run into the whole convenience vs security thing again.

That is not really the point, though. The point is simply having physical access to the machine does not guarantee you will have full access to it, at least not trivially like you suggested in the first post I responded to. If you wan to say "in most cases physical access == full access" then I can agree with that. However, you make it sound like in all cases an attacker is guaranteed to compromise the machine if they have physical access to it, and that is simply misinformation, because a user can fortify themselves against such an attack and likely have a high chance to succeed in preventing access to their data.

---

### Post by uRock on 2013-04-05
With a default installation, which most users have, physical access does mean full access. While encryption may slow access to data, a well versed cracker with a powerful system and the right software can crack the encryption key.

---

### Post by deadflowr on 2013-04-05
> **KaosuX said:**
> That is not really the point, though. The point is simply having physical access to the machine does not guarantee you will have full access to it, at least not trivially like you suggested in the first post I responded to. If you wan to say "in most cases physical access == full access" then I can agree with that. However, you make it sound like in all cases an attacker is guaranteed to compromise the machine if they have physical access to it, and that is simply misinformation, because a user can fortify themselves against such an attack and likely have a high chance to succeed in preventing access to their data.

Physical access might not be a guarantee to root access, it does break a major barrier.

---

### Post by KaosuX on 2013-04-05
> **uRock said:**
> With a default installation, which most users have, physical access does mean full access. While encryption may slow access to data, a well versed cracker with a powerful system and the right software can crack the encryption key.

We're not talking about a default installation, though. I was talking about ways people can fortify themselves against physical attacks. That would be like me making recommendations for securing a workstation with Internet access and you arguing that an unpatched machine is vulnerable. I have said time and time again that nothing is guaranteed in the realm of information security and that people are correct to assume that physical access will result in a full compromise in most cases, but not all cases. It is almost like people are arguing against ways to harden their physical security because it has been so ingrained into them for so long that it is impossible to protect yourself against a physical breach. This isn't 2003, people now have easy access to things like full-disk encryption using AES, newer motherboards that provide better security against physical attacks that were once exclusive to enterprise customers, affordable and powerful fingerprint scanners / smart card readers and built-in support for them within the consumer-level OS (Windows) and free Unix-like OSes, affordable locked cabinets, cases that now support various types of lock mechanisms at affordable rates, etc. Notice the trend? Technology that the Government/Enterprise used to enhance physical security are now available to any interested consumer without having to invest a small fortune into it.

Times change, security changes, but you guys seem like you're stuck in the past when it comes to physical security. Sure, a common default installation will be vulnerable to physical attacks - period. However, so is a machine on the Internet that is not properly maintained. Implementing most of my suggestions is as easy (or easier) than basic OS security (patching, updating, hardening, firewall configurations). None of them are going to make you immune to physical attacks, but make it such a hassle that it is unlikely they would have the skill, time, desire or prolonged access to circumvent them without you noticing.

Also, a powerful system with the "right software" is not going to magically bypass AES. Sure, if the user chooses a crappy password or leaves their token out in the open to be copied/stolen then it would be rather easy to defeat it. Heck, even if they boot from an unencrypted partition stored within the same system it would be easy to defeat. However, I already stated that user habit and enterprise policy are the major factors to consider when paired with reasonably strong encryption. It isn't like someone with a powerful computer and "the right software" will just magically get access to your AES protected data if you use a strong passphrase. If this were the case, then it would not be the industry standard and AES256 would not be certified for top secret files by the NSA. Sure, some AES implementations are poor and can be attacked, that is why it is important to use a well tested and vetted implementation.

> **deadflowr said:**
> Physical access might not be a guarantee to root access, it does break a major barrier.

Again, this depends on many variables. It might break a major barrier in some cases, but breaking one barrier just to access another strong barrier is not much of a gain. I agree, it does give the attacker an edge, but that is based on the attackers overall skill. If we were talking about the NSA wanting access then maybe AES wouldn't be up to the task (not that anything shows it wouldn't be), but in almost all cases if you opted-in for all 6 suggestions, implemented them correctly and followed a good policy/had good user habits, then you wouldn't likely have to worry about anyone circumventing them unless you left them alone with the machine for a very long time, and even then they still might fail.

I just want people to step out of the dark ages and realize you now have real options to greatly enhance physical security. Choosing to have a default installation and then claiming that physical security is pointless would be akin to never updating your OS, using incorrect permissions/restrictions, running a bunch of Internet-facing services without a firewall or any sort of maintenance and claiming all forms of Internet-related security suck or are pointless.

There is no magic pill for being secure. You need strong and sane layers of security to achieve anything of value, so why simply ignore physical security and just automatically assume it would be compromised no matter what? That is just the kind of thinking that never really progresses.

---

### Post by uRock on 2013-04-06
Your definition of a small fortune and mine is completely different. Nobody I know uses full disk encryption, a locked case, biometrics, nor any of the other hardware features you speak of. End users just don't bother with that for their home systems. With the use of power tools, I could cut through a hardened lockable case within a matter of minutes. AES may be hard to crack, but again, studies show that most people use the same password for everything. You missed where I said "a well versed cracker". A well versed cracker knows how the different softwares work to create the encryption algorithm. I am looking at this from a forensics angle. It is what I study. In a case where I am planning to crack someone's system for forensic evidence, I am going to look at everything possible to find what I need to know about the subject user. I will know his common interests, his favorite teams and players. I will most likely find everything I need to set up a usable dictionary attack against the suspect system, then I am going to use every system at my disposal to crack their encryption.

Most people I know of do not have 6 figure incomes to afford to buy a new PC every year to keep up with technology, nor do they have the money for much more than the cheapest of AV softwares. Half of them are still running Windows XP systems. One of them brought me her laptop because she forgot her admin password she had set years ago. In less than 5 minutes, I burnt a disk, booted her system from it, and cleared her passwords from all of her accounts on it. Android phones offer the capability to encrypt your info. Out of everyone I have asked, I am the only person I know who has taken advantage of that capability. Most people I know of do not lock their smart phone. I recognize the latest and greatest technologies and I except the fact that most people do not care enough to use them.

Needless to say, we have hijacked this thread. What we are talking about has nothing to do with the simple question the OP asked.

---

### Post by KaosuX on 2013-04-06
> **uRock said:**
> Your definition of a small fortune and mine is completely different. Nobody I know uses full disk encryption, a locked case, biometrics, nor any of the other hardware features you speak of. End users just don't bother with that for their home systems. With the use of power tools, I could cut through a hardened lockable case within a matter of minutes. AES may be hard to crack, but again, studies show that most people use the same password for everything. You missed where I said "a well versed cracker". A well versed cracker knows how the different softwares work to create the encryption algorithm. I am looking at this from a forensics angle. It is what I study. In a case where I am planning to crack someone's system for forensic evidence, I am going to look at everything possible to find what I need to know about the subject user. I will know his common interests, his favorite teams and players. I will most likely find everything I need to set up a usable dictionary attack against the suspect system, then I am going to use every system at my disposal to crack their encryption.

Most people I know of do not have 6 figure incomes to afford to buy a new PC every year to keep up with technology, nor do they have the money for much more than the cheapest of AV softwares. Half of them are still running Windows XP systems. One of them brought me her laptop because she forgot her admin password she had set years ago. In less than 5 minutes, I burnt a disk, booted her system from it, and cleared her passwords from all of her accounts on it. Android phones offer the capability to encrypt your info. Out of everyone I have asked, I am the only person I know who has taken advantage of that capability. Most people I know of do not lock their smart phone. I recognize the latest and greatest technologies and I except the fact that most people do not care enough to use them.

Needless to say, we have hijacked this thread. What we are talking about has nothing to do with the simple question the OP asked.

I agree that this thread has been hijacked. I will leave this conversation with just a few key points made:

A) Please note the following bolded text below;
    > [COLOR=#000000]Again, this depends on many variables. It might break a major barrier in some cases, but breaking one barrier just to access another strong barrier is not much of a gain. I agree, it does give the attacker an edge, but that is based on the attackers overall skill. If we were talking about the NSA wanting access then maybe AES wouldn't be up to the task (not that anything shows it wouldn't be), but in almost all cases if you opted-in for all 6 suggestions, implemented them correctly** and followed a good policy/had good user habits**, then you wouldn't likely have to worry about anyone circumventing them unless you left them alone with the machine for a very long time, and even then they still might fail.[/COLOR][COLOR=#000000]

B) The situations you described are not people who are fortifying themselves, not following good user habits or even basic security guidelines. So, they are not really that important to the debate regarding it being accessible and possible to harden a machine against a physical attack. These people you speak of are literally in the dark ages when it comes to security. As I said before, just because most people choose not to defend themselves against these types of attacks does not mean it isn't practical or possible.

C) Sure, you might do some information gathering on your target, but the type of attack(s) you described are rather basic and highly ineffective. The FBI tried to use an inefficient/outdated attack model like this against a Brazilian banker using TrueCrypt, and after around a year or two of non-stop attempts they failed miserably. Trying to use a simple dictionary attack, even if it is a targeted list, would only work against individuals that do not follow even the most basic security guidelines, choosing strong passphrases is security 101. Sure,  a lot of users use the same password for everything, use weak passwords, etc. However, we're talking about security oriented individuals. I don't think the target audience you speak of would even frequent a security discussion forum.  Also, in the described situation, this "well versed cracker" or "forensic examiner" relying on dictionary attacks, attacking weak implementations using (semi)automated software, etc. would not succeed against the six suggested steps if the end-user followed them all, implemented them all correctly and had good policies/user habits (as described in the quote above). 

D) I suppose our definition of small fortune could be different. However, I think most people would agree that a $80-$200 (basic biometrics that are at the very least FBI certified. the FS88 was only $89.00 or so) investment would not be too much of a hit if they really valued security. [/COLOR][COLOR=#000000]Don't be so over dramatic either, you don't need a six-figure income to afford a new computer every year. Heck, that was not even what I was saying. My point was, if someone wanted to build a new machine with physical security in mind they could do so. Most people that build for "gaming" usually end up with similar hardware. The price tag on the items are not the cheapest, but are very accessible to even home consumers[/COLOR][COLOR=#000000]

E) Yeah, you could cut through the case. You just better hope the machine was not powered down before you started working on it, because you would likely lose your chance of a CBA in that time Also, if the machine was powered on, and you had enough physical access to use power tools, then I would not consider this to be someone using a good policy or good user habits, because they clearly left the machine on and unattended for longer than they should have.

Like I said before, too many people still believe good physical security is a myth, but all it really takes is just a little time, money and effort.

Anyway, I have made all of the points about this topic that I need to. I will simply not respond anymore and just respectfully agree to disagree with the general consensus. 

Thanks for the discussion.[/COLOR]

---

### Post by tubbygweilo on 2013-04-06
KaosuX +1, a good posting.

---

### Post by uRock on 2013-04-06
> **KaosuX said:**
> Like I said before, too many people still believe good physical security is a myth, but all it really takes is just a little time, money and effort.[/COLOR]

Nobody said it was a myth. Most people would rather spend their time, hard earned money, and efforts on things they enjoy, not hardening the system they use for Facebook, Youtube and iTunes. Most of those folks don't even bother with backups. I can't image a true gamer wasting processes on encryption, when most of the ones I know turn off anti-virus and any other services they can in order to speed up their system.

---

### Post by alphaamanitin on 2013-04-24
I'm sorry but this is all crap.  No matter what you say physical acess==it is not your computer anymore.  All your protections are BS.  Some one that is prepared and ready to get make your machine turn against you will accomplish that with physical acess.  Forget your BS about your bios passwords, encryptions etc; some one prepared to take you machine over can simply install a hardware keylogger.  Hell, depending on the money availabe to the group and willingness to keep at it until they get it, they don't even need to put a device on your machine: ever here of electromagnetic analysis of the different keys or acoustic cryptoanalysis?  

Nothing short of a computer that never connects to the outside world (even through removable media) and creation of a system that is 100% effective against physical accesses and passive EM and acoustic analysis will secure you computer.  But then, what the hell is the point you no longer have a really usable machine.

For a usable machine for the home user (not state secrets, confidential material, etc) the best advice is:

1) limit physical acess to your computer
2)use encryption to encrypt your computer (with a separate home partition you can set separate passphrases to boot into linux and to mount your home partition)
3) shut down computer if you have to leave it unattended
4) if your computer has been out of your sight for quite a while, inspect it for tampering, including opening it up if you feel it necessary
5) if you are only worried about very specific files, use something like TrueCrypt to create an encrypted folder that is only decrypted for use and re-encrypted as soon as the use is over


Other advice: don't bother with the fingerprint readers unless they have become MUCH better.  The myth busters beat some commertial grade fingerprint readers for *very* reputable companies and beat it with a photo copy that was like and placed on thumb to mimik real "life" signs.

---

