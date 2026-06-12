---
title: "Ubuntu Server Samba and Windows ACLs"
date: 2009-10-14
forum: Server Platforms
---

### Post by H.Callahan on 2009-10-14
Where can I find detailed information on using Windows ACLs with Samba on an Ubuntu server?

I am trying to set up a file server for a, up to now, 100% Windows LAN.  I have set up the server, Samba, and the shares.  In a basic fashion, everything works.  I can map to the share, create files, change files, delete files, etc.  However, I need to be able to set security permissions for different users and groups from within the Windows environment and have them be honored by Samba when accessed by other Windows machines.

Most of the information that I have found is either very old (recompiling the kernel or Samba for ACL support) or are specific to a flavor of Linux other than Ubuntu.  Also, none of the information really presents the information in an manner that would allow someone to get from ground zero to a finished installation if one has never done it before.

I need some help here.

TIA

---

### Post by SteveDee on 2009-10-15
There may be something here that could help you: [http://ubuntu.swerdna.org/ubusambaserver.html#dbase](http://ubuntu.swerdna.org/ubusambaserver.html#dbase)

---

### Post by H.Callahan on 2009-10-15
Thanks for the link.  It had some good information that I didn't know about that I think I can use for some other things, but it is not really what I am looking for.  I need to know how to set up Samba so Windows ACLs work correctly.

---

### Post by cariboo on 2009-10-15
Moved to server platforms, as you will probably get better answers to your questions here.

---

### Post by H.Callahan on 2009-10-16
> **cariboo907 said:**
> Moved to server platforms, as you will probably get better answers to your questions here.

Cool.

Thank you.

---

### Post by H.Callahan on 2009-10-20
Anyone?

---

### Post by Pnuts on 2009-10-20
I believe it was covered in a book I have, "[A Practical Guide To Ubuntu Linux]("http://www.amazon.com/Practical-Guide-Ubuntu-Linux-Versions/dp/0137003889/ref=sr_1_1?ie=UTF8&s=books&qid=1256057678&sr=8-1")"

I'll have to verify when I get home tonight (hopefully i remember to check) but I think it was pretty simple.

You just enable ACL for the partition on which you are going to use it on. Then in the ACL file user DOMAIN\USER (assumes you already added the Linux box to the Windows Domain)

Actually, a quick search brings back this page: [http://samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id2613463](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id2613463)

Says you can even use windows security dialog box's if you want instead of editing the ACL files manually.

-Pnuts

---

### Post by koenn on 2009-10-20
> **H.Callahan said:**
> I need to be able to set security permissions for different users and groups from within the Windows environment and have them be honored by Samba when accessed by other Windows machines.

you're a bit vague about where those user and group accounts will come from.

If it's an Active Directory Domain, try this for a quickstart guide : [http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm)

In any case, what you're looking for is posix ACL - current Linix/Samba/ext3 versions support this, the required packages are in the Ubuntu repos.

---

### Post by H.Callahan on 2009-10-21
Ok, let me explain a little more.  

We are a small to medium sized operation, 100% Windows.  We are currently peer to peer -- no Active Directory, workgroup based only.  As we are non-profit and in this economy, we have virtually $0 to accomplish things around here.  Up to now, our Board of Directors has been vehemently anti-Linux.  However, we have a need for an plain old vanilla file server.  I have some unused computers sitting around from an upgrade we did over the summer.  I would dearly love to get Linux's nose in the tent, so to speak.

I think I can convince the board that we can actually spend no (additional) money an put up a file server that one of our departments really needs.  However, I need to behave as much like a Windows Server as possible at least in the area of ACLs.  We administer rights to files/directories using the Windows Security dialogs to a Windows Server 2000 machine and to a couple of NAS devices being used as file servers.

As a test, I have set up Ubuntu Server 8.04 LTS on one of these boxes, installed Samba, configured it and am able to attach to it from a Windows machine.  I can create and delete files and access them without a problem.  Where I am getting tied up is in setting up access rights for the directories and files using the Windows Security on the Ubuntu box.  For example, when I open the properties box, I a listing for "Everyone" (with RO access), my login to the server (with full control), and the Samba group (I am using "force group" in smb.conf) (with RO access).  I have created other users on the Ubuntu Server and registered them with Samba.  They can log into the server and create and delete files just fine, as well.  Opening up a security dialog shows the same thing as a file I created, except that their login to the server is listed rather than mine.  The problem comes when I try to add additional users to the security listing so that I can give other users access to a file not created by them.  

Let's say have I have three users -- Tom, Dick and Harry (me).  I create a file on the server.  I have Full Control of the file by virtue of the fact that I created it.  I also want Tom, my trusty sidekick, to have full control over that file, as well.  However, I want Dick to have no access at all.  I create the file.  I try to add Tom to the ACL and I can't do it.  I am told "An object named 'Tom' cannot be found. Check the selected object types and location for accuracy and ensure that you typed the object name correctly, or remove this object from the selection.  Same situation for adding Dick.  Consequently, I can not give Tom RW access to the file and I can not block Dick from having any access at all.  Both of them have RO only by the fact that I am forcing everyone to use the same group in smb.conf (I tried removing that restriction and it didn't help the situation any).  I can change to group access to RW and both have RW access or I can set it to None and neither have access to the file.  However, I can not control access by any other mechanism other than group (and Everyone, of course) and only when I force the group in smb.conf.

What I need to know is how to set it up so that I can control access to files and directories by user login.  Additionally, I would like to get rid of the force user and also be able to control access by groups as well, but that would be a secondary consideration.

Oh, I have also enabled ACLs in Ubuntu both at the file system level (in /etc/fstab) and in Samba (smb.conf) in case that gets brought up.

---

### Post by koenn on 2009-10-21
when you have samba and posix acl, you'll be able to manage ACLs through the Security Dialog on the share, from Windows, just like you could with a Windows file server. It does help if you keep in mind that Microsoft ACl are not completely POSIX compliant - read 'man setfacl' to understand how things work from the Linux side as well, it sometimes helps to understand things


For your user problem :
As you don't have a domain or an other form of central user management, your users are local to the file server. This means you need to create user accounts (and groups) on the server itself. You'd have to do the same if this was a Windows file server, right ? 

You can create them with the command "smbpasswd -add username'. These are NOT Linux user accounts. You may need to create linux user accounts for the same users as well - the account names will be the same but they will be separate entities. 

You also have to set the samba security model ('user' I think, but you need to check).

When this works, The security dialog should recognise your samba users - you may have to use the search function (location = your server) to get them.
If this works,  you can try groups as well.

It's probably best you read up on this in the official samba documentation
or find one of their recipes that matches your situation. 

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html)

---

### Post by H.Callahan on 2009-10-22
> **koenn said:**
> when you have samba and posix acl, you'll be able to manage ACLs through the Security Dialog on the share, from Windows, just like you could with a Windows file server. It does help if you keep in mind that Microsoft ACl are not completely POSIX compliant - read 'man setfacl' to understand how things work from the Linux side as well, it sometimes helps to understand things
I am aware of that aspect.  However, I did not read anywhere that ACL entries could not be made for individual users.  All I really need is in the way of access is NONE, RO and RW.  But, I DO need them to be able to be applied in different combinations  for different users.
> **koenn said:**
> For your user problem :
As you don't have a domain or an other form of central user management, your users are local to the file server. This means you need to create user accounts (and groups) on the server itself. You'd have to do the same if this was a Windows file server, right ?

You can create them with the command "smbpasswd -add username'. These are NOT Linux user accounts. You may need to create linux user accounts for the same users as well - the account names will be the same but they will be separate entities. 
Correct.  ...and I HAVE created a test set of users on the Linux box and added them to the Samba users' database. 


> **koenn said:**
> You also have to set the samba security model ('user' I think, but you need to check).
Yup.  ...and already done.

> **koenn said:**
> When this works, The security dialog should recognise your samba users - you may have to use the search function (location = your server) to get them.
If this works,  you can try groups as well.
This is where the wheels fall off the wagon.  I can not add users and when I search for them, I get the message "An object named 'xxxxx' cannot be found. Check the selected object types and location for accuracy and ensure that you typed the object name correctly, or remove this object from the selection."  This is in spite of the fact that the user does exist and is part of the Samba users.  I can log in to the Samba server with that user and that user can create, edit and delete files. 

> **koenn said:**
> It's probably best you read up on this in the official samba documentation or find one of their recipes that matches your situation.

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html)
I think I have been through that page, but I will check it again, just to be sure.

