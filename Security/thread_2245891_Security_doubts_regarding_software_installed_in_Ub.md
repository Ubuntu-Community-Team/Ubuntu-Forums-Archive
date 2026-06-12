---
title: "Security doubts regarding software installed in Ubuntu 14.04"
date: 2014-09-26
forum: Security
---

### Post by intuition2 on 2014-09-26
Hi everyone!

I'm a new user to Ubuntu, and linux systems in general, so when I first got it, I accepted help from a friend to install it about 2 weeks ago. 

While he was starting to mess with the comands I was, of course, very curious and trying to learn from it, but the guy is programmer and he was so fast I couldn't keep up with all the new information.

So I kept asking questions, like what is this and that, but at some point he just stared very serious at the screen, not replying to me at all, except to ask me to introduce my password everyonce in a while, and he did act weird specially when I asked him what were all the shh... os ssh.. he was typing in the terminal, and also what kind of software was landscape, and he did not tell me at all.

So later, in the beggining of this week we met and he turned into a stranger, he was making all sort of different conversations with me (that I usually don't have with him but with more close friends) it felt a bit weird because he was acting soooo diferent but just like one of my bestfriends did in a recent fb conversation! I felt like he changed personality and started to be more open, but eventhough that was red flag, I though hummm since he's so easy going right now, let me ask about the stuff he installed that he didn't tell me in the beginning, and it took me a while but I started to remember those names, you know the shh or sshh... and the landscape thing, and asked him what was that about, he told me to my face: "Oh, I didn't install that program, and I don't know what shh comands you're talking about! Never heard of it and can't remember using them on your lap-top!"

So, he was obviously lying, maybe I'm freaking out, and instead of being grateful I was becoming suspicious about him, so I talked to a mutual friend who also immediatly told me: "Yeah!!! That guy always knows stuff about me I could swear I never told him!"

So, basically, I want to know if any of you guys know something about those commands and programs, and of course if he could be spying on me, and what can I do to get rid of those, or others I missed and still don't have a clue what might be!

I'm afraid I gave him permissions for whatever he did install, so how can I know what's from the original system and what's not?

He told me this would be one of the safest systems I could ever get but.. I don't feel safe at all!!!

Any ideas?!?

Many thanks!

---

### Post by mörgæs on 2014-09-26
Hi, welcome to the fora.
If in doubt the best you can do is installing anew, erasing all of the present system in the process.

---

### Post by intuition2 on 2014-09-26
Humm... I though of that like in a last option scenario.. I've just spent so many up-late nights trying to install everything I need.. Isn't there any other way? Or something I could run to get rid of bad stuff, or a list of all the original system programs so that I can uninstall and delete all the others I don't know? Or somekind of program that detects hidden malefic software? Or any way I can find or track if he or someone was really hacking or spying for sure sure???

---

### Post by Irihapeti on 2014-09-27
I would look at it this way: your machine has been hacked. OK, not by some unknown individual out there in cyberspace, but that doesn't make a huge difference. You don't know what on earth your "friend" has done to it, and the things your mutual friend has told you don't inspire confidence.

Most people will recommend reinstalling in the circumstances. Losing a bit of time - even several late nights - is far better than wondering what this individual may know about you (and do with the information).

To make things easier in future, you could make notes (even in an old-fashioned paper notebook) about the tweaks you make. I've found this very helpful on a number of occasions.

---

### Post by Lars Noodén on 2014-09-27
> **intuition2 said:**
> Humm... I though of that like in a last option scenario.. I've just spent so many up-late nights trying to install everything I need.. Isn't there any other way? Or something I could run to get rid of bad stuff, or a list of all the original system programs so that I can uninstall and delete all the others I don't know? Or somekind of program that detects hidden malefic software? Or any way I can find or track if he or someone was really hacking or spying for sure sure???

+1 for re-installing.  It is the one way to be sure.  

However, if you have installed a lot of packages, you can carry that list over to your new system.  

```

dpkg --get-selections > packages.list

```

Then just copy the file packages.list to a USB stick or something that you can use after you re-install.  It will have a list of what you've added or removed.  

Once you have reinstalled, read them in on the new system and tell it to make the changes:

```

sudo dpkg --set-selections < packages.list
sudo apt-get dselect-upgrade

```

---

### Post by mörgæs on 2014-09-27
... but that will copy the dubious packages into the new system as well.

---

### Post by Irihapeti on 2014-09-27
> **mörgæs said:**
> ... but that will copy the dubious packages into the new system as well.

I agree. Better to decide what packages you want to be in the system and go from there. It takes longer but is safer.

---

### Post by Lars Noodén on 2014-09-27
Yes, there is a point there.  I was thinking more that the dubiousness of any packages lay in the configuration rather than the packages themselves.  And the dselect-upgrade method only copies the clean packages directly from the Ubuntu repositoriesd with fresh configurations.

---

### Post by intuition2 on 2014-09-27
OKay guys! I've made up my mind, I will try to delete everything and make a fresh start!
 I knew I should have done it myself, I tried to keep up with the steps, but honestly it looked much harder and it took much longer than I imagine it would take in the first place (around 3 hours), specially for a pro like him! 
I think he really made it look complicated! But I'm not sure if I'll be able to do it on my own... :( 

Regardless of that, I also think it would be really important to figure out if he did something or not, and** I'm afraid if I delete everything I just delete all the important evidences plus I will never know the truth**, and I really need to know! 
Also, I don't have many friends that use linux around here (lol about 2, being him one of them) and I don't want to rule out anyone based only in suspicion!...

---

### Post by thnewguy on 2014-09-27
Usually installing Ubuntu takes around twenty minutes, maybe a little more for customizations. Three hours strikes me as being an awfully long time to install any operating system. A typically install of Ubuntu will just get you to run the installer and click "Next" a few times, followed by entering a new username and password for yourself. That should be it to get a basic fresh installation.

After that I'm sure you'll want to tweak things a little, but the initial setup probably won't be nearly as long as your associate made it seem the first time.

---

### Post by mörgæs on 2014-09-27
I understand that you would like to know what the guy installed on your computer but searching for it is a big task, especially if you are new. 

You need on-site help from an experienced user and even with that you can never be sure that you discovered all his tricks. And yes, **if** he installed an ssh server without you knowing nor accepting it you should be worried about tricks. A normal user does not need it.

If you have an extra hard disk you could remove the present one and keep it for future testing while you install a fresh system on the other.

---

### Post by uRock on 2014-09-27
One way to see if the guy installed the ssh server would be to open the Software Center and see if it is installed. At this point, I wouldn't trust the guy's installation, but at least you will have some solid information next time you talk to the guy and something to mention to friends in reference to his IT morals.

Open Ubuntu Software Center and search for openssh-server. This is not installed by default. If it is marked as "installed", then he has opened the door to log into your computer. This would also be a sign that you may need to reset your router, because it may be possible that he set it to forward ports to the machine.

If you have any questions on installing and configuring ubuntu, then please feel welcome to start a new thread on each question and one of the folks will likely be able to help you through it.

---

### Post by qyot27 on 2014-09-27
> **Lars Noodén said:**
> +1 for re-installing.  It is the one way to be sure.  

However, if you have installed a lot of packages, you can carry that list over to your new system.  

```

dpkg --get-selections > packages.list

```

Then just copy the file packages.list to a USB stick or something that you can use after you re-install.  It will have a list of what you've added or removed.  

Once you have reinstalled, read them in on the new system and tell it to make the changes:

```

sudo dpkg --set-selections < packages.list
sudo apt-get dselect-upgrade

```
get-selections doesn't provide a list of everything you added or removed.  It's a list of every package installed, period.  The set-selections/dselect method is also prone to break if the package names change between versions of Ubuntu (for those of us that do fresh installs every time).

A more streamlined and accurate method is to get the information straight from the apt logs (/var/log/apt/history.log and any of its older gzipped brethren).  That will show you what's been installed and removed, and it does so chronologically so you can ignore the base install's packages and only focus on post-install changes.

---

### Post by Lars Noodén on 2014-09-28
> **qyot27 said:**
> get-selections doesn't provide a list of everything you added or removed.  It's a list of every package installed, period.  The set-selections/dselect method is also prone to break if the package names change between versions of Ubuntu (for those of us that do fresh installs every time).

get-selections shows what has been uninstalled, too.  However, everything, even the default items, are in one long laundry list with no other information.  Since he is staying on the same version, it should work fine, especially since it will only install from a safe source - the official repositories.  But, as you describe, going to a new version might occasionally introduce a problem.  But then it will complain and that package can be hunted manually.  Though any dodginess would not be with the packages but with their configuration, a clean sweep is probably even better.

> **qyot27 said:**
> 
A more streamlined and accurate method is to get the information straight from the apt logs (/var/log/apt/history.log and any of its older gzipped brethren).  That will show you what's been installed and removed, and it does so chronologically so you can ignore the base install's packages and only focus on post-install changes.

More accurately, /var/log/dpkg.log shows what has been added or removed post-install, so the long list of default items is not needed.  Even with that, there is a lot of log noise that needs to be trimmed with awk

```

less /var/log/dpkg.log

```

or 

```

 awk '$3 ~ /install/ || $3 ~ /remove/ { print $0 } ' /var/log/dpkg.log | less

```

@intuition2, that line will give you a chronological list over what has been added or when.  The time stamp will show if it occured when he was putting in those hours on the machine.  But it will not give any information about the configuration of said changes, which would be the real determination of the situation.

That said, a full install goes quickly, especially from the Desktop image.

---

### Post by Doug S on 2014-09-28
I would have a look at the .bash_history file to try to investigate what the person did, at least for command line stuff. However a clever bad person might have edited the file and removed some content. ( I realize I might be too late with this suggestion.)

---

### Post by intuition2 on 2014-09-28
So it would be unlikely that it would take that long, approximately 3 hours would be too much, plus anyone knows if it would be required to type those shh, or ssh, at any moment during or after installation?!? Also, is it possible to know if the configurations have been changed at any point from what they supposed to be in the original form? Is it possible to detect them?!? Also another thing I find weird while trying to go through the software is that I only got this system 2 weeks ago, (so everything installed dates back from 2 weeks further on) but when I go to the Software history it goes back around 2 months ago, in July when I didn't even had the system... Is that normal?

---

### Post by Doug S on 2014-09-28
> **intuition2 said:**
> So it would be unlikely that it would take that long, approximately 3 hours would be too muchYes.> **intuition2 said:**
> plus anyone knows if it would be required to type those shh, or ssh, at any moment during or after installation?!?I think no, but am not sure.> **intuition2 said:**
> Also, is it possible to know if the configurations have been changed at any point from what they supposed to be in the original form? Is it possible to detect them?!?I do not know. I always keep a copy of the original file and can always compare to that. You might be able to save some of the files and then compare after you do a new installation.> **intuition2 said:**
> Also another thing I find weird while trying to go through the software is that I only got this system 2 weeks ago, (so everything installed dates back from 2 weeks further on) but when I go to the Software history it goes back around 2 months ago, in July when I didn't even had the system... Is that normal?It is hard to know for sure what you are talking about. The attached is a screen shot of the "software center" - "history" for a 14.10 VM I installed on September 16th, and you can see it only goes back to September 16th. However, if you are referring to file date stamps, then yes they can be from whenever, example (from the same VM):```
doug@desk-dev:~$ [COLOR=#ff0000]ls -l /etc[/COLOR]
total 1132
drwxr-xr-x  3 root root     4096 Sep 16 00:39 acpi
-rw-r--r--  1 root root     2981 Sep 16 00:33 adduser.conf
-rw-r--r--  1 root root       44 Sep 28 11:24 adjtime
drwxr-xr-x  2 root root     4096 Sep 28 11:15 alternatives
-rw-r--r--  1 root root      401 [COLOR=#ff0000]Jul  7[/COLOR] 02:22 anacrontab
-rw-r--r--  1 root root      112 [COLOR=#ff0000]Jan 10[/COLOR]  2014 apg.conf
drwxr-xr-x  6 root root     4096 Sep 16 00:36 apm
drwxr-xr-x  3 root root     4096 Sep 28 11:23 apparmor
drwxr-xr-x  8 root root     4096 Sep 28 11:23 apparmor.d
...
```By the way, here is my .bash_history file for that VM, as an example:```
doug@desk-dev:~$ [COLOR=#ff0000]cat .bash_history[/COLOR]
sudo apt-get update
sudo apt-get dist-upgrade
[COLOR=#ff0000]sudo apt-get install openssh-server[/COLOR]
df
ls -l /boot
dpkg -l | grep linux-
sudo updatedb
locate sysctl.conf
cat /etc/sysctl.conf
ls -l /proc/sys/net/netfilter
sudo apt-get update
sudo apt-get dist-upgrade
dpkg -l | grep evi
dpkg -l | grep evin
grep evin /var/log/*
ls -l
df
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get update
sudo apt-get dist-upgrade
locate .jpg
locate .jpg | more
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get update
sudo apt-get dist-upgrade
ifconfig
ping 192.168.111.13
ls -l
ls -l /etc
logout
sudo apt-get update
sudo apt-get dist-upgrade
ls -l
ls -l /etc
ps aux | grep ssh
last
```
[ATTACH=CONFIG]256779[/ATTACH]

---

### Post by Irihapeti on 2014-09-28
> **intuition2 said:**
> plus anyone knows if it would be required to type those shh, or ssh, at any moment during or after installation?!?

I've done a fair number of installations and never had to use ssh during the install process.

ssh is used for connecting to and doing things to other systems. If you're not wanting to do that, then you don't need it.

---

### Post by intuition2 on 2014-09-28
So I opened the Ubuntu Software Center and searched for openssh-server and got nothing, but when looking for ssh I got:
- Openssh-client (6.6p12ubuntu2)
- libssh-4 (0.6.1-ubuntu3)
- ssh-askpass-gnome (6.6p1-2ubuntu2)
(These ones were all installed in July)

I also looked for that only program that I actually could recall "Landscape" and I did find:

- Landscape-client-ui-install (Installed in July)
- Landscape-common (15 set)
- Landscape-client-ui (15 Set)
- Landscape-client (15 Set)

I also went through my .bash_history but the first thing I got was my very first command and none of the previous ones he did insert right in front of me! Weird, right? Is it possible that he deleted them? I didn't insert many so the list is still really short, because most stuff I've installed through the software center.

So what would you guys think of that?!

All the stuff in the past goes back to the same hour, 10:01, all on the date, 22 of July (...I assume 2014)

When I go to History, I actually have more files on that date, than in all the other dates, all together... There are a lot of stuff I wouldn't recognize but somehow sound strange or weird to me (probably just for not being familiar with them!) I'll just name a few of them to give you guys an idea: "python", "libipc", "telepathy", "zenity", "gnome", "ghostscript-x", "nautilus-sendto-empathy", "cpp", "xinput", "popularity-contest", "bluez-alsa", "wodim", "zeitgeist", "casper" and so on... Really a lot of stuff, some of them repeat with some differences.. 

From the installation date there are only a few that sound weird.. like "clam-tk", "lib", "linbencode-locate-pearl", "clamav", "landscape", "python" again... 

Do any of these words ring a bell?!?


(By the way, I'm very thankful that all of you are helping me!!!)

---

### Post by intuition2 on 2014-09-28
I also got that list Lars mentioned and this was what I got:

2014-07-22 22:19:07 ........Too many things way before... Let me know if you need them.. I think they would fill around 20 pages tho... 
2014-07-22 22:19:07 install user-setup:all <none> 1.48ubuntu2
2014-07-22 22:19:07 install casper:i386 <none> 1.340
2014-07-22 22:19:08 install lupin-casper:all <none> 0.55
[B]2014-09-15 05:09:04 install libclamav6:i386 <none> 0.98.1+dfsg-4ubuntu1.1
2014-09-15 05:09:08 install clamav-base:all <none> 0.98.1+dfsg-4ubuntu1.1
2014-09-15 05:09:10 install clamav-freshclam:i386 <none> 0.98.1+dfsg-4ubuntu1.1
2014-09-15 05:09:11 install clamav:i386 <none> 0.98.1+dfsg-4ubuntu1.1
2014-09-15 05:09:11 install libcairo-perl:i386 <none> 1.104-1
2014-09-15 05:09:12 install libglib-perl:i386 <none> 3:1.304-1
2014-09-15 05:09:13 install libpango-perl:i386 <none> 1.224-2
2014-09-15 05:09:14 install libgtk2-perl:i386 <none> 2:1.249-2
2014-09-15 05:09:15 install libcarp-clan-perl:all <none> 6.04-1
2014-09-15 05:09:15 install libbit-vector-perl:i386 <none> 7.3-1build1
2014-09-15 05:09:16 install libdate-calc-perl:all <none> 6.3-1
2014-09-15 05:09:17 install libencode-locale-perl:all <none> 1.03-1
2014-09-15 05:09:17 install libhttp-date-perl:all <none> 6.02-1
2014-09-15 05:09:18 install libfile-listing-perl:all <none> 6.04-1
2014-09-15 05:09:18 install libhtml-tagset-perl:all <none> 3.20-2
2014-09-15 05:09:19 install libhtml-parser-perl:i386 <none> 3.71-1build1
2014-09-15 05:09:20 install libhtml-tree-perl:all <none> 5.03-1
2014-09-15 05:09:20 install libio-html-perl:all <none> 1.00-1
2014-09-15 05:09:21 install liblwp-mediatypes-perl:all <none> 6.02-1
2014-09-15 05:09:22 install libhttp-message-perl:all <none> 6.06-1
2014-09-15 05:09:22 install libhttp-cookies-perl:all <none> 6.00-2
2014-09-15 05:09:23 install libhttp-negotiate-perl:all <none> 6.00-2
2014-09-15 05:09:23 install libnet-http-perl:all <none> 6.06-1
2014-09-15 05:09:24 install liblwp-protocol-https-perl:all <none> 6.04-2ubuntu0.1
2014-09-15 05:09:24 install libwww-robotrules-perl:all <none> 6.01-1
2014-09-15 05:09:25 install libwww-perl:all <none> 6.05-2
2014-09-15 05:09:26 install clamtk:all <none> 4.45-1
2014-09-15 05:09:28 install libdate-calc-xs-perl:i386 <none> 6.3-1build1
2014-09-15 05:09:29 install libfont-afm-perl:all <none> 1.20-1
2014-09-15 05:09:29 install libhtml-form-perl:all <none> 6.03-1
2014-09-15 05:09:30 install libhtml-format-perl:all <none> 2.11-1
2014-09-15 05:09:30 install libhttp-daemon-perl:all <none> 6.01-1
2014-09-15 05:10:49 install gnuchess:i386 <none> 6.1.1-1
2014-09-15 05:10:52 install gnome-chess:i386 <none> 1:3.8.3-1
2014-09-15 05:11:11 install gnuchess-book:all <none> 1.02-1
2014-09-15 05:12:43 install python-twisted-names:all <none> 13.2.0-1ubuntu1
2014-09-15 05:12:44 install python-configobj:all <none> 4.7.2+ds-5build1
2014-09-15 05:12:46 install landscape-common:i386 <none> 14.01-0ubuntu3[/B]
[B]2014-09-15 05:12:47 install landscape-client:i386 <none> 14.01-0ubuntu3
2014-09-15 05:12:49 install landscape-client-ui:i386 <none> 14.01-0ubuntu3[/B]
2014-09-15 15:29:05 install hunspell-en-ca:all <none> 1:4.2.1-0ubuntu1
2014-09-15 15:29:06 install hyphen-en-us:all <none> 2.8.6-3ubuntu2
2014-09-15 15:29:07 install libreoffice-l10n-en-gb:all <none> 1:4.2.6.3-0ubuntu1
2014-09-15 15:29:08 install libreoffice-help-en-gb:all <none> 1:4.2.6.3-0ubuntu1
2014-09-15 15:29:10 install libreoffice-l10n-en-za:all <none> 1:4.2.6.3-0ubuntu1
2014-09-15 15:29:10 install And the list goes on with the stuff I did install later... 

I've used **BOLD** to highlight the stuff he installed during the time of installation, he was on it from around 2.00 am to 5.00 a.m. with the shh commands back and forward.. But it looks like he only started to install stuff from 5:09 to 5:12... So I duno what to think anymore... 
Do any of you guys see anything strange or suspicous?!

---

### Post by Irihapeti on 2014-09-28
I don't see why you would need Landscape-client. It's for remote administration of PCs, for example in a corporate network. Did you ask him to manage your PC for you?

---

### Post by fugu2 on 2014-09-28
> **intuition2 said:**
> I'm afraid if I delete everything I just delete all the important evidences plus I will never know the truthOk, so Ill will go a head and disagree with what the experts are saying, just to play devils advocate. What you said is true, you'll never know if you delete that stuff. And him being your 'friend', im sure he'll find a reason to stop back inside your house for some reason, and if you reinstall everything he could trojan it again.  Most of the time it only takes ~15 seconds to comprise a computer (especiaslly on linux if your gurentted to have the correct password.) So, why not trick him up a bit and buy a 2nd computer he doesn't know about. you can keep his trojans on the orginal one, and you only power it up when he is around. he'll try and re-trojan the hell outta it and when he gets home he won't have acces to your computer. You only use the 'clean' computer for everything you do and everything he touches is the old computer which he knows the password too. Oh and change your password(on the new computer). lol

---

### Post by intuition2 on 2014-09-29
No I didn't ask for any kind of remote assistance! 

He knew I was about to change to Ubuntu and offered to help! I remember saying something like... "It can't be that hard" but he somehow convinced me it wouldn't be that easy that he should help in case it would get tricky. Anyhow, it's my fault I accepted it, I think I believed in him because he is programmer and after all a new operating system.. 

Before coming in here, I asked him several times what were shh commands and the landscape thing but he denied typing those things... So once he started to play stupid I started to get really suspicious about him.

Anyway, after coming in here, I already tried to play games with him to see if he would fall for them, so I told him I was thinking about installing it in another computer, if he would be kind enough to pass me all the steps he used through the command line "You know all the sshh's you used for like 3 hours" and he told "Oh, I don't have them, I know them by heart".

But then he did insist a lot asking: "but are you getting a new computer? Are you going to install it again on your laptop? Which printer do you have? I could help you again one of these days if you like!"
And then I asked "Why would like to know which printer I use?
He didn't explained and logged off.

---

### Post by Elfy on 2014-09-29
Just reinstall it. The longer you wait the more time there is for someone to connect from somewhere else external - _if they're going to._

If you want to keep the old install - create a new partition for the new install - and then the old partition and data will be there till you remove that partition.

---

### Post by intuition2 on 2014-09-29
He probably already did in the past I'm afraid and if so there's nothing I can do to change it.

What I can do is to concentrate on the future now (and with some help, of course) I could try to find proof that he actually did it and catch him for good. 

Of course I won't let him get close to any of my devices again until I get this straight, but if he did there must be a way to find out.

For instance, that Landscape Service, it's the only program I have installed in the System itself, none of the other lie there... So I can actually access it directly from the System Settings (which I find weird) when I try to click on it the following message appears:

"System Policy prevents you from reading and writing landscape client Settings.
An application is attempting to perform an action that requires privileges.

Authentication is required to perform this action"

Ask for password - I insert it - and try to authenticate it

But then a message pops out on the top right corner saying "Landscape management service - Authentication failed" 


I can't do anything with it, but if someone can, can I know who?!?

---

### Post by Irihapeti on 2014-09-29
I don't know if there's any way to find out what he's been up to, and if there is, it may not be worth the effort.

To me, your best way forward would be to reinstall, keeping the old partition if you really want to (so it can be investigated later on), and then take your time to learn how to use Ubuntu. Unless you've got some really unusual hardware, it's not generally difficult to get Ubuntu working the way you want. If you want to know something, ask in the relevant area of the forums. Most people are happy to help.

They want to see you learn how to do it yourself, not tell you that it's likely to be too hard for you. :)

---

### Post by mörgæs on 2014-09-29
Threads merged.
Please stop double-posting.

---

### Post by Doug S on 2014-09-29
Note: I agree with all the previous input, you should just re-install. I am just addressing some of your previous points, to try to help.

> **intuition2 said:**
> So I opened the Ubuntu Software Center and searched for openssh-server and got nothing, but when looking for ssh I got:
- Openssh-client (6.6p12ubuntu2)
- libssh-4 (0.6.1-ubuntu3)
- ssh-askpass-gnome (6.6p1-2ubuntu2)
(These ones were all installed in July)These are normal. ssh client installation is normal.> **intuition2 said:**
> I also looked for that only program that I actually could recall "Landscape" and I did find:
- Landscape-client-ui-install (Installed in July)
- Landscape-common (15 set)
- Landscape-client-ui (15 Set)
- Landscape-client (15 Set)Already answered. I just wanted to say that the "landscape-client-ui-install" part of it is normal, the rest is not.> **intuition2 said:**
> I also went through my .bash_history but the first thing I got was my very first command and none of the previous ones he did insert right in front of me! Weird, right? Is it possible that he deleted them?It is not necessarily weird, as your friends stuff might have been during installation and before things were all setup. It is possible he deleted entries. It is also possible he set up a different user and then there would be another .bash_history file for that user.> **intuition2 said:**
> All the stuff in the past goes back to the same hour, 10:01, all on the date, 22 of JulyThat I find odd. I can only assume the installation was actually some clone install or something from one done on July 22nd. From your next post, the change point from July 22nd to September 15th is at about the right point between a new installation completion and subsequent stuff.> **intuition2 said:**
> When I go to History, I actually have more files on that date, than in all the other dates, all together... There are a lot of stuff I wouldn't recognize but somehow sound strange or weird to me (probably just for not being familiar with them!) I'll just name a few of them to give you guys an idea: "python", "libipc", "telepathy", "zenity", "gnome", "ghostscript-x", "nautilus-sendto-empathy", "cpp", "xinput", "popularity-contest", "bluez-alsa", "wodim", "zeitgeist", "casper" and so on... Really a lot of stuff, some of them repeat with some differences..Yes, most, if not all, of these seem strange or weird to you due to due to lack of familiarity. You will go crazy if you want to understand the purpose and need for every single package.> **intuition2 said:**
> From the installation date there are only a few that sound weird.. like "clam-tk", "lib", "linbencode-locate-pearl", "clamav", "landscape", "python" again... The clamav stuff is an antivirus program. To learn more go to the [package web pages]("http://packages.ubuntu.com/trusty/clamav") to look up packages, which often also have an upstream link.

Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=2246136"), and see if you can learn anything from the last or lastlog commands.

---

### Post by intuition2 on 2014-09-29
> **mörgæs said:**
> Threads merged.
Please stop double-posting.

I didn't mean to double-post, I did ask here first, but more in a general way regarding the "security" of all the software installed.

Once we could determine that, at least, **Landscape** was an identified potential risk, I though I should try to seek more specific help about the Landscape Service itself, _hoping to find a more specialized team for me to ask in the relevant area of the forum_. 
(I also tried t look online for their contacts but couldn't find any. I ask them directly on their webpage and got a promotional standard mail back, I don't think anyone has even read my problem yet.)

I don't understand why it was brought back here (unless the specialized team there is the exact same team here, of course) because I would really like to know if anyone got to view or answer my threat before you moved it back here. I also think other people with the same problem regarding the specific software would find it interesting.

---

### Post by Elfy on 2014-09-29
Ubuntu Landscape is not a security risk in and of itself. 

You appear to think you've got issues with an existing install - that unless you've done something and not told anyone in thread - has been in that state for a couple of days at least.

Deal with that installation - that was the reason for this thread - numerous people have given you the exact same advice - reinstall.

Given your apparent reluctance to actually deal with the suspected issue - someone with access to the machine I'm wondering about the veracity of the thread in general.

This issue is now going round in circles. 

Thread Closed.

---

### Post by Elfy on 2014-09-30
re-opened - for the moment

---

