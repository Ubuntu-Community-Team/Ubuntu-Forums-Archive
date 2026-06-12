---
title: "Purchased Music (temporary) problem"
date: 2010-05-07
forum: Ubuntu One (CLOSED)
---

### Post by bturnbough on 2010-05-07
I've been charged for music and I'm getting the following message (without the music downloading):

"There was a (temporary) problem getting your list of purchased songs.  Please wait a short time and try again, or return to the music store."

How do I go about correcting this issue?

I've downloaded a couple of albums and each one I've experienced different issues.  I'm starting to become disappointed with the U1 Music store / U1 service.  I know that Canonical is working to resolve the issues, but when will this service become reliable?  IMHO this should have been tested better if this is going to be a vital revenue source for canonical.

---

### Post by duanedesign on 2010-05-07
There are two problems. The first is some songs not getting to the cloud storage. The second problem where the files aren't making it to your computer.

Are the songs in Ubuntu One in the cloud? You can test this by looking at the web interface at htp://one.ubuntu.com/files, under User Defined Folders > Purchased Music

For people not getting there songs in their cloud storage there is a bug you can subscribe and comment on.

> [https://bugs.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/551755](https://bugs.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/551755)

All purchases are recorded and they will work with you to get you your tunes. They have also been regularly running a script to unjam stuck songs.


If the songs show up in the cloud and not locally can you try running the following commands from a terminal session?

```
u1sdtool -d; u1sdtool -q; u1sdtool -c
```

Wait a couple minutes and then run these commands and let me know what it outputs?

```
u1sdtool -s; u1sdtool --current-transfers
```

---

### Post by bturnbough on 2010-05-08
The songs are not in the U1 cloud.  After several hours of waiting, the link for "My Downloads" in rhythmbox for the U1 store still produces the "there was a (temporary problem)...etc....

---

### Post by bturnbough on 2010-05-09
Thread bump.

Canonical / 7 Digital.... Can you PLEASE correct my purchase issues described above?

---

### Post by alecu on 2010-05-10
> **bturnbough said:**
> I've been charged for music and I'm getting the following message (without the music downloading):

"There was a (temporary) problem getting your list of purchased songs.  Please wait a short time and try again, or return to the music store."

How do I go about correcting this issue?

I've downloaded a couple of albums and each one I've experienced different issues.  I'm starting to become disappointed with the U1 Music store / U1 service.  I know that Canonical is working to resolve the issues, but when will this service become reliable?  IMHO this should have been tested better if this is going to be a vital revenue source for canonical.

Hi bturnbough,

can you please tell me the song details (artist, album or song name) of the tracks you are having problems with? I'll look in the download server logs to try to find out what is the problem you are experiencing.

thank you,
-- 
alecu

---

### Post by bturnbough on 2010-05-10
I'm having issues downloading (the entire album... I haven't been able to download any tracks for either of these albums):

"James Brown & The Famous Flames / The James Brown Band - James Brown Live At The Apollo, 1962".
Order Number     : 3184466

"Frank Sinatra - 40 Enduring Classics"
Order Number     : 3192615

---

### Post by bturnbough on 2010-05-12
Thread Bump.  

Duane & Joshua --- Just checking in to see where we are with this.  Please advise.

Thanks,

Brad

---

### Post by joshuahoover on 2010-05-13
> **bturnbough said:**
> Thread Bump.  

Duane & Joshua --- Just checking in to see where we are with this.  Please advise.

Thanks,

Brad

Hi Brad,

We haven't forgotten about you. We're tracking down some issues that are related to this bug, which is related to the problem you're reporting: [https://launchpad.net/bugs/576472](https://launchpad.net/bugs/576472) Alejandro (alecu) is actively working on this. He's likely tired of me pinging him several times a day about it. ;) It's proving to be a trickier problem to diagnose than we would've thought, partially because we have a fair number of the team at UDS this week. I'll try to get an update on that bug tomorrow. 

Thank you,

Joshua

---

### Post by bturnbough on 2010-05-17
Hi Guys --

