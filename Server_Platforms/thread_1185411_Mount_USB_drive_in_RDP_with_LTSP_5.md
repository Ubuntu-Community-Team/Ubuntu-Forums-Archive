---
title: "Mount USB drive in RDP with LTSP 5"
date: 2009-06-12
forum: Server Platforms
---

### Post by pgemme on 2009-06-12
I am running ubuntu-ltsp 2.6.27-7.  My thin client is a Dell Optiplex 160.  The LTSP server uses rdesktop to point to a W2k3 terminal server.  

From a ubuntu desktop I am able to run the command:
[B]/usr/bin/rdesktop -5 -u user -a 16 -K -r disk:usb=/media/<username>/<usbdrive> w2k3.terminal.server.com

[/B]This works and mounts the USB drive from the LTSP thin client to the remote desktop.

I'm not sure how to do this in the _lts.conf_ file.  My current lts.conf file contains:

    # rdesktop options
    RDP_SERVER      = terminals.server.com
    RDP_OPTIONS     = "-a 16 -x l -r sound:local" 
    SCREEN_02       = rdesktop

How do I add the **-r disk:usb=/media/...   **to this file to get the USB drives to work.  I don't already know ther usernames or the names of the USB devices that will be plugged in.  Are there wildcards that I'm missing?  

I feel that I'm very close, any help would be appreciated.

---

### Post by gekkos on 2012-06-29
Its a very old thread, but did someone find a solution?

Many thanks

---

### Post by pgemme on 2012-10-19
Not sure if you're still looking for this, but using the generic Drives=/media/root does now work for me.

(i.e. **SCREEN_05 = "rdesktop -a 16 -x l -r sound:local -r disk:Drives=/media/root terminal.server.com"**)

---

### Post by gekkos on 2012-10-19
TXS

For me it works now with

LTSP_FATCLIENT  = False
SCREEN_07       = "rdesktop -r disk:USB=/media/root -r sound:local -f -a 16"


I have to add 'LTSP_FATCLIENT = False' because default I use the server with 'FAT_CLIENTS = true'

---

