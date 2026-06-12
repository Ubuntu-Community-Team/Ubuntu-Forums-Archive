---
title: "Detention and best practises - Advices"
date: 2024-03-27
forum: Security
---

### Post by netw844f on 2024-03-27
I already know the answer to this question is a resounding NO!

I've conducted thorough research, and most responses I've come across on this topic typically suggest:


[LIST=1]
[*]It's extraordinarily unlikely.
[*]Unless a file specifically asks for your password when opened, you should be fine.
[*]Linux systems are generally safe.
[*]As long as you avoid visiting dangerous websites, you should be fine.
[*]Installing antivirus software on Linux machines is often deemed a waste of time since granting root permissions to such software can create convenient entry points for attacks.
[/LIST]

I'm already aware of these points and take precautions by being  selective about the websites I visit, verifying links before clicking on  them, and confirming the legitimacy of files before opening them.
However, if I want to determine whether my system has been compromised, I currently use [https://www.clamav.net/](https://www.clamav.net/) Are there any other options available? (Since ClamAV only scans files)  What steps should I take to further enhance the security of my system?

For example, I've already divided my hard drive into two partitions -  one for / and another for /home. I'm considering setting all files  within /home to have file permissions of 600, allowing only the owner to  read and write the files. Is this considered a best practice?
Within /home, I have folders like "snap" and "VirtualBox". Would it be advisable to apply 770 permissions to these folders?

In addition to these practices, I'd like to implement a method for  detecting files that may be spying on me. I often collaborate on  open-source projects where I may receive files, such as C files, from  other team members (usually, the team is just me and one other person). Even if I review the code, I'm concerned that the  files (often consisting of multiple files) may still contain hidden  malicious code. Therefore, I want to ensure that my computer is not  currently infected.

Thank you in advance

---

### Post by &amp;KyT$0P# on 2024-03-27
ClamAV is not the way to check whether a Linux system is compromised, especially if ClamAV is installed on the system you're scanning.  That's a recipe for a false sense of security.

See [this post by DuckHook]("https://ubuntuforums.org/showthread.php?t=2184758&p=12833795&viewfull=1#post12833795"), and [this thread where I overestimated the importance of anti-malware scanning]("https://ubuntuforums.org/showthread.php?t=2332576").

> **netw844f said:**
> [LIST=1]
[*]It's extraordinarily unlikely.
[*]Unless a file specifically asks for your password when opened, you should be fine.
[*]Linux systems are generally safe.
[*]As long as you avoid visiting dangerous websites, you should be fine.
[*]Installing antivirus software on Linux machines is often deemed a waste of time since granting root permissions to such software can create convenient entry points for attacks.
[/LIST]


(2) is incorrect, and the other points are misleadingly incomplete.  Again, see the linked post by DuckHook.

> In addition to these practices, I'd like to implement a method for  detecting files that may be spying on me. I often collaborate on  open-source projects where I may receive files, such as C files, from  other team members (usually, the team is just me and one other person). Even if I review the code, I'm concerned that the  files (often consisting of multiple files) may still contain hidden  malicious code.

If you distrust these files to that extent, don't run them on your main system.  Only work with them in a secured, semi-disposable (i.e. snapshotted or backed up) VM.

---

### Post by currentshaft on 2024-05-07
n

---

### Post by TheFu on 2024-05-08
I cannot really tell what the question was,  *Detention and best practises - Advices *  doesn't really fit.   Perhaps **Detection** was the intended word?

What can be done to secure a system is almost endless.  What you CAN do and what you SHOULD do are other questions dependent on the threats.

Don't confuse management, flexibility, privacy and security.  These are 4 distinct things.

For most end-users on a desktop system, just review the Stick Threads in this sub-forum and follow those suggestions. That is more than sufficient.

Don't do stupid things.  Just like walking around a slum with a new gold watch at 2am is a bad idea, don't expect your desktop to be 100% secure when visiting the nastier parts of the internet.

Whole drive encryption is only useful when the drives are not unlocked.  That effectively happens only when the computer is completely shut down.  Not just in standby or hibernated.  Shutdown.  With a laptop, encryption and shutting down the system whenever changing buildings should be required.  Whether general storage in a tower-desktop needs to be encrypted or not is not so clear.  The main reason I encrypt desktop storage is for HDDs under warranty so returning a failing HDD through an RMA process doesn't give access to my data.

Daily, automatic, "pull"ed, versioned, backups are my main security.  I've only used AV scanners when contractually mandated.  They never found anything, but our E&O insurance mandated it for coverage, so I put AV on every system and maintained the signatures.  ClamAV is the "standard", but there are companies who will happily take your money if you prefer that.  AV is only catches about 50% for each tool used.  If you run 3+ of the AV tools, studies show about 90% of viruses will be caught.  That could be important if your Linux server shares files with MS-Windows.   Linux attacks tend to be different than MS-Windows attacks, so a different type of security is needed.

Tailor your security for the risks of the system. Mitigate what you can.  Keep backups where the client cannot gain access and for sufficient time that subtle modifications that aren't noticed for months wouldn't prevent restoration.  Every day, I look at the backups reports for how much data was changed.  When there are larger than normal amounts, that's when I need to figure out what happened to cause the changes. 

If you believe the system has been compromised.  Wipe it. Reload the OS from a known-good source. Start over from your last known good data and config backups.  For any system with less than 50G, this shouldn't take over 45 minutes.  For systems with more data, it is doubtful you need access to all that data at restore time.  Just the core restore will get it up and working again.  I don't bother backing up OS programs and haven't for nearly 15 yrs.  Backup data, configurations, and lists of installed packages.  Again the client system being backed up shouldn't have access to the backup storage, if that is possible.  That last thing we want is for a corrupted system to also be connected to backup storage with the ability to corrupt that as well.

---

### Post by netw844f on 2024-09-13
Thank you once again, TheFu, for another excellent answer. I really appreciate your time.

---

