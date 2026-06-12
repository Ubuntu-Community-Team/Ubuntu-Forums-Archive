---
title: "SSH from Connectbot to 11.10 Openssh-server"
date: 2012-03-29
forum: Server Platforms
---

### Post by mastermindg on 2012-03-29
I followed these instructions:

[https://github.com/mchelen/michaelchelen.net---old-2/wiki/android.connectbot.ssh.key.auth.howto](https://github.com/mchelen/michaelchelen.net---old-2/wiki/android.connectbot.ssh.key.auth.howto)

I've got my public key in ~/.ssh/authorized_keys with chmod 644. However when I attempt to connect with Connectbot it is failing. How can I troubleshoot this?

---

### Post by Insomn1a on 2012-03-29
> **mastermindg said:**
> I followed these instructions:

[https://github.com/mchelen/michaelchelen.net---old-2/wiki/android.connectbot.ssh.key.auth.howto](https://github.com/mchelen/michaelchelen.net---old-2/wiki/android.connectbot.ssh.key.auth.howto)

I've got my public key in ~/.ssh/authorized_keys with chmod 644. However when I attempt to connect with Connectbot it is failing. How can I troubleshoot this?
 

what kind of failure is connectbot saying? is it access denied, dropped, denied, etc.?

---

### Post by mastermindg on 2012-03-30
```
Attempting 'publickey' authentication with any in-memory public keys
Authentication method 'publickey' with key 'cxkey' failed
Trying to authenticate
```

Then it prompts for a password.

---

### Post by nk711 on 2012-06-27
Hi, did you solve this? I am having the same problem-- copied pub key from android device to server, appended to authorized_keys, and doesn't work.
Thanks

---

### Post by spynappels on 2012-06-27
What often happens is that the key is copied across 2 or 3 lines instead of the single line it's supposed to be.

Check the authorized_keys file and check that each key is on a single line. If it is not, remove any errant line feed/carriage returns and try again.

---

### Post by Habitual on 2012-06-27
> **mastermindg said:**
> ...chmod 644.

Mine have always been 600

---

### Post by nk711 on 2012-06-27
Thanks for the responses. I had already checked for line breaks, and my perms are 600 too. Verbose logging on the server indicates "Failed publickey". I don't know how else to debug this. I even tried re-installing Connectbot. It's probably an Android or even a Connectbot question, but I asked here since I found this unresolved thread, hoping the OP solved it.

---

### Post by spynappels on 2012-06-27
I know it does not help much, but I use ConnectBot daily to access several Ubuntu servers. I'll try to create a new key and upload it to a server to see if I can recreate the issue, but it will be tomorrow before I can do that.

---

### Post by nk711 on 2012-06-27
Thanks, that's kind of you. Give me another day to test before you go to any trouble though--

I just tried connecting to a different server and it worked, so it might be something specific to this machine (though I've not had trouble with this machine before, this is the first time I'm connecting via Android).

I want to test on my home network tonight and I'll report back.

---

### Post by nk711 on 2012-06-28
OK, everything works on my home network. Just the first server I tested it on (of course!) doesn't work. Pretty sure I did the identical procedure on all computers. If I figure out the problem on the non-working setup I'll post back here. Thanks again for help and offers of help!

---

