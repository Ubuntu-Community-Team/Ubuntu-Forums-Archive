---
title: "Problem's pacemaker (unknow excuted)"
date: 2013-07-04
forum: Server Platforms
---

### Post by lythelong on 2013-07-04
Dear,
  I'm a newbie, recently i'm configuring a HA system (nginx+heartbeat+pacemaker+corosync+...). And while excuted nginx by pacemaker, perhaps "nginx ocf script" error or something, then show mistake and configure of pacemaker:

                  

```
Online: [ ubuntu2 ubuntu1 ]


         P_IP   (ocf::heartbeat:IPaddr2):       Started ubuntu1


         Failed actions:
              nginx_res_start_0 (node=ubuntu2, call=4, rc=-2, status=Timed Out): unknown exec error
             nginx_res_start_0 (node=ubuntu1, call=6, rc=-2, status=Timed Out): unknown exec error
```

```



root@ubuntu2:~# crm configure show
node $id="5d51ea64-2024-41a3-ba59-615a7c71390a" ubuntu2
node $id="77b5dab1-1b54-4832-9621-928dce7de2d8" ubuntu1
primitive P_IP ocf:heartbeat:IPaddr2 \
        params ip="192.168.2.100" cidr_netmask="255.255.255.0" \
        op monitor interval="20s" \
        meta target-role="Started"
primitive nginx_res ocf:heartbeat:nginx \
        params configfile="/nginx/conf/nginx.conf" httpd="/nginx/sbin/nginx" \
        op monitor interval="60s" timeout="10s" \
        op start interval="0" timeout="40s" \
        op stop interval="0" timeout="60s" \
        meta target-role="Started"
property $id="cib-bootstrap-options" \
        dc-version="1.1.6-9971ebba4494012a93c03b40a2c58ec0eb60f50c" \
        cluster-infrastructure="Heartbeat" \
        last-lrm-refresh="1372854456" \
        stonith-enabled="false"



```

pls, help me. NOTE: resource nginx_res's not start.

Thank you

---

### Post by lythelong on 2013-07-04
pls, help me

---

### Post by lythelong on 2013-07-05
no one can help me, haizzz, i trusted

---

