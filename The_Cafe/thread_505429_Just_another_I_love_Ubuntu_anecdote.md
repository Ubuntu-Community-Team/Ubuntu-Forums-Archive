---
title: "Just another I love Ubuntu anecdote"
date: 2007-07-20
forum: The Cafe
---

### Post by tcpip4lyfe on 2007-07-20
So I found an old ATI wonder remote laying in my basement. My computer is my TV and for the last year or so I've needed a remote so I wouldn't have to get up and press the up arrow to change channels.  I plugged in the USB receiver and tried the remote and it didn't do anything, not surprisingly because I have an Nvidia graphic card and some generic TV tuner. I figured it was going to be a 2 or 3 day ordeal learning how to map keys to the remote and getting the right driver for it and what not.  Not really wanting to get into all that I just set the remote down and forgot about it.

This morning I rebooting because something went haywire and when I logged in my cursor was moving by itself.  WTF how do I fix this? I sat back in my chair and realized that coffee mug was laying on the ATI remote.  I moved the coffee mug and the cursor stopped moving.  "No way did the ATI remote start working after restarting."  I fired up TVtime and channel, fullscreen, and volume work fine.  

I went to console.  

```

josh@josh-desktop:~$ lsmod | grep remote
ati_remote             12296  0 
usbcore               134280  7 ati_remote,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd

```

Serious attention to detail like this is why I love using linux.

---

### Post by DoctorMO on 2007-07-20
it's a usb device produced by ati as a serial hid device? (human input device) glad you got it working :-)

---

