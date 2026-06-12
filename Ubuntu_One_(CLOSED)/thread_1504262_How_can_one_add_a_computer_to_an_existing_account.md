---
title: "How can one add a computer to an existing account?"
date: 2010-06-07
forum: Ubuntu One (CLOSED)
---

### Post by ManfredKlinglmair on 2010-06-07
Hi,
when registering my account online (I use Ubuntu 10.4), I for some reason did not get the "Confirm Computer Access" screen (no, I did not overlook it!).
In the Ubuntu One client, my machine is listed as <local computer>, and I cannot figure out how to add this computer to my existing account now.

How do I do this?

Thanks a lot,
Manfred

---

### Post by Palanthas on 2010-06-07
You actually reminded me that I hadn't re-connected my machine since I installed 10.04... so thanks!

Anywho, I just connected my 10.04 machine, (as I said above) and had no issues. Here's what I did and and seemed to work correctly...

  System>Preferences>Ubuntu One - This opened up the Ubuntu One Preferences window and a few seconds later Firefox opened a new tab (already had FF running) to Ubuntu One which asked me if I wanted to add this machine to the account, clicked yes of course and maybe another button, (terrible about remembering some specifics) and the machine was added.

  Back to the Ubuntu One Preferences window, I clicked on the "Devices" Tab and on the bottom clicked "Connect" and presto! All was set and on their way to being synchronized.

Hope that Helped... :P

---

### Post by ManfredKlinglmair on 2010-06-08
According to the FAQ on the Ubuntu One site, that should happen, only that no window opens, and the Ubuntu One client reports an error and closes.
Which kind of sucks, since Ubuntu One was one of the reasons I switched to the OS.

Any other way of connecting?

Oh, and before I forget, thanks anyway!

Manfred

---

### Post by duanedesign on 2010-06-08
There has been a bug that is affecting some Lucid users while adding new computers. When following [the steps here]("https://one.ubuntu.com/support/installation/"), at step 8 the add computer button was not there. The workaround for that is [here.]("https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?") Basically you close the Ubuntu One Preferences, if open, and run the command:

```
 u1sdtool -q; killall ubuntuone-login; u1sdtool -c
```

This should force a web browser to open and put you at step 2 of [the process.]("https://one.ubuntu.com/support/installation/")

---

### Post by ManfredKlinglmair on 2010-06-08
Thanks.
Tried it, but to no avail. Any other workarounds? Is anyone else having this particular problem?

The error message i get if i try to connect via the client is

*[Errno socket error] [Errno 104] connection reset by peer*

M.

---

### Post by Argeroth on 2010-06-08
> **duanedesign said:**
> There has been a bug that is affecting some Lucid users while adding new computers. When following [the steps here]("https://one.ubuntu.com/support/installation/"), at step 8 the add computer button was not there. The workaround for that is [here.]("https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?") Basically you close the Ubuntu One Preferences, if open, and run the command:

```
 u1sdtool -q; killall ubuntuone-login; u1sdtool -c
```

This should force a web browser to open and put you at step 2 of [the process.]("https://one.ubuntu.com/support/installation/")

I had a similar issue and I tried what was suggested. It worked perfect for me!  Thanks alot :)

---

### Post by ManfredKlinglmair on 2010-06-09
It does not work for me... unfortunately. Does anyone know of another workaround? Please?

M.

---

### Post by azizzle on 2010-06-10
> **ManfredKlinglmair said:**
> It does not work for me... unfortunately. Does anyone know of another workaround? Please?

M.

I'm having the issue. I'm about to cancel my account and start from scratch.

---

### Post by duanedesign on 2010-06-10
> [Errno socket error] [Errno 104] connection reset by peer

That looks like you might be behind a corporate/university proxy?

---

### Post by ManfredKlinglmair on 2010-06-10
I'm not, although I am using mobile broadband, maybe that could be a reason?

I'll try connecting when using WiFi instead of 3G. Will report back. :)

---

### Post by ManfredKlinglmair on 2010-06-14
Yes!

People, if you have trouble connecting to One and you're using mobile broadband, try connecting through WiFi.

---

### Post by Ch4rl3s on 2010-06-16
I get the same problem, almost exactly the same, except mine gives an error saying connection timed out even when it opens my browser, anything going on to fix this?

---

### Post by dre12b on 2010-07-09
suggested fix worked for me...on mobile broadband.  Thanks!

---

