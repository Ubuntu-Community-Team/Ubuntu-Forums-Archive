---
title: "OpenArena Multiplayer?"
date: 2009-03-17
forum: The Cafe
---

### Post by kevin11951 on 2009-03-17
I just found out about open arena a few days ago, and I cant stop playing it!

the only thing I cant do is have more than 12 people on a lan game, and 12 is not enough people for what I am planning (2 rooms of 30 kids each playing on opposite teams).  Any help? :)

---

### Post by mips on 2009-03-17
Just an idea, dunno if it will work though as I have never used OpenArena, but edit your server config file and change the ***sv_maxclients*** parameter to **60** or how many clients you need and see if that works.

[http://openarena.wikia.com/wiki/Servers#Example_linux](http://openarena.wikia.com/wiki/Servers#Example_linux)
[http://www.sp1r1t.org/networks/q3_install/q3_linux_server_howto.php#step4](http://www.sp1r1t.org/networks/q3_install/q3_linux_server_howto.php#step4)

I suspect you would need a powerfull machine to act as a server, preferably headless with no X etc. Look at using a multicore machine and set your r_smp parameter according to the amount of cores it has.

Also look at the network config to set rates etc else you might have issues. [http://openarena.wikia.com/wiki/Tweak](http://openarena.wikia.com/wiki/Tweak)

Edit: Oops, maybe this does not apply to LAN play but if you want to consider setting up a server then follow the above.

---

