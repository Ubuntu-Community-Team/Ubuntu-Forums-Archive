---
title: "need help installing server"
date: 2008-08-30
forum: Server Platforms
---

### Post by MyR on 2008-08-30
I'm trying to install ubuntu 8.04.1 server on the used dell gx1 I just purchased at a garage sale.  P3 600 MHz, 128mb ram

When I attempt to install, I get an error on the getting installation files from CD step. (something like that) It says failed to read files from disc. Retry won't work.  Going back to the detect and mount CD drive step doesn't work. same error.

I booted the CD on my laptop and checked the disc integrity -- no problems there.

I tried using a USB cd drive to boot, but the bios is too old for that.  I would make a bootable usb device but I bet that would be a waste of time.

I started a memtest but frankly didn't want to wait for it to complete. The first 8% is error-free :]

It appears as if the previous owner recently installed win xp. So it's not a brick, right?

I just want to get a base system installed to use as a server.  Is the 128 ram not enough?  Maybe I should try another distro?

Any ideas?

EDIT: incidentally puppy linux doesn't load either. DSL does load however and also detects my ethernet :D

---

### Post by windependence on 2008-08-31
I believe Ubuntu has an alternate install CD you can try (usually CD2) to boot and then it will ask you to insert CD 1.

Also, get into the bios and make sure it is set up to boot from the CD first. Older Dells are notorious for not having this on by default.

If that doesn't work, try FreeBSD. You can get help [here.]("http://daemonforums.org/index.php")

Hope this helps.

-Tim

---

### Post by kitterma on 2008-08-31
128MB is not enough:

[http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)

---

### Post by windependence on 2008-08-31
You're right but the CD should at least attempt to boot.

-Tim

---

