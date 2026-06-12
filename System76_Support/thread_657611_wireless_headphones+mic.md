---
title: "wireless headphones+mic"
date: 2008-01-03
forum: System76 Support
---

### Post by system77 on 2008-01-03
hi,

I often speak over skype and wanted to find a wireless headphone+mic, so I can plug them into my sound-out and mic outputs and be able to freely talk  meters away from the laptop and also don't bother with cables hanging around..
I searched alot on google etc... couldn't find such thing !!? 
There is some wireless-headphones-only, but most of the time they are very expensive.

So my best bet seems to be to use some usb-to-bluetooth converter and then use some of these ear-plugs+mic many have for their gsm/cdma phones.

But then the question is which usb-bluetooth cnverter should I buy, so that I can make it easy to work on my Pangolin.

I don't want to buy some of those skype-phones, 'cause i may switch to different IM 
(i'm not big fan of skype, especially the condition that you can not pay for 2 or more account with your paypal account !! no support , etc.. ) 
 and if I have audio-based solution it will work there too and as added bonus I can listen music too or use it with other computer.... and so on..

Does someone of you tried some usb-bluetooth converters like this... ?
Even if I have the thing confgured, how do I use it like sound output device ?

If you have any resource, docs to which you can direct that will be good too..

thanx alot

---

### Post by imhavoc on 2008-01-03
I have connect my wife's Motorola H500 Bluetooth headset as well as my BlueAnt V12 blueooth headsets to computer. My Daru2 has built-in bluetooth, but I have successfully connected to the desktop with a Kensington USB bluetooth adapter without problems.

As of Ubuntu 7.10, it's pretty straight forward to get the device paired. once paired, you'll need to run:

btsco [device address]

(device address will look like: 00:11:22:33:44:55)

I got a lot of info from this page:
[http://www.linux.ie/articles/bluetoothheadset.php](http://www.linux.ie/articles/bluetoothheadset.php)

but many of the steps have been automated by current distros.

Good luck!

---

