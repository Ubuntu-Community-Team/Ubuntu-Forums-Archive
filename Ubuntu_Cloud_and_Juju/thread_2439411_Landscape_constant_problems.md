---
title: "Landscape constant problems"
date: 2020-03-27
forum: Ubuntu Cloud and Juju
---

### Post by hofmannj-fisp on 2020-03-27
Hi there,

really hoping that someone may have the same issues and can maybe help me out with this. We're using a landscape on-prem installaion for quite a while now (> 1 year) and i am constantly having problems regarding the clients. Currently its again that the client will not take the orders from the landscape-master, neither update nor reboot or something like this. I've had this in the past sometimes with only a few of the machines and could just fix it with re-installing the landscape-client, but now most of my client-machines (actually all these are servers) dont work anymore. 
I Checked the broker log and found the following, but i am not sure if it has something to do with it:
```
During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/landscape/client/broker/transport.py", line 82, in exchange
    message_api)
  File "/usr/lib/python3/dist-packages/landscape/client/broker/transport.py", line 56, in _curl
    headers=headers, cainfo=self._pubkey, curl=curl))
  File "/usr/lib/python3/dist-packages/landscape/lib/fetch.py", line 118, in fetch
    raise PyCurlError(e.args[0], e.args[1])
landscape.lib.fetch.PyCurlError: Error 77:
2020-03-23 06:26:33,104 INFO     [MainThread] Message exchange failed.
2020-03-23 06:26:33,104 INFO     [MainThread] Message exchange completed in 0.02s.
2020-03-23 06:27:33,201 INFO     [MainThread] Starting urgent message exchange with https://$server.$domain/message-system.
2020-03-23 06:27:33,215 ERROR    [PoolThread-twisted.internet.reactor-1] Error contacting the server at https://$server.$domain/message-system.
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/landscape/lib/fetch.py", line 116, in fetch
    curl.perform()
pycurl.error: (77, '')
```

Also i always have the message that none of my servers could connect to the landscape-master. This is a prolem i've had from the start and i dont know how to fix this. Firewall should be fine and i dont see any problems -.-

Regards

Jonas

---

### Post by hofmannj-fisp on 2020-06-30
Found the solution!!!
Uninstalled landscape on every machine, deleted the landscape-master, cancelled the incredibly expensive subscription and moved to SuSE-Uyuni. Based on salt, OpenSource, Free, Better docs & support and...to mention that, better forum.

---

