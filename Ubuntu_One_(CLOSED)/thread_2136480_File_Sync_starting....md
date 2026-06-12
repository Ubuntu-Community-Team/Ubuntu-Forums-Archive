---
title: "File Sync starting..."
date: 2013-04-17
forum: Ubuntu One (CLOSED)
---

### Post by sefs on 2013-04-17
Hi all

I am on 12.04 lts 64 bit.

I installed UOne but in the Cpanel it says "File Sync starting..." and never changes.
No files synce

```

:~$ u1sdtool --status
State: READY
    connection: With User Not Network
    description: ready to connect
    is_connected: False
    is_error: False
    is_online: False
    queues: WORKING

```

---

### Post by GUZZLR on 2013-04-27
Mine does this too when I Open Ubuntu One on the Windows 7 (64bit) Machine.  I tried a small folder to sinc...only about 6MB.  it never got past the "File Sync Starting".  I then got fed up with it (after day one) and stopped the sync.  Now, it only reads "Getting information, please wait..." so i wait, and wait, and wait...

---

### Post by sefs on 2013-04-27
Hi,

Have does it work for you in ubuntu?

I realized I needed to install network-manager.  Since I don't use it, I additionally stopped it from running and set it's override to manual so it would not start at boot,  but strangely enough Ubuntu one seems to be dependent on having network-manager installed.  It's working for me now.

---

### Post by GUZZLR on 2013-04-28
Interesting, can you post steps on how you got U1 to work...You lost me on the network manager part.  I'm experimenting with Ubuntu 12.10, and trying to get off of Windows 7

---

### Post by sefs on 2013-04-28
Keep in mind I did not have network-manager installed.
So....

1/
sudo apt-get install network-manager

2/
sudo stop network-manager  (will probably give an error if it has not started which is usually case if just installed)

3/
sudo touch /etc/init/network-manager.override

4/
sudo nano /etc/init/network-manager.override (to edit this file)

5/
type "manual" in the editor without the quotes and save it with crtl-x

6/
reboot

after that I realized that it was now fully starting up and syncing.

---

