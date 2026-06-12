---
title: "failed to start xcp-networkd"
date: 2012-01-29
forum: Virtualisation
---

### Post by buran16 on 2012-01-29
Hello everybody,

I am trying to install XEN on a clean and new Ubuntu x64 11.10. I am following the steps on [http://wiki.xen.org/wiki/XAPI_on_Ubuntu](http://wiki.xen.org/wiki/XAPI_on_Ubuntu). While installing the  xcp-xapi package I get the following error:
```
xcp-networkd (1.3.2-1ubuntu1~oneiric1) wird eingerichtet ...
Starting the XCP networking daemon: .............................. * failed to start xcp-networkd.

invoke-rc.d: initscript xcp-networkd, action "start" failed.

```Is there somewhere a log where I can find out more about the problem? Do you have a idea what could be the source of the problems?

Thank you for your answer.

Greetings
Reto

---

### Post by paykoob on 2012-01-31
> **buran16 said:**
> Hello everybody,

I am trying to install XEN on a clean and new Ubuntu x64 11.10. I am following the steps on [http://wiki.xen.org/wiki/XAPI_on_Ubuntu](http://wiki.xen.org/wiki/XAPI_on_Ubuntu). While installing the  xcp-xapi package I get the following error:
```
xcp-networkd (1.3.2-1ubuntu1~oneiric1) wird eingerichtet ...
Starting the XCP networking daemon: .............................. * failed to start xcp-networkd.

invoke-rc.d: initscript xcp-networkd, action "start" failed.

```Is there somewhere a log where I can find out more about the problem? Do you have a idea what could be the source of the problems?

Thank you for your answer.

Greetings
Reto

I got this error too and I comment the 2>/dev/null in the xcp-networkd script and i see this error:

```
Fatal error: exception Unix.Unix_error(20, "open", "/etc/xcp/network.conf")

```

but there is not /etc/xcp/network.conf !

---

