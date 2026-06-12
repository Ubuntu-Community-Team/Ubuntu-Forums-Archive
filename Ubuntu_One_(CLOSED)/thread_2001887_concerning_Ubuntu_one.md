---
title: "concerning Ubuntu one"
date: 2012-06-11
forum: Ubuntu One (CLOSED)
---

### Post by Pedroski55 on 2012-06-11
I have Ubuntu one set up, but I don't really understand it, excuse my dullness. Am I correct in assuming, it has copied all the contents of /home/Home/Documents to a computer somewhere on the net??

That is great, if it's right, because I would be in trouble if I lost the data! It is just school stuff, but represents a lot of work!

If I should fry this laptop, I could get another, install Ubuntu, and Ubuntu One would automatically copy the contents of the web based Documents to my new laptop???

Is that how it works??

---

### Post by Ubun2to on 2012-06-11
Well, to make sure it's synchronized, open the Ubuntu One application (by default it's in the Unity sidebar thingy).
It will then pull up a list of folders in sync. If you want to add or remove folders to your account, just check and uncheck the boxes.
If by chance your computer is in a plane crash or a nuclear explosion (or some other event in which your laptop is lost or destroyed), and your data is lost, the data is still on the servers, and will be uploaded as soon as you sign in on your new machine.
So, yes, if your documents folder is in sync, your data is safe unless all their servers are wiped out and they have no backup copies, which is about as likely as wining the $1 billion powerball jackpot.

---

### Post by deadflowr on 2012-06-11
Yes, if you have Ubuntuone setup and your Documents folder added as an Ubuntuone folder, everything you add to it gets uploaded to the cloud. Even documents you work on and save. I have several documents in Ubuntuone, and everytime I work on one and save it, my notification area lights up that that document has been uploaded to Ubuntuone. Not only that but I can access that file from any computer in the world.

---

### Post by Pedroski55 on 2012-06-11
That's cool, thanks! My stuff doesn't even add up to 5GB, so I have no prob!

But wait: what if Mr Gates nukes me and Ubuntu????

btw Ubun2u: you dropped an 'e' in 'refugee'

---

### Post by oldos2er on 2012-06-12
Moved to Ubuntu One.

---

### Post by Dragonbite on 2012-06-13
> **Pedroski55 said:**
> That's cool, thanks! My stuff doesn't even add up to 5GB, so I have no prob!

But wait: what if Mr Gates nukes me and Ubuntu????

btw Ubun2u: you dropped an 'e' in 'refugee'

Because the Ubuntu One process is synchronization, even if the U1 cloud service were to suddenly dissappear it doesn't mean the files on your local system will be removed.  This is a great setup for cloud storage for this reason.

**Folder Synchronization and Confirmation**
As you mentioned, if you set up Ubuntu One on system "A" to synchronize your ~/Documents folder and the ~/Documents folder is set up to be synchronized (*open the Ubuntu One applications and there is an option to choose what to synchronize I believe, else right-click on the ~/Documents folder and select something like "Synchronize with Ubuntu One"*) it will copy all of the files in your folder to cloud storage.

You can verify this by going to the [[COLOR="Blue"]Ubuntu One dashboard[/COLOR]]("http://one.ubuntu.com") and click the [[COLOR="Blue"]Files[/COLOR]]("https://one.ubuntu.com/files/") heading (after logging in of course).

**Ubuntu One Website File Listing**
There you will find a list of your files and folders being synchronized.  You can also download from here to any computer (through the browser), share files and folders and add/delete files.  Any changes you perform through the browser will then be synchronized with computer "A" the next time you log in and it talks to Ubuntu One.

**Synchronizing second computer**
Now if you get a second computer, computer "B", and install Ubuntu on it when you connect its Ubuntu One to your account it will begin to synchronize (download, since chances are your folders are empty at this point) your Ubuntu One folder.

In the Ubuntu One application find the list of synchronized directories and if they aren't already, select those folders you want to synchronize.

