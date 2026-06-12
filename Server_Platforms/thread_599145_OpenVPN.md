---
title: "OpenVPN"
date: 2007-11-01
forum: Server Platforms
---

### Post by tj71587 on 2007-11-01
I have openvpn set up on a linux server, but I was just wondering if it is possible to connect to a openvpn without the gui thru windows.  Does anyone have any idea if this is possibel and if it is how to do it.  Thanks.

---

### Post by robert_pectol on 2007-11-02
I bet if you were to read this page, you could answer your own questions:

[http://openvpn.net/INSTALL-win32.html](http://openvpn.net/INSTALL-win32.html)

Good luck!

---

### Post by tj71587 on 2007-11-02
I read that, sorry it was my first time setting it up.  You have to have a special connectiong configured to connect thrut he command line or you can use the gui but either way you need that special connection.  thanks for the reply though.

---

### Post by robert_pectol on 2007-11-02
> **tj71587 said:**
> I read that, sorry it was my first time setting it up.  You have to have a special connectiong configured to connect thrut he command line or you can use the gui but either way you need that special connection.  thanks for the reply though.

If by, "special connectioning configured", you are referring to the requirement of having a configuration file, then yes.  A configuration file is needed.  This is the case, regardless of whether or not you use the gui.  The documentation is very clear on how to create a configuration file.  It's pretty basic stuff...

---

### Post by tj71587 on 2007-11-02
It creates a tap-win32 adapter in the network connections when you install the gui.  You cannot connect to the vpn with the tap-win32 adapter.

---

### Post by robert_pectol on 2007-11-02
> **tj71587 said:**
> It creates a tap-win32 adapter in the network connections when you install the gui.  You cannot connect to the vpn with the tap-win32 adapter.

You must install openvpn on the Windows machine before you can connect.  You can install the gui version or the non-gui version.  Either one will install the underlying mechanisms (tap interface, etc.) that are required for connection to the VPN server.  If you want to run without the gui, simply grab the non-gui install here:

[http://openvpn.net/download.html](http://openvpn.net/download.html)

Select the, "Windows Installer" file.  Once you have installed it, you can create/edit the configuration file and you'll be able to connect to the VPN via the command line, run it as a service in the background, etc.  The gui version is available here:

[http://openvpn.se/files/install_packages/openvpn-2.0.9-gui-1.0.3-install.exe](http://openvpn.se/files/install_packages/openvpn-2.0.9-gui-1.0.3-install.exe)

It will install openvpn along with the graphical interface.  Does that clarify things?

---

### Post by tj71587 on 2007-11-03
Yes, I have it installed and configured already, I was just explaining where I was tripped up, but thanks for taking the time to help.

---

### Post by robert_pectol on 2007-11-03
My apologies!  I thought you were still struggling.  :-)  Take care.

---

