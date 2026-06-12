---
title: "Making Ubuntu One Sync work in Xubuntu some nice"
date: 2012-03-30
forum: Ubuntu One (CLOSED)
---

### Post by M_Mynaardt on 2012-03-30
Making Ubuntu One Sync work in Xubuntu some nice:

I wanted to try out **Ubuntu One** on my desktop.  However, I use Xubuntu on my desktop computer and I didn't want to mess things up with DE clashes.  It seems that the default for *Ubuntu One Sync* is using the Nautilus file manager.  I found a solution to make *Ubuntu One Sync* work in Xubuntu.  I installed *Ubuntu One Sync* on my Xubuntu PC and it seems to work just fine.

I cannot claim to be a bright spark who solved this all on my lonesome.  But I am just passing this along, should any other Xubuntu users out there want to have a go at *Ubuntu One* on their Xubuntu computers.

Source:
[http://askubuntu.com/questions/82978/how-can-i-run-ubuntu-one-on-xubuntu]("http://askubuntu.com/questions/82978/how-can-i-run-ubuntu-one-on-xubuntu")


**Installing Ubuntu One Sync In Xubuntu Using Synaptic:**

**STEP 1 - Select These Packages:**
desktopcouch-ubuntuone
python-ubuntuone
python-ubuntuone-client
python-ubuntuone-control-panel
python-ubuntuone-storageprotocol
ubuntuone-client
ubuntuone-client-dbg
ubuntuone-control-panel
ubuntuone-control-panel-gtk
ubuntuone-couch

**STEP 2 - Ensure These Packages Are _NOT_ Selected:**
ubuntuone-client-gnome
ubuntuone-client-gnome-dbg

**STEP 3 - Starting Ubuntu One**
You will now find Ubuntu One in the Xfce Menu, like so:
Xfce -> Settings -> Ubuntu One
Sign in with your account, or create one

**STEP 4 - Opening the Ubuntu One Folder**
You can now open the Ubuntu One folder properly with Thunar


**ENJOY!**
\\:D/

---

### Post by duanedesign on 2012-04-06
You will want to become familiar with the command line tool u1sdtool. You will use this tool to access all the features in a non-Gnome environment. Here is a nice page discussing the u1sdtool. The u1sdtool is a commandline program that talks to ubuntuone-syncdaemon over dbus, and allows you to do nearly everything you can do via the Nautilus plugin. The only thing not implemented in u1sdtool is sharing a folder with somebody via email. I'd recommend you use the sharing feature in the web interface.

---

### Post by M_Mynaardt on 2012-04-06
> **duanedesign said:**
> You will want to become familiar with the command line tool u1sdtool. You will use this tool to access all the features in a non-Gnome environment. Here is a nice page discussing the u1sdtool. The u1sdtool is a commandline program that talks to ubuntuone-syncdaemon over dbus, and allows you to do nearly everything you can do via the Nautilus plugin. The only thing not implemented in u1sdtool is sharing a folder with somebody via email. I'd recommend you use the sharing feature in the web interface.

Right on!  Thanks for that, I'll check it out!

---

