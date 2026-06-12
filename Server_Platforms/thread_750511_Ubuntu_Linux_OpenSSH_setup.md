---
title: "Ubuntu Linux OpenSSH setup"
date: 2008-04-09
forum: Server Platforms
---

### Post by kebes on 2008-04-09
I guess your installation is still set to use the CD instead of the online repository. You should be able to switch it by going System > Administration > Software Sources and on the "Ubuntu Software" tab set it to use the online sources instead of the CD (see some instructions [here]("http://www.psychocats.net/ubuntu/sources")).

You could probably also edit the file "/etc/apt/sources.list" and enable the repositories by un-commenting the appropriate lines (get rid of the "#" at the beginning). After saving the file you'll need to update the repository list with "sudo apt-get update".

---

