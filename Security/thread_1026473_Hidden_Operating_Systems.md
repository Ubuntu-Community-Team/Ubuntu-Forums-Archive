---
title: "Hidden Operating Systems"
date: 2008-12-31
forum: Security
---

### Post by Tubes6al4v on 2008-12-31
Hey Guys,

   I have played around with truecrypt's hidden partition and OS features and have found the idea quite interesting. In order to protect myself from prying eyes (and no, I don't trust government officials to protect me, I can do it myself) I thought it would be interesting to set up a full level of deniability. I have a few questions regarding Hidden OSs:

- Can Truecrypt's boot manager give an indication of a hidden OS? Obviously if your decoy system is not encrypted, then it becomes quite obvious.
- Is there a way to create a hidden Linux OS? I know truecrypt does not do this, but perhaps something else would.
- As long as the security precautions adressed on the truecrypt site are used, are there any other security flaws? Note: the idea is to avoid the detection of the system as well as access.
- Any oter thoughts on the subject?


[http://www.truecrypt.org/docs/?s=hidden-os](http://www.truecrypt.org/docs/?s=hidden-os)

---

### Post by Dave_Connor on 2008-12-31
If you want to hide your OS on a portable computer (airport sweeps, etc) you could have GRUB not read your main os partition and only read from a decoy with some documents and pictures, etc. Then when your in the location you wanted you can boot into a live cd and mount your hardrive and repair grub to boot your main os. I prefer just to remove all un-important data and then just transfer over everything with an rsync script through ssh.

---

### Post by Tubes6al4v on 2008-12-31
Removing grub does not really hide the data. If they were to see another partition (or in this case a drive) that was not accessable from the operating system, that would cause suspicion. Likely they would remove the drive and examine it on their machine, or use a live cd of their own to boot it. 

Unlike the Airport screaning thread, I want this to be a perminant solution that I do not need to do any prepare the drive any time I move it. I do not have anything I believe to be illegal, but I would like to keep my data private from all eyes. So it needs to present plausible deniability if the computer and/or drive were taken from my home. This is where the truely hidden (not simply not on the boot menu) system would prevail.

---

### Post by bumanie on 2008-12-31
This may help - it's from the super [grubdisk wiki]("http://www.supergrubdisk.org/wiki/HideLinuxBoot#Resources").

---

### Post by Tubes6al4v on 2009-01-08
Hmm, so I seem unable to convey this. If someone got ahold of my computer and pulled the drive, they could plug it into another computer (or just run gparted from a live cd) and see another partition there. Simply by that, they could prove that there is something there and attempt to compell me to reveal the password. What I would like is a way to make it virtually impossible to prove the existance of the OS. Just like Truecrypt can do (but I can't seem to get working) with Windows. Dig?

---

### Post by LexLuthor08 on 2009-01-08
I am really a noob but I fully understand your request. I wonder why the linux geeks haven't come up with a solution for this yet.

I think this is a major drawback for linux in terms of security. Having a non-hidden encrypted OS is virtually useless, since in most countries you will render yourself liable to prosecution if they find an encrypted volume and you refuse to provide the key.

Anyway, I will not rest until I find a solution, but I cannot code anything by myself.

---

### Post by Dr Small on 2009-01-08
I too understand what you want to do, but know of no options to do it.

---

### Post by bodhi.zazen on 2009-01-08
> **LexLuthor08 said:**
> I am really a noob but I fully understand your request. I wonder why the linux geeks haven't come up with a solution for this yet.

I think this is a major drawback for linux in terms of security. Having a non-hidden encrypted OS is virtually useless, since in most countries you will render yourself liable to prosecution if they find an encrypted volume and you refuse to provide the key.

Anyway, I will not rest until I find a solution, but I cannot code anything by myself.

It is an interesting question, how would you hide an encrypted OS ? The partition must show up somehow as even if it is encrypted the hard drive space is not all zeros.

If someone pulls your hard drive they can analyze the "data" and the presence of encrypted data would be obvious.

---

### Post by LexLuthor08 on 2009-01-09
I am no expert, but it sais on the truecrypt site: > It is **impossible** to prove that a hidden TrueCrypt volume exists (provided that certain guidelines are followed; for more information, see the section Hidden Volume) and, therefore, it is impossible to prove that a hidden operating system exists. 

Also the commercial software drivecrypt sais it it impossible to prove, with their method.


I think because the hidden volume takes the free space inside a normal true crypt volume (which is always filled with random data), it cannot be distinguished from this random data.

---

### Post by Tubes6al4v on 2009-01-09
The idea is that they can see the encrypted partition. They could even force you to reveal the password to the outer "container" which would show up as some semi-sensitive data (photos of your secretary, etc) and a bunch of random bits afterward. You can plausibly say the random bits are from overwriting a previous partition or system with random bits (for security). When in actuality, the end of the partition contains a set of files that is encrypted with another key and/or algorithm. 

As the Truecrypt information claims, it is all about plausible denyability. It may be that you need to convice whomever it is (some government your spying on, nosey friends, suspecting wife, etc) beyond a reasonable doubt that there is nothing there. This has been demonstrated on linux as proof of concept, and can be done with windows (maybe mine didn't work because it is Vista 64 and HP laptops are notorious for not supporting unusual ideas).


On a similar note, I was just thinking today that it might be interesting to have a hidden OS on a live cd. Just for fun really. And maybe it would be possible to create a set of configuration files and programs that load to ram when booting from the live cd. Depending on what password you enter, you could boot into different environments (i.e. one with Tor, one without for going into china ;)   )

---

### Post by halovivek on 2009-01-09
> **bumanie said:**
> This may help - it's from the super [grubdisk wiki]("http://www.supergrubdisk.org/wiki/HideLinuxBoot#Resources").

Ubuntu attracts Human Beings - Windows attracts viruses and worms 
nice quote

---

### Post by nanamin on 2009-10-24
I think it's unfortunate nobody has a solution for this. I'm currently in a similar boat -- I can't find a way to do a system encryption of ubuntu and want plausible deniability (thus just encrypting /home, /swap, and /tmp isn't enough). I was thinking about installing Windows 7, doing a full system encryption with pre-boot auth, and then running Ubuntu as a hidden operating system, but I'm not sure if this is possible.

Any new insights?

---

### Post by lisati on 2009-10-24
Opinion: I don't think it's possible to completely hide data/os/partition etc on a disk. It will be there no matter what you do and there will usually be some kind of clue that *something* is there. 

I have a picture in my head of some kind of super-duper data compression which, with the help of some kind of encryption, might help things a little.

---

### Post by bodhi.zazen on 2009-10-24
> **nanamin said:**
> I think it's unfortunate nobody has a solution for this. I'm currently in a similar boat -- I can't find a way to do a system encryption of ubuntu and want plausible deniability (thus just encrypting /home, /swap, and /tmp isn't enough). I was thinking about installing Windows 7, doing a full system encryption with pre-boot auth, and then running Ubuntu as a hidden operating system, but I'm not sure if this is possible.

