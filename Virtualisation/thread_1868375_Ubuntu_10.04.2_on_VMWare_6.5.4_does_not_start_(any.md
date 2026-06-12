---
title: "Ubuntu 10.04.2 on VMWare 6.5.4 does not start (any more)"
date: 2011-10-24
forum: Virtualisation
---

### Post by Stephan Wöbbeking on 2011-10-24
Hi,

there is already an entry in "[Ubuntu Forums]("http://ubuntuforums.org/index.php")      > [The Ubuntu Forum Community]("http://ubuntuforums.org/forumdisplay.php?f=130")       > [Main Support Categories]("http://ubuntuforums.org/forumdisplay.php?f=327")       > [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331")" under the same title; but somebody recommended to me to post here as this issue may probably be related to a VMWare issue:

I have an Ubuntu 10.04.2 installation of a VMWare instance (6.5.4) which  was working ok for a few weeks already. Recently I switched on a serial  port and I think I tried to update the VMWare tools which both I think  it's not the reason for the problem but I don't really know.
The point is, that my Ubuntu does not start (completely) any more - I  didn't really see a good reason what could have made Ubuntu to resign. I  do see the logo screen with "the running bubbles" (Is that known as the  "splash" screen?) but it will go forever. When I press Esc, the  attached output appears. I can change to the consoles via Alt-F1 to F6,  but whatever I checked locked fine to me.
How can I find out what is missing, what holds Ubuntu back from starting  my desktop (I already tried "sudo init 6" and "startx" just by chance,  didn't help)?

Screenshot:
[http://ubuntuforums.org/attachment.php?attachmentid=203526&d=1317725110](http://ubuntuforums.org/attachment.php?attachmentid=203526&d=1317725110)

In the meanwhile I have also tried "sudo dpkg-reconfigure xserver-xorg" as it was suggested in the other thread.

Thanks for any ideas,
Stephan

---

### Post by dcstar on 2011-10-27
> **Stephan Wöbbeking said:**
> Hi,

there is already an entry in "[Ubuntu Forums]("http://ubuntuforums.org/index.php")      > [The Ubuntu Forum Community]("http://ubuntuforums.org/forumdisplay.php?f=130")       > [Main Support Categories]("http://ubuntuforums.org/forumdisplay.php?f=327")       > [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331")" under the same title; but somebody recommended to me to post here as this issue may probably be related to a VMWare issue:

I have an Ubuntu 10.04.2 installation of a VMWare instance (6.5.4) which  was working ok for a few weeks already. Recently I switched on a serial  port and I think I tried to update the VMWare tools which both I think  it's not the reason for the problem but I don't really know.
The point is, that my Ubuntu does not start (completely) any more - I  didn't really see a good reason what could have made Ubuntu to resign. I  do see the logo screen with "the running bubbles" (Is that known as the  "splash" screen?) but it will go forever. When I press Esc, the  attached output appears. I can change to the consoles via Alt-F1 to F6,  but whatever I checked locked fine to me.
How can I find out what is missing, what holds Ubuntu back from starting  my desktop (I already tried "sudo init 6" and "startx" just by chance,  didn't help)?

Screenshot:
[http://ubuntuforums.org/attachment.php?attachmentid=203526&d=1317725110](http://ubuntuforums.org/attachment.php?attachmentid=203526&d=1317725110)

In the meanwhile I have also tried "sudo dpkg-reconfigure xserver-xorg" as it was suggested in the other thread.

Thanks for any ideas,
Stephan

Log in to a console session and run the installation of the VMWare tools package.

---

### Post by zpatz on 2011-12-06
[http://hitachi-id.com/largedocs/patches/vmware655onUbuntuNatty.zip](http://hitachi-id.com/largedocs/patches/vmware655onUbuntuNatty.zip)

This is a patch for getting vmware655 on Natty and possibly more recent versions if anyone still cares.

---

