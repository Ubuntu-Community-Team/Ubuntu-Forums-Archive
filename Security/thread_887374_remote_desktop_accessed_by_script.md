---
title: "remote desktop accessed by script"
date: 2008-08-12
forum: Security
---

### Post by antm88 on 2008-08-12
Hi,
I just thought I'd report this, I'm sure it's probably been mentioned before but hey:
A few days ago, I was using my computer, terminal opens and a script started running. Thankfully it was a windows script involving deleting system32 etc, but if it had been a script able to run in linux, it would be able to do a good amount of damage (something like rm -R ~/*)

I had hastily enabled remote desktop the day before which would have been how it happened, but I really wasn't expecting remote desktop to open itself up to the internet - sure I should have read the settings properly, but it just doesn't seem a good idea to have it default to open to anyone on the outside. Anyone who wants to set up remote desktop from the internet IS going to change the settings anyway so why not set remote desktop to default to local network only?

I'd always taken it for granted that ubuntu was pretty secure for the basic user and this was a bit of an eye opener!

Ant

---

### Post by hyper_ch on 2008-08-12
why do you run a desktop on a server?

---

### Post by antm88 on 2008-08-13
huh?
I never said I was running a server...?

---

### Post by hyper_ch on 2008-08-13
my mistake... thought you posted in the server section.

---

### Post by osjak on 2008-08-13
> **antm88 said:**
> Hi,
I had hastily enabled remote desktop the day before which would have been how it happened, but I really wasn't expecting remote desktop to open itself up to the internet - sure I should have read the settings properly, but it just doesn't seem a good idea to have it default to open to anyone on the outside. Anyone who wants to set up remote desktop from the internet IS going to change the settings anyway so why not set remote desktop to default to local network only?

Ant
If you have a local network, then you had to setup a port forward on your router to get your system exposed to Internet. That implies you made a conscious decision to do it, no default configuration can prevent this.

If you don't have a network and your computer is connected directly to the Internet, then... well, as soon as you open a port, it becomes exposed to everyone. There's no way around it.

Yes, Ubuntu is pretty secure, it doesn't come with remote desktop installed by default. Not to bash you too much, you are correct - you needed to set up your remote desktop server properly. That's what it comes down to. It would help you to get a router as well, even if you only have one computer at your network. It will separate your inner network from the Internet.

---

