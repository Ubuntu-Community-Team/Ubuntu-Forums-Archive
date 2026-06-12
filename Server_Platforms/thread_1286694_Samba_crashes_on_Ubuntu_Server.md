---
title: "Samba crashes on Ubuntu Server"
date: 2009-10-09
forum: Server Platforms
---

### Post by danooch13 on 2009-10-09
Hello,

I have an ubuntu fileserver setup running 9.04, with the latest samba to date.  I have a share setup, which is open to everyone and anyone can do anything.  It is a private network in my house which windows clients around the house connect to.  

I have been having a problem where at first I thought samba was crasshing with only big files, then last night it crashed just opening a picture.  What happens, to describe the issue, is I open the share on a windows xp client (now just using unc path //server/blah), and browse around the files.  I opened a directory with pictures, and started to browse them, got to one picture, and it just locked up the entire windows machine, and I had to kill a bunch of processes on the windows machine to get it going again.  This also happens when I copy big files.  Sometimes it actually requires me to restart the samba process on the linux server, sometimes I cant even do that, the entire server becomes unresponsive.  I am not sure what is going on.  My server is not using any swap space, so I dont see it being a memory issue.

Possibly something wrong in my config?

Any ideas?  

Thanks.

---

### Post by ghostborg on 2009-10-09
I remember something weird (Highly Tech) about the location of the shared files on XP. Try creating a shared folder (ex C:\MyTest ) outside of the MyDocuments. I never figured out why. Hope this helps.:confused:

---

### Post by danooch13 on 2009-10-09
I appreciate the input, but you may have misunderstood my problem.  The share is created on the ubuntu samba server, so for example samba shares the path /srv/files to everyone.  A windows machine will connect to the samba share, and as stated in the examples above, it crashes from time to time, with different behaviors each "crash".  Sometimes the ubuntu server just dies, sometimes the windows machine crashes, sometimes they both do, and sometimes, it is just a temp freeze for like 10 min on the windows machine, I just kill the task on the windows machine, then try again and it works fine.

---

### Post by danooch13 on 2009-10-09
bump

---

### Post by danooch13 on 2009-10-11
Any ideas?

---

