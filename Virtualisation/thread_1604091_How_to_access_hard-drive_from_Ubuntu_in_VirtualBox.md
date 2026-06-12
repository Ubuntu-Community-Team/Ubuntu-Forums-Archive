---
title: "How to access hard-drive from Ubuntu in VirtualBox"
date: 2010-10-23
forum: Virtualisation
---

### Post by aisajib on 2010-10-23
As I've decided not to upgrade from LTS to an STS release, I've installed Ubuntu Maverick Meerkat on Oracle VirtualBox. It's running smooth and cool but I can't get files from my hard drive to the OS installed in VirtualBox.

I'm a new user of VirtualBox so I'm having a hard time figuring out how to access my hard drive folders for songs, movies and other documents from my Ubuntu Maverick Meerkat installed using VirtualBox. Help will be highly appreciated.

---

### Post by fjgaude on 2010-10-23
I don't use VBox anymore, but I remember you have to first have the tools installed, then you find the Share menu, and then simply click on the partitions or drives you wish VBox guest to have access.

---

### Post by SeijiSensei on 2010-10-23
Either create "[shared folders]("http://forums.virtualbox.org/viewtopic.php?t=15868")" or write the content to a network drive both the host and guest can access.  To install the required "Guest Additions" for shared folders, you need to be using the proprietary version of VirtualBox at [http://www.virtualbox.org/](http://www.virtualbox.org/).

---

