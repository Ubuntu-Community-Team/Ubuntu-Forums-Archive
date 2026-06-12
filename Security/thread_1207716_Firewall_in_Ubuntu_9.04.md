---
title: "Firewall in Ubuntu 9.04"
date: 2009-07-08
forum: Security
---

### Post by Elder_Usr on 2009-07-08
Hello All,
First off. I'm relatively new and don't know if i'm posting this in the right area, but here goes.

I currently have a LAMP setup at home, running drupal using (k)ubuntu 9.04 desktop edition, and am planning on setting up a Firewall between my exterior connection and my internal. I was wondering what you would suggest, and if there is any guides for it?

What i'm looking for is something along the lines of this:

Internet
   |
   |
   |
ISP Router
   |
   |
Firewall/Linux Box
   |
   |
   |
  HUB
   |
To the rest of my network.

I really would like to use a Ubuntu Distro or something of the like. I am a little linux savy, but would prefer a gui any day then going in and messing with IPtables. 

Thanks in advance.

---

### Post by cariboo on 2009-07-08
I would suggest either Smoothwall or Ipcop. They both use a web based configuration interface.

---

### Post by Elder_Usr on 2009-07-08
Yeah. That probably would be the best, cause I would like to be able to set it up GUIish. Do you know of any good documentation on how to setup IPCop. I heard good things about that one.

Thanks,.

---

### Post by sasho_zl on 2009-07-09
> **Elder_Usr said:**
> Yeah. That probably would be the best, cause I would like to be able to set it up GUIish. Do you know of any good documentation on how to setup IPCop. I heard good things about that one.

Thanks,.

I would recommend the book "Configuring IPCop Firewalls - Closing Borders With Open Source".
"This book is an easy introduction to this popular application. After introducing and explaining the foundations of firewalling and networking and why they're important, the book moves on to cover using IPCop, from installing it, through configuring it, to more advanced features, such as configuring IPCop to work as an IDS, VPN and using it for bandwidth management. While providing necessary theoretical background, the book takes a practical approach, presenting sample configurations for home users, small businesses, and large businesses. The book contains plenty of illustrative examples."

---

