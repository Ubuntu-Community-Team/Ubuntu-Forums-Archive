---
title: "Problems getting tuncfg to be run at boot"
date: 2006-07-12
forum: Server Platforms
---

### Post by nameiwantistaken on 2006-07-12
I've been working through a problem getting hamachi to work on my Ubuntu linux box. I had it working, but when I reboot, I get the dreaded

12 00:35:36.026 [ 0] [ 7514] tap: connect() failed 2 (No such file or directory)

error. I did some reading on your site and it seems this is a problem with tuncfg not being run. I'm using the config file here

[http://doc.gwos.org/index.php/VNC_and_Hamachi](http://doc.gwos.org/index.php/VNC_and_Hamachi)

and from the looks of things it should be starting it. Could there be something I did wrong? Does the #!/bin/sh get put at the start of the file? How can I make all of this just start when the machine is booted? Any advice would be appreciated.

---

### Post by sidd-tx on 2006-07-25
Sorry I can't offer a definite fix. The script looks correct, and yes,, you do have to put the "#!/bin/sh" at the beginning of the script. I have Hamachi installed and running. I used this guide:

[http://www.ubuntuforums.org/showthread.php?t=135036](http://www.ubuntuforums.org/showthread.php?t=135036)

And the only issue I have concerns automatically connecting to the hamachi network I created. After each boot, I use the following command:

sudo hamachi -c /etc/hamachi go-online network

and it connects without any errors. I don't see any of the errors you posted. Try starting from the beginning of the guide I posted above, It worked for me..  I am currently looking around these and other forums to see if I can get hamachi to automatically login to my network without need ing any intervention from me. If I find something, I'll post it here also..


Sidd...

---

