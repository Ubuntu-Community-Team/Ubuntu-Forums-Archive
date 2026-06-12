---
title: "LTSP forward usb port from client to server"
date: 2011-05-28
forum: Server Platforms
---

### Post by albatros78 on 2011-05-28
Hello everyone,
 I'm new to the forum
 I wanted to be able to redirigre the USB port of a PC client LTSP
 on the server, but with the exception of USB mass storage, the rest of the hardware is not recognized by the server.

 Someone can help me?


 I tried using the application usbip,

it's all right if I type
   usbip -l <server_ip>
that returns the list of shared devices in the PC server

but when I try to send the command
  usbip -a <ip_server> <bus_id>

usb remote connection is not established

and the PC Client reports these errors:

with uspip -p the answer is:
Port 00: <Port Initializing>
Port 01: <Port Available>
Port 02: <Port Available>
Port 03: <Port Available>
Port 04: <Port Available>
Port 05: <Port Available>
Port 06: <Port Available>
Port 07: <Port Available>


with lsusb command the answer is:
usb 3-1: parent hub has no TT
usb 3-1: parent hub has no TT
usb 3-1: parent hub has no TT
usb 3-1: parent hub has no TT

What's wrong?
Someone can help me?

Thanks

---

### Post by albatros78 on 2011-05-29
CuuuCuuuuu....:p

---

### Post by nordemoniac on 2012-02-11
I'm looking info doing something similar. Can I forward a USB-port from the thin client to the LTSP-server. 
I was hoping to use Raspberry Pi's for this project. 
I'm hoping to be able to forward USB-cameras and sensors. 

Is this possible? Cat5/6 adapters which needs resetting all the time is killing me! Would rather stream it through the client.

---

### Post by nordemoniac on 2012-02-16
Sooo...not possible?

---

### Post by nordemoniac on 2012-02-21
Could it be a solution to run the USBIP server as a local app on the thin client, so that you can access USB-devices through the USBIP-client on the LTSP-server...

No...?

---

