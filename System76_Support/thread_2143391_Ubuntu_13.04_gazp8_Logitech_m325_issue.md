---
title: "Ubuntu 13.04 gazp8 Logitech m325 issue"
date: 2013-05-08
forum: System76 Support
---

### Post by insanengineer on 2013-05-08
Since my upgrade to Ubuntu 13.04 on my gazp8 laptop I have been having issues with my Logitech M325 mouse. It intermittently stops working. The mouse cursor just freezes on the screen for about 1-2 seconds then the mouse resumes working normally. The scroll wheel also ceases to function. While the mouse is unusable the laptop touch pad still functions normally. I have tried replacing the mouse battery and disabling the touch pad, but neither seem to have helped.  I have also done a clean install of 13.04 to resolve another issue i was having. Has anyone else had this issue with any Logitech mice?

This mouse worked perfectly fine before the upgrade. 

I have been doing some searching on the web but I have yet to find a solution

---

### Post by isantop on 2013-05-09
Which port do you have your unifying receiver plugged into? Also, do you have any other devices paired to the Unifying Receiver.

---

### Post by insanengineer on 2013-05-09
I have the receiver plugged into the left USB port (the USB 2.0 port). Nothing else is connected to the receiver. I also have the latest system 76 driver installed

---

### Post by isantop on 2013-05-10
Try repairing the mouse to the receiver. You can do this in Ubuntu using the Unifier Utility:

[http://www.launchpad.net/unifier](http://www.launchpad.net/unifier)

---

### Post by insanengineer on 2013-05-10
Alright I tried that and it is still happening just less often now. I also tried moving the receiver to one of the usb 3.0 ports and the same issue happens

For the benefit of others here is how to install the unifier since it is not in the standard Ubuntu 13.04 repo

first run the following command to add the PPA 
```
sudo add-apt-repository ppa:unifier-dev/unifier-release
```


then run this command next to include the contents of the new repo in you lists
```
sudo apt-get update 
```


Now you can run the next command to install the application
```
sudo apt-get install unifier
```

---

