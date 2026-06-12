---
title: "Encrypt disk without formatting? Something similar to BitLocker?"
date: 2016-06-16
forum: Security
---

### Post by provotector on 2016-06-16
Hi. I have a 500GB Usb disk unit formatted with ext4. I need to encrypt the entire unit. All methods that I found, need to format the unit before encrypting. 

I need to protect the data, not erase that or format. There's any way to do this without copy all data to another unit, format, encrypt and paste the data again? Anithing similar to Windows Bitlocker that protects the data inside the drive, without formatting?

Best regards.

---

### Post by TheFu on 2016-06-16
Welcome to the forums.

You can use one of the less-secure file encryption methods.  encfs or encryptfs are options.  But it really depends on why you are encrypting.  If this is to meet some legal requirement, then using luks is really the best practice and should be followed.  File-based encryption leaks metadata for the files.

[https://help.ubuntu.com/community/FolderEncryption](https://help.ubuntu.com/community/FolderEncryption)
[https://www.howtoforge.com/tutorial/encrypt-your-data-with-encfs-on-ubuntu/](https://www.howtoforge.com/tutorial/encrypt-your-data-with-encfs-on-ubuntu/)

Be aware:
* [https://defuse.ca/audits/encfs.htm](https://defuse.ca/audits/encfs.htm)
* [https://defuse.ca/audits/ecryptfs.htm](https://defuse.ca/audits/ecryptfs.htm)

Also, when using any method of encryption, having 100% know-you-can-restore backups is mandatory.  A tiny area of corruption on any disk can make the entire encryption become lost.  I´d simply use the backup method you are already using to migrate to LUKS encrypted partition(s) and use LVM under it to make LVs which would be mounted.  But that is me.

Good luck.

---

### Post by provotector on 2016-06-17
Hi and thanks for the reply! My problem is that I'm not using any system backup method. I only dissasemmblied a disk from one computer, and I need to encrypt the data that contains. Because that, I'm not interested in formatting the unit... I will try with one of your "less secure" methods. ¡¡¡thank you a lot!!!

---

### Post by provotector on 2016-06-17
Ok... this not solve my problem... I have a 500GB unit and I NOT want to move data. Only encrypt. Windows bitlocker encrypts te entyre unit and go. The encfs method need to copy/paste all the data from the unit to the encrypted folder. I not want to move data, only encrypt, because there is a lot of data and copying/pastings will take a lot of time...

How can encrypt entire hard disk unit with ubuntu? Without moving files, formatting units, copy/pastings, lossing data...etc? Is impossible????? Is not any similar to Bitlocker in the Linux world???

I tryed this: [http://blog.sambull.org/easily-encrypt-folders-2/](http://blog.sambull.org/easily-encrypt-folders-2/) But I'm not using Nautilus. I'm in Linux mint and that's not working...

---

### Post by mikodo on 2016-06-17
I see you didn't mention trying eCryptfs in the earlier post. For your decided upon usage of encryption you could try that. Like TheFu above, I too think a backup is mandatory. See TheFu's post why.

To start your learning about eCryptfs, see this link: [https://wiki.archlinux.org/index.php/ECryptfs](https://wiki.archlinux.org/index.php/ECryptfs)

See section [3.3] Backup

And a little more from Ubuntu: [https://help.ubuntu.com/12.04/serverguide/ecryptfs.html](https://help.ubuntu.com/12.04/serverguide/ecryptfs.html)

I hope this helps.

---

### Post by provotector on 2016-06-17
You don't understand me. Sorry.

With eCryptfs I need to copy/paste the 500GB of my source HDD to another HDD to have the "encrypted" directory. I will need to add another HDD to my computer to move the files to it and I no have more disks and no have a PC case where I can add 2 HDD.

I need only to encrypt my 500GB HDD, not moving the data to another disk or copy/paste or adding disks. Only encrypt is not possible in Linux????????  Without copy pasting, or moving data?? With Windows Bit locker I can do that, not in Linux???? I only have the option to copy my entire 500GB unit to another "encrypted" unit???

---

### Post by mikodo on 2016-06-17
Hi again.

Have a look at this. Maybe it is more fitting for your needs:

dm-crypt:  [https://wiki.archlinux.org/index.php/Dm-crypt/Encrypting_a_non-root_file_system](https://wiki.archlinux.org/index.php/Dm-crypt/Encrypting_a_non-root_file_system)

[I]"Encrypting a secondary filesystem usually protects only sensitive data,  while leaving the operating system and program files unencrypted. This  is useful for encrypting an external medium, such as a USB drive, so  that it can be moved to different computers securely. One might also  choose to encrypt sets of data separately according to who has access to  it".  
[/I]
You might find having a cheap hard drive enclosure that you can connect your drive by usb to your computer to encrypt with dm-crypt would work.

But, It might again entail you using two drives. One you encrypt and then moving the data from the other drive on to the encrypted drive.

[URL="http://www.vantecusa.com/en/product/view_detail/676"]http://www.vantecusa.com/en/product/view_detail/676

[/URL]

---

### Post by TheFu on 2016-06-17
> **provotector said:**
> Hi and thanks for the reply! My problem is that I'm not using any system backup method. I only dissasemmblied a disk from one computer, and I need to encrypt the data that contains. Because that, I'm not interested in formatting the unit... I will try with one of your "less secure" methods. ¡¡¡thank you a lot!!!

Just so I understand this ... the data is important enough to be encrypted, but not important enough to backup before attempting a highly risky process like encryption?  100% data loss is acceptable?

---

### Post by xen3 on 2016-06-17
> **provotector said:**
> You don't understand me. Sorry.

With eCryptfs I need to copy/paste the 500GB of my source HDD to another HDD to have the "encrypted" directory. I will need to add another HDD to my computer to move the files to it and I no have more disks and no have a PC case where I can add 2 HDD.

I need only to encrypt my 500GB HDD, not moving the data to another disk or copy/paste or adding disks. Only encrypt is not possible in Linux????????  Without copy pasting, or moving data?? With Windows Bit locker I can do that, not in Linux???? I only have the option to copy my entire 500GB unit to another "encrypted" unit???

Yeah, people are not answering your question, they are trying to make you do what they like more.

The only thing I can possibly recommend, without having used it, is VeraCrypt. VeraCrypt is a further development of TrueCrypt. I know TrueCrypt on Windows can encrypt existing harddrives; whether VeraCrypt can do this on Linux, is for me a big question. But if VeraCrypt cannot do it, nothing else can either.

Anything else requires moving data around. eCryptFS is not a solution at all, this is not a good way to encrypt an entire harddrive and is rife with complications.

If you seriously have no access to a spare drive for storing this information while you encrypt the drive (or set it up for encryption) that you want the data to end up on, you can only try to move stuff around on the same drive, which is complicated and annoying. You did not mention what filesystem or filesystems are currently on the drive, and what partitions, if any, if any more than one.

If there are multiple partitions, then you can try moving the data around. However, if the disk is filled, you will need to either use TrueCrypt from Windows (or VeraCrypt) or use a spare drive; a TrueCrypt or VeraCrypt encrypted drive will be accessible in Linux (and Ubuntu).

If you do have a spare drive, you must realize that TrueCrypt/VeraCrypt can encrypt entire drives including the partition table, but on Linux using "LUKS" the setup is more complicated, and you will need to have at least a partition table, a partition, a LUKS container in that partition (meaning that that partition is now encrypted) and then an LVM (logical volume system) inside the LUKS, and then the actual partitions inside THAT. For this reason, if it is an external drive, I think I would recommend TrueCrypt or VeraCrypt.

That would also make it cross-platform (compatible with Windows) depending on what filesystem you use.

In that case, copying the data (file by file, so to speak) would probably be easier than trying to "image" the disk and backing that up. A second hand harddrive would be dirt cheap.

I know TrueCrypt on Windows can encrypt stuff in place, but this is mostly meant for running systems (which Linux can't do anyway). However, there is really no such capability in Linux.

Your best bet would be to use a Windows computer. At the same time, I don't know if TrueCrypt/VeraCrypt can handle "entire encrypted disks" in Linux, but I think they can. I am pretty sure they can. Would need to test though. I can, if you want. I can wipe some flash card to test it on, if needed.

> **TheFu said:**
> Just so I understand this ... the data is important enough to be encrypted, but not important enough to backup before attempting a highly risky process like encryption? 100% data loss is acceptable?

Oh, by the way, encrypting data on Windows using TrueCrypt is not risky, it maintains an internal pointer (on disk) as to what part has been encrypted already, and you can take off where you've started last time. In case of system encryption it also asks you to test your boot procedure, and it that fails, it won't do it for you. If also forces you basically (almost) to burn a rescue DVD or CD. The only thing risky about TrueCrypt is losing your password.

And "system backup" scenario's are rather complex and hard to set up without good software, and on Linux that mostly means having to do a lot of work, unless you have an external drive and you use something like FreeFileSync.

But encryption itself is not the most risky thing there is, at least not from a technical perspective.

---

### Post by TheFu on 2016-06-17
I do feel like I 
a) answered the question
b) provided guidance based on decades of experience WHY that is a less-good solution

What the OP does is completely up to him. 

Just trying to provide options which are generally agreed within the community to be better (for certain values of "better").  I used encryptfs for about a year. It was a poor choice for my needs, which I later learned was best solved by using dm-crypt with LUKS.  LUKS does NOT require the use of LVM, BTW. [https://www.linux.com/learn/how-encrypt-linux-file-system-dm-crypt](https://www.linux.com/learn/how-encrypt-linux-file-system-dm-crypt) .  LVM just provides extra flexibility, if desired.

Ecryptfs does NOT require another disk or even another partition.  It is only if someone uses the encrypt-home-directory scripts where that comes to play. That is a choice, not mandatory.
[https://askubuntu.com/questions/574110/how-to-use-ecryptfs-with-a-random-directory](https://askubuntu.com/questions/574110/how-to-use-ecryptfs-with-a-random-directory) provides a solution to encrypting any directory. 

We all have different modes of operation.  For example, I do not consider TrueCrypt as a viable option. It is unsupported. The developers have warned against using it. With that said, I have used truecrypt previously for many years, but only on Windows. 

Why, besides the side-attack vectors and metadata leakage, is encryptfs NOT a viable solution here? Please be specific.  Teach me Obiwan.

Ever had an encrypted file or partition become corrupted?  Complete data loss was the result for me. Perhaps I'm just an idiot. Hard to say. I do know that backups were used to get the data back after normal data recovery attempts failed directly on the encrypted volume. IME, it is best to assume data loss will happen and to be prepared. YMMV.  Not having backups is a choice.

---

### Post by xen3 on 2016-06-17
I don't see there is a reason to answer those cynical questions.

Apparently it is possible to simply create an encFS or ecryptFS managed folder and move everything into that without requiring more space. I think that was the gist of your answer. However the OP indicated not understanding that, but no one responded with clarification. Depending of course on how big the files are and how much space is available.

So maybe I was mistaken about my rad response above, however no one elucidated why encFS or ecryptFS would work.

Personally I would choose death over using eCryptFS, but that is beside the question here.

In general answering questions by providing more questions (more stuff to research) is not a very helpful thing to do. And of course, yes, you can create a filesystem directly on LUKS, I'm sorry.

But providing a link to someone does not answer the "why" (something would work).

And you also know TrueCrypt is only said to be "unsafe" in case further attacks against known and used ciphers, are revealed. But I guess, this is something the VeraCrypt developers have taken on.......

But also beside the point. In any case, the OP asked whether there was something similar to BitLocker, and no one answered, but the answer is simply no.

You must start with the question, not with what you want the answer to be. The question is in the title to this thread. The answer is a very simple "no". I don't see any of you mentioning that "no" anywhere. Hence, you did not answer the question.

If I ask you how much liters of water go into a can, and you answer "5 kilograms" then that is not an answer, even though it might be slightly correct.

Learn how to answer questions please. It would save everyone a lot of time. The simple answer is that, no, this thing does not exist, but encFS or ecryptFS may be able to move individual files from "nonencrypted" to "encrypted", hence not requiring much space.

So basically

"[COLOR=#000000]The encfs method need to copy/paste all the data from the unit to the encrypted folder. I not want to move data, only encrypt, because there is a lot of data and copying/pastings will take a lot of time..."

[/COLOR]Was incorrect, but no one told him that.? Moving data in this sense IS encrypting it.

It just happens file by file, hence requiring little space, and I guess that was the answer??? It's not like "encrypting on the spot" will be any faster than moving it into an eCryptFS folder.

---

