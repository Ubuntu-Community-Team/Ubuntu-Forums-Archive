---
title: "Permissions issue on a Samba share"
date: 2012-09-13
forum: Server Platforms
---

### Post by groupthinker on 2012-09-13
Hello community! I'm setting up my first linux fileserver for Windows clients and am having some problems properly setting up the shares. I have a shared folder via Samba where multiple users (who are organized  by group) should have permissions of rwxrwx--- (0770). But when user  "joe" creates a folder and a file within it, user "jane" cannot move  those files out or create files there.
Ubuntu 12.04 3.2.0-30-generic
Samba version 3.6.3
from /etc/samba/smb.conf
[sharename]
    path = /srv/samba/sharename
;    browseable = yes
    writeable = yes
    valid users = @somegroup
#    admin users = adminstaff
    force group = somegroup
    create mode = 0770
    force create mask - 0770
    directory mode = 0770
    force directory mask = 0770
#    directory security mask = 000
    inherit permissions = yes
    vfs object = recycle
    recycle:repository = RecycleBin
    recycle:keeptree = yes
    recycle:exclude = *.tmp, *.bak

How can I make it so that members of the same security group can edit each other's work?
I've already set the initial permissions to be:
drwxrwx--- 7 root somegroup 4096 Jan 01 12:00 sharename
I'd still like to know who owns each file and who edited the file last, but want members of the same group edit each other's work.
Any ideas or help is greatly appreciated. I'm trying to keep this small business from buying a Windows domain controller if possible.

---

### Post by redmk2 on 2012-09-14
> **groupthinker said:**
> Hello community! I'm setting up my first linux fileserver for Windows clients and am having some problems properly setting up the shares. I have a shared folder via Samba where multiple users (who are organized  by group) should have permissions of rwxrwx--- (0770). But when user  "joe" creates a folder and a file within it, user "jane" cannot move  those files out or create files there.
Ubuntu 12.04 3.2.0-30-generic
Samba version 3.6.3
from /etc/samba/smb.conf
[sharename]
    path = /srv/samba/sharename
;    browseable = yes
    writeable = yes
    valid users = @somegroup
#    admin users = adminstaff
    force group = somegroup
    create mode = 0770
    force create mask - 0770
    directory mode = 0770
    force directory mask = 0770
#    directory security mask = 000
    inherit permissions = yes
    vfs object = recycle
    recycle:repository = RecycleBin
    recycle:keeptree = yes
    recycle:exclude = *.tmp, *.bak

How can I make it so that members of the same security group can edit each other's work?
I've already set the initial permissions to be:
drwxrwx--- 7 root somegroup 4096 Jan 01 12:00 sharename
I'd still like to know who owns each file and who edited the file last, but want members of the same group edit each other's work.
Any ideas or help is greatly appreciated. I'm trying to keep this small business from buying a Windows domain controller if possible.

I would have thought that```
    force group = somegroup
```... would have done the trick, but it just goes to show that you should set the underlying file system permissions rather than relying on Samba.

What you need to do is first set the group you want  on the directory you have set as root of the Samba share (i.e /srv/samba/sharename). ```
sudo chgrp somegroup /srv/samba/sommedir
```...then set the GID bit on that directory ([COLOR="Red"]see below[/COLOR]).

At this point if you do  these 2 steps, all files and folders will have the group assigned and the sgid bit applied.  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid") for sgid details. 

[COLOR="Red"]I usually do this when I originally create that directory.[/COLOR]  At that time is is simply ```
sudo chmod 2770 /srv/samba/somedir
```...The gotcha is that if you do this to a directory full of files and directories, ALL the files will be executable.  The workaround is to do the chmod  something like this ```
sudo chmod ug=rwX o=rX
```...the X=set directories to executable but not files (unless already set).

Once you see that you can create files and directories as you want from the command line, you can comment out a lot of the force parameters in your smb.conf file.  Just remember that default umask is 0002 for Ubuntu 12.04.  Some of the mask parameters you have are also redundant you can remove the deprecated ones too.

---

### Post by laryllian on 2012-09-16
If you use inherit permission, the mode/mask options become useless, its either one or all the others. Also keep in mind, if you completely want to control the permissions, use force user, force group and

create mask 
force create mode
directory mask
force directory mode
security mask
force security mode
directory security mask
force directory security mode

Yes, all of them.

"Mask" imposes the maximum allowed permissions 
"Mode" imposes the minimum allowed permissions
and security applies, if programs want to alter permissions of existing files.

By setting min and max permissions to the same value, you get exactly your desired permissions. ;)

PS: Further details look [here]("http://translate.google.de/translate?sl=de&tl=en&js=n&prev=_t&hl=de&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fblog.jonaspasche.com%2F2010%2F11%2F24%2Fendlich-verstehen-samba-rechtevergabe%2F&act=url").

---

### Post by SeijiSensei on 2012-09-16
If you need to audit file ownerships, "force user" will not work for you since all the files will be owned by the forced user, not the individuals who created the files.

---

### Post by groupthinker on 2012-09-16
Thank you everybody! I'm choosing to correctly set the system's permissions underlying Samba. redmk2 nailed what I was trying to do. I didn't understand about the GID bit, and reset the permissions with that in mind. Now that the filesystem's permissions are set correctly, I'm using
    inherit permissions = yes
I'm commenting out all the force modes and mask and create modes and mask. I'm sitting on the revised configuration now for a week awaiting feedback from the staff who are actually using the server. I'm appreciative of all the feedback and the links which articulate and explain what each item does.
I'm stubbornly leaving leaving:
    force group = somegroup
for right now. I'll remove that line later once I'm confident everything is working well.
larryllian, thanks for leading me to the idea of using Samba as an alternate way to manage permissions too. That info. may come in very handy in the future. I failed to grasp the max/min component to mask/mode. I'm still unclear about how Samba interprets conflicting lines, ex inherit permissions vs force. But I'm sure as I dabble more I'll come across a way of making good choices.

---

### Post by cybercity@localhost on 2012-09-23
try to change permissions from 0770 to 0777

---

### Post by groupthinker on 2012-09-24
"try to change permissions from 0770 to 0777"
I ended up using 2660 instead of 0777 because the group bit needed to be set and I don't need executing permissions on files. I didn't need the world to have access at all.
After changing my permissions to 2660 I then ran "sudo chmod -R ug=rwX /srv/samba/somedir"
Does this seem like bad form or a bad idea to anybody? Ideally, I'd like any other administrator to see what's going on make sense of it. So, if I'm deviating from a best practice, please let me know.
-PS
thanks for everybody's input.

---

### Post by xdracco on 2012-09-24
I've set up my apache server to be a shared volume. I've set the owner/group to www-data, setguid to shared volume, and a few samba parameters to [@]www-data and when stuff is saved from a client, it's saved as user www-data and group @www-data.

Example:

```
$ chown -R www-data.www-data /path/to/samba/share
$ chmod g+s /path/to/samba/share
```and in smb.conf

valid users = @www-data
read list = @www-data
write list = @www-data
force user = www-data
inherit owner = yes

Lastly, add the user in question to the group. In my case, I added my normal user to the group www-data

```
$ usermod -a -G www-data my-user
```Whatever you do, don't set permissions to 777. That is a temporary solution, not permanent. In fact, that is horrible advice especially when your goal is for this volume to be available for a specific group of users. Since this is your goal, permissions of 0770 is much more preferred.

---

