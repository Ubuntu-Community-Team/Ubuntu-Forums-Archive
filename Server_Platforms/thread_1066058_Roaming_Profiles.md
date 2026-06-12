---
title: "Roaming Profiles"
date: 2009-02-10
forum: Server Platforms
---

### Post by Kidwell on 2009-02-10
I have 4 Ubuntu 8.10 machines and one Ubuntu server 8.10.
What's going one:
Server contains all of the /home files.
I export /home with NFS
I mount the shares with the fstab.
Till this works 100% i also have the /home folder still on the machines

What I know:
If i login using the local /home and then mount the nfs share over that /home, everything stays the same (AS IT SHOULD) and works fine.  So i add that mount to the fstab and checkit one more time with umount -a and umount -l any of the ones that don't want to quit. check and make sure they are gone and they are, now i mount -a and everythings back and working, must work so i shutdown completely and restart.... the problem:

after restart when i try to login i get my background with a mouse.  No panels or gnome apps, can't even launch terminal, i can ctrl alt bckspc to logout but that's about it... any ideas?

i'm no pro, but i've had no problems with NFS shares before and i'm thinking this is more of a permissions thing then an NFS thing, I've made it as lax as i can to just getting running, with 777 permissions and added users to both the local and server, and making sure those users are the owners and correct groups, even NO_ROOT_SQUASH. In short i've tried many combos and nothing, looked on line for awhile but no dice, sorry if this is already posted, please redirect me if it is.  Thanks for your help!

2 months worth of Linux experience and loving it.

---

### Post by petersenmde on 2009-02-10
I don't have any experience with an NFS mounted /home directory but I have set up NFS shares.

2 things I would look at:

1. Does the user or usergroup that you are logging into the client with, exist on the server? If it does, does that user or usergroup have read/right permission on the server and on the mount point?

2. Have you copied over the .files & .directories from the client to the server?

Mark

---

### Post by ilrudie on 2009-02-10
1)  It doesn't matter if the user exists on the server or not but the UID/GID of the remote home folder will need to match that of the user on all the clients.  That means you will need to make sure your username on every client has the same UID/GID if you want this to work.  Changing your home folder to 777 could cause issues as well plus its just a bad idea.  Also depending on how the NFS mount is setup NFS can be changing the permissions and that could be messing you up.

2)  Doing this is a bad idea.  It seems really good and logical to do it but its just not.  If the server isn't on or crashes or corrupts the /home directory or any number of other things suddenly you can't log in to any of your systems.  Thats no good.  There may also be problems if you are logged in as the same user on two or more systems with lock files and multiple writes to the same file and all sorts of other nasty problems.  What ever you decide to do make sure you have 1 regular user whose home directory is not NFS mounted.  Usually this would be root but root is disabled in Ubuntu so make your own user.  Make sure that user has sudo/admin permissions as well.

3)  The traditional best practices approach is to just share the documents/music/videos/whatever that you need and mount them to some mount point.  Then you can soft link to that mount point from in your home and bingo.  Yes you have the change your settings 5 times.  Yes that is annoying.  Its still better than 1 mistake messing up all your computers.

* A comment on your title.  I'm assuming you were thinking of Windows Style roaming profiles when you were writing this post.  I have had to support windows roaming profiles.  They are garbage.  They get messed up all the time and break your account on every server that uses them.  Best practice even on this OS that attempts to support them is to NOT use them.

---

### Post by Kidwell on 2009-02-10
Well thanks for both of your replies.  I did end up doing just as you suggested, and only shared the user files and left the home local, after reading your replies it made me think about what i was trying to do, and the pleasure was not worth the pain.  So thanks again!

---

