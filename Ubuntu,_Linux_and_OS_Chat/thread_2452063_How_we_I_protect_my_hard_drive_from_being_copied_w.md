---
title: "How we I protect my hard drive from being copied without my consent?"
date: 2020-10-15
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2020-10-15
A person here in the United State allegedly had a laptop in the repair shop and the data from the laptop is being used against him.

Now, this worries me as a Linux user and as a regular citizen who should have the right to privacy, and as such, I don't want snoopy computer shop technicians doing the same to me in the future when I have to bring my laptop for repairs.

Are there ways to protect myself from this? Ways to protect my data from being copied off my laptop without my consent?

---

### Post by CelticWarrior on 2020-10-15
Short answer: Full drive encryption.

---

### Post by ardouronerous on 2020-10-15
> **CelticWarrior said:**
> Short answer: Full drive encryption.

Is that the same encryption option I get when I install Ubuntu?

---

### Post by kurt18947 on 2020-10-15
If it's practical, could you remove the hard drive before taking it to the shop? Some people, when they buy a new PC also buy a spare hard drive. Maybe set up the new PC with the original hard drive then remove the original hard drive and install the extra. Install any O.S.(s) you like. If the PC needs to be shipped out for repair re-install the original hard drive. That wouldn't work if the hard drive was the issue but if the hard drive were the problem I would probably image the original hard drive if it were readable - maybe a couple images - then wipe the hard drive before taking it to the shop. As far as protecting against the machine being stolen, full drive encryption as CelticWarrior says.

---

### Post by ardouronerous on 2020-10-15
> **kurt18947 said:**
> If it's practical, could you remove the hard drive before taking it to the shop? Some people, when they buy a new PC also buy a spare hard drive. Maybe set up the new PC with the original hard drive then remove the original hard drive and install the extra. Install any O.S.(s) you like.

The option of removing my SSD before bringing it to the repair shop did cross my mind.

> **kurt18947 said:**
> That wouldn't work if the hard drive was the issue but if the hard drive were the problem I would probably image the original hard drive if it were readable - maybe a couple images - then wipe the hard drive before taking it to the shop.

But Ubuntu would alert me if there was a problem with my SSD right? And I've read somewhere that, if the problem is the drive, it usually better to buy a new drive instead.

> **kurt18947 said:**
> As far as protecting against the machine being stolen, full drive encryption as CelticWarrior says.

Is that the same option presented to me when I install Ubuntu? When I install Ubuntu, there's an option to encrypt, is that the same thing? I'm upgrading to 20.04 next month.

[IMG]https://ubuntucommunity.s3.dualstack.us-east-2.amazonaws.com/original/2X/4/46e9947d7b4ad3e96487d81cf61c327485d56b5a.png[/IMG]

---

### Post by mastablasta on 2020-10-16
i believe the encrypt option will encrypt home (your data) not full drive (so OS is not encrypted). i could be wrong.

full drive encryption will offer some protection. 

know that physical access is access. latest GPU for example are quite fast in brute force attacks. to get the data one would image the drive and then attempt to crack the encryption. long passwords or better yet keys separated from drive are a good idea in these cases. they will make it much hardware for hackers.

at the same time be aware that when you encrypt the data you need to have good backups. any small disk error (that can usually be easily resolved on non encrypted file system) and your data is gone.

IMO on laptop the encryption is still good thing to have. especially, if you use after sales service.

---

### Post by metacell on 2020-10-16
> **ardouronerous said:**
> Is that the same option presented to me when I install Ubuntu? When I install Ubuntu, there's an option to encrypt, is that the same thing? I'm upgrading to 20.04 next month.
Yes. But I think you need to do a clean install to be able to use the encryption.

> **mastablasta said:**
> i believe the encrypt option will encrypt home (your data) not full drive (so OS is not encrypted). i could be wrong.
Ubuntu removed home folder encryption (ecryptfs), in favour of full disk encryption (LUKS), due to security concerns. So if he's installing 20.04, he'll be fine.

> **mastablasta said:**
>  at the same time be aware that when you encrypt the data you need to have good backups. any small disk error (that can usually be easily resolved on non encrypted file system) and your data is gone.
A very good idea. I have two encrypted removable drives, and use [FONT=courier new]rsync[/FONT] to backup everything important to them.

---

### Post by scorp123 on 2020-10-16
> **ardouronerous said:**
> Are there ways to protect myself from this? Ways to protect my data from being copied off my laptop without my consent?

I do all computer repairs myself. YouTube can tell me how if I happen to not know something.

---

### Post by sdsurfer on 2020-10-16
As mentioned, drive encryption is the answer. I have a Windows 10 drive I inherited that is encrypted. Can't access it, can't format it, it is basically a useless block without the encryption password.

The "bad" (ish) news is, you can only do this as it's formatted, it requires a complete erase of the drive in any OS.

---

### Post by T6&amp;sfpER35% on 2020-10-16
another thought , take it to a reputable repair shop

---

### Post by Shibblet on 2020-10-16
My Bullet List...

Repair shops may need to access the OS in order to fix certain problems.
Don't use Windows.
Keep any personal information on an external hard drive.
Use Full drive encryption.

---

### Post by Shibblet on 2020-10-16
> **ardouronerous said:**
> A person here in the United State allegedly had a laptop in the repair shop and the data from the laptop is being used against him.

I mean... that sucks, and all.  Its his personal information.  But you have to realize that if certain things are found on the Hard Drive during repair, they may have no choice but to contact the police.
In the United States, this can turn the employee into a witness, and then they become liable for what they've seen.  In order to keep themselves out of it, they have to report it.

I don't want to speculate what the data was, but there are many ways for it to "pop up."  If someone has their wallpaper set to "gallery" and one of their inappropriate pictures (i mean illegal) pops up as the next wallpaper in the queue...  You see where I am going with this?

---

### Post by makitso on 2020-10-16
> [COLOR=#000000]Now, this worries me as a Linux user and as a regular citizen who should have the right to privacy, and as such, I don't want snoopy computer shop technicians doing the same to me in the future when I have to bring my laptop for repairs.[/COLOR]

[COLOR=#000000]Are there ways to protect myself from this? Ways to protect my data from being copied off my laptop without my consent?[/COLOR]

Personally, I can't think of any computer shop that would be qualified to work on linux -- none in my area do.
If you have a dual-boot system e.g. win10 and ubuntu, and your problems are on the windows side, they can't directly see the linux partitions.

---

### Post by sdsurfer on 2020-10-19
> I don't want to speculate what the data was, but there are many ways for it to "pop up."

I am guessing the "person" in question is involved in politics and the story is in all the news, that is all I will say.

---

### Post by metacell on 2020-10-20
There are many legitimate reasons to keep your data private.

For example, you may have business secrets that rival companies could use.

You may have content that is socially embarrassing, but completely legal.

Also, you can always find *something* incriminating if you know enough about a person. That's why USA has the self-incriminating clause in the fifth amendment. Being compelled to witness against yourself is considered to give the prosecution such a large advantage, it increases the risk of wrongful convictions.

---

### Post by mastablasta on 2020-10-20
> **metacell said:**
> 
Also, you can always find *something* incriminating if you know enough about a person. That's why USA has the self-incriminating clause in the fifth amendment. Being compelled to witness against yourself is considered to give the prosecution such a large advantage, it increases the risk of wrongful convictions.

which reminds me of old dos game Floor 13. the more you "drill" into people and investigate them, the more bizare things become. sometimes you find something, other times it's just embarrassing for the person.

---

