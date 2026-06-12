---
title: "URGH! Is it supposed to be this slow?"
date: 2012-04-05
forum: Ubuntu One (CLOSED)
---

### Post by x-shaney-x on 2012-04-05
Having flirted with Ubuntu One on and off since it's creation, I finally decided it is just what I need to keep my important photos synchronised between multiple computers.

So I went ahead and added the photos to the Ubuntu One folder, around 2GB worth.

Well that was about 3 hours ago and it is still not close to being complete.
Out of 15 folders in there, only 5 are showing as ticked and 2 of those are currently empty!!

I don't expect miracles but Dropbox synced the same files in a fraction of the time.

---

### Post by x-shaney-x on 2012-04-06
Well it has been running most of today and still less than half the 2GB synced.

I cannot seriously consider Ubuntu One as an option anymore.

---

### Post by Paddy Landau on 2012-04-06
You must have a fast Internet connection if you can synchronise 2Gb in just an hour or so with Dropbox. I backed up about 3Gb data (for a magazine that I edit) and it took a full day.

But if Dropbox is much faster for you than Ubuntu One -- I don't know why that should be -- I guess you'll have to stick with Dropbox.

---

### Post by duanedesign on 2012-04-06
Things have been a little slow yesterday and this morning. It is slowly getting back to normal. Sorry for the inconvenience.

---

### Post by x-shaney-x on 2012-04-06
If there is a problem with the service and things aren't normally this bad then that's fine.

I am getting more confused with things though...

I have a "Pictures" folder inside the Ubuntu One folder and inside this pictures folder are a further 15 folders containing photos.

About an hour ago, all but one folder was showing a tick, indicating (I assume) that those folders are synced ok, with one folder showing the sync overlay and a mix of ticked and sync overlays inside.

I checked a few minutes ago and that one folder is still syncing but now a further 3 are showing that they are syncing and none of the pictures inside have ticks.

So how do I know what has synced and what hasn't and is this a problem with Ubuntu One not displaying properly or is it actually losing sync and having to start again?

The web interface indicates that the last sync activity was 2 hours ago but it has been syncing or appearing to sync constantly since then.

I also uploaded a single photo from my Android phone about 6 hours ago and it is showing in the web interface but still not on my computer.

---

### Post by duanedesign on 2012-04-06
What version of Ubuntu are you using?

If you are using an older version of Ubuntu you can use the following two commands to see how many items are in the queues.

```
u1sdtool --waiting-content | wc -l

u1sdtool --waiting-metadata | wc -l
```

If you are using 11.04 or newer these have been combined in one command:

```
u1sdtool --waiting | wc -l

```
This will tell you how many items are waiting to sync. Ubuntu One syncs the metadata queue before the content. You can tell things are syncing as the number gets smaller.

Did you add the photo to the Pictures - <phone> folder? That folder is probably not syncing locally. In newer versions of Ubuntu One you can check the Folders tab of the control Panel and click the sync locally option for that folder.

---

### Post by x-shaney-x on 2012-04-06
I am using 11.10.

At the time I saw the above post, the output of the u1sdtool command showed there were just over 300 files in the que.
I kept checking back and each time I ran the command it was showing smaller and smaller numbers until it finally reached zero and all folders in the Ubuntu One folder were showing as ticked and fully synced.
The U1 application also said everything was synced and up to date.

I came back to my computer some hours later and noticed that once again, folders were showing the sync overlay again.
I ran the ulsdtool command again and it now showed 201 files in the que.
I haven't added or removed any files in the folder or touched them in any way!!
That was over an hour ago and since then, every time I run the command it is still showing 201 files in the que.

So I don't know what's up with it now.

As for the picture uploaded by phone, I had previously pointed the Android app to a folder already in my Ubuntu One pictures folder and after many hours the picture did eventually show up on my computer so no problem with configuration, just incredibly slow to make it to me and that is downloading FROM the server, not uploading to it!

<EDIT>
Now the Ubuntu One application keeps telling me file sync is disabled.  I click on enable and then a little later it says it's disabled again <sigh>

---

### Post by x-shaney-x on 2012-04-07
Hi, me again :)

Since I last posted, my Ubuntu One folder has been in a loop of synchronising for no apparent reason at all.

It gets fully synced then about an hour later, just starts randomly syncing folders again, even though the folders have not been touched or accessed in any way and cannot possibly have any changes to need syncing.

This in itself wouldn't be a big deal but the never ending uploading is slowing my internet to a crawl, making it pretty much useless for anything else.

---

