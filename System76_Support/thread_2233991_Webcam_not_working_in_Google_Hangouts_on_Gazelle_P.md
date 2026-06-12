---
title: "Webcam not working in Google Hangouts on Gazelle Professional"
date: 2014-07-11
forum: System76 Support
---

### Post by mecrider on 2014-07-11
I just purchased a Gazelle Professional, shipping with Trusty 14.04. The webcam works fine in Cheese and guvcview, but Google Hangouts using google-talkplugin 5.4.2 amd64 says there is no webcam. I tried creating a script for GoogleTalkPlugin with LD_PRELOAD pointed to usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so, but the script causes the plugin to crash when it loads. Any ideas how to get the Bison NB Pro cam working with googletalk?

---

### Post by mecrider on 2014-07-11
An additional note - I turned off the webcam with the function key and plugged in a USB webcam I have been using for Google Hangouts on another computer with Trusty 14.04, and it does not work either. Hangouts Settings says it does not detect a webcam connected to the computer. Is there some additional package I need to install that doesn't come with Ubuntu on System76 installs?

---

### Post by rss3ks on 2014-07-18
I had the same problem develop about 3 days ago.  I have a new system 76 laptop.  I hope its not a hardware falure. I have had Ubuntu 14.04 installed for a couple of months the web onboard web cam worked perfetly untill a couple of days ago.  I have not made any physical changes exept for allowing updater to run I think sometime arrond the same time fram.  A lsusb produces the following:

 Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 8087:07dc Intel Corp. 
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

On mine Cheese does not function.  It gives an error message "No device found".

Please help me fix this as I need the web cam for classes i am curretly taking!!

Thanks in avance.

Rob

---

### Post by a-emma on 2014-07-21
Hello,

My name is Emma and I'm happy to help with your Google Hangouts and webcam concerns on your Gazelle Professional. Are you using Chrome? If you install Chrome and Google Talk Plugin, the webcam should work after restarting the browser. If you use the function key and f10 to turn the webcam on, you may still need to click the camera icon within the hangout to turn it on. The hangouts should work without any extra packages beyond installing Chrome and Google Talk Plugin. If you are using Firefox, please attempt to use the Hangout in Chrome and see if that fixes. If not, please login to your System76 account and speak with our support staff to diagnose if there's an alternative solution. They will be happy to help!

Kind Regards,
[email]Emma@System76.com[/email]

---

