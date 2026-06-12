---
title: "Ubuntu 20.04 on Raspberry Pi doesn’t require password for sudo"
date: 2020-07-10
forum: Server Platforms
---

### Post by rowanq on 2020-07-10
After initial setup and changing the default password, Ubuntu on raspberry pi doesn’t seem to require a password for sudo. Is this by design? After having a look at /etc/sudoers, there doesn’t seem like there is a straight forward way to make this work the way I’m accustomed to with Ubuntu desktop.
 Any ideas?

Rowan

---

### Post by LHammonds on 2020-07-11
Are you already using the root account?  I only have the earliest version of Raspberry Pi so I cannot install Ubuntu to see what its doing.

LHammonds

---

### Post by rowanq on 2020-07-11
When you burn Ubuntu Server to an SD, it creates a default user and password, both of which are “ubuntu”. You’re required to change the password on first boot. The ubuntu account appears to work like a normal user, requiring that you run root level commands through sudo.
But the OS never prompts for a password. If you run “sudo -i” you are switched to the root user.
I’m familiar with how to require a sudo password in Raspberry Pi Os by using visudo to change /etc/soduers, but the same approach doesn’t seem to work in Ubuntu.

---

### Post by LHammonds on 2020-07-11
Ah, I see.  I just re-installed my old Pi with the Raspberry Pi OS v10 and it too does not require a password when issuing a sudo command (using the default pi account).

---

### Post by rowanq on 2020-07-11
Ok, I figured it out. In /etc/sudoers.d/ is a file called "90-cloud-init-users". This needs to be be modified with visudo by typing:

   sudo visudo /etc/sudoers.d/90-cloud-init-users

. Change the one line in this file:

    ubuntu ALL=(ALL) NOPASSWD:ALL

so that it reads:

    ubuntu ALL=(ALL) PASSWD:ALL

Once saved, the default account 'ubuntu' will now require you in enter your pass to execute sudo commands.

---

### Post by LHammonds on 2020-07-11
Awesome, thanks for figuring it out and sharing it with us.  If I ever get a current generation Pi, I'm sure this will come in handy.  Just have three of the originals which I re-formatted today to revive my old project to create an authentication server, file server and a pi-hole DNS server.

Thanks,
LHammonds

---

