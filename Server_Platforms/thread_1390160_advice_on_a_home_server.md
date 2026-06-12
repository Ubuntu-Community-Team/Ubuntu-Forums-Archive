---
title: "advice on a home server"
date: 2010-01-25
forum: Server Platforms
---

### Post by aquavitae on 2010-01-25
I'm setting up a small server at home with ubuntu server 9.10, serving about 3 or 4 computers (some windows, some linux). The idea is to provide internet, file storage, printers, and a music database for amarok. My questions are:
1. My modem works through the usbserial module which I've had to specify manualy in modprobe.d and brings up /dev/ttyUSB0. I can then connect with wvdial. Is there a way to get it to either bring up the interface automatically or to run wvdial when I plug in. The device works through CDMA (I think).
2. My intention is to set up a wireless network with WPA security. Is this appropriate for this sort of system? 
3. I'm thinking of using squid as a proxy server, but I think it might be a bit excessive for such a small system. Any comments?
 4. What would be te best way of managing users and access? Does each user nees a login on the server? Does the WPA give good enough security or should I use something else too?

Any advice or suggestions would be very useful!

---

### Post by munky99999 on 2010-01-25
> 1. My modem works through the usbserial module which I've had to specify manualy in modprobe.d and brings up /dev/ttyUSB0. I can then connect with wvdial. Is there a way to get it to either bring up the interface automatically or to run wvdial when I plug in. The device works through CDMA (I think).
I personally not exactly sure what you are trying to achieve here. 

Sounds like you want to enter your commands into /etc/network/interfaces for it to automatically be brought up.

> 2. My intention is to set up a wireless network with WPA security. Is this appropriate for this sort of system? 
If you can. You want to use WPA2. Which uses AES encryption. The standard WPA uses tkip which is flawed and potentially hackable like wep. WPA itself is dictionary attackable. So use a strong password.

> 3. I'm thinking of using squid as a proxy server, but I think it might be a bit excessive for such a small system. Any comments?
No. I think squid would be just fine.

> 4. What would be te best way of managing users and access? Does each user nees a login on the server? 
You could setup the network share and everything via samba. Which then can allow you to have no user/password to access it. Obviously that's not that secure. You can make 1 universal login/password for accessing the share. 

Really depends on your situation.

---

### Post by aquavitae on 2010-01-28
Thanks for the reply.  I want the connection to come up automatically whenever the modem is available (i.e. plugged it). I know how to do this when I have an interface such as eth0, but I'm not sure how to do it when I only have /dev/ttyUSB0.  I tried creating a udev entry, but it doesn't seem to work:
```

DRIVERS=="usbserial_generic", ATTRS{idVendor}=="1d09", ATTRS{idProduct}=="4000", RUN="usr/bin/wvdial &"

```

---

