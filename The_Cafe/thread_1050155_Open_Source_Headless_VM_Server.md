---
title: "Open Source Headless VM Server?"
date: 2009-01-25
forum: The Cafe
---

### Post by kevin11951 on 2009-01-25
Right now I am using virtual box as an rdp VM server, but I dont like their dual licensing practices, do you know of any programs that allows for RDP, and are easy to setup? Also, my server is strictly cli

---

### Post by kevin11951 on 2009-01-25
just to add: It needs to be able to run windows xp as well...

---

### Post by toupeiro on 2009-01-25
VMWare ESXi = Free. (though I doubt its GPL'ed)  Since its basically RHEL under the hood, you shouldn't have any problems getting into it, or running it headless.

---

### Post by Dragonbite on 2009-01-25
That was what I was thinking of.

---

### Post by kevin11951 on 2009-01-25
> **toupeiro said:**
> VMWare ESXi = Free. (though I doubt its GPL'ed)  Since its basically RHEL under the hood, you shouldn't have any problems getting into it, or running it headless.

this is for a business, so, do you have to pay for business licensing?

---

### Post by toupeiro on 2009-01-26
:)

As mentioned, ESXi is free, ergo, no you have no business licensing to pay for.  However, if the business wants a support agreement, well thats another story.  Good thing is, those smart guys over at VMWare can do that whenever you're ready to. 

Enjoy!  Its powerful!

---

### Post by Dragonbite on 2009-01-26
If this is for a business willing to spend some money on it you can also look at the additional tools for managing the images as well as backing up the images even while they are running.

I don't know the details of what is available, but we have VMWare running here with multiple images (our Exchange server in one image, our SQL Servers in another, our individual development servers are on another, etc.) all currently running Windows.

For our individual development images we can RDP into them to tweak it as we need without effecting the production environment.

---

