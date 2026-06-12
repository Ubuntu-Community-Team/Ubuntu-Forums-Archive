---
title: "Hacking Ubuntu from Windows7"
date: 2010-04-13
forum: Security
---

### Post by ChristopherH on 2010-04-13
I need to know whether Ubuntu can be hacked when it is installed as a dual boot with W7 by hacking windows and getting access to the Ubuntu partition? 
 
What I would also like to know if this way can be used to put a key logger or screen capture in Ubuntu which installs next time Ubuntu is started?

---

### Post by cariboo on 2010-04-13
Without using extra software Windows can't directly access any type of partition other than NTFS/vfat.

With social engineering, anything is possible. If you use Ubuntu, you know that system wide programs have to installed by root.

---

### Post by CharlesA on 2010-04-13
Why do people use the term "hacking" so frequently. :|

You'd need to have the ext-FS driver installed and I believe that it won't read EXT4 partitions.

---

### Post by dgw on 2010-04-13
If they have physical access, it's probably easier to get in by booting the computer from a live CD, rather than going in through your Windows install.

---

### Post by CharlesA on 2010-04-13
> **dgw said:**
> If they have physical access, it's probably easier to get in by booting the computer from a live CD, rather than going in through your Windows install.

Bingo.

---

### Post by Dayofswords on 2010-04-13
> **ChristopherH said:**
> I need to know whether Ubuntu can be hacked when it is installed as a dual boot with W7 by hacking windows and getting access to the Ubuntu partition? 
 
What I would also like to know if this way can be used to put a key logger or screen capture in Ubuntu which installs next time Ubuntu is started?

whatcha up to?

---

### Post by meskes on 2010-04-13
My Spidy Senses are tingling like MAD over here. I don't like the direction this guy is going AT ALL... *try not to jump to conclusions* *BUT IT'S SO HARD RIGHT NOW*

---

### Post by a.walker on 2010-04-13
Physical Access = Root Access.

If you don't trust someone with your computer do the following:

1) Don't let him near the computer.
2) Encrypt your file system.

---

### Post by Jive Turkey on 2010-04-14
if windows was compromised to the point where an attacker could install some driver to read your linux filesystem and put some specially crafted files in the correct places (assuming no encryption in those places) it could be possible.  I wouldn't be surprised if Microsoft deployed an update that messes with linux partitions either.  Full encryption might help to avoid such an (unlikely attack).

---

### Post by ChristopherH on 2010-04-14
I am less worried about local access at this stage.  Reading the replies it seems to me that it is entirely possible to get to Ubuntu through W7.  I am not worried about a chance attacker so much but a targeted attack to take sensitive data and I am left with the same concerns I started with.  I like the idea of encryption and would like to know what to do to encrypt Ubuntu if it is already installed.  I have a copy of TrueCrypt and can encrypt containers but don't know about encrypting partitions or Ubuntu.

---

### Post by OpSecShellshock on 2010-04-14
Talking people into just (unknowingly) giving you what you're looking for or installing the surveillance software for you during the Ubuntu session is far, far easier than attempting to hijack one OS, let alone hijack the other one after that.

---

### Post by ChristopherH on 2010-04-14
There is no chance of me giving anyone access to my PC or me installing unknown software for them.  So the potential vulnerability as I understand it is using W7 to get to my Ubuntu.  My Ubuntu does not go on the net and therefore as long as I protect local access and use an encrption container then it should be safe apart from remote access via W7.  If I am wrong about this then please let me know.  I am coming to the conclusion that my W7 is definately not safe because it goes on the net and my Ubuntu is also not safe as, reading the threads, W7 can be used to get to it.  What can I do apart from just not use either for sensitive work??  What a bummer!!

---

### Post by OpSecShellshock on 2010-04-14
Well you could try booting into Windows and then looking at the files on the disk to see if you are able to list and/or access the files on the Ubuntu partition when it's not booted. There's a chance that even if Windows would be "aware" that another partition exists, it still wouldn't be able to see what's in it. Certainly a remote attacker wouldn't have any way of knowing. If there's any risk at all it'd be very, very low.

---

### Post by ali_etoom on 2010-04-14
Windows 7 wont recognize Ubuntu because  windows 7 uses NTFS files systems and ubuntu recognize FAT32 file systems

---

### Post by doas777 on 2010-04-14
as long as its not a virtual host, or wubi, you should be fine. 
yes what you suggest is possible, but but very improbable. the perpertrator would have to want to target you specifically, and go to all the trouble of getting to your hdd, uploading the malcode, and configing it to autorun manually, is a serious disincentive.

---

