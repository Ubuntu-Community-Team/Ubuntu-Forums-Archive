---
title: "The data management concept of Ubuntu1 is a miracle!"
date: 2013-12-15
forum: Ubuntu Cloud and Juju
---

### Post by jolexin on 2013-12-15
On my iphone I have got Ubuntu-one (App U1), among others to store there a few mp3 files for journeys abroad; I would like to listen to these files during my journey, without the necessity to connect to the Ubuntu cloud. Now everybody knows that all mobile phones must be switched off during start and landing of airplanes. But what happens after that, when I switch on my iphone in the foreign country? 

I observed that if I do the "wrong" thing, my iphone starts to re-synchronize tons of bytes, although they did not change. But what is "wrong" exactly? May I sign out of Ubuntu? The underlying logic is a miracle for me! Therefore the following remarks and proposals:

1) I would be glad if I could read sowewhere, how to use the U1 app in order to prevent unnecessary (expensive) data transfer. 

2) What seems to be missing in the U1 app, is a simple global query to the server, whether anything has changed at all, before the app starts to synchronize file by file. 

3) In some locations there is no connection via the mobile internet. In that case I would appreciate a possibility to log in to U1 locally and access (listen to) the files that happen to reside on my iphone.

Next I consider the Ubuntu-one on my PC (Ubuntu 12.04) 

4) On my PC I established a folder with selected mp3-files to listen. I specified that folder to be sync'd in Ubuntu1, such that they will also be accessible on my iphone. After all the files had been uploaded to the cloud, I clicked "stop syncing"; my intention was to start future synchronization only when I see the necessity. I learned that "stop syncing" means "delete the files in the cloud" - which I did not intend to do.

**Obviously I have misunderstood part of the data management concept of Ubuntu1**, or, in other words my imagination of "logic" differs from that of the Ubuntu1 developers. So what can I read about that? Who is willing to to discuss or describe that in this forum? I am certain that this is a topic of general interest.

---

### Post by tgalati4 on 2013-12-15
You have found a Use Case that Ubuntu One was not developed for.  The fact that the iPhone is a closed environment (sometimes called Walled Garden); you are supposed to listen to music through iTunes only.  Try downloading an mp3 file from your home-based server using Safari on the iPhone.  Good luck getting it to download or stream.

The resync in your case may have been a timezone issue.  If your phone has changed timezones, then the time stamps on the files may be stale and Ubuntu One is trying to update the files--even though the files haven't changed.  This may be a bug or a feature depending on how useful this behavior is.

I would post your detailed experiences in the Ubuntu One bug tracker and see if others are having similar issues.

---

