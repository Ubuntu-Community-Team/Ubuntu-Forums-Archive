---
title: "Very slow upload"
date: 2010-04-25
forum: Ubuntu One (CLOSED)
---

### Post by adamantis on 2010-04-25
I have been trying out Ubuntu One for the past couple of days but find it to be incredibly slow. At first i had put a folder will a large amount of images in the ubuntu one folder. The total size of it was 35Mb, after over 26 hours only 11,5Mb of that had been uploaded.

After looking around some on these forums i saw several comments about it being slow when it is a large amount of files, no matter if the filesize is small or large. I decided to try it out with a larger single file. I erased everything that was in the previous share and then put my testfile of 350Mb in the Ubuntu One folder. 

After two hours of waiting i could still not see it on the U1 website so i decided to see how long it would take with dropbox and put a copy of that file in my dropbox folder as well. The file was uploaded correctly to dropbox in just a couple of minutes but it has still not been uploaded to the U1 website even though it has been 4-5 hours since i first put it in my U1 folder.

---

### Post by Curtiss on 2010-04-25
I have also found that uploads are slow also. I'm also a dropbox user and it works flawlessly in Lucid Lynx 10.04 RC 64 bit. I think in time ubuntu one will only get better.

Curtiss

---

### Post by adamantis on 2010-04-25
I hope so, if Ubuntu One worked a bit faster and more "instant" i wouldn't have any problems to use it instead of Dropbox.

My single "testfile" of 350Mb has still not been uploaded even after more then 6 hours.

---

### Post by andyrogers2008 on 2010-04-25
I too agree that the overfull upload performance of UbuntuOne is really bad, and will put people off until it is sorted.

I have been trying to get approx 6500 files up onto my space for the past 3 weeks and so far have got just over 1000 left.

I keep having the problem of a long server rescan and takes over an hour to rescan then may upload a couple of files and then drops its connection and restarts a server rescan again.

---

### Post by Tig3rzhark on 2010-04-26
> **adamantis said:**
> I hope so, if Ubuntu One worked a bit faster and more "instant" i wouldn't have any problems to use it instead of Dropbox.

My single "testfile" of 350Mb has still not been uploaded even after more then 6 hours.
I've tried uploading files smaller than that, and so far it hasn't sped up yet.  The service seriously needs to raise its upload speed if I''m going to consider upgrading to more space.

---

### Post by duanedesign on 2010-04-27
The Ubuntu One team are currently deploying new servers to spread the load and scale better in preparation for the upcoming Lucid release. Unfortunately the increase in Ubuntu One users happened earlier than expected & as such things are currently not working as well as they should be. Things should improve in the next few days.

---

### Post by joshuahoover on 2010-04-27
> **duanedesign said:**
> The Ubuntu One team are currently deploying new servers to spread the load and scale better in preparation for the upcoming Lucid release. Unfortunately the increase in Ubuntu One users happened earlier than expected & as such things are currently not working as well as they should be. Things should improve in the next few days.

As always, Duane is on top of things. :) Thank you Duane! 

And to back up what is already said... Yes, we're (painfully) aware of the performance problems and we are addressing them as I type this message. This work is all on the server side and has been in the making for a while now. In other words, it's not a simple fix. Hopefully you all will see speed improvements shortly.

Thank you,

Joshua

---

### Post by Tig3rzhark on 2010-04-27
> **joshuahoover said:**
> As always, Duane is on top of things. :) Thank you Duane! 

And to back up what is already said... Yes, we're (painfully) aware of the performance problems and we are addressing them as I type this message. This work is all on the server side and has been in the making for a while now. In other words, it's not a simple fix. Hopefully you all will see speed improvements shortly.

Thank you,

Joshua

So what you're saying is, that there are more users than the servers can handle.  Which means you would have to increase the amount of servers in order to handle the load, right?

---