**Starting Synchronizing folder already containing files warning**
While I am not 100% sure, it is probably best to set folders to synchronize if the folder is empty (copy the folders to a second folder if you have file).  I think the last time I did it, the files already existing in my folder were wiped out and replaced with the ones from Ubuntu One.  Even if it isn't supposed to, it would probably be a good idea "just in case".

**Manage connected computers**
I think it is included in the Ubuntu One application, or you can manage which computers are connected (or to be synchronized) with your Ubuntu One account through the Ubuntu One website's [[COLOR="Blue"]Your Account[/COLOR]]("https://one.ubuntu.com/account/") page.

**Windows**
I don't know how Windows' version of Ubuntu One works (haven't tried it ... yet).

---

### Post by Ubun2to on 2012-06-13
> **Pedroski55 said:**
> btw Ubun2u: you dropped an 'e' in 'refugee'

*facepalm

---

### Post by Barney-R on 2012-06-15
I hope I'm not hijacking this thread, but I'm pretty vague about this subject.

I've read the above, and understand it as far as it goes, but I'm still not 100% sure what Ubuntu One actually is.

My main interest in on-line storage is as somewhere to store files so I can send or post a download link that others can use, as was the case when ISPs provided a certain amount of web-space to customers.

I'm thinking in terms of sharing (linking to) individual files rather than a full backup for my own use.

Is Ubuntu One suitable for this kind of thing, or do I need to rent some space? It's not really important, just something I found useful when I had my own website (hosted on that "free space" I've already mentioned).

---

### Post by Dragonbite on 2012-06-15
> **Barney-R said:**
> I hope I'm not hijacking this thread, but I'm pretty vague about this subject.

I've read the above, and understand it as far as it goes, but I'm still not 100% sure what Ubuntu One actually is.

My main interest in on-line storage is as somewhere to store files so I can send or post a download link that others can use, as was the case when ISPs provided a certain amount of web-space to customers.

I'm thinking in terms of sharing (linking to) individual files rather than a full backup for my own use.

Is Ubuntu One suitable for this kind of thing, or do I need to rent some space? It's not really important, just something I found useful when I had my own website (hosted on that "free space" I've already mentioned).

