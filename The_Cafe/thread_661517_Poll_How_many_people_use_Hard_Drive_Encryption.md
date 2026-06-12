---
title: "Poll: How many people use Hard Drive Encryption?"
date: 2008-01-08
forum: The Cafe
---

### Post by AegisTalons on 2008-01-08
I was reading a [New York Times Article]("http://www.nytimes.com/2008/01/07/us/07bar.html?ex=1357448400&en=1d8bcaa757f2bde9&ei=5124&partner=digg&exprod=digg"), and I was thinking about the full encryption of the hard drive. Disregarding whether it is legal for the government to go through one's computer at the border, even though normally they would need a warrant to see a computer's content in someone's house. 

I know about SeaHorse, TrueCrypt, and cryptsetup as good open source encryption program.

How many people in the Linux community run encryption and what do you run encryption on (email, certain files,entire hard drive) and why?

---

### Post by p_quarles on 2008-01-08
I use cryptsetup + losetup for sensitive information.

---

### Post by Tenken on 2008-01-08
I use the FireGPG plugin for email, and SeaHorse for hdd files.

---

### Post by AegisTalons on 2008-01-08
I was more interested on why you run encryption? Why do you decide to encrypt your email and files on your computer? Do you have any issues or slowdowns running encryption versus not running encrpytion? As for email encrpytion, do your contacts all run encryption also? Did they have encrpytion before you contacted them or as a result of you running encryption?

---

### Post by p_quarles on 2008-01-08
I don't encrypt e-mail, since I never use that for anything even vaguely private.

I encrypt parts of my hard drive, though, because I run some public servers. Even though I'm relatively confident about the security measures I've taken, I still don't want anyone smarter than me gaining access to my personal info.

---

### Post by AegisTalons on 2008-01-08
As a side question, this was the first poll I created on ever on a forum. What do you guys think?

---

### Post by hyper_ch on 2008-01-08
my system is fully encrypted as I have sensitive data on it.

---

### Post by insane_alien on 2008-01-08
encryption of certain files that could be dangerous if someone else got their hands on them but thats about it. only 3MB is encrypted. i can't be bothered with the overhead of ful disk encryption to be honest.

---

### Post by nocturn on 2008-01-08
> **hyper_ch said:**
> my system is fully encrypted as I have sensitive data on it.

What program did you use for this?  I'm contemplating doing the same.

---

### Post by hyper_ch on 2008-01-08
dm_crypt / luks --> if you install gutsy from the alternate cd you can directly fully encrypt your system... otherwise you can do that manually afterwards - but that requires time.

---

### Post by 50words on 2008-01-08
I use TrueCrypt containers ("crypts") for my business and personal files. About 5 GB of files in two 5GB containers. My clients' information is confidential, and I believe that personal data on anything that is portable should be encrypted. Not to do so is just reckless.

Plus, TrueCrypt containers are nice and portable, and it is easy to make encrypted backups. If you encrypt on your drive, but do not encrypt backups, then there is not much point in encrypting.

I don't encrypt e-mail. I have not looked into it, but anything I use would have to be able to be decrypted without additional software or steps, or my clients will never bother to read it. I do require clients to use a personal e-mail address if they want to communicate with me, since they have little or no privacy interest in communications through a work e-mail address.

---

### Post by wieman01 on 2008-01-08
**Truecrypt **for encryption of personal files. **Enigmail** (Thunderbird add-on) for encrypted email correspondence whenever possible. 

And **WPA2 (AES)** for wireless networking. ;-)

---

### Post by hyper_ch on 2008-01-08
50words: You should also encrypt swap in that case :)

---

### Post by Tristam Green on 2008-01-08
We use Pointsec/Checkpoint at our business for full-HD encryption for theft-deterrent purposes.

On my Linux machine, though, I use none, and see no reason to.  I change my user password regularly and the laptop doesn't leave my side.  not that anything **important** is stored locally anyway :)

---

### Post by AegisTalons on 2008-01-08
Has anyone noticed any slowdowns between a computer running fully hard drive encryption and one with out? Also, for a computer that has full HD encryption, after you turn it on and after the BIOS POST screen, can you describe the load process? Does the encryption program take over right after the GRUB screen? Does it ask for your passphrase before it would load Ubuntu or after like you are logging in? I know it differs from program to program, but just the gist.

Also I understand encryption if you are an employee or if you have sensitive information on your laptop, like client information. I'm a college student and the only things that I work on my laptop are class projects and papers. I do not seen these as sensitive enough documents. Let me know what you guys think.