---

### Post by koenn on 2009-10-22
hm ... difficult. I have a working samba with posix ACL that I can manage with Windows Security Dialog, but it's an AD integrated samba, so it uses domain accounts. Works as expected.

I have an other samba with security=user, but it doesn"t have Posix ACl so it has only the user/group/other permission bits (and a representation of that visible in Windows ' security dialog)

So I can't test/search where your setup goes wrong (unless I setup Posix ACL on that 2nd box, but I was not really planning to).


Couple of ideas :
* you're absolutely sure you have Posix ACL working ? It should be visible when you run ```
mount
```. Could you post that output ?

* do the posix acl work when you use them on the linux box, i.e. with setfacl and getfacl i.s.o windows gui ? 

* ( Longshot: )You might have to give user account names in the form LOGONDOMAIN\username or LOGONDOMAIN\\username,, where LOGONDOMAIN is the hostname of the SAMBA server.

---

### Post by H.Callahan on 2009-10-22
```
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda3 on /media/Vol1 type ext3 (rw,relatime,acl)
securityfs on /sys/kernel/security type securityfs (rw)

```
/dev/sda3 is the Samba share.

---

### Post by koenn on 2009-10-22
looks OK to me.
Have you tried reading ACL with getfacl or editing them with setfacl ? Does that work ?

---

### Post by H.Callahan on 2009-10-23
> **koenn said:**
> looks OK to me.
Have you tried reading ACL with getfacl or editing them with setfacl ? Does that work ?
It appears to.  Sample output from getfacl on a file on the share.
```

