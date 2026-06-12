---
title: "Torrentflux Users integtated with Linux Users"
date: 2010-01-18
forum: Server Platforms
---

### Post by Anaximander Thales on 2010-01-18
Hello Masters,

I have decided to set up a NAS with torrent seedbox with Ubuntu Server 9.10.

Everything is currently working the way it should.

However, in my investigation to find a multi-user torrent client, I came across an article that I would like to now implement.

I am using torrentflux-b4rt with BitTornado as the back end.  The article I came across was for integrating the linux users in to the torrentflux user list.  Now, whether this occurred or not, I'm not sure.  I thought I had bookmarked the article, but I didn't.  And now I'm not able to find it in Google -- just can't find the right list of word to search for and not search for.

What I am exactly looking for is this.  I have a list of users on the server.  I'd like for the users on the server to be imported and set up in torrentflux.

I would like to do this so that each individual user can download to their home directories.  Currently, they download to a public directory that's available to everyone.  

Just to illustarte --
Currently:
UserA has an account on the server.  UserA logs into tf-b4rt, and starts a torrent d/l.  Download finishes, they open up their samba mapped public folder (//server/public) from their windows box. UserA now can open UserA, UserB, UserC and any other folders listed in 'public'.

What I want:
UserA has an account on the server.  UserA logs into tf-b4rt, and starts a torrent d/l.  Download finishes, they open up their samba mapped home folder (//server/UserA) from their windows box and copy their d/l to their computer (or whatever else they want to do with it now).

So, I'm wondering if any person has done this or if it's possible, and what would I need to do to integrate the linux users into tf-b4rt and to have tf users d/l to their home folder.  I'm flexible on integrating the user logins, but I really want them to d/l to their home folders.

Thanks,
AT

---

### Post by Anaximander Thales on 2010-01-23
Bump??

---

### Post by buntunoob on 2010-01-28
It sounds like you've done the hard part(installing and setting up the users TF and Samba)
I know that it will d/l to each users own folder, I don't rember if you could Specify the path thou or if the user could CH mod from TF to get Access to the Files that have been D/L). 
ahh.... if I do rember right they can d/l stright from the TF gui thou..

---

