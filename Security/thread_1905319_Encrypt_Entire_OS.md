---
title: "Encrypt Entire OS"
date: 2012-01-06
forum: Security
---

### Post by bustard on 2012-01-06
I know that Truecrypt for windows lets you encrypt the entire OS but that it can not do that with linux.

But is there some way I could make a truecrypt container, move / to it, and then, somehow, whenever I boot the pc, enter a password to decrypt it, so that it would then be the OS?

---

### Post by MadsRC on 2012-01-06
You can do a full disk encryption with LVM2/LUKS and then when you boot the OS you will be prompted to type in a password.

It isn't a true "full disk encryption" though, as you cannot encrypt your boot partition. But that partition doesn't have any valuable data on it.

---

### Post by MadsRC on 2012-01-06
I've found this link to be very usefull when doing such an install. Those installs have been for BackTrack though, but should be fairly easy to port to Ubuntu, as BackTrack is Ubuntu based.

Link: [http://www.edwiget.name/2011/11/administration-backtrack-5r1-full-disk-encryption-install-to-hard-drive/#codesyntax_1](http://www.edwiget.name/2011/11/administration-backtrack-5r1-full-disk-encryption-install-to-hard-drive/#codesyntax_1)

---

### Post by /dev/random/username on 2012-01-06
This is the guide I followed for my machine [http://joernfranz.net/2011/01/20/installing-ubuntu-10-10-with-full-disk-encryption/](http://joernfranz.net/2011/01/20/installing-ubuntu-10-10-with-full-disk-encryption/)

Follow that to the letter and you'll have yourself an encrypted Ubuntu.
[]("http://joernfranz.net/2011/01/20/installing-ubuntu-10-10-with-full-disk-encryption/")

---

### Post by 0011235813 on 2012-01-08
Honestly what's the point? I can understand encrypting valuable files and sensitive information, but this is just pointless. What on Earth do you plan on doing with this? Do you really think being made to enter two passwords on boot really makes you that much more secure? It's not like a virus can destroy your system: Sudo takes care of that. So what is left?

---

### Post by Cheesemill on 2012-01-08
Without encryption I could access everything on your machine if I was in front of it.
If it was encrypted I wouldn't have a chance (well, [maybe]("http://xkcd.com/538/")).

Physical Access = Root Access

---

### Post by uRock on 2012-01-08
> **0011235813 said:**
> Honestly what's the point? I can understand encrypting valuable files and sensitive information, but this is just pointless. What on Earth do you plan on doing with this? Do you really think being made to enter two passwords on boot really makes you that much more secure? It's not like a virus can destroy your system: Sudo takes care of that. So what is left?

Encrypting the full OS not only protects the data from being seen, but also prevents people with physical access from reading system logs. The system logs are stored in the root partition(or folder depending on the install), which means they are visible when only the home partition is encrypted.

Most importantly, the OP shouldn't have to explain why (s)he wants to use encryption.

---

### Post by Ms. Daisy on 2012-01-09
> **Cheesemill said:**
> ...(well, [maybe]("http://xkcd.com/538/")). 
I LOLed. Thanks!
		[QUOTE=0011235813]Honestly what's the point? I can understand encrypting valuable files  and sensitive information, but this is just pointless. What on Earth do  you plan on doing with this? Do you really think being made to enter two  passwords on boot really makes you that much more secure? It's not like  a virus can destroy your system: Sudo takes care of that. So what is  left? 	[/QUOTE]
The point is that the OP wants to do it. The point of this forum is to find a way to do it.  It is pointless to hijack a reasonable help request to preach your point of view.

---

### Post by Dangertux on 2012-01-09
> **0011235813 said:**
> Honestly what's the point? I can understand encrypting valuable files and sensitive information, but this is just pointless. What on Earth do you plan on doing with this? Do you really think being made to enter two passwords on boot really makes you that much more secure? It's not like a virus can destroy your system: Sudo takes care of that. So what is left?

What on earth are you talking about? 

For that matter what are any of you talking about? Full drive encryption is hugely misunderstood I think.

1 - Once LUKS/ecrytpfs/whatever else is unlocked at mount the data is as good as plain text until it's unmounted. Full drive encryption is a physical security measure. It will not protect against anything happening while the filesystem is mounted.

2 - What do sudo and viruses have to do with any of this? Nothing.

3 - Yes the OP should be able to do whatever they want. However I don't think this will do what the OP thinks it will.


Hope this helps.

---

### Post by 0011235813 on 2012-01-09
> **Cheesemill said:**
> Without encryption I could access everything on your machine if I was in front of it.
If it was encrypted I wouldn't have a chance (well, [maybe]("http://xkcd.com/538/")).

Physical Access = Root Access

No you couldn't access everything on the machine- Because you don't know the root password! 
What do viruses have anything to do? Nothing really- It just reinforces my point- that it's pointless to encrypt anything other than sensitive files. Because important system files are held in root folders which require sudo to view. The only advantage I would see to encrypting the whole disk would be that if a hacker somehow manages to get access to your computer (and thus know the password) they wouldn't be able to delete those important files. But still- they could do plenty of other nasty things to your computer. (and it's highly unlikely it would ever happen ANYWAY, as the VAST majority of these attacks occur because the user is fooled into doing something they shouldn't- SSH access for example)

But anyway, if you so desperately need full-disk encryption, you CAN use TrueCrypt within Linux (see attachment). Installation isn't very user friendly, but there are some turoials on line that show you how to do it.
[http://mygeekopinions.blogspot.com/2011/06/install-truecrypt-in-ubuntu-1104-natty.html](http://mygeekopinions.blogspot.com/2011/06/install-truecrypt-in-ubuntu-1104-natty.html)
It's natty- But it should work.

---

### Post by 0011235813 on 2012-01-09
> **Dangertux said:**
> What on earth are you talking about? 

For that matter what are any of you talking about? Full drive encryption is hugely misunderstood I think.

1 - Once LUKS/ecrytpfs/whatever else is unlocked at mount the data is as good as plain text until it's unmounted. Full drive encryption is a physical security measure. It will not protect against anything happening while the filesystem is mounted.

2 - What do sudo and viruses have to do with any of this? Nothing.

3 - Yes the OP should be able to do whatever they want. However I don't think this will do what the OP thinks it will.


Hope this helps.
I agree TrueCrypt doesn't do what the OP thinks it does- I've used it after all! But for that matter, OP: What **exactly** do you plan to do? 
I was saying that if the computer was infected, sudo would prevent it deleting important system files- there would be no need for encryption.
What exactly is full disk encryption supposed to do? Make you enter an obscure 20 character password everytime you try to access a file or open a program??!

---

### Post by /dev/random/username on 2012-01-09
You only type that obscure 20 char password once upon boot, and thats it. You have access to your system and all.

Read #1 on Dangertux's post

---

### Post by Cheesemill on 2012-01-09
> **0011235813 said:**
> No you couldn't access everything on the machine- Because you don't know the root password! 
What do viruses have anything to do? Nothing really- It just reinforces my point- that it's pointless to encrypt anything other than important files. Because important system files are held in root folders which require sudo to view. The only advantage I would see to encrypting the whole disk would be that if a hacker somehow manages to get access to your computer (and thus know the password) they wouldn't be able to delete those important files. But still- they could do plenty of other nasty things to your computer. (and it's highly unlikely it would ever happen ANYWAY, as the VAST majority of these attacks occur because the user is fooled into doing something they shouldn't- SSH access for example)

But anyway, if you so desperately need full-disk encryption, you CAN use TrueCrypt within Linux (see attachment). Installation isn't very user friendly, but there are some turoials on line that show you how to do it.
[http://mygeekopinions.blogspot.com/2011/06/install-truecrypt-in-ubuntu-1104-natty.html](http://mygeekopinions.blogspot.com/2011/06/install-truecrypt-in-ubuntu-1104-natty.html)
It's natty- But it should work.

I don't neeed to know the root password.

You can either boot the recovery kernel from grub - no need for the root password
Boot from a live CD - no need for the root password
Remove the drive and use it in an installed system - no need for the root password


The **ONLY** protection for physical access is disk encryption.
This is best achieved by LVM on top of LUKS:

[https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto](https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto)

I've not used this how-to because I am currently using Arch, but I've scanned through it and it looks OK.

---

### Post by 0011235813 on 2012-01-09
> **/dev/random/username said:**
> You only type that obscure 20 char password once upon boot, and thats it. You have access to your system and all.

Read #1 on Dangertux's post

Oh I forgot! The **Operating System It'sefl** requires password on boot! What a funny thing! You don't suppose this is a new feature do you?

And to the other guy/girl (Does this site support multiquoting?), there is no way software can protect you if someone has physical access to your computer. I honestly don't see the point, if someone has physical access to your computer, there are other things they would be more interested in. Say:

1. You're in a business environment, and an employee with a grudge decides to go to your computer and find out personal information to humiliate you with. Full-disk isn't necessary- just encrypt a single directory.
2. Someone steals into your home and steals your computer. Again, the important information is secure, and you won't care if they have a different OS or not since you won't have your computer!

Seriously, the only scenario I would think this necessary would be in a governmental agency (MI5, MI6). And who is really so concerned about physical access anyway? If somebody has physical access the computers doomed anyway. Now you might say; what if someone breaks my system just for the sake of it? In which case, they could just take a hammer and smash the computer to bits. Encryption my @$$!

---

### Post by Cheesemill on 2012-01-09
> **0011235813 said:**
> 1. You're in a business environment, and an employee with a grudge decides to go to your computer and find out personal information to humiliate you with. Full-disk isn't necessary- just encrypt a single directory.
2. Someone steals into your home and steals your computer. Again, the important information is secure, and you won't care if they have a different OS or not since you won't have your computer!!

Just encrypting /home isn't a foolproof method.
Even with an encrypted home directory there are several options:

Copy /etc/passwd and /etc/shadow and brute force your user password.

Log on as root and sniff the company network.

/var/log contains a lot of useful information that could help crack your company network.

/tmp could contain unencrypted files from /home as well as encryption keys.

Even with full disc encryption there are a couple of methods that have a chance of working, for example freezing the RAM to sub zero temperatures can allow you to recover encryption keys from a recently shut-down system.

My point is that full disc encryption is currently the best way of protecting your data from someone having physical access to your machine.

In fact **ALL** of the laptops that I administrate at work have full disc encryption set up as standard to help comply with data protection-laws.

---

### Post by /dev/random/username on 2012-01-09
> **0011235813 said:**
> Oh I forgot! The **Operating System It'sefl** requires password on boot! What a funny thing! You don't suppose this is a new feature do you?

And to the other guy/girl (Does this site support multiquoting?), there is no way software can protect you if someone has physical access to your computer. I honestly don't see the point, if someone has physical access to your computer, there are other things they would be more interested in. Say:

1. You're in a business environment, and an employee with a grudge decides to go to your computer and find out personal information to humiliate you with. Full-disk isn't necessary- just encrypt a single directory.
2. Someone steals into your home and steals your computer. Again, the important information is secure, and you won't care if they have a different OS or not since you won't have your computer!

Seriously, the only scenario I would think this necessary would be in a governmental agency (MI5, MI6). And who is really so concerned about physical access anyway? If somebody has physical access the computers doomed anyway. Now you might say; what if someone breaks my system just for the sake of it? In which case, they could just take a hammer and smash the computer to bits. Encryption my @$$!

Read carefully what Cheesemill and Dangertux said.. also I would like to see you gaining access to fully encrypted system.. unless you have a few billion years to spend waiting while bruteforcing.

Cheesemill pointed out that with a "livecd" and phisical access to a system without encryption, root or user password wont help out.

---

### Post by 0011235813 on 2012-01-09
> **/dev/random/username said:**
> Read carefully what Cheesemill and Dangertux said.. also I would like to see you gaining access to fully encrypted system.. unless you have a few billion years to spend waiting while bruteforcing.

Cheesemill pointed out that with a "livecd" and phisical access to a system without encryption, root or user password wont help out.

In the end, you only need to encrypt the important files, encrypting an entire OS is just pointless, since it won't protect your computer from someone with physical access. I don't see anything else to say, I've explained in clear terms why I think full-disk encryption is pointless, you can agree or disagree. I've also explained to the OP how to get& install TrueCrypt. Now, either you give advice on how to install an arguably superior encryption program, or build on my advice, but debating this is pointless and off-topic. I've told the OP that what they are suggesting may not do what they think it does, but I've still told them how to install the program they **originally asked for**. If you really think full-disk encryption is so important, start your own thread, otherwise leave it at that.

PS: Governmental Agency's regularly decrypt messages and e-mail. It will not take billions of years- this is not Astronomy or Geology, and we're not talking about the life of stars or the creation of planets- we're talking about a simple encryption program, which could probably be broken in a couple of minutes with the use of a supercomputer.

---

### Post by MadsRC on 2012-01-10
If you actually read the OP then you can see that he asks if TrueCrypt supports Full Disk Encryption in Linux, as it does in Windows. Source: " Truecrypt for windows lets you encrypt the entire OS but that it can not do that with linux."

So you actually never really did answer his question.

And we alle know that TrueCrypt doesn't support FDE for Linux, as it does for Windows, hence the information regarding LVM on top of LUKS as the solution.

> PS: Governmental Agency's regularly decrypt messages and e-mail. It will not take billions of years- this is not Astronomy or Geology, and we're not talking about the life of stars or the creation of planets- we're talking about a simple encryption program, which could probably be broken in a couple of minutes with the use of a supercomputer.

The only known way to break AES-256 is by bruteforcing (though there were a proof-of-concept some time ago about some other possible, but unlikely way) the password. If you use a short easy password, then yes, you could break it in a few seconds. But if you use a "obscure 20 character password" as discussed earlier then it can't be done in a few seconds. Best in a couple of years.

There's a reason AES-256 is adobted by US-Goverment (And especially the NSA) and other govermental agencies. If it could be cracked by a super computer in a couple of seconds, then it wouldn't be approved for govermental use.

Besides, there's not infinite super computers in the world, so the goverment would need a pretty good reason to use it against your computer, instead of cracking something else.

I remember a case i Brazil where the goverment tried, for 2 years, to crack a AES-256 TrueCrypt container. When they couldn't, all charges where canceled.

That was a AES-256 encrypted folder. Same encryption as LVM on top of LUKS would utilise.

I suggest you read up on AES: [http://en.wikipedia.org/wiki/Advanced_Encryption_Standard#Known_attacks](http://en.wikipedia.org/wiki/Advanced_Encryption_Standard#Known_attacks)

The only negative things I can see that there is with software encyption is:
1: A bit slower performance
2: Loose your key, loose your data
3: You can still, with physical access, format the harddrive. But you wouldn have to recover the ENTIRE encrypted partition to get any information out of it.

Please correct me if the above 3 points are wrong.

---

### Post by 0011235813 on 2012-01-10
> **MadsRC said:**
> If you actually read the OP then you can see that he asks if TrueCrypt supports Full Disk Encryption in Linux, as it does in Windows. Source: " Truecrypt for windows lets you encrypt the entire OS but that it can not do that with linux."

So you actually never really did answer his question.

And we alle know that TrueCrypt doesn't support FDE for Linux, as it does for Windows, hence the information regarding LVM on top of LUKS as the solution.



The only known way to break AES-256 is by bruteforcing (though there were a proof-of-concept some time ago about some other possible, but unlikely way) the password. If you use a short easy password, then yes, you could break it in a few seconds. But if you use a "obscure 20 character password" as discussed earlier then it can't be done in a few seconds. Best in a couple of years.

There's a reason AES-256 is adobted by US-Goverment (And especially the NSA) and other govermental agencies. If it could be cracked by a super computer in a couple of seconds, then it wouldn't be approved for govermental use.

Besides, there's not infinite super computers in the world, so the goverment would need a pretty good reason to use it against your computer, instead of cracking something else.

I remember a case i Brazil where the goverment tried, for 2 years, to crack a AES-256 TrueCrypt container. When they couldn't, all charges where canceled.

That was a AES-256 encrypted folder. Same encryption as LVM on top of LUKS would utilise.

I suggest you read up on AES: [http://en.wikipedia.org/wiki/Advanced_Encryption_Standard#Known_attacks](http://en.wikipedia.org/wiki/Advanced_Encryption_Standard#Known_attacks)

The only negative things I can see that there is with software encyption is:
1: A bit slower performance
2: Loose your key, loose your data
3: You can still, with physical access, format the harddrive. But you wouldn have to recover the ENTIRE encrypted partition to get any information out of it.

Please correct me if the above 3 points are wrong.

All tru, but quite simply; If someone was advanced enough to try and figure out how to bypass much simpler encryption techniques used by programs like Cryptkeeper, they could probably bypass just about anything. But anyway; Would such high-grade encryption **really** be useful for the standard computer user? The only type of people I could see trying to hack into an encrypted computer would be people like MI6, or the CIA or NSA or whatever. But unless you have committed some sort of crime, I don't see any reason why they would try to do that. If they (accidentally) do... What have you got to hide?

---

### Post by Dangertux on 2012-01-10
> **0011235813 said:**
> All tru, but quite simply; If someone was advanced enough to try and figure out how to bypass much simpler encryption techniques used by programs like Cryptkeeper, they could probably bypass just about anything. But anyway; Would such high-grade encryption **really** be useful for the standard computer user? The only type of people I could see trying to hack into an encrypted computer would be people like MI6, or the CIA or NSA or whatever. But unless you have committed some sort of crime, I don't see any reason why they would try to do that. If they (accidentally) do... What have you got to hide?

Just a heads up. While cryptkeepers default hashing (md5) is rather weak it also supports AES encryption. Note hashing and encryption are not the same, so not sure where your info is coming from.

For those interested : NSA uses both AES and SHA512, both of which are considered secure and FIPS compliant standards.

Also if you ask if "high grade" encryption is useful for the average user keep in mind that your TLS/SSL sessions with your bank, social network of choice, and email are all encrypted using AES standard.

---

### Post by MadsRC on 2012-01-10
Just to be clear, it's not only high profile govermental agencies that will try and break your encryption. All agencies, even the local police, will try if your charged with something.

you say that I would only need encryption if i commited a crime? While I understand your argument, I also see how narrow-minded that thought is. Would you also say the only reason to use, say TOR, is if your a criminal?

Do you know what the penalty in some countries are if your cought with system critical information? The current situation in some middle eastern countries would most likely result in some grave consequences if your cought with journalistic material that isn't approved by the state.

Basicly, encryption is about protection your privacy against prying eyes. Ensuring that information can be freely distributed and censorship can be circumvented (Like TOR).

Some people don't trust their goverments. And if they want to make sure that what information they have, is for their own eyes only, then they  should have the option to do a Full Disk Encryption.

But to answer your question: No, I have NOTHING to hide, but just like I don't like the idea of worldwide GPS tracking of all citizens, then I also don't like that my (and I repeat: MY) data is accessible to everyone with physical access.

Knowledge is power, knowledge about you, is power over you.

One last thing:
I think it's more convenient to do a Full Disk Encryption than using an encrypted container (Like TrueCrypt) as you would have to "manually" mount that container when you boot. With FDE you decrypt when you boot, and if you need to quickly make sure the data is inacsessible then you just need to pull the power.

I guess it all comes down to what you need encrypted. I have used TrueCrypt containers if it's only a few files I need encrypted and when there's no reason to encrypt the entire OS.

BUT if the OP wants to do a FDE then let him do so? Why he wants to do that is none of our business, and if you don't trust OP to use it only for legal purposes, then don't post an answer :P

---

### Post by 0011235813 on 2012-01-11
> **MadsRC said:**
> Just to be clear, it's not only high profile govermental agencies that will try and break your encryption. All agencies, even the local police, will try if your charged with something.

you say that I would only need encryption if i commited a crime? While I understand your argument, I also see how narrow-minded that thought is. Would you also say the only reason to use, say TOR, is if your a criminal?
*I believe you may have slightly mis-understood what I was saying- I was saying that the only kind of force who would need FDE to be stopped was probably the kind of force you shouldn't  try to protect against. Simply encrypting the necessary files would be enough to stop maybe 99% of thieves.*

Do you know what the penalty in some countries are if your cought with system critical information? The current situation in some middle eastern countries would most likely result in some grave consequences if your cought with journalistic material that isn't approved by the state.
*I doubt most people in this forum live in the Middle-east...*

Basicly, encryption is about protection your privacy against prying eyes. Ensuring that information can be freely distributed and censorship can be circumvented (Like TOR).

Some people don't trust their goverments. And if they want to make sure that what information they have, is for their own eyes only, then they  should have the option to do a Full Disk Encryption.

But to answer your question: No, I have NOTHING to hide, but just like I don't like the idea of worldwide GPS tracking of all citizens, then I also don't like that my (and I repeat: MY) data is accessible to everyone with physical access.

Knowledge is power, knowledge about you, is power over you.

One last thing:
I think it's more convenient to do a Full Disk Encryption than using an encrypted container (Like TrueCrypt) as you would have to "manually" mount that container when you boot. With FDE you decrypt when you boot, and if you need to quickly make sure the data is inacsessible then you just need to pull the power.

I guess it all comes down to what you need encrypted. I have used TrueCrypt containers if it's only a few files I need encrypted and when there's no reason to encrypt the entire OS.

BUT if the OP wants to do a FDE then let him do so? Why he wants to do that is none of our business, and if you don't trust OP to use it only for legal purposes, then don't post an answer :P*I was simply pointing out that FDE probably won't do what **they** thought it would do *

The message is written within the quote :)

---

