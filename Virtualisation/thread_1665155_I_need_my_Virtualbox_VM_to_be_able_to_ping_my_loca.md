---
title: "I need my Virtualbox VM to be able to ping my local network"
date: 2011-01-11
forum: Virtualisation
---

### Post by diablo75 on 2011-01-11
Okay, so I have Ubuntu 10.10 with Virtualbox running Windows XP inside of it.  I have a print server setup elsewhere in the house and I need my XP VM to be able to contact it.  What's the best way to do this in Virtualbox?

---

### Post by gerowen on 2011-01-11
What OS is the print server running?

First just make sure that the guest XP OS network settings are right.  Click on your VM while it's not running, click "Settings", then click "Network".  Change the "Attached to" dropdown to "Bridged Adapter".  This will allow the guest OS to pull its own IP from your router instead of your host OS, thus allowing it to see other machines on the network.  See the attached screenshot.

---

### Post by diablo75 on 2011-01-11
> **gerowen said:**
> the "Attached to" dropdown to "Bridged Adapter".  This will allow the guest OS to pull its own IP from your router instead of your host OS, thus allowing it to see other machines on the network.  See the attached screenshot.

Cool, that's what I needed thanks.

By the way, the print server is an Ubuntu machine.  I've setup another native Windows XP box to print to it and have had no problems so it should all go through the same with this VM on a bridged connection.

---

### Post by sineld on 2013-04-04
> **gerowen said:**
> What OS is the print server running?

First just make sure that the guest XP OS network settings are right.  Click on your VM while it's not running, click "Settings", then click "Network".  Change the "Attached to" dropdown to "Bridged Adapter".  This will allow the guest OS to pull its own IP from your router instead of your host OS, thus allowing it to see other machines on the network.  See the attached screenshot.

Thanks alot. You saved my life :popcorn:

---

### Post by wildmanne39 on 2013-04-05
Thread closed. Please do not post in old threads.

---

