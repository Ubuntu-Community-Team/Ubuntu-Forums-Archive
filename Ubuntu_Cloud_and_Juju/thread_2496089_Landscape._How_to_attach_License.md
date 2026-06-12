---
title: "Landscape. How to attach License?"
date: 2024-03-13
forum: Ubuntu Cloud and Juju
---

### Post by kugane on 2024-03-13
Hi &#128075;,

I bought today 8 Ubuntu Pro (infra-only) licences.
Added my Landscape onprem Server to the subscription, but Landscape wont recognize them.

"pro status" shows that the VM is attached and pro works, except the seats in Landscape.

Tested on Server 22.04, with latest stable landscape-ppa and Beta.
Nothing works

---

### Post by #&amp;thj^% on 2024-03-13
Sorry if you have already seen this, but recheck: [https://ubuntu.com/landscape/docs/manual-installation](https://ubuntu.com/landscape/docs/manual-installation)
Dose the file exist?  check with>>> "tac /etc/landscape/license.d"


Also "/etc/rabbitmq/rabbitmq-env.conf" needs to read like:
```
NODE_IP_ADDRESS=127.0.0.1
```
That's new in 22.04, Then restart it:
```

sudo systemctl restart rabbitmq-server
```
That Link has a lot of help listed.

---

