---
title: "Wireless option gone on Serval"
date: 2007-08-12
forum: System76 Support
---

### Post by mpow on 2007-08-12
I got my new Serval about half a week ago and the wireless worked right out of the box. Now that I have had it longer and tried to fix the wireless not working after suspend/hibernate, I managed to lose the option of wireless from the network manager. (see attached image)

What can I do to allow the manager to recognize my wireless card?  I am using a wired connection now but I am going on a road trip tommorow and wireless is much preferred.

---

### Post by thomasaaron on 2007-08-13
I hate to ask this, but for the sake of being thorough...

Did you push the wireless button above your keyboard?

If so, try this:

To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.
It should now boot faster and connect to networks more easily.

NOTE:
Unless you are dealing with static IP addresses (which is pretty rare for the
general end-user) you should NOT establish a network connection by going to 
System > Administration > Network.

Instead, you should connect to the Internet using the Network Manager icon
in the upper right corner of your screen (the one that looks like a little 
computer monitor).


EDIT: ACTUALLY THE WIRELESS SWITCH IS NOT ABOVE THE KEYBOARD. IT IS ON THE FRONT EDGE OF THE COMPUTER JUST BELOW WHERE YOUR LEFT HAND RESTS.

---

### Post by mpow on 2007-08-13
Yes, I at some point did turn the wireless switch off and on. this was after hibernate wouldn't restore the wireless connection. I did what you said to the interfaces file, rebooted and the wireless option is still not there.  the network manager screen still shows up like it did in my first post. 
Are there any commands i can run to see if the wireless card is responding or if the manager is not recognizing it? 

Thanks in advance.

---

### Post by thomasaaron on 2007-08-13
Just to cover the bases. Let's take suspend/hibernate out of the picture.
Turn the computer off and back on.

I did make a mistake in telling you that the wireless switch was above the keyboard. It is on the leading edge of the laptop, just below where our left palm rests. Make sure it is on.

If it is on and you still see no wireless access points, we will need to turn the computer over and remove the panel covering the wireless card to make sure one of the two wires that connect to it did not come off during shipping.

If you need help with this, give me a call.

---

### Post by mpow on 2007-08-14
I don't exatly know if I 'm ready to start taking the laptop apart. The wireless switch (on the front, yep) works to my knowledge, when i turn it on the light turns on. i have scoured these forums and found similar problems with different wireless cards, so I have a feeling that it is not a hardware problem.
I will keep looking for some direction and I'll post back if i find anything.

Thanks for the help, nice to see fast responses.

---

### Post by thomasaaron on 2007-08-15
It may be easier to contact me via email (support[at]system76[dot]com, and I can help you that way.

The Serval definitely has excellent connectivity. It's probably a configuration issue of some kind.

---

