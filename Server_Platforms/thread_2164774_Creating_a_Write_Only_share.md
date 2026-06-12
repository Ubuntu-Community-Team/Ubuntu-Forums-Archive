---
title: "Creating a Write Only share"
date: 2013-08-01
forum: Server Platforms
---

### Post by billo4th on 2013-08-01
I am setting up my first Ubuntu server to replace a windows 2000 file server. I'm running version 12.04.2. 
The only thing I have been unable to implement is a write only folder. We currently have several folders in
windows where the sales people submit reports to their supervisor. It is ok if they see what files are in there,
but they should not be able to read or copy anything in that folder, only add new files. Is there way to
accomplish this?

Thanks - Bill

---

### Post by TheFu on 2013-08-01
Set the umask to 077 for each user.
Set the directory permissions to d-wx-wx---t.

If that isn't enough, you can use ACLs to do absolutely anything you can ever imagine.

That should do it.Understanding UNIX directory and file permissions in depth is a highly worthwhile thing to study.

You might find it easier to setup an "upload" directory under each user's HOME, then grab those files with a script every day moving them to a protected directory only the supervisor controls.  The root crontab can do amazing things - if you don't want to use root, you can setup group permissions so the supervisor can grab the files and move them himself ... or run a script that does this hourly, daily, weekly, whenever.

---

### Post by TheFu on 2013-08-01
Set the umask to 077 for each user.
Set the directory permissions to d-wx-wx---t.

If that isn't enough, you can use ACLs to do absolutely anything you can ever imagine.

That should do it.Understanding UNIX directory and file permissions in depth is a highly worthwhile thing to study.

You might find it easier to setup an "upload" directory under each user's HOME, then grab those files with a script every day moving them to a protected directory only the supervisor controls.  The root crontab can do amazing things - if you don't want to use root, you can setup group permissions so the supervisor can grab the files and move them himself ... or run a script that does this hourly, daily, weekly, whenever.

---

