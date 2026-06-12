---
title: "some questions about python3-maas-client"
date: 2018-11-21
forum: Ubuntu Cloud and Juju
---

### Post by khbkhb on 2018-11-21
Ubuntu 16.04.5 LTS, installed maas and all the trimmings.

[https://docs.maas.io/2.4/en/manage-libmaas](https://docs.maas.io/2.4/en/manage-libmaas) 

1) Why is python3-maas-client still in alpha after all these years?

2) [http://maas.github.io/python-libmaas/client/index.html](http://maas.github.io/python-libmaas/client/index.html) has example code which fails with "from maas.client import login ImportError: No module named 'maas'" Cloning via git clone [https://github.com/maas/python-libmaas.git](https://github.com/maas/python-libmaas.git) has lovely test code, such as test_maas_client where the imports are from "apiclient.maas_client" (replacing the maas.client doesn't work either).  

While I'm aware of the advice to use virtualenv/pip/pypi but I need to do this work in a segregated lab, where we've only got u16 (and no direct external internet connectivity). Isn't it possible to use the client library that's in the repository? If so, how come we don't have examples which work "out of the box" with the standard installable maas packages?

---

