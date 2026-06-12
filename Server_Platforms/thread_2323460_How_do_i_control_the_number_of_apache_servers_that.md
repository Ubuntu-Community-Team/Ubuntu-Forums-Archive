---
title: "How do i control the number of apache servers that start"
date: 2016-05-05
forum: Server Platforms
---

### Post by PeterK2003 on 2016-05-05
When I look at the "server-status" page it show 18 servers started all using 300 plus megs of memory which is killing my sever.  How do I limit the number that start?

Thanks,
Peter

---

### Post by PeterK2003 on 2016-05-05
It appears that these setting in the apache config have little to no effect:
<IfModule mpm_prefork_module>
    StartServers          3
    MinSpareServers       0
    MaxSpareServers       5
    MaxRequestWorkers     5
    MaxRequestsPerChild  50
    ServerLimit           5
</IfModule>


Am I missing something?

---

