---
title: "Connection to cloud totally broken"
date: 2011-11-22
forum: Ubuntu One (CLOSED)
---

### Post by OakRaider4Life on 2011-11-22
After changing my UID today, I opted to rename my home folder as well to match my new UID. It would seem that this has had the unfortunate side-effect of utterly and completely breaking my connection to Ubuntu One. Where formerly, I was syncing my documents folder and pictures folder, I am unable to add those folders (or any folders for that matter) to my Ubuntu One cloud folders, and am also unable to check off any of my Cloud folders to sync with my current /home directory. I changed my UID from "user" to "user-ubuntu". In my Ubuntu One client, my cloud folders still reflect the old /home directory (for example, my documents folder is listed as /home/user/Documents). On the Ubuntu One website, these directories are reflected using the ~/ directory. This led me to believe that if I was able to totally remove every trace of Ubuntu One and reinstall, it could very well fix my problem. So I followed [these instructions]("https://answers.launchpad.net/ubuntuone-client/+faq/778") to do exactly that. Upon reinstalling ubuntu one, I've found that absolutely nothing has changed. I'm still unable to select my folders from the cloud to sync, and totally unable to add any folders to sync to the cloud. Help?

---

### Post by OakRaider4Life on 2011-11-22
Solved... for some reason, after all that, all it took was a

```
sudo apt-get purge ubuntuone-control-panel-gtk*
sudo apt-get install ubuntuone-control-panel-gtk*
```

and that seemed to erase whatever part of the configuration needed erasing. Sorry to take up forum space :p

---

### Post by duanedesign on 2011-11-24
Thank yo for updating us on the fix for your problem. That will help anyone else in the future with your issue.

---

