---
title: "New Cloud Sync service Copy.com"
date: 2013-05-22
forum: The Cafe
---

### Post by Roasted on 2013-05-22
It's nice seeing all of these other services come about. If you think about all of the space you get from signing up with multiple vendors it's crazy. I'm still relatively content with my ownCloud server. 3TB of cloud service in my own basement on my own hardware? Yes plz. :P

---

### Post by Dragonbite on 2013-05-23
> **Roasted said:**
> It's nice seeing all of these other services come about. If you think about all of the space you get from signing up with multiple vendors it's crazy. I'm still relatively content with my ownCloud server. 3TB of cloud service in my own basement on my own hardware? Yes plz. :P

I'm tempted in putting an ownCloud server on an Amazon Web Service account so that it has the best parts of Dropbox (file sync, web access), some of Google Docs (some editing capabilities) and the data is mine! All Mine! mwah! Ha! Ha!  :p

Of course depending on how much activity and space you use it could get expensive but theoretically you don't have to worry about running out of space.

---

### Post by Roasted on 2013-05-23
> **Dragonbite said:**
> I'm tempted in putting an ownCloud server on an Amazon Web Service account so that it has the best parts of Dropbox (file sync, web access), some of Google Docs (some editing capabilities) and the data is mine! All Mine! mwah! Ha! Ha!  :p

Of course depending on how much activity and space you use it could get expensive but theoretically you don't have to worry about running out of space.

Yeah - it totally depends on your situation. In my case, I already had a server running at home for various tasks with 3TB of RAID'd storage. In the future I might increase that accordingly, which would only give me more storage access. Sure, I have to maintain the thing with updates and whatnot, but once it was set up I don't think I've touched it aside from upgrading from 4.5 to 5.0. Beyond that it's just kind of... worked.

---

### Post by nobodysbusiness on 2013-05-24
The only problem that I see with an ownCloud server set up in your basement would be the danger from having copies of your data in close proximity. For example, let's say that you just have your home computer that you use to work with your data. That computer is backed up to the ownCloud server in the basement. What happens if there's an unexpected house-fire? Your main computer and the ownCloud server could both be destroyed in the same incident.

Having an off-site backup with [Copy.com]("https://copy.com?r=odoDlI") or some other service would reduce the risk.

---

### Post by TheGurkha on 2013-05-25
> **nobodysbusiness said:**
> What happens if there's an unexpected house-fire?.

Yep, it's those unexpected ones that catch you out :)

My question is, once I've downloaded the Copy tgz and unzipped it, what do I do with the files? 

Do I copy the folder to /usr/bin?

Thanks in advance.

---

### Post by nobodysbusiness on 2013-05-25
@TheGurkha: I took the directory and put it into a directory in my home dir, actually. You could copy the directory to "/home/your_username/opt/copy" and it works fine. Once the files are copied into place, then you simply have to go to the "x86_64" directory (I'm assuming you're on 64-bit) and run the CopyAgent program. It would be something like this:

```
cd /home/your_username/opt/copy/x86_64
./CopyAgent
```

---

### Post by converted on 2013-05-25
Is there anything extra that most folks are having to do?  Following the instructions has not seemed to result in a working service for me.

I have installed, agent is running, it shows in my tray.  I have added a small number of files.  The agent show 0 bytes, 0 files sync'ed.  I have rebooted just in case.  The agent shows "scanning for changes" endlessly in the menu that pops up when I right-click it.

The website shows a quickstart pdf which is NOT in my local "copy" folder.

I have verified that the agent knows what folder I want to sync -- have tried the "move copy folder" option just in case, and it let's me know I'm trying to move the folder inside itself...

I'd like to be really excited to get another 15GB of cloud storage for free -- but so far it seems not to actually work.  (Clearly not the case for everyone.)

Has anyone had to mess with it at all to get it working?

I'm running Cinnamon 1.8 on 13.04, but I wouldn't expect the DE to make a difference...

Edit:  For whatever reason when I created a folder through the website it seemed to kick everything off.  Now folders I put into the copy folder have synced and vice versa.  Hopefully will come in handy for someone else...

---

### Post by nobodysbusiness on 2013-05-25
@converted: The service is still pretty new, so they probably still have some bugs. The main value in signing up now is so that you'll have your account with however many GB of space available. The bugs will be fixed in time, but the space is forever. Remember, though, you don't just get 15 GB of storage space for free, you get 20 GB if you sign up through someone else's referral link ([like this one, for example]("https://copy.com?r=odoDlI")).

---

### Post by Dragonbite on 2013-09-09
Now that people have started using it for a while, has anybody run across any problems with their Copy installation or use?

I'm still trying to figure out the best setup (locate the tar files, and tell it to use another directory?  Run it all from one palce?).  What setup are you using?

I'm up to 132 GB of space (which is more space than my laptop's hard drive ;) )!  I'm just about to turn off my Dropbox account for cross-platform and cross-distro synchronization (leaving Ubuntu One and SkyDrive for OS-specific things like Visual Studio solutions and etc.)

---

### Post by zacktu on 2013-09-21
I've experimented by placing symbolic links to other directories in my Copy folder.  They are synced with my Copy directory at copy.com.  The icons for the directories appear to imply that the directories are shared.  If I right click on a directory icon for details, the directory appears to be Public.  What is being implied here?

---

### Post by vicsar on 2013-09-22
> **Dragonbite said:**
> ... be willing to drop my 25GB of SkyDrive.

Thanks Dragonbite.

Here is my referal code, please use it to get extra storage, for both of us.

---

### Post by mJayk on 2013-09-23
Not another why why why so many

---

### Post by knpoe on 2014-02-23
i tested this for a bit- honestly..  i kinda like dropbox.com>than -- but the copy.com stuff definitely is feature rich.

---

### Post by ssam on 2014-02-23
I use OwnCloud, on a mini-itx server at home. Gives me 4.5TB of storage and if I want more I just put a new disk in. Privacy is very good because its in my house and all transport is over HTTPS.

---

### Post by Dragonbite on 2014-02-23
> **knpoe said:**
> i tested this for a bit- honestly..  i kinda like dropbox.com>than -- but the copy.com stuff definitely is feature rich.

Dropbox definitely has the advantage in apps available to save/work with files stored in there. If I could get src:kit (a Chrome extension) working, it allows me to edit files stored in Dropbox in a color-syntax editor (I used it for PHP files).

Otherwise Copy isn't too bad, but its online offerings are limited.

---

### Post by PJs Ronin on 2014-04-15
> **ssam said:**
> I use OwnCloud, on a mini-itx server at home. Gives me 4.5TB of storage and if I want more I just put a new disk in. Privacy is very good because its in my house and all transport is over HTTPS.
winner

---

### Post by Dragonbite on 2014-04-15
Is ownCloud tricky to get up and running in Ubuntu?

---

### Post by mgmiller on 2014-04-15
Works very well for me.  It even supports symlinks in your home directory.  Just right click the file or folder and select "Make Link"  the resulting icon is then dragged into your Copy folder and it just works.  You can get a free extra 5 GB by signing up with this link:  [https://copy.com?r=aTrLih](https://copy.com?r=aTrLih)

---

### Post by jnaphta on 2014-04-18
It works fine with symlinks, good alternative to Ubuntu One, specially for that big amout of free storage. Here is my referral link [https://copy.com?r=RS9B4K](https://copy.com?r=RS9B4K) use it for signing up and get 20GB.

---

