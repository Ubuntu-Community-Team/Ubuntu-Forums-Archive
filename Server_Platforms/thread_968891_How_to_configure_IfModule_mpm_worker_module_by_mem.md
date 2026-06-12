---
title: "How to configure IfModule mpm_worker_module by memory"
date: 2008-11-03
forum: Server Platforms
---

### Post by vuit on 2008-11-03
Dear all

Please help me to configure  IfModule mpm_worker_module by memory
Example : I have 1 server ubuntu linux use  Apache+PHP FastCGI with MPM=Workers . 

- How to configure : 

<IfModule mpm_worker_module>
	ServerLimit ?
	StartServers ?
	MaxClients ?
	MinSpareThreads ?
	MaxSpareThreads ?
	ThreadsPerChild ?
</IfModule>

for : 4G ram , or 5G , 6G ,7G .v.v.v

- Have math configure <IfModule mpm_worker_module> </IfModule> by memmory ?

---

