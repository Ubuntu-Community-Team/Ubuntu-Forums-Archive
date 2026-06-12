---
title: "Know of any good server monitoring apps?"
date: 2010-06-02
forum: Server Platforms
---

### Post by karmic-koala on 2010-06-02
Anybody know of a good server health/status/performance monitoring apps? I have only used cacti never really tried anything else.

---

### Post by arrrghhh on 2010-06-02
> **karmic-koala said:**
> Anybody know of a good server health/status/performance monitoring apps? I have only used cacti never really tried anything else.

Depends on what your needs are.  Nagios, Zenoss and NMIS are all good ones that we use.  NMIS we're trying to get rid of in favor of Zenoss however :D

---

### Post by dudumomo on 2010-06-03
I think cacti is quite good. A lot of features, a lot of customizations, etc...But a bit tricky sometimes to use it.
In my case I'm using Munin. I like it because it is easier to configure than cacti and it displays only the basic graph (Disk Usage, CPU, RAM, Load, Mysql entries, etc... but nothing too complicated).
But indeed, there are far less features than cacti. :(

---

### Post by arrrghhh on 2010-06-03
Zenoss has a cacti plugin as well!

---

### Post by Vegan on 2010-06-03
I use Webmin as it solves most problems quickly. I can also manage the servers quickly when needed.

---

### Post by wojox on 2010-06-03
[Nagios]("http://en.wikipedia.org/wiki/Nagios")

---

### Post by BobVila on 2010-06-03
Nagios. 

My experiences with Zenoss (with more than 10 devices monitored) have been awful. It's too bloaty (for lack of a better term) to use to monitor one machine, but has never scaled well IMO.

---

### Post by arrrghhh on 2010-06-04
> **BobVila said:**
> Nagios. 

My experiences with Zenoss (with more than 10 devices monitored) have been awful. It's too bloaty (for lack of a better term) to use to monitor one machine, but has never scaled well IMO.

Interesting.  They tout their system as being used by large enterprises, that have 20,000+ devices monitored.  We use nagios, but only to generate emails... I really want something with a webUI.

---

### Post by BobVila on 2010-06-04
> **arrrghhh said:**
> Interesting.  They tout their system as being used by large enterprises, that have 20,000+ devices monitored.  We use nagios, but only to generate emails... I really want something with a webUI.

My experience has only been with the free edition. Even with InnoDB and huge DB cache/file size as recommended in their forums, I've found that it pukes all over itself with 20ish clients connected. 

I'm sure that if you buy the supported version, they can fix it up to run quite nicely. Admittedly, I didn't dig super deep; just followed suggestions I found on their forums that improved performance, but never to what I thought was an acceptable level, even on beefy hardware.

---

### Post by llawwehttam on 2010-06-04
I have to admit I am a big nagios fan too.

---

### Post by arrrghhh on 2010-06-04
> **BobVila said:**
> I'm sure that if you buy the supported version, they can fix it up to run quite nicely. Admittedly, I didn't dig super deep; just followed suggestions I found on their forums that improved performance, but never to what I thought was an acceptable level, even on beefy hardware.

Perhaps that was an old version, I'm using the 'core' (read: free) version currently, and I have about 500 devices in it.  Runs great.

What do you guys do for a web front end with Nagios?  Or do you just use it to generate emails?

---

