---
title: "Getting the widows workgroups right"
date: 2008-11-20
forum: Server Platforms
---

### Post by happyhacker on 2008-11-20
I am going to load up Ubuntu server after lunch to get our office network sorted. I am going to load ebox which I assume will invoke SAMBA and anything else needed. My questions are based around my confusion about how the windows PCs should be configured:

1. I would like at least 2 workgroups on the windows PCs. Is the server going to cope with more than one?

2. I assume workgroups is the way to go. The tutorial I am going to follow is (albeit for 8.10) [http://www.howtoforge.com/running-a-file-and-print-server-with-ebox-on-ubuntu8.04-server]("http://www.howtoforge.com/running-a-file-and-print-server-with-ebox-on-ubuntu8.04-server")
Am I right in thinking a domain is not required on windows?

Initially, I want to get file sharing and backups (on-site and off-site) working but later want remote access. DHCP I intend ffrom the existing ADSL router.

---

### Post by jonabyte on 2008-11-20
You are not required to have a domain for you windows boxes to connect to a samba share.
Just make sure you have the same workgroup name on the windows machines as in your smb.conf file and you should see the share.

---

### Post by happyhacker on 2008-11-20
Thanks I will configure the system so they agree.

---