### Post by CharlesA on 2010-04-14
> **ali_etoom said:**
> Windows 7 wont recognize Ubuntu because  windows 7 uses NTFS files systems and ubuntu recognize FAT32 file systems

That makes no sense at all.

---

### Post by uRock on 2010-04-14
> **CharlesA said:**
> Why do people use the term "hacking" so frequently. :|

I have asked my Network Security Management professor the same thing. The text for said class calls them hackers and I get really weird replies when I say "No they are not hackers, they are crackers."

They crack the code to find loopholes to take control of or manipulate a system. A hacker just makes his or her own programs work the way he or she wants them to work.

---

### Post by OpSecShellshock on 2010-04-15
> **uRock said:**
> I have asked my Network Security Management professor the same thing. The text for said class calls them hackers and I get really weird replies when I say "No they are not hackers, they are crackers."

They crack the code to find loopholes to take control of or manipulate a system. A hacker just makes his or her own programs work the way he or she wants them to work.

Actually nowadays most of them buy software written by someone else, throw it on their PC, and run it. Which makes them *users*.

---

### Post by LeeDaugherty on 2010-04-15
Not that it matters, but I haven't heard the term cracker used in 15 years, don't use it, you sound racist, or like you read a textbook from the 80's.  The act of hacking is modification, the modification without permission is still technically hacking.  In any case, cryptdisks or the like is easy to setup, search for info on it, and if you're info is that valuable, dump Windows off your laptop, or better yet, spend $10 on a USB flash drive and carry it with you, or booty bump it if it means that much to you.  Ubuntu is safe, if you are worried about a targeted attack, and you believe the person has the know-how, it doesn't matter what OS you use.  And that's just simple fact.  Targeted attacks can't (well...for the most part) be stopped if the other person knows what they are doing.  Never use wifi, and never use a network that isn't under your control.  And live the rest of your life in fear...in other words...relax.  After 15 years, I've thought and said most of the same things.  Then I realized besides someone finding out how much porn I actually have, the files I have, ain't that special, and the rest of the world agrees.

---

### Post by uRock on 2010-04-15
> **LeeDaugherty said:**
> haven't heard the term cracker used in 15 years, don't use it, you sound racist,
What? That's just wrong. A cracker is someone who cracks code.

---

### Post by LeeDaugherty on 2010-04-15
Yes, technically yes, its just a term no one uses.  It's like calling a janitor a custodian.  It's correct, but the term isn't used.  You crack passwords, and that's called brute-force dictionary attacks, unless you are in a movie.  95% of all exploits are buffer overflows, I wouldn't say I cracked a program if I just got lucky enough and forced 300 characters in a field that should only fit 10 and the program barfed and allowed me to drop shell code.

---

### Post by uRock on 2010-04-15
> **LeeDaugherty said:**
> Yes, technically yes, its just a term no one uses.  It's like calling a janitor a custodian.  It's correct, but the term isn't used.  You crack passwords, and that's called brute-force dictionary attacks, unless you are in a movie.  95% of all exploits are buffer overflows, I wouldn't say I cracked a program if I just got lucky enough and forced 300 characters in a field that should only fit 10 and the program barfed and allowed me to drop shell code.
You may not use it, but it is used. Why should true hackers be treated as bad people when their real motive is to make their own system work, not "crack" into other people's systems?

---

### Post by LeeDaugherty on 2010-04-15
Are we really talking about this?  true hackers? what, it's 9:30a and I already want to drink...I never said ooo hackers ooo all bad people...no I simply said and use the term daily...ex.  To improve your H264 acceleration on your NVidia VDPAU enabled GPU, insert the disable composite hack in your xorg.conf.  That's actually true for anyone that cares...in any case, it's a word it can be used.  I didn't mean to upset you, don't know why you are getting all up in arms, just felt like pointing out that no one uses that term.  People use hack too much, that's why I don't personally use the term hacker.  Hackers existed along time ago, do you honestly think they would have named it the great hacker war if they had to say the great cracker war?  I f33l like typing 3lit3 now.  I don't use it, and if you want to shove everything back in my face more power to you.  Walk around your techy job, in your techy school, writing your visual basic scripts that write 0's on the MBR and call your self a cracker.  Cause at the end of the day, that's exactly what you are going to be...with squirt cheese...mmm snack break....oh and there are more proper terms that actually are used.  People have hats they wear.  It's an old proverb, it's the job you do and the hat you wear.  I don't know what job the man in the red Fedora did...which techically at the time was called Red Hat.  But you refer to hackers that do good and improve society and its moral fiber white-hats.  And then black hats and grey hats are self-explanatory.

