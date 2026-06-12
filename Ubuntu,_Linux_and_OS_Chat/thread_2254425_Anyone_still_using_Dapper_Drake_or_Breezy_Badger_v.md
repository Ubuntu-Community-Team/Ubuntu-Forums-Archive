---
title: "Anyone still using Dapper Drake or Breezy Badger version of Ubuntu?"
date: 2014-11-27
forum: Ubuntu, Linux and OS Chat
---

### Post by flaymond on 2014-11-27
I just wanna see ***if ***there someone still using this 'Godfather' version. I will  be surprised if someone still using it.

---

### Post by Irihapeti on 2014-11-27
If they are, I hope it's being kept offline!

---

### Post by lisati on 2014-11-27
I have an older machine with a broken CLI install of Dapper Drake on it. And yes, it's kept offline.

---

### Post by flaymond on 2014-11-27
I still don't understand, why it must be kept offline? Is there any critical and dangerous bugs? Also, what happen if an ubuntu version support expired?

---

### Post by lisati on 2014-11-27
The reason I installed Dapper on my old machine is that it was the newest version I could get to run on it, and that was without a GUI. I'd configured it as a backup for the machine (now defunct) I was using as a webserver at the time, so visitors could at least be given a "Sorry, we're doing maintenance at the moment" web page while I was tinkering with the main machine. I stopped using it after Dapper went EOL because at some point I managed to break the Apache web server, and couldn't be bothered trying to fix it.

---

### Post by coffeecat on 2014-11-27
> **InterProg said:**
> I still don't understand, why it must be kept offline? Is there any critical and dangerous bugs?

Yes. Vulnerabilities in the kernel and in the web browser, to mention only two of the most important, discovered after an obsolete version became eol will not have been fixed.

> **InterProg said:**
> Also, what happen if an ubuntu version support expired?

You don't get any updates!

---

### Post by flaymond on 2014-11-27
Oh! I see.

---

### Post by SagaciousKJB on 2014-11-27
The kernel on those versions has had about 3 root-privelege bugs discovered.  As well OpenSSL was the broked version Debian had made, and then I think Heartbleed  has happened since then too.  So unless a user has been updating the kernel, openssl, etc. ( very hard to do since gcc would be outdated ) then yeah those machines would be pretty vulnerable.

My server ran 6.06 but it hasn't been online for a few years.  Luckily I had patched most of the aforementioned bugs, but you can only do so much once you need  newer version of gcc--or at least I could only do so much.

I thought I was a trooper having only upgraded to 12.04 from 8.04 a year or less ago.

---

