---
title: "Which Version Should I use?"
date: 2011-07-14
forum: Server Platforms
---

### Post by mcarrara on 2011-07-14
I have six servers running 8.04LTS and feel it is time to upgrade.  The natural choice would be 10.04 LTS.  However that has been around for a while and I wonder if there will be another LTS version soon.  Or should I go with 11.04?  My servers run either samba or LAMP stacks.  What would you recommend?

Mark

---

### Post by linuxnizer on 2011-07-14
I would expect the next LTS to be out  Q2 2012 . It's your call whether you want to wait or get 10.04 today.

---

### Post by ruffEdgz on 2011-07-14
I would use (if you can): Ubuntu 10.04 LTS 64bit

---

### Post by wojox on 2011-07-14
You can upgrade from LTS to LTS fairly simple. So 10.04 would be my choice. Then wait for 12.04.

---

### Post by arrrghhh on 2011-07-14
> **wojox said:**
> You can upgrade from LTS to LTS fairly simple. So 10.04 would be my choice. Then wait for 12.04.

This ^^.

Stick to LTS on server editions, then just upgrade when the next LTS is out - April 2012 as stated above.

---

### Post by capscrew on 2011-07-14
> **mcarrara said:**
> I have six servers running 8.04LTS and feel it is time to upgrade.  The natural choice would be 10.04 LTS.  However that has been around for a while and I wonder if there will be another LTS version soon.  Or should I go with 11.04?  My servers run either samba or LAMP stacks.  What would you recommend?

Mark

When I updated from 8.04 to 10.04 I was not sure how the change would go.  There were (are) changes.  For one thing the switch over to Upstart affects Samba.  There is a bug regarding the starting of NMBD that you will have to work through.  Also GRUB becomes GRUB2.

 I would not go initially from 8.04 LTS to 12.04 LTS myself.  The prudent thing would be to do one server at a time and use 10.04.2 LTS.  If all goes well you can update to 12.04 at a later date.

---

### Post by arrrghhh on 2011-07-14
> **capscrew said:**
> When I updated from 8.04 to 10.04 I was not sure how the change would go.  There were (are) changes.  For one thing the switch over to Upstart affects Samba.  There is a bug regarding the starting of NMBD that you will have to work through.  Also GRUB becomes GRUB2.

 I would not go initially from 8.04 LTS to 12.04 LTS myself.  The prudent thing would be to do one server at a time and use 10.04.2 LTS.  If all goes well you can update to 12.04 at a later date.

You can't go 8.04 -> 12.04 - that upgrade path is **not** supported.  Just like you can't got 9.04 -> 10.04.  Gotta go to 9.10 then to 10.04...

---

### Post by dFlyer on 2011-07-14
I would use 10.04 LTS for a server, if you decide to upgrade. The next LTS will be out 12.04.

---

### Post by capscrew on 2011-07-14
> **arrrghhh said:**
> You can't go 8.04 -> 12.04 - that upgrade path is **not** supported.  Just like you can't got 9.04 -> 10.04.  Gotta go to 9.10 then to 10.04...

Are you sure?  I went from 8.04 to 10.04 on my server.  I was under the impression that you could go from an LTS to any LTS.  No intermediate steps.

---

### Post by arrrghhh on 2011-07-14
> **capscrew said:**
> Are you sure?  I was under the impression that yu could go LTS to LTS.  No intermediate steps.

Yes of course you can.  But you are saying skip 10.04 and go 8.04 -> 12.04.  That's not supported, you have to go 8.04 -> 10.04 -> 12.04.  Which 8.04 folk need to upgrade soon, I think support is ending for that on server soon...

---

### Post by dFlyer on 2011-07-14
You can go 8.04 to 10.04. I don't think you can go 8.04 to 12.04. To go to 11.04 you will have to go 8.04 > 10.04 > 10.10 > 11.04.

---

### Post by capscrew on 2011-07-14
> **arrrghhh said:**
> Yes of course you can.  But you are saying skip 10.04 and go 8.04 -> 12.04.  That's not supported, you have to go 8.04 -> 10.04 -> 12.04.  Which 8.04 folk need to upgrade soon, I think support is ending for that on server soon...

That's good to know.  Only one LTS to the next.  I wasn't recommending that jump anyway.  I think th OP needs to move to 10.04.2 for sure.  ! would wait for 12.04 to settle down anyway (maybe 12.04.2) in 2013.  I'm not an early adopter for production stuff anyway.

---

### Post by arrrghhh on 2011-07-14
> **capscrew said:**
> That's good to know.  Only one LTS to the next.  I wasn't recommending that jump anyway.  I think th OP needs to move to 10.04.2 for sure.  ! would wait for 12.04 to settle down anyway (maybe 12.04.2) in 2013.  I'm not an early adopter for production stuff anyway.

Indeed.  I keep my server on LTS releases, and wait for the .1 release of the next LTS version before going to it.  Waiting for the .2 release is never a bad idea either - just don't wait so long that you won't be able to upgrade (easily) :p.

---

### Post by mcarrara on 2011-07-15
I have decided to take what seems to be the majority idea which is to upgrade one server to 10.04 and see how it goes.  If all goes well then the rest will be upgraded to 10.04 this summer.  Thanks for the input.

Mark

---