---

### Post by isparkes on 2008-01-08
Most things open, 1GB and 200MB of fairly and very sensitive information, using AES256 loopback devices in container files.

Looking to move over to dm_crypt/luks when I get around to it.

---

### Post by vermoos on 2008-01-08
After getting my laptop stolen in a cafe, and then *returned* several days later, I have started using encfs to encrypt important work, and gnupg to encrypt my passwords.

I still don't know what the hell I am doing though...

---

### Post by Biochem on 2008-01-08
I use Encfs for folder encryption of financial data and seahorse for unregular sensitive research info. I don't encrypt email since I don't send sensitive information by email and and nobody use it anyway at the receiving end

---

### Post by hyper_ch on 2008-01-08
> **AegisTalons said:**
> Has anyone noticed any slowdowns between a computer running fully hard drive encryption and one with out?
Only when reading/writing lots of data... normal office use won't make any difference (except if you're on a really old computer and have little ram and a cpu less than 1ghz....)

> **AegisTalons said:**
> Also, for a computer that has full HD encryption, after you turn it on and after the BIOS POST screen, can you describe the load process? Does the encryption program take over right after the GRUB screen?
Well, with luks/dm_crypt on a fully encrypted system you will have the /boot partition unencrypted. Linux needs to load first the kernel and encryption modules so that it actually can "uncrypt" your other stuff. You will get to the GRUB screen and then after selecting Linux you'll see the Ubuntu splash screen and in there it will ask for your password(s).

> **AegisTalons said:**
> Does it ask for your passphrase before it would load Ubuntu or after like you are logging in? I know it differs from program to program, but just the gist.
It will ask your password ones it needs to load other stuff than from your /boot partition.

> **AegisTalons said:**
> Also I understand encryption if you are an employee or if you have sensitive information on your laptop, like client information. I'm a college student and the only things that I work on my laptop are class projects and papers. I do not seen these as sensitive enough documents. Let me know what you guys think.
It's up to you if and what you want to encrypt. E.g. you might just be a student with not much sensitive information. But the websites you visit, the bookmarks you got etc. can tell a lot about you... pictures of you, your family and friends, your gf/bf..... it's your privacy that you don't protect... you don't have to do it but you can if you want...

---

### Post by 50words on 2008-01-08
> **hyper_ch said:**
> 50words: You should also encrypt swap in that case :)

No need. I always unmount my containers before putting the laptop on standby or leaving it alone, which removes all encrypted data from memory and swap.

---

### Post by 50words on 2008-01-08
> **AegisTalons said:**
> Also I understand encryption if you are an employee or if you have sensitive information on your laptop, like client information. I'm a college student and the only things that I work on my laptop are class projects and papers. I do not seen these as sensitive enough documents. Let me know what you guys think.

I also encrypt my personal files, which include financial information (like my Moneydance and GnuCash files), letters regarding various matters, scans of important documents, etc.

---

### Post by capink on 2008-01-08
I don't get the point of encrypting the whole HD. It is enough to encrypt the partitions containing private data. But encrypting the root partition? what is the point?

Also I would imagine that encrypting drives using truecrypt is good choice since it enable you to access it from windows too.

---

### Post by Polygon on 2008-01-08
if someone steals your laptop and you have potential personal information, like credit card numbers, registration emails from a bunch of sites, etc etc, then your data is safe.

---

### Post by hyper_ch on 2008-01-08
> **capink said:**
> I don't get the point of encrypting the whole HD. It is enough to encrypt the partitions containing private data. But encrypting the root partition? what is the point?

You don't encrypt your SWAP?

---

### Post by AegisTalons on 2008-01-09
What exactly are "containers" that you guys have referenced earlier? Also why would you encrypt your swap partition? Do you need to setup encryption when you are setting up Ubuntu or can you do it after?

I'm running a dual boot system XP and Ubuntu. I need XP for a few programs that don't run in Ubuntu or under Wine. So if I run software to encrypt the HD, which partitions would I encrypt: /root, /home, swap, XP?

As for email encryption, how do you get other people to run encryption so it actually is effective communication?

---

### Post by hyper_ch on 2008-01-09
well, think of containers as created large files that are encrypted... once "uncrypted" you can store other files in there...  if you then unmount it you'll only see the encrypted container again..

well, swap is a partition and stuff that is put to swap, will be written to that partition... it may not be kept in momery but as long as the physical blocks aren't overwritten again, the data is still there.

You can encrypt your system also afterwards. What you want to encrypt is up to you. If you do want to encrypt, then it's also good to encrypt swap.

