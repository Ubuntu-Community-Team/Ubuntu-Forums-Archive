---
title: "My purchased music won't download"
date: 2010-03-26
forum: Ubuntu One (CLOSED)
---

### Post by blazemore on 2010-03-26
I've bought 1 song successfully from the Ubuntu One Music Store, and it downloaded within 5 minutes.
Last night I bought an album, and this morning all the songs still say they're transferring to Ubuntu One Storage.
What's going on here?

---

### Post by duckleet on 2010-03-26
Have you filed a bug report yet on it.

---

### Post by derekeverett on 2010-03-26
I'm to chicken to jump into 10.04 yet so I'm no help with your issue.

But I did want to congratulate you on your fine music taste sir.

---

### Post by Holmen on 2010-03-26
I have the same problem with two songs that I've purchased. I can download them from one.ubuntu.com, but they wont download with the local client.

---

### Post by blazemore on 2010-03-26
> **Holmen said:**
> I have the same problem with two songs that I've purchased. I can download them from one.ubuntu.com, but they wont download with the local client.

Mine aren't even on one.ubuntu.com
They're not transferring to that.

---

### Post by StephenDavison on 2010-03-26
I ran into a similar problem with my first (and so far only) purchase from the music store (Concrete Blonde - Concrete Blonde).  In this case 11 of the 12 tracks downloaded.  I contacted 7digital.com customer support and received the reply quoted below.  Unfortunately, this isn't very helpful because I can't (or at least don't know how) to login to 7digital directly.  I've now followed up asking for more help and will post back here if they are able to help me.

Also, I just realized that purchased music does not sync. into the  ~/Ubuntu One directory; instead, it goes into ~/.ubuntuone.  

> Dear Customer, 

Thank you for submitting your query to the 7digital Customer Services team.

A member of our team will reply to you shortly.

If the problem you are experiencing is related to downloading from 7digital or one of our partner stores, please try downloading it again from your locker - [http://us.7digital.com/locker](http://us.7digital.com/locker) - as this solves most problems - and if it does please let us know (via the link above)! 

If you have any additional information or comments you would like to add to your case, please update it by clicking on the link at the top of this message.

Kind Regards,
7digital Customer Services

---

### Post by joshuahoover on 2010-03-26
For those having problems downloading music, please try the following from a terminal session:

u1sdtool -c
u1sdtool -s

The first command will connect the client if it's not connected and the second command will show you the status of the connection (online/offline, what it's doing, etc.)

If you're connected and still don't see your files, can you please hop on #u1msbeta on Freenode IRC and ask for help there? You can also file a bug at: [https://bugs.launchpad.net/rhythmbox-ubuntuone-music-store/+filebug](https://bugs.launchpad.net/rhythmbox-ubuntuone-music-store/+filebug)

Thanks to everyone for trying out the music store prior to 10.04 LTS being released!

Joshua

---

### Post by StephenDavison on 2010-03-29
Thanks for that tip Joshua.  I haven't tried the IRC channel yet, but last week I did submit a request through the U1MS customer service link in Rhythmbox.  Should I expect a reply to the e-mail address submitted there?  (Haven't received one yet.)  I'll try the IRC channel before submitting a bug request in Launchpad.

---

### Post by Rifester on 2010-04-18
Joshua,
I tried out the Ubuntu One Music Store last night for the first time!  Great work, I think this is a really cool feature.  I spent a bit of time exploring Ubuntu one last night and must admit I am impressed (I was very skeptical).   It took me some time to figure out where my music was saved locally.  Is it possible to have the music files save directly to the Music folder or the folder of the users choice?  Thank you for your work!

---

