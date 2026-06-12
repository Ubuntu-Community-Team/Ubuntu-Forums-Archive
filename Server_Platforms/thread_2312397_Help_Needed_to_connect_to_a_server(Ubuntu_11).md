---
title: "Help Needed to connect to a server(Ubuntu 11)"
date: 2016-02-04
forum: Server Platforms
---

### Post by midhun4 on 2016-02-04
I am trying to connect my client computer(Ubuntu) to server running ubuntu 11.10.I am a newbie hre,pls guide me step by step process as to how to do it?
My shared folders are visble in server and i can acces files from server machine,but when i try to connect to server from my pc,its nt getting connected.
Tried SSH too.Or may be i dnt know to use t .
Some folders are being shared in server,but when i tried sharing a new folder It says I need to install updates apt-get updates?is it ok to update?because since its server am worried.
But even then the shared folders in server cannot be accessed by my machine.PLS HELP !!!!!

Is it because the server machine needs to install updates?Pls guide me asap

---

### Post by matt_symes on 2016-02-04
Hi

> I am trying to connect my client computer(Ubuntu) to server running ubuntu 11.10

Ubuntu 11.10 is 'End Of Life', actually very EOL :)

You'll want to upgrade to a supported version. 

You'll get support then.

Kind regards

---

### Post by midhun4 on 2016-02-04
> **matt_symes said:**
> Hi



Ubuntu 11.10 is 'End Of Life', actually very EOL :)

You'll want to upgrade to a supported version. 

You'll get support then.

Kind regards

I know t,But its my office machine,I am helpless and need help on it.

---

### Post by matt_symes on 2016-02-04
Hi

> **midhun4 said:**
> I know t,But its my office machine,I am helpless and need help on it.

OK.

I'll move this thread to the **Server Platforms** sub forum and see if anyone can help you.

You really want to speak to whomever administers that server and get them to upgrade though.

You'll get no security updates for that release and the server administer is being incredibly shortsighted by not upgrading. You have a huge security hole sitting in your office. 

You may find it difficult to get support here as most people who run servers, will run an LTS sever release.

Kind regards

---

### Post by Habitual on 2016-02-04
> **midhun4 said:**
> My shared folders are visble in server and i can acces files from server machine,but when i try to connect to server from my pc,its nt getting connected.

```
ssh -vv user@server.ip
```
output should help the server admin help you get connected.

Contact the Server Admin, or your Network Admin.

---

