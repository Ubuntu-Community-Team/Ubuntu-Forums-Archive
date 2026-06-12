---
title: "Hibernate with encrypted SWAP"
date: 2015-03-06
forum: Security
---

### Post by humanoverdrive on 2015-03-06
Hello all,

So I have a question regarding what is possible regarding hibernation with encrypted SWAP partition.  I am already aware of the solution presented [here]("https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap"); however, the necessity of utilizing a 2nd user-defined LUKs password is not an ideal solution for me.

So my question is whether any of the following 3 alternative options could be potential alternative solutions, and if so, how one might go about implementing them:
[LIST=1]
[*]Instead of decrypting the SWAP partition initially with a LUKs password, could the SWAP instead be decrypted at the same time as my home directory DURING LOGIN using my login credentials?  For this solution, I would be fine with a large delay in startup after logging in, as hibernation is more important to be for it's ability to preserve and resume my previous session state (open documents, etc) than it is for its ability to decrease boot times into a full state.
[*]Alternatively, could the SWAP partition be decrypted AFTER login, and then the previous system state applied on top of my new "fresh" state?  I.e. I log in to a new session, then decrypt the SWAP partition, and the now decrypted hibernation data is applied to the current session, opening previously open applications along with all content previously entered into said applications (e.g. like opening a word document I was previously working on in the same state it was in when I hibernated my computer).
[*]If none of the above are possible, would it be possible to load the system resources early enough in the boot process that would be required in order to use something like a [YubiKey]("https://www.yubico.com") to provide the system with the LUKs password?
[/LIST]

I apologize if these questions are ridiculous, I am rather new to encryption and how the whole hibernation system works on an Ubuntu machine.

Thanks!

---

### Post by sudodus on 2015-03-07
After some testing of 'Encrypted disk' and 'Encrypted home', I have found that 'Encrypted home' is quite buggy. It is possible to make cryptswap work with some special tweaks, but it does not work 'out of the box'. See these links
[URL="http://ubuntuforums.org/showthread.php?t=2267845"]
Please discuss encrypted home - is it useful or not?[/URL]
[LVM encrypted disk & encrypted home in Lubuntu Vivid complicated or buggy]("http://ubuntuforums.org/showthread.php?t=2266912")
the bug report [https://bugs.launchpad.net/ubuntu/+s.../+bug/1310058/]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058/")

After some reading, for example at the following link [https://wiki.archlinux.org/index.php/disk_encryption](https://wiki.archlinux.org/index.php/disk_encryption) I think that 'Encrypted disk' is better than 'Encrypted home'.

---

### Post by humanoverdrive on 2015-03-10
So you are suggesting that I set up my Ubuntu install as an LVM and encrypt the whole disk?  Right now I am NOT utilizing LVM, I have my hard drive divided into 2 fixed size partitions, a system partition and a SWAP partition, so that would pretty much require me to do a fresh install if I wanted to switch to LVM.  I also have a few preferences for set partitions over LVM.

So far I have had zero issues in getting the encryption on both of those partitions working.  In fact, following the [above referenced solution on enabling hibernation with an encrypted SWAP]("https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap"), I have been able to successfully implement hibernation with BOTH an encrypted System partition and SWAP partition through use of cryptswap and a LUKS password; however, as I previously stated, this is not an ideal solution for me.  I understand your point regarding use of LVM instead, however could you (or anyone else who might be reading this), please address my actual question and let me know if any of the 3 solutions I presented are at all possible?

---

### Post by sudodus on 2015-03-10
I stumbled into the problem with encrypted home and cryptswap because I'm iso-testing Lubuntu, and found that one of the test-cases no longer works. So I'm really no expert in encryption, and I can't give you good answers to the three questions in your opening post (post #1). ***Let us hope that someone who knows will chip in and give you good advice*** :-)

I think it would help giving good advice if you explain why you want a special solution. What do you want to achieve? Why would those alternatives be better than what you have now?

It might be worthwhile to read the following link for more information about different encryption methods:

[https://wiki.archlinux.org/index.php/disk_encryption](https://wiki.archlinux.org/index.php/disk_encryption)

---

### Post by humanoverdrive on 2015-03-11
There isn't really a special reason why I would like one of the 3 cases I outlined to work other than simplicity; it would just be nice to be able to log in with 1 password rather than 2.  As I also tend to be a bit OCD when it comes to my digital security and typically have very long, complicated passwords, having to remember only 1 password instead of 2 would be ideal.

Additionally, while not the norm, I have noticed that once in a while I actually do encounter 1 slight issue with the encryption (perhaps the same issue you ran into), namely the SWAP partition not decrypting after entering my LUKs password.  This prevents the system from resuming from hibernate and boots a new session instead.  Quite annoying to say the least.

---

### Post by sudodus on 2015-03-11
I think it is risky to tamper with encrypted systems, or make own encrypted systems. It is so easy to overlook some security hole. For that reason I suggest that you use the standard method offered by the Ubuntu flavours: Encrypted disk with LVM (and without encrypted home). You can always let the user log in automatically into the user (so only login once, into the encrypted disk system). But in order to remember the user password for sudo (superuser) tasks, it might be a good idea to have the same password as the disk password, or a natural part of it.

---

### Post by humanoverdrive on 2015-03-11
I'm not looking to make my own encryption system, and I currently AM using a "standard method" of encryption. Using encryption with an LVM formatted disk is not the only "standard method" of encryption in Ubuntu. In fact, the encryption of my root directory, which I set up using the prompts to do so upon installing Ubuntu, works flawlessly. The only issue (which I have already solved, just not to my liking) is in also encrypting my SWAP partition. I could easily solve this issue by using a SWAP file rather than a SWAP partition, but I prefer SWAP partitions over files for a few reasons, including performance.

I currently have my disk formatted into 2 fixed logical partitions, and not only do I not feel like completely reformatting my disk to use LVM instead, which would be a total pain in the ass, but for this application I prefer logical partitions over LVM.

That being said, let me reiterate, I am not looking to use my own encryption or anything like that, I am simply attempting to make it possible to either
A) restore my hibernated state AFTER logging in to a new state and decrypting my root directory and SWAP as normal by simply logging in to my account, or
B) decrypt my SWAP partition WHILE logging in without the need for a LUKS password in addition to my account password

---

### Post by sudodus on 2015-03-12
I understand your reasons to do what you do and to try to improve it. I'm sorry, but I cannot help you much. I really hope that someone with more experience will find this thread and help you with some real advice about the technical details.

---

### Post by HermanAB on 2015-03-12
Howdy,

There is a simple solution: Encrypt your disk and use a swap file.  Read 'man swapon' for details on making a swap file.

---

