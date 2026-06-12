---
title: "Can't browse WEBrick/rails on Edgy server"
date: 2006-12-17
forum: Server Platforms
---

### Post by niklasro on 2006-12-17
Hi,

I can wget localhost:3000 and get the rails page for my project but I can't connect in browser from remote machine and would appreciate a suggestion on the matter.

Thanks,

Niklas

---

### Post by DevPee on 2007-08-21
I had the same problem, and after much searching figured out that running

ruby script/server

binds the server to localhost 127.0.0.1, NOT to the ip address that you will have used to connect to your machine from a remote machine.

run

ruby script/server --binding=<ipaddress>

and it might work.

---

