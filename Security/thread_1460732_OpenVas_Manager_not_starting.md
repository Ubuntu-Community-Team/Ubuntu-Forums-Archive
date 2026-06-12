---
title: "OpenVas Manager not starting"
date: 2010-04-23
forum: Security
---

### Post by firekilroy on 2010-04-23
Hi,

I'm in the process of installing OpenVAS Manager on 10.04, but when I try to start it nothing happens, no message, nothing. That's quite frustrating, to say the least. And I can't seem to find anyting on the matter when googling.

Anyone with the answer, things to try or just an encouraging comment, feel free to post here.

Thank you
/Firekilroy

---

### Post by cariboo on 2010-04-23
Have you checked /var/log/messages and /var/log/syslog?

---

### Post by bodhi.zazen on 2010-04-23
> **firekilroy said:**
> Hi,

I'm in the process of installing OpenVAS Manager on 10.04, but when I try to start it nothing happens, no message, nothing. That's quite frustrating, to say the least. And I can't seem to find anyting on the matter when googling.

Anyone with the answer, things to try or just an encouraging comment, feel free to post here.

Thank you
/Firekilroy

You need to tell us what you have done up to now ?

What how-to are you following ?

---

### Post by firekilroy on 2010-04-24
Sorry for not posting that, it slipped my mind when I sat there ripping my hair out by the fistfull.

I grep'ed the logs, but found not info about my problem at all.

As for what I've done so far:
I've just followed the instructions in the readme/install files that came with the tar's from the openvas site. No optional extras, no leather seats, no nothing. Just a bog standard install.

Thank you for replying so fast, and reminding me of the things I forgot

---

### Post by bodhi.zazen on 2010-04-24
I am not sure about compiling from source.

On Ubuntu 10.04 :

```
sudo apt-get install -y openvas-server openvas-client
```

The client is then in your menu or you would run

```
gksu openvas-client
```

Otherwise, what command are you running ?

---

### Post by firekilroy on 2010-04-24
I'm not running the GTK client, I'm going to run the CLI-client. And that one need the manager to be able to run. It's libraries -> scanner -> manager -> cli.

---

