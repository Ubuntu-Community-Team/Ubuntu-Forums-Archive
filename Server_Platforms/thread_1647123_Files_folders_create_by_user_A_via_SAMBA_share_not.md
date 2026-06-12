---
title: "Files folders create by user A via SAMBA share not delete-able by user B"
date: 2010-12-16
forum: Server Platforms
---

### Post by Sam Changtum on 2010-12-16
Hi All,

I have a problem that I have been trying to figure out. I believe this to be a Linux file system permissions issue and not a SAMBA permission issue. 

What I have is security camera device that is configured to save video files to a SAMBA file share named 'camera_files' using a specific user name 'camera' and password. The security camera will create a new directory for each day that it detects motion and start writing video files to the newly created directory.

Then I also have a user 'mary' that opens the 'camera_files' file share from her Windows 7 desktop. Mary's job is to inspect and delete these directories and video files that were created by the security camera. This is the problem - Mary does not have permissions to delete anything the video camera created.

Other things to note. Both the 'camera' and 'mary' accounts belong to a Linux group named 'security-camera-users'. The 'camera' user is the owner of the 'camera_files' directory on the server and 'security-camera-users' is the group for this directory as well. Both the owner and group have read/write/execute permission on this directory.

Here's my smb.conf file share definition:

[INDENT][camera_files]
browseable = yes
read only = no
path = /var/files/camera/camera_files
valid users = mary, camera
force group = security-camera-users[/INDENT]


Does anyone have any idea how to solve this permissions issue?

---

### Post by SeijiSensei on 2010-12-16
Try adding "create mode = 0664" to the share definition.  This should give all new files the correct permissions.  Another option is to use "force user = camera".  Then all users of the share will appear to the operating system as the camera user.

---

### Post by Sam Changtum on 2010-12-21
> **SeijiSensei said:**
> Another option is to use "force user = camera".  Then all users of the share will appear to the operating system as the camera user.

Using "force user = camera" did the trick. I experimented with the create mode/create mask parameters - no success. So I gave up on that and went with the force user parameter.

Thank you SeijiSensei, for the direction.

---

