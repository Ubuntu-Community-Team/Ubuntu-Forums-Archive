---
title: "enable htaccess with ISPConfig - 8.04"
date: 2008-07-08
forum: Server Platforms
---

### Post by mspIggy on 2008-07-08
hello

i have a fresh install / build of 8.04 amd64 and ISPConfig

i am having a real problem trying to understand how to enable htaccess, on a per site basis or server wide...

our current server is centOS and we use this - modified for each site 


<Directory /home/.sites/120/site53/web>
Options -Indexes
AllowOverride All
</Directory>

in httpd.conf

the http.conf file is blank in this install - i have asked in the ISPConfig forum and exhausted what seems to be all resources there 

please help!

thank you

---

### Post by windependence on 2008-07-09
httpd.conf is not used in the Ubuntu Apache setup. In this case the conf file is at /etc/apache2/apache2.conf

-Tim

---

