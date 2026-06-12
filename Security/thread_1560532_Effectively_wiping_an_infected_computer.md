---
title: "Effectively wiping an infected computer?"
date: 2010-08-25
forum: Security
---

### Post by I_Want_To_Learn on 2010-08-25
Hello ):P

Before I begin, I should warn everybody reading that I suffer from paranoia. :(

Getting a hand-me-down computer. The past owner was a Windows user who didn't care about computer security. Had numerous encounters with viruses & malware. I want to completely wipe the computer & install Ubuntu. I already know that the vast majority of viruses wont work on Ubuntu (I'm so glad for that), but it's still not absolute.

What is the best method to wipe this computer so I can be certain (although in life, nothing is certain) anything malicious is deleted? I want to be able to wipe the disk multiple times, including the MBR as a precaution.

Is the tools on Ubuntu's Live CD (DD, Shred, Wipe, etc.) the best way to accomplish this? I know there is DBAN, but I currently don't have a computer I could confidently say is "clean". If so, what are the correct commands to enter (still not great with commands & don't want to make a mistake that will harm my computer)?

Thank You

---

### Post by cascade9 on 2010-08-25
Just deleting the current windows partitions and creating new linux partitions should do the trick. 

DBAN, etc, are more for wiping the drive so that no data is recoverable.

---

### Post by mikewhatever on 2010-08-25
A simple formatting during the installation is enough.
In case you want that data completely gone, there are guides on youtube.
[http://www.youtube.com/results?search_query=hdd+destruction&aq=0](http://www.youtube.com/results?search_query=hdd+destruction&aq=0)

---

### Post by I_Want_To_Learn on 2010-08-25
Yup, I know the only way to completely remove everything from a HD would be to destroy it,but that's not an option for me :D. I would like to wipe the entire HD for peace of mind.

After doing some homework, is this the correct procedure to wipe the entire HD including the MBR?

1) Boot live session from Ubuntu Live CD.

2) Open Terminal & use either one of the commands below:

For DD

```
sudo dd if=/dev/urandom of=/dev/sdx
```

For Shred

```
sudo shred /dev/sdx -f -v -z
```

Where sdx is the name of the HD. Shouldn't put sdx1 since that only wipes the partition.

3) Shutdown & reboot with Live CD. Install Ubuntu.

I read in a thread that shred uses the same urandom method as DD, is this correct?

Thanks

---

### Post by rookcifer on 2010-08-25
> **I_Want_To_Learn said:**
> 
For Shred

```
sudo shred /dev/sdx -f -v -z
```

Where sdx is the name of the HD. Shouldn't put sdx1 since that only wipes the partition.

You have that command a bit reversed.  It should be:

```
sudo shred -fvz /dev/sdx
```

> I read in a thread that shred uses the same urandom method as DD, is this correct?

The command above writes zeros to the drive.  /dev/urandom writes random data.  Shred can also be used to write random data, though I see little point in doing so in your case.

---

### Post by Hobgoblin on 2010-08-25
> **I_Want_To_Learn said:**
> Yup, I know the only way to completely remove everything from a HD would be to destroy it,but that's not an option for me :D. I would like to wipe the entire HD for peace of mind.


There is no need to do anything complicated.

Just boot from the liveCD and opt to use the whole HDD for the Ubuntu installation.

That will wipe the drive to an unreadable state by any normal means, effectively removing any viruses.

Any more than that is wasting your time.

---

### Post by Bucky Ball on 2010-08-25
I wouldn't be too paranoid about this one. No Windows virus is going to make any difference to a Ubuntu install. May as well not be there anyway. Put install disk in and tell ubuntu to use the entire drive, as mentioned, or manual partition and use the whole thing however you want leaving free space if you like (that will mark the drive as 'writeable' basically). When you delete something in the course of everyday computing it marks that part of the drive as writable, that is all. It doesn't actually remove anything. That happens when you write new data onto the marked 'writable' section. It overwrites what was there.

Second hand information from a previous user; who wants it and who will come looking? Windows viruses in Linux? Irrelevant.

---

### Post by BkkBonanza on 2010-08-26
After installing you could use the **sfill** cmd from secure-delete pkg to wipe the free space. That way anything not overwritten by the install will be wiped clean. That would be an adequate amount of paranoia.