**Online Locker**
If all you are looking for is an online locker you can upload files to and share it so you send somebody a link they can click on to get the file and/or entire folders, then there are a number of solutions for that.  Ubuntu One, Dropbox, Google Drive and SkyDrive (Microsoft Live's storage) are all capable.

**using Ubuntu One with synchronization**
With Ubuntu, by default, when you install/turn on Ubuntu One it creates a folder in your ~/ directory called "Ubuntu One".  Any files placed in here will be uploaded to your Ubuntu One cloud storage site.

I am not sure if this can be done locally, but if you log into your Ubuntu One account through the browser you will find a list of all of the files in your Ubuntu One folder listed (if they are done being uploaded).

If it can be done locally, that may make it slightly easier to manage the files and sharing without having to go through the browser.

Clicking the "More" link for whatever file you want to share, you will find an option called "Publish File".  This should produce a link which anybody can use to access this file.

Likewise you can share an entire folder and as you add or remove files in the folder locally, the online version reflect the same.

---

### Post by Barney-R on 2012-06-15
Thanks for that, Dragonbite. You've answered my question, and it looks to me as if you've probably answered Pedroski55's as well, though it's not for me to speak on another's behalf.

Thanks.

---

### Post by Pedroski55 on 2012-06-15
Just one other comment for new users: it seems the up- and download rate is initially set to -1. This is presumably why, in other versions of Ubuntu, UbuntuOne never actually did anything, although it started.

So, new users: set the up- and download speeds to something appropriate, or nothing will happen!!

I have it a 200KB

---

### Post by patriot56 on 2012-07-17
As Dragonbite said 4 weeks ago, I too hope that I'm not hijacking this thread.  This most defiantly is not my intention. 
I am using Duplicity for my backup utility on Ubuntu 11.10 "Oneiric" and I have set Duplicity to backup to Ubuntu One.
Just recently my backups were failing (which is what I expected) because I ran out of space.  Now here's the problem....

When I log into my account (the free 5 gig.'s that U1 offers) I see the folder that I set up to backup to.  When I examine that folder, it shows a bunch of "items" with a .gpg extension, which I assume are encrypted files. (3.0 gig.'s worth).
So I am under the impression that the backup was successful and I should be able to restore these files to the computer.  However when I open Duplicity and point it to the Ubuntu One folder I get an error telling me that there are no files to restore.:confused:
I will be the first to admit that I know very little about backing up to the Cloud.  I'm still not sure that I completely understand it.

Is there anyone that can help me with this?  Offer a solution, more information, advice, etc.  
Your help is greatly appreciated.
Thank you in advance.

---

### Post by jockyburns on 2012-07-17
I'd just like to add, On Saturday, I managed to screw up my Ubuntu 11.04 installation (about a year old) I've now installed 12.04 from scratch and set up Ubuntu One. My .gpg backup files are all there, but can I download them and use them? Not a cat in hell's chance. I've downloaded  a few folders to see what I'd managed to salvage and every one is corrupted. Looks like I've lost about a years worth of stuff. Photo's, documents, music files etc. So I'm not a happy bunny.

---

### Post by Dragonbite on 2012-07-17
> **patriot56 said:**
> As Dragonbite said 4 weeks ago, I too hope that I'm not hijacking this thread.  This most defiantly is not my intention. 
I am using Duplicity for my backup utility on Ubuntu 11.10 "Oneiric" and I have set Duplicity to backup to Ubuntu One.
Just recently my backups were failing (which is what I expected) because I ran out of space.  Now here's the problem....

When I log into my account (the free 5 gig.'s that U1 offers) I see the folder that I set up to backup to.  When I examine that folder, it shows a bunch of "items" with a .gpg extension, which I assume are encrypted files. (3.0 gig.'s worth).
So I am under the impression that the backup was successful and I should be able to restore these files to the computer.  However when I open Duplicity and point it to the Ubuntu One folder I get an error telling me that there are no files to restore.:confused:
I will be the first to admit that I know very little about backing up to the Cloud.  I'm still not sure that I completely understand it.

Is there anyone that can help me with this?  Offer a solution, more information, advice, etc.  
Your help is greatly appreciated.
Thank you in advance.

I would start a new thread on this but my first thought is that when a system is backed up to Ubuntu One (e.g. via DejaDup) it stores it in a hidden folder labeled for the name of the computer it was backing up from. 

So when my computer was named "pixie" (hey! no smirking!), it backed it up to (IIRC) "~/.pixie" in Ubuntu One, or something like it.  

I don't know if you have to specify the folder location or not, but that's just my first though.  I don't have much experience with duplicity.

---

### Post by Pedroski55 on 2012-07-17
Yeah, I found deja-dup messes up videos, some open office files, and maybe other things. As I don't have crazy amounts of stuff, I just back up everything without deja-dup. That said, my 5GB is almost full with my folder Documents.  And I have my entire Home directory copied on an external hd.

---

### Post by patriot56 on 2012-07-18
Thank you all for your valuable input.  I am very grateful.
At this point I am not very please with DejaDup as a backup alternative so I am going to look for something else.
Any suggestions are appreciated.
Also, I'm not too sure about Ubuntu One either at this point.   But I am going to start with another Backup utility first and go from there.

Thanks again for everyone's help... =D>

---

### Post by Dragonbite on 2012-07-18
I am in the process of looking at **Back in Time**. I read somewhere that it can save the files in an uncompressed format similar to **rsync**.

---

### Post by patriot56 on 2012-07-23
> **Dragonbite said:**
> I am in the process of looking at **Back in Time**. I read somewhere that it can save the files in an uncompressed format similar to **rsync**.
Thanks Dragonbite.
I'll take a look at it an see if it'll work for my needs.
Do you know if there is an application for Linux that will take a snapshot (image) of the drive and allow you to restore from that image?

Thanks again mate.

P.S.  Sorry it took so long to respond. :oops:  I was working on another project and forgot all about this thread.  (senior moment)#-o

---

### Post by Dragonbite on 2012-07-23
> **patriot56 said:**
> Thanks Dragonbite.
I'll take a look at it an see if it'll work for my needs.
Do you know if there is an application for Linux that will take a snapshot (image) of the drive and allow you to restore from that image?

Thanks again mate.

P.S.  Sorry it took so long to respond. :oops:  I was working on another project and forgot all about this thread.  (senior moment)#-o

You mean like Clonezilla (a Linux distro)?  I've wondered about setting it up as a dual-boot with my Linux (or any, really) system so I can boot into it and tell it to clone the other partitions into an image on a NAS or something.

I just used Clonezilla recently to copy my Windows 7 disk onto a larger Windows 7 disk.  Since I did disk-to-disk (with an external USB drive in the middle) I had to go into it with Ubuntu LiveCD (10.10) and re-arrange the partitions (move the 2nd partition to the end and have the OS partition grow to include the empty space).

A handy thing with Clonezilla is that after it asks you questions regarding which disk to what location, and before it runs it gives you the command you would use if you wanted to do the same thing again.

---

### Post by patriot56 on 2012-07-24
> You mean like Clonezilla (a Linux distro)?  I've wondered about setting  it up as a dual-boot with my Linux (or any, really) system so I can boot  into it and tell it to clone the other partitions into an image on a  NAS or something.Yea, that's exactly what I was talking about.:)  So cool.  
Here's the scary thing, (*and by scary I'm referring to my own ignorance*)  I downloaded Clonezilla several months ago but I've never booted it.  I can't give a reason, other than perhaps, another one of those "confounded senior moments" ([FONT=Comic Sans MS]and being one qualifies me to be able to say that[/FONT]).

