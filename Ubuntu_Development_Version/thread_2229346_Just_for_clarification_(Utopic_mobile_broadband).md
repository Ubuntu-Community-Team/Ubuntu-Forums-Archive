---
title: "Just for clarification (Utopic mobile broadband)"
date: 2014-06-12
forum: Ubuntu Development Version
---

### Post by jimmy-frydkaer on 2014-06-12
Greetings people

I've just installed Utopic (Ubuntu 14.10) on my MSI MegaBOOK by way of editing my /etc/apt/sources.list.

The download and installation of files went flawlessly and after reboot the system came up beautifully. Good ol' Ubuntu pleasure.

I then proceeded to go on-line via my Huawei mobile broadband USB-modem. No pain here - But after I clicked on "Connect" a dialog-box came up. Same as always. And then again NOT - This dialog-box prompted me for the PIN for the modem AND a password?? WHAT?

Out of nowhere I hit the Cancel-button. Tried again and the same result came up: Password?? WHAT password??

A bit nervous that I'd damage my modem I decided to enter my root-pass. and away we went - ON-LINE :o

That happened a couple of days ago and I have been on and off the Internet a number of times, but not ONCE have I been prompted for either my PIN or password? Double that ??

What causes this apparently one-time-password-demand before I was able to log on to the Internet?

I have tried to switch the modem between the USB-ports in my laptop, but not once have I been able to get the system to ask for the password. How come??

---

### Post by grahammechanical on 2014-06-12
You will find the PIN typed on a label stuck on the bottom of the router. It is used in connection with WiFi Protected Setup (WPS). Does your router have a button that can be pushed when using WPS? Did you push it? why it should appear in your case is any bodies guess. 

[http://kb.netgear.com/app/answers/detail/a_id/96/~/what-is-wi-fi-protected-setup-(wps)-or-push-n-connect%3F](http://kb.netgear.com/app/answers/detail/a_id/96/~/what-is-wi-fi-protected-setup-(wps)-or-push-n-connect%3F)

> 
[LIST]
[*]PIN Method, in which a [personal identification number]("http://en.wikipedia.org/wiki/Personal_identification_number") (PIN) has to be read from either a sticker or the display on the new [wireless device]("http://en.wikipedia.org/wiki/Station_(networking)"). This PIN must then be entered at the "representant" of the network, usually the [access point]("http://en.wikipedia.org/wiki/Wireless_access_point") of the network. Alternately, a PIN on the Access Point may be entered into the new device. The PIN Method is the mandatory baseline mode; every Wi-Fi Protected Setup certified product must support it.
[*]Push-Button-Method, in which the user simply has to push a button, either an actual or virtual one, on both the access point and the new wireless client device. Support of this mode is mandatory for access points and optional for connecting devices.
[*]Near-Field-Communication Method, in which the user simply has to bring the new client close to the access point to allow a [near field communication]("http://en.wikipedia.org/wiki/Near_field_communication") between the devices. NFC Forum compliant [RFID]("http://en.wikipedia.org/wiki/RFID") tags can also be used. Support of this mode is optional.
[*]USB Method, in which the user uses a [USB flash drive]("http://en.wikipedia.org/wiki/USB_flash_drive") to transfer data between the new client device and the access point of the network. Support of this mode is optional, but deprecated.
[/LIST]


[http://en.wikipedia.org/wiki/Wi-Fi_Protected_Setup](http://en.wikipedia.org/wiki/Wi-Fi_Protected_Setup)


Regards.

---

### Post by ventrical on 2014-06-12
I always have to enter my WEP on all my (new) wireless installs.

---

### Post by cariboo on 2014-06-12
I know network-manager does store your wireless password in /etc/NetworkManager/system-connections/<some-wireless-profile>, your usb modem probably does the same thing.

---

### Post by jimmy-frydkaer on 2014-06-13
On Ubuntu GNOME 14.04 LTS I just plug-in my USB-modem (dongle) and the system ask for my pin-code. That's normal, even if you remove the dongle and insert it in another USB-port. Same thing happens if I insert the dongle in my desktop Pc's USB-port. It only ask for the pin-code and goes on-line. 

In Ubuntu GNOME Utopic Unicorn a.k.a. U-G 14.10, the system ask for both the pin-code AND a password first time I want to connect the dongle to go on-line. The OS does nothing before I click "Connect" in network manager. On insertion of the dongle the system finds, and mounts, the dongle as a pen drive, then, when the modem is "called" to go on-line it ask for both pin and password. This happens only the first time I connect to the Internet via the dongle/modem, after entering the admin-code and pin code the modem goes online, never to ask for either pin nor password again regardless what USB port I insert the thing into. THAT's weird.

One should think that the two codes should be entered each time the thing goes on-line, right?

Over at the Danish forum one mentioned that it could have something to do with cgroups which I investigated but can't find anything about through google search. Any number of searches on mobile broadband modem and cgroups turns up no clear answer.

Logically it would be necessary to type those codes like it must be done in 14.04 LTS. It makes no sense that you only type in the codes on "first boot" (after install). And never again thereafter.

The pin code is, of cause, to ID oneself to the ISP, but why the admin-code? And WHY only once?

Don't get me wrong on this. The feature should have been thought of way earlier. This kind of "parring" the hardware is great and an improvement. But some how, since the admin-code only is to be entered once, the feature seem a bit half baked. If it's for security it need logic, since the feature does not show up in connection with the on board Wi-Fi card.

---