### Post by joshuahoover on 2010-04-29
> **Tig3rzhark said:**
> So what you're saying is, that there are more users than the servers can handle.  Which means you would have to increase the amount of servers in order to handle the load, right?

Pretty much. If only it were that simple to do. :-) We made the bulk of the major changes yesterday and saw great gains in performance immediately. Now we're working out some kinks that come with splitting out the main Postgres database out into multiple instances ("shards"). There are still performance issues with syncing lots of files (hundreds). We're tackling this one next. It's going to require changes on the client and server.

Thank you,

Joshua

---

### Post by elkikin on 2010-04-29
Hope you guys sort this out soon. I'm dying to try the new Music Store and everything, but when I can't even sync with U1 120 MB of files in like 3 or 4 hours (it seems to be stuck at 31.5 MB), then I guess I should wait a little bit longer...

I can understand that this is a massive undertaking for Canonical, and I appreciate everything that's being done, though.

---

### Post by cannonfodder on 2010-04-29
Have been trying Ubuntu One on three different machines since yesterday.

Its been hit and miss, which, I guess, is to be expected since the service is just in the beta stage.

At this point though, Ubuntu One is a GREAT idea whose implementation leaves a lot to be desired.

My experience with Ubuntu One includes one instance on Lucid (alt install of gnome-core, NOT gnome-desktop-environment) and two on Karmic (default Gnome live CD install).

I'm pretty sure the version on Lucid is the default from the repos, as opposed to the ppa. It is the most feature complete and polished. 

The version available through Karmic repos, on the other hand, simply did not work for me. I resorted to the Ubuntu One beta ppa.

This worked on one of the machines. The other simply will not connect.

Both working instances of Ubuntu One are slower than molasses in winter.

If the developers are listening, I would pay money for this service but synch is a complete deal-breaker and the interface is too simple.

And as long as I'm complaining, focusing too heavily on GNOME Desktop Environment and Nautilus integration is a waste of resources. 

They are both examples of the kind of bloat I thought I was leaving behind with Windows.

Concentrating on developing a Desktop Environment/File Manager-agnostic version of the client that will work well no matter what the configuration (KDE, XFCE, LXDE, etc.) would be of greater benefit to community.

</rant>

---

### Post by joshuahoover on 2010-04-30
> **cannonfodder said:**
> Have been trying Ubuntu One on three different machines since yesterday.

Its been hit and miss, which, I guess, is to be expected since the service is just in the beta stage.

At this point though, Ubuntu One is a GREAT idea whose implementation leaves a lot to be desired.

My experience with Ubuntu One includes one instance on Lucid (alt install of gnome-core, NOT gnome-desktop-environment) and two on Karmic (default Gnome live CD install).

I'm pretty sure the version on Lucid is the default from the repos, as opposed to the ppa. It is the most feature complete and polished. 

The version available through Karmic repos, on the other hand, simply did not work for me. I resorted to the Ubuntu One beta ppa.

This worked on one of the machines. The other simply will not connect.

Both working instances of Ubuntu One are slower than molasses in winter.

Yes, right now, syncing is likely to be slow as we are getting a ton of new users and trying to scale things properly to keep up with the demand. My apologies for the poor performance. We are working on fixing this. 

As for the other problems you've alluded to, I'd like to help troubleshoot this with you either via a bug report with log files or in real time on #ubuntuone on Freenode IRC. I'm joshuahoover there and normally on 13:00-21:00, Monday-Friday.

> 
If the developers are listening, I would pay money for this service but synch is a complete deal-breaker and the interface is too simple.

And as long as I'm complaining, focusing too heavily on GNOME Desktop Environment and Nautilus integration is a waste of resources. 

They are both examples of the kind of bloat I thought I was leaving behind with Windows.

Concentrating on developing a Desktop Environment/File Manager-agnostic version of the client that will work well no matter what the configuration (KDE, XFCE, LXDE, etc.) would be of greater benefit to community.

</rant>

