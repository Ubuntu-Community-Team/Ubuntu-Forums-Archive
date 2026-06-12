---
title: "sshd - what if it's NOT runnung?"
date: 2009-02-21
forum: Server Platforms
---

### Post by mistypotato on 2009-02-21
sshd does not appear to be a runnung service on my server?

Is this a default item installed during server installation or is it something that SHOULD be installed afterwards?

Just not sure what all this sshd talk is about?

thanks!

---

### Post by cariboo on 2009-02-21
The ssh client is installed by defualt, you have to install openssh-server manually eg:

```
sudo apt-get install openssh-server
```

The  default setup allows you to conect to the server using your user password:

```
ssh user@server
```

enter your password when asked.

Jim

---

### Post by Iowan on 2009-02-21
> **mistypotato said:**
> Is this a default item installed during server installation or is it something that SHOULD be installed afterwards?It's an option that *can* be installed during setup, but it can be installed afterwards, too. 
**cariboo907** already mentioned how.

---

