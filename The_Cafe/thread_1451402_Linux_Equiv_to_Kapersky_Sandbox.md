---
title: "Linux Equiv to Kapersky Sandbox?"
date: 2010-04-10
forum: The Cafe
---

### Post by neu5eeCh on 2010-04-10
If any of you are familiar with the Sandbox feature in Kapersky (a feature which effectively isolates the browser from the rest of the OS), just wondering if there's an equivalent in Linux. I've been googling but haven't found anything yet. I understand that the feature isn't as necessary in Linux simply by virtue of its design.

---

### Post by chriswyatt on 2010-04-10
Isn't Google Chrome sandboxed by design?

---

### Post by neu5eeCh on 2010-04-10
> **chriswyatt said:**
> Isn't Google Chrome sandboxed by design?

I don't think so. It has an inpornito mode, but that's not the same as sandboxed - but maybe you mean something else?

---

### Post by cariboo on 2010-04-10
Have a look at chroot, it probably does what you need. It is installed by default.

---

### Post by chriswyatt on 2010-04-10
> **chriswyatt said:**
> Isn't Google Chrome sandboxed by design?

Ah, yes, sorry, I was wrong.  Chrome itself isn't sandboxed but it does sandbox the web pages and plugins inside it by the looks of things:

[http://www.eweek.com/c/a/Security/Google-Chrome-Puts-Security-in-a-Sandbox/](http://www.eweek.com/c/a/Security/Google-Chrome-Puts-Security-in-a-Sandbox/)

---

### Post by neu5eeCh on 2010-04-10
> **cariboo907 said:**
> Have a look at chroot, it probably does what you need. It is installed by default.

Pretty close, but Kapersky's sandbox **completely** isolates the browser - including the users home directory. I wonder if there isn't a linux browser (not Firefox) with the same capabilities.

---

### Post by bash on 2010-04-10
> **VTPoet said:**
> Pretty close, but Kapersky's sandbox **completely** isolates the browser - including the users home directory. I wonder if there isn't a linux browser (not Firefox) with the same capabilities.

I have no idea if it is possible, but you might be able to do this with SELinux or AppArmor profiles.

---

### Post by neu5eeCh on 2010-04-10
I think I may have finally discovered the right combination of search terms. I came up with the following:

[http://www.averyjparker.com/2006/05/10/sandbox-your-browser-on-a-linux-system/](http://www.averyjparker.com/2006/05/10/sandbox-your-browser-on-a-linux-system/)

It's not the same as Kapersky but it appears, in effect, to accomplish the same. I may try it, then deliberately expose myself to some horrifically untrustworthy website. See what happens... like [Mustard]("http://ubuntuforums.org/showthread.php?t=72598"), he who deliberately infected his Wine install. What's the fun of matches if you can't play with them?

---

### Post by MaxIBoy on 2010-04-10
> **VTPoet said:**
> Pretty close, but Kapersky's sandbox **completely** isolates the browser - including the users home directory. I wonder if there isn't a linux browser (not Firefox) with the same capabilities.
Yes, a chroot jail can do that.

A large percentage of your OS might need to be duplicated within the jail. Or you can "mount" your /usr, /lib, and /bin directories within the jail. They will still be protected by permissions the way they always are, so this is safe. At the very least, a few of your /dev items will need to be mounted in this way to allow sound, full graphics, Internet access, etc. to programs which are "jailed."

You'll need to start a whole new X session running inside the jail (there may be a workaround for this, but I don't know for sure.) Downloaded files will be restricted to locations inside the jail. Non-jailed programs will see the jail and its contents as if it were just a directory.

Chroot jails can be made very convenient. You create a short shell script to mount everything, chroot in, and start the new X session. If you mess anything up, you can delete the jail altogether and start a new one quite easily. It's also completely secure. (Well, yes, I'm sure there are "jailbreak" vulnerabilities, just like on the iPhone, but otherwise it's secure.)

---

