---
title: "I need a free server for evolution groupware."
date: 2009-11-22
forum: Server Platforms
---

### Post by t.rei on 2009-11-22
Hi,

I am as of now evaluating the possibility of deploying evolution in an small buisiness environment.  The aim is to replace a windows XP and Exchange setup. The reasons being primarily costs, reliability and stability for at least 4 years. (I wont go any further as development is at an amazing speed currently, and you never know what's in the cloud ;) ).

So I might want to deploy a complete ubuntu based environment.

To the average user that means: Openoffice, Evolution, Firefox. Those three should cover about 9/10 work-hours.

Now the thing that puts a hurt to me: 
**What server can I use to have the complete functionality of evolution while remaining open and free?**

If nothing is available: What commercial solution is the complete backend to evolution?

I decided to first find or get an answer to this problem, before spending too much time figuring out everything else. (Roaming, File-Storage, VPN, ...)

Thanks for any help.

---

### Post by crankyadm1n on 2009-11-22
[Zimbra]("http://www.zimbra.com/") maybe a good option for you.

---

### Post by t.rei on 2009-11-22
Thanks, I'm doing a test-installation as I type.

But, to get this right - there is no 'official' canonical driven/supported server backend? (wonders, as I understood it, companie-support is where the $$$ comes from?)

---

### Post by i.r.id10t on 2009-11-22
openexchange, citadel, zimbra and others

---

### Post by t.rei on 2009-11-22
Interesting - I'll check out citadel first, as it is in the repositories. That should make maintaining it (patching it) more easy.

BTW - Zimbra needs a LTS install. Need to get that one before I can even test that. Thank god for VMs.

*update1: citadel* Ok, citadel fails the test by not being able to run with evolution on a fully operational basis (experimental groupdav plugins not being the way to go) So... off to the next candidate.

*update2: open x-change* Ok, openexchange fails my first "don't be a pain in the a*se" test. I might need to try running the 9.04 version though. But enough for today. 

So far not happy about the simple lack of any ubuntu-provided backend for groupware that gets you to the point where the real work ist maintainance (users, documents, mail, lists, ... aka 'content').

---

### Post by t.rei on 2009-11-23
Small update for anyone interested:

So far the most reliable configuration for groupware on ubuntu was to install everything needed for and kontact itself and run it against a kolab2 server.

Not pleasing really. But working.

---

### Post by Denbert on 2009-11-23
> **t.rei said:**
> 

The aim is to replace a windows XP and Exchange setup. The reasons being primarily costs, reliability and stability for at least 4 years. (I wont go any further as development is at an amazing speed currently, and you never know what's in the cloud ;) ).



Why not Google Apps? Below 25 users its free, and very stable :-)

---

