---
title: "Upgrade OpenStack IceHouse to Mitaka on ubuntu 14.04"
date: 2017-02-14
forum: Ubuntu Cloud and Juju
---

### Post by cherva on 2017-02-14
Hello all,
currently I have OpenStack IceHouse on ubuntu 14.04 servers.
And I am looking on how to upgrade to Mitaka, but I am struggling to find any documentation.

From OpenStack I can see that you have to go one version at a time and work your way up.
Can someone point me in the right direction ?
I was thinking something like:
1) Stop all services on all nodes.
2) Upgrade Ubuntu hosts to 16.04
3) Change the cloud-archive repo to Mitaka
4) Upgrade OpenStack packages 
5) Make changes in the config files
6) Profit ?

---

### Post by cherva on 2017-02-15
Thanks to jamespage in #ubuntu-server irc channel.
The short answer is that you need to step through all of the Ubuntu cloud archive pockets for trusty - so that's juno, kilo, liberty, mitaka

If anyone has a better idea now is the time.
I will update the post when I start the upgrading.

---

