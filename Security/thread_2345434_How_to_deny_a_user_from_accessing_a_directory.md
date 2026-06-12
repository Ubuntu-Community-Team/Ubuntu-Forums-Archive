---
title: "How to deny a user from accessing a directory?"
date: 2016-12-04
forum: Security
---

### Post by zendhetmij on 2016-12-04
Last week I choose Ubuntu for my homeserver setup to learn more about linux and everything went fine, until I tried installing plex. I have read how to handle the permissions on linux filesystems, but running into the problem that I can not remove permissions from the plex webservice (proces owner is user: plex) to have access to other folders then my media folders. 

[B]My settings
[/B]

In de following example I use my download folder (this is not the download folder in the home dir).
I followed the official plex installation instruction for Ubuntu. Which gives me a plex user that runs the plex processes. The plex user is member of the following groups:
```
groups plex
plex : plex mediagrp
```

Then I checked mij download folder that has the following owner, group and permission modes enabled:
```
Ls-l
drwxrws---+ 4 downloadclient downloadgrp 4096 nov 27 16:26 Downloads
```

**Test 1: Failed**
From this I gather that that only the owner and groupmembers have access to this folder, 'others' have no access.Then I open the plex webgui from another computer and notice that the gui still has access to the download folder.

**Test 2: Succes**
When I remove the mode settings for the group (so that the group does not have any permissions, leaving only the owner with permissions) I notice the plexwebgui can not access this directory. This to certain myself of the fact that I'm not mistakenly using root permissions or owner permissions for the plex processes.

**Question**
How can I stop plex from accessing directories without having owner or group permissions?

---

### Post by TheFu on 2016-12-04
Welcome to the forums.

Which file system is the storage on?  How is is being accessed - directly or through smb/cifs?
What groups is the plex userid in?  Also, plex server might be caching some access, so restarting it might help. Also, forcing a refresh is necessary for that type of media.  Plex wants TV separate from Movies and that needs to be separate from home/unknown videos.

You are correct in thinking this is a permissions issue.
There are ACLs (denoted by the + at the end of the permissions), would be worth looking at those as well.  ACLs are like normal permissions on steroids, so you can use them to forbid plex from access.  I wouldn't solve it this way because ACLs are sort of hidden and easy to forget about.

---

### Post by zendhetmij on 2016-12-04
Thanks, you remark about the ACL sign is interesting, will check that out as soon I get home. 

I believe the other mentioned possible errors are already excluded, ill explain why I think so (maybe I forgot something, still not comfortable yet with the cli) 

The filesystem is ext4 on the server running plex (directly, not using samba/cifs)

The plex user is member of the groups: plex mediagrp (my previous message mentioned it)

There is no caching problem, because I have ofcourse tried restarting the server (coming from windows, i do that a lot ;) ).  I can navigate the filetree from plex when adding new video's and still see files that have changed since the last time. 

refreshing does not solve the fact that when adding new libraries i can navigate my file tree and can not navigate it when removing group permissions. So I excluded this from my possible errors. 

I understand how plex organizes its library, I don't think that could give these permission problems.

you mention acls, while I've read about it and understand it, I have not used them myself. If that + sign indicated they are in use I should check those as well. But thats probably not going to fix my issues. at least i can not believe acl countrers default settings, that would be very weird.... right?

Not home right now, but will check the acls tomorrow anyway, at least I have something to look further into. really dislike to leave my webstuff with to much permissions.

---

### Post by TheFu on 2016-12-04
ACLs can overrule everything.  THAT is why they are dangerous and powerful.  It is strange to see ACLs if you didn't manually add them, but perhaps the new Plex Server does this automatically to avoid all the permissions hassles that some users seem to have?  I don't know if that is the case or not.

The best way for get help would be a full listing of the parent directory and each directory for the different media types.  Just the top levels.

BTW, I just tested permissions on my Plex "video" storage and it immediately worked as expected.

