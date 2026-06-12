---
title: "Tomboy syncs with Ubuntu One - and promptly deletes all my local notes!"
date: 2010-01-14
forum: Ubuntu One (CLOSED)
---

### Post by jacksonpollack on 2010-01-14
I attempted to sync Tomboy notes with Ubuntu One, the process claimed to be successful &#8211; and deleted all the notes on my computer, with no warning at all. Thankfully I had just backed things up yesterday...

I'm running Karmic, the Tomboy is version 1.0.0, and the Ubuntu One client is 1.0.2 (I think).

A little while ago I was having problems with Tomboy syncing with Ubuntu One at all. Then things worked, but I ran into problems with the program declaring that the notes online were newer than my local ones &#8211; which was certainly not the case, as I only use my Ubuntu One account with a single computer. Some of the notes were conflicting, though there were also problems with templates (probably something similar to this bug here: [https://bugs.launchpad.net/ubuntuone-servers/+bug/502017](https://bugs.launchpad.net/ubuntuone-servers/+bug/502017)). 

So I deleted all the notes, manually, on the Ubuntu One site, thinking this would help. It certainly didn't help with my template problem, and now when I sync it declares &#8220;Synchronization is complete, 32 notes updated. Your notes are now up to date.&#8221; &#8211; and lists all of my notes stating that they were deleted locally! And indeed they are.

If I go online and look at Ubuntu One, the notes tab simply says: "You have no notes (yet!)."
I tried to see if this was recurring, and it is. Every time all my notes are deleted.

Any solutions? Anyone even running into this same problem? Thanks ahead of time for any help!

---

### Post by joshuahoover on 2010-01-15
> **jacksonpollack said:**
> I attempted to sync Tomboy notes with Ubuntu One, the process claimed to be successful – and deleted all the notes on my computer, with no warning at all. Thankfully I had just backed things up yesterday...

I'm running Karmic, the Tomboy is version 1.0.0, and the Ubuntu One client is 1.0.2 (I think).

