---
title: "ls -l Permission denied for user who is in group"
date: 2007-11-03
forum: Server Platforms
---

### Post by phylae on 2007-11-03
This one really has me stumped. I have been setting up a file server using ZFS on FUSE and SAMBA on Ubuntu 7.10, and I have run into a big problem.


I have a folder /share with the following permissions:
drwxrwSr-x   9 specialuser smb     11 2007-11-03 01:40 share


I have three users in the smb group:
-specialuser
-computerab
-computera

specialuser can create files and folders within /share with no problems. However, computera and computerab cannot connect to the folder at all--not even read-only.

If either computera or computerab tries cd /share or ls -l /share or touch /share/tryme then I get a "Permission denied" error.

If I change the permissions on /share to be drwxrwxr-x then it works. However, I need the SGID bit so that new files and folders created under /share will have the group smb (so everyone else can see those files).

Here are some details behind my set up:
I am running ZFS on FUSE 0.4.0 beta1. /share is the only filesystem on a raidz1 zpool with two 500GB drives.

Samba is set up to share /share. However, the above problem exists even when I stop the Samba daemons.

umask returns 0002

I am connecting to the machine through SSH.

id for user specialuser
uid=1000(specialuser) gid=1000(specialuser) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),110(lpadmin),111(admin),1000(specialuser),1001(smb)


id for user computerab
uid=1001(computerab) gid=1002(computerab) groups=1001(smb),1002(computerab)


id for user computera
uid=1002(computera) gid=1003(computera) groups=1001(smb),1003(computera)


I'd **really** appreciate some help on this one. I am so close to getting this server all set up.

Note: I changed the usernames cuz I'm paranoid about security. :)

---

### Post by phylae on 2007-11-03
Just a quick update:

I tested this out with a new folder on an ext3 partition (my root partition). The new folder is not set up with samba either. So I guess that eliminates samba and ZFS as the cause of this problem.

Am I just totally misunderstanding the SGID bit? I thought that it meant that the group has execute permissions AND when using those permissions this folder's group is used instead of the user's default group.

Thanks

---

### Post by koenn on 2007-11-03
your chmod was probably wrong - the permissioon you set is 'S' which doesn't include 'execute' - to travers directories en get directory listings directories need to be executable - that would be 's' -- lower case. 

[http://www.zzee.com/solutions/unix-permissions.shtml](http://www.zzee.com/solutions/unix-permissions.shtml)
[http://www.library.yale.edu/wsg/docs/permissions/sgid.htm](http://www.library.yale.edu/wsg/docs/permissions/sgid.htm)

Oh - and when you test this : it only affects new files, not existing ones ...

---

Also, in your case, I suppose you could also set the GUID of all relevant users to 1001 (smb group) so all files the make are owned by the smb group- and all other members get rw permission. but you should check if  that affects the possibility to sudo (~admin group)

---

### Post by phylae on 2007-11-03
Thank you! Thank you! Thank you!

That was exactly my problem. I guess I assumed that `chmod g=rws /share` would do the trick. But even though I typed a lower case `s` it still entered it as upper case. I exectuted `chmod g+x` and now I have the lower case `s` and everything works. (Well not *everything*, but at least this problem is solved.)

---

### Post by koenn on 2007-11-04
good to hear that  
- I mean the problem that's solved, not that there are a few remaining  :)

---

### Post by pmorton on 2007-11-11
I have a similar problem - perhaps my confusion - which doesn't involve the guid. 

I have a folder /public  with permissions:
drwxr-x--- 19 root users  4096 2007-11-10 22:06 public

There are two  users in the users group:
-pc1
-pc2

but if either  tries to cd /public or ls -l /public   or touch /public/foo  then he gets a "Permission denied" error. It's as if the group permissions aren't working at all.

Changing the permissions to drwxr-xr-x allows pc1 and pc2 access to the /public folder and listing of its contents.

I tried this on another Gutsy machine, and drwxr-x---  allows members of the 'users' group to enter and view the folder as expected, which is even more puzzling.

---

### Post by pmorton on 2007-11-11
A restart has sorted this. I was working with a new install, so that may be all it was.

---