```
$ ls -Fla
total 16
drwxrwxr-x  4 thefu thefu 4096 May 28  2016 ./
drwxr-xr-x 11 thefu thefu 4096 Aug 16 11:35 ../
drwxrwx---  2 thefu thefu 4096 Mar 27  2016 Misc-Family-videos/

```
See how the parent directory is 775, but the Misc-... is 770?  That is sufficient to remove Plex's access.  This is in my V3/ directory - so the 3rd disk of videos.

Definitely check the ACLs.

---

### Post by zendhetmij on 2016-12-04
Thats great news... although weird to have acl's in action its probably the problem I'm experiencing.. I'll check it tommorow, thanks for this great help so far.

---

### Post by TheFu on 2016-12-04
> **zendhetmij said:**
> Thats great news... although weird to have acl's in action its probably the problem I'm experiencing.. I'll check it tommorow, thanks for this great help so far.

I'm still guessing here.  

Running an older version of Plex here, so I haven't seen the issue you are seeing and I'm unwilling to update (I don't use the term "upgrade" anymore).  I've been burned too many times with different media stuff breaking due to updates.  My kodi playback system with PlexBMC is next to worthless thanks to an update back in October.  Just haven't taken the time to roll things back.  It was easier to load a dedicated plex client to keep others inside the house happy, but that has some huge design issues. Pressing pause on the client brings up an info-bar, which covers the subtitles I paused to read, for example.  Haven't found a way to make it go away after 1sec or move it to the top of the screen. Terrible design. Lots of complaints for years and years. No changes made.  It also ignores remote inputs sometimes. Usually it works fine, but ...   At least with Kodi, the input, pause, file-based playback, jumps, all work well.  It is nice to catch up on a game by jumping from play to play - effectively reducing a 3+ hr game into about 1 hr.   Alas, those are my issues.  

Hope this turns out to solve yours, but I'm still just guessing.

---

### Post by zendhetmij on 2016-12-07
> **TheFu said:**
> I'm still guessing here.  

Running an older version of Plex here, so I haven't seen the issue you are seeing and I'm unwilling to update (I don't use the term "upgrade" anymore).  I've been burned too many times with different media stuff breaking due to updates.  My kodi playback system with PlexBMC is next to worthless thanks to an update back in October.  Just haven't taken the time to roll things back.  It was easier to load a dedicated plex client to keep others inside the house happy, but that has some huge design issues. Pressing pause on the client brings up an info-bar, which covers the subtitles I paused to read, for example.  Haven't found a way to make it go away after 1sec or move it to the top of the screen. Terrible design. Lots of complaints for years and years. No changes made.  It also ignores remote inputs sometimes. Usually it works fine, but ...   At least with Kodi, the input, pause, file-based playback, jumps, all work well.  It is nice to catch up on a game by jumping from play to play - effectively reducing a 3+ hr game into about 1 hr.   Alas, those are my issues.  

Hope this turns out to solve yours, but I'm still just guessing.

It was an excellent guess though... 

just had time to check it and found a default mask from the root of my data drive no less that basically contained a group that granted all permissions to plex. I'm absolutely sure I have not used ACL, let alone on this computer, but there it was. Removed the group permissions (left the group for further analysis) and whola problem solved. 

from the positive side, I really think I got the linux filesystem down now ;) 

Thank you so much!!!

p.s. running ubuntu 16.10 desktop here, due to using that system both as a homeserver and NAS. Although prefereing kodi, i have plex on the nas because our tv has an integrated plex client which works great, also my family does, great for family photo and video sharing (and backups). I use the latest builds from kodi and plex which works great at the moment, as soon even stable build break hard on me, i might consider not updating those packages to often anymore like your use case.

---

### Post by TheFu on 2016-12-07
So changing the ACLs fixed the issue?

If this is solved, please mark it so using the "Thread Tools" button near the top.

---

