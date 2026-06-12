---
title: "Accessing Password Protected Ext3 Files"
date: 2010-07-31
forum: Security
---

### Post by kradecki on 2010-07-31
I have a drive that originally was used with a Linksys Network Storage Link (NSLU2), then stopped working with it. Now I'm trying to get the files off the drive. When I USB connect the drive to Ubuntu, I can see the files, but I'm unable to open them or copy them. The error message is: "Error Opening File: Permission Denied". I did have permissions set on the NSLU2. So far I'm not able to find a way to get around the permissions issue in Ubuntu.
 
I have used apps like EASEUS Data Recovery and Recover My Files. It appears that they are finding the files and are able to access them, so I know it can be done. I don't mind spending some $, but these apps are taking a *long* time to run. If I could properly access the files in Ubuntu long enough to copy the files, I think I'd be all set.
 
Any guidance to get me started? I'm fairly new to Ubuntu/Unix, so even mounting a drive is not something I have done often. 
 
Thanks in advance.

---

### Post by FuturePilot on 2010-07-31
```
sudo chown -R $USER:$USER /mount/point
```

Should get you going. Replace /mount/point with the actual mount point. It's usually a subdirectory under /media

---

### Post by jerenept on 2010-08-01
ALT-F2

type "gksudo nautilus"

enter your password and navigate to the files you want.
 
You can then right-click on the files and select "Properties"

Go to the "Permissions" tab and under "Others->Folder Acess", set to "Create and delete files"
and under "Others-> File Access" set to "read and write"

If it is a folder, click "Apply Permissions to Enclosed Files"

This does the same thing as what FuturePilot said, except graphically.

---

