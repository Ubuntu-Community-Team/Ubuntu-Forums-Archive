---
title: "Multiple layers of encryption"
date: 2010-01-12
forum: Security
---

### Post by Ebuntor on 2010-01-12
Hi everyone,

I've got a question: Does encrypting a file multiple times give better security?

A friend of mine is storing some very sensitive info, he uses TrueCrypt to encrypt his files. As I understand it he made three a TrueCrypt containers in each other using cascade algorithms (AES-Twofish-Serpent).

He made a container, then he put that container in a second container, again using a cascade algorithm. Finally for third time he put the second container in a third container.

Now it has been years since I learned about encryption at my university but I can vaguely remember reading that it wasn't a good idea to encrypt the same file multiple times, or that it was pointless because it didn't offer better protection, something like that.

---

### Post by juancarlospaco on 2010-01-12
Common encryption method uses multiple encryption pases, usually 3 times...

---

### Post by blueshiftoverwatch on 2010-01-12
> **Ebuntor said:**
> I can vaguely remember reading that it wasn't a good idea to encrypt the same file multiple times, or that it was pointless because it didn't offer better protection, something like that.
It will decrease read/write performance in relation to modifying that particular file/folder(s). But I don't know that it'll actually compromise security. There was a debate somewhere in [this thread]("http://ubuntuforums.org/showthread.php?t=1334368") about whether encrypting with multiple layers was a good idea. I think the general consensus was that it won't hurt anything. But it'll just slow things down. I would imagine that it'd provide more security. Assuming that you used a different passphrase for every layer of encryption.

---

### Post by Xbehave on 2010-01-12
> **Ebuntor said:**
> Now it has been years since I learned about encryption at my university but I can vaguely remember reading that it wasn't a good idea to encrypt the same file multiple times, or that it was pointless because it didn't offer better protection, something like that.
Theoretically pointless yes, but in the real world you don't crack the crypto anyway.
- instead of 1 long password he has 3 shorter password, this is less safe (cracking 3 10char passwords is easier than 1 30char)
+ he may be using multiple levels of hidden partitions meaning if anybody gets in they won't know they haven't found the real files (and if they do, they may think it's just another layer of deception)

re cascade algorithms (i.e multiple encryption with different algorithms), it means that if a weakness is found in one algorithm cracking the other two is still hard and cracking the crypo is all or nothing because unencrypted randomnes looks the same as encrypted randomness.

---

### Post by MasterNetra on 2010-01-12
> **Xbehave said:**
> Theoretically pointless yes, but in the real world you don't crack the crypto anyway.
- instead of 1 long password he has 3 shorter password, this is less safe (cracking 3 10char passwords is easier than 1 30char)
+ he may be using multiple levels of hidden partitions meaning if anybody gets in they won't know they haven't found the real files (and if they do, they may think it's just another layer of deception)

re cascade algorithms (i.e multiple encryption with different algorithms), it means that if a weakness is found in one algorithm cracking the other two is still hard and cracking the crypo is all or nothing because unencrypted randomnes looks the same as encrypted randomness.

I usually use passwords near 30 chars on important stuff anyway. And sometimes 20+ char passwords just for logining into the computer. My storage computer uses Fedora 12 and has a 30+ char password on the hard drive alone....Don't really need it I suppose just put on for the fun of it I guess...

---

### Post by Xbehave on 2010-01-12
> **MasterNetra said:**
> I usually use passwords near 30 chars on important stuff anyway. And sometimes 20+ char passwords just for logining into the computer. My storage computer uses Fedora 12 and has a 30+ char password on the hard drive alone....Don't really need it I suppose just put on for the fun of it I guess...
The numbers i used are arbitrary, the point still stands if you sub in 10 for 100, hes likely to use 3 100char passwords instead of 1 300char password. While 30+ char passwords are cool and all 16 is safe for the foreseeable future and much more practical (i mean whats the point in 10second boot if it takes you another 10 to type your password, 9 is more than enough for a local login password that can't be brute forced, if anybody is going to type out ~700 thousand trillion passwords well they can have access to my files.

---

### Post by gsmanners on 2010-01-12
The thing about all encryption is that simply looking at the data usually reveals the fact that there is data to be found. This is where steganography can really come in handy.

---

### Post by cariboo on 2010-01-12
This thread belongs here in Security Discussion, not the Cafe. Moved.

---

### Post by HermanAB on 2010-01-13
Hmm, he used Truecrypt only?  So the same flaw will work against all three layers.  It would be better to use three different encryption systems.  

However, unless he also uses whole disk encryption, a plain text copy of his data is likely remaining somewhere on the machine file system anyway.

---

### Post by NiGhtMarEs0nWax on 2010-01-13
AES is uncrackable as far as i know, a 30 character password with upper/lower case / Special characters & numbers ie the full Latin-1 range has about 255^30 combinations.  ie some 255000000000000000000000000000000 possible passwords. its virtually uncrackable even with the fastest computers on the planet afaik.

i could be wrong though; that's just my best guess from my experience.

---

### Post by dogdo on 2010-01-13
So how does encfs compare to truecrypt?

---

### Post by Ebuntor on 2010-01-13
> **HermanAB said:**
> Hmm, he used Truecrypt only?  So the same flaw will work against all three layers.  It would be better to use three different encryption systems.  

However, unless he also uses whole disk encryption, a plain text copy of his data is likely remaining somewhere on the machine file system anyway.

I see, no he doesn't use full disk encryption. How could someone obtain a plain text version of is data? Via backup files? A cold boot attack?

---

### Post by Xbehave on 2010-01-14
> **Ebuntor said:**
> I see, no he doesn't use full disk encryption. How could someone obtain a plain text version of is data? Via backup files? A cold boot attack?
There is a chance that the password gets pushed out to swap. While I think truecrypt can keep the key in active ram to avoid this and forgets the passwords as soon as you type it, any data being used can be swapped out along with the program using it and due to the way Linux handles swap, closing the program will not get rid of the data (unless truecrypt does something clever, which i don't think it does).

The solution is to encrypt the swap partition (however that breaks hibernation, unless there is some clever work around)
Alternatively (i.e encrypting swap is the right way to do this, this is just a random thought), you could
1) close truecrypt (and all relevant programs)
2) make a swapfile to hold all important swap data
3) close the swap partition
4) wipe the swap partition (dd if=/dev/urandom of=/dev/<swap partion>...)
5) remount swap partition
6) delete swapfile

