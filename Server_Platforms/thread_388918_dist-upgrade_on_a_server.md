---
title: "dist-upgrade on a server?"
date: 2007-03-20
forum: Server Platforms
---

### Post by homli on 2007-03-20
I haven't been able to located documentation on when it's a good idea (or not so good idea) to run 'apt-get dist-upgrade' or 'apt-get install linux-image-server' on a production ubuntu server.

It appears the edgy server CD includes linux-image-server 2.6.17-10.33.  As of this post, 'apt-get upgrade' updates to 2.6.17-10.34 and 'apt-get dist-upgrade' updates to 2.6.17-11.35.  The latest rev of 2.6.17 on kernel.org is 2.6.17-14.

First question... Are security fixes added to 2.6.17-10 as necessary (thus the reason for .33 and .34?), or is dist-upgrading to 2.6.17-11 necessary to keep up with security issues?

Second question... Will edgy eventually be upgraded to 2.6.17-14 since it's the most recent fixes in the 2.6.17 line?  Or how does Ubuntu determine when to upgrade to newer kernels in the same 2.6.XX?

---

### Post by homli on 2007-03-20
I found some info on the wiki that begins to answer my second question.
[https://wiki.ubuntu.com/StableReleaseUpdates#head-eceaffe5c151e18b2b18c5756d63efb53d053e22](https://wiki.ubuntu.com/StableReleaseUpdates#head-eceaffe5c151e18b2b18c5756d63efb53d053e22)

How about thoughts on how frequently to 'apt-get dist-upgrade' or 'apt-get install linux-image-server' on a production server?

---

### Post by Brazen on 2007-03-20
I use dist-upgrade all the time on production Dapper servers.  I would be a little more reluctant on Edgy servers though, but of course I would never use Edgy in a production environment to begin with.

---

### Post by homli on 2007-03-20
> ...I would never use Edgy in a production environment to begin with.

My preference would be to use the latest LTS release in production.  However, the Dapper installer has a bug (debian bug # 377391) that prevents creating LVM on an SATA software RAID1 array, which is a requirement for my environment.

I'm still deciding whether to attempt to patch the Dapper installer myself and hope the rest of the install goes more smoothly.  Otherwise I'm stuck with Edgy, returning to RHEL4, or trying RHEL5--none of which have me too excited.

---

### Post by Brazen on 2007-03-21
...and there you have one of the downfalls of LTS releases.  In your case, rather than go with Edgy or RHEL, I would suggest going with Debian Etch.  It is in the very late beta stages right now and is supposed to go gold on April 2nd.

I had a problem with Samba that would be fixed with a newer version than what comes in Dapper.  After weighing basically the same choices that you listed, I decided to go with Debian Etch.  I installed it and have it working as of January with no problems.  Since it is beta though, I have not been updating it (other than right after the install) just in case some breakage is introduced, however after it goes final then I will start updating it regularly.

---

### Post by DoLoop on 2007-03-21
I'm still a relative newbie, having only had Ubuntu (Dapper) servers in production for 7 months.  But they get a dist-upgrade every month and I haven't killed them yet.

---