Just checking in to see how this issue is progressing.  Can you please grant me access to view the issue in launchpad?  It says I don't have permission to view the issue.

---

### Post by joshuahoover on 2010-05-18
> **bturnbough said:**
> Hi Guys --

Just checking in to see how this issue is progressing.  Can you please grant me access to view the issue in launchpad?  It says I don't have permission to view the issue.

My apologies. I made the bug public. I didn't realize it was set to private. The devs are back from UDS and working on solving this problem. I've been told we may have a fix ready for late tomorrow. In the mean time, I'm seeing what we can do for you and any others affected by this problem (in addition to getting you the music you paid for). Again, thank you for your patience.

Joshua

---

### Post by bturnbough on 2010-05-20
Howdy.... Just letting you know that I am now getting the following error message when clicking on the "My Downloads" link:

 504 Gateway Time-Out
The server didn't respond in time.




All other music store links work fine, however....


Brad

---

### Post by bturnbough on 2010-05-24
Guys,

What is the status of this?  It's going on TWO WEEKS NOW!

I paid for my music, and I want what I paid for!

I'm very dissatisfied with this service and will not be using it again until after Maverick.  It's quite obvious that this service is BETA.... I think Canonical needs to make it more apparent to the end user that this is the case.  

I refuse to be charged for something that I won't receive.

---

### Post by duanedesign on 2010-05-24
bturnbough,

If you can please  come by #ubuntuone between 13:00 and 21:00 GMT and you can get this sorted out in no time. The Ubuntu One team will make sure you get your music. Ping rye or joshuahoover or alecu . They will get you fixed up in no time

---

### Post by joshuahoover on 2010-05-25
> **bturnbough said:**
> Guys,

What is the status of this?  It's going on TWO WEEKS NOW!

I paid for my music, and I want what I paid for!

I'm very dissatisfied with this service and will not be using it again until after Maverick.  It's quite obvious that this service is BETA.... I think Canonical needs to make it more apparent to the end user that this is the case.  

I refuse to be charged for something that I won't receive.

Hi Brad,

