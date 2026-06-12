---
title: "NIS - Master/Slave problems"
date: 2013-05-15
forum: Server Platforms
---

### Post by chrislynch8 on 2013-05-15
Hi,

Just a quick question regarding NIS.

I am using it here in work between a few Servers. One Server acts as the Master Server held in the central office and the other are slaves that pull the Users and Group down. This works great 99.999% of the time as Internet is fairly solid. But when a remote server is unable to connect to the Master Server then users are unable to access folder/files on the their loca file server because the connection is not available.

I thought that NIS should still work in this case and the remote server that no longer has an active connection to the Master would be able to use a copy of the most recent download from the Master. Is this correct or am I missing something?

Rgds
Chris

---

