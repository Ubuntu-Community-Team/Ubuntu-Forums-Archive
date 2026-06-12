---
title: "Best Practice for User and Group file Storage"
date: 2007-02-14
forum: The Cafe
---

### Post by rverrips on 2007-02-14
Hi

I'm running a samba server pretty happily in my establishment and all my 400+ non-Linux clients are connecting to the network shares without a problem.

My shares are devided into three seperate areas:

home - (i.e. %username%) Only the logged in user has access to this folder (i.e. private)
group - User has access to this share folder as does the rest of his/her department (14 department throughout the organisation) 
share - All users in the organization can access this shared folder

The idea was that users would save private stuff in home, things they work on together as a department in group, and files relevant to the entire organization on share.

The principle works, but after five years we have numerious files in group and share with no real "ownership" as the users have moved departments or left the organization, and deleting their "home" leaves the other files intact: Some files of deleted users we may want to leave on the group and share drives, and sometimes not.  

Also, some files in the Group and Share folders need to be read-write 'cause the users work on them together, and others are to be read-only, so no-one damaged information that's for other users benefit

A daily task I also have is "move" sub-folders that were accidently dragged/dropped by a user with a sticky mouse.  

I've tried to setup the Group and Share drives as read-only by default, and users then need to change the permissions themselves, but this hasn't had successful results.

My "vision" is to have four folders off each users home drive, called Group-RO, Group-RW, Share-RO, and Share-RW.  If they put files in each I've like it to symlink (or hardlink) to a "virtual" Group and Share Drive

So I see the possible solution to be that I then need to either run a script to automatically create the links (and subfolders) in the Group and Share drives from each user drive, and create them with limited access.  

The script would also need to account for subfolders as the creation of a file in a subfolder i.e. someuser\Share-RO\subfolder\second.txt would need to put the symlink in the same subfolder as someotheruser\Share-RO\subfolder\first.txt

Removing a user would then mean I'd need to tidy up the dangling symlinks though.

Is this the best solution?

---

### Post by kidders on 2007-02-14
Hi there,

Your scheme is interesting, but it has two major drawbacks:

[LIST]
[*]It would be quite labour-intensive to administer.
[*]In order to find something, people will have to start thinking about what they're looking for in terms of what sort of access privileges they think they might have to it.
[/LIST]

I may be wrong, but it looks as though the major issue is that, by default, Samba won't cooperate when a Windows user right-clicks a file, opens up its properties, and starts tinkering with access control. Samba & Linux *can* be made to support ACLs though, which would allow you to maintain your current, simple filesharing system *and* give users finer-grained control over who can do what with their files.

Would that be any use?

---

### Post by rverrips on 2007-02-14
Thanks for the prompt reply Kidders'

> **kidders said:**
> 
I may be wrong, but it looks as though the major issue is that, by default, Samba won't cooperate when a Windows user right-clicks a file, opens up its properties, and starts tinkering with access control.

Actually, the problem existed before Samba - I simply migrated the existing "shared" folders from a Windows 2000 server - It's only now that I have the ability to use links and symlinks that I'm hoping for a better solution.  

Right-clicks work fine on my Samba implementation and the authentication is seamless against the existing Active Directory structure.  The problem is my users store all their files on the network (hot-seat environment) and most don't realise the access possibilities available or how to manage access controls (i.e. right-click, etc)

I'm hoping that the Group and Share drives can include all files symlinked from all the user home folders and users simply need to decide if the files in the Group folder are with RW or RO rights ... 

Am I hoping to simplify it too much for the users, and in doing so complicate it too much for myself?

---

### Post by Omnios on 2007-02-14
I havent played around with samba much but users and groups allow for some interesting stuff. It may be possible to make a root like group with prives that you want and add a second user as a group. SO say George and george home. Now george would be a full featured user and geoge home will be entered as a group for george though the same user. As a group user you can set up different access levels for george and george home as group provies. I recently set up document drives for my Dad and My step mom this way and it worked rather well. Basicly by playing around with users etc and there groups you can be fairly flexable.

