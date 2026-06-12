---
title: "Counter-forensic software on Journaling FS: Ideas?"
date: 2008-08-26
forum: Security
---

### Post by jesushero on 2008-08-26
I was doing some reading on the efficiency of counter-forensic software such as shred, wipe, and the rest, on journaling filesystems such as ext3 and ReiserFS.

The problem seems to be that when shred tries to overwrite a certain file 24 times, the data will not necessarily overwrite the original file, but may be written on a different part of the hard drive, thus rendering the shredding insecure. 

I had the following idea: 

If we only want to shred a specific file on a journaling FS, for example /partition/shred.file 

```
shred /partition/shred.file
dd if=/dev/zero of=/partition/shred.file
sync
shred -n 64 -vxzu
sync
```

This would initially overwrite the file 24 times, which may however not be written on top of the original file which will still physically exist unaffected. Then it would fill the file with zeros until the partition is full, thus eliminating all the free space, where the original file would be sitting. Then it would shred that large file, overwriting more times than the default, say 64, verbosely, exact size, zeroing in the end to hide the shredding and finally removing the file. 

After this process, the free space on a given partition will have been overwritten at least 65 times. 

This makes me think that any deleted files will have been physically overwritten 65 times. Am I missing something? 

I am assuming that the traces of the files will still be there, but the contents will be unrescuable. Correct?

---

### Post by cdenley on 2008-08-26
```
man shred
```
> 
In the case of ext3 file systems, the  above  disclaimer  applies  (and
       shred  is  thus  of  limited  effectiveness) only in data=journal mode,
       which journals file data in addition to just  metadata.   In  both  the
       data=ordered  (default) and data=writeback modes, shred works as usual.


If you want to overwrite all free space on a drive
```

sudo apt-get install secure-delete
sudo sfill /

```

---

### Post by /etc/init.d/ on 2008-08-26
You haven't accounted for the following:

**Slack space in other blocks**:  If the file you are shredding has shrunk from its original size, or for a couple of other reasons (e.g. defragmentation), blocks that the file occupied but now no longer occupies may be in use by other files.  If these other files don't occupy the entire block, fragments of the sensitive file may reside in the "tips" of these blocks.

To account for this you'd need to look at every occupied block on the file system and for the blocks that don't extend to the end, zero them out (Eraser does this and calls it "erasing cluster tips" or something similar).

Wiping the free space will not touch these blocks as they are occupied.

**Swap**:  presumably this file has been used at some point, you have no guarantees that it hasn't been written to a swap device; therefore you would need to wipe every swap device that has been active while the file has been accessed.

**Journal:**  following on from the poster above, if the file system is mounted in data=journal mode, data from the file may have potentially been written to the journal.  I do not know of a way to zero the journal without zeroing the entire file system.  (Though there may be a way.)

**Reallocated sectors:**  your drive might have silently reallocated a block relating to this file (unlikely, but a possibility).  Modern drives can wipe their reallocated sectors, but it involved wiping the entire drive.

**Off-track areas:**  when writing data, hard drives can sometimes go off-track due to various reasons, one of them being shock or vibration.  Data relating to the file in question may have been written to an off-track area.  Again, this is unlikely, and can be wiped by the drive's firmware, but requires wiping the entire drive.

In the past I have been told that a lot of the above is overkill.  If the data is sensitive enough that you want to wipe it, then it isn't overkill and you need to consider all possibilities, otherwise you'd just be kidding yourself.

---

### Post by jerome1232 on 2008-08-26
If your data is that sensitive why not just go for full disk encryption. 

To file carving programs it just looks like a bunch of random junk.

---

### Post by HermanAB on 2008-08-26
Nothing beats a 25lb sledge hammer...

---

### Post by jesushero on 2008-08-26
> **/etc/init.d/ said:**
> You haven't accounted for the following:

**Slack space in other blocks**:  If the file you are shredding has shrunk from its original size, or for a couple of other reasons (e.g. defragmentation), blocks that the file occupied but now no longer occupies may be in use by other files.  If these other files don't occupy the entire block, fragments of the sensitive file may reside in the "tips" of these blocks.