A little while ago I was having problems with Tomboy syncing with Ubuntu One at all. Then things worked, but I ran into problems with the program declaring that the notes online were newer than my local ones – which was certainly not the case, as I only use my Ubuntu One account with a single computer. Some of the notes were conflicting, though there were also problems with templates (probably something similar to this bug here: [https://bugs.launchpad.net/ubuntuone-servers/+bug/502017](https://bugs.launchpad.net/ubuntuone-servers/+bug/502017)). 

So I deleted all the notes, manually, on the Ubuntu One site, thinking this would help. It certainly didn't help with my template problem, and now when I sync it declares “Synchronization is complete, 32 notes updated. Your notes are now up to date.” – and lists all of my notes stating that they were deleted locally! And indeed they are.

If I go online and look at Ubuntu One, the notes tab simply says: "You have no notes (yet!)."
I tried to see if this was recurring, and it is. Every time all my notes are deleted.

Any solutions? Anyone even running into this same problem? Thanks ahead of time for any help!

Deleting all the notes on the server and then syncing with your local PC will result in the notes being deleted from your computer, assuming the notes between your PC and the server are the same.

Are you still getting the original problem that notes on the server are newer than notes on your local PC? If so, can you file a bug at: [https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug](https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug)

Thank you,

Joshua

---

### Post by osomphane on 2010-01-15
You know, this and a lot of other data loss problems can be remedied simply by changing one thing:

Instead of deleting the files permanently on all machines, move the files tagged as deleted to the thrash. This will also enable users to undo deletes by restoring files from the thrash.

Consider this: a user has two computers or a single computer and Ubuntu One. He deletes a file by accident using the U1 web interface. He realizes that he made a mistake and wants his file back, so he goes to one of the computers and restores the file from thrash. Wouldn't that be a nicer solution than realizing he is SOL?

---

### Post by jacksonpollack on 2010-01-15
Thanks for your reply Joshua. 

I restored all of my notes from a backup, and this time successfully synchronized them with Ubuntu One. But after editing a few and synchronizing them again - they are all deleted, old and new! I'm not quite sure what to do now, save never to synchronize my notes again.

Hm, yeah, sending them to the trash might be nice idea. It certainly caught me off guard, and was lucky to have lost very little.

---

### Post by joshuahoover on 2010-01-20
> **osomphane said:**
> You know, this and a lot of other data loss problems can be remedied simply by changing one thing:

Instead of deleting the files permanently on all machines, move the files tagged as deleted to the thrash. This will also enable users to undo deletes by restoring files from the thrash.

Consider this: a user has two computers or a single computer and Ubuntu One. He deletes a file by accident using the U1 web interface. He realizes that he made a mistake and wants his file back, so he goes to one of the computers and restores the file from thrash. Wouldn't that be a nicer solution than realizing he is SOL?

Agreed. We will eventually add the ability to allow people to rollback deletions and edits.

---

### Post by joshuahoover on 2010-01-20
> **jacksonpollack said:**
> Thanks for your reply Joshua. 

I restored all of my notes from a backup, and this time successfully synchronized them with Ubuntu One. But after editing a few and synchronizing them again - they are all deleted, old and new! I'm not quite sure what to do now, save never to synchronize my notes again.

Hm, yeah, sending them to the trash might be nice idea. It certainly caught me off guard, and was lucky to have lost very little.

This is a serious issue. We should not be deleting notes as you described. Can you do me a HUGE favor and try the following:

[LIST=1]
[*]Quit Tomboy 
[*]Applications->Accessories->Terminal, and run: 

[LIST]
[*]tomboy --debug > ~/tomboy_debug.log 
[/LIST]
[*]Try to reproduce the bug and then attach ~/tomboy_debug.log to a bug report filed at: [https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug](https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug)
[/LIST]
Thank you!

Joshua

---

### Post by joshuahoover on 2010-01-20
> **joshuahoover said:**
> This is a serious issue. We should not be deleting notes as you described. Can you do me a HUGE favor and try the following:

[LIST=1]
[*]Quit Tomboy
[*]Applications->Accessories->Terminal, and run:
[LIST]
[*]tomboy --debug > ~/tomboy_debug.log
[/LIST]
 
[*]Try to reproduce the bug and then attach ~/tomboy_debug.log to a bug report filed at: [https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug](https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug)
[/LIST]
Thank you!

Joshua

Also, if you can attach the following log file to that bug report, it will help us determine what is going on: ~/.cache/desktop-couch/log/desktop-couch-replication.log

---

### Post by jacksonpollack on 2010-01-21
Well, this is a bit weird, but I re-added the synchronization information (I had deleted it for fear of mistakenly synchronizing again), exited from tomboy and followed your instructions. When I first tried to synchronize, I got a bunch of errors about conflicting new note templates. I pushed on through those, and afterwards nothing was updated (though nothing was deleted locally either). Then I tried again... and everything synched up just fine. Now everything works.

So I can't reproduce what was happening, though I'm happy it all works now. I have no clue what went wrong though. I had deleted the synch info before and re-added it, but that hadn't worked, so why were things fine this time?

In any case, thanks for your help.

---

### Post by joshuahoover on 2010-01-22
> **jacksonpollack said:**
> Well, this is a bit weird, but I re-added the synchronization information (I had deleted it for fear of mistakenly synchronizing again), exited from tomboy and followed your instructions. When I first tried to synchronize, I got a bunch of errors about conflicting new note templates. I pushed on through those, and afterwards nothing was updated (though nothing was deleted locally either). Then I tried again... and everything synched up just fine. Now everything works.

So I can't reproduce what was happening, though I'm happy it all works now. I have no clue what went wrong though. I had deleted the synch info before and re-added it, but that hadn't worked, so why were things fine this time?

In any case, thanks for your help.

Very strange. If you have further problems, please either file a bug and email me personally at joshua dot hoover at canonical dot com or hop on #ubuntuone on Freenode IRC and ask for joshuahoover there. I'm normally on Monday-Friday, 14:00 to 22:00. 

Thank you,

Joshua

---

### Post by jacksonpollack on 2010-01-22
Sure thing. Thanks again for your help.

---

### Post by calvim on 2013-02-04
I have been getting an error while syncing Tomboy with Ubuntu One for the last couple of days. Then suddenly this morning the sync went through, but alas ALL MY NOTES ARE GONE (two years worth of them) from my work MacBook. Fortunately I have an Ubuntu machine at home which only synchronizes manually so hopefully I am not doomed.  It seems to me that somehow the notes on the U One server were deleted, and that caused the local notes on my MacBook to be also deleted. 
Is there a way to prevent  the notes from my home PC from sharing the same fate, but rather being 'pushed' to the server at the next sync?

---

### Post by HelloU on 2013-02-04
This problem here. ;(

All my Tomboy notes are gone this morning. 

Hope I can restore my notes from another Ubuntu installation.

---

