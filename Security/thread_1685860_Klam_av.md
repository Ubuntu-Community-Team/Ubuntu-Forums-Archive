---
title: "Klam av?"
date: 2011-02-11
forum: Security
---

### Post by PhilRogers34 on 2011-02-11
ok i just scanned my system with klam av.  i'm getting little boxes pop up telling me that some files cannot be scanned, the message reads something like "cant scan file /location/filename/blah/blah/ - access denied"     is this normal? or should klam scan every single file? i have a batch from different locations it couldn't scan,    when i used symantec endpoint i could scan my entire windows install in about 12 mins, roughly 80.000 files,  with klam it has taken over an hour to scan over 155.000 files,  this is wrong surely? why does ubuntu have so many files?  i not going to sit through this everytime i want to make sure my system is safe.  is this too many files , i only installed it about 3 days ago!!!!          also i noticed a mistake with klam av, whilst scanning there is text in the bottom right corner that reads   0 viruseses/problems found.   someone spelt viruses wrong, they put an extra 'es' on the end, if someone could tell the klam developers and hopefully they can rectify this in an update or the next version.  cheers!

---

### Post by Grenage on 2011-02-11
You're obviously scanning the whole system, and as a regular user?  A regular user won't have access to a lot of system files.

Out of curiosity, why are you scanning at all?  Is it for the benefit of Windows machines somewhere?

---

### Post by ajgreeny on 2011-02-11
I wouldn't bother to run, and don't even have a virus checker on my computer any more.

I assume you are a new user of linux and Ubuntu and have not realised that viruses are largely a thing of the past, belonging to your windows(?) days.  If you are running a server for email, perhaps it is worth running clamav, which can look at emails and attachments as they arrive, but for a general desktop installation, virus checking is a waste of time.

---

### Post by PhilRogers34 on 2011-02-11
yes i am scanning the entire system, i'm using the account i set up on install which is labelled as an administrator. this has nothing to do with any windows machine. i just wanted to make sure klam was working properly.  i scanned my system because i wanted to be sure there were no viruses or spyware on it, i'm having a few issues with streaming videos and wanted to eliminate the possibility of an infected system.   i realise ubuntu is fairly safe but it is not 100% safe.If viruses were a thing of the past then there would be no need to even create an antivirus.  the only reason linux is safer is because not as many people use it as they do windows and consequently there are not as many people writing viruses for it.  i do not believe for 1 second that viruses are a thing of the past, people will break linux eventually, no matter what you believe, there will always be some geeky teenager somewhere with a higher iq than the rest of the planet who will suss out how to do it.

---

### Post by Joe of loath on 2011-02-11
I don't think you understand fully.

ClamAV is a virus scanner for Windows viruses. Ubuntu *can't* catch Windows viruses. If you want to make sure your system is safe, you're going the wrong way about it.

---

### Post by Grenage on 2011-02-11
You'd want to use sudo with KlamAV; but make sure you don't tell it to automatically remove bad files.  A false positive could result in a ruined machine.

When it comes to viruses, Linux has nothing to worry about.  That might change in the future, but I wouldn't waste your time now.  The definitions it's using are mostly for Windows machines, the main reason for using it is scanning USB drives before giving them to other Windows users.

---

### Post by PhilRogers34 on 2011-02-11
ok, edit my last edit, i didn't realise klam was for windows viruses, i assumed it was for linux, so what scans for linux viruses then?

---

### Post by coffeecat on 2011-02-11
> **PhilRogers34 said:**
> what scans for linux viruses then?

What Linux viruses? :) There are none in the wild at the moment. You are much more likely to be a victim of phishing or other OS-independent scams.

---

### Post by Grenage on 2011-02-11
> **PhilRogers34 said:**
> ok, edit my last edit, i didn't realise klam was for windows viruses, i assumed it was for linux, so what scans for linux viruses then?

There aren't any Linux viruses in circulation.

---

### Post by PhilRogers34 on 2011-02-11
ok, don't take this the wrong way but just because you 2 people haven't come across them doesn't mean they don't exist. i even read an article on reverse engineering trojans into linux so i know it can be done.

---

### Post by beew on 2011-02-11
You probably don't need an AV, but if you must have one get a real one like bitdefender. Clam AV is a joke and the only thing it does well even according to its advocates is scanning email. It is  slow, resource hogging and detection rate is very low.

I figure the reasons why it is always recommended are

1) virus is not a real problem in Linux so even a do-nothing placebo is good enough. The people who recommend it probably never use it themselves because they don't really need an AV, or only use it for things like scanning email.

2) It is open source. The fact that it sucks in actual performance is overlooked because of 1)

