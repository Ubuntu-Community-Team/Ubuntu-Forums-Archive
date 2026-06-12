---
title: "Missing 'command-not-found' database"
date: 2023-11-04
forum: Ubuntu Development Version
---

### Post by MAFoElffen on 2023-11-04
On the Noble Server I installed last night from the pending Daily iso image there last night... It has a weird bug. This is not on the upgraded releases, but on the newly installed from ISO.

Package 'command-not-found' is installed but it is not working. If I do a fictitious command, it throws this error:
```

fictitious --help
Could not find command-not-found database. Run 'sudo apt update' to populate it.
ficticious: command not found.

```
Running 'sudo apt update', does not populate the database. If I list /var/lib/command-not-found/, the folder is there, but it is an empty folder...

I know that the fix for that is just to try to reinstall it, and then to recheck that directory to see if it is populated...

I just want to check if anyone else got this on their iso installer install's, for me to report it as an installer bug or not, before I try to fix it... 

I just checked the pending updates for it, and none of those should resolve that error from those updates... (Unrelated packages)

So the new installer does an rsync copy of an image it extracts from the Snap into /tmp... Instead of where the older installers used to use dpkg to install the base. So that would mean that the folder contents is missing from that "image" it is rsync'ing from...

Could someone please check their install, if it happened on theirs?

---

### Post by #&amp;thj^% on 2023-11-04
No daily here just a "sed upgrade" and I'm not helpful on "snaps" none nada zip zilch.
but:
```
apt search fictitious
Sorting... Done
Full Text Search... Done
sugarplum/noble,noble 0.9.10-18.1 all
  automated and intelligent spam trap/cache-poisoner

swe-basic-data/noble,noble 4.0-20221111-2 all
  Swiss Ephemeris library (basic set of ephemeris files).

swetest/noble 2.10.03-3 amd64
  Swiss Ephemeris test application.


```
Nothing to see there
```
ls /var/lib/command-not-found
commands.db  commands.db.metadata

```
Mine is installed:
```
apt policy command-not-found
command-not-found:
  Installed: 23.04.0
  Candidate: 23.04.0
  Version table:
 *** 23.04.0 500
        500 http://archive.ubuntu.com/ubuntu noble/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu noble/main i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by MAFoElffen on 2023-11-04
LMAO!!! I thought the command "fictitious" was actually something that did not exist... 

But still... I'll just report it. Just a pain to file bugs from server, where I have to generate the report as not-sent / create apport file, then transfer that to another machine with a browser to create a new blank bug, then upload the other machine's apport files.

RE: [https://bugs.launchpad.net/command-not-found/+bug/2042746](https://bugs.launchpad.net/command-not-found/+bug/2042746)

And reinstalling package 'command-not-found' does not fix it. That package being broken, seems to be the root problem there. I can probable copy it over from something else (so that it does exist initially), but lets let the system work. LOL

---

### Post by Doug S on 2023-11-05
> **MAFoElffen said:**
> Just a pain to file bugs from server, where I have to generate the report as not-sent / create apport file, then transfer that to another machine with a browser to create a new blank bug, then upload the other machine's apport files. I have just always said "It doesn't work for me" and set the bug report back from "incomplete" to "new".

> **MAFoElffen said:**
> RE: [https://bugs.launchpad.net/command-not-found/+bug/2042746](https://bugs.launchpad.net/command-not-found/+bug/2042746)
And reinstalling package 'command-not-found' does not fix it. That package being broken, seems to be the root problem there. I can probable copy it over from something else (so that it does exist initially), but lets let the system work. LOL I get the same as you and will chime in on the bug report.

EDIT: From bug report:

> Noble 24.04 Server edition daily dated 2023.11.03...
Mine was from the 2023.11.02 Server ISO, but updated via "sudo apt update" and "sudo apt upgrade" to today.
I set the bug report to "confirmed".

---

### Post by MAFoElffen on 2023-11-05
> **Doug S said:**
> I have just always said "It doesn't work for me" and set the bug report back from "incomplete" to "new".

 I get the same as you and will chime in on the bug report.

I set the bug report to "confirmed".
LOL. For server, I have to save them... Then 'scp' them to my workstation, to report server bugs from there.

Thank you Doug! I saw that in-between reeling in some Salmon on the river. I had to go unwind...

---

### Post by Irihapeti on 2023-11-06
I was noticing the same thing, too. But I thought it was to do with the strange things I do with my installs, so didn't pay too much attention to it. I'll add myself to it as "affects me too".

---

### Post by corradoventu on 2023-11-06
My BUG: [https://bugs.launchpad.net/ubuntu/+source/command-not-found/+bug/2042691](https://bugs.launchpad.net/ubuntu/+source/command-not-found/+bug/2042691)

[https://packages.ubuntu.com/search?keywords=command-not-found](https://packages.ubuntu.com/search?keywords=command-not-found)

---

### Post by Doug S on 2023-11-06
> **corradoventu said:**
> My BUG: [https://bugs.launchpad.net/ubuntu/+source/command-not-found/+bug/2042691](https://bugs.launchpad.net/ubuntu/+source/command-not-found/+bug/2042691)

Thanks. So, one of the 2 bug reports should be set as a duplicate of the other. Even though yours was entered first, I suggest that it be set as the duplicate.

---

### Post by #&amp;thj^% on 2023-11-06
Everyone else gets to have fun but me :(
ex:
```
nvme
Command 'nvme' not found, but can be installed with:
sudo apt install nvme-cli