Any new insights?

I think this says it all:



[IMG]http://imgs.xkcd.com/comics/security.png[/IMG]

---

### Post by __p1n__ on 2009-10-25
Forget truecrypt and grub, I can think of 2 approaches that would befuddle the slack-jawed droolers at the airport:

1. Use netbsd as a dom0 and keep all your real domu images as lvm blocks.

2. Use any 'nix type o/s and modify the vfs driver to store meaningful data in the slack space at the end of each cluster. 

These approaches would not however defeat a forensic sector analysis.

---

### Post by shaggy999 on 2009-10-25
You really need to decide who your "adversary" is. If it's the government or a major corporation and you think they have bucketloads of money to throw at you -- you're screwed, hidden OS or not. Even if you had an encrypted OS hidden away all they have to do is modify the bootloader on your system to log all the keystrokes to a file and then give the system back to you.

If you're worried about losing private data if lost or stolen, or if you generally don't want people to stumble across your private data here's what I did:

1) Just to ensure general security, I installed the OS on an encrypted partition with no swap

2) Set up /home, /tmp, /var/log, etc to be mounted to tmpfs. You could do this through fstab, but I didn't want to place it there and also you can't specify that /home goes to /dev/shm/home and tmp to /dev/shm/tmp because anything inside of /dev/shm disappears on shutdown, so I needed a way to create folders to mount inside /dev/shm on bootup. So what I did was created a bootup script that creates folders inside /dev/shm and then mounts /home, /tmp, and /var/log using unionfs to subfolders of /dev/shm.

3) I then realized that inside this same script I could do a check for a particular USB drive (this changed to an SD card as the laptop in question had a built-in SDHC card reader). If that drive was present I could mount it and copy all the files over to my user's directory before I login.

4) Later I created a script that hooks into the logout function of gnome that rsyncs files back to that usb drive if it's present.

5) Personal files that are critically important go into a truecrypt partition on said SD card.


End result:

1) Noone can boot the system unless they have the password.
2) If they do get access to the system they won't find anything because the system is "sterilized" to the best of my ability.
3) All my personal data is on an external SDHC card. The system will boot just fine without it plugged in. So if I go through airport security I can just boot the system and nobody would be the wiser. I suggest you check out the payrate for TSA agents sometime how they could hire someone with l33t hax0r skills for such a low payrate.
4) All of my personal data can be carried seperately on an SDHC or even a mini-SDHC card. Have you seen how tiny those mini-SDHC cards are? I could think of a MILLION places where I could hide one of those if necessary.

If you want to make things even extra difficult: Put the bootloader and /boot directory on a seperate USB key. The end result is that the system is completely unbootable without the USB key and it looks like you have just one partition that's unreadable. You can easily come up with some excuse like "I did so and so and now my hard drive won't boot" and generally act like a newbie to computers. You WILL get flagged by the border guards, though and they will probably image your computer. But what does that matter since all your data is hidden on a mini-SDHC card that you hid in your shoe?


Also +1 XKCD comic

---

### Post by cprofitt on 2009-10-25
It is an interesting theory...

The real 'trick' here, despite all the fancy technology, is to make someone think that they are seeing the 'real data' when they are seeing the 'cover' data.

Its an interesting concept, but I think that one the 'trick' is known there is a way to 'expose' it.

As others have said... casual inspection by corporate IT or airport security will likely be fooled, but a well funded targeted attempt to get your data... not so much.

---

### Post by f1r3br4nd on 2011-07-09
All said and done, though, it's pretty lame that Windows users have hidden OS and decoy hidden OS capability with TrueCrypt and we 1337 hax0rs don't. 

It's also a lame decision on TrueCrypt's part to only permit one level of hidden partitions. If they could have one level, why the hell can't they have an arbitrary number of levels and thus offer REAL plausible deniability. As it is, with just one level of hidden partitions, anybody who has a clue will demand both passwords from a TC user.

---

### Post by CharlesA on 2011-07-10
Nice res.

Thread closed.

---