[ http://en.wikipedia.org/wiki/Clam_AntiVirus]("http://en.wikipedia.org/wiki/Clam_AntiVirus")

---

### Post by uRock on 2011-02-11
> **Grenage said:**
> There aren't any Linux viruses in circulation.
+1 While it is possible for someone to design one, it will most likely be discovered and patched before an infection can be carried out.

Like beew says, ClamAV is no good because it has a high false positive rate.

Moving to Security Discussions.

---

### Post by spook1980 on 2011-02-11
i've been using ubuntu since 7.04 and have never needed to run antivirus in ubuntu it's just not a problem on linux systems

---

### Post by coffeecat on 2011-02-11
@PhilRogers34, you might find this sticky useful:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

While you are still used to the leaky boat that is the Windows world, it is difficult to be confident of the more secure  world of Linux. Nevertheless, it is sensible to be able to understand the relative risks and you are right to be sceptical

---

### Post by cariboo on 2011-02-11
> **PhilRogers34 said:**
> ok, don't take this the wrong way but just because you 2 people haven't come across them doesn't mean they don't exist. i even read an article on reverse engineering trojans into linux so i know it can be done.

I've been using Linux since 1998, I've never run across a Linux virus in the wild either. 

All malware needs user interaction of some sort, there are many theories out there on how to do it, but no one has come up with anything that works yet.

If you are sharing files via Samba or NFS, I would suggest you use a malware scanner, especially if you have users that are click happy, and click almost every link they see.

Clamav does scan for Linux viruses too. Have a look [here]("http://blog.clamav.net/2009/02/clamav-active-malware-report.html")

---

### Post by hakermania on 2011-02-11
Ok, this is my opinion:
99,9% of Ubuntu Users have tried Windows before and know how to use them well. They also know how to avoid viruses, how to scan their system, how to set up a firewall etc. So, when somebody comes into ubuntu he is more or less "experienced" on the threats of viruses/hacker attacks etc. What I want to pass, is that, crackers want "easy preys" (read "Windows Users").

On the other hand, it isn't impossible to make a Linux Virus. Myself (without spreading them of-course), have made a program in C++ that can take firefox's passwds (that have user privileges) and sends them via email to me, and another one which copies itself everywhere it can (into USBs through /media/ or into remote connections through ~/.gvfs). All these can be done easily for someone with a few knowledge of programming. If anyone using Ubuntu has the experience to recognise what he should run, and not to execute things blindly, he is safe.
But, e.g. a firefox's Mater Password is essential for strong security. i would recommend a firewall as well(firestarter is pretty good)!
80%

---

### Post by uRock on 2011-02-11
Firestarter is no longer supported and not needed if one is using a modern router.

---

### Post by Joe of loath on 2011-02-11
the ubuntu firewall runs by default, you don't need a program to manage it. if you really want to fiddle with it, i hear ufw is good.

---

### Post by CharlesA on 2011-02-11
> **Joe of loath said:**
> the ubuntu firewall runs by default, you don't need a program to manage it. if you really want to fiddle with it, i hear ufw is good.

It is running, but it's not enabled by default. You can use ufw or gufw to manage it.

---

### Post by PhilRogers34 on 2011-02-12
Thanks for all the replies, i've read the sticky too, i'm kinda getting the picture.  i've added bitdefender and i have firestarter, i've also set up a new user profile and swapped all administration rights over to that one, i would have used it as a desktop user but it didn't carry all my music over and would have meant having to import music yet again so i made that account the admin one instead.  just to confirm though, when people mention being logged on as 'root' they mean administrator don't they? or are root and administrator 2 different things?

---

### Post by CharlesA on 2011-02-12
If you are an "administrator" you are the same as a normal desktop user, except you can use sudo and do admin tasks such as install updates/programs.

Root is root, they are different.

---

### Post by PhilRogers34 on 2011-02-12
ok, so what is the root account? is it the one that gets set up on install or is it one i have to create?

---

### Post by uRock on 2011-02-12
> **PhilRogers34 said:**
> ok, so what is the root account? is it the one that gets set up on install or is it one i have to create?
We do not recommend creating the root account as it is not needed. You can become root using the terminal to get things done by using the **sudo** command.

---

### Post by cariboo on 2011-02-12
You don't have to do anything, the root acount is there but disabled, to get to a root prompt, just type:

```
sudo -i
```

For more info, have a look at the [RootSudo Howto]("https://help.ubuntu.com/community/RootSudo")

Please heed the warnings, if you decide to make any changes.

---

### Post by vortmax on 2011-02-12
> **PhilRogers34 said:**
> the only reason linux is safer is because not as many people use it as they do windows and consequently there are not as many people writing viruses for it.

This is not true at all.  Linux is safer because it uses a safer security model than windows.  When you run a program as a user, (by default) that program doesn't run with root permissions...that means it doesn't have access to alter system files. When you download a file, it is not granted execute permissions by default either.  With the addition of apparmor, which even further restricts the access applications have to the file system, it becomes even safer.  Most of the exploits in found in windows that lead to the big malware infections are holes that allow the browser direct access to the system for the sake of "enhanced user experience".

---

### Post by PhilRogers34 on 2011-02-13
Thanks, it's highly unlikey i will ever need to use the root account, i just wanted to make sure that 'administrator' and 'root' are different. i'm not intending to activate the root account, just trying to get a picture in my mind of what's what.

---

### Post by CharlesA on 2011-02-13
Glad you got it sorted. :)

Don't forget the mark the thread as solved from thread tools.

---

### Post by PhilRogers34 on 2011-02-13
Yeah pretty much sorted, i'm gonna have a play with apparmor as well just make sure everything is as locked down as it can be. thanks for all the replies.

---

