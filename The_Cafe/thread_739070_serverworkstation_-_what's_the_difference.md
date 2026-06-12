---
title: "server/workstation - what's the difference?"
date: 2008-03-29
forum: The Cafe
---

### Post by chucky chuckaluck on 2008-03-29
for hardy, i'm going to try to do a minimal installation (you know, just a cli environment) and add x, wmii and a few apps. i've tried to do it in the past but always got stuck once i realized i had no idea what i was doing. this time, i think i'm prepared for all my past stumbling blocks. the dilemna is which to install, the server edition or a cli setup via the alternate cd?

---

### Post by hessiess on 2008-03-29
the server edition includes server programs by defalt

---

### Post by chucky chuckaluck on 2008-03-29
> **hessiess said:**
> the server edition includes server programs by defalt

so, that would be more than i need, then? that might be the answer, right there.

btw, what's a server program?

---

### Post by LaRoza on 2008-03-29
> **chucky chuckaluck said:**
> so, that would be more than i need, then? that might be the answer, right there.

btw, what's a server program?

Workstation: Applications for using the computer, anything you want. Browsers, multimedia, office, art, etc.

Server: A program (or the computer which runs it) that communications over a network.

A web server (Like Apache, which is installed when you install Ubuntu as a server) listens on port 80 and responds to HTTP requests. If you aren't going to be hosting web sites, this is not needed. It is also a security risk, having servers running, and can violate the ISP's contract with you.

Ubuntu installed as a server will also install MySQL, a database server.

---

### Post by detgar on 2008-03-29
By the sound of it, you shouldn't install with the Server CD. Better download the Alternative CD and install with the CLI option (I can't remember the exact name). After installation you'll be greeted by a console and can simply apt-get whatever you want.

---

### Post by Dr Small on 2008-03-29
I installed Ubuntu from the alternate CD as a Command Line system and then built my own server out of it. You could do the same, and build a workstation out of it.

---

### Post by chucky chuckaluck on 2008-03-29
ok, it sounds like the alternate cd, for sure. and, am i right in thinking the alternate cd for a cli installation is all the same for all the varieties of ubuntu (meaning i can download whichever iso is the smallest)?

---

### Post by LaRoza on 2008-03-29
> **chucky chuckaluck said:**
> ok, it sounds like the alternate cd, for sure. and, am i right in thinking the alternate cd for a cli installation is all the same for all the varieties of ubuntu (meaning i can download whichever iso is the smallest)?

I don't know, honestly.

The alt disk is able to install a desktop (as normal), a server, and a base system (cli). You can use whatever ISO you want I would imagine.

I would guess they are the same, as it is just the core components, but I am not sure.

Either way, it really doesn't matter, as you can install all packages with any disk anyway. So the smallest ISO would work just as well.

---

### Post by Barrucadu on 2008-03-29
I have always built a custom system with the Ubuntu Server disk, as I don't have any alternate install disks, and you can just not install any server software. It gives you a choice of what to install, so just don't select anything. The only big difference is the kernel, though sudo apt-getting linux-image-generic fixes that.

---

