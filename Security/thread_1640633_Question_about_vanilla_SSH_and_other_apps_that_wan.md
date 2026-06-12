---
title: "Question about vanilla SSH and other apps that want to use it"
date: 2010-12-08
forum: Security
---

### Post by TheFr00n on 2010-12-08
Hi all,

So, I've got an Ubuntu 10.04 box (up to date) with a MySQL database that I log into remotely via an SSH tunnel. In order to make this secure, I've remapped the SSH port to something obscure, and locked down the firewall to allow only this port.

I've disabled password login, and get in via a 1024-bit RSA key, which has an attached passphrase.

Right now, it works like a charm.

However, I've become interested in trying out NoMachine NX as a way of working on the Ubuntu machine (VNC works, but is not an option). NoMachine NX requires a DSA key without a passphrase, and is not interested (as far as I know) in playing nicely with my existing RSA keys.

My question, for you security experts, is this. Do I have to scrap my existing SSH config and start fresh with NX in mind? Or is there a way around this?

Moreover, if I do that, and get NX working, will I still be able to use Putty to tunnel in as I do now, for using the database?

Sorry if these questions appear noobish.

---

### Post by bodhi.zazen on 2010-12-08
Personally I would simply ssh -X 

You almost certainly do not need to forward the entire desktop.

---

### Post by TheFr00n on 2010-12-09
Thank you for your feedback, but it doesn't really address my question.

Effectively, ssh -x is what I want to do. I don't want to forward the entire desktop, just the odd GUI app. I can do this right now, but as anyone who has attempted it over the Internet can tell you, it's unusably slow, even when using compression over SSH, largely because of the huge amount of superfluous interaction that exists between an X11 GUI and its underlying app.

NX server's main claim to fame is that it hugely accelerates X11 forwarding, partly by compression, but largely by intelligently caching re-usable data, discarding useless data, and only transmitting what is absolutely necessary. It's ssh -x, but on steroids. Hence my interest in it.

Let me rephrase my question.

I have an existing SSH setup that works beautifully with RSA keys. NX server uses DSA keys only.

Is there a way to get the two systems to co-exist, or do I have to redo my SSH config using the less secure DSA keys?

---

### Post by bodhi.zazen on 2010-12-09
> **TheFr00n said:**
> Is there a way to get the two systems to co-exist, or do I have to redo my SSH config using the less secure DSA keys?

In theory yes. In practice I personally have not been able to get freenx and ssh to play nice together.

---

### Post by TheFr00n on 2010-12-10
OK well, I guess I'll have to do a test with some old boxen lying around, since I don't want to risk borking a working setup.

If I get any insight, I'll let you know.

---