---

### Post by Ebuntor on 2010-01-14
> **Xbehave said:**
> There is a chance that the password gets pushed out to swap. While I think truecrypt can keep the key in active ram to avoid this and forgets the passwords as soon as you type it, any data being used can be swapped out along with the program using it and due to the way Linux handles swap, closing the program will not get rid of the data (unless truecrypt does something clever, which i don't think it does).

The solution is to encrypt the swap partition (however that breaks hibernation, unless there is some clever work around)
Alternatively (i.e encrypting swap is the right way to do this, this is just a random thought), you could
1) close truecrypt (and all relevant programs)
2) make a swapfile to hold all important swap data
3) close the swap partition
4) wipe the swap partition (dd if=/dev/urandom of=/dev/<swap partion>...)
5) remount swap partition
6) delete swapfile

Hmmm, seems a lot easier to just use full disk encryption for Linux. I also forgot to mention my friend uses Windows primarily. 

If I remember correctly Windows uses paging, the page file is in root directory of the partition where Windows is installed, right? Sounds to me Windows needs full disk encryption just as much as Linux, maybe even more.

---

### Post by Xbehave on 2010-01-14
> **Ebuntor said:**
> If I remember correctly Windows uses paging, the page file is in root directory of the partition where Windows is installed, right? Sounds to me Windows needs full disk encryption just as much as Linux, maybe even more.
It's always a trade off.

Full disk encryption means somebody needs to steal your computer without you noticing and install a bootloader rootkit/hw keylogger
Just encrypting your swap/page file (not sure if windows can do that), means that somebody needs to steal your computer without you noticing and install a normal rootkit, but is a lot less trouble to work with (no need for a preboot password)
My crazy suggestion gives the same security as encrypting your swap/page but is vulnerable if your hdd heads move slightly (i think this attack was shown to be too hard to bother with), but allows you to hibernate
Not encrypting anything but your secret files is pretty safe though, you have to be unlucky for it to be swapped and left there just before your computer is stolen.

Sorry for being so verbose, but basically
FDE=v.good but a pain
swap=good enough and easy
nothing=probably fine

---