There's not automated encryption for email as it normally works on public/private key. If you want to encrypt an email to somebody, you will need to get this person's public key. With that you can then encrypt the message and he can, with his private key decrypt it.

---

### Post by AegisTalons on 2008-01-09
So if I have my /home partition, I would have to create a "container" on the /home partition and encrypt it. I place data I want to keep encrypted into this "container". Do you have to actually mount it or do you have it mount automatically when Ubuntu loads, or is that program specific?

As for the email, I understand the ideas with the encryption with the public and private keys but my question is if the people that you communicate with do not use encryption, how do you convince them to run encryption?

---

### Post by hyper_ch on 2008-01-09
well, you either encrypt a full partition - which can then be made usable during boot - or you use some diskspace, create a file as big as you want the desired containter to be and then you have a containter that you could transfer to a usb pen drive for example and within that container you store the files.

If you want to encrypt an essential part of your linux files system you'll have to create a whole partition for encryption (like for the /home folder)... well, you could also have a default /home and then once booted use a containter that will be mounted there... I think there's somewhere a howto here.

Well, that's up to you on how you convince them to use encryption. I say it's a matter of privacy. It's not hard to encrypt - once properly setup.

---

### Post by 50words on 2008-01-09
The TrueCrypt website will answer most of your questions. A TrueCrypt container is just a file that you can mount as if it were a drive (in Windows) or a folder, just like you would mount anything else in Linux.

I prefer containers because you can back them up in encrypted form just by copying the unmounted container file. If you encrypt a full partition, you would have to use PING or some other imager to get an encrypted backup, or else also encrypt your backup drive, which gets slow and needlessly complicated.

Containers are just more versatile, in my opinion.

---

### Post by Xbehave on 2008-01-09
> **capink said:**
> I don't get the point of encrypting the whole HD. It is enough to encrypt the partitions containing private data. But encrypting the root partition? what is the point?

Also I would imagine that encrypting drives using truecrypt is good choice since it enable you to access it from windows too.
By encrypting root i know my root is the same as it was last time i used it (although since ive managed to block liveCD attacks i suppose i dont need it on my laptop but too late now).
By encrypting /tmp and swap i keep them safe at no cost (ubuntu hibernation decides to log me out so with kde im up and running faster from a clean boot)
im not sure why i encrypt home 

I suppose all my encryption is just because its easy and this way if i ever do have sensitive data i dont need to do anything, and if my laptops stolen without my password its a brick and i cant lose any private data!

---

### Post by hyper_ch on 2008-01-09
you can also unencrypt drives automatically through a script to make backups.

And as for encrypting the whole filesystem. Don't forget the logs of programs, don't forget /temp folder... there could also be sensitive data in it.... for some it's even essential that others won't know what's installed....

either you know all you want to encrypt and you encrypt just that or take the "lazy" route and encrypt everything.

---

### Post by Polygon on 2008-01-09
> **hyper_ch said:**
> you can also unencrypt drives automatically through a script to make backups.

And as for encrypting the whole filesystem. Don't forget the logs of programs, don't forget /temp folder... there could also be sensitive data in it.... for some it's even essential that others won't know what's installed....

either you know all you want to encrypt and you encrypt just that or take the "lazy" route and encrypt everything.

its really just easier to encrypt the whole filesystem, except for /boot which the computer needs to actually start linux.

---

### Post by zugu on 2008-01-09
TrueCrypt is my friend.

---

### Post by AegisTalons on 2008-01-09
Great response from the community like always. I'm going to look into at least starting off with Enigmail between my family and friends. I'll read up some more on TrueCrypt.

---

