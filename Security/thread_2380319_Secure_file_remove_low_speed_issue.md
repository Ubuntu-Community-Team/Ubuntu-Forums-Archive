---
title: "Secure file remove low speed issue"
date: 2017-12-15
forum: Security
---

### Post by norian on 2017-12-15
Hello 
When I try to delete files with SRM using flags -rvz 
[HTML]sudo srm -rvz *file*[/HTML]
It took like 16 hours for a 5GB file and file wasn't deleted yet, I canceled this process. I think it's too much time.
There is a software called Eraser for Windows and it take like 1 hour to delete a 5GB file.

For both software Eraser and SRM i'm using Gutmann method. Only difference it's in Windows I'm deleting from NTFS volume and using Ubuntu i'm deleting from Ext4
Also I checked read/write speed for drives and speed is okay.
What can be the problem ? I

---

### Post by agillator on 2017-12-15
You say you are using the Gutmann method. That can mean several things. My initial guess is that your 'problem' is the number of overwrites you are trying to do. At one time the recommendation was 30. For a 5GB file you can imagine that would take some time, a lot of time. New hard drives pack much more data in the same space and are far more accurate so fewer overwrites are necessary. In fact I have seen some recommendations that a single overwrite with modern equipment is adequate. I am paranoid and always do at least 3. I am no expert, but then the world won't end if the NSA can still recover some of my data. So, check the configuration of your srm. I suspect the default number of overwrites is large. If so, reduce it. If not, the problem is somewhere else. I would not use windows as a comparison since I would trust windows about as far as I could throw Redmond, which isn't very far. But then that is only my personal opinion. If you think you still have a problem try using 'wipe' or one of the other secure removal programs and see if that helps.

---

### Post by norian on 2017-12-16
srm number of overwrites using Gutmann method is 38 passes and Eraser using Gutmann method is 35 passes. So with srm it need to overwrite like 200 GB for 5 GB. So if speed is 100-150MB/s it gonna take like 3-4 hours. Are my calculations correct ?
So last time it took like 10+ hours and I canceled srm.

Thanks agillator. I will try to do it once again using srm. If it will be the same I will try to use another tool. I just wanted to use srm cause I think it's most powerful tool for secure removal.

---

### Post by HermanAB on 2017-12-17
Hmm, this is why it is best to encrypt a disk.  With encryption, the data saved on disk is always random.  If you want to securely erase something, just forget the key.

---

### Post by norian on 2017-12-19
So I just do a test, I tried to delete a 5GB file using wipe. It took ~8hours for 2 passes and ETA was 6days.
In Windows using eraser and Gutmann method (same method as wipe use) it took less than one hour for a 2GB time.
The write/read speed is almost the same for both OS

---

### Post by HermanAB on 2017-12-20
Howdy,

First you need to figure out what is the threat that you are trying to protect against.  If the threat is your little kid sister, then erasing a file once the usual way is good enough.  If your threat is a government, then srm is not good enough.  

As far as I can tell, srm is a toy, that is good at wasting time and wearing out disk drives, but it has severe flaws/omissions regarding its erase function, with the result that it may not really work any better than a single erase/overwrite.

Some of the issues to consider are:
1. The file system: Does it have a journal?  If so, you need to erase the journal also.  (NTFS and most Linux file systems do).  There is no easy way to erase the journals.
2. The disk drive: Is it spinning metal or Flash?  If metal, then you need to erase bad blocks also (mostly impossible).  If Flash, then a single overwrite is enough and ditto for the bad blocks.
3. Copies of the file may be in the home directory, in the tmp directory and in the swap file/partition.  These need to be erased also, but how can you do that, if you don't know what or where they are?

If you encrypt the whole disk, then all of the above are taken care of and then you need not do anything special to erase a file.  All you need to do is hit yourself upside the head with a brick to forget the password...

---

