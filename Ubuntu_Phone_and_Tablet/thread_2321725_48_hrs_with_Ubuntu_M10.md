---
title: "48 hrs with Ubuntu M10"
date: 2016-04-24
forum: Ubuntu Phone and Tablet
---

### Post by NiksaVel on 2016-04-24
Hey all,

here are my experiences with the new Ubuntu tablet...  let me just say that I am not an IT or Linux pro...  I am a Linux enthusiast, using it regularly since 2004...  usually switching between ubuntu and mint...

What I need from a tablet is not much, I use it mostly for reading, while I do all my messaging and social stuff on my phone. 

I need the following:
[LIST=1]
[*]Working screen orientation
One thing that REALLY annoy me is the screen orientation...  I felt most of the time as if the tablet was trying to make me hate it by reorienting the screen of every app differently. I felt like I was rotating it for a full 360 every couple of minutes as I was using different apps. Why THE HECK don't scopes work in any other orientation than horizontal upside down? Unless I shake it like crazy, than it is horizontal normal?? The vertical orientation, which I believe is what most people hold their tablets like when reading (at least I do) is a no go for scopes.


[*]Web browsing
The built in browser works okay. It crashed a few times with no explanation but it works okay and "fluid enough" for regular surfing. Firefox has no keyboard ...   and is a regular desktop firefox unoptimized for the small screen and touch interface. I REALLY REALLY miss Chrome, since I've lately switched from desktop Firefox to Chrome (stability, speed) and it has all my history, bookmarks, passwords etc...   If there is some third party app like X-marks that can help here, please let me know about it.


[*]reading offline content with Pocket app
The Pocket web app is perfectly okay if you are in range of wifi signal...  but it loses the basic functionality of pocket that is offline reading. Also, there is no simple "share to pocket" with just a web app. The replacement app PockIt seems promising - BUT it wouldn't let me login with my google auth (the actual confirmation opens in a new tab that never appears), and it seemed to have some glitches - some of my articles were synced just the subject and the text showed "null". It gives the option of offline reading and "share to pockit" though.


[*]reading offline various ebook formats
So far the Document viewer app works okay, and it really should be installed by default.


[*]organization with Trello and Google Cal (or compatible) app.
Trello web app works okay, but it is missing one key feature - long press on a task and dragging it to another board or archive bin. With long press you get a context menu!? Neither web, android, ios or chrome app behave like that. Even using a moust to drag in "desktop mode" works okay. Not a deal breaker but really annoying. Google calendar web app works okay, as expected.


[*]File management with SMB, access to USB sticks and/or SD cards
File manager should really be installed by default.
Why THE HECK do I need to press Full access to be able to access my USB stick? And why doesn't the keyboard appear when I need to enter that password? Okay... closed file manager, reopened it full access again, and there keyboard is here now. So accessed the USB stick, clicked on the 720p video file, told it to open with media player, 5 min later the stick led light still blinking, tablet didn't do anything, and went to sleep mode. Tried "software eject" with file manager or the external device 
Tried copying the file over to the internal memory I see the media player app starting and just staring at a black screen. So the movie playback is a no go... hrmmm.
No matter how I tried to remove the device, it could never be removed because "it was busy"...  I just yanked it out in the end (I know the manual stated that it should be removed by first powering down the tablet....   REALLY?!??  In 2016??) Didn't have any spare SD cards to test, but I assume behaviour is similar.

SMB works... I can list all the files and folders on my LAN, (of course first submenu and allow full access!?). Most larger video files (.mkv) will not open via LAN... nothing happens (is it trying to copy the large file locally?) I can open images. Text files are inaccessible because there is no app to open them. I installed edIt from the store....  but it only works for .txt extension and there is no "open with" option...

All in all, the file manager is deceptively friendly with familiar interface and icons, but lack of thumbnails and icons makes you feel on hostile territory pretty soon - i.e. there is no simple way to easily see if you can open a file with a certain extension or is it missing any app to open with - all the icons are the same.