### Post by Palmyra on 2008-01-09
I use encryption, but your poll does not have an option for me.  I encrypt a particular partition on my external hard drive (I don't encrypt email, and "certain" files).

---

### Post by tact on 2008-01-09
> **capink said:**
> I don't get the point of encrypting the whole HD. It is enough to encrypt the partitions containing private data. But encrypting the root partition? what is the point?


1.  The data you place in truecrypt type containers, or have stored in encrypted file systems like encfs, those things you see a reason to deliberately protect - are not the only places where copies of those things may be found (look in /tmp for example).   

2.  If you use a journalling file system like the default ext3 - perhaps large or complete portions of the data you wish to protect are laying around your HDD - perhaps "deleted" after writing to disk - but still recoverable.

3.  There is a LOT of personal info to be gleaned from other sources that perhaps you dont think about deliberately protecting in encrypted containers or encrypted file systems - like your browser history, recently used files records, etc...

Saying that this or that system (like truecrypt?) deletes all stuff in tmp folders before it shuts down may not fully protect you.  Stuff can be undeleted (points 1 & 2 above) And it does nothing for point 3 above.  

Perhaps truecrypt has strategies in place for that(??).   Does it deleting the stuff in swap and then it overwrites it several times with random patterns to ensure that what was there is not recoverable?  Must take a LONG time to shut down.  hehehe

I personally use full disk encryption now - that which comes standard with the ubuntu v7.10 alternate installer (dm-crypt/LUKS).  I toyed with it only in the past 3 mths as a matter of interest.  Here is why:

My only computer is the Dell laptop my company supplied me.  It has company and personal stuff on it.  I used to only encrypt my personal stuff using encfs - keeping it totally separate from the corporate stuff as well as protected.  

One day I will have to return the laptop - I also wanted to know that my personal stuff wont be accessible to corporate IT people under any circumstance (heck - what if I died suddenly and my laptop were send back to HQ IT dept with all my personal stuff clearly readable).

I found encfs was suitable for the above needs.

Like I said it was just personal interest for me that I dabbled with whole disk encryption.  It seemed like a very good idea for a corporate "road warrior" to have the corporate info, as well as private info, secured in case of laptop theft or loss.  It is not a company initiative.

I have a spare HDD for my laptop.  Periodically I clone the HDD that is in my laptop (the working HDD) to the external spare.  It is a full clone, bootable, and contains all my personal and work stuff.  Between full cloning episodes I back up /home using (g)rsync to keep it current.  (I also back up the work stuff on /home (only) to a file server on the corporate domain using (g)rsync) 

So seeing I have that spare HDD - one fine weekend a few mths ago I blew away what was on it and installed ubuntu Gutsy clean and new from alternate CD using the option for full disk encryption.   Then copied /home from the working HDD.

Once I was happy I swapped out the working HDD from the laptop HDD bay (it has become my full back up HDD and stored separately), and replaced it with the whole disk encrypted HDD.

So for the past few months I have been using a nice clean installed Gutsy on full encrypted HDD.

Observations:
My laptop is a Dell D410.  It is no powerhouse.  It has a 1.73GHz Pentium M processor.  1.5GB RAM and 120GB HDD

I have a 250MB /boot partition unencrypted.  The rest (including /, /home, swap etc) is all encrypted.

I still keep my personal stuff segregated in an encfs file system on the encrypted /home.  

I rarely notice any slowdown attributable to the HDD encryption.  I have a CPU monitor running all the time on my desktop courtesy of conky and so this is a measured observation - not just a feeling.

I see that on occasions dm-crypt takes up CPU time and that has never gone above about 18% in every day use (includes heavy disk intensive processes from time to time).   Thus slowdown would only occur if other processes were using more than 82% CPU time (taking CPU to 100%) at a time when intense disk activity was making dm-crypt work hard too.

Note:  for most of the day dm-crypt doesn't even show up on conky CPU meter - the 18% mentioned above is exceptionally/rare.

More info on day to day use and tasks?  Ask.

---

### Post by tact on 2008-01-10
> Originally Posted by capink
I don't get the point of encrypting the whole HD. It is enough to encrypt the partitions containing private data. But encrypting the root partition? what is the point?

Another reason for encrypting system partitions (non-private data) would be to prevent malicious people from booting your system with LiveCD and changing or aliasing system files so that they gain control that way.

---

### Post by tact on 2008-01-10
Following on from what I wrote above:
Next phase for me was after using the full HDD encryption system for about 3 mths I decided to stay with it.  

Thus I felt it was time to update my spare HDD to full disk encryption.  Remember from the narrative above the "spare" HDD was previously installed in the laptop as the working HDD before my foray into full disk encryption and was not encrypted at all (though it had my personal files encrypted via encfs)

I had 2 options:
1.  clone the fully encrypted HDD to the spare drive as per my past practice prior to beginning to use full disk encryption.

2.  Start over with a clean install of Gutsy, encrypted fully, then copy over /home files.

I chose the latter, a clean new install,  because I had used the default "use whole disk" automatic partitioning/encryption option first time around and that had the whole filesystem in one logical partition on the encrypted partition.   I prefer to have /home on its own partition.

So last weekend, starting again from scratch, I installed Gutsy clean and fresh on the spare HDD.  

I set aside 250MB for /boot (unencrypted) and the rest of the HDD was made  "physical partition for encryption".

In the encrypted physical partition I created logical partitions/volumes:
9GB for /
2.5GB for swap 
and the rest for /home.

This time I allowed the system to "erase" the partitions before creating file systems.  I guess this is like "shred" or "wipe" to ensure that there is nothing easily recoverable on the drive.  Be warned on 120GB drive it took a LONG time!

Once all installed, booted, updated, etc...  I copied /home across from the working HDD...  swapped out the working drive so it became my new full system "back up" and installed the newly installed drive into the laptop drive bay - making it the new working drive.

I have found that the spare HDD (now also using full disk encryption) is fully accessible to me when installed into an external USB drive casing.  Plug in the USB cable and immediately the /boot partition shows up as a removable USB drive icon on my desktop, and I am prompted for the passphrase needed to unlock the encrypted partitions.  I can then manually mount the encrypted volumes easily (tho it took a while and some reading to find the right commands.)

So I am very happy that I can have full drive encryption on the HDD in my laptop AND that I can access fully encrypted volumes when connected as removable external drives.  THis allows me to continue my practice of periodically cloning my working HDD to an external drive, and in between clonings use grsync to do incremental data backups.

Todo...
1.  At the moment while the working and spare HDD's have the same data on them and thus the spare is a good backup.  The drives are not identical.  (one has separate /home partition and one does not).  SO in a few months when the new working drive has settled and no problems surface - I will clone it onto the spare drive so the file systems, as well as data, is identical.

2.  Next thing I want to toy with is setting the whole drive encryption up such that a new encryption key for the swap partition is randomly generated by the system at every boot.

---

### Post by CCNA_student on 2008-01-10
I have not encrypted very many of my files as I have had no need to.

---

### Post by oni5115 on 2008-01-12
I don't use it yet, but I'd like to do it on my laptop.  I'm wondering though, if I did an install with the alternate CD, is there a way to set up my computer to have a /boot, /windows, /, and /home,  partitions?

Because space is limited for me on my laptop, I chose to make 10 Gb win, 10 Gb /, and the rest all /home.  By using the ext2/3 drivers for windows, I can mount my /home paritiion in windows to access my files.  I'm curious if I could still do such an installation using encryption or not.

I'd love to completely dump windows honestly... but wine isn't perfect, and I know at least one game I want to play that has issues at the moment.

---

### Post by regomodo on 2008-01-12
truecrypt for me for a whole drive (of 6). it's the smallest of the lot and only has my most sensitive stuff on it

---

### Post by Biochem on 2008-01-12
> **oni5115 said:**
> I don't use it yet, but I'd like to do it on my laptop.  I'm wondering though, if I did an install with the alternate CD, is there a way to set up my computer to have a /boot, /windows, /, and /home,  partitions?

Because space is limited for me on my laptop, I chose to make 10 Gb win, 10 Gb /, and the rest all /home.  By using the ext2/3 drivers for windows, I can mount my /home paritiion in windows to access my files.  I'm curious if I could still do such an installation using encryption or not.

I'd love to completely dump windows honestly... but wine isn't perfect, and I know at least one game I want to play that has issues at the moment.

I'm considering doing the same thing. For the Home partition, the option I'm considering to use [http://www.freeotfe.org/](http://www.freeotfe.org/) in windows to make the dm-crypt/LUKS partitions usable. Does anyone has experience with freeotfe?

---

### Post by kevdog on 2008-01-12
Can I somehow apply dm-crypt/LUKS to my Feisty system??  Im really getting paranoid about data encryption.

As far as gpg for email encryption, the default of lazy way of installing the keys and such is less than optimal.  You really want to tweak your gpg.conf file, to optimize the choice of ciphers and hashes to use.  I would not recommend the default SHA1 hash if you dont have to use it. 

Also, I probably would recommend RSA signing and encryption keys or DSA/Elgamal keys (the default).  Its really a toss up between RSA and DSA2 depending on who you read.  The bad part about DSA2 however is that since its still beta, its not backward compatible with older gpg versions.  Hence for that reason I would stick with RSA keysets.  The default way of creating keys doesnt give you this option.

Ive meant to write a tutorial on the proper way to set up and configure gpg, however Ive never really gotten around to it.  I guess I should spend more time writing than reading the forum comments.

---

### Post by tact on 2008-01-13
> **oni5115 said:**
> I don't use it yet, but I'd like to do it on my laptop.  I'm wondering though, if I did an install with the alternate CD, is there a way to set up my computer to have a /boot, /windows, /, and /home,  partitions?

Because space is limited for me on my laptop, I chose to make 10 Gb win, 10 Gb /, and the rest all /home.  By using the ext2/3 drivers for windows, I can mount my /home paritiion in windows to access my files.  I'm curious if I could still do such an installation using encryption or not.


When you run the alternate installer and manually set up encryption, you can manage what partitions are on the encrypted volumes and which are not.  If you allocate a non-encrypted partition to /home then you can share it with windows via the ext2 or ext3 drivers available for windows. 

I have no idea whether there exists any suitable software to unlock and access dm-crypt/LUKS partitions from windows.  Perhaps others can advise about that.

---

### Post by Methuselah on 2008-01-13
.

---

### Post by kevdog on 2008-01-13
> If you allocate a non-encrypted partition to /home then you can share it with windows via the ext2 or ext3 drivers available for windows. 


So that means that if you are running a SAMBA share, you couldnt share the files/directories if they were located on an encrypted partition?  This would be one major disadvantage to entire disk encryption if your were on a home network with linux/windows machines.

---

### Post by tact on 2008-01-13
> **kevdog said:**
> So that means that if you are running a SAMBA share, you couldnt share the files/directories if they were located on an encrypted partition?  This would be one major disadvantage to entire disk encryption if your were on a home network with linux/windows machines.

No not like that.   I meant in the context of a dual boot situation (which if I understood correctly was the question I was addressing)  - if you had /home unencrypted then no reason why you cannot access /home partition when booted into windows (dual boot) using the available windows tools to access ext2/3 file systems.

What you are talking about is different.  Sharing via samba is only relevant if booted into ubuntu.  If you have your "full disk encrypted" ubuntu installation booted then your encrypted partitions are transparently available to all applications including samba.

At boot time you are asked to enter the dm-crypt/LUKS passphrase, assuming it is entered correctly, from that point on all the encrypted partitions will be made accessible in a manner transparent to the user and all programs/data that use it.

---

### Post by kevdog on 2008-01-13
Ok,  I dont dual boot, so I didnt think of the situation you proposed.

---

### Post by hyper_ch on 2008-01-14
Well, an option that comes to my mind would be as following:

(1) encrypt your full system with dm_crypt/luks - but leave an unencrypted partition for your /home folder - but don't do anything with it yet.

(2) run linux and install TrueCrypt for it.

(3) With truecrypt make a container for that whole unencrypted partition and format it then to ext3

(4) copy your /home folder to that new partition and make sure permissions are correct.

(5) then mount that new partition as /home

On Windows you'llh ave then this truecrypt container and you can make it transparent. With the additional ext2/3 drivers you can write to it.
Well, that would be one option. I suggest ext3 as filesystem because of permissions and stuff.

You could also make a truecrypt container with fat32 or ntfs in it but then you shouldn't mount it as home but maybe as ~/Share or ~/Desktop/Exchange or something ilke that and safe all the data in there.

---

### Post by tact on 2008-01-15
> **kevdog said:**
> Ok,  I dont dual boot, so I didnt think of the situation you proposed.

Ya I was responding to another poster who was asking about sharing an encrypted partition between windows and linux in a dual boot system.

Responding to your question - about using DM-crypt/LUKS on your feisty system:
I believe you can install the packages and encrypt partitions.  I have seen pages talking about doing full disk encryption written for "dapper drake".  (Sorry I dont have any links to post - just google)

When you encrypt a partition it is totally destructive of whatever is on the partition so you would have to back up everything before you go for it.

---

### Post by hyper_ch on 2008-01-15
later encrypting can be done but gutsy makes it so simple now to create a fully encrypted system from the start... so I'd rather go that way...

---

### Post by SanskritFritz on 2008-01-15
I use EncFS over GMailFS. And I also encrypt my private files.

---

### Post by tact on 2008-01-15
> **hyper_ch said:**
> later encrypting can be done but gutsy makes it so simple now to create a fully encrypted system from the start... so I'd rather go that way...

Totally agree with you.  There is nothing simpler than booting from the alternate installer CD, answer the usual installer questions, choose the "use whole disk, automatically set up encrypted install" option and let it run.  In a short time you have a full fresh new installation of Gutsy running on fully encrypted HDD (except for the /boot partition of course).

It is a little more complicated if you want to manually set up the partitioning but still not anything you could call "difficult".  :)

So easy in operation too.  Just one time at bootup asked for a passphrase.  After that totally transparent operation.

I have a spare HDD and as mentioned in past posts is used as a full back up to my running system - a fully bootable backup.  It runs full disk encryption too.

Also very simple:
Whenever I plug the spare drive into the running  system, via USB case,  to do incremental backups - the system recognises that the removable drive just plugged in has dm-crypt/luks encrypted partitions on it and asks me for the passphrase.  Once entered I can mount the encryption(s) and standard apps like nautilus and grsync work fine.

(It could be even more simple if after entering the passphrase the mount was automatic - but i am not complaining.  :))

