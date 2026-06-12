---
title: "Selective PolicyKit control for manual networking"
date: 2008-05-11
forum: Security
---

### Post by fishtoprecords on 2008-05-11
Since Hardy has PolicyKit, it gets in the way of my needs to adjust the network setup manually for work, home, wired, wireless, etc.

There is a 'unlock' button, but I don't need to constantly unlock and enter a password.

How do I disable it, or enable it forever? Once I've logged in, I don't want any extra security helping me on the networking side.

I've followed all the links I can find from googling PolicyKit and there seem to be only very limited man pages. I don't see how to use it, edit it, or what ties the "Manual networking" application into PolicyKit

Thanks
Pat

---

### Post by davey.moore on 2008-05-15
I think i just found a method, you go to
[B]
System > Administration > Authorizations[/B]

and once there
[B]
org > freedesktop > systemtoolsbackends > Manage system configuration[/B]

Once there you click on **Grant, select your user**, and I chose "**Must be in active session on local console**", because at the moment I don't need more than that.

This gives password-free access to many more things (as you can imagine) than the network-manager.

I am using this method though until i find something specific.

---

### Post by fishtoprecords on 2008-05-15
Thanks. I agree its a bit of a sledgehammer, but it works. When we learn how to be more specific, we should update this thread.

---

### Post by ouro on 2008-08-20
My problem was well described by colbster on [http://ubuntuforums.org/showthread.php?p=5627700#post5627700](http://ubuntuforums.org/showthread.php?p=5627700#post5627700)
and is related to this topic. I was testing with Authorizations too, but as davey.moore says, this solution give access to more things than I want.

---