There are trade offs with making things agnostic, but we try to make all the Ubuntu One desktop software as agnostic to the desktop environment as possible. We'll continue to do better here as we (and others with us) start to port to other platforms. 

Thank you,

Joshua

---

### Post by michiel33 on 2010-05-04
Still extremely slow syncing, to the point where you wonder if it syncs at all. Hope this is sorted out soon or I will have to revert back to DropBox :-).

Thanks for all the effort though.
Michiel 

> **joshuahoover said:**
> Pretty much. If only it were that simple to do. :-) We made the bulk of the major changes yesterday and saw great gains in performance immediately. Now we're working out some kinks that come with splitting out the main Postgres database out into multiple instances ("shards"). There are still performance issues with syncing lots of files (hundreds). We're tackling this one next. It's going to require changes on the client and server.

Thank you,

Joshua

---

### Post by michiel33 on 2010-05-04
Actually going a lot better now! :)

Thanks!

Michiel

> **joshuahoover said:**
> Pretty much. If only it were that simple to do. :-) We made the bulk of the major changes yesterday and saw great gains in performance immediately. Now we're working out some kinks that come with splitting out the main Postgres database out into multiple instances ("shards"). There are still performance issues with syncing lots of files (hundreds). We're tackling this one next. It's going to require changes on the client and server.

Thank you,

Joshua

---

### Post by duanedesign on 2010-05-04
Yep, I just dropped a 500k file in my Ubuntu One folder and it synced in less than 5 seconds. \o/

---

### Post by joshuahoover on 2010-05-04
> **michiel33 said:**
> Actually going a lot better now! :)

Thanks!

Michiel

Great to hear Michie! The team has been working super duper overtime to get things back to acceptable. We want the service to rock for you and all the other Ubuntu One users out there. We're still fixing and improving things but we are seeing that syncing is going much faster as of late.

Thank you,

Joshua

---

### Post by jatoo on 2010-05-04
Working much better for me too.

Thanks Joshua, giving a good explanation about what's happening and letting us know it's being fixed really eases the frustration with this sort of thing. 

Ubuntu One seems pretty cool now it's working!

---

### Post by joshuahoover on 2010-05-11
> **Chauncellor said:**
> I myself have been sitting here, trying to sync four 3 kB files..... 

It's been going at a whopping one file per four minutes! ;)

Yikes! That's no good. We're currently in the process of deploying some changes on the server side that are going to initially have a negative impact on performance (as a lot of clients will be attemtping to rescan the servers). These changes will allow us to more easily tweak various parameters on the server side that will help us get things performing better without having to wait for full rollouts. Bottom line: We're trying to get to a point where we can get the service working much, much faster for everyone.

Thank you,

Joshua

---

### Post by nikkkko on 2010-05-13
A few days ago synching 900mb took three attempts and 24hrs, but it worked and small changes were quickly updated. I love Ubuntu so didn't hesitate to get out my card for the 50gig upgrade.  

However, another 24hrs later and all I've managed to upload is an extra 8 empty directories.  The service is *chronically* slow with *zero* feedback and the only reason I haven't cancelled is because I'm a long time Ubuntu user who has had this fantastic software for free for all these years,

---

### Post by joshuahoover on 2010-05-13
> **nikkkko said:**
> A few days ago synching 900mb took three attempts and 24hrs, but it worked and small changes were quickly updated. I love Ubuntu so didn't hesitate to get out my card for the 50gig upgrade.  

However, another 24hrs later and all I've managed to upload is an extra 8 empty directories.  The service is *chronically* slow with *zero* feedback and the only reason I haven't cancelled is because I'm a long time Ubuntu user who has had this fantastic software for free for all these years,

