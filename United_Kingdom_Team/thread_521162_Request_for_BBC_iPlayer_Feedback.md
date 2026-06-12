---
title: "Request for BBC iPlayer Feedback"
date: 2007-08-09
forum: United Kingdom Team
---

### Post by Beamerboy on 2007-08-09
As some of you know I am currently running a letter writing campaign against the BBC's decision to restrict their new iPlayer service to Windows XP.  I am in the process of generating a new set of letter templates now the service has launched and I would like to gather some feedback from people using the service.

I am particularly interested in more information regarding the p2p engine called Kontiki which is apparently what iPlayer uses. I have heard that it remains open and continues to use bandwidth when the iPlayer service is not running, which places consumers at the risk of breaking their ISP’s Fair Usage Policy leading them to face bills for extra bandwidth usage. It would be useful if anyone is running it to setup some bandwidth monitoring system to build up some statistics as to how much bandwidth Kontiki is using in the background when the iPlayer service has been shut down.

Also I have read that uninstalling iPlayer does not uninstall Kontiki and that users must run a second uninstall program to specifically remove this service. But upon trying to uninstall it some users have reported that the uninstall program tries to persuade the user not to uninstall and then crashes if they attempt to continue. If anyone has experienced this, it would be very useful information to add to the new letter templates.

So if you could please add your feedback to this thread it would be very helpful to the ongoing campaign.

You can read more about the campaign on my blog:

[http://blog.paladine.org.uk/?cat=11](http://blog.paladine.org.uk/?cat=11)

Thanks

Paladine

---

### Post by bobbocanfly on 2007-08-09
I havent had any problems with Kontiki eating my bandwith, though there is a 13mb background SYSTEM process called KService which just appeared today which im guessing is part of Kontiki. 

I havent tried uninstalling it yet (Despite the massive restrictions it is VERY useful :( ) so i cant really report on that.

I have been having a problem with a Bluecreen Crash. When i am watching something i have already downloaded then try and download something else at the same time, Windows fails and goes into a Bluescreen claiming NV4.dll as the problem (NVidia 4?).

So far 3/10 overall though if they de-drmed it, made it available on Linux, got a few more programs on it and it didnt actually crash. Then it might get a 7/10 because they didnt use Bit-torrent

---

### Post by Beamerboy on 2007-08-09
> **bobbocanfly said:**
> I havent had any problems with Kontiki raping my bandwith, though there is a 13mb background SYSTEM process called KService which just appeared today which im guessing is part of Kontiki. 

I havent tried uninstalling it yet (Despite the massive restrictions it is VERY useful :( ) so i cant really report on that.

I have been having a problem with a Bluecreen Crash. When i am watching something i have already downloaded then try and download something else at the same time, Windows fails and goes into a Bluescreen claiming NV4.dll as the problem (NVidia 4?).

So far 3/10 overall though if they de-drmed it, made it available on Linux, got a few more programs on it and it didnt actually crash. Then it might get a 7/10 because they didnt use Bit-torrent

Yes from what I can gather KService is the p2p service.  Does it continue to run when you close the iPlayer service or does it stop?  Also have you run any software to monitor the bandwidth the  KService process uses, that way we can be find out if it is still using bandwidth when iPlayer is not running.

Thanks for the feedback.

Paladine

---

### Post by bobbocanfly on 2007-08-09
> **Beamerboy said:**
> Yes from what I can gather KService is the p2p service.  Does it continue to run when you close the iPlayer service or does it stop?  Also have you run any software to monitor the bandwidth the  KService process uses, that way we can be find out if it is still using bandwidth when iPlayer is not running.

Thanks for the feedback.

Paladine

I right clicked the BBC iPlayer Library and told it to exit but that may or may not actually stop the iPlayer service. But when i just click exit KService still runs in the background using up a fair bit of RAM for a basic daemon service that shouldnt even be running!

What software should i use to check if it is stealing bandwith?

---

### Post by Beamerboy on 2007-08-10
> **bobbocanfly said:**
> I right clicked the BBC iPlayer Library and told it to exit but that may or may not actually stop the iPlayer service. But when i just click exit KService still runs in the background using up a fair bit of RAM for a basic daemon service that shouldnt even be running!

What software should i use to check if it is stealing bandwith?

Am not sure I haven't used windows for a very long time.  I think I heard someone talking about DU Meter on a broadband forum recently, maybe give that a try.  You need something that will allow you to monitor individual applications and services, I think DU Meter lets you do that.

Paladine

---

### Post by IanW on 2007-08-16
The PC modding forum [Bit-Tech]("http://bit-tech.net") has an article on their front page today describing this very behaviour.

Essentially, the author of said article queued 5 files for download using iPlayer, then paused  the downloads and closed the player from the taskbar.
He returned to the PC several hours later to find that KService.exe was still running, and merrilly hogging all the upload bandwidth it could find!

---

### Post by Beamerboy on 2007-08-16
> **IanW said:**
> The PC modding forum [Bit-Tech]("http://bit-tech.net") has an article on their front page today describing this very behaviour.

Essentially, the author of said article queued 5 files for download using iPlayer, then paused  the downloads and closed the player from the taskbar.
He returned to the PC several hours later to find that KService.exe was still running, and merrilly hogging all the upload bandwidth it could find!

Interesting article, I suspected as much.

Bobbocanfly, I notice in the article that the author was using a windows application called NetLimiter to monitor the kservice bandwidth usage, so you might want to give that a try and report back with your findings?

Thanks

Paladine

---

### Post by bobbocanfly on 2007-08-21
Sorry, totally forgot all about this thread. Will give this a go either tonight or when i get back from Reading on Wednesday.

---

