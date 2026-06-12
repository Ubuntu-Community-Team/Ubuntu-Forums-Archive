---
title: "NFS Handle Becoming Stale Often"
date: 2016-11-12
forum: Server Platforms
---

### Post by Kirk Schnable on 2016-11-12
Hello,

In my setup at home, I have several VM's running on a physical host, and a file server running on a physical host.  The VM's mount the file server's volumes through NFS to access the files stored on it.

Since doing updates for dirty cow recently, I am frequently having issues with the NFS mount becoming stale on one of my VM's.  I'm not sure what's causing this to happen as I have the same mount on another identical VM and it doesn't have this issue.  They both use the same physical underlying network which is very simple (I have a dedicated gig switch in my server rack for storage use only).

In the past, I've only had issues with stale file handles when doing things like restarting the NFS service on my file server.  This seems to happen randomly and several times a week at least.

I am able to solve the issue by unmounting and remounting the path.  However this server is used by other people who don't have access to do this so I am looking to prevent this from continuing to happen.

Is there a practical way I can troubleshoot this?  I haven't found any obvious log output related to the events when this happens.  

Also, is there a practical way I can prevent it?  Like is there a mount option for NFS that I could add to my fstab to "remount if it becomes stale"?

Thanks!

---

### Post by SeijiSensei on 2016-11-12
You might consider putting a simple bash script in /etc/cron.hourly to unmount and remount the shares.

---

