---
title: "clamav"
date: 2009-04-27
forum: Security
---

### Post by boondocks on 2009-04-27
I want to install clamav-daemon.
So I click on the clamav-daemon package in Synaptic Package Manager.

It says, > You are about to install software that can't be authenticated! Doing this could allow a malicious individual to damage or take control of your system.

What should I do?

---

### Post by Sam Lars on 2009-04-28
Have you enabled any special repositories?
If not, try updating the package lists and then see if it still has that message.

---

### Post by boondocks on 2009-04-28
I have not enabled any special repositories.

I did:

```
sudo   aptitude   clean

sudo   aptitude   update

```
But that did not help.

---

