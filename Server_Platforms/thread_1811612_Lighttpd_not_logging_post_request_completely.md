---
title: "Lighttpd not logging post request completely"
date: 2011-07-25
forum: Server Platforms
---

### Post by aliahsan81 on 2011-07-25
Hi All,

Please educate,I am running lighttpd on ubuntu 10.04 LTS. We are facing a small issue our post request not logged complete only some part is logged. Please let me know how can i logged full post request.

My Request contains following argument.

[http://172.16.100.130/api/username':'BussinessXYZ','secret':'egash12bgjg123jh','v':'1','mobile':'0xxxxx','action':'PM','keyword':'KeyWordXYZ](http://172.16.100.130/api/username':'BussinessXYZ','secret':'egash12bgjg123jh','v':'1','mobile':'0xxxxx','action':'PM','keyword':'KeyWordXYZ)', 'message': 'Hello customer, welcome to BusinessXYZ on ring': 'fullmsg': '1'

But in lighttpd log i only get this

172.16.100.132 172.16.100.130 - [25/Jul/2011:13:45:34 +0500] "POST /api/ HTTP/1.1" 200 22 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"

---

