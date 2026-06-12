---
title: "[SOLVED] Found virus"
date: 2008-09-15
forum: Security
---

### Post by mailtwogopal on 2008-09-15
Hi,

  Today i ran clamav in my ubunty hardy box and the status below shows "viruses found : 1" but the point is i cannot locate the file and even i dont know which file contains viruses. the clamtk virus scanner lists some of my mp3 files and two or more files which are listed as not scanned. I am worried and don't know what to do with it? please help regarding same.

---

### Post by jerome1232 on 2008-09-15
I rarely use clam and I've never used it's gui but if you run clamscan from a command line you can get the full path to your infected file. You should probably delete the file especially if it's in a directory that's shared with windows computers.

```
clamscan -ir ~/
```

---

### Post by rogeriopvl on 2008-09-15
If you are running Ubuntu, you have no reason to worry. Those virus were probably found in the windows partition or in some shared folders. Just delete/repair those files.

---

### Post by Dr Small on 2008-09-15
If there truly is a virus, then it will not infect your system. Live in bliss. But if you share files to Windows shares, or pass it along in an email to other Windows users, then they will get the virus.

---

### Post by tarun.winlin on 2008-09-15
> **Dr Small said:**
> If there truly is a virus, then it will not infect your system. Live in bliss. But if you share files to Windows shares, or pass it along in an email to other Windows users, then they will get the virus.

Why do you say that, if a virus was found in a file in linux partition, why would it not be able to infect linux, just because there are no known linux viruses ?

Sorry for being ignorant !!

---

### Post by jerome1232 on 2008-09-15
The same reason why Linux cannot run Windows programs, or a Mac binary, or a BSD binary, or a program complied for any other Operating system. That Virus is designed to exploit weakness in Windows Programs and/or the Windows Operating System. It will have no effect in a foreign environment.

---

### Post by Dr Small on 2008-09-15
> **tarun.winlin said:**
> Why do you say that, if a virus was found in a file in linux partition, why would it not be able to infect linux, just because there are no known linux viruses ?

Sorry for being ignorant !!
Because the virus would need to be specifically written for Linux, and you must install it for it to execute as a virus. If ClamAV found a virus, you can guarantee that it's one for Windows, so it won't affect your system.

---

### Post by cariboo on 2008-09-15
Even if you were lucky enough to catch a linux virus in the wild, it still couldn't do anything until you run it as root.

Jim

---

### Post by mailtwogopal on 2008-09-16
Hi guys,

  I run clam in terminal and i delete the file. But why some of the files are not scanned and is there any mystery behind it? also i use only ubuntu in my box and not windows at all.

---

### Post by mailtwogopal on 2008-09-16
Hi all,

  I scanned thru terminal window using "clamscan -ir ~/" and here is the result. 

```

gopal@gopal-desktop:~$ clamscan -ir ~/

----------- SCAN SUMMARY -----------
Known viruses: 425156
Engine version: 0.92.1
Scanned directories: 748
Scanned files: 7162
Infected files: 0
Data scanned: 2096.11 MB
Time: 768.258 sec (12 m 48 s)
gopal@gopal-desktop:~$ 

```

I am scared to see this. The first line represents "Known viruses: 425156" but when i scanned yesterday using clamtk (GUI) it indicated me only one virus. Is my computer contains this much number of viruses. I am much worried. Can anyone help me in this? I think even i can throw my computer outside or i can sell it to any lowest price demand by market if any. Please help me. I am much much worried.

Or am wrong with anything?

---

### Post by jerome1232 on 2008-09-16
That says Known Viruses, that means it knows of that many viruses not that you have that many infected files, it says it found none in your ~/ or your home directory.

Linux is not subject to Windows viruses, even if your scan found 40k viruses and they are all windows viruses, it doesn't matter. You could even arrange them as pretty little icons on your desktop and grin every time they do absolutely nothing just sitting there.

---

### Post by mailtwogopal on 2008-09-16
Hi jerome,

  Thanks for your reply. Am i getting it clear that clamscanner is able to find a virus if any by comparing the files in computer with 42K. am i right?

i.e clam scanner knows this much viruses in his database to identify a virus.... i hope so. please clarify me.

---

### Post by jerome1232 on 2008-09-16
Yes If you take a second look at the output it says infected files: 0; known viruses is just the amount of viruses clam knows how to scan for.

Unless you plan on sharing files with a windows computer there is no real need for scanning though :)

---

### Post by mailtwogopal on 2008-09-16
Hi jerome,

 Thanks once again for clarifying me. Also i thank all who replied to this post. I am clarified now and i wont fear hereafter ;)

---

### Post by mailtwogopal on 2008-09-16
Hi jerome,

 Thanks once again for clarifying me. Also i thank all who replied to this post. I am clarified now and i wont fear hereafter ;)

---

### Post by cariboo on 2008-09-16
I think with all the replies, nobody mentioned that clamav only scans for windows viruses.

> Known viruses: 425156 

That is the number of known windows viruses. If you look here:

[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

You'll see the number of Linux malware, is just a drop in a bucket compared to the number of know windows viruses.

Jim

---

### Post by Locutus_of_Borg on 2008-09-16
> **mailtwogopal said:**
> Hi all,

  I scanned thru terminal window using "clamscan -ir ~/" and here is the result. 

```

gopal@gopal-desktop:~$ clamscan -ir ~/

----------- SCAN SUMMARY -----------
Known viruses: 425156
Engine version: 0.92.1
Scanned directories: 748
Scanned files: 7162
Infected files: 0
Data scanned: 2096.11 MB
Time: 768.258 sec (12 m 48 s)
gopal@gopal-desktop:~$ 

```

I am scared to see this. The first line represents "Known viruses: 425156" but when i scanned yesterday using clamtk (GUI) it indicated me only one virus. Is my computer contains this much number of viruses. I am much worried. Can anyone help me in this? I think even i can throw my computer outside or i can sell it to any lowest price demand by market if any. Please help me. I am much much worried.

Or am wrong with anything?
Infected Files: 0



indicates of the 425156 known viruses, 0 of them are on your computer


generlly 'viruses' are not worried about in linux

there are malicious applications, but they do not infect your system in the way a traditional virus would on Windows

---

### Post by jerome1232 on 2008-09-16
I thought I covered the "don't worry about viruses" thing but no matter how many times you say it or point differences out, old habits die hard I think.

---

### Post by mailtwogopal on 2008-09-17
Hi guys,

  Tell me onething is that am completely a linux user (ubuntu). For documents am using openoffice which comes as a part of OS ubuntu. In order to take print out of documents say resume or some files i am saving word processor document as .doc format so that while taking printing outside it opens. I am using pen drives to transfer. Moreover i scan my USB drive whenever am using. Is that saving in .doc or in .xls can create anything harmful. I am asking this out of ignorance.

---

