---
title: "HOWTO Logitech Rumblepad 2 in Wine"
date: 2009-03-15
forum: Wine
---

### Post by jyaan on 2009-03-15
I had a bit of a pain getting my Logitech Rumblepad 2 to work in Wine, so I thought I would share how I got it working.

[http://wiki.winehq.org/UsefulRegistryKeys]("http://wiki.winehq.org/UsefulRegistryKeys")
This page has the most useful information I have found so far. Look under HKEY_CURRENT_USER/Software/Wine/DirectInput. You will need to create the DirectInput key if it does not exist. The settings they mentioned in that section were for Logitech Dual Action, and these did not work for me at all. I was able to use the left analog to move left and right, but not up and down. This is the string value I entered to make my gamepad work:
```

(string value name)                   (string value)
Logitech Logitech RumblePad 2 USB     X,Y,Rx,Ry,POV1
```

I bought the Prince of Persia trilogy and have been playing it with the gamepad. All axes and buttons are working, which is quite nice.

---

### Post by BOZO1 on 2009-10-14
hi jyaan, 

i've been trying to play Prince of Persia in Ubuntu karmic through wine but the game crashes.. though install goes through ok.

Could you post the way that you have it installed?!

Many thanks in Advance

---

### Post by myromance123 on 2009-10-30
@jyaan,
 I want to thank you very much for sharing this information. I am now able to use my Logitech Rumblepad 2 in games!

There is just one problem for me so far, that is my right joystick (my left one works great, both y-axis and x-axis are recognized) only the x-axis is recognized, not the y-axis.

 How can I change the string value so that my y-axis (on the right joystick) can be recognized?
Do you happen to know?
I'm testing out some ways now but with your expertise I think it can be solved.

Thanks in advance!

EDIT: I have figured out that Rz makes my x-axis work but nothing seems to be working still for my y-axis. ALSO, Rx and Ry have no effect both are unusable to make the right joystick movement recognized.

Ps: the game I am playing is Sudeki, an Xbox game ported to the PC.

---