# file: test.txt
# owner: Harry
# group: SambaUsers
user::rw-
group::r--
other::r--

```

---

### Post by koenn on 2009-10-23
yes, but it shows nothing but the ordinary linux user(owner)/group/others permissions.

can you add one, eg 
```
setfacl -m u:Tom:rwx /path/to/test.txt
```

does that work ? can you see the change with getfacl ? and from Windows ?

---

### Post by ukripper on 2009-10-23
i know you are not looking for PDC but you will find plenty of useful info in this thread in regards to samba - [http://ubuntuforums.org/showthread.php?t=1184288](http://ubuntuforums.org/showthread.php?t=1184288)

---

### Post by H.Callahan on 2009-10-23
> **koenn said:**
> yes, but it shows nothing but the ordinary linux user(owner)/group/others permissions.

can you add one, eg 
```
setfacl -m u:Tom:rwx /path/to/test.txt
```

does that work ? can you see the change with getfacl ? and from Windows ?

getfacl from the server:
```
# file: test.txt
# owner: Harry
# group: SambaUsers
user::rw-
user:Tom:rwx
group::r--
mask::rwx
other::r--

```

And, yes, I can see user Tom in the Windows Security dialog and manipulate his settings and those changed settings are reflected in the Samba server's ACL.  However, interestingly enough, I can not delete Tom from Windows.  It appears to work, but the deletion does not propagate to Linux -- and if I close the Windows security dialog and then reopen it, Tom shows up again.

I can still not add anyone from the Windows dialog.

---

### Post by H.Callahan on 2009-10-23
> **ukripper said:**
> i know you are not looking for PDC but you will find plenty of useful info in this thread in regards to samba - [http://ubuntuforums.org/showthread.php?t=1184288](http://ubuntuforums.org/showthread.php?t=1184288)
Good stuff!

I would like to do this in the future.  The problem is two-fold.  One, we are a non-profit organization and in this economy, we really have virtually no money to do anything.  Secondly, so far, our Board of Directors has been vehemently anti-Linux.  Since this file server is needed badly and there is no money to do it in a Windows-only environment, I am hoping that the Board will see this as a viable alternative and in-so finding out that Linux is not the devil.  The server, though, needs to be fairly transparent to the staff (who will be using only Windows) for it to be acceptable.  If I can get past that and get Linux in the door, I may be able to do a lot more for little money here.  Having a domain would be one of those things.

---

### Post by koenn on 2009-10-23
> **H.Callahan said:**
> 
And, yes, I can see user Tom in the Windows Security dialog and manipulate his settings and those changed settings are reflected in the Samba server's ACL.  However, interestingly enough, I can not delete Tom from Windows.  It appears to work, but the deletion does not propagate to Linux -- and if I close the Windows security dialog and then reopen it, Tom shows up again.

I can still not add anyone from the Windows dialog.
Interesting.
Well, I don't know then. I haven't done workgroups since windows 98 so I'm not sure where to look next. Sounds like a communication problem between Windows and Samba (eg in deleting the user from the ACL), or a protocol question (eg in Windows not being able to read a list of users off the server). 

One last thing you could try is editing the ACL from the 'Advanced' section of the security dialog and see if that makes a difference. I've experienced that some settings against a samba server didn't work from the basic view, but were manageble in 'Advanced'. Maybe worth the try.

Other than that, hopefully we've narrowed it down sufficiently for someone else to help you further, or for you to know where to start looking for  more help (maybe a samba forum ?)

Or you could work around it, eg if you add / remove users to the ACL with a sensible default, your colleagues/users might edit them further.

Since your just testing, do consider trying the PDC approach. It won't cost you anything extra, and might help solving this problem because domain users are known to the domain, not just to the server.  And an NT4 style domain is pretty simple - it's like a workgroup with centralised user accounts. 

GL & HF

---

### Post by H.Callahan on 2009-10-26
> **koenn said:**
> Interesting.
One last thing you could try is editing the ACL from the 'Advanced' section of the security dialog and see if that makes a difference. I've experienced that some settings against a samba server didn't work from the basic view, but were manageble in 'Advanced'. Maybe worth the try.

Same results.  I can edit the permissions for an existing user, but can not add or delete one.

> **koenn said:**
> Since your just testing, do consider trying the PDC approach. It won't cost you anything extra, and might help solving this problem because domain users are known to the domain, not just to the server.  And an NT4 style domain is pretty simple - it's like a workgroup with centralised user accounts.
I might play with it, but I doubt I would (initially) get that solution past the Board.  It would require too many changes to the current setup and would require a reliance on Linux for day to day things to work.  I don't think that would fly.  I was hoping to get Linux in on a low risk project and then, after time, be able to point to the server in that it has been reliable and request being able to try something like a PDC for the operation.

---

### Post by suresh.kandukuru on 2010-09-03
[Dear Callahan ,]("http://ubuntuforums.org/member.php?u=561336")
                 I am also facing the similar issue as yours. Can you please tell me how did you fix this problem?.

I am anticipating you replay

Thanks in advance
Suresh
[]("http://ubuntuforums.org/member.php?u=561336")

---

### Post by H.Callahan on 2010-09-03
Unfortunately, I never really could come up with a totally successful resolution to this.  Basically, I abandoned the concept and had to go with Windows.

---

### Post by ukripper on 2010-09-03
> **H.Callahan said:**
> Unfortunately, I never really could come up with a totally successful resolution to this.  Basically, I abandoned the concept and had to go with Windows.

Sorry to hear that!

---

