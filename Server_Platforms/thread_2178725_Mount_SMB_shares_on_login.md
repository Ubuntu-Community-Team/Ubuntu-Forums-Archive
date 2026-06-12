---
title: "Mount SMB shares on login"
date: 2013-10-04
forum: Server Platforms
---

### Post by terabyte128 on 2013-10-04
Hello - 

I am trying to configure an Ubuntu server to login with Active Directory credentials.

I have been using likewise-open (the newer version, now owned by powerbroker) to authenticate using Active Directory. I can join a domain, and login as a domain user.
The issue is that I cannot figure out how to mount Windows file shares. I have tried running the likewise ```
samba-interop-install
``` command but it does not seem to make any difference. I have been able to successfully mount windows shares manually using the mount command.

I've been told that I must write a login script that somehow grabs the password and then mounts the shared folder. 
However, there doesn't seem to be an easy way to get the password from lightdm (because it would be a security hole)

Has anyone done this and have any tips for a good way of doing it?

A bit of context:
This is for a school environment. I'd like users to be able to login with their active directory credentials and have their network home folder automatically mounted upon login. 

Thank you!

---

### Post by TooLboy on 2013-11-22
What I have tested is auomounting of users home dir, as specified in AD and user mounting another smb share, like common departmental or class fileshare. Here are some quick notesusing power broker, pbis open edition, once called likewise-open:

1. User automount of HomeDir works with open edition og pbis when you set the RemoteHomeDirTemplate and CreateHomeDir is true. It is in the docs.
  /opt/pbis/config --list show many options that can be set, I used:
  /opt/pbis/config RemoteHomeDirTemplate "%H/local/%D/%U/My Documents"

When the user object in AD has the Home directory attribute set, like H: set to \\thefileserver\homeshare\%username%  Then pbis will automount that share to the local path "/home/local/$yourdomain/$youruser/My Documents"
NB! That means you might want to alter the skeleton dir so that it is clear to users that on Linux, only the "My Documents" in their home folder actually is on the network. Othe folders created automatically (Pictures, Videos, etc) are actually local. So if it is a multi user seat/computer then they might save some documents locally by mistake (In /home/local/domain/user/new-document.txt)

The licensed enterprise version I think will let you control this from AD group policies.
I have not been able to make it work without errors having a direct substitution, so that the network share is the exact /home/local/domain/user, like it is in windows. I get errors in many apps, haven't figured out that, yet.
/opt/pbis/bin/config --show "SkeletonDirs" shows that the template for new users are in "/etc/skel", update that or change:
/opt/pbis/bin/config "SkeletonDirs" "/etc/skelSchoolKids6to9"



2. Mounting other shares as AD user. Not perfect but easy and I think good enough: gvfs.
Test as a user from terminal window (be sure to start bash if not default, much easier):
  gvfs-mount smb://server/share
There will automatically be a new folder under ~/.gvfs named like "data on server.domain". The mount (disk or drive) will show up in the left tree in the file browser (nautilus). 
You can make a visible folder in the users home dir with something like: ln -s "~/.gvfs/datashare on sever"  ~/DepartmentX.  
This you would have to put in he skeleteon dir so eash new user get a loginscript, which they actually have in most Linux distro's, I use ~/.profile, it seem to work, just update and export PATH or use full paths.

---

### Post by lingpanda on 2013-11-22
I haven't tested this but you might want to take a look.

 [http://techcommons.stanford.edu/topics/miscellaneous/mounting-active-directory-windows-cifs-file-share-ubuntu-linux](http://techcommons.stanford.edu/topics/miscellaneous/mounting-active-directory-windows-cifs-file-share-ubuntu-linux)

---

### Post by bab1 on 2013-11-22
> **lingpanda said:**
> I haven't tested this but you might want to take a look.

 [http://techcommons.stanford.edu/topics/miscellaneous/mounting-active-directory-windows-cifs-file-share-ubuntu-linux](http://techcommons.stanford.edu/topics/miscellaneous/mounting-active-directory-windows-cifs-file-share-ubuntu-linux)

This is completely wrong and outdated.  The only thing correct is the comments.

---

