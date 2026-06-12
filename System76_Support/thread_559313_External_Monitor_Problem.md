---
title: "External Monitor Problem"
date: 2007-09-25
forum: System76 Support
---

### Post by mrshores on 2007-09-25
Running Feisty on a System 76 Pangolin notebook.  Want to connect to a Dell 17" Flat Screen, but not working.  From the key icons, I am assuming that F3 should toggle between on-board display and external monitor.  Nothing happens.  I know the monitor is OK and the cable is OK.  Monitor senses the PC and switches from 'test mode' to blank screen.  Is there a special sequence of events I must follow to make this work?  I have seen that with some older notebooks.  Stumped for the time being.

MichaelPS

---

### Post by thomasaaron on 2007-09-25
Try connecting the monitor to the Pangolin before booting it up.

---

### Post by mrshores on 2007-09-25
Having monitor connected and turned on makes no difference.  I have also learned that the Function-F3 key combination is not enabled on the Pangolin.  I see two graphics drivers.  One is presumably for the on-board and the 2nd for the external VGA.  However, nothing for the external shows up for configuring monitor settings, just for the on-board.

---

### Post by thomasaaron on 2007-09-25
Please go to the system 76 driver and post the model number for your computer that it reports: (System > Administration > System 76 Driver)

I believe you have an PanV2. Correct?

Also, are you using the blue VGA out port, or are you using the S-Video out?

Try this:
1. Shut down your computer
2. Plug the external monitor into the vga out (blue) port
3. Turn the computer back on.
3. As soon as you see the Intel splash screen, press the Fn-F3 key. Wait for a second. Did you get a pic on your monitor? Now do it again. And again. This key will cycle through three different LCD/External Monitor combinations.
4. Put it on the combination you want and let the computer continue to boot.

---