---

### Post by canuda10 on 2008-01-15
I encrypt my $HOME with encfs, but without encrypting filenames. It's a bit less secure then, but it is enough for me anyway.
The question is that I make daily external backups with rsync over internet, and this way I can  simply search for any file, from any date, to recover by simply copying it again.
I also use encfs on my usb sticks, since i sometimes carry sensitive information on them.

---

### Post by PetePete on 2008-01-15
how much slow down is there from encrypting the whole drive by installing ubuntu with alt cd method?

---

### Post by hyper_ch on 2008-01-15
You will notice the slowdown when you have a lot of data transfer.... so copying gigs and gigs of data will noticably be slower... but on day-to-day uses you won't notice hardly anything.

---

### Post by kevdog on 2008-01-15
Again any way of employing to luks encryption to a feisty system up and running?

---

### Post by hyper_ch on 2008-01-15
there is ;) but do you have enough space to backup your data to?

---

### Post by kevdog on 2008-01-15
> **hyper_ch said:**
> there is ;) but do you have enough space to backup your data to?

Sounds like your going to tell me to just start over.  In that case I would just backup what I needed and then just install Gutsy.  I take it that its not an easy proposition.

---

### Post by 3rdalbum on 2008-01-15
Possibly a better question than "Why encrypt swap" is "Why have swap on a system with plenty of free RAM"?