Are you getting this error after quitting and then opening Rhythmbox? We are still chasing down the bug that is causing you to not get your music. We are tracking things here: [https://bugs.edge.launchpad.net/ubuntuone-servers/+bug/576472](https://bugs.edge.launchpad.net/ubuntuone-servers/+bug/576472) 

You should be receiving credit on the store for the headaches these problems have caused you. This is in addition to getting you the music you purchased previously. Please feel free to ping me on #ubuntuone on Freenode IRC (I'm normally on Monday-Friday, 13:00-21:00 UTC) or email me directly via the forum here. I'm personally chasing this one down so please don't hesitate to contact me at any time.

Thank you,

Joshua

---

### Post by bturnbough on 2010-05-25
Joshua,

I have completely closed an reopened Rhythmbox about 10 times and have even rebooted a couple of times in hopes that this issue would be resolved.  

Brad

---

### Post by joshuahoover on 2010-05-27
> **bturnbough said:**
> Joshua,

I have completely closed an reopened Rhythmbox about 10 times and have even rebooted a couple of times in hopes that this issue would be resolved.  

Brad

Hi Brad,

I'm having a developer look into this further on both the 504 error and the original problem of not receiving your music purchases. I emailed you personally so feel free to email me directly if you have any questions/concerns. I'm going to be off tomorrow (Friday) but will do my best to check in over the weekend to see if we make progress on this.

Thanks,

Joshua

---

### Post by bturnbough on 2010-06-03
I would like everyone to know that my problem is still unresolved after four weeks.  I have yet to hear any updates on any progress from a dev or a PM.  I'd HIGHLY advise EVERYONE to steer clear of this poorly written service.  Go to dropbox instead.

---

### Post by *g!t5^_)*(H on 2010-06-05
I purchased one album two days ago and songs are not in my Ubuntu One local folder:

> xxx@xxx-laptop:~$ u1sdtool -d; u1sdtool -q; u1sdtool -c
ubuntuone-syncdaemon stopped.
xxx@xxx-laptop:~$ u1sdtool -s; u1sdtool --current-transfers
State: SERVER_RESCAN
    connection: With User With Network
    description: doing server rescan
    is_connected: True
    is_error: False
    is_online: False
    queues: WORKING_ON_METADATA

Current uploads: 0
Current downloads: 0
xxx@xxx-laptop:~$

This is a pitty, because I would like to buy music quite often in order to 'somehow' pay the exellent job of Ubuntu workers.

There is also another problem, special characters such like "à","ú" or "ó" are not displayed when I download the song from the web space of Ubuntu One.

I can't recommend this service until it perfectly works for everyone.

---

### Post by tk03759 on 2010-06-19
This is occuring for me as well. I get the "There was a (temporary) problem getting your list of purchased songs. Please wait a short time and then try again, or return to the music store." each time I try to click "My Downloads" and I am waiting for a song to come through that I just purchased.

Funny thing is, this song was given to me as a reimbursement for a song I had downloaded before it that had imperfections in it. :/

---

### Post by element23 on 2010-07-12
I have this same issue too! I receive "There was a (temporary) problem getting your list of purchased songs. Please wait a short time and then try again, or return to the music store." This shows up on all 3 of my systems in the Ubuntu One Music store extension on both Banshee and RB. Please Help

---

### Post by thebear78 on 2010-07-12
> **tk03759 said:**
> This is occuring for me as well. I get the "There was a (temporary) problem getting your list of purchased songs. Please wait a short time and then try again, or return to the music store." each time I try to click "My Downloads" and I am waiting for a song to come through that I just purchased.

Funny thing is, this song was given to me as a reimbursement for a song I had downloaded before it that had imperfections in it. :/

When you purchase songs in the Ubuntu One Music Store, they are first transferred from 7digital, our music provider, to your personal cloud at [https://one.ubuntu.com/files/](https://one.ubuntu.com/files/) . Then they are downloaded to all of your computers that you have setup for synchronization. The My Downloads page tracks this progress and shows different status messages.

Are your songs available at [https://one.ubuntu.com/files/](https://one.ubuntu.com/files/) ?
If not, this means there was a download error from 7digital. We've mostly resolved these issues so this is unlikely.

If they are in the cloud, can you see the songs in the ~/.ubuntuone folder on your computer?
If not, it is because you probably have a general file synchronization problem. You can test this by adding a new text file to your ~/Ubuntu One/ folder and checking the website to see if it has successfully synchronized to the cloud.

If you can see the files in the .ubuntuone folder, some users have reported problems with songs being added to the Rhythmbox and Banshee libraries. 
Rhythmbox bug: [https://bugs.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/604767](https://bugs.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/604767)
Banshee bug: [https://bugs.launchpad.net/ubuntu/+source/banshee-community-extensions/+bug/604699](https://bugs.launchpad.net/ubuntu/+source/banshee-community-extensions/+bug/604699)

Subscribe to these bugs to track their progress.

---

### Post by element23 on 2010-07-12
Ok I may have found a rough fix to retrieve purchased music in Banshee. In banshee go to Media > Import Media > Local Folders Choose > "your user name" >.local> shared > ubuntu one. Highlight that folder and click "Import" Make sure that you have enabled view hidden files. This worked for me hope it helps. The "My Downloads" section in the Music store is still busted though and needs fixing.

---

### Post by element23 on 2010-07-29
Ok folks it was been weeks since my original post and the Ubuntu One extensions on both banshee and rhythm box are still not working when i click the "my downloads" section AND no one has even replied to me to help fix this. I am sad to say that i will have to move my business over to Amazon. I can't use the Ubuntu One Music store until i am confident that I will receive the songs i purchase in a speedy and convient manner. I will be happy to return when Ubuntu Music store is fixed.

---

### Post by tk03759 on 2010-07-29
I have since moved to amazon.com as well. Ubuntu One's music store software/server issues in combination with with 7 digital's slim selection and corrupted music files makes the whole service more of a headache than it's worth.

I am also still experiencing the issue you had when accessing my downloads several weeks after the problem was supposed to be fixed.

---