---

### Post by rverrips on 2007-02-14
> **Omnios said:**
> I havent played around with samba much but users and groups allow for some interesting stuff. It may be possible to make a root like group with prives that you want and add a second user as a group. SO say George and george home. Now george would be a full featured user and geoge home will be entered as a group for george though the same user. As a group user you can set up different access levels for george and george home as group provies. I recently set up document drives for my Dad and My step mom this way and it worked rather well. Basicly by playing around with users etc and there groups you can be fairly flexable.

Thanks for the idea's Omnios, but the problem isn't so much which Group priveliges to assign to a user as it's the various privelges per file, i.e. some files are to be Read Only, and other Read-Write - I need a simple mechenism to allow the user to select this, but can't think of a better way then having folders in this "home" drives that apply the priv's and symlink to a central location?  

I will however change Prives per Group so that on the Group drive, only the users of that Group get either RW or RO writes to the file(s) in question, thanks for pointing that out!

---

### Post by kidders on 2007-02-15
Hey again,

I think I'm getting a better understanding of what you're looking for. It sounds like you want to be able to guess & then automagically assign the access restrictions you place on a file based on its location within a person's own home directory. I can't help feeling that administering such a system would be an absolute nightmare though!

Let's imagine you have two users and one shared volume called "World-RW", fully accessible by everyone in the office, that looks like this...```
file1 -> /home/user1/World-RW/file1
file2 -> /home/user2/World-RW/file2
```
A few issues spring to mind:
[LIST=1]
[*]It's a little counter-intuitive (I can't help wondering if it would cause problems) that user1 would have full read/write access to a file in a directory whose parent he has no access to whatsoever (user2's home).
[*]What if both user1 and user2 try to make modifications to file2 at the same time?
[*]What if user2 deletes file2 while user1 has it open? When user1 saves his changes (naturally, he will receive no indication that the underlying file has been deleted, since the symlink will still be in place), he will either succeed (which would be a disaster, as the file would now not be living in anyone's home) or perhaps fail (because a dead symlink was using the desired filename).
[*]The publicly accessible "World-RW" share would be perpetually out of date, as the moment all the symlinks are updated, they would already be old news.
[*]What if user1 and user2 were both sharing a file called "file1"?
[/LIST]

This may not quite meet your needs either, but I'd be interested to hear what you think...

[LIST]
[*]A script runs as root on your file server once every 10 minutes.
[*]If necessary, it (re)creates directories in each user's home called "Group-RO", "Group-RW", "World-RO", "World-RW".
[*]Any files found in any of those directories is actually moved to public access shares by the same names, so that they no longer reside in users' homes. (The directories are, in effect, dropboxes).
[*]Windows messaging is used to inform users who've dropped something in one of the four dropboxes of the status of their files. They would maybe see something like "25 files exported successfully. 1 failure. You can't use the name 'file1', as it is already in use.".
[*]Files that failed to move for some reason would simply be left in the user's home until they resolved whatever was wrong.
[*]The script would, of course, rewrite all file permissions appropriately, based on the name of the directory they came from (eg "Group-RO").
[/LIST]

The big issue with something like this is that the creators of documents destined to be read only would effectively lose access to something they should really be allowed to alter. One possibility might be to always allow read/write access to the original owner of a file, by "chmod u+rw"-ing it, even if it lives on a read-only share.

Something else worth considering might be "expiring" files. Stuff that has been living unaltered on a public share for, say, 3 days could be automatically trashed, and then (maybe after 30 days) eventually erased. The script would maintain a list of files (eg a read-only grievance policy document) that would be exempt from your "recycling" programme. That way, people could freely share revisions to files (by calling them something like "file1 2007/02/11", "file1 2007/02/15", etc., happy in the knowledge that the long trail of revisions would be automagically cleaned up. Users could perhaps add items to the "do not delete" list by emailing a script (rather than an actual person) with the name of the file.

Anyhow, I suppose the bottom line is that I can certainly (from experience!) appreciate your need to have some way of second-guessing your users' filesharing intensions. There must surely be a smart way to achieve the effect you want at a price (administratively speaking) you're willing to pay! With luck, you, Omnios & I will figure one out.

---

### Post by rverrips on 2007-02-15
> **kidders said:**
> 
I think I'm getting a better understanding of what you're looking for. It sounds like you want to be able to guess & then automagically assign the access restrictions you place on a file based on its location within a person's own home directory. I can't help feeling that administering such a system would be an absolute nightmare though!

It's a nightmare managing the system as it is - I can't see it getting any worse - An Ehl of a lot more complicated, but not worse :-)

> **kidders said:**
> Hey again,
Let's imagine you have two users and one shared volume called "World-RW", fully accessible by everyone in the office, that looks like this...```
file1 -> /home/user1/World-RW/file1
file2 -> /home/user2/World-RW/file2
```A few issues spring to mind:[LIST=1]
[*]It's a little counter-intuitive (I can't help wondering if it would cause problems) that user1 would have full read/write access to a file in a directory whose parent he has no access to whatsoever (user2's home).
[*]What if both user1 and user2 try to make modifications to file2 at the same time?
[*]What if user2 deletes file2 while user1 has it open? When user1 saves his changes (naturally, he will receive no indication that the underlying file has been deleted, since the symlink will still be in place), he will either succeed (which would be a disaster, as the file would now not be living in anyone's home) or perhaps fail (because a dead symlink was using the desired filename).
[*]The publicly accessible "World-RW" share would be perpetually out of date, as the moment all the symlinks are updated, they would already be old news.
[*]What if user1 and user2 were both sharing a file called "file1"?[/LIST]

I need to do some testing on this - Firstly, I believe symlinks negate the issue of parent folder rights ... they'd have to otherwise my whole idea of symlink out of privately maintained home folders into a publich "pool" of files will not work.  

Futher, with regard mutliple accesses, I believe the files that are being opened are "locked" as such, i.e. a user get's a prompt when he/she opens a file that's opened by another user, and they get's read-only access - This was the behaviour on the Windows shares, I'm not sure if Samba replicates this directly, but I can't think that it wouldn't?

Suffice to say I was thinking of my "script" solution in terms of a situation where the file would only be accesible by one user at a time - I'll confirm this in the next few days though (Weekend here in the Middle east on Friday and Saturday)

> **kidders said:**
> 
This may not quite meet your needs either, but I'd be interested to hear what you think...
[LIST]
[*]A script runs as root on your file server once every 10 minutes.
[*]If necessary, it (re)creates directories in each user's home called "Group-RO", "Group-RW", "World-RO", "World-RW".
[*]Any files found in any of those directories is actually moved to public access shares by the same names, so that they no longer reside in users' homes. (The directories are, in effect, dropboxes).
[*]Windows messaging is used to inform users who've dropped something in one of the four dropboxes of the status of their files. They would maybe see something like "25 files exported successfully. 1 failure. You can't use the name 'file1', as it is already in use.".
[*]Files that failed to move for some reason would simply be left in the user's home until they resolved whatever was wrong.
[*]The script would, of course, rewrite all file permissions appropriately, based on the name of the directory they came from (eg "Group-RO").[/LIST]

This "grab and correct" script would solve my user permission problem beautifully, but again, lack of ownership would be a problem - If the files have been moved from the users home drive he's not going to "maintain" it anymore.

My challenge as I see it is that some files are worked on by perhaps 10 or more people at different stages, but in a GROUP area no-one takes actual responsibility for it.  If the user has it in his/her home drive that "ownership" is a forced one.

The idea of expiring files is a good one though, but I've a feeling I'd need to implement a timeframe more to the likes of 3 months not activity = "holding" area - 18 months in holding area = Trash ... Some files are not touched for about 8 months, and then become very active for a month or two, and then lie dormant for months again. (contracts prepared in advance for future work etc.)

I'll keep thinking about it and perhaps get some sample scripts running and see how it goes ... 

Thanks for your input, it really is getting my thinking towards what I'm hoping will be a really "sweat" solution ...

---

