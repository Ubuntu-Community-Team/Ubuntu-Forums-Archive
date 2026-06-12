---
title: "Graphics driver on Merkat"
date: 2011-04-05
forum: System76 Support
---

### Post by tc101 on 2011-04-05
On my new Merkat Ion, when I go to system/preferences/monitors, I get this message:

"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"

What should I do?  Click Yes or No or what?

The monitor is a Dell flat screen, but I can't find the model number.  It is about 3 years old.

---

### Post by tc101 on 2011-04-05
One other related question.  Can I use two monitors with this system?

I tried plugging in two to the two different monitor ports, but it only recognises the one plugged into the smaller socket.

---

### Post by isantop on 2011-04-05
You'll want to click Yes there. It will take you to Nvidia's monitor configuration utility. This will allow you to set up both of your monitors.

---

### Post by tc101 on 2011-04-05
I messed something up.  When I started working on this it showed both monitors.

---

### Post by tc101 on 2011-04-05
The E228WFP on the left is the one I can see.  The other is blank.  I set  the one on the right, the E207WFP for twin view, did a restart, and now it show as disabled.

---

### Post by isantop on 2011-04-06
After you make settings changes in that Nvidia configuration utility, you'll to make sure you click on "Save to X configuration file". That will take your changes and save them on the system so that Ubuntu uses those instead of loading the defaults over again.

You may get an error the first time you run it about not being able to parse the existing configuration file. That's okay, since there isn't one yet. Just click okay, then save the file in the default location.

---

