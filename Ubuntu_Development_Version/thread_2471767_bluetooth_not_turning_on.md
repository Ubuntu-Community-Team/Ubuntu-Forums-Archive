---
title: "bluetooth not turning on"
date: 2022-02-08
forum: Ubuntu Development Version
---

### Post by Claus7 on 2022-02-08
Hello,

having upgraded to 22.04 development version I noticed that bluetooth was refusing to turn on. 

The normal procedure in order to enable it is from Settings->Bluetooth where I can see the following: 
> Airplane Mode is on
Bluetooth is disabled when airplane mode is on.

and I have the ability to click on:

> Turn Off Airplane Mode

By clicking the above option, Bluetooth icon takes the place of an airplane accompanied with the following text: 
> Bluetooth Turned Off
Turn on to connect devices and receive file transfer.

And on top of the bluetooth settings window there is a switcher that if turned on, should turn bluetooth on. Alas, this is not working as is.

Solution: in order to enable bluetooth on my box I do the following:
1) Clicking the "Turn off airplane mode" button.
2) Clicking the switcher in order to turn on (up to now bluetooth is not working)
3) Clicking again the switcher, yet now in order to turn it off.
4) Clicking again the "Turn off airplane mode" button

and bluetooth is turning on!

I have not understood why I have airplane mode on a desktop ubu box and why repeating this process actually turns on bluetooth.
This seems to be an issue even from 20.04.

In order for this to work I had previously (do not know if had affected the process) issued the command:
sudo systemctl enable bluetooth.service

Just to mention that there were other commands that I tried to no avail like:
rfkill (un)block bluetooth
systemctl enable bluetooth.service

Also I should mention that removing the bluetooth dongle and putting it back, bluetooth was turning on.

Regards!

---

