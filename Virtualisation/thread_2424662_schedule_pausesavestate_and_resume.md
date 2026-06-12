---
title: "schedule pause/savestate and resume"
date: 2019-08-12
forum: Virtualisation
---

### Post by parisv on 2019-08-12
I have a VM which only need up during working hours Monday-Friday 9.00am - 5.30pm

I'd like it to resume where I left off so don't want it shut down.

I guess save state would be better for other resources on the host server?

So I guess I need 1 script with - VBoxManage controlvm <vmname>  savestate 

and another with - VBoxManage controlvm <vmname> resume

Just not sure how set this to run during those times?

---

### Post by TheFu on 2019-08-12
I would use the crontab for the userid that normally starts and manages the VMs.  There are probably some environment variables that are available in a normal login session that wouldn't be there in the cron session, so you'll need to figure out what those are and add them to your start/stop script.

---

