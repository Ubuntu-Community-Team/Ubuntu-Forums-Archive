---
title: "Dahdi intall fails"
date: 2009-11-12
forum: Server Platforms
---

### Post by mudcow007 on 2009-11-12
Hi guys i think this is something to do with a kernel issue?

im trying to install Dahdi on my 9.10 install when i try to "make" dahdi i get the following error.

```
/usr/src/asterisk/dahdi-linux-complete-2.2.0.2+2.2.0/linux/drivers/dahdi/wctc4xxp/base.c:777: error: â&#8364;&#732;struct net_deviceâ&#8364;&#8482; has no member named â&#8364;&#732;openâ&#8364;&#8482;
/usr/src/asterisk/dahdi-linux-complete-2.2.0.2+2.2.0/linux/drivers/dahdi/wctc4xxp/base.c:778: error: â&#8364;&#732;struct net_deviceâ&#8364;&#8482; has no member named â&#8364;&#732;stopâ&#8364;&#8482;
/usr/src/asterisk/dahdi-linux-complete-2.2.0.2+2.2.0/linux/drivers/dahdi/wctc4xxp/base.c:779: error: â&#8364;&#732;struct net_deviceâ&#8364;&#8482; has no member named â&#8364;&#732;hard_start_xmitâ&#8364;&#8482;
/usr/src/asterisk/dahdi-linux-complete-2.2.0.2+2.2.0/linux/drivers/dahdi/wctc4xxp/base.c:780: error: â&#8364;&#732;struct net_deviceâ&#8364;&#8482; has no member named â&#8364;&#732;get_statsâ&#8364;&#8482;
/usr/src/asterisk/dahdi-linux-complete-2.2.0.2+2.2.0/linux/drivers/dahdi/wctc4xxp/base.c:781: error: â&#8364;&#732;struct net_deviceâ&#8364;&#8482; has no member named â&#8364;&#732;do_ioctlâ&#8364;&#8482;
make[4]: *** [/usr/src/asterisk/dahdi-linux-complete-2.2.0.2+2.2.0/linux/drivers/dahdi/wctc4xxp/base.o] Error 1
make[3]: *** [/usr/src/asterisk/dahdi-linux-complete-2.2.0.2+2.2.0/linux/drivers/dahdi/wctc4xxp] Error 2
make[2]: *** [_module_/usr/src/asterisk/dahdi-linux-complete-2.2.0.2+2.2.0/linux/drivers/dahdi] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-server'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/asterisk/dahdi-linux-complete-2.2.0.2+2.2.0
```

someone has mentioned that it could be that my kernel is too recent and unsupported? but i have seen loads of peeps with asterisk installed on 9.10??

anyone please help :)

---

