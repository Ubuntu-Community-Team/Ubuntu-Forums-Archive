---
title: "New Notifier for Gmail, Calendar, Wave, Reader and Google Voice"
date: 2009-11-26
forum: The Cafe
---

### Post by brandoncolorado on 2009-11-26
I have been looking for something like this for a long time.  Found a great notifier today, and thought I would share it with you guys.  It is a Linux/Windows system tray notifier for Google Voice, Google Calendar, Google Reader, Gmail, and Google Wave.

It is definitely in the early stages of development, but it is the best Google Voice notifier out there right now.

Take a look!

[http://googsystray.sourceforge.net/](http://googsystray.sourceforge.net/)

---

### Post by toupeiro on 2009-11-26
Liking it!  I can confirm its working well with wave as well.

---

### Post by Paqman on 2009-11-26
Looks nice. I like the way it only notifies of RRS once there's a number of new posts. Will definitely install this later.

---

### Post by brandoncolorado on 2009-11-26
A new name would be nice, would help with popularity and search rankings.

---

### Post by Mateo on 2009-11-26
not push = no thanks.

---

### Post by Junkieman on 2009-11-29
Just what I was looking for, notification of reader RSS feeds :)

Note: You need to install python-gtk2-dev for it to work

---

### Post by Paqman on 2009-12-09
Been using this for a few weeks now, really like it. Good find!

---

### Post by Junkieman on 2009-12-12
I'm just a bit worried about how it saves your Gmail password in plain text, but I guess our trusty GNU/Linux OS is pretty safe; I'm just overly security-conscious ;)

---

### Post by AldenIsZen on 2009-12-12
> **brandoncolorado said:**
> 

It is definitely in the early stages of development, but it is the best Google Voice notifier out there right now.

Thanks for sharing!

> **Mateo said:**
> not push = no thanks.
I am not sure exactly what you are wanting to "push".

> **toupeiro said:**
> Liking it!  I can confirm its working well with wave as well.

Good to know.

> **Paqman said:**
> Looks nice. I like the way it only notifies of RRS once there's a number of new posts. Will definitely install this later.

 Good to know as well.

> **Junkieman said:**
> I'm just a bit worried about how it saves your Gmail password in plain text, but I guess our trusty GNU/Linux OS is pretty safe; I'm just overly security-conscious ;)

I agree, if I understand correctly though, anything running in userpsace, i.e. without root access can possibly access all other userspace files. etc. This means one program could read it from another or it's files. They may need to target a particular application, such as this, but I guess they could just do a search for passwords in general, depending on how they are stored. I really do not know what I am talking about exactly, but I would think this would be high on the priority list of changes...

 I think this is a great idea and like the SMS screen shot.  I think I will hold off testing this for now, as much as I want to, for the naked password reason. :popcorn:

---

### Post by TheNessus on 2009-12-12
This is awesome. 

The only thing lacking is that it doesn't show how many emails you have on the icon itself - instead, you have to hover the mouse over it to see.

---

### Post by AldenIsZen on 2009-12-12
> **TheNessus said:**
> This is awesome. 

The only thing lacking is that it doesn't show how many emails you have on the icon itself - instead, you have to hover the mouse over it to see.

 Good idea, perhaps in time that option, or others will be added.

 I have posted about the unencrypted password on the SourceForge.net project page [here]("https://sourceforge.net/projects/googsystray/forums/forum/1005365/topic/3487461"), in case anyone is curious and wants to be updated. (or add suggestions...) You can monitor the project or thread without posting if you wish.

edit/ Update about plain text password below, or [click here]("http://ubuntuforums.org/showpost.php?p=8489539&postcount=17") to go there now.

---

### Post by Ms_Angel_D on 2009-12-12
Hey thanks for sharing this, does anybody got a deb?

---

### Post by TheNessus on 2009-12-12
> **Ms_Angel_D said:**
> Hey thanks for sharing this, does anybody got a deb?
You don't need one really, it's very easy to install. (and I HATE not using debs).
need help?

