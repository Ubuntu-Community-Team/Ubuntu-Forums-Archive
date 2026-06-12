---
title: "Raring Ringtail daily build - error generated when running Software Updater"
date: 2013-01-12
forum: Ubuntu Development Version
---

### Post by #1udancqSHv% on 2013-01-12
Hi there U+1ers!

I just installed Raring Ringtail daily build, which completed without any problems.

However, I ran Software Updater after first boot, and got an error message (content included below).

I also tried updating using 'sudo apt-get update && sudo apt-get upgrade', but didn't get the same error (or any error at all).

My question is; would there be any benefit to the testing team if I made a bug report for this? I'll see if I can replicate the error with Software Updater after rebooting before I take it any further...
 
Thanks in advance for any guidance on this (quite new to Ubuntu, even more so to bug testing!)
```
Package operation failed
The installation or removal of a software package failed.

Details:
nstallArchives() failed:  Extract templates from packages: 16%% Extract templates from packages: 33%% Extract templates from packages: 49%% Extract templates from packages: 66%% Extract templates from packages: 82%% Extract templates from packages: 99%% Extract templates from packages: 100%% 
Preconfiguring packages ... 
 Extract templates from packages: 16%% Extract templates from packages: 33%% Extract templates from packages: 49%% Extract templates from packages: 66%% Extract templates from packages: 82%% Extract templates from packages: 99%% Extract templates from packages: 100%% 
Preconfiguring packages ... 
 Extract templates from packages: 16%% Extract templates from packages: 33%% Extract templates from packages: 49%% Extract templates from packages: 66%% Extract templates from packages: 82%% Extract templates from packages: 99%% Extract templates from packages: 100%% 
Preconfiguring packages ... 
 Extract templates from packages: 16%% Extract templates from packages: 33%% Extract templates from packages: 49%% Extract templates from packages: 66%% Extract templates from packages: 82%% Extract templates from packages: 99%% Extract templates from packages: 100%% 
Preconfiguring packages ... 
(Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 156501 files and directories currently installed.) 
Preparing to replace tar 1.26-4ubuntu3 (using .../tar_1.26+dfsg-0.1ubuntu1_amd64.deb) ... 
Unpacking replacement tar ... 
Processing triggers for man-db ... 
Processing triggers for mime-support ... 
Setting up tar (1.26+dfsg-0.1ubuntu1) ... 
(Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 156501 files and directories currently installed.) 
Preparing to replace libitm1:amd64 4.7.2-17ubuntu2 (using .../libitm1_4.7.2-18ubuntu1_amd64.deb) ... 
Unpacking replacement libitm1:amd64 ... 
Preparing to replace libgomp1:amd64 4.7.2-17ubuntu2 (using .../libgomp1_4.7.2-18ubuntu1_amd64.deb) ... 
Unpacking replacement libgomp1:amd64 ... 
Preparing to replace gcc-4.7-base:amd64 4.7.2-17ubuntu2 (using .../gcc-4.7-base_4.7.2-18ubuntu1_amd64.deb) ... 
Unpacking replacement gcc-4.7-base:amd64 ... 
Setting up gcc-4.7-base:amd64 (4.7.2-18ubuntu1) ... 
(Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 156501 files and directories currently installed.) 
Preparing to replace libstdc++6:amd64 4.7.2-17ubuntu2 (using .../libstdc++6_4.7.2-18ubuntu1_amd64.deb) ... 
Unpacking replacement libstdc++6:amd64 ... 
Setting up libstdc++6:amd64 (4.7.2-18ubuntu1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
(Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 156501 files and directories currently installed.) 
Preparing to replace cpp-4.7 4.7.2-17ubuntu2 (using .../cpp-4.7_4.7.2-18ubuntu1_amd64.deb) ... 
Unpacking replacement cpp-4.7 ... 
Preparing to replace libquadmath0:amd64 4.7.2-17ubuntu2 (using .../libquadmath0_4.7.2-18ubuntu1_amd64.deb) ... 
Unpacking replacement libquadmath0:amd64 ... 
Preparing to replace libgcc-4.7-dev:amd64 4.7.2-17ubuntu2 (using .../libgcc-4.7-dev_4.7.2-18ubuntu1_amd64.deb) ... 
Unpacking replacement libgcc-4.7-dev:amd64 ... 
Preparing to replace gcc-4.7 4.7.2-17ubuntu2 (using .../gcc-4.7_4.7.2-18ubuntu1_amd64.deb) ... 
Unpacking replacement gcc-4.7 ... 
Preparing to replace libgcc1:amd64 1:4.7.2-17ubuntu2 (using .../libgcc1_1%%3a4.7.2-18ubuntu1_amd64.deb) ... 
Unpacking replacement libgcc1:amd64 ... 
Processing triggers for man-db ... 
Setting up libgcc1:amd64 (1:4.7.2-18ubuntu1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
dpkg: error: dpkg status database is locked by another process 
Setting up cpp-4.7 (4.7.2-18ubuntu1) ... 
Setting up libquadmath0:amd64 (4.7.2-18ubuntu1) ... 
Setting up libgomp1:amd64 (4.7.2-18ubuntu1) ... 
Setting up libitm1:amd64 (4.7.2-18ubuntu1) ... 
Setting up libgcc-4.7-dev:amd64 (4.7.2-18ubuntu1) ... 
Setting up gcc-4.7 (4.7.2-18ubuntu1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 

```

