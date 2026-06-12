---
title: "Is this tutorial that simple?"
date: 2010-02-24
forum: Server Platforms
---

### Post by waloshin on 2010-02-24
I have decided to go with Ubuntu and not openSuse so...

To setup postfix on Ubuntu: Does this tutorial actually work?

And if so when setting up:

Again, you’ll be asked some questions:

General type of configuration? <– Internet Site
Where should mail for root go? <– Leave blank
Mail name? <– server1.example.com
Other destinations to accept mail for? <– server1.example.com, example.com, localhost.example.com, localhost
Force synchronous updates on mail queue? <– No
Local networks? <– 127.0.0.0/8
Use procmail for local delivery? <– Yes
Mailbox size limit? <– 0
Local address extension characters? <– +
Internet protocols to use? <– all

Is this how I would set mine up? Or do I leave it as server1.example.com?


General type of configuration? <– Internet Site
Where should mail for root go? <– Leave blank
Mail name? <– mail1.waloshin.com
Other destinations to accept mail for? <– mail1.waloshin.com, waloshin.com, localhost.example.com, localhost
Force synchronous updates on mail queue? <– No
Local networks? <– 127.0.0.0/8
Use procmail for local delivery? <– Yes
Mailbox size limit? <– 0
Local address extension characters? <– +
Internet protocols to use? <– all

---

### Post by volkswagner on 2010-02-24
> **waloshin said:**
> ...

Is this how I would set mine up? Or do I leave it as server1.example.com?



You should substitute your hostname for all instances of "server1", and substitute your domain name for example.com.

---

