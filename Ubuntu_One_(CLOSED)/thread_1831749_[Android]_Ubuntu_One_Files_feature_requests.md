---
title: "[Android] Ubuntu One Files feature requests"
date: 2011-08-23
forum: Ubuntu One (CLOSED)
---

### Post by mkarnicki on 2011-08-23
Hi everyone,

I'm a member of ubuntuone-android-hackers team on Launchpad, I work on Ubuntu One Files app. If you would like to see new features in the app, you can post your ideas here. I think the forums is a good and comfortable place to share ideas. We have already received quite a lot of requests via e-mail.

Most notably, these have been already requested:
- secure app launch with PIN entry
- preserve folder structure when auto-uploading files
- real sync (i.e. reupload a file, that has been modified; sync down favorite folders; etc)

We continue to fix bugs and improve on what we already have, this is just to give you a place to share ideas on new features. We will select the best we can take on given available time and resources. I can't guarantee we'll implement them, I can guarantee however that we're doing our best and I'll be keeping track of this official thread.

Cheers!
Ubuntu One Android Hackers team

PS Please keep in mind this thread is not dedicated to bugs. If you find a bug in U1F, please either file a bug report at
[https://bugs.launchpad.net/ubuntuone-android-files](https://bugs.launchpad.net/ubuntuone-android-files)
or comment in an according thread we'll set up for each release. Much thanks!

---

### Post by aviceda on 2011-08-25
Any chance of a Gallery feature like Dropbox?

---

### Post by mkarnicki on 2011-08-25
That could be a nice feature, I will suggest that to the team. I can't tell anything more at that point, though.

---

### Post by mkarnicki on 2011-08-29
"Support App 2 SD"

To support App 2 SD for Ubuntu One Files we have to consider the following:

Catch broadcast of ACTION_EXTERNAL_APPLICATIONS_AVAILABLE to:
(1) restart MediaCatcher (lightweight service that waits for new pics)
(2) reregister failed tranfer alarm

"Your accounts created with AccountManager will disappear until external storage is remounted." -- this could influence future features. We should not assume nothing about the user, but we'd expect they will mount the SD storage back soon.

ACTION_BOOT_COMPLETED - we may never get this. We used it for (1) and (2) as well. User would have to launch the app once after phone boot. Not cool.

Finally, apps that have widgets should not be moved to SD. We may provide a widget, but people might choose not to use it and move the app to sd.

All in all, we know you guys are expecting app2sd, we just still have to give it a little more thought, rather than adding 2 lines in the AndroidManifest.xml and hoping for the best.

---

### Post by liquidmonkey on 2011-09-22
was just in using the u1 android app on my samsung galaxy s2 and i downloaded a file (.pdf).
that worked BUT when i later went back into that folder, i could not tell which file had been downloaded or not, ie, they all looked the same.

it would be nice to have a little check mark, different color, a symbol or anything that tells me THIS IS A LOCAL FILE.





ps, i'm very grateful for the free 5gigs and free app, thank you!

---

### Post by mkarnicki on 2011-10-26
Hello,

Please notice the background color of files that have been downloaded is white, whilst the files which have not been downloaded have grey background. We might make this more obvious some time in the future (a tick, like you suggested, or something similar).

---

### Post by UngodlySpoon on 2011-11-16
Love what you guys are doing with Ubuntu One and loving the integration with Android, great job!

Here's my feature suggestion: I just realised that I can not only Sync my Tomboy notes with U1, but I can also view/edit/create them in my web browser!  Cool stuff!  That makes me think that it would be even cooler if Ubuntu One provided a sync for the 'Sticky Notes' application, or just something like it (one specific note in Tomboy?).  Yes this isn't Android specifically, but the use case I'm thinking of would be to have a home screen widget on my phone (like the built-in one, although a lot of the 3rd party ones are better) where I can quickly jot down notes and reminders, having them all sync to my computer so that I remember them later.

---

### Post by mkarnicki on 2011-11-17
Hello,

Thanks for your suggestion. At the moment, we're focusing on improving our current apps and there's no plan for a Tomboy notes app for Android. We may look into it at some point, and I recognize many users would probably find that very useful.

You might wanna give this a try:
[https://market.android.com/details?id=org.tomdroid&hl=en](https://market.android.com/details?id=org.tomdroid&hl=en)

---

### Post by michael81 on 2011-12-02
Hi,

A real sync feature, like on Windows and Linux, would be the best feature. But just the ability to download an entire folder (including all subfolders), and also to download a top level cloud folder would be great.

I'm sure there are a few people like me who probably won't be changing files on their phones much, so don't need a full sync feature, but would like to be able to download everything from a cloud folder.

Thanks!
Michael

---

### Post by jmate24 on 2012-02-11
I don't know if this has been suggested but...

To be able to stream/play .ogg and .flac files?

---

### Post by mkarnicki on 2012-02-12
We allow streaming of music files in Ubuntu One Music. You'll always be able to download files with Ubuntu One Files, but streaming will not be implemented as part of Ubuntu One Files, sorry!

---

### Post by hildenbrandsteven on 2012-02-13
Does anyone know about Ubuntu development within the iPhone possibly? I'd love to help with this.. and also willing to put my 4S through beta testing!

---

### Post by thepisu on 2012-02-13
**Remember username and password feature**

What about implementing a "remember" feature on login, so it's not needed to re-enter username and password at each restart?

See has been asked also in this post:
[http://ubuntuforums.org/showthread.php?t=1911665](http://ubuntuforums.org/showthread.php?t=1911665)

---

### Post by mkarnicki on 2012-02-13
@hildenbrandsteven
Hit us up at #ubuntuone on irc.freenode.net 

Also, check out
[http://launchpad.net/ubuntuone-ios-files](http://launchpad.net/ubuntuone-ios-files)
[http://launchpad.net/ubuntuone-ios-music](http://launchpad.net/ubuntuone-ios-music)

@thepisu
Simply move Ubuntu One Files from SD back to phone storage. It's an Android limitation, not U1F bug. Many users have requested to allow app2sd, but the account in Account Manager is removed once the storage is unmounted / phone rebooted.

---

### Post by thepisu on 2012-02-16
> **mkarnicki said:**
> 
@thepisu
Simply move Ubuntu One Files from SD back to phone storage. It's an Android limitation, not U1F bug. Many users have requested to allow app2sd, but the account in Account Manager is removed once the storage is unmounted / phone rebooted.

You're right! Sorry I did not noticed this.

Thank you

---

### Post by mkarnicki on 2012-02-17
No problem, happy to help :)

---

### Post by killabee44 on 2012-04-28
Still taking suggestions? I was wondering if it would be possible to have the ability to "browse" the phone to pick a folder to put on the cloud. 

Also the ability to delete multiple files from a web browser. When you have a lot of files up on the cloud, it's a pain to delete, let's say half of them one by one. 

Thanks.

---

### Post by mkarnicki on 2012-04-30
Sure! Keep them coming :)

> **killabee44 said:**
> Still taking suggestions? I was wondering if it would be possible to have the ability to "browse" the phone to pick a folder to put on the cloud.

We may explore these kind of features when we'll be working on sync, which should be matter of 2-3 months from now, I think.

> Also the ability to delete multiple files from a web browser. When you have a lot of files up on the cloud, it's a pain to delete, let's say half of them one by one. 
Thanks.

Right, there will be UI revamp of our web site, but this section of the forum accepts only requests related to Android apps. For what it's worth, we'll most probably add multiple selection for deletion purposes to the Android app soon :)

---

### Post by killabee44 on 2012-04-30
Thanks, I appreciate the info...



> **mkarnicki said:**
> Sure! Keep them coming :)



We may explore these kind of features when we'll be working on sync, which should be matter of 2-3 months from now, I think.



Right, there will be UI revamp of our web site, but this section of the forum accepts only requests related to Android apps. For what it's worth, we'll most probably add multiple selection for deletion purposes to the Android app soon :)