### Post by Tuxee on 2010-04-18
> **StephenDavison said:**
> I ran into a similar problem with my first (and so far only) purchase from the music store (Concrete Blonde - Concrete Blonde).  In this case 11 of the 12 tracks downloaded.  I contacted 7digital.com customer support and received the reply quoted below.  Unfortunately, this isn't very helpful because I can't (or at least don't know how) to login to 7digital directly.  I've now followed up asking for more help and will post back here if they are able to help me.

Also, I just realized that purchased music does not sync. into the  ~/Ubuntu One directory; instead, it goes into ~/.ubuntuone.

I do have the same problem and got the same unhelpful reply from 7digital. Though Ubuntu One states, that you can re-download your songs, it nowhere says **how**...

Have you found a solution to your problem yet?

Greg

---

### Post by jcphil on 2010-04-18
I got the same response from 7Digital. They reference the "locker" link in mine too. But I can't log in to that URL with my Ubuntu One credentials. The URL for sending replies seems to be broken too, since the CAPTCHA doesn't appear and you can't send without it. My message to Ubuntu is this: If you are rolling out a service where you expect people to spend money, there ought to be *something* about it that works right. I converted from Kubuntu to try the new Ubuntu One services. It wasn't worth it. I'm back on KDE now. There are reliable services out there that do the same thing as Ubuntu One. I won't trust this piece of crap again.

---

### Post by thebear78 on 2010-04-18
For those of your who are waiting for some of you songs from your purchase to download, please subscribe to this bug for the latest updates.
[https://bugs.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/551755](https://bugs.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/551755) 
We're sorry for the delay and realize this is a serious issue. We made great progress late last week and should have this resolved within a few days.

I'm also working with 7digital on customer service processes which will improve soon. Thanks!

---

### Post by jcphil on 2010-04-19
> **thebear78 said:**
> For those of your who are waiting for some of you songs from your purchase to download, please subscribe to this bug for the latest updates.
[https://bugs.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/551755](https://bugs.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/551755) 
We're sorry for the delay and realize this is a serious issue. We made great progress late last week and should have this resolved within a few days.

I'm also working with 7digital on customer service processes which will improve soon. Thanks!
How is it you guys find it acceptable to take people's money and give them no way to retrieve the files they paid for? I would think the least you could do is inform people of this bug before they make a purchase. But I guess that would be too hard. What you really ought to do is pull the service until you can offer some reliable way for people to get the files they purchased. I won't risk another penny or another file on this service. I'll be deleting my Ubuntu One account as soon as I find some way to get all of the music I paid for.

---

### Post by joshuahoover on 2010-04-19
> **jcphil said:**
> How is it you guys find it acceptable to take people's money and give them no way to retrieve the files they paid for? I would think the least you could do is inform people of this bug before they make a purchase. But I guess that would be too hard. What you really ought to do is pull the service until you can offer some reliable way for people to get the files they purchased. I won't risk another penny or another file on this service. I'll be deleting my Ubuntu One account as soon as I find some way to get all of the music I paid for.

This is a bug that has been affecting some of our users and we've been chasing it down, with multiple people looking into the root cause of the issue. We will be emailing all affected users and providing them with their files. We appreciate everyone's help in testing this new feature and for your patience as we work out some nasty bugs that we intend on having resolved prior to the final release. 

Thank you,

Joshua

---

### Post by StephenDavison on 2010-04-20
Received the following from 7digital last Thursday after letting them know I have no way of accessing a 'locker' to retrieve my purchase.
> Hello,
Apologies for the delay of our reply - it appears that we're still in an early 
stage of this project and aren't able to fix or replace faulty downloads. Have 
you been able to download the track since we last heard from you? If not, the 
only option is to cancel the purchase and issue a refund.

Thanks,
7digital Download Support
My take on this is not to get too excited about these early  glitches and give our friends at Ubuntu every opportunity to make it right.  I'm going to wait for the UbuntuOne devs to make good on the missing song rather than to pursue a refund.

Having used Ubuntu since 8.04, I've gotten a lot of value from it for zero dollars out of pocket.  Not getting perfect service from an unreleased beta product is a minor inconvenience by comparison.

Thank you Ubuntu Devs.

Sincerely,
Stephen Davison

---

### Post by joshuahoover on 2010-04-20
> **StephenDavison said:**
> Received the following from 7digital last Thursday after letting them know I have no way of accessing a 'locker' to retrieve my purchase.

My take on this is not to get too excited about these early  glitches and give our friends at Ubuntu every opportunity to make it right.  I'm going to wait for the UbuntuOne devs to make good on the missing song rather than to pursue a refund.

Having used Ubuntu since 8.04, I've gotten a lot of value from it for zero dollars out of pocket.  Not getting perfect service from an unreleased beta product is a minor inconvenience by comparison.

Thank you Ubuntu Devs.

Sincerely,
Stephen Davison

Thank you Stephen for your support and patience! We GREATLY appreciate it. The last thing we want to do is to abuse the trust you and others have placed in Ubuntu and Ubuntu One. We should have good news to report very soon. We're finishing up some final testing on this issue before we make a more formal announcement and get everyone squared away.

Thank you,

Joshua

---

### Post by StephenDavison on 2010-04-20
I would agree that you are definitely making progress!  Minutes ago I was able to download the missing song (containing a ' in the title) through the U1MS 'My downloads' list and confirmed it to be sync'ed to my local HD. 

Pictures to prove it are in a public album under my profile:
[http://ubuntuforums.org/album.php?albumid=1786](http://ubuntuforums.org/album.php?albumid=1786) 

Now to decide on what that next purchase should be...

---

### Post by mrkennie on 2010-04-26
I've just purchased my first ever digital album, and what's more, I did it using Ubuntu One!

I did encounter a minor issue with not being able to transfer some tracks to Ubuntu One storage but retrying a couple of times after a few minutes seemed to get it work. Also it seems to take a while to transfer to U1 storage but they are slowly appearing one by one in Rythmbox. I'm not sure if the speed is anything to do with the fact that the album is a new release (today) or things are still being tweaked (naturally). Not expecting perfection, especially during the early days.

Other than that, brilliant, I'll be using it again and again. The interface is clear and easy to use! Thank you Ubuntu devs for bringing us yet another fantastic release full of cool goodies like U1M!

---

### Post by joshuahoover on 2010-04-27
> **mrkennie said:**
> I've just purchased my first ever digital album, and what's more, I did it using Ubuntu One!

I did encounter a minor issue with not being able to transfer some tracks to Ubuntu One storage but retrying a couple of times after a few minutes seemed to get it work. Also it seems to take a while to transfer to U1 storage but they are slowly appearing one by one in Rythmbox. I'm not sure if the speed is anything to do with the fact that the album is a new release (today) or things are still being tweaked (naturally). Not expecting perfection, especially during the early days.

Other than that, brilliant, I'll be using it again and again. The interface is clear and easy to use! Thank you Ubuntu devs for bringing us yet another fantastic release full of cool goodies like U1M!

Thank you for the kind words and support! Rest assured, we are doing everything we can to improve the service on a daily basis. The speed issue you experienced was likely a result of some scaling issues we've been experiencing of late but are currently rolling out improvements for. 

Thank you,

Joshua

---

### Post by majikshoe on 2010-05-01
I have similar problems with a copy of "Bedrock 11" I just bought. Bedrock 11 is a compilation CD and has several remixes of the same song by the same artists. This appears to confuse the heck out of Ubuntu Music, which based on my observations below, appears to assume that the track name in an album is unique?

I have the following scenario:

[LIST]
[*]Paid for the album, all went through OK
[*]The "My Downloads" tab currently shows most tracks as *Transferring to your Ubuntu One storage* - even though these actually *are* in my storage, so shouldn't it say "completed" or something?
[*]Some tracks - those that are remixes - are stuck on *0Mb Downloaded*. They have been stuck for 3 hours now.
[*]The files fail to synch with my local directory - I had to download them all manually via the web interface. Looking in ~/.ubuntuone, I can see the directories have been created but there are no files in any of them
[/LIST]

I read elsewhere that to get remixed tracks downloaded, a workaround was to remove it from storage (after downloading it) and re-trying via RhythmBox. Indeed, RhythmBox detected it was deleted (in fact, it told me the original and the remix were both deleted) and informed me I had 4 downloads left, but on clicking the "Download" link, nothing happens. So, I'm short three tracks that are all remixes with no obvious way to download them.

So, through this I have some ideas
[LIST]
[*]I think the idea with the cloud is great but only adds value if you want to use that as a serious storage/distribution mechanism. Why not provide a way to simply download the tracks directly through RhythmBox to the local file system, rather than going through the intermediary cloud service? Or perhaps I can, but it isn't obvious. For me, the cloud adds no value as an intermediary between the music store and my file system. In fact right now, it's seriously in the way.
[*]The files for a compilation are sorted into directories by *artist* which makes zero sense for a compilation CD. The net effect is my top-level "Purchased Music" directory contains over 15 sub-directories with the name of the artist all containing one song, when they actually all belong to a single album, and should be arranged on the file system as such.
[*]The web interface is fairly basic. Would be nice to download a tarred/zipped *directory* or at least multiple files at once.
[/LIST]

Have subscribed to the bug linked earlier, looking forward to seeing a fix where I can get the rest of my songs.

Thanks

---

### Post by elkikin on 2010-05-01
> **majikshoe said:**
> 
[LIST]
[*]The files fail to synch with my local directory - I had to download them all manually via the web interface. Looking in ~/.ubuntuone, I can see the directories have been created but there are no files in any of them
[/LIST]


Same thing happened to me with a single I bought as an experiment: Shitdisco - Reactor Party. After the purchase, the mp3 files appeared in one.ubuntu.com, but the sync with my computer failed. I noticed that the directories exist, but no files were transferred. I managed to download the tracks fine from one.ubuntu.com, though.

So far I've been unable to consistently upload or download files/folder to my PC with the syncdeamon. Most of the time, it just seems to be doing nothing. And when it works, it's ultramega slow.

EDIT: I copied the mp3 to ~/.ubuntuone/Purchased ... /Shitdisco/Reactor Party/ and the syncdeamon eventually recognized the syncing as being done.

---

### Post by deathblossom on 2010-05-01
Hope this gets fixed soon. My Gorillaz album is sitting in Transferring limbo and now the web is down, so I can't get them that way either, even though the bug is listed as Fixed.. It's a great idea I guess, but I think I'll just stick to AmazonMP3.

---

### Post by Curtiss on 2010-05-01
I thought I'd try the store again made a purchase of $3.04 about an hour ago and still shows begin queued LOL. I think the music store is getting worst not better. I purchase some music about week ago and all but four out eighteen did not download got the four the next day but the downloads started fairly quickly.

I really like the music store ideal and want it to work been getting my music at amazon but they don't have the down loader thing for 64 bit ubuntu only 32 bit. The music store is just not ready and this is going to turn alot of people away from using the store. Just my thoughts.

---

### Post by elkikin on 2010-05-01
They are working on it. Let's wait and see. Maybe this week things will get better on the whole server thing. In the meantime, we can always download our purchased music using the web interface (one.ubuntu.com).

Besides, there are updates for ubuntuone packages waiting to be tested in lucid-proposed.

---

### Post by Curtiss on 2010-05-01
Thanks got em on my hard drive now.

---

### Post by joshuahoover on 2010-05-03
Apologies to all who've had problems with Ubuntu One and the music store in particular. Our service has been experiencing large spikes with the release of Lucid and is making certain key parts of the system to not function properly. We're working on fixing these problems. We'll keep you updated in two ways on our progress:

1) [http://identi.ca/ubuntuone](http://identi.ca/ubuntuone)
2) [https://wiki.ubuntu.com/UbuntuOne/Status](https://wiki.ubuntu.com/UbuntuOne/Status)

Again, apologies for the inconvenience and thanks to all of you for your patience as we get things running better.

Thank you,

Joshua

---

### Post by ukblacknight on 2010-05-05
I've just had this problem on Banshee, where it said that it was transferring to my Ubuntu One account.

Luckily I was able to download the track from the web interface, create the relevant directory structure in ~/.ubuntuone/ and copy the file into the folder.

The instant it copied over, it showed as completed in the music store and the file appeared in my "Recently Added" playlist in Banshee.

---

### Post by joshuahoover on 2010-05-05
> **ukblacknight said:**
> I've just had this problem on Banshee, where it said that it was transferring to my Ubuntu One account.

Luckily I was able to download the track from the web interface, create the relevant directory structure in ~/.ubuntuone/ and copy the file into the folder.

The instant it copied over, it showed as completed in the music store and the file appeared in my "Recently Added" playlist in Banshee.

We're going to be running a script very soon that attempts to re-download files that got stuck in the process. We're still chasing down some of the issues that cause these problems but the script should at least get things going again. And we'll continue to run this script until we're able to determine the cause of the issues so that people are able to get their purchases. We appreciate everyone's patience as we work out some of these issues. We want this service to run as smooth as possible for all of you.

Thanks,

Joshua

---

### Post by Kacey on 2010-05-06
Any update on this? I would download them via the website but I just got a bunch of whole albums and it would take a very long time to do it that way.

---

### Post by joshuahoover on 2010-05-07
> **Kacey said:**
> Any update on this? I would download them via the website but I just got a bunch of whole albums and it would take a very long time to do it that way.

There are two problems. The first is some songs not getting to the cloud storage. You're not experiencing this one, which is a good thing. :) You're experiencing the second problem where the files aren't making it to your computer. Can you try running the following commands from a terminal session?

u1sdtool -d; u1sdtool -q; u1sdtool -c

Wait about a minute and then run these commands and let me know what it outputs?

u1sdtool -s; u1sdtool --current-transfers

Thank you,

Joshua

---

### Post by Kacey on 2010-05-07
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

Current uploads: 0
Current downloads: 0

---

### Post by joshuahoover on 2010-05-11
> **Kacey said:**
> State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

Current uploads: 0
Current downloads: 0

Hi Kacey,

Apologies for the delay in following up on this. I was out sick the past few days.

I think you may be affected by the following bug that I'm working on helping us get a fix released ASAP: [http://launchpad.net/bugs/571548](http://launchpad.net/bugs/571548) 

To work around this issue, you can try creating a folder for each artist whose album you purchased. So you would do the following:


[LIST=1]
[*]Open Places->Home
[*]In your home folder, press *Ctrl-h* to show hidden folders
[*]Double-click on the "Purchased from Ubuntu One" folder
[*]Right-click and select "Create Folder" and give the folder the name of an artist whose music you purchased from the store
[*]Open Applicaitons->Accessories->Terminal and run:
```
u1sdtool -d; u1sdtool -c
```
[/LIST]
That should get your music downloading until we release the fix. Please let me know if that doesn't work for you.

Thank you,

Joshua

---

