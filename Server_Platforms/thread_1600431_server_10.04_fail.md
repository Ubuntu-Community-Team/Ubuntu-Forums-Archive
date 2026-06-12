---
title: "server 10.04 fail"
date: 2010-10-18
forum: Server Platforms
---

### Post by Conundrum69 on 2010-10-18
Ok, I am new to Ubuntu and looking to make my home a windows free home, I have a few computers that I have installed ubuntu on and have played around with, the next step that I was trying to do was setup a home server. I am using a dell desktop that I had laying around and installed server 10.04 on it. Install went fine, could ssh into it from my desktop fine. The problem that I ran into was when the power went out and I tried to start the server back up all I got was a black screen after post. I thought that the install might have corrupted so I did a reinstall. I then restarted the server after it was all up and running and once again all I got was a black screen. I don't know if I'm doing something wrong or if its my server thats messing up. Any and all help would be appreciated.

---

### Post by dtfinch on 2010-10-19
What happens if you press the 's' key (to skip waiting for devices to mount) during the black screen? If you have anything in your fstab that's no longer available, like a usb drive that's no longer plugged in (or plugged in but somehow mapped to a different device name than before), it could be stuck waiting for the device to appear. It could also be doing a fsck, but it shouldn't take very long on a new server.

---

### Post by Conundrum69 on 2010-10-19
ok, tried pressing the "s" key and I am still getting nothing, as it stand when I start the server up it goes through post then the screen goes into standby(orange power light). The only things that are connected to the server are the screen, mouse, and keyboard.

---

