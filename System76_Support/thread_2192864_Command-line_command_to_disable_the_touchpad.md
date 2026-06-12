---
title: "Command-line command to disable the touchpad?"
date: 2013-12-10
forum: System76 Support
---

### Post by volkerbradley on 2013-12-10
My system is Ubuntu 13.10, 64-bit.  I have a laptop with a touchpad that is not controlled by a synaptics driver.
Am presently using  the touchpad-indicator application to disable the touchpad.
When I click on the touchpad-indicator Prefences, the application crashes. Seems to be looking for a synaptics driver.
Is there a command-line command in the touchpad-indicator application to disable the touchpad?

---

### Post by Bucky Ball on 2013-12-10
What machine are you using?

---

### Post by volkerbradley on 2013-12-10
I am using a System76 Serp6.
Here is what System76 has to say about my touchpad problems:
"We're aware of this issue. It's complicated by the fact that this trackpad actually works in a way similar to a theramin than a Synaptics touchpad. Currently, the best solution I can provide is to turn the trackpad off (Fn+F1) while typing, then turn it back on when you're finished. "

---

### Post by codenine75a on 2013-12-10
alternative, use an external mouse.

---

### Post by Bucky Ball on 2013-12-10
*Thread moved to **System76 Support**.*

You might have more luck here as seems specific to the System76 touchpad. This kinda says it all:

> ... this trackpad actually works in a way similar to a theramin than a Synaptics touchpad.

---

### Post by volkerbradley on 2013-12-10
Well, I turn off the touchpad and use the mouse.  However, every time I reboot, I have to be sure to turn off the touchpad in the touchpad-indicator application.  It used to be possible to set the preferences in the touchpad-indicator to have the touchpad be turned off when touchpad-indicator started at boot time.  However, when clicking on "Preferences" in the touchpad-indicator app. causes this application to crash now and no longer works.
That is why I asked my specific question:  Is there a command-line command to turn off the touchpad in the touchpad-indicator application?  
Can't seem to find an answer to this question.

---

### Post by jbelmonte on 2013-12-10
Is there a reason you can't/don't want to turn the trackpad off using (Fn+F1)?

reason for edit: typo

---

### Post by volkerbradley on 2013-12-10
Although your response does not answer my question of: "Is there a command-line command to turn off the touchpad in the touchpad-indicator application?' I'll answer your question.
I tried the Fn-F1 routine for a long time. There were times when I just neglected to click on these keys until havoc occurred.  Therefore I am looking for an automatic solution that the touchpad-indicator provided through Preferences.  Unfortunatley, clicking on Preferences crashes the entire application now.  That is why am looking for a command-line command that I can use to set the touchpad to be disabled.  Sure wished that I could program in python.  Suredly, the answer is in the code of the touchpad-indicator application.

---

### Post by Dave_L on 2013-12-10
On my computer, these commands work:

Enable touchpad:
```
xinput --set-prop 'FSPPS/2 Sentelic FingerSensingPad' 'Device Enabled' 1
```

Disable touchpad:
```
xinput --set-prop 'FSPPS/2 Sentelic FingerSensingPad' 'Device Enabled' 0
```

The parameter 'FSPPS/2 Sentelic FingerSensingPad' is the device name for my touchpad. On your computer, use this command to determine the device name:
```
xinput --list
```

For more information:
```
man xinput
```

---

### Post by volkerbradley on 2013-12-11
The command > xinput --set-prop 'FSPPS/2 Sentelic FingerSensingPad' 'Device Enabled' 0 works perfectly on my laptop as well.
Thank you very much for pointing me in the right direction.

---

### Post by vasa1 on 2014-02-17
> **Dave_L said:**
> On my computer, these commands work:

Enable touchpad:
```
xinput --set-prop 'FSPPS/2 Sentelic FingerSensingPad' 'Device Enabled' 1
```

Disable touchpad:
```
xinput --set-prop 'FSPPS/2 Sentelic FingerSensingPad' 'Device Enabled' 0
```

The parameter 'FSPPS/2 Sentelic FingerSensingPad' is the device name for my touchpad. On your computer, use this command to determine the device name:
```
xinput --list
```

For more information:
```
man xinput
```

Another way to use xinput is to run just **xinput** and look at the output to find the relevant device's ID.

Then,
*xinput --disable xx*
and *xinput --enable xx*
are enough (where *xx* is the device ID obtained from the output of *xinput*.)

---

### Post by Dave_L on 2014-02-17
I formerly used the device ID, but the disadvantage is that it can change each time you boot.  To address that, I wrote a complicated script to extract the ID from the output of xinput.

Then I found that you can use the device name instead of the ID. So you can have a simple command that works all the time.

---

### Post by vasa1 on 2014-02-18
> **Dave_L said:**
> I formerly used the device ID, **but the disadvantage is that it can change each time you boot**.  To address that, I wrote a complicated script to extract the ID from the output of xinput.

Then I found that you can use the device name instead of the ID. So you can have a simple command that works all the time.

Thanks, I didn't know about the id changing!

---

