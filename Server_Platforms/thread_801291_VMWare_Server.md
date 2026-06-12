---
title: "VMWare Server"
date: 2008-05-20
forum: Server Platforms
---

### Post by carbm1 on 2008-05-20
How long does it usually take for VMWare Server to show up in the partner repositories for 8.04? 

I updated from 7.10 and had installed from the repositories. Its obviously broken now after the upgrade... I didn't have anything terribly important running but it would be nice to get back to testing things.

I have read several guides on how to install it... I've done it before. I just want to be able to easily type "apt-get install vmware-server" and badda bing badda boom... done.

I still haven't got my mind wrapped around how the software is released for Ubuntu.   I recently attended a workshop where we installed OpenSUSE and installed ntop and other security related software...  I wanted to use my Ubuntu but the ntop version is older.  Is there a wiki or something I can read to have a better understanding of this?

Thank You,

Craig

---

### Post by dmizer on 2008-05-21
ubuntu has little to no controll over the vmware release schedule because it's not open source, so that's part of the problem.  as far as i know, the only way to install vmware server in hardy is to hack it.  at least at the moment.

i was able to get it to install, but you don't seem interested in a hack job so i'll save myself the trouble of tracking it down (it was not easy).

as for how the versions go, i didn't land anything that explained things in detail, though i'm sure it exists.  usually though, new version updates come only after kernel updates.  

inbetween are usually only bug patches, or security fixes.  so in short, don't expect vmware server to show up in the repos until after the next kernel update.

here are a few basic links that may help to get you started.
[https://wiki.ubuntu.com/TimeBasedReleases](https://wiki.ubuntu.com/TimeBasedReleases)
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce)
[https://wiki.ubuntu.com/HardyReleaseSchedule](https://wiki.ubuntu.com/HardyReleaseSchedule)
[https://wiki.ubuntu.com/OtherProjectSchedules](https://wiki.ubuntu.com/OtherProjectSchedules)

---

### Post by windependence on 2008-05-21
> **dmizer said:**
> ubuntu has little to no controll over the vmware release schedule because it's not open source, so that's part of the problem.  as far as i know, the only way to install vmware server in hardy is to hack it.  at least at the moment.

i was able to get it to install, but you don't seem interested in a hack job so i'll save myself the trouble of tracking it down (it was not easy).

as for how the versions go, i didn't land anything that explained things in detail, though i'm sure it exists.  usually though, new version updates come only after kernel updates.  

inbetween are usually only bug patches, or security fixes.  so in short, don't expect vmware server to show up in the repos until after the next kernel update.

here are a few basic links that may help to get you started.
[https://wiki.ubuntu.com/TimeBasedReleases](https://wiki.ubuntu.com/TimeBasedReleases)
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce)
[https://wiki.ubuntu.com/HardyReleaseSchedule](https://wiki.ubuntu.com/HardyReleaseSchedule)
[https://wiki.ubuntu.com/OtherProjectSchedules](https://wiki.ubuntu.com/OtherProjectSchedules)

Actually, VMware Server is the only product in their line that IS open source and totally free (as in beer). 

It would be easier to install it on 7.10 and then upgrade later. I have a working install in a production environment on 7.10 server and it runs great. I did not apt-get it though, I installed from source which is fairly easy and may yield a bit of a speed difference too.

-Tim

---

### Post by dmizer on 2008-05-21
not that i doubt you, but if that is the case why is it necessary to register for keys?

edit:
the source is listed on the vmware site as "modified".

---

### Post by windependence on 2008-05-21
> **dmizer said:**
> not that i doubt you, but if that is the case why is it necessary to register for keys?

edit:
the source is listed on the vmware site as "modified".

I think this is more so they can market to you. They also tell you not to use Server in production yet Server is just a rewrite of one of their old production products and it works just fine. I have some web servers running on Server for over a year now without incident. I'm convinced they don't want to tell you it would work just fine for production so they can sell you the commercial products.

-Tim

---

### Post by fester225 on 2008-05-21
"How long does it usually take for VMWare Server to show up in the partner repositories for 8.04?

I updated from 7.10 and had installed from the repositories. Its obviously broken now after the upgrade... I didn't have anything terribly important running but it would be nice to get back to testing things."

I'm in the same boat as Craig. I had VMWare 1.04 working just fine in 7.04, then I upgraded to 8.04, which is when VMWare quit. So far VMWare Server 1.05 won't install, or if it's installed, it won't work.

I've gone through;
[http://ubuntuforums.org/showthread.php?t=788169](http://ubuntuforums.org/showthread.php?t=788169)
[http://ubuntuforums.org/showpost.php?p=4357442](http://ubuntuforums.org/showpost.php?p=4357442)
[http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually)
   ...needless to say nothing has worked yet.

Is there another forum we should be bringing this problem to?

---