[*]access to cloud filesharing services (MEGA, Google Drive, Dropbox, Box, Onedrive).
This is a horror show - yes you get web apps for some of them...  Personally I use MEGA since it is the only one with Linux native client. The web access has no "preview" but offers to download the file locally, and than fails with "NetworkError: 301 - Protocol "filesystem" is unknown". The line of text above is filesystem:[http://mega.nz](http://mega.nz).....  so I guess there's the problem. Works fine on android. I would of course give you a copy/paste - but how??  It doesn't work in the built in browser window. I took a screenshot with both volume buttons depressed, heard the screenshot sound. Can't find the screenshot image....   :/  It's not in the Pictures/screenshots folder.


[*]watching videos from my home LAN (plex media server)
From file manager it is simply not working. As far as I see there is no plex or kodi app that I might setup for video streaming.
Accessing Plex web view locally gives normal access for listing, but playback doesn't work. With stock browser I get rotating loading indicator but no playback, with Liri browser pressing play doesn't do anything. Tried it with Firefox and I get "Streaming this media is unsupported".


[*]teamviewer and/or NoMachine NX protocol
Nothing here to work with...


[*]VPN access to work
I see only OpenVPN protocol and I need MPPE ....   anyone knows what to do here?


[*]good battery
Not sure yet...  been toying a lot with it for testing, but with couple of hours of testing installing and removing stuff, I see something like 22 hrs of bat time. 
[/LIST]


This is also the priority list for me, anything else is a bonus - i.e. "Desktop mode". So far I can do all of the above on my android device, and some of it with iOS, but iOS always frustrates the hell out of me so I decided to give Ubuntu tablet a fair go to see if it can replace my Android...   



Other


Having said all that, let me just say that I REALLY tried to love the ubuntu tablet, and I realise it is in it's really early stages, and I realise most of my dissatisfaction comes from lack of dedicated third-party apps, I think that there are some things that really require immediate attention:
[LIST=1]
[*]screen orientation funky rotation is killing my love for this device, and I dont want to lock it in place manually.
[*]scopes should work in vertical mode too
[*]file management should just work, no special permission hidden in a side submenu should be required. Thumbnails. Initiated file transfers should work even in background or when screen goes to sleep. This stuff should also work perfectly as it should be one of the strong points having "convergance" in mind.
[*]keyboard sometimes not appearing bug should be addressed
[*]I think it would be more intuitive to be able to close an opened app by dragging it from the dock than long pressing for submenu and clicking close (it it's pinned it should return to it's place in the dock but closed). Or maybe a bubble icon with an X should appear where I could drag it so it closes - let's start thinking more in terms of mobile, touchscreen platforms.
[*]there is no simple text editor preinstalled - I had to search and find edIt...   but there is no "open with" option so anything that isn't .txt remained inaccessible. (.nfo, .srt..,...)
[*]working in full desktop mode, sometimes the system would slow down with loads of opened apps...   I guess I just got used to working on android and not closing down anything. A "close all" button on the dock would be useful.
[*]what is wrong with the light sensor? In auto mode it keeps changing backlight every couple seconds... 
[/LIST]


I will add to this list and remove from it as I continue my love/hate relationship with M10 for as long as I can bear :)    If anyone has any answers or solutions to some of my problems, please share!

