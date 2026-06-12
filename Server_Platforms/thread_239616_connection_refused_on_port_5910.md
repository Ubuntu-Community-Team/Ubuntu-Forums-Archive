---
title: "connection refused on port 5910"
date: 2006-08-19
forum: Server Platforms
---

### Post by hela on 2006-08-19
I need port 5910 open for a terminal server with xrdp / ubuntu 6.06. Starting a remote session xrdp / sesman reports "connecting to 127.0.0.1 5910", "error - problem connecting". Testing "telnet 127.0.0.1 5910" on the terminal server gives the error message "connection refused". Portmap is running and  iptables shows acceptions on all ports and ip's.

---

### Post by hela on 2006-08-19
After installing kubuntu-desktop I was able to connect using KDE. Gnome sessions are not possible.

---

### Post by mrnumnuts on 2006-10-05
Gnome is supported, I found this today. 

Edit /usr/local/xrdp/startwm.sh

the following is commented out in the file:
# gnome
#if [ "'which gnome-session'" != "" ]; then
#  gnome-session
#  exit 0
#fi

I left this alone and added this to the begining of the file:

if [ "'which gnome-session'" != "" ]; then
  dbus-launch gnome-session
  exit 0
fi

Thanks,
Robert

---

