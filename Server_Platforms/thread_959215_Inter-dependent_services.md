---
title: "Inter-dependent services"
date: 2008-10-26
forum: Server Platforms
---

### Post by akbarmunir on 2008-10-26
I am using both Apache James and Apache Directory service on the Ubuntu Server 8.04. The Apache Directory service has an index number of 20 and Apache James service has an index number of 21.

I used 21 for Apache Jame mail service (through update-rc.d) because James in its initialization accesses directory service and it is mandatory that James starts when the Directory service has finished its initialization and is listening on the specified port.

Is it possible to somehow specify an inter-dependent factor when using the script update-rc.d to make sure that James is not started until after directory has finished its initialization? Or is there some other solution to this problem?

Thanks,
Akbar.

---

