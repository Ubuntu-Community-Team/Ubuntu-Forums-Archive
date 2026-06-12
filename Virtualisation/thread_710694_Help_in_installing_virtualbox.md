---
title: "Help in installing virtualbox"
date: 2008-02-28
forum: Virtualisation
---

### Post by enoughsaid05 on 2008-02-28
Hey all

I am thinking about installing virtualbox into my ubuntu 7.1 gutsy. Any ideas how I do I get about doing it?

The last time I did it via Synaptic Manager (stupid move one) and ended up crashing everything (well no quite) and reinstalled the system (stupid move two. Could have edited /etc/group file, saving the trouble of having to reformat my disk)

So any ideas on the safest way to install the program without crashing my system?

Thanks!

---

### Post by petzworld999 on 2008-02-28
Open a terminal window and type in

```

sudo apt-get install update

```
then
```

sudo apt-get install virtualbox

```

---

### Post by 3rdalbum on 2008-02-28
Then go to System > Administration > Users And Groups and click "Manage Groups". Click "vboxusers" at the bottom of the list. Click Properties, and then put a check next to your name. Log out, log back in, and run Virtualbox and you should be right.

---

