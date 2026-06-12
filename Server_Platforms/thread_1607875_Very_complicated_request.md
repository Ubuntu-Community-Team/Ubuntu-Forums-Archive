---
title: "Very complicated request"
date: 2010-10-28
forum: Server Platforms
---

### Post by b4t3m4n on 2010-10-28
I want to setup a server with full disk encryption that I can wake remotely and put in the encrypted drive password remotely.

Its a server sitting behind a router running DD-WRT so I think I have a fair bit of ways to wake the server remotely, but I am not sure if full disk encryption is possible if I want to be able to put the password for it in remotely as well.

---

### Post by Grenage on 2010-10-28
Oh, does full disk encryption not at least bring up a basic system functionality?

---

### Post by b4t3m4n on 2010-10-28
> **Grenage said:**
> Oh, does full disk encryption not at least bring up a basic system functionality?


I believe it does but I would need SSH.  This is just a hypothetical question.  I am not sure its possible, and I haven't tried it yet because it would require I cannibalize a computer that I am not ready to do unless I know its possible.

---

### Post by Grenage on 2010-10-28
I would have thought that ssh might have been available, but I cannot say for sure.  I do have some old boxes knocking around, so I might dabble with that next week; I'll subscribe to this thread and post back if you haven't found the answer.

---

### Post by the_original_billq on 2010-10-28
Serial console connected to a terminal server attached to the same network (behind your firewall).
Open up ssh to the term server.
ssh to the serial console, and control your machine all the way from POST.
(appropriate security measures needed on term server, of course)

-Bill

---

### Post by b4t3m4n on 2010-10-28
> **the_original_billq said:**
> Serial console connected to a terminal server attached to the same network (behind your firewall).
Open up ssh to the term server.
ssh to the serial console, and control your machine all the way from POST.
(appropriate security measures needed on term server, of course)

-Bill

This is a really good idea, though I would need another computer.

---

### Post by the_original_billq on 2010-10-29
> **b4t3m4n said:**
> This is a really good idea, though I would need another computer.

Hmm, no, you need:

your existing server.

a terminal server (like [this]("http://www.digi.com/products/consoleservers/digi-passport-i-kvm.jsp")).

your existing firewall/router.

yes, you would need another computer to ssh/vnc to your server, but I assumed that's pretty much what you were doing anyway.  The i-kvm supports both serial and KVM connectivity, so you could go either way.

Disclaimer - I don't work for or have any financial ties to Digi.  I just use their products and like them a lot.

-Bill

---

### Post by b4t3m4n on 2010-10-29
> **the_original_billq said:**
> Hmm, no, you need:

your existing server.

a terminal server (like [this]("http://www.digi.com/products/consoleservers/digi-passport-i-kvm.jsp")).

your existing firewall/router.

yes, you would need another computer to ssh/vnc to your server, but I assumed that's pretty much what you were doing anyway.  The i-kvm supports both serial and KVM connectivity, so you could go either way.

Disclaimer - I don't work for or have any financial ties to Digi.  I just use their products and like them a lot.

-Bill

holy god thats expensive, I guess I misunderstood you.  I thought you meant setup a box that is a terminal server for thin clients and connect it directly to the file server via the serial port.

---

### Post by b4t3m4n on 2010-10-29
The more I think about it, the best route will probably just have a partition that is encrypted that has to be mounted manually.

---

### Post by Thirtysixway on 2010-10-29
> **b4t3m4n said:**
> The more I think about it, the best route will probably just have a partition that is encrypted that has to be mounted manually.

Seems the easiest way to do things.  Not much point in encrypting the system files, in my opinion.

---

