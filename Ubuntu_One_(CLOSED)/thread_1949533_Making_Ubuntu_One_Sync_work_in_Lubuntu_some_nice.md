---
title: "Making Ubuntu One Sync work in Lubuntu some nice"
date: 2012-03-30
forum: Ubuntu One (CLOSED)
---

### Post by M_Mynaardt on 2012-03-30
I wanted to try out **Ubuntu One** on my laptop.  However, I use Lubuntu on my laptop and I didn't want to mess things up with DE clashes.  It seems that the default for *Ubuntu One Sync* is using the Nautilus file manager.  I found a solution to make *Ubuntu One Sync* work in Xubuntu.  I installed *Ubuntu One Sync* on my Lubuntu Laptop with this Xubuntu solution and it seems to work just fine.

This solution is *mostly* the same as the one I just posted for making *Ubuntu One Sync* work nicely in Xubuntu.

I cannot claim to be a bright spark who solved this all on my lonesome.  But I am just passing this along, should any other Lubuntu users out there want to have a go at *Ubuntu One* on their Lubuntu computers.

The only difference I saw between following these instructions on my Xubuntu PC and my Lubuntu laptop was that when I first signed in to *Ubuntu One* with Lubuntu, I was prompted for a Keyring password.  I dont know if this is because I was using Lubuntu, or because I was using a laptop connected to the Internet by wireless.  If someone could tell me why I did not have a Keyring prompt on my Xubuntu Desktop and did on my Lubuntu Laptop when I first signed in to *Ubuntu One*, I'd appreciate that.  For future reference.

Source: 
[http://askubuntu.com/questions/82978/how-can-i-run-ubuntu-one-on-xubuntu]("http://askubuntu.com/questions/82978/how-can-i-run-ubuntu-one-on-xubuntu")


**INSTALLING UBUNTU ONE SYNC IN LUBUNTU USING SYNAPTIC:**

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

**STEP 2 - Ensure These Packages Are NOT Selected:**
ubuntuone-client-gnome
ubuntuone-client-gnome-dbg

**STEP 3 - Starting Ubuntu One**
You will now find Ubuntu One in the LXDE Menu, like so:
LXDE -> Preferences -> Ubuntu One
Sign in with your account, or create one

**STEP 4 - Opening the Ubuntu One Folder**
You can now open the Ubuntu One folder properly with PCManFM


**ENJOY!**
\\:D/

---

### Post by marinara on 2012-03-31
If you like I can create a blank wiki page so you can put this info on the lubuntu wiki.  thanks!

---

### Post by oldos2er on 2012-03-31
Closed, duplicate.

---

