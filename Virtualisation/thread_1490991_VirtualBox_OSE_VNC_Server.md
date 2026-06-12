---
title: "VirtualBox OSE VNC Server"
date: 2010-05-23
forum: Virtualisation
---

### Post by madverb on 2010-05-23
Does anyone know how to setup guests with a VNC server? From what I can find, the OSE version supports VNC server to access headless setups.
I am looking at this because I need to enter in the passphrase for an encrypted partition on boot.
I wanted to see if I can get this working before installing the full version of virtualbox to access the VRDP server.
Cheers

---

### Post by madverb on 2010-06-04
Yay! There was an update for virtualbox-ose and it seems to have resolved my problem.
It now has the VNC server option by default.
> Usage:
   -s, -startvm, --startvm <name|uuid>   Start given VM (required argument)
   -n, --vnc                             Enable the built in VNC server
   -m, --vncport <port>                  TCP port number to use for the VNC server
   -o, --vncpass <pw>                    Set the VNC server password
   -c, -capture, --capture               Record the VM screen output to a file
   -w, --width                           Frame width when recording
   -h, --height                          Frame height when recording
   -r, --bitrate                         Recording bit rate when recording
   -f, --filename                        File name when recording.  The codec
                                         used will be chosen based on the
                                         file extension

---

### Post by chrisinspace on 2010-06-04
Sounds like you got it worked out, but you might also want to look at FreeNX.  I like it much better than VNC.

---

### Post by madverb on 2010-06-04
Virtualbox doesn't have support for FreeNX. Yes, I could use it to access the guest once it's loaded, but I wouldn't be able to enter in the password prior to the system loading.

---

### Post by TheFu on 2010-06-06
According to your other posts, I guess a newer version of VBox supports VNC at the host level. My OSE 3.1.6 install does not.  So the solution for me to have VNC support in a client OS install is to run a VNC server inside the client and connect to it. The HostOS doesn't know anything about the VNC running in the quest.

Anyway, I figured someone else might need this information.  If the client OS supports RDP (Windows Professional or greater), then simply enable that service like normal for RDP support in the client.

---