To answer the question, I don't use hard drive encryption as I sometimes try out other live CDs, and I don't want to make it difficult for me to access my hard drive from within another distro. But I do have an encrypted folder of stuff I wouldn't want a nun to see.

---

### Post by hyper_ch on 2008-01-16
> **kevdog said:**
> Sounds like your going to tell me to just start over.  In that case I would just backup what I needed and then just install Gutsy.  I take it that its not an easy proposition.

Well, if you want to encrypt a drive/partition it is recommended that you wipe it first and then you still have to create a new encrypted drive/partition... so you have to backup that data anyway somewhere...

So the simpler approach would be a direct encryption setup ;)

---

### Post by tact on 2008-01-16
> **kevdog said:**
> Sounds like your going to tell me to just start over.  In that case I would just backup what I needed and then just install Gutsy.  I take it that its not an easy proposition.

Well thats gotta be the least painless way to get full disk encryption.  

I suppose nothing is impossible and you could figure out a stack of hoops to jump thru to migrate what you have running now to a full encrypted setup but I doubt anyone has done it.  I scratched my head and thought about a while and got tired just thinking about it!  :)

If you have a plain install of feisty (no device mapper etc) you are not able to just move what you have to encrypted partitions - device-mapper (logical partitions, logical volumes, logical groups etc) are involved as well.