I will boot it up and give it a try.  I like the idea of dual booting it too.  At this point I don't have the HDD space to provide for a backup location however, I do have a number of DVD-RW disk's that I can use.

Hmm, I'm gonna to do a little experimenting. :-k
Thanks again for your help mate.
As always, it is very helpful and appreciated.=D>

---

### Post by Dragonbite on 2012-07-25
Yesterday I realized that when I booted up my cloned Windows 7, it immediately began updating the SkyDrive.  I thought "great, it will download all of the new files".  No!  Instead, my SkyDrive reverted to what the local system looked like, before I moved things around! Argh!

But since I did a disk-to-disk clone to the USB drive, I was able to plug the hard drive in, as a second drive, enable it (Windows didn't like them having the same name and identifiers) and copied the files from the cloned image in the new drive and let it update SkyDrive to my CURRENT view.

I'm not sure exactly how Ubuntu One would handle it, if any better.

---

### Post by Ubun2to on 2012-07-25
> **Dragonbite said:**
> Yesterday I realized that when I booted up my cloned Windows 7, it immediately began updating the SkyDrive.  I thought "great, it will download all of the new files".  No!  Instead, my SkyDrive reverted to what the local system looked like, before I moved things around! Argh!

But since I did a disk-to-disk clone to the USB drive, I was able to plug the hard drive in, as a second drive, enable it (Windows didn't like them having the same name and identifiers) and copied the files from the cloned image in the new drive and let it update SkyDrive to my CURRENT view.

I'm not sure exactly how Ubuntu One would handle it, if any better.

In my experience, it copies the files from the server in the same layout as they were uploaded. So, if you liked the configuration on another computer, and got a new one, you don't have to mess around with rearranging everything.
It doesn't move any files around-if there are any clones in different locations, it will upload those files, unless you delete them so they will no longer be available for download on other computers.
However, I recommend wiping all your folders that you want to sync and manually placing everything in that was already there. This will help you make sure you don't go over your 5 GB cap and that there won't be any duplicate files.

---

