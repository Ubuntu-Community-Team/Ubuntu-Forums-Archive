---
title: "SSHd allow only 1 instance of user"
date: 2006-12-21
forum: Server Platforms
---

### Post by PetePete on 2006-12-21
I want to only allow a user to have 1 instance of the ssh open at a time, how would i go about doing this ? also how would i specify the timeout so the server automaticly knocks out idle connections for instance when a users PC crashes and doesn't get to logout correctly?

thanks

---

### Post by darrenm on 2006-12-21
MaxStartups will only allow a certain number of connections, cant see it on a per user basis.

TCPKeepAlive should be enabled by default which will drop a severed connection.

---

### Post by PetePete on 2006-12-21
thanks for replying, TCPkeepAlive is on, lol don't know why i forgot about that considering i was configuring it yesterday, think i confused myself with the new problem.

I know you can restric the number of concurrent connections but thats not really what i want to do. Just that i saw it on another server once and wondering how i can implement that on mine :D

---

### Post by PetePete on 2006-12-22
anyone? i can't belive that no one here knows how to do this :P

---

### Post by MJN on 2006-12-22
For me at least I can't see *why* you'd want to do this?
 
I know that doesn't help but it might explain why others don't know the answer either..
 
Mathew

---

### Post by Enjeru on 2008-06-20
Sorry to revive a dead post, but does anyone know the how to do this?

---