---

### Post by Ms_Angel_D on 2009-12-12
> **TheNessus said:**
> You don't need one really, it's very easy to install. (and I HATE not using debs).
need help?

Well kinda I managed to get it installed in Kubuntu, but it seems like it will only run as root, I can't start it under my own account.

---

### Post by TheNessus on 2009-12-12
> **Ms_Angel_D said:**
> Well kinda I managed to get it installed in Kubuntu, but it seems like it will only run as root, I can't start it under my own account.
how did you install it?

anyway, works ok for me, I downloaded it to the desktop, extracted, and
cd
cd Desktop
cd googsystray or whatever folder
sudo python setup.py install

---

### Post by Ms_Angel_D on 2009-12-12
> **TheNessus said:**
> how did you install it?

anyway, works ok for me, I downloaded it to the desktop, extracted, and
cd
cd Desktop
cd googsystray or whatever folder
sudo python setup.py install

Never mind I rebooted and it's working fine now, thanks for the offer of help though ;)

---

### Post by AldenIsZen on 2009-12-13
> **Junkieman said:**
> I'm just a bit worried about how it saves your Gmail password in plain text, but I guess our trusty GNU/Linux OS is pretty safe; I'm just overly security-conscious ;)

 Yes, Jim Duchek convinced me that it should not be a concern:

                                            Short answer, yes, plaintext.  Long answer:
  Yes, the password is stored in plaintext, although the file is chmod'd such that only your user can see it. There are no plans to 'encrypt' it, although I'm adding an option where if you leave it blank, it'll ask you every time you start it up, for those worried about it being left on the disk (in the next version released, likely) I may look into trying to use gnome-keyring from Python. I haven't looked into it much, and here's why:
  There is no way to 'encrypt' a password you need on disk without requiring another password to unencrypt it. You can, of course, do something like Firefox (if you don't use a master password, which most people don't) and just obfuscate the password, but that's merely security theatre -- anyone with access to the file would still be able to get your password, albeit with a little bit more effort on their part. Regardless, anyone capable of getting access to arbitrary files in your home directory is more than capable of un-obfuscating something like that.
  The following scenarios would allow an attacker to get access to this file:
  1> Anyone gains root access to your system. From the network, extremely difficult on most 'Desktop' installs most people use -- they're pretty locked down.
  2> Anyone gains physical access to your machine and knows what they're doing -- steals/copies the contents of your hard drive, reboots with init=/bin/sh, etc. If you're anal enough to be worried about this, you probably ought to be encrypting your drives anyhow.
  3> Anyone gains access to read arbitrary files with the permissions of your user (A situation where an attacker managed to, say, be able to run programs as 'mail' or another random user would not be able to access this file, which constitute most *nix exploits)... or just somehow found out the PW to your user and logged in, which means I doubt your Google password is any more secure ;) There have been browser/java/javascript/etc exploits like this in the past, although they're pretty rare and usually patched quite quickly.
  All in all the only method of getting at this file (that doesn't seem extraordinary) is somebody sitting down at your machine while unattended and looking at it. Obfuscation could help a little bit in this case (making such a person take a little bit more time in front of your machine), but I don't want anyone to be thinking their password is somehow 'encrypted' when it's really not, which is why I will never use obfuscation. 



 Thanks again Jim.

---

### Post by Junkieman on 2009-12-13
> **AldenIsZen said:**
> Good idea, perhaps in time that option, or others will be added.

You should suggest that on the Feature Tracker ;)

> **AldenIsZen said:**
> I have posted about the unencrypted password on the SourceForge.net project page

I [requested this as a feature update]("http://sourceforge.net/tracker/?func=detail&aid=2905770&group_id=277278&atid=1177511"), sorry I should have posted the link sooner :p But he gives some technical reasons too if anyone keeps up. Security is such an interesting anomaly ;)

Jim is correct that physical access is the biggest threat, and then all your files are at risk anyway.

---