To account for this you'd need to look at every occupied block on the file system and for the blocks that don't extend to the end, zero them out (Eraser does this and calls it "erasing cluster tips" or something similar).

Wiping the free space will not touch these blocks as they are occupied.

**Swap**:  presumably this file has been used at some point, you have no guarantees that it hasn't been written to a swap device; therefore you would need to wipe every swap device that has been active while the file has been accessed.

**Journal:**  following on from the poster above, if the file system is mounted in data=journal mode, data from the file may have potentially been written to the journal.  I do not know of a way to zero the journal without zeroing the entire file system.  (Though there may be a way.)

**Reallocated sectors:**  your drive might have silently reallocated a block relating to this file (unlikely, but a possibility).  Modern drives can wipe their reallocated sectors, but it involved wiping the entire drive.

**Off-track areas:**  when writing data, hard drives can sometimes go off-track due to various reasons, one of them being shock or vibration.  Data relating to the file in question may have been written to an off-track area.  Again, this is unlikely, and can be wiped by the drive's firmware, but requires wiping the entire drive.

In the past I have been told that a lot of the above is overkill.  If the data is sensitive enough that you want to wipe it, then it isn't overkill and you need to consider all possibilities, otherwise you'd just be kidding yourself.


Yes, indeed..  I have missed a few points here..

---

### Post by jesushero on 2008-08-26
> **jerome1232 said:**
> If your data is that sensitive why not just go for full disk encryption. 

To file carving programs it just looks like a bunch of random junk.

It is not that I have anything sensitive enough to actually be in desperate need for anything of this sort, I am just trying to further my understanding of journaling filesystems, which is rather limited.

When it comes to direct comparison though, which one is safer? A correctly and fully shredded/wiped drive, or an encrypted drive?? Is it easier for someone to dig through multiple layers of overwriting or to crack the encryption key? 

My understanding is that however hard it may be, it is POSSIBLE to crack an encryption key. I am not sure how it goes with layers of overwritten data though.

---

### Post by jesushero on 2008-08-26
> **cdenley said:**
> ```
man shred
```


If you want to overwrite all free space on a drive
```

sudo apt-get install secure-delete
sudo sfill /

```

Thanks, I hadn't heard of this package before. I'll check it out.

---

