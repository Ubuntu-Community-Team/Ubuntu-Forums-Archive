---
title: "New server / Old www files..."
date: 2011-07-10
forum: Server Platforms
---

### Post by couchie on 2011-07-10
I had an old windoz 2003 server running a few recreational web sites. I've grown tired of all the hacking attempts, FTP floods, etc. Ok.. I've grown tired of windoz period.

When I set the server up, I had the operating system on one physical drive and stored all of the web files on a separate physical drive just in case I ever wanted to make some changes to the operating system.

So... in my adventurous ways, I've dumped windoz and installed ubuntu 11, 32 bit server edition on this machine. It is running fine from what I see on the server side. 

The first problem I've noticed is when even attempting to navigate to localhost through the server's web browser, I get a permissions issue.

> Forbidden

You don't have permission to access / on this server.

So... off to the drive where the httpd.conf file points to. This is the second physical drive. When checking permissions and attempting to change them to the correct ones for the folder, I can't change them. I've tried through the GUI and the terminal as root. Neither way will change the permissions.

I've stepped back and checked the permissions on the physical drive the files are stored on. I am having the same issues with the drive itself. 

How in the world can I change the permissions either on the drive or the folder? Is there something I should do as far as the drive's mounting?

Thanks in advance!

---

### Post by karlson on 2011-07-10
One has to ask what filesystem it is but I have to assume it's NTFS and as far as I know you can't change permission on NTFS system from Linux.

Question is what permissions does the NTFS system show?

---

### Post by couchie on 2011-07-10
I don't know why I didn't think of this. You are indeed correct, the drive is formatted in NTFS as it was running on a windows box. 

What about reformatting (after backing up files of course) for Linux? Would that make a difference? Could it be that the drive's permissions can't be changed due to the windoz settings from earlier?

As to the question of 'what does it show now'....

The owner is listed as me/Sudo root with create/delete
The group is my group again with 'none' under folder access
Others is just plain 'none'.

None of these can be changed. If an attempt is made to changing the permissions in the GUI, after you select the permission you want, it defaults back to what was originally set.

---

### Post by karlson on 2011-07-10
> **couchie said:**
> 
What about reformatting (after backing up files of course) for Linux? Would that make a difference? Could it be that the drive's permissions can't be changed due to the windoz settings from earlier?

To answer questions in order:

That's up to you.
It would absolutely make a difference.
No I think this may be because the file system is mounted read only or it could be because of the way that permissions are.

I would look at this first:
[http://www.linuxforums.org/forum/newbie/177749-how-change-permissions-ownership-ntfs-mounts.html](http://www.linuxforums.org/forum/newbie/177749-how-change-permissions-ownership-ntfs-mounts.html)
and the FAQ it refers to also.

---

