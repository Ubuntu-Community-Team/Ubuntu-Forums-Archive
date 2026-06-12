---
title: "Running XDMCP and Connecting?"
date: 2006-11-24
forum: Server Platforms
---

### Post by romUdog on 2006-11-24
Im looking to use XDMCP as a "VNC" because its already there maybe i need something else? I really just would like to know how to setup one computer as a host to allow connections. I want something i can login to with a Username+Password and have multiple accounts allowed on it....PS Kubuntu works great on a USB HDD :) Thanks in Advance :)

---

### Post by houstonbofh on 2006-11-25
I am not sure what the question here is.  It works on Ubuntu.  You will need a window manager to use it...  'sudo apt-get install ubuntu-desktop' on a server install will do this for you.

---

### Post by chrismyers on 2007-02-18
Found a fix:

Host machine:

1. Go to System » Administration » Login Window.

    Select tab Remote » Style: Same as Local

    Close the window

2. Open a terminal & type: sudo gedit /etc/X11/gdm/gdm.conf

    Now search for RemoteGreeter=/usr/lib/gdm/gdmlogin

    & uncomment this line.

3. Search for the [xdmcp] section & scroll a few lines down until you find Enable=False

    Change it to Enable=True

4. Save & reboot. Your host is sorted.

Client Machine

Enable the XDMCP option in the Terminal Server Client:

sudo apt-get install xnest

I hope this helps.

---

