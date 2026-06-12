---
title: "Problems with Upgrade 6.10 -&gt; 7.04"
date: 2007-04-19
forum: Sun Sparc Users
---

### Post by terra3110 on 2007-04-19
Hi,

Based on the docu, i try follow commands:

sudo apt-get update
sudo apt-get uprade
sudo apt-get install update-manager-core
sudo do-release-upgrade

but i got follow error:

root@billgates:~# apt-get install update-manager-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package update-manager-core

All debs in /etc/apt/sources.list are active. Any hints ?

best regards

Frank

---

### Post by t1m on 2007-04-19
Does this help [http://www.ubuntu.com/getubuntu/upgrading ]("http://www.ubuntu.com/getubuntu/upgrading")?

Hope it does. :)

---

### Post by eentonig on 2007-04-19
traffic jams. Wait untill the hype is over before doing the upgrade. If you do it now, you'll be waiting forever before everything is downloaded.

---

### Post by pikkio on 2007-04-19
Why don't you simply do this:

$: gksudo 'update-manager -c -d'

I hope this will help you out

---

### Post by terra3110 on 2007-04-19
Hi,

I use this page to find the way for upgrading. The chapter is

"Network upgrade for Ubuntu servers (recommended)"

but on Sparc, its dont work in this way.

best regards

Frank

---

### Post by SL666 on 2007-04-19
I had this same issue, however i ran the commands you listed and it was fixed, however i did spell upgrade correctly, - i hope that is just a typo when you put it here?

Cheers Steve.

EDIT- however NOW im getting the lack of response from the upgrade server type errors :) I'll just try later.

---

### Post by ericbarch on 2007-04-19
I had the same problem. Just update your repositories and you should be good to go.

---

### Post by terra3110 on 2007-04-20
My repositories are uptodate.

During my apt-get update and apt-get upgrade, i dont get any error.

best regards

Frank

---

