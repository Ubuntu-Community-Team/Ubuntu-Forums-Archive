---
title: "Karmic Koala guest additions in virtualbox?"
date: 2009-10-09
forum: Virtualisation
---

### Post by dewboi on 2009-10-09
I just can't wait for the official release! I want to try out the Karmic beta in virtualbox, but I simply cannot get the Guest Additions installed. The installer stops, saying "Unable to build the kernel module."
I have seen videos of people with successful Karmic installs in virtualbox... share the love?

---

### Post by Perryg on 2009-10-10
Mine installed native.  Make sure that you have the linux-headers and build-essentials installed and try again.

---

### Post by animefan82 on 2009-10-26
> **dewboi said:**
> I just can't wait for the official release! I want to try out the Karmic beta in virtualbox, but I simply cannot get the Guest Additions installed. The installer stops, saying "Unable to build the kernel module."
I have seen videos of people with successful Karmic installs in virtualbox... share the love?

What OS are you using as host? On my *shudder* Vista I had the exact same problem running Virtualbox 2. ....something....but it doesn't matter. My point is that upgrading to the latest version of Virtualbox (3.0.8 at the typing moment) solved my problem. As a matter of fact, I'm typing this from Koala guest with full compiz effects on a Vista host.

---

### Post by macdav76 on 2009-11-06
I'm kinda late to this party but I just successfully installed the Guest Additions for Karmic Koala. I'm running Virtual Box 3.0.10 on OS X.

First, you need to intall dkms:
sudo apt-get install dkms

Then change to the directory where the Guest Additions are. In my case, after mounting them with Virtualbox, they were in: /media/cdrom/

To install the Guest Additions: 
sudo sh ./VBoxLinuxAdditions-x86.run

This will build the kernel modules you need and then let you know you need to restart to complete the installation.

---

### Post by SpearZ on 2009-12-09
> **macdav76 said:**
> I'm kinda late to this party but I just successfully installed the Guest Additions for Karmic Koala. I'm running Virtual Box 3.0.10 on OS X.

First, you need to intall dkms:
sudo apt-get install dkms

Then change to the directory where the Guest Additions are. In my case, after mounting them with Virtualbox, they were in: /media/cdrom/

To install the Guest Additions: 
sudo sh ./VBoxLinuxAdditions-x86.run

This will build the kernel modules you need and then let you know you need to restart to complete the installation.

Worked like a charm for me, thanks :D

---

### Post by jocampo on 2009-12-29
Bringing this thread to live again...

I think I have the same issue. VirtualBox headless version is 2.2.4. The guest is running Linux 2.6.31-16-generic (Xubuntu Karmic Koala) Not sure but I have the suspicion my VBox 2.2.4 is not compatible with this new Xubuntu version ... still would like to hear suggestion/ideas ...

I want to keep VBox 2.2.4 and still install the additions on guest...

---

