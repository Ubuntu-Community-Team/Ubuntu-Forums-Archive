---
title: "setting up a single board computer as a HMI"
date: 2023-11-19
forum: Ubuntu Application Development
---

### Post by z-simon-0 on 2023-11-19
I am looking at designing a HMI. To do this I will use a SBC running linux (Ubuntu server) with just one program running for the user to interact with. I have found Squareline Studio, is this a good choice or are there others ways to accomplish this?

---

### Post by TheFu on 2023-11-19
What do you mean by "HMI"?  It isn't a common term.

---

### Post by #&amp;thj^% on 2023-11-19
A Human-Machine Interface (HMI) is a user interface or dashboard that connects a person to a machine, system, or device. While the term can technically be applied to any screen that allows a user to interact with a device, HMI is most commonly used in the context of an industrial process.

HMIs are similar in some ways to Graphical User Interfaces (GUI) but they are not synonymous; GUIs are often leveraged within HMIs for visualization capabilities.
But for the OP I have no use for one so I can't say if Squareline Studio is good choice or not.
Perhaps a little more information may help us with what your trying to accomplish.
There just might be a better way to go.

---

### Post by z-simon-0 on 2023-11-20
Human Machine Interface indeed. It's the technical term for your mouse and keyboard and the words HMI will feature in the device manager I believe. In my previous job the HMI was a custom machined box with an 8 bit micro controller board custom designed inside with switches as inputs and LED's as outputs.

In my new job things have advanced somewhat and we make small portable machines. I have a machine ECU that talks CAN bus and there is to be the HMI that the user uses to control the machine tat will send commands to the ECU and get back information on the machine that it displays. We have reached a point where a single board computer makes sense and so need to create visualizations of speed and and motor torque for example. Buttons will be used to work a menu system or navigate between items on the screen and change their values.

---

### Post by TheFu on 2023-11-20
I've heard HID used for keyboard and mouse and remote controls.  

I used to work in avionics software. We didn't use the HMI term there, though obviously the entire cockpit was full of it.  

Sorry, I can't recall all the different process view software that ran on Unix.  I think LabView is MS-Windows only (don't quote me) now, but they had a Linux version previously.  One of the guys on my team left for NI when the project was finished. He was an excellent programmer. Actually all the people on my sub-project were excellent programmers. At the time, I was the noob.

---

### Post by z-simon-0 on 2023-11-23
Ah yes, it is HID, my bad. Well anyway, yes Labview does not seem to support linux and will be very pricey.

---