---

### Post by DavidOfLondon on 2010-08-26
"I wouldn't be too paranoid about this one. No Windows virus is going to make any difference to a Ubuntu install."

This is the sensible answer. Unless you're planning to take over the White House I fail to see what you're concerned about - you're using this forum which means your IP is visible to every mod who logs in anyway.

Linux is super safe because it's super-unused (currently). Install the firewall and turn it on and you're set to go. Nothing migrates from a windows-free, wiped hard drive. It simply doesn't. The analogy is to ask whether you can catch feline flu because a cat lived in your apartment during the 1970s :)

If you're hyper-worried just zero the hard drive from the boot up screen (look for the prompt -Esc/F8 -  depends on maker) and expect this to take quite a long time. Zeroing guarantees it's officially empty for ever and every Amen.

No one is ever going to hack your Linux OS from over the internet unless you're doing something truly foolish like using hacking software.

---

### Post by spynappels on 2010-08-26
> **DavidOfLondon said:**
> 
Linux is super safe because it's super-unused (currently). 


Ok, I'll bite. This statement is false. Linux is not super-unused, Linux servers serve the majority of the internet, and the perceived underuse in the desktop arena is only a small part of the reason for it being a safe and secure OS. Sweeping statements like the above are not helpful because they imply if more people used Linux, it would be considerably less safe.

> **DavidOfLondon said:**
> 
No one is ever going to hack your Linux OS from over the internet unless you're doing something truly foolish like using hacking software.


Again untrue. There are areas where users need education, else they may make their systems vulnerable. A good example is allowing VNC access to their system without setting a password. That is why BodhiZazen and others spend so much time trying to educate users on here.

To the OP, a clean install will be sufficient but if you have doubts, do a shred before installing the system. Also, invest some time in reading the security sticky and learn how to further secure an already safe and secure OS. Also do not be afraid to ask questions and search the forums, it is how many of us learned.

---

### Post by DavidOfLondon on 2010-08-27
I think you ought to learn to separate a superlative from an exaggeration before quoting me as if I were speaking 'ex cathedra'.

Of course the guy can get hacked. Is it likely? 

No.

Even less likely if he's using a Linux OS?

Yes.

What is wrong with you long-term users? You perceive your use of the verb 'to inform' as though it covers 'to denigrate', 'to snot', and 'to look better informed'.

Not exactly 'community spirit'.

---

### Post by rookcifer on 2010-08-27
> **DavidOfLondon said:**
> I think you ought to learn to separate a superlative from an exaggeration before quoting me as if I were speaking 'ex cathedra'.

Of course the guy can get hacked. Is it likely? 

No.

Even less likely if he's using a Linux OS?

Yes.

What is wrong with you long-term users? You perceive your use of the verb 'to inform' as though it covers 'to denigrate', 'to snot', and 'to look better informed'.

Not exactly 'community spirit'.


Nah, he was just correcting your false assumption that Linux is more secure because "it is super unused."  That is patently false as has been explained *ad infinitum* on these boards.  For example, look at the Linux market share on servers and then tell me where all the malware and security issues are.

Are there security issues on Linux?  Yes.  Are they the same as on Windows?  No, not at all.  People who keep looking for Windows flaws (malware) on Linux miss the real threats that are specific to Linux and other *nixes.  Basically, if you don't run a server, you have very little to worry about where security is concerned.

---

### Post by spynappels on 2010-08-27
I reckon Community Spirit means telling people the facts and arming them with the knowledge they need to use the systems securely. That does not mean I tell them wrong information, or leave out info that is important and give them a false sense of security.

Have a nice day!

---

### Post by mailc on 2010-08-27
If I may go back to OP s original question...

1. It is not really necessary that you wipe it all

2. However if you prefer to do it, then start the computer with a live CD, open a terminal and type : 
sudo shred -fvz /dev/sdx  
[FONT=monospace]replacing the x with the drive letter (likely ' a ' ).

Depending on the size of the drive , be prepared to wait for a while.

You can then install Ubuntu from the same live CD - 

[/FONT]

---

### Post by I_Want_To_Learn on 2010-08-27
> **rookcifer said:**
> Shred can also be used to write random data, though I see little point in doing so in your case.

EDIT: Removed post since nobody wants to comment on it.

---