---

### Post by grahammechanical on 2013-01-13
See if it happens tomorrow. When running the development branch some of us find it better to do daily updates or even twice daily updates.

The problem could have been at the repository end of things. The repositories are being changed/modified/updated as well during the development cycle.

Sometimes we get invitation to do a Partial Upgrade. We always ignore it and you should also. There is a sticky about at the top of the section.

Some of us always use the terminal to update. Some use Synaptic Package Manager (not installed by default any more). Keep in mind that Update Manager is itself under going development.

Regards and welcome to testing.

---

### Post by kevpan815 on 2013-01-13
That's why I use Zsync to Update to each and every days newest Nightly Build and then don't even bother Installing Updates that come out in the middle of the day, and then Clean Install after using Zsync, just to let you know that it usually prevents me from getting an Unuseable System on a Development Branch of Ubuntu.

---

### Post by #1udancqSHv% on 2013-01-24
Hi grahammechanical and kevpan815 - thanks for your replies and apologies for not getting back to you until now (just arrived back from the hospital today following surgery, so my spelling and typing may be worse than usual too!!)

As I've been away from this installation for so long, I've decided to re-install with the latest build, and then attempt to replicate the issue. I'm still a bit woozy today, so that might be a job whilst I'm stuck in bed tomorrow.

I'll take all the advice on board - thanks, it's appreciated!

> **grahammechanical said:**
> Sometimes we get invitation to do a Partial Upgrade. We always ignore it and you should also. There is a sticky about at the top of the section.
I tried to apply the advice straight after I read the post a week ago (but didn't get chance to reply) - by that time any I update I tried wouldn't work **apart** from a Partial Upgrade. However, I didn't get chance to try replicating the error afterwards.

> **grahammechanical said:**
> Keep in mind that Update Manager is itself under going development.Yup, understood. My post wasn't a complaint or support request, I appreciate that the rules are different when testing. However, I wanted to test the Software Updater too. That's why I was wondering if there was any benefit to sending the error report in. I just wasn't sure if the error report was something useful, or just due to me doing something stoopid! I'm trying to balance enthusiasm to help against actually making a useful contribution, and it might take a little while to offer more of the latter!! ;) haha

> **grahammechanical said:**
> Regards and welcome to testing.Thank you, and I'm grateful for both of your advice! :)

---

### Post by grahammechanical on 2013-01-24
Hi and welcome back!

Three years ago I had open heart surgery. So, I know all to well that feeling of being ill, too ill to even think. I wish you better.

Have you seen this - relevent to Update Manager

[http://www.omgubuntu.co.uk/2013/01/update-updater-app-arrives-in-raring]("http://www.omgubuntu.co.uk/2013/01/update-updater-app-arrives-in-raring")

In the past I have had problems with updating due to something going wrong at the repository end of things. If you see the message that the update has failed due to a missing header, then this command will fix it.

```
sudo rm /var/lib/apt/lists/*
```

That removes/deletes all the scripts in the lists directory. Then replace them with new versions by running

```
sudo apt-get update
```

I have had to do that in a released version of Ubuntu as well as the development version. I just want to show that sometimes there is another reason for something happening.

You might want to make a collection of command codes. This page has some very useful sudo codes.

[https://wiki.ubuntu.com/U+1/tester-wiki]("https://wiki.ubuntu.com/U+1/tester-wiki")

Other then that, you will see some very experienced persons posting in this section and you will also see some, like me, who are learning on the job. We often have no idea of what is going wrong.

Regards

---

### Post by #1udancqSHv% on 2013-03-17
Hi grahammechanical, apologies again for the very late reply, and thanks for those tips - I'll try them out if I get any problems. Currently testing raring for Ubuntu Studio...  :)

---

