---
title: "dm-crypt/LUKS vs. TrueCrypt"
date: 2010-10-04
forum: Security
---

### Post by jwhendy on 2010-10-04
Hi,


I've searched far and wide and have only found a very few posts about this, and not many seem to be very recent.[1] A lot end up digressing into off topic side comments about encryption method, methods, etc.

I'm simply interested in a more basic discussion of why one would choose one of these methods over the other. What do they offer that the other does not? I'll start with what I know:

- dm-crypt/LUKS
--- included in a lot of install images already; in other words, perhaps easier to implement on a fresh install

- TrueCrypt
--- multiple encryption algorithms possible
--- plausible deniability possible via hidden volumes (though I've heard conflicting information on how well this works either 1) in general with Linux and surely 2) with a "decoy" OS)
--- Windows compatible.

As you can see... I don't know much!

For me... I have no need for Windows compatibility, though I do use OS X on a dual booting MacBook. I believe TrueCrypt woks with OS X, so that could be a bonus, though I can simply encrypt my home folder on OS X with it's own FireVault and be fine.

My setup (after wiping and starting over) will probably be like so:
- /boot on it's own primary partition
- / on it's own primary partition with logical partitions within
--- /usr, /var, /etc, /opt, and the like on a logical partition
--- /home on a logical partition

/home will surely be encrypted and I'm leaning toward encrypting the rest as well, though perhaps it's not necessary. I'm open to input there as well -- is there anything the leaks from normal application use into /var or /tmp that would make one lean toward just encrypting the whole thing?

I'm open to any thoughts. I have been using Arch Linux lately, but truly appreciate the massive and knowledgeable Ubuntu community for many questions as well as the extremely fast response time in the forums; I may start the project tonight after backing up!

One last thought -- I opened up TrueCrypt just to look at it and since I can't encrypt a whole partition without losing data... I pretty much have to encrypt from what? A live CD? This could be a drawback -- I think since TrueCrypt isn't coming on install disks, I'd have to go with an unencrypted (or dm-crypt/LUKS) root partition and then use TrueCrypt to make a container (or partition) for /home only. I can't think of another way to do this since I can't encrypt the whole disk as one entity with my dual booting situation...

Thanks for any input.

[1] Probably the most helpful discussion I've found is here: [http://www.phoronix.com/forums/showthread.php?t=24722](http://www.phoronix.com/forums/showthread.php?t=24722)

---

### Post by bodhi.zazen on 2010-10-04
Use what you like. I have not seen any "definitive" guide that has convinced me one is superior to another, just opinions.

---

### Post by rookcifer on 2010-10-04
> **jwhendy said:**
> H
- TrueCrypt
--- multiple encryption algorithms possible
--- plausible deniability possible via hidden volumes (though I've heard conflicting information on how well this works either 1) in general with Linux and surely 2) with a "decoy" OS)

Dm-crypt has all of the algorithms Truecrypt has and some Truecrypt doesn't offer.  It can use any algorithm that's built into your kernel.

Dm-crypt doesn't have "hidden volumes" but the usefulness of those are specious anyway.  (Really, if you wanted, you could create your own hidden volumes with dm-crypt.  Just create a volume then create another volume inside of it).

> One last thought -- I opened up TrueCrypt just to look at it and since I can't encrypt a whole partition without losing data... I pretty much have to encrypt from what? A live CD? This could be a drawback -- I think since TrueCrypt isn't coming on install disks, I'd have to go with an unencrypted (or dm-crypt/LUKS) root partition and then use TrueCrypt to make a container (or partition) for /home only. I can't think of another way to do this since I can't encrypt the whole disk as one entity with my dual booting situation...

TC does not offer full disk encryption for Linux, so if you want that, TC is out of the equation.  I recommend encrypting your whole disk (except for /boot of course).  You can do this by using the Ubuntu "alternate CD" which you can download from the main site.

---

### Post by jwhendy on 2010-10-04
[QUOTE=rookcifer]Dm-crypt has all of the algorithms Truecrypt has and some Truecrypt doesn't offer.  It can use any algorithm that's built into your kernel.[/quote]

Good to know!

[QUOTE=rookcifer]Dm-crypt doesn't have "hidden volumes" but the usefulness of those are specious anyway.  (Really, if you wanted, you could create your own hidden volumes with dm-crypt.  Just create a volume then create another volume inside of it).[/quote]

I have heard similar things re. the usefulness of hidden volumes... there seems to be a lot of confusion about whether a "blog of random data" will create plausible deniability or simply raise suspicion about why there is a very odd blob of data there. One thing I've not heard is whether once the outer volume is decrypted if the hidden block can be identified as "different" in any way.

In any case... is what you suggest the same as what TrueCrypt is doing? I guess, more specifically, is each creating just a "volume" (kind of like a logical partition?) inside another one? Or is this like creating an encrypted "file" and using that as a container?

Still new to this... if it's the file method, it would seem that it could be identified. This isn't horribly important to me as I can't think of many situations in which I'd need to have some sort of "decoy" partition... I think it'd be easier to just use a USB drive and trash it if I were ever worried!

[QUOTE=rookcifer]TC does not offer full disk encryption for Linux, so if you want that, TC is out of the equation.  I recommend encrypting your whole disk (except for /boot of course).  You can do this by using the Ubuntu "alternate CD" which you can download from the main site.[/QUOTE]

Good to know. I will probably have to do something a little different since I'm using OS X and dual booting. I think the easiest for me will be:

- partition 1: GUID partition table (required by OS X to be on separate partition)
- partition 2: HFS+ partition which will have an encrypted home partition
- partition 3: /boot for Linux
- partition 4: Linux partition that will use LVM to have separate partitions for / and /home (any others that should be on their own?)

I'm leaning more and more toward dm-crypt and will use that on partition 4.

Thanks for your input!

---

### Post by Soul-Sing on 2010-10-05
software comes with licenses, and truecrypt has a bad one, and is therefore discouraged on several support fora.
: [http://forums.fedoraforum.org/showthread.php?p=1397886](http://forums.fedoraforum.org/showthread.php?p=1397886)

---

### Post by jwhendy on 2010-10-05
> **leoquant said:**
> software comes with licenses, and truecrypt has a bad one, and is therefore discouraged on several support fora.
: [http://forums.fedoraforum.org/showthread.php?p=1397886](http://forums.fedoraforum.org/showthread.php?p=1397886)

I'd run into inklings about this as well. Thanks for bringing it up!

---

### Post by jwhendy on 2010-10-08
One last question... does anyone with experience with either/both note anything related to performance? I read somewhere that dm-crypt doesn't support multi-core systems. Is that the case? Elsewhere it sounded like they had implemented such functionality perhaps earlier this year but it was tough to track down a definitive statement.

Seeing as how disk encryption will require constant encrypting/decrypting on the fly... I could see this mattering. I know that TrueCrypt has such functionality.

---

### Post by rookcifer on 2010-10-09
> **jwhendy said:**
> One last question... does anyone with experience with either/both note anything related to performance? I read somewhere that dm-crypt doesn't support multi-core systems. Is that the case? Elsewhere it sounded like they had implemented such functionality perhaps earlier this year but it was tough to track down a definitive statement.

Seeing as how disk encryption will require constant encrypting/decrypting on the fly... I could see this mattering. I know that TrueCrypt has such functionality.

Not sure about dm-crypt and multi-core.  I know that on my dual-core system it only slows it down by about 5% or so.  Phoronix has done [benchmarks]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_hdd_encrypt&num=3") and their results are about the same.  It really depends on what it is you're doing, as you can see from their results.

Truecrypt now supports the new AES instruction set that Intel has put in some of their processors.  I am pretty sure the dm-crypt devs plan on implementing this (if they haven't already).

---

### Post by HermanAB on 2010-10-10
Howdy,

Years ago, I measured the slowdown of LUKS with AES256.  I installed two identical servers and compiled the kernel, then timed how long it took. It amounted to about 3%.  So nothing to worry about.

If it would make you feel better, governments and military commonly use LUKS with AES256, CBC, ESSIV and SHA256 to protect stuff up to the level of secret and above that level they may use exactly the same algorithm, but just an audited and certified version.

---

### Post by jwhendy on 2010-10-10
@HermanAB:

Very cool to know. That *is* cool to know about governments/military using this system.

I'm still kind of stuck on how exactly to setup in a useful way on a dual booting Mac/Linux setup. I use Linux so much these days I'm leaning toward using FireVault on OS X and dm-crypt/LUKS on Linux and then having some sort of shared TrueCrypt file between the two. I've gotten no answers on my post so I'm not sure if there's a better way to go about this :( --> [LINK]("http://ubuntuforums.org/showthread.php?t=1589691")

---

### Post by rookcifer on 2010-10-10
> **jwhendy said:**
> Very cool to know. That *is* cool to know about governments/military using this system.

I don't know if they actually use dm-crypt/LUKS itself, but I do know that AES has been certified for protection of data up to the SECRET level.  And if you use 256 bit keys, it has been certified for some TOP SECRET data as well.  Of course, the implementation must be cleared by NSA first (they test it and make sure it's secure), but the algorithm itself has been deemed secure.  Dm-crypt/LUKS has the option to use AES (as any good crypto software should).

> I'm still kind of stuck on how exactly to setup in a useful way on a dual booting Mac/Linux setup. I use Linux so much these days I'm leaning toward using FireVault on OS X and dm-crypt/LUKS on Linux and then having some sort of shared TrueCrypt file between the two. I've gotten no answers on my post so I'm not sure if there's a better way to go about this :( --> [LINK]("http://ubuntuforums.org/showthread.php?t=1589691")

I don't know much about OS X and FileVault, but I do dual-boot my system with Windoze 7 (don't ask).  I use full disk encryption with Linux as normal.  Dual booting should not affect using encryption.  

Is it that you want to be able to see your encrypted Linux partition from OS X?  If so, I am not sure about that.  I do know that Windows has the ability to mount dm-crypt/LUKS partitions with FreeOFTE.  Perhaps there is an OS X equivalent?

Off the top of my head, you're Truecrypt solution should work.  If you have a spare storage drive, you can just encrypt the whole thing as one big container with Truecrypt.  Then install Trucerypt on your Mac and Linux boxes and you should be able to access it from both OS's.

---

### Post by jwhendy on 2010-10-10
> **rookcifer said:**
> ...Dual booting should not affect using encryption.

Is it that you want to be able to see your encrypted Linux partition from OS X?  If so, I am not sure about that.  I do know that Windows has the ability to mount dm-crypt/LUKS partitions with FreeOFTE.  Perhaps there is an OS X equivalent?

Off the top of my head, you're Truecrypt solution should work.  If you have a spare storage drive, you can just encrypt the whole thing as one big container with Truecrypt.  Then install Trucerypt on your Mac and Linux boxes and you should be able to access it from both OS's.

Yup -- I'd like to be able to access bidirectionally if possible. Though I'm now leaning toward just keeping all my files on Linux. I currently have an 80gb hard drive in my Macbook, have about a 65gb partition for OS X and 15gb for Linux. I keep everything in my Users folder on the OS X side since I can mount HFS+ in Linux but not ext4 on OS X. That's been working great. When I backup I just do it from OS X since all that's on Linux are the temporary downloads or whatever I was working on, various config files, and applications.

Every once in a while I'll copy various configs over to the OS X partition so that I have those for reference, but really it wouldn't be anything major to reinstall Linux for me at all with this setup. I'd just have to update, reinstall everything I want and re-setup configuration files.

I'm thinking the shared TrueCrypt idea might be best. I could actually do that with my whole backup drive... Then I could get at it from either. I'll probably have to format it as HFS+ since I don't think Linux is great with NTFS and I have files bigger than 4gb which rules out Fat32.

I'm also thinking I'll make a small partition with HFS+ to use as a shared partition between the two internally as well.

By chance do you know if OS X can read extended/logical partitions made by Linux and/or vice versa? I'm limited to 4 partitions due to OS X and one of them is for EFI. Thus:

- efi
- os x
- unencrypted /boot
- linux

means I have no more. If I could mount an extended/logical partition from one or the other, I could use that as the shared partition... though perhaps I'll make it a file on the OS X side and that way I can mount it in Linux if I need to, put some files in it, and then when I reboot it'll be there. It does suck that if I want a file from the Linux side, I'll have to reboot into Linux, copy a file over, and then reboot again. ..

Thanks for the thoughts.

---

### Post by NothingToSeeHere on 2010-10-17
Well, on Linux you really can't encrypt everything with truecrypt, because Pre-Boot-Authentification is not supported on Linux. So it is true, all you can do is to encrypt your home partition with it.

One major drawback with dm-crypt is: It is NOT multithreaded. I honestly think that this is pretty embarrassing for THE built-in encryption most people use on linux/ubuntu and I really don't like it that the developers are trying make excuses for it.

1. If you don't have a really fast CPU, the CPU will be a limiting factor. The developers are pretending that everybody has Core i7 4GHz CPUs, because you really need those. A Q8300 will give you about 350 MB/s, so 1 core will give you about 90 MB/s. That is pretty damn fast! But: If you spent money on a really fast harddisk or a recent ssd  dm-crypt will limit the performance to (at most) 90 MB/s although the 3 idling cores could provide a lot of additional performance.

2. If you have a Notebook or even a Netbook you should really think if you want to apply encryption. dm-crypt on an Intel Atom will give you about 25 MB/s at the most. The Atoms are not the fastest CPUs, but they can handle 2 threads and there even are dual core Atoms (D510 gives you 4 threads), so while the Atom could easily give you 50 MB/s and maybe even more, dm-crypt will limit the throughput to 20-25 MB/s by not being multi-threaded.

Especially because fast hdds/ssds and netbooks are not rare and especially the ssds will become a bigger market, it is - to me - an absolute mystery why dm-crypt is still a single-threaded application. I would have expected it to be multi-threaded for at least 5 years now, but what I read from the developers made me wonder if it will ever be multi-threaded.

I often find myself feeling a little bit sad that there have been a lot of linux people who were like "64-bit? sure, linux had this forever now. Multithreading? Sure, linux has this forever now", but sadly, when I started with Ubuntu a couple of years ago 64-bit was a big problem with a lot of applications and multithreading was not even a bit more real in most linux software that it was on any other os.

Conclusion: 
dm-crypt will be the easiest option on ubuntu, but you should think about the possibility to only encrypt / and swap with dm-crypt and encrypt /home with truecrypt for maximal performance. (You could even write a script to mount your home parition automatically, so you would not really have more to do to use it).

---

### Post by jwhendy on 2010-10-17
@NothingToSeeHere:


Thanks for the input. That's interesting about the multi-threaded nature of the solutions being compared. I'm not sure which I'll go for, but am thinking that for the level of security I need and the fact that I dual boot OS X and Linux that encrypting /home on both might be the easiest way to go given your comments on speed as well as the road blocks I was already encountering on how to share the two. I'll keep giving it some thought.


Thanks!

---

### Post by zhaotianwu on 2010-11-10
> **rookcifer said:**
> 
TC does not offer full disk encryption for Linux, so if you want that, TC is out of the equation.  I recommend encrypting your whole disk (except for /boot of course).  You can do this by using the Ubuntu "alternate CD" which you can download from the main site.


Can you explain/provide a link to just how to proceed with full-partition encryption using "alternate CD"? I'm using a netbook and dual-booting with windows xp, and I'm going to do a fresh-install from scratch. I noticed with regular graphic installation, there is one step asking you if you wish to "encrypt home folder", is this what we are talking about or there is something else about LUKS? Any help will be highly appreciated. Thanks.

---

### Post by jwhendy on 2010-11-10
> **zhaotianwu said:**
> Can you explain/provide a link to just how to proceed with full-partition encryption using "alternate CD"? I'm using a netbook and dual-booting with windows xp, and I'm going to do a fresh-install from scratch. I noticed with regular graphic installation, there is one step asking you if you wish to "encrypt home folder", is this what we are talking about or there is something else about LUKS? Any help will be highly appreciated. Thanks.

You should see something about asking if you want full disk encryption with dm-crypt/LUKS and possibly a mention of LVM (logical volume management). Googling around should get you to some more information like this:

- [http://superuser.com/questions/33514/how-to-setup-disk-encryption-with-ubuntu](http://superuser.com/questions/33514/how-to-setup-disk-encryption-with-ubuntu)
- In case you don't have a CD drive: [http://coliena.com/blog/2010/05/how-to-install-ubuntu-10-04-on-a-netbook-with-full-disk-encryption/](http://coliena.com/blog/2010/05/how-to-install-ubuntu-10-04-on-a-netbook-with-full-disk-encryption/)
- a slightly older but very comprehensive step by step guide to full disk encryption on 8.04: [http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/](http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/)

I'm assuming this is the alternate CD being referred to (I use Arch Linux so I have never downloaded it): [LINK]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download").

Hope that helps a bit!

---

### Post by zhaotianwu on 2010-11-11
> **jwhendy said:**
> You should see something about asking if you want full disk encryption with dm-crypt/LUKS and possibly a mention of LVM (logical volume management). Googling around should get you to some more information like this:

- [http://superuser.com/questions/33514/how-to-setup-disk-encryption-with-ubuntu](http://superuser.com/questions/33514/how-to-setup-disk-encryption-with-ubuntu)
- In case you don't have a CD drive: [http://coliena.com/blog/2010/05/how-to-install-ubuntu-10-04-on-a-netbook-with-full-disk-encryption/](http://coliena.com/blog/2010/05/how-to-install-ubuntu-10-04-on-a-netbook-with-full-disk-encryption/)
- a slightly older but very comprehensive step by step guide to full disk encryption on 8.04: [http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/](http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/)

I'm assuming this is the alternate CD being referred to (I use Arch Linux so I have never downloaded it): [LINK]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download").

Hope that helps a bit!

Thank you very much, your links are very helpful!

---

### Post by zhaotianwu on 2010-11-11
> **jwhendy said:**
> You should see something about asking if you want full disk encryption with dm-crypt/LUKS and possibly a mention of LVM (logical volume management). Googling around should get you to some more information like this:

- [http://superuser.com/questions/33514/how-to-setup-disk-encryption-with-ubuntu](http://superuser.com/questions/33514/how-to-setup-disk-encryption-with-ubuntu)
- In case you don't have a CD drive: [http://coliena.com/blog/2010/05/how-to-install-ubuntu-10-04-on-a-netbook-with-full-disk-encryption/](http://coliena.com/blog/2010/05/how-to-install-ubuntu-10-04-on-a-netbook-with-full-disk-encryption/)
- a slightly older but very comprehensive step by step guide to full disk encryption on 8.04: [http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/](http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/)

I'm assuming this is the alternate CD being referred to (I use Arch Linux so I have never downloaded it): [LINK]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download").

Hope that helps a bit!

Just a follow-up question. I'm no expert but the links you provided seem all deal with Ubuntu Only, and I'm going to dual-boot with windows xp being the first primary partition, is it going to be a problem for implementing LUKS full disk encryption? Actually I just need to protect my Linux side, windows xp side doesn't need to be encrypted at all. Could you please briefly confirm if dual-boot ok with LUKS full disk encryption or not? Many thanks.

---

### Post by bodhi.zazen on 2010-11-11
> **zhaotianwu said:**
> Just a follow-up question. I'm no expert but the links you provided seem all deal with Ubuntu Only, and I'm going to dual-boot with windows xp being the first primary partition, is it going to be a problem for implementing LUKS full disk encryption? Actually I just need to protect my Linux side, windows xp side doesn't need to be encrypted at all. Could you please briefly confirm if dual-boot ok with LUKS full disk encryption or not? Many thanks.

You can dual boot with windows and Linux (Ubuntu) and use LUKS for your Ubuntu partition, no problem.

---

### Post by zhaotianwu on 2010-11-12
> **bodhi.zazen said:**
> You can dual boot with windows and Linux (Ubuntu) and use LUKS for your Ubuntu partition, no problem.


With dual-booting, can I encrypt linux swap partition as well? I've heard that that partition often leads to data leak.

Another question, am I correct in saying that LUKS can only encrypt a LVM? At least this is what I've read from the links you provided.:P What is that?

---

### Post by Fafler on 2010-11-12
The easiest way to do this is to install from the alternate CD and use encrypted LVM. This automatically encrypts / and swap, leaving only a unencrypted boot partition.

LUKS can encrypt anything, i think. I have used LUKS on partitions, raw devices, RAID arrays and files setup as loopback devices.

LUKS/dm-crypt is single threaded. My own way to overcome this is a RAID array with the individual drives encrypted. Now i have 3 threads and much better performance on my fileserver.

I use encrypted LVM on all my machines, laptops and desktop, and i don't find the speed penalty that bad.

---

### Post by zhaotianwu on 2010-11-12
> **Fafler said:**
> The easiest way to do this is to install from the alternate CD and use encrypted LVM. This automatically encrypts / and swap, leaving only a unencrypted boot partition.

LUKS can encrypt anything, i think. I have used LUKS on partitions, raw devices, RAID arrays and files setup as loopback devices.

LUKS/dm-crypt is single threaded. My own way to overcome this is a RAID array with the individual drives encrypted. Now i have 3 threads and much better performance on my fileserver.

I use encrypted LVM on all my machines, laptops and desktop, and i don't find the speed penalty that bad.


Can I go without LVM? I'm a home user and LVM doesn't seem to be extremely useful. Can I still take advantage of LUKS full encryption and do it automatically using the alternate CD?

---

### Post by Fafler on 2010-11-12
Why? It works. Everything is setup automatically. Every time you boot, you just enter your password. Apart from that, it works like every other Ubuntu computer out there.

Encrypted LVM it more or less the same. Is uses LUKS and dm-crypt and puts a LVM on top to conceal the partitions inside. Does this make sense?

```

Raw disk -> Partition 1-> /boot
        |-> Partition 2 -> dm-crypt -> LVM -> Partition 1 -> /
                                           |-> Partition 2 -> Swap
```

---

### Post by bodhi.zazen on 2010-11-12
> **zhaotianwu said:**
> Can I go without LVM? I'm a home user and LVM doesn't seem to be extremely useful. Can I still take advantage of LUKS full encryption and do it automatically using the alternate CD?

You can configure your partitions however you choose and you will be able to dual boot. The partitioning layout does not affect your ability to boot Windows.

As far as LVM, it is not necessary, but it makes using LUKS much easier. If you do not go with the defaults you will need to manually configure your LUKS partitions and setup. This is possible, but you will need to know what you are doing or be prepared to do some reading.

---

### Post by rookcifer on 2010-11-12
> **zhaotianwu said:**
> Can I go without LVM? I'm a home user and LVM doesn't seem to be extremely useful. Can I still take advantage of LUKS full encryption and do it automatically using the alternate CD?

You have to use LVM if you want to use a single password for all the partitions.  Otherwise you'll end up having to enter a separate password for / and /home, etc.

---

