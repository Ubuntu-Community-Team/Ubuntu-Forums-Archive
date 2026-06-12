---
title: "LTS server lifetime"
date: 2011-08-30
forum: Server Platforms
---

### Post by cphuntington97 on 2011-08-30
Support docs say: LTS desktop is supported for 3 years; LTS server is supported for 5 years.

What if I add ubuntu-desktop to a server install? Will support for the desktop packages end after 3 years anyway?

Clarification please...

---

### Post by arrrghhh on 2011-08-30
> **cphuntington97 said:**
> Support docs say: LTS desktop is supported for 3 years; LTS server is supported for 5 years.

What if I add ubuntu-desktop to a server install? Will support for the desktop packages end after 3 years anyway?

Clarification please...

Why would you do that?

You should never be adding a DE to Ubuntu Server.  That defeats the entire purpose of using a server.

I would say that's an unsupported setup, and a very silly one at that.  If you're needing a DE, use Ubuntu Desktop.  You can run all the same services that run on the Server Edition, on the Desktop Edition.  So you're not missing anything at all, and you really don't gain anything by installing ubuntu-desktop metapackage on top of Ubuntu Server.

Seriously, don't do it.  Again, if you need a DE Ubuntu Server edition is not the edition for you.  That's why there's other versions...

---

### Post by Enigmapond on 2011-08-30
You really answered your own question...yes correct. The LTS desktop support...no matter where you put it will end in 3 years....:)

---

### Post by amauk on 2011-08-30
Packages under "Desktop" will stop receiving bug & security fixes after three years, even if you install them on a server

Btw, there's absolutely no need to install a desktop environment on a server
Just SSH into the server

---

### Post by Habitual on 2011-08-30
> **arrrghhh said:**
> why would you do that?

You should never be adding a de to ubuntu server.  That defeats the entire purpose of using a server.

I would say that's an unsupported setup, and a very silly one at that.  If you're needing a de, use ubuntu desktop.  You can run all the same services that run on the server edition, on the desktop edition.  So you're not missing anything at all, and you really don't gain anything by installing ubuntu-desktop metapackage on top of ubuntu server.

Seriously, don't do it.  Again, if you need a de ubuntu server edition is not the edition for you.  That's why there's other versions...

+1

---

### Post by Wim Sturkenboom on 2011-08-31
> **arrrghhh said:**
> Why would you do that?

You should never be adding a DE to Ubuntu Server.  That defeats the entire purpose of using a server.

I would say that's an unsupported setup, and a very silly one at that.  If you're needing a DE, use Ubuntu Desktop.  You can run all the same services that run on the Server Edition, on the Desktop Edition.  So you're not missing anything at all, and you really don't gain anything by installing ubuntu-desktop metapackage on top of Ubuntu Server.

Seriously, don't do it.  Again, if you need a DE Ubuntu Server edition is not the edition for you.  That's why there's other versions...

I'm obviously missing something ;) What's the difference (*with regards to your sentiments about a DE on a server*) between having a desktop version with server packages and a server version with DE package :confused:

I would actually think that the latter would be preferred over the former because it only installs (or at least should only install) the absolute minimum required for a DE.

---

### Post by arrrghhh on 2011-08-31
> **Wim Sturkenboom said:**
> I'm obviously missing something ;) What's the difference (*with regards to your sentiments about a DE on a server*) between having a desktop version with server packages and a server version with DE package :confused:

I would actually think that the latter would be preferred over the former because it only installs (or at least should only install) the absolute minimum required for a DE.

If that's what actually happened, that would be fine.  But the "ubuntu-desktop" meta-package comes with *exactly* everything from the full blown Ubuntu Desktop edition.  So again - you can run all the same services on Ubuntu Desktop that you can on Server.  The Server Edition is meant to be lean and mean, no GUI to worry about updating or to bog down the system.  Only the bare essentials.  Again, if you need a GUI/DE, then the Server Edition is not for you.  That's why there are multiple editions - so you can choose which one fits your needs most.

I've seen some that go thru the hassle of trying to get gnome-core installed, but seriously - do you really need a DE?  If you genuinely feel the answer to that question is "yes", then I say just go with Ubuntu Desktop.  Your life will be much, much easier in the end - you won't be trying to fit a round peg into a square hole that way :p.

---

### Post by cphuntington97 on 2011-09-01
I thought the server version used a different kernel or something.

Anyway, I just find it really easy and elegant to connect to the server with vnc and have all my windows and processes open and efficiently grokable.

The alternative is PuTTy on Windows... and screen... I just hate to burden the server with the overhead of all the desktop stuff.

---

### Post by CharlesA on 2011-09-01
> **arrrghhh said:**
> 
I've seen some that go thru the hassle of trying to get gnome-core installed, but seriously - do you really need a DE?  If you genuinely feel the answer to that question is "yes", then I say just go with Ubuntu Desktop.  Your life will be much, much easier in the end - you won't be trying to fit a round peg into a square hole that way :p.

+1. I originally had a DE installed on my server box but found that it's way easier to just SSH in instead of doing stuff the GUI way.

> **cphuntington97 said:**
> I thought the server version used a different kernel or something.

Anyway, I just find it really easy and elegant to connect to the server with vnc and have all my windows and processes open and efficiently grokable.

The alternative is PuTTy on Windows... and screen... I just hate to burden the server with the overhead of all the desktop stuff.

The server version uses the server kernel, which is optimized for server hardware.

As for having everything running on the GUI - you can do that but on my box, I just run stuff headless and configure it via CLI or a web interface (in the case of virtualbox) I've found that more convenient for me.

---

### Post by cariboo on 2011-09-01
Another way to run gui apps on a server is to use ssh + X forwarding, eg:

```
ssh -X user@server
```

Then once at the prompt on the server type the application name.

---

### Post by CharlesA on 2011-09-01
> **cariboo907 said:**
> Another way to run gui apps on a server is to use ssh + X forwarding, eg:

```
ssh -X user@server
```

Then once at the prompt on the server type the application name.

+1. You'd need to have an X-server running, so you can use it from another *nix box or use something like XMing, or Cygwin on Windows.

---

