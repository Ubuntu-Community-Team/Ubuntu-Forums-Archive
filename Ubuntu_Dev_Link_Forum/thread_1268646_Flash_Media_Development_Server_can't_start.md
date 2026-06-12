---
title: "Flash Media Development Server can't start?"
date: 2009-09-17
forum: Ubuntu Dev Link Forum
---

### Post by infernus_crusher on 2009-09-17
If anyone is familiar with FMS please let me know how to setup it properly on Ubuntu. I downloaded the thing from [http://www.adobe.com/cfusion/tdrc/index.cfm?loc=en_us&product=flashmediaserver](http://www.adobe.com/cfusion/tdrc/index.cfm?loc=en_us&product=flashmediaserver), unpacked the tar file, installed it with all the required libraries but could only start the admin server. When I tried starting the media server it gave me this error:

```

:/opt/adobe/fms# ./fmsmgr server start
Server:start command:
Server service start not found. Exiting.

```

---

### Post by infernus_crusher on 2009-09-20
Anyone?

---

### Post by kulshoks2121 on 2011-05-11
After a year....

check your Application.xml, Vhost.xml, most likely its Adaptor.xml there should be some syntax error there

---