I'm sorry to hear Ubuntu One isn't working properly for you. Can you let me know about how many files and folders you are attempting to sync in total and the total size? There is a known issue with performance of syncing a lot of files at one time (100's) that we have as a top priority to fix this release cycle (Maverick). If you run the following commands, can you report the output?

u1sdtool -s
u1sdtool --current-transfers

Thank you,

Joshua

---

### Post by nikkkko on 2010-05-14
> There is a known issue with performance of syncing a lot of files at one time (100's) that we have as a top priority to fix this release cycle (Maverick).

I'm surprised because with a 50gb drive to play with isn't it inevitable that many people are going to breach that limit?  Also, are you implying that this problem will not be fixed for another 6 months?  Even if I were prepared to wait that long I have no intention of upgrading to Maverick, which has no long term support as far as I am aware.

I'm trying to back up a work directory at the moment, 9gb in total and around 5,700 files and it's been running for three days. As of this morning I have 2.6gb transferred.

Here's the output :

```
nick@dell-laptop:~$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: WORKING_ON_CONTENT

nick@dell-laptop:~$ u1sdtool --current-transfers
Current uploads:
  path: /home/nick/Kazuba/images/enviro photos/0702_SA_Trip/SANY0060.JPG
    deflated size: 1519366
    bytes written: 978540
  path: /home/nick/Kazuba/ventes/Hering/Order
    deflated size: 748
    bytes written: 0
  path: /home/nick/Kazuba/Mktg/Salons/Ecorismo 2007/SANY0277.JPG
    deflated size: 1624240
    bytes written: 1624240
  path: /home/nick/Kazuba/Mktg/Salons/Ecorismo 2007/SANY0282.JPG
    deflated size: 1519595
    bytes written: 0
Current downloads: 0

```

---

### Post by nikkkko on 2010-05-14
All this morning my internet connection has been crawling so thought maybe that might be why U1 is taking so long to sync.  So I disconnected U1 from the U1 prefs window and my connection went back to normal.  Which means that not only is U1 taking forever to snyc, but it's also crushing my connection.

---

### Post by joshuahoover on 2010-05-14
> **nikkkko said:**
> All this morning my internet connection has been crawling so thought maybe that might be why U1 is taking so long to sync.  So I disconnected U1 from the U1 prefs window and my connection went back to normal.  Which means that not only is U1 taking forever to snyc, but it's also crushing my connection.

Do you have the bandwidth throttling turned on in the Ubuntu One Preferences under the "Devices" tab? If not, you might want to try that and then click the "Disconnect/Connect" button.

As for when we'll fix this problem. It's a mix of server and client changes. We'll be working on it for Maverick and will release the code in our beta PPA. Right now, I'm guessing the changes to the client may be too drastic to get into a 10.04 LTS update but I'll discuss this with the developers working on it to confirm one way or the other. I really want to see these changes make their way into 10.04 LTS, so we'll see what we can do. The alternative will be to install our beta PPA, but that is definitely a less than ideal solution.

Thank you,

Joshua

---

### Post by nikkkko on 2010-05-15
> Right now, I'm guessing the changes to the client may be too drastic to get into a 10.04 LTS update

Does this mean that the problem with uploading large numbers of files will never be fixed for 10.04 users?

---

### Post by duanedesign on 2010-05-15
I think that is yet to be determined. Of course server side changes we all benefit from. Changes to the client would have to so through the [SRU process]("https://wiki.ubuntu.com/SecurityTeam/SponsorsQueue").

---

### Post by nikkkko on 2010-05-15
I am a big fan of Ubuntu.  I support open standards, have convinced most of my fellow workers to adopt Ubuntu and am prepared to give up my time to make it work when it doesn't.  But Ubuntu One is different.  It is a paid for service and the relationship is that of a contract whereby I pay a sum of money and in return receive the service advertised. I am currently paying for a service, which by anyone's standard does not work properly, and which may never work with 10.04 LTS. 

The difference between the money I pay and the service I receive is being make up for with goodwill, which will eventually run out.

---

### Post by sallymc on 2010-05-17
I read audio books for Librivox.org and have been uploading them happily until about a month ago.  Now they just sit in the upload box and don't move.  My server can find no problem on their side and I am nearly tearing my hair out!  
Do you think the problem could be with Ubuntu?  I upgraded to 10.04 recently, but I also experienced the problem  with Karmic.
I love Ubuntu and always manage to sort my problems out, so here's holding thumbs for this one.
Huge thanks in anaticipation.
Sallymc

---

### Post by joshuahoover on 2010-05-17
> **nikkkko said:**
> I am a big fan of Ubuntu.  I support open standards, have convinced most of my fellow workers to adopt Ubuntu and am prepared to give up my time to make it work when it doesn't.  But Ubuntu One is different.  It is a paid for service and the relationship is that of a contract whereby I pay a sum of money and in return receive the service advertised. I am currently paying for a service, which by anyone's standard does not work properly, and which may never work with 10.04 LTS. 

We will make sure fixes get to 10.04 LTS users one way or the other. We can't add anything that is considered new functionality. While the code we write won't be new functionality it will likely change quite a few things at the core to improve performance on the client side. We'll need to prove that any risk with these changes, even though they may be drastic in terms of the lines of code that are affected, are mitigated properly and the pros far outweigh the cons to get them in as an Ubuntu 10.04 LTS stable release update. I think we can do that and that will be the goal. If we aren't able to do that, we can provide 10.04 LTS users with a PPA that will provide our latest fixes. Either way, we'll get these fixes out to 10.04 LTS users. 

Thank you,

Joshua

---

### Post by nikkkko on 2010-05-18
> Either way, we'll get these fixes out to 10.04 LTS users.


That's reassuring to hear, so thanks. It would be nice to know when of course...  but I know you can't answer that with any certainty.

---

### Post by Andy Q on 2010-09-12
> **joshuahoover said:**
> We'll need to prove that any risk with these changes, even though they may be drastic in terms of the lines of code that are affected, are mitigated properly and the pros far outweigh the cons to get them in as an Ubuntu 10.04 LTS stable release update. I think we can do that and that will be the goal. If we aren't able to do that, we can provide 10.04 LTS users with a PPA that will provide our latest fixes. Either way, we'll get these fixes out to 10.04 LTS users. 


Any progress on this bug? I am still getting the same symptoms (some files getting stuck, others uploading at max 10KiB/s)

Andy

---

### Post by nikkkko on 2010-09-13
I ended up giving my money to Dropbox.  It works really well, you can do selective sync with the new client and it is cross platform.

---

### Post by razer.anthom on 2010-11-19
OMG.... I am feeling very fool... I just payed for 20Gb at Ubuntu One and having this problem... I think my files will never finish to upload.

---

### Post by wangxue on 2010-11-23
u1 needs your confidence

---

### Post by mitchroberts on 2010-11-24
I have had slow uploads from ubuntu one but it's a lot better then apples mobile-me dropbox is no better it also has slow uploads sometimes.

---

### Post by jbrown1028 on 2011-10-09
I probably should have searched before I bought as well... I purchased 100 Gig because I am transferring 80 Gig worth of custom programming for everyone in my group to use. There is approximately 135,000 files mixed between Images, HTML, PHP, JS, and text files including docx, xlm, and other text based files.

Now that it has been 2 years since this probably began (according to the posts), I am a little concerned if this is going to be fixed. I don't mind paying for the service, although it has been 48 hours so far and we are still at about 100 files uploaded on a 30 Meg Fiber connection.

The Android version is constantly failing on uploads, the Windows version is constantly crashing, or just displaying the "Getting Information" popup, or displaying the "Starting to Sync Files" message.

After a couple of years I thought this would have had many milestones passed, and I could have fully be sure that the Ubuntu Team would have not pushed it as such.

Another complaint is, why no progress bar, that would at least know something is happening, even if it is 10 years to upload 5 files.

The only other complaint I have is why are you forcing ONLY the Documents folder for paid people.

Dropbox may be on my list - I hate to be the party pooper here, but answers to when this would be resolved would be great.

---

