---
title: "Ubuntu One Alternative, now that it's being shut down?"
date: 2014-04-08
forum: Ubuntu One (CLOSED)
---

### Post by NoBugs! on 2014-04-08
Sadly it looks like Ubuntu One is shutting down now - does anyone know of any alternatives that offer:

[LIST]
[*]Decent amount of space
[*]Good Ubuntu app
[*]Good OSS Android app available on F-droid (not Play)
[/LIST]

It's sad that the one good OSS app for Android-pc syncing I've found will now be useless :(

---

### Post by lukeiamyourfather on 2014-04-08
Google Drive, ownCloud, DropBox. I'm sure there are others.

---

### Post by thnewguy on 2014-04-09
I found ownCloud to be a good alternative. It's open source, cross-platform and free.

---

### Post by oldfred on 2014-04-09
Four alternatives discussed:

[http://www.omgubuntu.co.uk/2014/04/three-alternatives-ubuntu-one](http://www.omgubuntu.co.uk/2014/04/three-alternatives-ubuntu-one)

---

### Post by MadMax2 on 2014-04-09
I'm confused. I use google drive and as far as I can tell google Drive/ \docs and Ubuntu One are apples and pears. In Ubuntu One I work on my PC or laptop and save to a folder where they are synced with the cloud folder. With Drive I work within the website, which is an inferior environmet except in some circumstances (e.g I have some simple spreadsheets I update on my smartphone).
Qu. There used to be an app called Google gears which synced but it doesn't work with lynux or was discontinued?
Qu. Drop Box syncs on Linux and windows?
 -----
A.odt is synced to Ubuntu One and is in the Documents folder. It is altered and the altered docoment goes to the cloud.
What happens in Drop Box?

---

### Post by bapoumba on 2014-04-09
> **MadMax2 said:**
> 
Qu. Drop Box syncs on Linux and windows?
 -----
A.odt is synced to Ubuntu One and is in the Documents folder. It is altered and the altered docoment goes to the cloud.
What happens in Drop Box?
Yes, there are clients for Linux, Mac OSX, Windows, iOS, Android.
If you modify A.odt which is in the Dropbox folder, changes are synced and reflected on all the machines you have setup in your Dropbox account.

---

### Post by marco-parillo on 2014-04-09
> **MadMax2 said:**
> I'm confused. I use google drive and as far as I can tell google Drive/ \docs and Ubuntu One are apples and pears. In Ubuntu One I work on my PC or laptop and save to a folder where they are synced with the cloud folder. With Drive I work within the website, which is an inferior environmet except in some circumstances (e.g I have some simple spreadsheets I update on my smartphone).
Qu. There used to be an app called Google gears which synced but it doesn't work with lynux or was discontinued?

Google Drive offers a sync application that creates a folder on Window that it synchronizes (similar to Ubuntu One, and Drop Box). There is no official sync application for Google Drive on Linux, though there are unofficial ones.

---

### Post by MadMax2 on 2014-04-09
I see Drop box works like Ubuntu One on Linux and windows. The difference is that Drop Box places a folder in the home folder of each machine and you can treat it as a second documents folder.

---

### Post by MadMax2 on 2014-04-09
You wont want the whole Dropbox folder placed on a Smartphone. Ubuntu One let you choose files to down load on a particular computer?

---

### Post by lukeiamyourfather on 2014-04-09
Google Drive can be mounted in Linux through FUSE.

[https://github.com/astrada/google-drive-ocamlfuse](https://github.com/astrada/google-drive-ocamlfuse)

---

### Post by oscar-brito-ir on 2014-04-11
All I want is a cloud client to be able to sync folders outside the default one or at least rename the folder, that's the key feature I used u1. I could sync complex files keeping the internal directory structure Any ideas of some client to do this? Please.


Note:
 mean, Blender files. My username is the same in all my machines so the paths were exactly the same and now that I have to change the location of my folder all my file's texture links are broken, HDRIs and such.

---

### Post by bapoumba on 2014-04-16
Moved a bunch of referral posts out of here to this one : [http://ubuntuforums.org/showthread.php?t=2217206](http://ubuntuforums.org/showthread.php?t=2217206)

---

### Post by mgmiller on 2014-04-16
> **oscar-brito-ir said:**
> All I want is a cloud client to be able to sync folders outside the default one or at least rename the folder, that's the key feature I used u1. I could sync complex files keeping the internal directory structure Any ideas of some client to do this? Please.


Note:
 mean, Blender files. My username is the same in all my machines so the paths were exactly the same and now that I have to change the location of my folder all my file's texture links are broken, HDRIs and such.


Yes, Copy does this.  It creates ~/Copy and then you just create symlinks to whatever you want in your Home and drag the links into the Copy folder.  Your internal directory structure remains unchanged.

Works very well for me.  Just right click the file or folder and select "Make Link"   the resulting icon is then dragged into your Copy folder and it just  works.  They give you 15 GB free and you can get a free extra 5 GB by signing up with this link:  [COLOR="#FF0000"]Edit : removed referral link, website is[/COLOR] [http://copy.com](http://copy.com)

Best price by far and it is cross platform for windows, mac, linux, android, etc.

---

### Post by bapoumba on 2014-04-16
@ mgmiller and everyone else : please move your referral links to this thread : [http://ubuntuforums.org/showthread.php?t=2217206](http://ubuntuforums.org/showthread.php?t=2217206)
Thanks.

---

### Post by cbtengr on 2014-04-16
I have installed Copy on 13.10 - works fine so far with one exception.  The Indicator icon doesn't function - none of the menu items appear, only
greyed out email address.  There is a discussion about this problem on the Copy forum.

[https://copy.zendesk.com/entries/28050018-Ubuntu-13-10-indicator-icon-](https://copy.zendesk.com/entries/28050018-Ubuntu-13-10-indicator-icon-)

---

### Post by bapoumba on 2014-04-16
I'll have a look tonight on 14.04. Just registered today (have to say that the dmg works OK on Mac OSX Mavericks).

---

### Post by cbtengr on 2014-04-16
Thanks, it also works on my Mac.  It seems to be the indicator that isn't 
playing well with Unity.

---

### Post by bapoumba on 2014-04-16
I'm on lubuntu 14.04, we'll see but it appears from the thread you linked to that the issue has not been fixed for 14.04. They are talking about a ppa, I may have overlooked the discussion, I cannot find which one it is.

---

### Post by bapoumba on 2014-04-16
Well, fortunately I've taken a screenshot during the setup process on lubuntu 14.04. Was working quite well. Rebooted, and now the only way to start it up is to run ./CopyAgent from the /opt/copy folder where I installed it per [http://ubuntuforums.org/showthread.php?t=2217206&p=12989518#post12989518](http://ubuntuforums.org/showthread.php?t=2217206&p=12989518#post12989518)
The icon then shows up and sync works (checked with files added to the Copy folder in my /home that appear in the web interface).

I have to find now a way to autostart. Been testing a few simlinks and reboots, but I have not found it yet. I'm done on this for tonight, will look again tomorrow.

Edit, I could not resist, things like that bug me until I find a workaround :D
Added this line to /home/<my_user>/.config/lxsession/Lubuntu/autostart
```
/opt/copy/CopyAgent
```
Sync and tray icon start up after a logout/log back in, and of course, a reboot.

---

### Post by axerun on 2014-04-18
installed Copy on my Ubuntu 13.10.  Others have already mention problems with the tray icons. In addition I found that syncing pictures from both my Galaxy S3 (android) and Jolla (sailfish/android)phones was troublesome. Then tried dropbox, and that one worked very well. Easy peasy to get 50GB of free space. Rune

---

### Post by cbtengr on 2014-04-18
> **axerun said:**
> installed Copy on my Ubuntu 13.10.  Others have already mention problems with the tray icons. In addition I found that syncing pictures from both my Galaxy S3 (android) and Jolla (sailfish/android)phones was troublesome. Then tried dropbox, and that one worked very well. Easy peasy to get 50GB of free space. Rune

How do you get 50GB for free?

---

### Post by axerun on 2014-04-18
> **cbtengr said:**
> How do you get 50GB for free?


Sorry, I might have been a little "too quick on the draw" here. :smile:

I have 52GB for free today, but most of it, it seems, I earned (48GB) because of my Samsung S3 phone (Dropbox pre-installed).  This Samsung promotion expires after 2 years.  ....so hardly such a good deal as I thought yesterday. :sad:

Rune

---

### Post by badman35 on 2014-04-20
I would like to know how to get the backup files that Déjà Dup Backup Tool put on my U1? I have close to one and half years werth of backsups from three desktops on there..

---

### Post by xubuntu84 on 2014-04-22
My solution to this problem was to continue using Google Drive (15 GB free, 100 GB for $2/month) like I always had, and use Insync to automatically sync everything.  I have successfully replaced Ubuntu One with it and it has Nautilus integration (right click > Insync > sync), so that you can sync anything you want outside of the Insync folder (this automatically creates a symlink for you).

If your desire is to maintain two computers (ie desktop and laptop) mirror images of each other, such as your ~/Documents folder, InSync will [do the trick]("http://www.benmctee.com/2014/04/replace-ubuntu-one-with-insync.html") via symlinks.

You can try it free for a couple of weeks to see if it fits the bill.  After that, you pay some small fee ($15?) for the continued use.  Totally worth looking into: [https://www.insynchq.com/](https://www.insynchq.com/)

---

### Post by David_Aaron_Groves on 2014-04-22
I know it does not have a linux cliet, that I know of, but honestly, OneDrive (SkyDrive) is awesome. I have 80GB of storage for free from them. You start with 7 but they always send me emails giving me free space. Over the last yeah I went from 7GB to 80GB... pretty awesome stuff.

---

### Post by badman35 on 2014-04-23
that won't help me at all.. the Déjà Dup Backup Tool  put all the backup file on U1 not on my pc. I want to get all my backups but I can't with insync or any other cloud storage service.

---

### Post by weaseldb83 on 2014-04-23
Sorry; I feel for you; Thats why I never store online.

---

### Post by Jon Hanna on 2014-05-01
> **badman35 said:**
> the Déjà Dup Backup Tool  put all the backup file on U1 not on my pc. I want to get all my backups but I can't with insync or any other cloud storage service.

If you pull all your files off the site as a zip, the zip will contain the gpg files of the backups in a single folder, and déjà dup can be set to use the folder you move it to as a new location, and you can then synch that folder with another service to have off-site copies.

Edit: I think u1ftp still works, which would allow you to cherry-pick downloads more easily than one zip while conversely not being as much work as picking out each file individually.

I'm using déjà with copy via copy-fuse while also using the copy app but ignoring the folder the backup writes to so that (the bug with the indicator aside) I've got a set-up now that's pretty close to how u1 worked, with the advantage of being more able to exclude folders within included folders so all in all if they fix that indicator bug I'll be happier than I was with u1. Still it's definitely worth shopping around in terms of features, free storage limits, cost per storage beyond that, etc. For me google drive's not following links or junctions on Windows was a show-stopper but that wouldn't matter to people who either don't use Windows or are happy with how it works on Win, while another person who doesn't care about lack of upload from mobile might like the greater security provisions of SpiderOak, and so on.

And do see if there are referral links possible for anything you have yet to sign up for; I understand the reasons for not allowing links in posts, but since they give you more storage as well as the referrer (e.g. currently Copy you start with 20GB instead of 15, SpiderOak you start with 3GB instead of 2GB) ask around your friends to see if any are using the service in question already, for your mutual benefit.

---

### Post by Jon Hanna on 2014-05-01
We'd chosen Ubuntu One for a reason, and hence I'm sure I'm not the only one who would like the other services to act the same way. I wrote [this short article]("http://www.hackcraft.net/u12copy/") about how I got Copy to act more like U1 did. In particular, having Déjà Dup use it without needing to have a local copy requires a little bit of work.

I'd be interested to hear if anyone did better with other services too (while the UI bugs remain in Copy, I could still be convinced to move to something else).

---

### Post by bapoumba on 2014-05-02
Here is a thread where it's been discussed : [http://ubuntuforums.org/showthread.php?t=2215788](http://ubuntuforums.org/showthread.php?t=2215788)

---

### Post by Jon Hanna on 2014-05-02
Yeah, I read that when I started looking into replacements, and the last post on it is by myself. I was thinking of how to get U1-like behaviour out of those choices than the question of which choice to go for, but if you as forum mod think the overlap is too great to justify a thread, could you merge them?

---

### Post by bapoumba on 2014-05-02
Threads merged :)

---

### Post by rvboutin on 2014-05-03
Hi,
For file storage there are other options I agree, but as it is now, Ubuntu One is also the account used to synchronised the installation of applications between computers in the software center, and it is a useful feature!! How is this going to work once Ubuntu One is gone??
Cheers,
Rv

---

### Post by Jon Hanna on 2014-05-04
> **rvboutin said:**
> Hi,
For file storage there are other options I agree, but as it is now, Ubuntu One is also the account used to synchronised the installation of applications between computers in the software center, and it is a useful feature!! How is this going to work once Ubuntu One is gone??The same as it does now, as per the announcement that it is only the file storage/sharing that is ending.

---

### Post by RichardET on 2014-05-04
So how do I retrieve my files from Ubuntu before they are deleted?

---

### Post by LastDino on 2014-05-04
^ There is ''download'' options if I'm not forgetting.  


It is sad that they are letting go of it as it actually worked really well for me, now I'm stuck with dropbox.

---

### Post by bapoumba on 2014-05-05
> **RichardET said:**
> So how do I retrieve my files from Ubuntu before they are deleted?

> **Goten0007 said:**
> ^ There is ''download'' options if I'm not forgetting.  


It is sad that they are letting go of it as it actually worked really well for me, now I'm stuck with dropbox.

A Download files as .zip appeared the other day on the website.

---

### Post by RichardET on 2014-05-05
There is a "Ubuntu One" forum folder and the website to download and then delete files was posted.

[https://login.ubuntu.com/](https://login.ubuntu.com/)

---

### Post by rasos on 2014-05-08
If you do not want to host ownCloud by yourself, you may try [http://allmenda.net](http://allmenda.net). They have integrated ownCloud with GroupOffice, which offers also webmail and syncing of files, address and calendars. They are hosting outside the US (where NSA has no access) and are organised as a co-op of open source specialists.

---

### Post by Sleepy-zz-John on 2014-06-09
> Originally Posted by rvboutin 
[I]Hi,
For file storage there are other options I agree, but as it is now, Ubuntu One is also the account used to synchronised the installation of applications between computers in the software center, and it is a useful feature!! How is this going to work once Ubuntu One is gone??[/I] > **Jon Hanna said:**
> The same as it does now, as per the announcement that it is only the file storage/sharing that is ending. Oh dear!   I've just uninstalled U1 and 10 associated U1 packages that I thought software center had apparently forgot to remove.  Does this mean I ought to reinstall some of them if I want software center to continue to work properly?   Original reason for uninstalling everything was to get rid of U1's stubborn green check arrows on previously sync'd folders,  and to eliminate a tiresome U1 closedown message that kept reappearing.

---

### Post by Sleepy-zz-John on 2014-06-09
Anyone given any thought to hubic.com  [https://hubic.com/en/offers/](https://hubic.com/en/offers/) ?   Their 25GB free offer is higher than most,  and they appear to support all platforms and sync-ing.  Based in France.   Any recommendations?   Any known snags?

---

### Post by bapoumba on 2014-06-09
> **Sleepy-zz-John said:**
> Anyone given any thought to hubic.com  [https://hubic.com/en/offers/](https://hubic.com/en/offers/) ?   Their 25GB free offer is higher than most,  and they appear to support all platforms and sync-ing.  Based in France.   Any recommendations?   Any known snags?
Had a closer look. It's OVH which has a good reputation.
If you read French, here is a recent review : [http://www.tomsguide.fr/article/comparatif-stockage-ligne-gratuit-cloud,2-1231-6.html](http://www.tomsguide.fr/article/comparatif-stockage-ligne-gratuit-cloud,2-1231-6.html)
To make it short, the main drawbacks are it's slow and you cannot edit a file stored there (for ex with an office app). More for a backup than a live directory as Dropbox can be. There used to be no limit for storage and it got abused, surprisingly..
Been using Copy, which works pretty well, if you leave out the tray icon problems.

---

### Post by Sleepy-zz-John on 2014-06-09
Here are extracts from the response I've received from Mega.co.nz if anyone's interested:
> we do have a FREE account you could test before you purchase a PRO account. With our FREE account you get a globally accessible, high-performance, secure cloud drive with 50 GB of storage space.

Your FREE account and its contents don't expire until you cancel / delete it.

You will not be able to install the MEGA Sync Client on those devices in question, as it is only available for Windows.

The launch of our Mac and Linux Sync clients has been scheduled for June of this month.

---

### Post by Navneet_Kumar on 2014-06-09
Yeah.......dropbox is working fine on my system and it is promising also.........
New features for enhanced accessibility and ease of use are regularly updated..............:D

---

### Post by Sleepy-zz-John on 2014-06-09
> **bapoumba said:**
> Had a closer look. It's OVH which has a good reputation.
If you read French, here is a recent review : [http://www.tomsguide.fr/article/comparatif-stockage-ligne-gratuit-cloud,2-1231-6.html](http://www.tomsguide.fr/article/comparatif-stockage-ligne-gratuit-cloud,2-1231-6.html)
To make it short, the main drawbacks are it's slow and you cannot edit a file stored there (for ex with an office app). More for a backup than a live directory as Dropbox can be. There used to be no limit for storage and it got abused, surprisingly..
Been using Copy, which works pretty well, if you leave out the tray icon problems. Hmm... thanks.   Hubic doesn't sound too bad for my purposes,  and I admit their 25GB is tempting!   However I've also sent a couple of enquiry e-mails out,  one to Mega.co.nz who are also offering 25GB free,  and another to Justcloud.com whose website doesn't make it clear what the upper GB limit of their free offer is,  or whether there's any time limit on their free offer.  Will wait for these two replies before coming to any conclusion.     

Interesting that so many posters on here are plumping for Copy.com.  Dunno whether that's because it really does have the best specification,  or if it's something to do with their special offer,  or perhaps because people just like to follow others rather than step out of line.       For the moment I'll keep Hubic and Mega.co.nz and Copy.com and Justcloud.com on my shortlist.

---

### Post by bapoumba on 2014-06-09
I've tried mega, but it lacks a client, only has the web interface last time I checked, so it is less convenient. Works on the phone though. Copy pretty much works as Dropbox that I already was using, so I did not look further. I used one of the referrals from the referral thread and got 25G iirc, compared to the Dropbox 5G, good enough for me for non-sensitive stuff.

---

### Post by Sleepy-zz-John on 2014-06-15
I've now registered with Hubic and started saving some material there by uploading via their web facility.  That all seems to be working OK and with 25 free GB available there,  it's nice not having to worry much about file sizes :)   I'm having some difficulties with their sync system though.  Haven''t managed to log-in to it so far.  I do need to persevere with that some more,  but if it turns out to be buggy and flawed (I'm not sure whether it's them or me at the moment) I'm wondering if there'd be any snag registering simultaneously with a second cloud with a better proven reputation for sync'ing like Dropbox or Copy.    Could then use that for sync and Hubic for my heavier files.      Might not be wise to attempt duplicate cloud system sync'ing,  but for the simple cloud storage part,  can anyone envisage a problem keeping two cloud systems current?     ,

---

### Post by bapoumba on 2014-06-15
> **Sleepy-zz-John said:**
> I've now registered with Hubic and started saving some material there by uploading via their web facility.  That all seems to be working OK and with 25 free GB available there,  it's nice not having to worry much about file sizes :)   I'm having some difficulties with their sync system though.  Haven''t managed to log-in to it so far.  I do need to persevere with that some more,  but if it turns out to be buggy and flawed (I'm not sure whether it's them or me at the moment) I'm wondering if there'd be any snag registering simultaneously with a second cloud with a better proven reputation for sync'ing like Dropbox or Copy.    Could then use that for sync and Hubic for my heavier files.      Might not be wise to attempt duplicate cloud system sync'ing,  but for the simple cloud storage part,  can anyone envisage a problem keeping two cloud systems current?     ,
Do you mean keep the same folder synced for 2 different cloud storage applications ? Such as say Dropbox and Copy ? I had never thought of that, and use them separately as I used Ubuntu One and Dropbox. I keep work files with one and personal files with the other and do not mix them. I do not know how they handle file permissions for their own local synced folders tbh and if that could cause problems.

I suppose this is for you to try with a test folder :)

---

### Post by Sleepy-zz-John on 2014-06-17
> **bapoumba said:**
> Do you mean keep the same folder synced for 2 different cloud storage applications ? Such as say Dropbox and Copy ?   No,  that's not exactly what I meant,  but thanks for the thought anyway :guitar:   My original idea was to have only one of them, for example Copy sync'd,  and the other simply as a web-cloud (Hubic with its free 25GB in my case)  for heavy files that might run the risk of exceeding my limit on Copy. That ought to be safe enough, don't you think? >  I had never thought of that, and use them separately as I used Ubuntu One and Dropbox.  Might be tempting fate too much to try and sync two clouds on the same folder.  I wasn't thinking of risking that,  but your idea might be OK if one sets up two seperate sync'd folders,  one say for Dropbox and a different one for Copy.  >   I keep work files with one and personal files with the other and do not mix them. I do not know how they handle file permissions for their own local synced folders tbh and if that could cause problems.

I suppose this is for you to try with a test folder :) Yes, and probably be safer to keep seperate folders IMHO if we were to go in for sync'ing two different clouds.

I was wondering if anyone here has actually tried running two clouds simultaneously   ??

---