### Post by AldenIsZen on 2009-12-13
> **Junkieman said:**
> You should suggest that on the Feature Tracker ;)

Perhaps I might, now that I will be trying it out likely later today. :D
> 
I [requested this as a feature update]("http://sourceforge.net/tracker/?func=detail&aid=2905770&group_id=277278&atid=1177511"), sorry I should have posted the link sooner :p But he gives some technical reasons too if anyone keeps up. Security is such an interesting anomaly ;)

Jim is correct that physical access is the biggest threat, and then all your files are at risk anyway.That Google OAuth sounds interesting Wesley. I think it would be great to get it in the keyring, since that is something "central". Perhaps once I start learning programming... Security is interesting, at least to me. Always a challenge, but no excuse for not understanding it. Definitely an anomaly.

---

### Post by AldenIsZen on 2009-12-15
Update:

Version 1.2 still seems to have a few bugs, and I couldn't get it to run but once, and that was only the preferences that I couldn't get to close with"OK, until I restarted. That also seemed to allow it to be found in my Internet section of the applications menu, unless I missed it the first time. But the only thing not working so far is remembering the tick mark for startup, but we wil see if another restart helps...

 The SMS worked well and I got the test message to my cell in less than 10 seconds. Can you say one click and send yourself short notes to take with you! Sweet! I still have yet to really give out my Google Voice # to many people and have no one to Wave with, but I definitely am liking what I see.

---

### Post by AldenIsZen on 2009-12-17
Another update: This software just got featured on [Lifehacker]("http://lifehacker.com/5428836/googsystray-notifies-you-of-new-activity-across-google-services-in-one-system-tray-app?skyline=true&s=i")! That's AWESOME! :guitar:

Thank you for sharing brandoncolorado!

---

### Post by richrosa on 2009-12-19
I had a permissions issue. I just needed chmod the tmp file to get it working. 

```

sudo chmod 777 /tmp/googsystray/

```

---

### Post by DeadSuperHero on 2009-12-19
Any chance of this working with libnotify/Ayatana notifications?

---

### Post by AldenIsZen on 2009-12-20
> **Mr. Psychopath said:**
> Any chance of this working with libnotify/Ayatana notifications?

 I think he was considering it. If you want more info, see the project support section. I know I saw mention of it in there.

---

### Post by aok109 on 2009-12-28
Mine crash a few seconds after starting configured window or sms. Even when i open About window. Please help.

---

### Post by TheNessus on 2009-12-28
a serious bug:

when the internet connection goes off and then on (happens often with wireless) , googsystray does not log on properly, and uses aprox 100% CPU.

---

### Post by AldenIsZen on 2009-12-30
> **aok109 said:**
> Mine crash a few seconds after starting configured window or sms. Even when i open About window. Please help.
How did you install it?

> **TheNessus said:**
> a serious bug:

when the nternet connection goes off and then on (happens often with wireless) , googsystray does not log on properly, and uses aprox 100% CPU.
 have noticed 100% CPU myself, but I thought it was due to me hibernating a lot. (Ubuntu gets made at me in general for that.) You may want to post this on the project support page. Jim would be able to run down what is happening quickest and avoid the issue.

---

### Post by aok109 on 2009-12-31
I install the way it was explained on their website.

- Download and untar the .tar.gz source archive.

terminal and type the 'sudo python ./setup.py install'

---

### Post by aok109 on 2009-12-31
> **aok109 said:**
> I install the way it was explained on their website.

- Download and untar the .tar.gz source archive.

terminal and type the 'sudo python ./setup.py install'

I got it to work after download version 1.1.0 and after installing it gave permission:
 
sudo chmod 777 /tmp/googsystray/

but configuration window hang when i click on auto start up. But is working now.

---

### Post by AldenIsZen on 2009-12-31
> **aok109 said:**
> 
but configuration window hang when i click on auto start up. But is working now.

Yea, that happened to me as well, so perhaps either it is a flaw in the code, or something to do with Ubuntu. Others have mentioned it as well.

---

