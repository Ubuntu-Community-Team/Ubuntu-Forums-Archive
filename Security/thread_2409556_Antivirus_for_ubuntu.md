---
title: "Antivirus for ubuntu"
date: 2019-01-03
forum: Security
---

### Post by kingpenguin on 2019-01-03
I work for a security company and stated to get more into linux. I have read an enormous amount of articles that state that linux does not need antivirus. I was wondering why this is. I know that linux has package managers so all software is tested before it is loaded to verify that it is safe. On the other hand linux has software just like any other operating system in the world and where there is software there is vulnerabilities. How is it that there is rootkits and malware for linux but antivirus is discouraged?

---

### Post by wildmanne39 on 2019-01-03
*Thread moved to **Security for a more appropriate fit**.*

---

### Post by lisati on 2019-01-04
My $0.02, for what it's worth: there is (or used to be) a perception that most of the malware one encounters in the wild is likely to be designed to run on a Windows system, and thus unlikely to do mischief on a linux-based system. 

This, however, doesn't do away with the need to exercise care and caution when downloading stuff, viewing websites, or opening email attachments.

---

### Post by TheFu on 2019-01-04
> **rawrmonster2 said:**
> I work for a security company and stated to get more into linux. I have read an enormous amount of articles that state that linux does not need antivirus. I was wondering why this is. I know that linux has package managers so all software is tested before it is loaded to verify that it is safe. On the other hand linux has software just like any other operating system in the world and where there is software there is vulnerabilities. How is it that there is rootkits and malware for linux but antivirus is discouraged?

Viruses are written for Windows, so AV on other platforms just looks for Windows virus signatures.  The most common way for Linux to be impacted by any virus is through WINE.

Part of this is because of the system architecture differences between Windows and almost every other OS.  From the ground up, since the beginning, Unix systems have been multiuser and file permissions are at the core of all Unix security.  If you login with a non-root account, the multi-user security is designed and tested so that non-root accounts cannot harm the running system.  The permissions have been around and understood so long and without any exceptions, that there just aren't ways around them through bugs.  That is where Windows fails, IMHO.  In Windows, it seems getting around file permissions happens constantly in an effort to make using the OS more convenient.  

When was the last time you had to help any end-user on Windows deal with permissions?
OTOH, on Unix OSes, end-users are always running into permission issues.

Also, people running Unix systems tend to have backups and more importantly, versioned backups.  Why run something constantly when it is unlikely to impact you and there is a versioned backup from 12 hrs ago which will fix the issue?  Versioned backups are my #1 security tool.  They solve all sorts of issues.  I can't imagine having less than 60 days of versioned backups for any system these days.  Some high-risk systems get 120-180 days of versioned backups here.  I feel these backups ("pulled", never "pushed") are sufficient to address viruses, rootkits, malware, cryptolocker stuff, pretty much anything.  Restoring the core functions for any system takes 30-45 minutes. Only huge data restores add to that time.  When your entire OS is 6G, not 60G, backups are much easier to restore.

IMHO.

Might want to read the "sticky threads" at the top of the Ubuntu  Security subforrum. There's one about antivirus there.

---

### Post by mcyber4 on 2019-01-04
Currently I'm trying Eset and it found a script injector in mozilla cache.
But more of a problem are rootkits.
I once thought Linux to be more secure than windows but not really anymore.

---

### Post by Autodave on 2019-01-04
Linux is light years ahead of Windows in security.  Things that affect Windows machines will not affect Linux.  I currently have 10 machines running Linux.  One is in a public place and gets many users. None have ever had a virus. None have ever had a program, document, or file changed, lost, or added.  All have total access to the internet through multiple browsers. Try doing that with a Windows machine and see what happens.

---

### Post by Frogs Hair on 2019-01-05
See the security link in my signature . If you share files with windows machines viruses could be a concern.

---

### Post by pending... on 2019-01-06
It is mainly discouraged for the average Linux user. I wouldn't say the same things if a company was running a lot of Linux boxes, because they'd have much more interactions with other computers which include Windows machines. If Linux is not compromised by a virus, it still can be an infection agent to other machines. And in businesses, it is just not worth taking these risks.

---

### Post by jdeca57 on 2019-01-06
The difference between Windows and Linux is most visible in security. Windows starts with a lot of open connections, Linux is rather closed. And also, a Windows user is the owner of the computer and - without effort - has root access. That last point is the main reason why Windows systems are so much more vulnerable. Using a browser as root?

---

### Post by yetimon_64 on 2019-01-08
My 2 cents, a couple of links worth reading OP (along with the link in Frogs Hair's sig) ...
[https://help.ubuntu.com/community/Antivirus]("https://help.ubuntu.com/community/Antivirus")
and
[https://help.ubuntu.com/community/Security]("https://help.ubuntu.com/community/Security")

> If you share files with windows machines viruses could be a concern.
^^^ This ^^^ ... would be about the only reason I'd consider using AV on ubuntu. I do have clamav installed in this trusty install I am posting from now for "on-demand" scanning when sharing files with windows users.

In 11 years of using ubuntu and various linux distros I've never encountered a virus that affected any of the installs. Have had a few rootkit warnings that ultimately turned out to be false positives in the chkrootkit program I use as well. I am not saying it is impossible to get a virus/malware in linux, put simply it IS possible, just much more difficult to catch one than in Windows. The above links and the link from Frogs Hair should give you a better idea why it is like this.

---

