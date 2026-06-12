---
title: "No sync from Android phone"
date: 2011-10-04
forum: Ubuntu One (CLOSED)
---

### Post by crong on 2011-10-04
I've got Ubuntu One set up on my laptop (running Natty) and I've installed the mobile app on my Android phone.

If I add files or folders to ~/Ubuntu One, they do appear in the phone app and (after several failed attempts) I can open them.

The problem is that, if I edit them on the phone, the files are not updated in the cloud nor on my laptop.

What am I missing?

---

### Post by crong on 2011-10-11
No replies?

---

### Post by atryus28 on 2011-10-11
Sorry I have not tried it on my Android phone yet.  I will give it a shot and see if it works.

One thing to think about though.  How long are you waiting to see if the sync has happened?  Is it supposed to be instantaneous?  I would think for data usage it may not do it as often.  I am on a pre paid plan so I use WiFi for my stuff 90% of the time.

---

### Post by crong on 2011-10-11
Thanks for replying atryus28. I'm on pay-as-you-go too and I've only tested this on WiFi so far. Although it was a little flaky at first, it now seems to update the file in the cloud very quickly. This is what I'm up against:

[LIST=1]
[*]When I open the app in my phone I can see the file listed.
[*]Tapping on the file causes it to be downloaded.
[*]Tapping again on the file allows me to open it with an editor.
[*]When I save the file on the phone the modified time is not changed and it is not uploaded to the cloud.
[*]If I change the file on the computer and repeat the above steps it overwrites any changes I have made to the file on the phone.
[/LIST]

---

### Post by atryus28 on 2011-10-11
I thought I had something to edit my documents with but it seems I was mistaken.  What are you using to edit files on your phone?  Is there a free one to try?

---

### Post by atryus28 on 2011-10-11
I just grabbed a basic text editor and think I know what you might need to try.  I think this is a bit ugly but it just may be how this works.

Edit your file.  After you edit your file click the plus symbol --> add file --> navigate to the file you just edited and select it.  It will then say file updated and will sync up with your PC/Cloud.

---

### Post by crong on 2011-10-12
OK, thanks, that worked, but it is ugly.

I have to manually do that every time and I need to be running the application on the computer for the file to sync back from the cloud to its original folder (uploading is automatic).

I guess Ubuntu One is not the syncing application I thought it was.

---

### Post by mkarnicki on 2011-10-26
Hi guys,

I'm the developer of Ubuntu One Files. It takes time to implement features, we have tons of feature requests and not only this is something users are asking, it's something we want to implement as soon as possible.

Please note that nor the Android Market description nor the application tells it it syncs anything. We wanted to be very clear about this, and I can understand the confusion comes only from the fact, that Ubuntu One on Ubuntu and Windows does, indeed, sync files. At the moment, we only back up pictures automatically. We like to call that auto-upload, to avoid confusion.

---

