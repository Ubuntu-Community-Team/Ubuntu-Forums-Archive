---
title: "Error when shutting down server"
date: 2007-02-04
forum: Server Platforms
---

### Post by greybeardjsy on 2007-02-04
I'm a newcomer to Ubuntu / Linux (please be patient). I have installed Edgy 6.10 server on a Compaq Pentium 3 and given it a fixed IP address and patched into my Netgear wireless router - the intention is to use it as a network file share (also have a Ubuntu 6.10 desktop).

When I first installed the server I was able to shutdown the server from the user account using -

sudo shutdown now

Now when I do this I get and error 

myusername$ init: rcl process (3453) killed by signal 15

followed by the root prompt.

The only way I can now shutdown is by physically turning off the server.

Any ideas what I should do / where I should look to find out how to resolve this?

---

### Post by greybeardjsy on 2007-02-04
Not sure what was happening before but I have just started the server up again and I find that I can shutdown properly either from root, or using sudo shutdown from my user account.

So - I probably was doing something wrong - but it seems to have sorted itself out.

---

### Post by Ramses de Norre on 2007-02-05
You need to use _sudo shutdown **-h** now_ to halt and _sudo shutdown **-r** now_ to reboot.
From the man page: > If no  options  are  given,  the maintenance event is sent. and that's why you got that root prompt.

---

### Post by greybeardjsy on 2007-02-05
OK - many thanks I will use this next time.

---

