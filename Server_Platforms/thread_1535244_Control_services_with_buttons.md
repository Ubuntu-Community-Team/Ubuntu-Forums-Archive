---
title: "Control services with buttons"
date: 2010-07-20
forum: Server Platforms
---

### Post by ezacon on 2010-07-20
I am searching a way to control services with a button.
I have a small headless home server and i want to control services like hostapd or mldonkey with external buttons to turn then on and off.
The hardware buttons can be serial or usb.
I have not found anything in the net.
Does someone know where to start?

---

### Post by ezacon on 2011-11-19
I have found the perfect hardware for this:
[http://www.pjrc.com/teensy/index.html]("http://www.pjrc.com/teensy/index.html")
This is a small micro controller board, compatible with the arduino ([http://www.arduino.cc/]("http://www.arduino.cc/")) IDE. It includes a complete USB HID stack so your program running inside teensy can send keystrokes in response to the state change of a digital input.
So i can program that on a button press, the teensy program simulate any string or keypress as if it was typed on a keyboard.
It is easy now to run a script when i push the button if there is a user logged in, but How can i run the script when the user is not logged on?.
I know  i can send a user and password from teensy to lon in before running my script, but i am looking for a beter aproach.

¿Any idea?

Thanks

---

