---
title: "Hash sum mismatch after the update"
date: 2015-03-09
forum: Ubuntu Development Version
---

### Post by enricobe on 2015-03-09
Hello, 
I have this "Has sum mismatch" error since I have updated from 14.10 to 15.04.

I've tried to do an ```
apt-get clean
``` and also a ```
sudo rm -r /var/lib/apt/lists/* -vf
``` but doesn't work.

rm -r /var/lib/apt/lists/* -vf worked for some days but now i can't update my ubuntu repositories. 

How can i solve?

---

### Post by Cavsfan on 2015-03-09
> **enricobe said:**
> Hello, 
I have this "Has sum mismatch" error since I have updated from 14.10 to 15.04.

I've tried to do an ```
apt-get clean
``` and also a ```
sudo rm -r /var/lib/apt/lists/* -vf
``` but doesn't work.

rm -r /var/lib/apt/lists/* -vf worked for some days but now i can't update my ubuntu repositories. 

How can i solve?

I got that error a few times yesterday doing **sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoclean** in terminal.

It was on one of the repositories towards the last, I don't recall which one.

I think it may have been 4-5 times in a row and I was wondering.... Then it worked and I haven't had a problem since.

---

### Post by enricobe on 2015-03-10
> **Cavsfan said:**
> I got that error a few times yesterday doing **sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoclean** in terminal.

It was on one of the repositories towards the last, I don't recall which one.

I think it may have been 4-5 times in a row and I was wondering.... Then it worked and I haven't had a problem since.
I've tried with the commands above, but still doesn't work :(
```

W: Impossibile recuperare http://it.archive.ubuntu.com/ubuntu/dists/vivid/main/source/Sources  Somma hash non corrispondente

W: Impossibile recuperare http://it.archive.ubuntu.com/ubuntu/dists/vivid/universe/source/Sources  Somma hash non corrispondente

W: Impossibile recuperare http://it.archive.ubuntu.com/ubuntu/dists/vivid/main/i18n/Translation-en  Somma hash non corrispondente

W: Impossibile recuperare http://it.archive.ubuntu.com/ubuntu/dists/vivid/universe/i18n/Translation-en  Somma hash non corrispondente

E: Impossibile scaricare alcuni file di indice: saranno ignorati o verranno usati quelli vecchi.

```

I can't undersand if the problem is with the localization (it-IT) or something else...

---

### Post by sudodus on 2015-03-10
Maybe it works if you re-install from the current daily iso file. Try it [live]("http://ubuntuforums.org/showthread.php?t=2230389") before installing.

---

### Post by zika on 2015-03-10
Do not reinstall.
```
[FONT=Ubuntu Mono]sudo rm /var/lib/apt/lists/*
[/FONT]sudo apt-get update
```It happens when repositories are in the middle od their refreshement.

---

### Post by sudodus on 2015-03-10
> **zika said:**
> Do not reinstall.
```
[FONT=Ubuntu Mono]sudo rm /var/lib/apt/lists/*
[/FONT]sudo apt-get update
```It happens when repositories are in the middle od their refreshement.

Thanks for the tip :-)

---

### Post by enricobe on 2015-03-10
> **zika said:**
> Do not reinstall.
```
[FONT=Ubuntu Mono]sudo rm /var/lib/apt/lists/*
[/FONT]sudo apt-get update
```It happens when repositories are in the middle od their refreshement.

[FONT=Ubuntu Mono]sudo rm /var/lib/apt/lists/* [FONT=arial][FONT=lucida console]is a directory[/FONT].[/FONT][/FONT]

I've used [FONT=Ubuntu Mono]sudo rm -r /var/lib/apt/lists/*[/FONT]
Then sudo apt-get update 

But it still doesn't work :(
```

W: Impossibile recuperare http://it.archive.ubuntu.com/ubuntu/dists/vivid/main/binary-amd64/Packages  Somma hash non corrispondente

W: Impossibile recuperare http://it.archive.ubuntu.com/ubuntu/dists/vivid/universe/binary-amd64/Packages  Somma hash non corrispondente

E: Impossibile scaricare alcuni file di indice: saranno ignorati o verranno usati quelli vecchi.
```



> **sudodus said:**
> Maybe it works if you re-install from the current daily iso file. Try it [live]("http://ubuntuforums.org/showthread.php?t=2230389") before installing.
Do you mean a complete re-install of Ubuntu? Should I format the current partition and re-install the whole system?
Is this ([http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)) the right place where to download the lastest iso?

---

### Post by zika on 2015-03-10
Before reinstall do try another server (repositories), preferably Main...
Server that You're using (it) might have some issues.
Also check if there is some firewall or such that might introduce some network &#8222;noise&#8220;.
If You do decide to reinstall try Live before that to see if there is the same issue with it.

---

### Post by sudodus on 2015-03-10
[B]This forum is for the discussion of Vivid Vervet and Trusty Tahr point release testing only.

[/B]So I guess you are prepared for a rough ride, testing Vivid rather than running Vivid as your production platform :-P

Of course, you should save all important data (personal documents, pictures etc) before you re-install. And yes, I suggest that you format the current partition and re-install. During testing of versions not yet released, I think it is often better to get a fresh install (in the whole drive or as a dual boot system).

It is too bad that cleaning did not work for you. I'm sure it works in many cases, but this case might be 'too borked', maybe because you upgraded from 14.10 at the wrong time, when Vivid was not ready for it.

Edit: Try [live]("http://ubuntuforums.org/showthread.php?t=2230389") before installing.

---

### Post by enricobe on 2015-03-10
> **sudodus said:**
> [B]This forum is for the discussion of Vivid Vervet and Trusty Tahr point release testing only.

[/B]So I guess you are prepared for a rough ride, testing Vivid rather than running Vivid as your production platform :-P

Of course, you should save all important data (personal documents, pictures etc) before you re-install. And yes, I suggest that you format the current partition and re-install. During testing of versions not yet released, I think it is often better to get a fresh install (in the whole drive or as a dual boot system).

It is too bad that cleaning did not work for you. I'm sure it works in many cases, but this case might be 'too borked', maybe because you upgraded from 14.10 at the wrong time, when Vivid was not ready for it.

Edit: Try [live]("http://ubuntuforums.org/showthread.php?t=2230389") before installing.

What do you mean with "**This forum is for the discussion of Vivid Vervet and Trusty Tahr point release testing only."**? I'm using 15.04 and i do every day a update, upgrade, dist-upgrade. Is it the wrong procedure? I'm not using the testing version?

The "cleaning" worked for some days (4 or 5 days) but since 3 days i can't update the repositories

> **zika said:**
> Before reinstall do try another server (repositories), preferably Main...
Server that You're using (it) might have some issues.
Also check if there is some firewall or such that might introduce some network &#8222;noise&#8220;.
If You do decide to reinstall try Live before that to see if there is the same issue with it.
I'll try to change the server and i'll tell you if it works. I don't have network problem because it works fine on other PCs and always worked with 14.10 :)

---

### Post by sudodus on 2015-03-10
When you scroll to the very top of this page, you should see the blue text

[SIZE=3]**[COLOR=#0000cd]Hello enricobe, this forum is for the discussion of  Vivid Vervet and Trusty Tahr point release testing only. The Vivid  release schedule can be found[/COLOR] [ here]("https://wiki.ubuntu.com/VividVervet/ReleaseSchedule")**[/SIZE]

I'm sorry if you were not aware that Ubuntu Vivid will released as Ubuntu 15.04 in April, and that it is now in the beta development phase. It is good testing to install it and to test update/dist-upgrade daily, but it is still meant for testing, and you must expect that things can break a few times before the release.

You are very welcome to test Vivid (and future releases) and to discuss and get help here.

But if you want something more reliable, use a released version, 14.10 or even better, the long time support version 14.04 LTS, with the newest point release now 14.04.2 LTS. The LTS releases of Ubuntu and Kubuntu are supported for 5 years, while the LTS releases of Lubuntu and Xubuntu are supported for 3 years. I'm not sure about the other flavours. But other versions, like 14.10 and 15.04 are and will be supported only for 9 months.

---

### Post by sudodus on 2015-03-10
Maybe I should add, that if you have a lot of personal data and personal settings, you can wait for a few days. The problems with hash sum mismatch might get resolved, when the servers (for updating ubuntu) get new daily improved program packages and hash sum checklists.

---

### Post by enricobe on 2015-03-10
Thank you sudodus, but I know that it is a testing version. I've installed it for my everyday use and also for help in testing. 
I have no personal data in my ubuntu partition because I save all data in my Windows Partition and in the cloud, so I'm not scared about a weekly re-install but i'm only trying to understand how to solve the problem, if it can be solved :)

---

### Post by sudodus on 2015-03-10
This is great news :KS (I was worried, that you had real problems.)

I would recommend that you do not write files from Ubuntu to the Windows partition. Instead, if you dual boot with Windows, it is a good idea to have a separate ***data*** partition with the NTFS file system and the label **data**, where you save documents, pictures, music, video-clips etc. Please shut down Windows and Ubuntu completely (no hibernation), because of problems with common data with another operating system.

Advantages with a data partition:

- easy backup of data because no operating system files in it
- easy backup of operating systems, because those partitions can be kept rather small and clean
- no risk that writing to the data partition will damage 'the other' operating system
- easy to re-install operating systems without losing personal data (if you have also mailbox files and browser bookmarks linked into the data partition).

Warning:

- Shared files can be destroyed by hibernation, but the damage can be worse if you share the files in the Windows partition.

Your backup to the cloud helps you relax, when you are doing risky things with your operating systems :-)

---

### Post by dino99 on 2015-03-10
As post #5 said, it's not so scary , it's the xapian index that is not syncing/refreshing its index as it should do to deal with such racing time errors (it should detect them and then continue rebuilding the index ( it's a know issue reported a while back ( Bug #655831 but still not catch maintainer attention)

---

### Post by enricobe on 2015-03-10
Thank you for your warnings. I actually write from ubuntu to Windows and now i'll be more careful. I would like to create a data partition, but at the moment i can't do it. I have a OEM PC with a lot of vendor's partitons and I won't delete them until the warranty expires. I think I have about 8 partitions for only 2 installed O.S. :mad:
I never hybernate Win or Ubuntu ;)

I would like to use OneDrive on my Ubuntu, but I can't because there isn't a stable and working client :( This is a little Off Topic, now i'm going to try the ap-get update from the live cd. I only have to boot the live and do a "apt-get install"?


@9d9: I'm not so expert, what should i do? Just wait?


I've found this on launchpad [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1371058](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1371058) Is it my bug?

---

### Post by sudodus on 2015-03-10
Try
```
sudo apt-get update
```
in the live session. But if you have some special repositories or PPAs, those are not tested in the live session.

I have a list of 'cleaning and repairing commands', that was originally posted by *oldfred*, where I added the commands for your issue today

```
# Oldfred's command list for cleaning and repairing
 
#houseclean
sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get clean

#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
sudo apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
sudo dpkg --configure -a

# Remove lock
# If you are absolutely sure you do not have another upgrade process running.
# Locked dpkg - only if sure you are not running another update.

sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a 

# added zika's tip for problems with hash sum mismatch

sudo rm /var/lib/apt/lists/*
sudo apt-get update

```

---

### Post by sudodus on 2015-03-10
> **enricobe said:**
> ...
I've found this on launchpad [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1371058](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1371058) Is it my bug?

Yes I think so. Some bugs are hard to squash. They seem to have many lives :-)

---

### Post by enricobe on 2015-03-10
Thank you for your help, i've tried all the "repair" commands but they did not work. :(

Should i say that bug also affects me on launchpad?

---

### Post by sudodus on 2015-03-10
Yes

---

### Post by dino99 on 2015-03-10
@9d9: I'm not so expert, what should i do? Just wait?


if it happens to fail, then redo the update, that's all about that transitional issue (maybe your will get better luck if the 'main' server is used instead of the 'local' one)

---

### Post by enricobe on 2015-03-10
I've tried to launch apt-get update from the daily live DVD and it works fine.

I've changed the server to MAIN and removed the ppa i had (for installing wine) and it worked! :D I will test it in the next days, but at the moment it works.

---

### Post by sudodus on 2015-03-10
Good news :KS

So the problem could be either a server issue or a PPA issue. What happens if you change back either of them and run **sudo apt-get update** again?

---

### Post by zika on 2015-03-10
Just to illustrate that even Main is not flawless:```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/vivid-proposed/main/i18n/Translation-en  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/vivid-proposed/universe/i18n/Translation-en  Hash Sum mismatch


E: Some index files failed to download. They have been ignored, or old ones used instead.
```just a minute ago, several times, until it settled and now is everything OK again. Just usual in this time of development when there is a bit more of traffic in repositories getting them ready for April... ;)

---

### Post by enricobe on 2015-03-10
> **sudodus said:**
> Good news :KS

So the problem could be either a server issue or a PPA issue. What happens if you change back either of them and run **sudo apt-get update** again?

I have restored my previous settings (PPA enabled and Italian server) and now it works fine... :?

I don't know what to say

---

### Post by Elfy on 2015-03-10
> **enricobe said:**
> ...

I don't know what to say

I've marked the thread as Solved seems to be the best thing to say :)

Personally I leave server set to Main, but afaik Main and UK server are in the same place ...

---

### Post by Cavsfan on 2015-03-10
> **sudodus said:**
> ...

I would recommend that you do not write files from Ubuntu to the Windows  partition.

...

I could not agree more with sudodus. 

Never write to windows from linux! Read and copy from but never write to that partition!

Windows has a certain way it keeps track of it's files and if a file gets added or deleted while windows is not running you could easily break windows.

I did that years ago and my auto backup quit working. I had the best Micro$oft gurus trying to help me get it working but in the end they recommended a re-install.
Prior to that I had never in my life had to re-install windows.

I'll mount C: windows drive and copy a file from it to Ubuntu and then immediately click unmount C: because I don't want to take any chances.

Glad you got your updates working. :)

---

### Post by enricobe on 2015-03-10
Now it is solved. I hope it will remain "solved" also in the future :)

---