[[IMG]http://fileserver.imagebucket.net/i/00000/zz4z6bmjmx9m_t.jpg[/IMG]](http://imagebucket.net/zz4z6bmjmx9m/IMG_20160424_134214.jpg)


[[IMG]http://fileserver.imagebucket.net/i/00000/6v2j5iwwv0tx_t.jpg[/IMG]](http://imagebucket.net/6v2j5iwwv0tx/IMG_20160424_134152.jpg)

---

### Post by eaz2 on 2016-04-24
Thanks for your good summary, I do agree on most of your observations!
The web browser did not yet crash on me, by the way. The email client has a lot of limitations though.
I find the automatic screen brightness very annoying and switched it off as it keeps dimming/brighting all the time.

Can you please tell me a bit more about the smb network file browsing? I cannot get this to work, my NAS is protected with userid and password, and I cannot yet access the files. This is by way the most annoying thing I came across.

---

### Post by John_Harris on 2016-04-24
I found that helpful, it gives me a glimpse of how other users hope to use the tablet. I've been through the Ubuntu Store and the entire paradigm is foreign to me, there's an icon, a writer's name and pricing information and that's it. What they do and why I should trust their app isn't stated but I'd not download anything to my laptop on that much background. I do need to spend some time on the non-desktop side of things eventually or I'll never learn.

---

### Post by NiksaVel on 2016-04-24
Did you use the upper right side drop down menu in file manager to grant full access. Until you do that you can see the external drives and Network but it will show as empty.

---

### Post by NiksaVel on 2016-04-24
As for the store..    Personally I find the official ustore scope clunky and slow with no indicator that something is loading...    I find [https://uappexplorer.com](https://uappexplorer.com) much more usable...     
The whole star and heart grading system really helped me to find some apps...

---

### Post by eaz2 on 2016-04-24
> **NiksaVel said:**
> Did you use the upper right side drop down menu in file manager to grant full access. Until you do that you can see the external drives and Network but it will show as empty.
Yes, I did, but no files show up...

---

### Post by roddy4 on 2016-04-24
> **eaz2 said:**
> Yes, I did, but no files show up...

The same thing happened to me, I just restarted the tablet and it worked.

---

### Post by eaz2 on 2016-04-24
> **roddy4 said:**
> The same thing happened to me, I just restarted the tablet and it worked.

I've restarted a couple of times, no cigar.
I don't think it could work, because how would it know how to log on to the NAS? it does not ask for a userid, It only asks a password. 
I've created a Phablet user on the nas, but it does not work.

---

### Post by NiksaVel on 2016-04-24
> **eaz2 said:**
> I've restarted a couple of times, no cigar.
I don't think it could work, because how would it know how to log on to the NAS? it does not ask for a userid, It only asks a password. 
I've created a Phablet user on the nas, but it does not work.

When I access te smb it asked me  for username and password. I could change the default phablet username.......  the fact that clicking the remamber doesnt do anything is another problem.

---

### Post by roddy4 on 2016-04-24
> **eaz2 said:**
> I've restarted a couple of times, no cigar.
I don't think it could work, because how would it know how to log on to the NAS? it does not ask for a userid, It only asks a password. 
I've created a Phablet user on the nas, but it does not work.

Sorry, I got confused and answered a question no one asked! ](*,) My mistake.

I've got the same problem you have. I can see the share but that's all. Won't connect or anything. When I click the share name the screen stutters but nothing happens. My share is open and doesn't need a username or password!

---

### Post by dregs on 2016-04-26
The Aquaris M10 Ubuntu Edition does seem a little more like a proof of concept than a polished product. That said, I've been able to work around its limitations and make it useful in my life. I listen to podcasts over a bluetooth speaker system, edit LibreOffice docs, and look at Facebook. I'm looking forward to using GIMP to clean up sketches that I do when I'm away from my laptop and scanner. Overall, I'm happy. I wish that the location services worked better, and I wish for a little more performance, and more apps will be nice when they come along. But this is a useful and fun device for me. And it's fun to ssh into it.

---

### Post by Lance_Wex on 2016-04-26
I'm really disappointed with it too. I knew it was going to be limited, but even still it has let me down. I thought even using it as just a media consumption device would be OK. But it can't really do that either. I am still not sure how I can load my photos on it unless through Facebook or Flickr or Instagram .And that is lame. I want to transfer a lot of photos from my computer. But this thing makes something so simple very difficult. This is like a proof of concept, and not at all ready.

---