```
```
apt policy  nvme-cli
nvme-cli:
  Installed: 2.6-1
  Candidate: 2.6-1
  Version table:
 *** 2.6-1 500
        500 http://archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Irihapeti on 2023-11-07
I was playing with a couple of Noble installs last night and didn't see it. Maybe it's been fixed.

---

### Post by ajgreeny on 2023-11-12
I had this problem yesterday on a Xubuntu Installation from the iso downloaded yesterday.

I removed all snaps and snapd as I always do then downloaded the tar.gz version of firefox which is my chosen method of running firefox. I use a symbolic link from the executable firefox file in the archive then use that link as the executable in a launcher.
Using that launcher is when I see the "command-not-found" error. 

I have used this method of running firefox very successfully since the snap version became the default and it has worked perfectly until now.

Interestingly if I create the symbolic link using the **firefox-bin **file instead of the **firefox** executable file it all works as expected.

---

### Post by ajgreeny on 2023-11-12
> **morrisrose said:**
> Maybe the problem is in the Firefox browser itself?

Not very likely as the firefox archive was copied across from another VM in KVM/QEMU where it is all working as expected.

---

### Post by corradoventu on 2023-11-12
Still having the problem on my Noble installed from ISO Ubuntu 24.04 "Noble Numbat" - Daily amd64 (20231102)

> corrado@corrado-n4-nn-1102:~$ entangle
Could not find command-not-found database. Run 'sudo apt update' to populate it.
entangle: command not found
corrado@corrado-n4-nn-1102:~$ apt list command-not-found
Listing... Done
command-not-found/noble,noble,now 23.04.0 all [installed,automatic]
corrado@corrado-n4-nn-1102:~$ apt list entangle
Listing... Done
entangle/noble 3.0-4 amd64
corrado@corrado-n4-nn-1102:~$

---

### Post by ajgreeny on 2023-11-13
On the Xubuntu install where I saw the problem I spoke of in post #11 I reinstalled the **command-not-found** and also **python3-commandnotfound** packages and the problem appears to have been solved.

---

### Post by corradoventu on 2023-11-13
corrado@corrado-n4-nn-1102:~$ sudo apt --reinstall install command-not-found  python3-commandnotfound
... does NOT solve the problem
corrado@corrado-n4-nn-1102:~$ entangle
Could not find command-not-found database. Run 'sudo apt update' to populate it.
entangle: command not found
corrado@corrado-n4-nn-1102:~$

---

### Post by corradoventu on 2024-02-09
Fixed also for me.

---

### Post by MAFoElffen on 2024-02-11
Well, curious.

So you both said in the install, it is still broken... But if you update and reinstall it, it is then fixed, (only) by that added work-around process...

So rather, it sounds like it is getting closer to being fixed.

---

### Post by corradoventu on 2024-02-11
On my Noble just installed from ISO dated feb-11 problem is disappeared.
```
corrado@corrado-n7-nn-0211:~$ entangle
Command 'entangle' not found, but can be installed with:
sudo apt install entangle
corrado@corrado-n7-nn-0211:~$ ls /var/lib/command-not-found -l
total 3592
-rw-r--r-- 1 root root 3670016 Feb 11 09:05 commands.db
-rw-r--r-- 1 root root    3214 Feb 11 09:05 commands.db.metadata
corrado@corrado-n7-nn-0211:~$ 
```
see my comment on [https://bugs.launchpad.net/command-not-found/+bug/2042746](https://bugs.launchpad.net/command-not-found/+bug/2042746)

---

### Post by MAFoElffen on 2024-02-17
@corradovento --

I saw that there was a release committed. Sorry that I had to play Devils Advocate to see if it also resolved the Ubuntu 'command-not-found' vulnerability in a logic flaw in the code that was discovered a couple days ago, that is an exploit to introduce malware... 

RE: 
[https://www.aquasec.com/blog/snap-trap-the-hidden-dangers-within-ubuntus-package-suggestion-system/](https://www.aquasec.com/blog/snap-trap-the-hidden-dangers-within-ubuntus-package-suggestion-system/)
[https://www.bleepingcomputer.com/news/security/ubuntu-command-not-found-tool-can-be-abused-to-spread-malware/](https://www.bleepingcomputer.com/news/security/ubuntu-command-not-found-tool-can-be-abused-to-spread-malware/)
[https://thehackernews.com/2024/02/ubuntu-command-not-found-tool-could.html](https://thehackernews.com/2024/02/ubuntu-command-not-found-tool-could.html)
[https://www.omgubuntu.co.uk/2024/02/security-researchers-detail-ubuntu-security-flaw](https://www.omgubuntu.co.uk/2024/02/security-researchers-detail-ubuntu-security-flaw)
[https://securityaffairs.com/159129/security/ubuntu-command-not-found-attack.html](https://securityaffairs.com/159129/security/ubuntu-command-not-found-attack.html)
[https://www.linkedin.com/posts/netmanageit_ubuntu-command-not-found-tool-can-be-abused-activity-7163563322993266688-LoOP/](https://www.linkedin.com/posts/netmanageit_ubuntu-command-not-found-tool-can-be-abused-activity-7163563322993266688-LoOP/)
...and many more, all in the past few days.

---

### Post by corradoventu on 2024-02-18
So until the Ubuntu 'command-not-found' vulnerability is not resolved the solution is simple: AVOID SNAPS!!!

---

### Post by MAFoElffen on 2024-02-18
> **corradoventu said:**
> So until the Ubuntu 'command-not-found' vulnerability is not resolved the solution is simple: AVOID SNAPS!!!

LMAO!!! I tend to avoid them anyways. LOL

---