Definitely easier to do a clean install and have it set up properly from start.  :)

---

### Post by hyper_ch on 2008-01-16
> **tact said:**
> If you have a plain install of feisty (no device mapper etc) you are not able to just move what you have to encrypted partitions - device-mapper (logical partitions, logical volumes, logical groups etc) are involved as well.

Definitely easier to do a clean install and have it set up properly from start.  :)

Well, the problem is, every partition that needs to be encrypted will first needed to be backupped somewhere else.... and I have written a guide some while ago on how to encrypt partitions and stuff on feisty... it would need a bit of adjustments to do full encryption but it's not much of a big deal anymore (I tend to think).

But as said, as you need to backup data anyway, it would be a lot less "painful" to directly encrypt the system upon installation.

---

### Post by Biochem on 2008-01-17
I have 2 question.

[LIST=1]
[*]when doing a fresh install on an encrypted disk. Is it possible without erasing the /home partition? :confused:
[*]If there is multiple encrypted disk. Is it possible to mount all of them with only one password?[/LIST]

---

### Post by hyper_ch on 2008-01-17
1. yes - but /home won't be mounted and encrypted then....
2. not that I know of (by default it asks for every encrypted device [except for swap]

---

### Post by euler_fan on 2008-01-17
One of the biggest reasons I don't encrypt my email is because then I'd have to set of PGP/GPG for everyone I know in order to exchange email with them. Major drag. This is probably a common experience for most people savvy enough to want to use encrypted email. I do digitally sign though.

If you count KeePassX as keeping an encrypted file, then yeah, I do encrypt a few "critical" files. One of these days I'll get off my butt and learn TrueCrypt and set myself up a couple of encrypted containers to store my more sensitive information in.

---

### Post by smbm on 2008-01-20
Hi

Sorry to go slightly off topic but I have an encryption related question.

I'm thinking of fully encrypting my laptop to safeguard my personal data should it go missing. I'm a little worried about battery life though, obviously encryption is going to be taxing the processor more.

Does anyone have any experience in the matter? How much battery life can I expect to lose?

Cheers

---

### Post by tact on 2008-01-20
> **smbm said:**
> Hi

Sorry to go slightly off topic but I have an encryption related question.

I'm thinking of fully encrypting my laptop to safeguard my personal data should it go missing. I'm a little worried about battery life though, obviously encryption is going to be taxing the processor more.

Does anyone have any experience in the matter? How much battery life can I expect to lose?

Cheers

I don't know if it would be measurable....  I have been running the standard encrypt from install Gutsy disk encryption for several weeks now. 

 I have conky on my desktop displaying load stats and I rarely ever see "kcryptd/0" (the background decryption process) show up.  "compiz.real" and "xorg" spend far more time in the load stats list.

Its only when opening and saving/copying/moving/deleting files that encryption processes get active.  So your CPU and disk would be getting kicked up a notch at those times anyway.  Thus there would not be any "unnecessary" CPU or disk "wakeups".   But perhaps the CPU load, once kicked up, might go higher than if no encryption was involved. How much extra that little portion of whats happening adds to battery usage - sorry its too little for me to get my head around and give a feel for it.

If you are doing some real disk intensive stuff...  lots of read/writes...  then yes the load on the CPU would go up higher than ot would without any encryption involved.  I have seen that.  When I grsync to back up stuff from my encrypted system to an encrypted external disk I see the "kcryptd/0" process in the load list longer and stronger.  :)

