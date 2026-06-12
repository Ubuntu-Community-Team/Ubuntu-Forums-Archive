---
title: "Install Hp Officejet 8600 in Ubuntu Gnome 13.04"
date: 2013-03-17
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2013-03-17
My Hp Officejet works fine in ubuntu 13.04 and fedora 18, but not in Ubuntu Gnome 13.04.  When I click to install printer form list, the window just closes and sometimes I get a message indicating that gnome-control-center has crashed.  Anybody esle have this problem? and if so any workarounds.

Henry

---

### Post by kc1di on 2013-03-17
Hi Henry,
Well 13.04 is just beta and not everything will work yet. so it may be that the hplip drivers are not complied for the newer kernel yet. 
you may have to wait awhile. ;)

---

### Post by Hewjr100 on 2013-03-27
Found a workaround for anybody with this problem.  All I did from terminal was: sudo apt-get install hplip-gui then ran: sudo hp-setup.  Hp 8600 installed perfectly.

Henry

---

### Post by kc1di on 2013-03-28
glad you got it going :)

---

### Post by screaminj3sus on 2013-03-28
I have that same printer, use system-config-printer instead of gnome's built in printer tool (vanilla ubuntu uses system-config-printer by default instead of gnome control center's, which is why it works for you in ubuntu and UGR's doesn't). I've heard that the gnome-control center's printer management has supposedly been fixed/improved in gnome 3.6, but IMO its still crappy compared to system-config-printer.

---