---

### Post by steveneddy on 2010-04-15
It is highly unlikely that some random person looking at your PC will even be able to detect that Ubuntu is even installed on your dual boot system for starters.

Secondly, it is also unlikely that anyone that DOES have direct access to your PC will know what Linux is and THEN be capable of installing anything remotely similar to a key logger on your Ubuntu install from Windows.

Third, a malicious person on the internet - a "hacker" by your definition, not mine - will only be looking for the Windows files, not Linux files, AND that malicious person with internet access to your PC will most likely not be able to see the Linux files on the drive.

Fourth, unless Ubuntu is running at the same time as Windows, NOTHING will be sent to the Windows side of the partition anyway.

So, rest easy and enjoy the secure feeling of using Linux.

Good reading:

[http://www.psychocats.net/ubuntu/security#bestpractices](http://www.psychocats.net/ubuntu/security#bestpractices)

[http://www.linuxtopia.org/LinuxSecurity/](http://www.linuxtopia.org/LinuxSecurity/)

---

### Post by uRock on 2010-04-15
> **LeeDaugherty said:**
> Are we really talking about this?  true hackers? what, it's 9:30a and I already want to drink...I never said ooo hackers ooo all bad people...no I simply said and use the term daily...ex.  To improve your H264 acceleration on your NVidia VDPAU enabled GPU, insert the disable composite hack in your xorg.conf.  That's actually true for anyone that cares...in any case, it's a word it can be used.  I didn't mean to upset you, don't know why you are getting all up in arms, just felt like pointing out that no one uses that term.  People use hack too much, that's why I don't personally use the term hacker.  Hackers existed along time ago, do you honestly think they would have named it the great hacker war if they had to say the great cracker war?  I f33l like typing 3lit3 now.  I don't use it, and if you want to shove everything back in my face more power to you.  Walk around your techy job, in your techy school, writing your visual basic scripts that write 0's on the MBR and call your self a cracker.  Cause at the end of the day, that's exactly what you are going to be...with squirt cheese...mmm snack break....oh and there are more proper terms that actually are used.  People have hats they wear.  It's an old proverb, it's the job you do and the hat you wear.  I don't know what job the man in the red Fedora did...which techically at the time was called Red Hat.  But you refer to hackers that do good and improve society and its moral fiber white-hats.  And then black hats and grey hats are self-explanatory.

You do not know me. Your assumptions are wrong. I am not the racist nor the squirt cheese eating IT guy that you perceive me to be.

---

### Post by LeeDaugherty on 2010-04-15
Well said!  But!  Whatever operating system is running, it is VERY easy and VERY reliable to fingerprint the system and find out what OS and version and service pack they are running. If Ubuntu isn't running then, no chance in heck, but OS fingerprinting is a key step in any system compromise.  Second, the person attacking your computer probably doesn't even know what Linux is?  Wow...I hope you weren't serious.  OR meant that in a different way.  So I won't respond.  And the rest is cool...except, how can you run Ubuntu the same time as Windows? nvm you meant virtual machine which I'm sure is in the scope of someone asking the original question :)

---

### Post by LeeDaugherty on 2010-04-15
You made my day...never lose the humor in this life.  I worked with a tech one-time that ate wheat thins and squirt cheese non-stop, and that's where that came from :P  And next on Springer...racist squirt cheese eating IT techs....jerry jerry jerry!  love it!

---

### Post by steveneddy on 2010-04-15
My point was that unless you have vital info on your machine, all some little squirt cheese is gonna look for is windows files.

Rarely is the "hacker" that lurks on your system for hours saying to him/herself - "I wonder where that darn Ubuntu install is?"

MOST OF THE TIME this stuff is installed on a Windows system in a drive by web site or from e-mail.

I wouldn't be overly concerned unless you are running a server with critical info on the server or the network it is on.

Is it possible for Ubuntu to be hacked?

Yes

Will it be caught by the community before it becomes a wide spread issue?

probably

If one DL's soft from a source that is malicious, like the one that was on gnomelook recently, then you will be pwned.

Read the links in my original post.

---

### Post by LeeDaugherty on 2010-04-15
PERFECT!  You win...well said...and I have nothing to add!  You say things alot nicer than I do :/ damn dr pepper fits...and you even said pwned....rock on! 31it3!

---

### Post by uRock on 2010-04-15
> **LeeDaugherty said:**
> You made my day...never lose the humor in this life.  I worked with a tech one-time that ate wheat thins and squirt cheese non-stop, and that's where that came from :P  And next on Springer...racist squirt cheese eating IT techs....jerry jerry jerry!  love it!
A person with an education watching Jerry? That is funny.

---

### Post by uRock on 2010-04-15
> **steveneddy said:**
> Will it be caught by the community before it becomes a wide spread issue?
That is one of the reasons I love this community.

---

### Post by Objekt on 2010-04-15
To access Ubuntu's files from within Windows 7, you would have to find some way to make Windows 7 speak ext3/ext4.  I have yet to make that work.  There are Installable File System utilities for Windows that claim to do it, but I have never got it to work.  Windows XP and 7 always insist the ext3 volumes are "unformatted" and offer to format them.

Not saying accessing Ubuntu files from Win 7 is impossible in general, just impossible on my hardware.  My hardware is nothing special, a mixture of oridnary SATA hard drives.  I have no idea why IFS won't work, but it doesn't.  Security through malfunction, I guess.

---

### Post by LeeDaugherty on 2010-04-15
[http://www.ext2fsd.com/](http://www.ext2fsd.com/) - worked for me last year Vista to ext3, just make sure you mount it on Linux first and stop the journal :)  I made that mistake once.  When it comes to security, you hit the wall of open source and GPL, closed-source to Linux has always been a challenge, when you want to play in Linux land in Windows, there are lots of fun little utils.  And ports of all your favorite utilities!

---

### Post by steveneddy on 2010-04-15
> **LeeDaugherty said:**
> [http://www.ext2fsd.com/](http://www.ext2fsd.com/) - worked for me last year Vista to ext3, just make sure you mount it on Linux first and stop the journal :)  I made that mistake once.  When it comes to security, you hit the wall of open source and GPL, closed-source to Linux has always been a challenge, when you want to play in Linux land in Windows, there are lots of fun little utils.  And ports of all your favorite utilities!

I agree that this is "possible", just not very probable that a "hacker" type would go to these lengths to see what theme's you have installed in your 133t Gnome install.

As for the OP who stated at the top of the thread:

> I need to know whether Ubuntu can be hacked when it is installed as a dual boot with W7 by hacking windows and getting access to the Ubuntu partition? 

What I would also like to know if this way can be used to put a key logger or screen capture in Ubuntu which installs next time Ubuntu is started?

Unless someone has direct access to the machine, it probably won't happen.

---

### Post by LeeDaugherty on 2010-04-15
Ahhh...the wonderful times...that we fill up 4 pages and never answer the original question...times like this make life fun....I think everyone agrees on this one....everyone say the Mythbuster line together:  It's Plausible...   and then we all add.... but it's not going to happen.

---

### Post by doas777 on 2010-04-15
> **LeeDaugherty said:**
> Ahhh...the wonderful times...that we fill up 4 pages and never answer the original question...times like this make life fun....I think everyone agrees on this one....everyone say the Mythbuster line together:  It's Plausible...   and then we all add.... but it's not going to happen.

ummmm, that _***is***_ the answer... 
not every question can be answered as a binary.
would you prefer we just said 'yes' and let the op crap him/herself?

---

### Post by OpSecShellshock on 2010-04-15
Wow, I missed the part about keyloggers and screen/form grabbers the first time around. That lowers the risk even more, because even if there were such a thing running, the Ubuntu build doesn't have network access. Where would it go?

---

### Post by Jive Turkey on 2010-04-15
> **doas777 said:**
> ummmm, that _***is***_ the answer... 
not every question can be answered as a binary.
would you prefer we just said 'yes' and let the op crap him/herself?

Excellent idea!

...YES!

---

### Post by node8472 on 2010-04-15
> **ChristopherH said:**
> There is no chance of me giving anyone access to my PC or me installing unknown software for them.  So the potential vulnerability as I understand it is using W7 to get to my Ubuntu.  My Ubuntu does not go on the net and therefore as long as I protect local access and use an encrption container then it should be safe apart from remote access via W7.  If I am wrong about this then please let me know.  I am coming to the conclusion that my W7 is definately not safe because it goes on the net and my Ubuntu is also not safe as, reading the threads, W7 can be used to get to it.  What can I do apart from just not use either for sensitive work??  What a bummer!!
you'd be better off letting ubuntu without any anti-virus or firewall gui installed on the net than letting winblows "anything" on the net!! there are more holes in windows than Swiss cheese! if you read the other posts you'd know that accessing the ubuntu part wouldn't work unless you install a driver that is suposed to allow windows to mount ext3 file systems. If you installed via wubi that might accessible to said intruder.

---

### Post by ChristopherH on 2010-04-24
Come on guys I need to know how to encrypt Ubuntu once it is installed and someone out there knows how to solve my problem of using W7 and Ubuntu but ensuring the Ubuntu is as safe as possible.  I accept local access is an issue but I am on this.  I have encountered information about a government high security linux flavour but don't know much about it.  I am prevented from progressing my research work because I cannot write it down and it is important work and is for the benefit of people.  I am less worried about a casual attack and more concerned about a targeted one.  Please help me.

---

### Post by v1ad on 2010-04-24
Lets All Hack "Open Source Software"

---

### Post by CharlesA on 2010-04-24
> **ChristopherH said:**
> Come on guys I need to know how to encrypt Ubuntu once it is installed and someone out there knows how to solve my problem of using W7 and Ubuntu but ensuring the Ubuntu is as safe as possible.  I accept local access is an issue but I am on this.  I have encountered information about a government high security linux flavour but don't know much about it.  **I am prevented from progressing my research work because I cannot write it down and it is important work and is for the benefit of people.**  I am less worried about a casual attack and more concerned about a targeted one.  Please help me.

So you cannot write it down because you are paranoid about Windows somehow gaining access to the linux portion of a dual-boot system?

The only way I know to do fully encrypt the drive after an install is to use Truecrypt and encrypt a volume. If you want the entire install encrypted, then do a reinstall.

Windows will still see the partition as "unknown" and allow you to delete it from Windows. Nothing you can do about that.

---

### Post by MCVenom on 2010-04-24
It is not reasonably possible. Please calm down, something like that would require **TONS** of work over a network attack, and would require the attacker to know that you have a Linux partition on your pc, something that's not going to be detectable by an attacker without jumping through hoops on it, if it even works at all (you probably have an ext4 partition, I doubt it's even possible with ext4). Just calm down and go on with your life :p

---

### Post by The Cog on 2010-04-26
I think hacking the Linux install from the running win7 is unlikely. But it your paranoia level is high enough, here are some thoughts:

Windows cannot (from items I've read - never tried it) read recent Linux partitions. I gather that the ext3 driver for windows can't cope with recent default inode sizes on ext3. However:

A determined attacker might have a driver that can read ext3. If this is a commercial targeted attack, this is quite possible.

A determined attacker could simply send the entire partition contents to the owner for later analysis, or replace the partition contents with those sent from the attackers machine.

He might be able to install keyboard logger and caching in the BIOS flash, or install a small VM to the boot partition so your Linux actually boots inside a secretly watching VM without knowing it. The VM could talk over the internet even when Linux has no network connectivity.

In short, if a determined attacker can breach your win7 then all other partitions are compromised, perhaps even the encrypted ones. That kind of stuff is (as far as I know) way beyond normal criminal hacking for credit card stuff, but probably well within the capabilities of a determined government department.

Did you know it's possible to see what's on almost any screen, and log what is typed on almost any keyboard from a nearby parked car (with appropriate radio receivers)? That's been possible for 20 years or more.

And I think you have it backwards. If you're worried about being hacked, it's win7 you should be isolating, not Linux.

---

### Post by OpSecShellshock on 2010-04-26
There is far greater risk (IMO) of someone either impersonating another user whom you trust or who is authorized to view the same data, or compromising the computer of such a person, than there is of having a compromised local Windows 7 installation acquire data from a Linux partition on the same drive.

---

### Post by popuptarget on 2010-04-26
> **ChristopherH said:**
> Come on guys I need to know how to encrypt Ubuntu once it is installed and someone out there knows how to solve my problem of using W7 and Ubuntu but ensuring the Ubuntu is as safe as possible.  I accept local access is an issue but I am on this.  I have encountered information about a government high security linux flavour but don't know much about it.  I am prevented from progressing my research work because I cannot write it down and it is important work and is for the benefit of people.  I am less worried about a casual attack and more concerned about a targeted one.  Please help me.

Your doing reasearch work at a level that you do not feel safe typing into a computer because it is going to be exposed to a targeted net attack.  Here is an idea.  Buy an extra hard drive for computer in question.  Put Ubuntu on it and dont plug it into the net.  Am I missing something?

---

### Post by steveneddy on 2010-04-26
I guess everything I posted on this thread was a waste of time.

Me thinks the OP worries too much.

The best way to run Ubuntu on your PC is to run it off of the live CD and never install it. It will NEVER be hacked if you choose that method.

---

### Post by PerfectReign on 2010-04-26
Very simple.

Just use ValuHack.  [http://valuhack.sourceforge.net/](http://valuhack.sourceforge.net/)

If you need more information, just send me your credit card number, expiration date, bank account number and your password.

I'll set you up with all you need.  :P

---

