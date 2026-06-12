---
title: "Can NFS be configured to replace AFS for remote home mounting?"
date: 2009-12-28
forum: Server Platforms
---

### Post by tarekeldeeb on 2009-12-28
Hello all,

I'm currently administering a 10-PC ubuntu lab, with 1 server.
Users have their home NFS mounted from the server.
The server has some heavy-processing tools that may be run by any user. When this happens, other users find problems accessing their home folder due to the too busy server.

Some friend told me about AFS; it seems to be a better solution. When a user logs-in, his home is copied to his local machine. When he logs-off the home folder is returned back to the server and stay in sync. This unit of storage is called 'cell' in the AFS systems.

Did any of you try to configure NFS to export async /home and let clients cache their home folders locally? What happens if the server becomes temporarily unreachable? Can anyone advise me about my situation?

Thanks in advance,

Tarek

---

### Post by Lars Noodén on 2009-12-28
Actually the unit of storage your friend is talking about, for the home directory, would be a 'volume'  You would set up a 'cell' for your site and, maybe, use one volume per user or per arbitrary set of users.  

AFS is originally designed to work with about 200 clients per server.  It can have increased.  

NFS is centralized.  AFS is decentralized.  If you plan to start having people work in different locations, then AFS might be worth considering.

---

### Post by Lars Noodén on 2009-12-28
> **tarekeldeeb said:**
>  What happens if the server becomes temporarily unreachable? Can anyone advise me about my situation?


Well with no network, with NFS you are SOL.  

AFS caches locally, but isn't designed work disconnected.  Work on a successor to AFS was called Coda, but a number of factors including a certain politician with the initials BG started to interfere at the research centers working on it.  Computer science and development seems to have mostly dried up and blown away starting around 1999.  

Work on [Coda](http://www.coda.cs.cmu.edu/) seems to be ongoing, but I myself haven't had a chance to test it for many years.  There aren't really any new publications, unless you write one, but the files are available for download.  

Give it a try but don't expend major effort unless it looks like it is working for you in your tasks.

---

### Post by tarekeldeeb on 2009-12-28
> **Lars Noodén said:**
> 
Work on [Coda](http://www.coda.cs.cmu.edu/) seems to be ongoing, 

Ubuntu's repos has openAFS, but not coda..


Anyway, I see the difference between NFS and AFS. It seem that AFS is better for my situation. I will give it a try.

thanks

---

### Post by Lars Noodén on 2009-12-29
Cool.  

OpenAFS works very smoothly with Kerberos for authentication and OpenLDAP for group membership.  So if you can, try to integrate them in the beginning before you start pilot projects.

Random comments on AFS:

The [AFS and Kerberos Best Practices Workshop 2010](http://workshop.openafs.org/afsbpw10/) will be held May 24-28, 2010 at the University of Illinois at Urbana-Champaign.  As with any conference next year, don't take any guff from [shills](http://www.techcrunch.com/2009/12/15/microsoft-recruits-student-bloggers-with-free-software-and-trips-to-conferences/), even ones disguised as students or their friends.  

Look into replication of volumes for backup and fail over.  

For the linux AFS client, you will need to compile a module which is not a big deal, but if you do a lot of installation or want to encourage others on your site to do so, then you might publish it somewhere in a signed repository.  For macintosh, installation of the client is drag and drop.  For either, radmind might help with lab maintenance once you have a client setup that you like.

Permissions can be managed with ACLs or Protection Server (PTS)  groups if more than 20 groups must have different permissions for the directory.

Access control for AFS is done at the directory level so if a file needs different permissions then it must be in its own directory.

You can make a drop box for users by granting **i**nsert permission to the group allowed to use the drop box.  No other permissions. 

**l**ookup permission will be needed in a parent directory to allow passthrough to child directories even if the child directory grants more permissions.  This would be important use if you have a Public/www directory for the user's web documents.  

You can view other AFS sites and make some visible by default.  If you use cross-domain authentication (or what ever it is called now) you can share files via AFS around the world.

---

