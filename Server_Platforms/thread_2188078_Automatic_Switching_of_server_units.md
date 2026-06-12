---
title: "Automatic Switching of server units"
date: 2013-11-15
forum: Server Platforms
---

### Post by clb199 on 2013-11-15
[COLOR=#ff0000]Dear sirs,

     I check the boards before I wrote.
I have only made a few posts so plesae be patient with me.
I am a "mid level" user...not a newbie, far from an expert.

I have a lamp server on a T1 using a static IP Address.
I have 3 open static IP addresses I can use if need be.
I want to set a second server as an automatic switch over / backup unit should the first one fail.
This is where I need help.

I need input/ advice on how to proceed.  
If possible, could you please take a few minutes of time and point me in the right direction. 

Thank you for your time,

clb199[/COLOR]

---

### Post by SeijiSensei on 2013-11-15
I'd start here: [http://www.linux-ha.org/wiki/Main_Page](http://www.linux-ha.org/wiki/Main_Page)

---

### Post by nerdtron on 2013-11-15
What service are you running on your server? The setup for automatic failover (or load balancing if you will) may differ from each service, i.e apache vs mysql etc.

---

### Post by houstonbofh on 2013-11-15
Since you have 3 IPs another easy option is CARP.  [http://laurentbel.com/2012/04/04/simple-failover-cluster-on-ubuntu-using-carp/](http://laurentbel.com/2012/04/04/simple-failover-cluster-on-ubuntu-using-carp/)

Each server has a real IP, and there is a virtual IP that either can answer.  If it is an interactive server, you may need to set up rsync between the, as well.

---

