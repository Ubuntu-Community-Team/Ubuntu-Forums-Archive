---
title: "trouble syncing folders outside Ubuntu One folder"
date: 2010-12-07
forum: Ubuntu One (CLOSED)
---

### Post by lovo on 2010-12-07
Hello,

I have successfully registered to ubuntu one. The sync is working in the /home/lovo/Ubuntu One folder but i would like to sync my Picture folder, as it says in this picture there:
[IMG]https://wiki.ubuntu.com/UbuntuOne/Tutorials/FileSharing?action=AttachFile&do=get&target=files_sync_on_u1_right_click_cropped.png[/IMG]
When I click on this button, nothing is happening.
Nothing appear neither in [https://one.ubuntu.com/files/](https://one.ubuntu.com/files/)

Is folder sync working ?

---

### Post by duanedesign on 2010-12-07
Could you please try running the following command:

u1sdtool --refresh-volumes


You can run the following command from the Terminal to see the list of User Designated Folder. These are folders other then the Ubuntu One folder that are set to sync.

u1sdtool --list-folders

---

### Post by lovo on 2010-12-08
Thanks for your reply.

I have tried your commands:

```
/home/lovo$**u1sdtool --refresh-volumes**
/home/lovo$**u1sdtool --list-folders**
No folders
/home/lovo$

```

Apparently it does nothing when I add a folder to ubuntu one from nautilus. I tried again on some other folders, seems to be the same

---

