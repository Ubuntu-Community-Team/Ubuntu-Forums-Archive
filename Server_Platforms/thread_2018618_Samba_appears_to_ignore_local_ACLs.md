---
title: "Samba appears to ignore local ACLs"
date: 2012-07-06
forum: Server Platforms
---

### Post by fleder on 2012-07-06
I am currently setting up a new Samba file server.

I already have one, this new one is going to be used to back up stuff from the productive file server, and to test things and so on.

The productive one works all right, except that it's a bit of a dirty job.
The smb.conf is hand-written, and there are no ACLs in the file system, and I have some user/group/other permission clean-up scripts that I run when there are problems with editing or changing files on the shares with the SMB clients, which usually happens when I locally create a new file on the shared directory.
It works, but I'm under the impression that this can be done better.

The permission script stuff is what I want to get rid of on the new file server for good. If I am to modify or create files locally on the server, I don't want to recursively set any permissions or ACLs to allow the SMB clients to change these files.

I started out with a simple task: Provide a shared folder where everybody can read and write everything without authentication, i.e. using Samba's guest account, and also being able to edit the files that I create when I'm messing around on the server itself.
Anyone must be able to do anything with any files there are, regardless of who created them.

The file server is a headless system, and I use an automatic login that provides me with a VNC server to the physical display. This is the user "autologin". That's the one I'm using when I modify files locally.

Then there's the system management user, the one that was created during the installation of Ubuntu 12.04, "superuser".

For the Samba guest access I created a user named "smbguest".

Each one of those users has its own primary group with its name being identical to the user's name.

The shared directory is /media/raid/networkdrive, and I set it up like this:

[IMG]http://fleder.dyndns.org/permshare/samba.acl.problem/networkdrive.ls-l.getfacl.png[/IMG]

The point being that everything that is created will inherit an ACL allowing autologin, superuser and smbguest to modify it, regardless of the owning user and group.

This works very well locally. I can create a file with smbguest that has the smbguest user and group as owning user and group, and can painlessly rename or delete it using the autologin user.

The problems start with Samba (surprise, surprise :-/ ).
I can create folders and files all right with the SMB client computer, a Windows XP machine.
The created stuff correctly has the smbguest user and group, and inherits the default ACLs.
Meaning for example, I can create a new file with the SMB client and then modify it using autologin.
What does not work is the other way round, i.e. when I create a new file with autologin and then want to move/modify it using the SMB client.

In fact the whole thing appears to behave kind of irregular, so here's a few examples:

What the client +can -cannot do with stuff it created on the share itself:

[LIST]
[*]File on the top level: +modify -rename -delete
[/LIST]

[LIST]
[*]File in a directory: +modify +rename +delete
[/LIST]

[LIST]
[*]Directory on the top level: +rename +delete
[/LIST]

[LIST]
[*]Subdirectory: +rename +delete
[/LIST]

What the client +can -cannot do with stuff created by autologin:

[LIST]
[*]File on the top level: +modify -rename -delete
[/LIST]

[LIST]
[*]File in a directory: +modify -rename -delete
[/LIST]

[LIST]
[*]Directory on the top level: -modify -delete
[/LIST]

[LIST]
[*]Subdirectory: -modify -delete
[/LIST]

This obviously is is far from what I intend to achieve with the ACLs. What is going on?
I want to finally and forever and really get rid of having to care about those awful owning users and groups! They have never done me any good, have forced me to write clean-up scripts, and now it appears that the ACL "exorcism" failed and they still are haunting me despite my best efforts, through Samba.

I did not even edit the smb.conf myself, except that I changed Samba's log file location to a file on /tmp.
I am trying to avoid messing with stuff I do not know well and use the most controllable tools available:

[LIST]
[*]Samba configuration: system-config-samba
[/LIST]

[LIST]
[*]ACL editing: eiciel
[/LIST]

So here's the gist of the setup, in pictures and links.
If anyone knows how to sort it out, please be so kind to let me know how, I'd very much appreciate that.

[IMG]http://fleder.dyndns.org/permshare/samba.acl.problem/system-config-samba.main-window.png[/IMG]
[IMG]http://fleder.dyndns.org/permshare/samba.acl.problem/system-config-samba.server-settings.basic.png[/IMG]
[IMG]http://fleder.dyndns.org/permshare/samba.acl.problem/system-config-samba.server-settings.security.png[/IMG]
[IMG]http://fleder.dyndns.org/permshare/samba.acl.problem/system-config-samba.edit-share.basic.png[/IMG]
[IMG]http://fleder.dyndns.org/permshare/samba.acl.problem/system-config-samba.edit-share.access.png[/IMG]

"test.file.smbguest.txt" is a top-level file that has been created by the SMB client.
[IMG]http://fleder.dyndns.org/permshare/samba.acl.problem/test.file.smbguest.ls-la.getfacl.png[/IMG]
[IMG]http://fleder.dyndns.org/permshare/samba.acl.problem/test.file.smbguest.rename-delete-smbguest.png[/IMG]

And here is the Samba configuration file:
[http://fleder.dyndns.org/permshare/samba.acl.problem/smb.conf](http://fleder.dyndns.org/permshare/samba.acl.problem/smb.conf)

Thank you very much in advance for any help.

---

### Post by fleder on 2012-07-07
In summary, this is what I'm trying to set up, on an Ubuntu 12.04 Server machine:

[IMG]http://fleder.dyndns.org/permshare/samba.acl.problem/draft.networkdrive.png[/IMG]

---

### Post by bab1 on 2012-07-07
Why use ACL's at all?  Just set the group ID (SGID) on the root directory of the share and all subsequent files and directories would inherit the group ID (GID) of the parent.  The basic permissions are 2775 on the root directory and then set the group ownership to a common group of your choice.  The owner (o) really doesn't matter only the group (g).  The others (o) will not matter either although by default they should have read rights.  Files should be 0664 and directories should be 2775 if the umask is 0002.

The group I created and use is *smbusers *, but by default there should be a group *sammbashare* if you wish.

---

### Post by fleder on 2012-07-07
Thanks for your answer.

I'm beginning to fear that ACLs are not properly supported by Samba, so I'll try to create a group "smbguest_rw" and add it as supplementary group to the users "smbguest" and "autologin" (and of course "superuser"), along with enabling the group inheritance SGID thing.

However, even if it works it still is a suboptimal workaround for me. I really WANT the ACLs to be the primary way of deciding who is allowed to do what.
For too many years I have deplored the lack something like the Windows ACL mechanism on Linux, until I recently found out that there are indeed some suitable-looking ACL mechanisms on Linux as well.

With ACLs, I can figuratively put my foot down and say, "In this directory tree, no matter who creates what, members of groupX and groupY may read and write anything, and members of groupZ may only read stuff. No exceptions or funny business!".

The classic Unix permissions have been a pain for me for several years now.
No matter what I did with my files and folders, afterwards I had to mind them and use chown -R, chgrp -R and chmod -R to no end.
With ACLs I can specify default access rights that definitely WILL be inherited to newly created files and folders, regardless of the user I create them with.

The classic permissions don't like me, I don't like them, so as far as I am concerned they can leave me well alone and we'll hopefully go separate ways some day.

---

### Post by kgatan on 2012-07-08
Hopefully someone can answer this better since i have limited experience.
You can try to modify your smb.conf with these options on the specific share,

```
inherit permissions = Yes         
inherit acls = Yes         
map acl inherit = Yes
```Im not 100% sure on what they do but google em to find out more and if they are what you need.

---