---

### Post by Akre on 2008-01-20
I use full disk encryption on my laptop. Just in case it got stolen or anything. I do not have there launch codes tho, I just like idea that my data are private and so on.

There is performance loss but this is one I'm willing to live with.

Question: If there is multiple encrypted disk. Is it possible to mount all of them with only one password?

Answer: Yes, I pass password for root partition only, rest of them are mounted using keys in files that were on encrypted partition. 

And If you fell this is not secure i suggest using debian installer way (thats ubuntu alternate) - using encrypted device, that is lvm, that has many volumes (or so I understand)

---

### Post by Pekkalainen on 2008-01-20
Why do people lock the door behind them when they go to the bathroom? Privacy. Doesnt have to mean you have something to hide.

I encrypt things that are for my eyes only. Wich means certain files and  e-mails.

---

### Post by DigitalDuality on 2008-01-21
d

---

### Post by euler_fan on 2008-01-21
> **Pekkalainen said:**
> Why do people lock the door behind them when they go to the bathroom? Privacy. Doesn't have to mean you have something to hide.

I encrypt things that are for my eyes only. Which means certain files and  e-mails.

+1

---

### Post by irw on 2008-01-27
I am required to have full hard drive encryption by the organisation i work with.

I have two hard drives, and one is fully encrypted; the other has a 10Gb unencrypted partition with Ubuntu on it, the rest being also encrypted.

The children can use the unencrypted system for games & internet access. No email, passwords or anything else sensitive is kept on there.

If police / immigration / anyone else want to use the system, grub is set before the trip to automatically select the unencrypted partition with little delay, and they get to look at a fully working system. Unless they start to look at hard disk partitions or grub,  the encrypted partitions are invisible.

---

### Post by Bruce M. on 2008-01-29
I don't feel a need to run encryption. No secerts here.

---

### Post by tubbygweilo on 2008-05-19
Thunderbird and Enigmail keeps casual prying eyes away from my emails and I also use the alt install 8.04 with for lvm + full disk encryption. I would hate for any of my kit to be stolen and data used in ways I would not approve of hence the encryption. I would of course supply pass phrases to those legally entitled to look at my work for to do otherwise might not be a good idea.

---

### Post by ice60 on 2008-05-19
i use truecrypt, but really i could probably not use encryption. i don't keep anything with my name and address or CC numbers or anything private like that on my computers. i don't use email or any kind of socal networking either, i'm a real privacy nut, i just can't bring myself to give any private info away!

i have a really long passphrase for truecrypt that i keep in a text file on my desktop j/k :lolflag:

---

