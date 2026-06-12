---
title: "file cloud syncing risks"
date: 2012-12-11
forum: The Cafe
---

### Post by sdowney717 on 2012-12-11
I recently was experimenting with cloud storage and syncing.

It is a nice idea to store a backup onto cloud storage. 

What if somehow a cloud site was hacked and someone deleted the files from synced accounts, then your backup is gone and your local files as well when your local client starts syncing the 2 accounts. Or some cloud site gets a virus to do the same, or some cloud admin with a personality disorder deletes random folders. Or some random catastrophe occurs on the cloud site.

So I have been thinking maybe a better option would be local storage on separate hardrive under your control for files like perhaps pictures or coding in addition to cloud storage.

---

### Post by grahammechanical on 2012-12-11
We have heard about some people who have their head in the clouds. This is fine so long as their feet are on the ground.

The company that I worked for had nightly backups on tape. Every morning the tapes were changed in a routine that had tape #1 being reused two weeks later. A fine system? No. The tapes were left in a pile next to the servers.

If there was fire those backups would be destroyed. A business could replace equipment within 48 hours but without the records of its customers it would go out of business. Belt and braces is best.

Is this not an example of data being stored in the 'cloud?'

[http://www.bbc.co.uk/news/technology-20641193]("http://www.bbc.co.uk/news/technology-20641193")

Regards.

---

### Post by forrestcupp on 2012-12-11
> **sdowney717 said:**
> I recently was experimenting with cloud storage and syncing.

It is a nice idea to store a backup onto cloud storage. 

What if somehow a cloud site was hacked and someone deleted the files from synced accounts, then your backup is gone and your local files as well when your local client starts syncing the 2 accounts. Or some cloud site gets a virus to do the same, or some cloud admin with a personality disorder deletes random folders. Or some random catastrophe occurs on the cloud site.

So I have been thinking maybe a better option would be local storage on separate hardrive under your control for files like perhaps pictures or coding in addition to cloud storage.Interesting thought. I use Dropbox for some important stuff, so what you're saying got me interested. So I went to my Dropbox folder and deleted a file that I didn't care about, just to see what would happen. Lo and behold, my local Dropbox immediately synced and deleted that file. The good news is that it popped up a notification that let me know that it was deleted from the web, and it also gave me the opportunity to go back and restore the file. I don't know about other Cloud storage services, but Dropbox keeps snapshots. I guess a hacker could probably wipe it all out. Hopefully, the likelihood of that happening is pretty low. But just in case, I do also perform local backups to an external drive, including my Dropbox folder.

Edit: according to [this article](http://www.pcworld.com/article/2010282/5-serious-business-alternatives-to-dropbox.html), earlier this year, Dropbox announced that thousands of user passwords had been stolen.

---

### Post by memilanuk on 2012-12-11
I think the OP does somewhat have a point... lots of people seem to see 'cloud' services as the answer to everything, and that it excuses them from having to think about their local infrastructure and processes.  If the data is that important or critical, multiple independent backups may be in order.

---

### Post by memilanuk on 2012-12-11
> **forrestcupp said:**
> Lo and behold, my local Dropbox immediately synced and deleted that file. The good news is that it popped up a notification that let me know that it was deleted from the web, and it also gave me the opportunity to go back and restore the file. I don't know about other Cloud storage services, but Dropbox keeps snapshots. 


Funny you should mention DropBox...

Recently I was setting up Eclipse IDE on a new laptop, and made a mistake when importing a directory full of project files from my Dropbox folder.  I deleted the projects inside Eclipse, thinking I had copied them over to local storage, not realizing I had goofed and deleted *all* the files from the sub-folder in Dropbox.  

After freaking out for a few seconds, I remembered about the Dropbox snapshot/restore feature.  I went online, and much to my surprise, that feature works okay for individual *files*... but not for entire folders.  When there are a few *thousand* files in hundreds of folders... thats not exactly a viable option.

I emailed their tech support requesting a roll back - basically an 'undo' of that particular event - and submitted the event id, etc. as required.

That was (going on) four days ago.

This morning I finally got a canned tech support email telling me they'd been real busy lately and hadn't been able to get around to things, and if I still needed help, to send them an email trouble ticket with the event id in it.  Which I *thought* was what I had already *done*.

Long story short... before, I specifically excluded my Dropbox folders when making local backups.  Not any more...

---

### Post by forrestcupp on 2012-12-11
> **memilanuk said:**
> Funny you should mention DropBox...

Recently I was setting up Eclipse IDE on a new laptop, and made a mistake when importing a directory full of project files from my Dropbox folder.  I deleted the projects inside Eclipse, thinking I had copied them over to local storage, not realizing I had goofed and deleted *all* the files from the sub-folder in Dropbox.  

After freaking out for a few seconds, I remembered about the Dropbox snapshot/restore feature.  I went online, and much to my surprise, that feature works okay for individual *files*... but not for entire folders.  When there are a few *thousand* files in hundreds of folders... thats not exactly a viable option.

I emailed their tech support requesting a roll back - basically an 'undo' of that particular event - and submitted the event id, etc. as required.

That was (going on) four days ago.

This morning I finally got a canned tech support email telling me they'd been real busy lately and hadn't been able to get around to things, and if I still needed help, to send them an email trouble ticket with the event id in it.  Which I *thought* was what I had already *done*.

Long story short... before, I specifically excluded my Dropbox folders when making local backups.  Not any more...Wow. That really sucks. That's good information to know. And I've always done local backups of my Dropbox folder. You just never know what could happen. I like redundancy.

---

### Post by Primefalcon on 2012-12-11
Well I too keep some important files in dropbox, I do mitigate the risk by having a backup though and also storing all of my files that in dropbox in an EncFS volume

---

### Post by Mikeb85 on 2012-12-11
I generally back up important files in Ubuntu one, have local files on both my computers (and sometimes my cell phone as well) but I log out of Ubuntu One and don't sync.  

It basically comes down to:  don't keep all your eggs in one basket...

---

