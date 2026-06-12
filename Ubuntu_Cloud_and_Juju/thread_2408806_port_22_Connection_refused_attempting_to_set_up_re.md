---
title: "port 22: Connection refused attempting to set up remote access."
date: 2018-12-23
forum: Ubuntu Cloud and Juju
---

### Post by lowergroundfloor on 2018-12-23
Hi

I rented a server running ubuntu 17 for some work that I need to get done. But I am horribly out of depth.

After 40 minutes, I can no longer login into my server from my local computer which is a Mac. All I would like is to be able to remotely login to the server using VNC. Not knowing what I am doing and trying to follow guides has lead me to changing something I shouldn't have.  The support team from the company I rented the server can login to root and the firewall on my Mac is off, if that helps.

Trying to access to the server responds with this.

port 22: Connection refused

And this is the output I was advised to get

xxxxx:~ xxxxxx$ ssh -v foo@bar
OpenSSH_7.7p1, LibreSSL 2.7.3
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 48: Applying options for *
debug1: Connecting to bar port 22.
ssh: Could not resolve hostname bar: nodename nor servname provided, or not known

Does anyone know how to fix this?

Please Pm me if you could help me set up VNC, for something in return. 

Thanks!

---

### Post by The Cog on 2018-12-23
"Could not resolve hostname bar" is different to "Connection refused". 

"Could not resolve hostname bar" means that your local comnputer couldn't look up the hostname "bar" to convert it into an IP address. This is a problem with your computer - either it has a problem in general looking up names into IP addresses, or (more likely) you have the wrong name. You didn't actually try to connect to a server called "bar" did you?

"Connection refused" means just that - the server you are trying to connect to is refusing connections, probably because the SSH server is not running.
If the machine is no longer running its SSH service, you probably need to get their support people to fix it, and they may tell you all they can do is revert it to a fresh install.

---

### Post by coffeecat on 2018-12-23
> **lowergroundfloor said:**
> Please Pm me if you could help me set up VNC, for something in return. 

Please do not ask for support by means of PM. This is a publicly accessible forum and community resource where support discussions and solutions may be of value to many more than just the person seeking help. 

But to your question:

> **lowergroundfloor said:**
> I rented a server running ubuntu 17

Are you sure? If so, ask for you money back. Both Ubuntu 17.04 and Ubuntu 17.10 were interim releases which each had only 9 months' of support and updates. They are both now obsolete. Anyone making money out of a resource built on an obsolete operating system should not be doing so, imo.

> **lowergroundfloor said:**
> The support team from the company 

Is that what they call themselves? If they really are running one of the 17.* releases, then I can think of a few other choice descriptions for them!

I stress **if** you are renting a server running 17.*, then I suggest you find a company that is running one of the supported LTS (long-term support releases, 16.04 or 18.04. 14.04 still has a few months's support left, but you would probably be better off with one of the newer releases.

---

### Post by lowergroundfloor on 2018-12-23
Apologies.

Thanks for informing me about the issue with ubuntu 17. Ultimately its my fault, as I just assumed it was the latest release based on what they were offering. I have contacted them about changing that - hopefully they don't charge me to have this done.

I just tried the release upgrade command but that can't be done from the terminal on my Mac.

---

### Post by lowergroundfloor on 2018-12-23
[COLOR=#000000]Brilliant! 'ssh -v' worked! I thought foo@bar was a command of some sort hehe, so thanks for bringing that to my attention[/COLOR]:)

---

### Post by The Cog on 2018-12-23
Good news. 
You can mark the thread solved using the pull-down Thread tools menu top-tight.

---

