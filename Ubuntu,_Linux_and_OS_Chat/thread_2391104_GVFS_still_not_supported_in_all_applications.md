---
title: "GVFS still not supported in all applications?"
date: 2018-05-05
forum: Ubuntu, Linux and OS Chat
---

### Post by kellyvotrenom on 2018-05-05
The way I understand it, not all applications support gvfs and so not all open/ save dialogs share the same attributes, for one example: not showing bookmarks.  This is the biggest frustration for me personally with Ubuntu since all my data is stored on an external server.  So if an application doesn't show the bookmarks I have created, it takes between 10-16 mouse clicks and 4-6 directory changes before I get to the destination folder on the network. (file system, run, user, nas location, destination folder, possible sub folders)

Why is this still the case considering that network storage is pretty common? Am I missing something or using the Linux file system the wrong way?  Is there a way for network storage locations to show up in all my open/save dialogs?

I have searched this topic over and over. The oddest thing is my browsers used to show the bookmarked network locations in earlier versions of 14.04 but they stopped at some point.  Totem video player used to in 14.04 but now that I am using 16.04 it doesn't show network bookmarks.  Libre Office didn't previously but now does.  As others have pointed out in other forums and posts it's hit and miss with any application.

I don't understand why there isn't some standard for file management in Ubuntu.  Do other Linux distros handle this better?

I apologize if this is all wrong but this is the understanding of the situation from all I have read. I attached a screen shot to show what my file manager looks like vs what many of my app open save dialogs look like that exhibit this behavior. I'm sure this is familiar to most.

Thanks for any additional light that you can throw on this for me.  

kvn

---

### Post by TheFu on 2018-05-06
Opinions follow.  Lots of people will disagree, which is fine.

Yes, you are doing it wrong by using gvfs at all. gvfs doesn't modify the mtab, so it isn't a "real mount" like cifs or nfs network mounts are.  Applications all support those methods because they are **real mounts** all the way throughout the OS.

On Unix systems, applications shouldn't deal with mounts.  The system should. Local or remote storage should all appear as local storage for all users.  End users shouldn't have authority to use 'mount', since the power to mount is the power to destroy.

So, for access to Unix system storage over a secured LAN, use NFS.
For access to Windows storage over a secured LAN, use CIFS.

For access to Unix storage over the internet, use a VPN + NFS or sftp or sshfs or 50 other methods.
For access to Windows storage over the internet, use a VPN and CIFS.

Both of these mount options can be accomplished - on demand - using a tool called autofs. 

BTW, nfs has been worked very well for 30+ years and CIFS has been working well thanks to the Samba team since at least 1995. 

IMHO, using any GUI to control mounts for storage is a bad idea. I've been burned enough to just manage everything through the config files. Real mounts are faster than gvfs, BTW.

GVFS seems easier, until it breaks or doesn't work.  NFS, OTOH, just works.

---

### Post by Morbius1 on 2018-05-06
The problem is that bookmark in nautilus is more than a bookmark it's also a launcher.

First it runs a mount command:
```
gvfs-mount smb://server/share
```
Then it displays the contents in nautilus of the resulting mount point:
> /run/user/1000/gvfs/smb-share:server=server,share=share/

Open Firefox > File > Open File and it has no idea that there is this "launcher / bookmark".

One way around this is admittedly convoluted. Create a bookmark to the parent folder of the mount points in Nautilus: **/run/user/1000/gvfs**. It will be labeled "gvfs" in Nautilus and in Firefox.

What makes it convoluted is that in Firefox it is in fact a link to the mount point only. It doesn't run the gvfs mount command so you will need to connect to the server and it's share first in nautilus then use the "gvfs" bookmark in Firefox to access the share.

You could use something like gigolo to have your network shares mounted as they become available then the "gvfs" bookmark in firefox will work more seamlessly.

---

### Post by kellyvotrenom on 2018-05-06
> **TheFu said:**
> Opinions follow.  Lots of people will disagree, which is fine.

Yes, you are doing it wrong by using gvfs at all. gvfs doesn't modify the mtab, so it isn't a "real mount" like cifs or nfs network mounts are.  Applications all support those methods because they are **real mounts** all the way throughout the OS.

On Unix systems, applications shouldn't deal with mounts.  The system should. Local or remote storage should all appear as local storage for all users.  End users shouldn't have authority to use 'mount', since the power to mount is the power to destroy.

So, for access to Unix system storage over a secured LAN, use NFS..

Thanks - this is a great answer. With your information i googled "How to automount network shares in Linux" and am on the path to solving my problem (I think).  I'll return with more questions if I get stuck but not using gvfs seems like the proper solution to my dilemma. Thanks for the advice.

I assumed that the way I was doing it was not right, I doubted that the way things were not working was just a "problem" with Ubuntu.

Thanks to Mobius1 for the explanation as to why it works in Nautilus but not necessarily in applications.  I will look into Gigolo, I remember being introduced to it when I first started using Ubuntu and didn't have any idea what it was for.  That may work as a solution as well.

Thanks again, much appreciated

---

### Post by Morbius1 on 2018-05-07
> **kellyvotrenom said:**
> I will look into Gigolo, I remember being introduced to it when I first started using Ubuntu and didn't have any idea what it was for.  That may work as a solution as well.

Here is my 2 minute HowTo on Gigolo should you decide to use it. The last step is not obvious and is not done by the application itself.

After you connect to the share:

** Create a bookmark in gigolo: [B]Right click the mount icon > Create Bookmark
[/B]
** Tell it to automount: [B]Select the Auto-Connect box
[/B]
** Have gigolo start minimized:** Edit > Preferences > Interface > Start minimized in the Notification Area**
[COLOR=#0000cd][I]You might want to deselect the "Show auto-connect error messages" box.
[/I][/COLOR]
** Then back in the desktop have gigolo autostart at login: [B]Startup Applicaions > Add > name = Gigolo, Command = gigolo.
[/B]
Then logout and login again. Your share should be mounted.

---

### Post by TheFu on 2018-05-07
Most people will be very happy using gigolo as Morbius1 suggests.  It is a point-n-click solution and works well enough for most uses.

---

### Post by kellyvotrenom on 2018-05-07
Gigolo makes it easier to automount but it doesn't solve the problem of network shares not showing in open save dialogs.  I appreciate that I don't have to edit my fstab, but I really need to have network shares show up in all applications.

---

### Post by Morbius1 on 2018-05-08
> **kellyvotrenom said:**
> Gigolo makes it easier to automount but it doesn't solve the problem of network shares not showing in open save dialogs.  I appreciate that I don't have to edit my fstab, but I really need to have network shares show up in all applications.
In the one example you gave above concerning Totem it does:[ATTACH=CONFIG]279619[/ATTACH]

Anyhoo, there are 100 other ways to do this like a cifs mount etc ...

---