---

### Post by mkarnicki on 2012-05-30
Hey folks,

If you want to give it a try, here's U1F 1.2.0-rc.1
[http://goo.gl/YVG6e.qr](http://goo.gl/YVG6e.qr)

Changes:
- greatly improved speed of directory refreshing
- allow sharing multiple files at once with Ubuntu One
- bug fixes

If you try it, please let us know how it worked for you. Thanks!

---

### Post by kev3124 on 2012-06-16
Having all of my photos backed up to the cloud automatically is great. My concern is having to manually download 200+ pictures, one by one in the event I have to restore. Is there a way to download the whole photo directory in one shot? Some sort of batch operation maybe? 

Manual file by file download isn't an opition when you have a large number of individual files.

---

### Post by mkarnicki on 2012-06-17
I've filed a bug report here for you.
[https://bugs.launchpad.net/ubuntuone-android-files/+bug/1014454](https://bugs.launchpad.net/ubuntuone-android-files/+bug/1014454)

Indeed, you can't download a top level directory, but you can download (non recursive file only download) any directory from context menu.

---

### Post by Rifester on 2012-08-04
I really would like to stay with Ubuntu One for my cloud storage and appreciate the obvious work that has been going into the service.    I am using the Ubuntu Android app on my phone for storing photos.   What I would really like to see is the ability to view photos in the Ubuntu One folders from the Android app.   Dropbox and Gdrive both have this ability.   I want to support Ubuntu, but the lack of this feature may make me reconsider renewing after my first year.   I am sure there are many people who won't sign up for Ubuntu One (or switch from other services) knowing that they cannot view their photos in the cloud.

Edit:  I filed a bug report about this.   If YOU would like to see this featured added to Ubuntu One please mark that it affects you as well.   [https://bugs.launchpad.net/ubuntuone-android-files/+bug/1033048](https://bugs.launchpad.net/ubuntuone-android-files/+bug/1033048)

---

### Post by mkarnicki on 2012-08-06
Fear not Rifester, Ubuntu One Team to the rescue. Well should have this out very soon as an experimental feature.

---

### Post by Rifester on 2012-08-06
Sweet!   Thanks!

---

### Post by Rifester on 2012-08-14
Any idea when we will see this and if it is experimental how can I test it?

---

### Post by mkarnicki on 2012-08-15
Current 1.2.3 version on Google Play has a gallery, which actually fetches previews, not original files, much smaller than original images. FWIW this is exactly what Dropbox does. We're now testing on-list thumbnails.

EDIT: Why don't you give this a try: [http://goo.gl/BDJ0a.qr](http://goo.gl/BDJ0a.qr) - please note, this is an experimental, officially unsupported build. Although the only thing you'll find is on-list thumbs and 'Download' added to image file context menu.

---

### Post by Rifester on 2012-08-22
Mkarnicki, I got an Ubuntu One Android update yesterday and can now view photos.  It is working great.  Thanks team!

---

### Post by mkarnicki on 2012-08-23
@Rifester Check out the latest update from the day before yesterday :)

@ZDroid I don't know what you mean. Ubuntu One Files app is free, open source, and doesn't come in trial version.

---

### Post by Random20210831 on 2012-08-23
I thought the Ubuntu One Music that can only used for 20 days.

---

### Post by mkarnicki on 2012-08-23
@ZDroid Ah. This topic is about 'Ubuntu One Files feature requests', so I thought you were talking about U1F. To answer your question, Ubuntu One Music is available with 30 days trial. Stay tuned!

---

### Post by pdwOnline on 2012-10-15
Ubuntu One is lovely. however, a better indicator of the syncing progress would be nice. Currently the ubuntu one panel only says 'sync in progress' 

I like to know if this sync still works, how many files still need to be done, and if there are large files, are there any bytes transferred (at what rate?)

Also cool would bee to see the overview in your devices tab (i.e. Device A: syncing 75%, Device B  up to date)

---

### Post by mkarnicki on 2012-10-15
I'm sorry, you have posted onto a wrong thread. This one concerns Android feature requests only, please note the topic of the thread. Have a nice day.

---

### Post by NewAmercnClasic on 2012-11-13
It would be nice to cross reference cloud backup systems e.g. sync between online back-ups like a redundant cloud raid, however I'm not sure if that would be against the TOS.  It would sure make desktop edits easier for those of us with multiple platform mobile devices.  I'd also like auto upload from SD upon mount.

---

### Post by partloer on 2013-01-21
It would be nice to have Ubuntu One work on Ubuntu Server without having setup the [Headless Mode]("https://wiki.ubuntu.com/UbuntuOne/Headless").  I could't get this to work and have added a [bug 219284]("https://answers.launchpad.net/ubuntuone-client/+question/219284") for this feature.

---

### Post by mkarnicki on 2013-01-21
@NewAmercnClasic We do have sync on the roadmap, it'll take a while, though.

@partloer Thanks for dropping by. However, this forum thread concerns Android only (and only I, as the Android developer, track it, so you may want to find a more suitable place to share that thought. Thanks! :) )

---

### Post by karni2 on 2014-04-24
[https://one.ubuntu.com/services/shutdown/](https://one.ubuntu.com/services/shutdown/)

---

