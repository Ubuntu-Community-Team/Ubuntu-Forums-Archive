---
title: "Recovery from possible rootkit"
date: 2010-09-18
forum: Security
---

### Post by andreseso on 2010-09-18
Hello,

Some weeks ago I noticed my .bash_history was unchanged from August 16th.  I tried everything I could think of to make it writable without success. Googling I came upon this IRC server called unreal whose official repos had been hacked with a rootkit that could execute commands as my user.  Just for fun I executed sudo aptitude remove unreal and four packages were uninstalled. Just for fun I executed sudo aptitude install reality.  Three of the four packages were to be installed from an unauthenticated repository. I said no thanks.  One of the packages had a name that started with thunderbird.

When some contacts did not sync to my android phone, I took the following steps.

[LIST=1]
[*]I installed Maverick
[*]I created a new user
[*]I changed my gmail password
[*]I installed Xmarks on all my browsers
[*]I reset my android phone to factory settings.
[/LIST]
In the old account I have six years worth of email in my Thunderbird profile and a couple of years of stored passwords and bookmarks in my firefox profile in the old account.  How do I copy this information and only this information to my new account? I have bookmarks in my new firefox profile.

I am under the impression that if I execute any program of my old account I will be rooted. 

Love,
Andres

---

### Post by Rubi1200 on 2010-09-18
What does the output from 
```
ls -l ~/.bash_history
``` return?

The result should look something like this:
```
rw------- 1 your_name your_name   7364 2004-03-27 08:57 /your_name/.bash_history
```

---

### Post by OpSecShellshock on 2010-09-18
I don't think the ~/.bash_history file updates unless you run a command in the terminal, rather than doing an operation graphically. It's entirely possible to go for a month without using it for many users. In fact, if you open a terminal, run the command posted by Rubi1200 above, check the output, and then read the .bash_history file again, you should see that command at the bottom and the date on the file should have changed.

---

### Post by lovinglinux on 2010-09-18
> **andreseso said:**
> In the old account I have six years worth of email in my Thunderbird profile and a couple of years of stored passwords and bookmarks in my firefox profile in the old account.  How do I copy this information and only this information to my new account? I have bookmarks in my new firefox profile.

For Firefox bookmarks, copy ~/.mozilla/firefox/<profilename>/places.sqlite into the new account. For the passwords, copy signons.sqlite and key3.db.

---

### Post by cariboo on 2010-09-18
I have been using Thunderbird since it was in beta, my email storage goes back to 2001. I've just been moving the ~/.thunderbird/xxxxxxxx.default directory from install to install. If are using the latest version of Thunderbird for your Ubuntu version you should have nothing to worry about. 

I know I have a couple of Windows viruses somewhere in my email store, one of these days I may even get around to removing them.

---

### Post by andreseso on 2010-09-20
> **cariboo907 said:**
> I have been using Thunderbird since it was in beta, my email storage goes back to 2001. I've just been moving the ~/.thunderbird/xxxxxxxx.default directory from install to install. If are using the latest version of Thunderbird for your Ubuntu version you should have nothing to worry about. 

I know I have a couple of Windows viruses somewhere in my email store, one of these days I may even get around to removing them.

Yes, but the problem is that I am paranoid enough to believe that  if I copy my Thunder Bird profile as is and execute it, I will be rooted.  I need to clean everything that is not necessary from it.

```
/home/andres/ThunderBird# du -h --max-depth=1
8.0M    ./.svn
12G    ./Mail
28M    ./News
360K    ./Cache
7.3M    ./ImapMail
0    ./minidumps
596K    ./chrome
1.7M    ./extensions
12G    .

```

I am guessing ./Mail and ./ImapMail as well as prefs.js but I am not sure any other directories or files are necesarry.

Thanks for the help with my Firefox

Love,
Andres

---

### Post by BkkBonanza on 2010-09-20
.bash_history only updates at the end of a console session. During the session it remains static as when started. The **history** command shows you what has been done in the current session. .bash_history, as it's name implies, is only to do with the bash shell so it does not record activity of other programs in the computer.

All your mail is stored in directories under ./Mail and ./IMapMail. Judging by size you use POP3 for your mail much more than IMap. Each subdirectory is a mail account. As far as I know those folders contain mail content and not executable files at all. Probably anything other than .js files under thunderbird is pretty safe to copy over.

---

### Post by unspawn on 2010-09-20
> **andreseso said:**
> Googling I came upon this IRC server called unreal whose official repos had been hacked with a rootkit that could execute commands as my user.
Unreal ircd (3.2.8.1) was subverted in November 2009. It was trojaned, *not rootkitted*, to run commands *as the user it runs as*. For details see the advisory (issued June 2010) here: [http://www.unrealircd.com/txt/unrealsecadvisory.20100612.txt](http://www.unrealircd.com/txt/unrealsecadvisory.20100612.txt).


> **andreseso said:**
> Just for fun I executed sudo aptitude remove unreal and four packages were uninstalled. Just for fun I executed sudo aptitude install reality.
Since none of the previous replies emphasizes this aspect, for future reference, when you suspect something is awry please try to *make certain* that your systems integrity is maintained (or not) instead of un-installing and installing software haphazardly. Doing this destroys package data, ownership data and timestamps, file hashes and log files, "evidence" that could have helped allay fears of a security problem.


> **andreseso said:**
> I am under the impression that if I execute any program of my old account I will be rooted.
If you don't know what to do then google://CERT+Intruder+Detection+Checklist (also see: Samhain, Aide, debsums, "known good" repo package comparison) should help or please ask for help before doing things without giving thought to the what and why. In the end this will be safer, more efficient and more to the point than trying to migrate whatever data due to a *presumed but never properly investigated* breach of security.


* Not meant as speculation, but since the subverted IRC daemon executes commands as the user it runs as making this work to the advantage of an average attacker (let's assert it runs as user "nobody") this would for example require the attacker to 0) find out you run the ircd, 1) recon version, 2) make it upload a malicious payload and for instance 3) compile and execute an exploit to elevate privileges. Since the amount of root-level compromises involving "traditional" rootkits have been dwindling the past years to nearly zero (feel free to counter if you possess current and practical incident response knowledge) it would be more common to find a kit uploaded containing prefab scanners, IRC bots and DoS tools instead. Not nice to find (but way more easy to detect and clean up after) and not the same level of compromise as a rootkit (which you shouldn't try to clean up anyway).

HTH

---