### Post by jerome1232 on 2008-08-26
With a sufficiently long passphrase it would take so much time and processing power (as in barring the guy doesn't have 10 super computers clustered together) that it might as well be impossible.

I guess if keeping the data isn't an issue wipeing the drive completely clean is in the end more secure because sometimes encryption methods have a weakness (not very random or something) that is discovered making the cracking process thousands of times easier.

as a previous poster mentioned, nothing beats a 25lb sledghammer

---

### Post by jesushero on 2008-08-26
> **HermanAB said:**
> Nothing beats a 25lb sledge hammer...

> **jerome1232 said:**
> as a previous poster mentioned, nothing beats a 25lb sledghammer

I seem to stumble upon this quote a lot in such a context. The Department of Defense in the USA seems to think that the only "safe" and acceptable way of wiping disks is by destroying them or subjecting them to degaussing.

So if we have the following example: 

Computer with one hard drive, partitioned as /dev/hda1 - ext3 and /dev/hda2 - swap

If I am to remove the drive from that computer, insert it on another system as /dev/hdb where the partitions would be /dev/hdb1 and /dev/hdb2, and shred /dev/hdb as a whole, zero it, write random data on it, etc, thus destroying the Master Boot Sector and all data in there, in what way would it still be better to physically destroy the drive? What is there left if I shred/wipe the whole drive instead of a partition? 

The man page of wipe (man wipe) contains a view that hard drive manufacturers might have secretly implemented a system on hard-disks that copies your data in a part of the drive that is inaccessible to a simple user but can be revealed to someone who is aware of the low-level IDE commands that control this (government agencies). Is this more likely to be a conspiracy theory or the truth? 

If we are to believe this, then I can totally see the point of physically destroying a drive...

---

### Post by jerome1232 on 2008-08-26
Well physically, magnetic traces of overwritten data still exist, theoretically it is possible to recover data that has been overwritten ~30 times, this is  definitely not researched fact on my part though, just something I recall having read, somewhere. So let me know if I'm spreading a load of crap.

edit:
some math about encryption
> TrueCrypt uses AES-256 by default, I'm not sure about the FDE so someone else will have to chime in. AES is the name of the standard the original cipher was known as Rijndael. Rijndael was selected from a field of competing ciphers during a selection process (which also included Twofish and Serpent, also ciphers in TrueCrypt). NIST made the actual selection but Rijndael was also endorsed by the NSA (AES is used to safeguard classified documents). The cipher has been well vetted and there are no known cryptographic weaknesses in it. Barring some breakthrough mathematics or significant advances in computing (and our understanding of solving difficult problems) it will likely remain like that for the foreseeable future.

With AES-256 you have a key size of 256 bits. That means there are 2^256 (approx. 10^77, to give you handle on that number it is estimated that there are about 10^80 particles in the observable universe) possible permutations for the key. Lets say you had a quad-core processor running at 2.4GHz with a program that could make one key attempt per clock-cycle and was perfectly parallel (and this is a gross over-estimation) That's 9.6 billion keys tested per second. It would take you approximately 10^67 seconds to try them all. That's about 10^59 years (many times the current estimated age of the universe.) And even if you throw thousands or even millions of times that computing power at the problem, you are only reducing it by scalar amounts.

It's more than likely that any flaws in the security system provided by TrueCrypt would not be caused by a weakness in the cipher itself but a flaw in TrueCrypt's implementation or the hardware it resides on that allows for the key to be weakened (some sort of side channel attack).

---

### Post by /etc/init.d/ on 2008-08-27
> **jerome1232 said:**
> So let me know if I'm spreading a load of crap.
I wouldn't say you're spreading crap; I've heard claims from those who seem to think there are companies out there that could recover data no matter how many times it has been overwritten.

If this were the case though, it would be theoretically possible to create a drive with infinite storage.  If you can always recover overwritten data, when you fill your drive, you simply overwrite some of the data with new data.  When you want the old data back, you simply use these magical recovery techniques people claim and get the old data back.  Essentially you'd have a device with infinite storage.

That would be great, wouldn't it?  But it flies in the face of everything logical.

I've yet to see any data recovery company that claims to recover data from a drive that has been overwritten with a psuedo-random pass.

The OP should take a look at [HDDErase]("http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml").  This activates the erasing commands built in to the drive's firmware and will perform a more thorough erase than any software tool.  This covers the two areas I talked about in my last post (reallocated sectors and off-track writes).

An Enhanced Security Erase uses a pseudorandom pass, a regular erase doesn't.

---

### Post by ekh on 2008-08-27
> **/etc/init.d/ said:**
> I wouldn't say you're spreading crap; I've heard claims from those who seem to think there are companies out there that could recover data no matter how many times it has been overwritten.

If this were the case though, it would be theoretically possible to create a drive with infinite storage.  If you can always recover overwritten data, when you fill your drive, you simply overwrite some of the data with new data.  When you want the old data back, you simply use these magical recovery techniques people claim and get the old data back.  Essentially you'd have a device with infinite storage.

That would be great, wouldn't it?  But it flies in the face of everything logical.

I've yet to see any data recovery company that claims to recover data from a drive that has been overwritten with a psuedo-random pass.

The OP should take a look at [HDDErase]("http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml").  This activates the erasing commands built in to the drive's firmware and will perform a more thorough erase than any software tool.  This covers the two areas I talked about in my last post (reallocated sectors and off-track writes).

An Enhanced Security Erase uses a pseudorandom pass, a regular erase doesn't.

I googled "fire damaged hard disk recovery"

and got

[http://www.salvagedata.com/](http://www.salvagedata.com/)

The company states:

"Salvage The Unrecoverable"
"No recovery - No Fee policy"

I have read an article long ago describing a company fire, disks were recovered. That recovery company stated they always removes the internal discs from the drive, and that they had readers sensitive to different magnetization depths. They stated that they could recover data many times overwritten, but the cost of recovery rises with the number of overwrites.

ekh

---

### Post by /etc/init.d/ on 2008-08-27
> **ekh said:**
> I have read an article long ago describing a company fire, disks were recovered. That recovery company stated they always removes the internal discs from the drive, and that they had readers sensitive to different magnetization depths.
That is perfectly reasonable; magnetic material does not lose its magnetic properties or state until heated to fairly high temperatures (its Curie point).  My post didn't specifically mention physical damage though, it dealt with overwriting.

It's worth keeping in mind also that some companies' definitions of "fire damage" mean some slight charring to the outer casing.

> **ekh said:**
> They stated that they could recover data many times overwritten, but the cost of recovery rises with the number of overwrites.
It would be interesting to see if this company is still trading, and if so, if they still make these claims and how they are able to substantiate them.  Otherwise this means practically nothing.

If they were so confident of their recovery, would they so prominently display their "No recovery - No Fee policy" clause?  Granted they all seem to say this.

---

### Post by jerome1232 on 2008-08-27
Well "it's possible" and "it is a 100% reliable way of recovering data" are very different things, and the process sounds like it would involve dissembling the HDD and using more sensitive equipment to read it.

---

### Post by cdenley on 2008-08-27
Even after scanning the platters with an electron microscope, I think some complex math formulas are required to make an educated guess as to what data may have previously been written. I don't think anyone can actually recover a file that has been overwritten with even 10 random passes, but I would be interested if someone were to prove me wrong.

Of course as technology in computer forensics improves, there may be some new technique for data to be recovered from your hard drives which will have been discarded for years. I don't think there are many data thieves that can recover any data that was overwritten with even a single pass of zeros. I think it's all just a question of how paranoid you or your clients are.

---

### Post by jesushero on 2008-08-27
> **/etc/init.d/ said:**
> 
The OP should take a look at [HDDErase]("http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml").  This activates the erasing commands built in to the drive's firmware and will perform a more thorough erase than any software tool.  This covers the two areas I talked about in my last post (reallocated sectors and off-track writes).


It looks interesting.. I'll have a closer look at it and the way it works. From what I understand, this is a "hardware erase", with no regard to the filesystem or anything like that, while the rest we have mentioned (apart from physical destruction) work on a filesystem level. It is understandable that the more low-level you get, the more possible it is to do things more effectively.

---

### Post by jesushero on 2008-08-27
> **/etc/init.d/ said:**
> It would be interesting to see if this company is still trading, and if so, if they still make these claims and how they are able to substantiate them.  Otherwise this means practically nothing.

Looks like they are and they're still promising a lot. 

It would be interesting to see this in action, somebody wiping/shredding/erasing/burning/smashing/melting hard-drives and somebody else in the same room recovering all the data from them! This would solve a lot of questions.

---

### Post by jesushero on 2008-08-27
> **cdenley said:**
> Even after scanning the platters with an electron microscope, I think some complex math formulas are required to make an educated guess as to what data may have previously been written. I don't think anyone can actually recover a file that has been overwritten with even 10 random passes, but I would be interested if someone were to prove me wrong.

Of course as technology in computer forensics improves, there may be some new technique for data to be recovered from your hard drives which will have been discarded for years. I don't think there are many data thieves that can recover any data that was overwritten with even a single pass of zeros. I think it's all just a question of how paranoid you or your clients are.

So scanning with an electron microscope would yield a bunch of binary bits and pieces which would then need to be put together in a "solving-the-puzzle" fashion, and if you're lucky it might make sense when it's done? That seems like a trial-and-error thing that requires a certain amount of luck (not to mention cash) rather than a bombproof way of recovering data.

---

### Post by ekh on 2008-08-27
As I have understood this, the success rate of recovering data many times overwritten depends on how long the data has resided on the disk platters.

As time goes by, the magnetization extends deeper into the media layer.

I think this property can be used to a very large extent. Often important data has been stored for a long time on a disk, meaning that the information can be read deep under the surface of the media.

The companies disassembles the disks and use special precision drives and heads to read.

Although the data on the disk is considered digital, it is actually an analog signal with phase, frequency and amplitude.

If old data is overwritten many times, and the disk sent to data recovery shortly after, then the new data has not penetrated deep into the media yet. Using a special reader head focusing to the right depth the data is there for reading.

The ordinary IC in the drive interprets the analog signal from the read head and outputs a digital stream of data.

When the disk writes the data, the model and radius defines the write frequency. Different writes can not be perfectly aligned, as well as temperature variations can account for slight variations in the write frequency.

Every control loop has a certain accuracy, so the temperature of the bearing is also a factor because the friction is not constant.

Summing it all up, the special readers varies focusing depth, and a digital signal processor observing the phase, amplitude and frequency from the high precision speed reader drive gives space for slightly variations of the parameters and digital filters, until a valid CRC is obtained.

Knowing (or trial and error) the OS, the typical directory area can be found, then when the first valid CRC appear, then the age of files begin to appear so the right focusing depth can be set. And now a situation is approached where "lost" data "magically" appears again.

Often this is done in corporation with the customer in hard need for the data, thus easing the process also.

When fractions of valid data appears, then the parameter profile of a given file has appeared, so now the hard part is done.

If you have to do a sound business, the recovery success rate must be high. If not, it will be tough to earn a living with the statement:

"No recovery - No Fee policy"

ekh

---

### Post by jesushero on 2008-08-27
> **ekh said:**
> As I have understood this, the success rate of recovering data many times overwritten depends on how long the data has resided on the disk platters.

As time goes by, the magnetization extends deeper into the media layer.

I think this property can be used to a very large extent. Often important data has been stored for a long time on a disk, meaning that the information can be read deep under the surface of the media.

The companies disassembles the disks and use special precision drives and heads to read.

Although the data on the disk is considered digital, it is actually an analog signal with phase, frequency and amplitude.

If old data is overwritten many times, and the disk sent to data recovery shortly after, then the new data has not penetrated deep into the media yet. Using a special reader head focusing to the right depth the data is there for reading.

The ordinary IC in the drive interprets the analog signal from the read head and outputs a digital stream of data.

When the disk writes the data, the model and radius defines the write frequency. Different writes can not be perfectly aligned, as well as temperature variations can account for slight variations in the write frequency.

Every control loop has a certain accuracy, so the temperature of the bearing is also a factor because the friction is not constant.

Summing it all up, the special readers varies focusing depth, and a digital signal processor observing the phase, amplitude and frequency from the high precision speed reader drive gives space for slightly variations of the parameters and digital filters, until a valid CRC is obtained.

Knowing (or trial and error) the OS, the typical directory area can be found, then when the first valid CRC appear, then the age of files begin to appear so the right focusing depth can be set. And now a situation is approached where "lost" data "magically" appears again.

Often this is done in corporation with the customer in hard need for the data, thus easing the process also.

When fractions of valid data appears, then the parameter profile of a given file has appeared, so now the hard part is done.

If you have to do a sound business, the recovery success rate must be high. If not, it will be tough to earn a living with the statement:

"No recovery - No Fee policy"

ekh

That was very insightful, thanks!! I was thinking that it could have to do with the analogue properties of the magnetic media, but couldn't establish how. Now I have quite a clear picture and it seems like a very "realistic" way of recovering old data.

The drive during normal operation focuses on the "louder" signals, while getting rid of "analogue background noise" that exists. It also "regenerates" the signal to simply get 0 and 1 values. Studying the background noise however, it is possible through phase cancellation and Fourier transforms to focus on an approximation of another signal. This would then be regenerated so as to only get the peak values, thus rejecting further background noise and louder values.. The only thing needed then is to make sure you have filtered out the right things and to find the beginning of the files out of what you have.

---

### Post by ekh on 2008-08-27
Reading the thread title once more my advice is:

-Use an encrypted file system with strong cryptography.
-Use a very long passphrase, at least 20 well chosen characters, I use 30+
-Use a very long user password also.
-Don't write down the password.
-Have a good memory so you don't loose the password.
-Make regular backups, also encrypted, to protect against HW failure and theft.
-Let the screen saver lock the screen within a short interval unused, or better, always lock the screen when you leave the computer. Have the computer ask for password regularly and before every possible transfer of bulk data in/out of the system.
-Let 2 subsequently failed password entries shut down the system.
-Never use wireless keyboards.
-Use a keyboard extra screened (low emc), so a very sensitive radio receiver can not read what you are typing. The same goes for reading the screen.
-Be sure no persons or cameras monitor you typing the passwords.
-Surveillance equipment exists that sees through walls almost tv camera quality, however the resolution decreases with distance. Compensate by working in a "radio dead" room (copper foil enclosed without "leaks").
-Never connect the computer to the internet or a server after the system is installed.
-Physically disable the radio part of your WiFi. (also good for your health preventing cancer, search the net yourself, it is scaring to see an EU agency comparing the danger of 3G, GSM, DECT and WiFi with asbestos)
-When shutting down the computer, be sure the last program executed overwrites the ram, as data can survive surprisingly long after power-down.
-Only transfer encrypted data to and from other systems via a solid state disk media, and wipe clean format the media right after each transfer.
-If possible never bring the data outside the safe area.
-Don't talk with yourself while working, microphones may listen, and cameras look. 
-Remove the battery from your mobile, as programs exist to wake up a powered down mobile, and start surveillance.
-Don't use paper for notes.
-Don't make printouts.
-Don't order your equipment, go buy individual parts and assemble the computer yourself, an ordered computer can be invisibly wired for surveillance. Or it can be after mounted if your computer is left out of sight.

All computers emit radio signals, which may be used for surveillance. Use a scanner to measure the level of emissions, and improve the EMC properties/install a radio noise source to "drown" the computer noise emissions beyond readability. I will not be surprised to find motherboards with standard crafted BIOS code with an innocent looking PCB trace acting as an antenna for data monitoring.  

If you have data for your eyes only, it will not help you to overwrite the data with an encrypted file system, if someone really wants your data, and have a chance of getting hold of your disks. 

Your only safe protection is a complete physical destruction of the disk, preferably melting it completely (temperature above Curie point and destruction of media surface).

And to be total paranoid: If your data is very valuable, so somebody are willing to do whatever necessary to get hold of the data:

-Prepare to withstand torture, and die for the data, especially if the data can severely compromise yourself, your dear ones, your country or the humanity.

-Never operate the computer outside a physical safe area, where you don't have sufficient time to shut down the computer in case of physical intrusion.

-Don't leave the safe area yourself, to prevent unpleasant encounters.

I very well know this is beyond the needs of most (nearly all) people, but the subject was preventing leak of data. Although my list is a little long I'm sure it is not exhaustive on the subject.

ekh

---

### Post by jesushero on 2008-08-28
> **ekh said:**
> Reading the thread title once more my advice is:

-Use an encrypted file system with strong cryptography.
-Use a very long passphrase, at least 20 well chosen characters, I use 30+
-Use a very long user password also.
-Don't write down the password.
-Have a good memory so you don't loose the password.
-Make regular backups, also encrypted, to protect against HW failure and theft.
-Let the screen saver lock the screen within a short interval unused, or better, always lock the screen when you leave the computer. Have the computer ask for password regularly and before every possible transfer of bulk data in/out of the system.
-Let 2 subsequently failed password entries shut down the system.
-Never use wireless keyboards.
-Use a keyboard extra screened (low emc), so a very sensitive radio receiver can not read what you are typing. The same goes for reading the screen.
-Be sure no persons or cameras monitor you typing the passwords.
-Surveillance equipment exists that sees through walls almost tv camera quality, however the resolution decreases with distance. Compensate by working in a "radio dead" room (copper foil enclosed without "leaks").
-Never connect the computer to the internet or a server after the system is installed.
-Physically disable the radio part of your WiFi. (also good for your health preventing cancer, search the net yourself, it is scaring to see an EU agency comparing the danger of 3G, GSM, DECT and WiFi with asbestos)
-When shutting down the computer, be sure the last program executed overwrites the ram, as data can survive surprisingly long after power-down.
-Only transfer encrypted data to and from other systems via a solid state disk media, and wipe clean format the media right after each transfer.
-If possible never bring the data outside the safe area.
-Don't talk with yourself while working, microphones may listen, and cameras look. 
-Remove the battery from your mobile, as programs exist to wake up a powered down mobile, and start surveillance.
-Don't use paper for notes.
-Don't make printouts.
-Don't order your equipment, go buy individual parts and assemble the computer yourself, an ordered computer can be invisibly wired for surveillance. Or it can be after mounted if your computer is left out of sight.

All computers emit radio signals, which may be used for surveillance. Use a scanner to measure the level of emissions, and improve the EMC properties/install a radio noise source to "drown" the computer noise emissions beyond readability. I will not be surprised to find motherboards with standard crafted BIOS code with an innocent looking PCB trace acting as an antenna for data monitoring.  

If you have data for your eyes only, it will not help you to overwrite the data with an encrypted file system, if someone really wants your data, and have a chance of getting hold of your disks. 

Your only safe protection is a complete physical destruction of the disk, preferably melting it completely (temperature above Curie point and destruction of media surface).

And to be total paranoid: If your data is very valuable, so somebody are willing to do whatever necessary to get hold of the data:

-Prepare to withstand torture, and die for the data, especially if the data can severely compromise yourself, your dear ones, your country or the humanity.

-Never operate the computer outside a physical safe area, where you don't have sufficient time to shut down the computer in case of physical intrusion.

-Don't leave the safe area yourself, to prevent unpleasant encounters.

I very well know this is beyond the needs of most (nearly all) people, but the subject was preventing leak of data. Although my list is a little long I'm sure it is not exhaustive on the subject.

ekh

Ok, that's like the ultimate counter-surveillance guide... Thanks!

---

### Post by panhandle on 2008-08-28
```
-Prepare to withstand torture, and die for the data, especially if the data can severely compromise yourself, your dear ones, your country or the humanity.
```

Wow...I, uh, just use ABP and NoScript. :lolflag:

---

### Post by Jive Turkey on 2009-12-31
xkcd covered this one pretty well:
[http://xkcd.com/538/]("http://xkcd.com/538/")

---

### Post by perrabyte on 2009-12-31
If you look at the difficulty of recovering files from various systems I think RAID 0 together with encryption could be of use. Say you make an array of 8+8 GB with one internal partition and a SDHC-card you could just easily destroy that single SDHC-card instead. I doubt there is an easy way to recover any files if one whole partition is missing regardless of computer power or equipment.

Since its a very fragile system. Backups are necessary though, as always.

---

### Post by BkkBonanza on 2010-01-01
Regarding data remanence on drives - what used to be considered feasible is no longer regarded so on modern drives. The wikipedia has some good articles on the subject and links to in depth references. I read through a lot of this a few months back and came to the conclusion that 1 or 2 passes of random and a zero wipe is really sufficient with modern drives even for law enforcement cases. 

[http://en.wikipedia.org/wiki/File_wipe](http://en.wikipedia.org/wiki/File_wipe)

Even Gutmann, who wrote the original work on methods for wiping securely, says his ideas have been taken out of appropriate context and a whole mythology has grown from them.

[http://en.wikipedia.org/wiki/Gutmann_method](http://en.wikipedia.org/wiki/Gutmann_method)

I'd love to read up on a court case where they actually used an electron microscope to recover data but so far I have never heard of that. I suspect that even so the error margin on recovery would allow statistically for almost any given dataset to be pulled from such a drive and make it very questionable.

Regarding the journaling file systems I believe it's possible to remount with ordered mode and then wipe and then revert back to journal mode. I read about this somewhere but since I don't use it anyway, I never tried it.

---

