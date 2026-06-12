---
title: "[SOLVED] daru2 webcam stopped working... terminal reads '/dev/video0 does not exist'"
date: 2008-02-24
forum: System76 Support
---

### Post by tuebinger on 2008-02-24
Recently my webcam stopped working.  When I type in 'cheese' from the terminal window it prints this:

> stephen@ubuntu:~$ cheese
** Message: Probing the webcam, please ignore the following, not applicabable tries
** Message: Error running pipeline 'v4l2src ! fakesink': Cannot identify device '/dev/video0'. [v4l2_calls.c(424): gst_v4l2_open (): /pipeline0/v4l2src0:
system error: No such file or directory]
** Message: test pipeline for v4l2src failed:
[v4l2src ! fakesink]: Cannot identify device '/dev/video0'.
** Message: Error running pipeline 'v4lsrc ! video/x-raw-rgb,width=640,height=480 ! fakesink': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /pipeline1/v4lsrc0]
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-rgb,width=640,height=480 ! fakesink]: Device "/dev/video0" does not exist.
** Message: Error running pipeline 'v4lsrc ! video/x-raw-yuv,width=640,height=480 ! fakesink': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /pipeline2/v4lsrc1]
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-yuv,width=640,height=480 ! fakesink]: Device "/dev/video0" does not exist.
** Message: Error running pipeline 'v4lsrc ! video/x-raw-rgb,width=320,height=240 ! fakesink': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /pipeline3/v4lsrc2]
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-rgb,width=320,height=240 ! fakesink]: Device "/dev/video0" does not exist.
** Message: Error running pipeline 'v4lsrc ! video/x-raw-rgb,width=1280,height=960 ! fakesink': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /pipeline4/v4lsrc3]
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-rgb,width=1280,height=960 ! fakesink]: Device "/dev/video0" does not exist.
** Message: Error running pipeline 'v4lsrc ! video/x-raw-rgb,width=174,height=144 ! fakesink': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /pipeline5/v4lsrc4]
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-rgb,width=174,height=144 ! fakesink]: Device "/dev/video0" does not exist.
** Message: Error running pipeline 'v4lsrc ! video/x-raw-rgb,width=160,height=120 ! fakesink': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /pipeline6/v4lsrc5]
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-rgb,width=160,height=120 ! fakesink]: Device "/dev/video0" does not exist.
** Message: Error running pipeline 'v4lsrc ! fakesink': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /pipeline7/v4lsrc6]
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! fakesink]: Device "/dev/video0" does not exist.
using source: videotestsrc


There is no video0 (or video1 or anything like that) in the /dev directory.  It vanished somehow, I guess.  Reinstalling the System76 driver and  pressing the 'P2" button on the laptop have no effect.

The only thing I can think of is maybe I inadvertently deleted this folder somehow?!!?

How can I get my webcam working again?  

Thanks!!

PS   Smilies above were not intentional!!

---

### Post by thomasaaron on 2008-02-25
Shut down whatever application you are using the webcam with.
Press the P2 button above the keyboard -- one time.
Restart the application.

---

### Post by tuebinger on 2008-02-25
I tried this.  I get a dialog windows that says, "Unable to find webcam.  Sorry!"

---

### Post by thomasaaron on 2008-02-26
Go to a terminal and enter...
```
lsusb
```

Post the results here.

Then press your P2 button and enter...
```
lsusb
```
again.

Post those results here too.

---

### Post by tuebinger on 2008-02-26
The output after entering lsusb into terminal:

> stephen@ubuntu:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 046d:c00f Logitech, Inc. 
Bus 005 Device 002: ID 147e:2016  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0db0:a97a Micro Star International 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

and after pressing P2 button:

> 
stephen@ubuntu:~$ lsusb
Bus 007 Device 006: ID 0c45:62c0 Microdia 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 046d:c00f Logitech, Inc. 
Bus 005 Device 002: ID 147e:2016  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0db0:a97a Micro Star International 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  


---

### Post by thomasaaron on 2008-02-27
So, if you press the P2 button and make "microdia" appear in lsusb, and then open cheese, what happens?

Also, have you been playing with gstreamer-properties, by any chance?

---

### Post by tuebinger on 2008-02-27
When I press P2 and get Microdia to appear, then open Cheese, I get the message that says:  "Unable to find webcam.  Sorry!"  As for playing with the g-streamer properites, I download all the g-streamer plugins one day.  Does that count?

---

### Post by thomasaaron on 2008-02-27
Possibly.

You might try uninstalling whichever ones you installed and then testing re-installing cheese and testing it.

---

### Post by tuebinger on 2008-02-27
I tried removing the gstreamer plugins I had installed but still no affect.  When I type in lsusb in the terminal I see the Microdia webcam but when I start Cheese or Ekuga still nothing.

---

### Post by thomasaaron on 2008-02-28
I'm not sure.

My hunch is that it is a bad configuration somewhere. You might want to just do a fresh install of Ubuntu 64-bit, run the System76 driver, download cheese and run it. If it doesn't work out of the chute, you may have a hardware issue.

For install instructions, contact me via email: support(at)system76(dot)com.

---

### Post by tuebinger on 2008-03-01
Your hunch was probably right.  I reinstalled and the webcam works fine.  Problem solved!

---

