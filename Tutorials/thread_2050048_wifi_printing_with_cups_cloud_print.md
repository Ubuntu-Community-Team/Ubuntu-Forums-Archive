---
title: "wifi printing with cups cloud print"
date: 2012-08-29
forum: Tutorials
---

### Post by Richardky on 2012-08-29
If your using a wifi printer and have no 64bit driver support like me you can try a nifty little program called _Cups Cloud Print_ 

CUPS Cloud Print is a Google Cloud Print driver for UNIX

what this does is it uses google cloud print as your system wide print driver assuming you have a wifi capable printer or cloud print ready device.

to install run in terminal
 
```
sudo add-apt-repository ppa:simon-cadman/cups-cloud-print
sudo apt-get update
sudo apt-get install cupscloudprint
sudo /usr/lib/cloudprint-cups/setupcloudprint.py
``` 

Follow the instructions about authorising CUPS Cloud Print to use your Google Account for printing, and you’re done.

(_google account required_) 

I now can use my Lexmark 6675 no problems at all which was a large paper weight until i found this awsome nifty software


original site and credit to author located here [http://www.niftiestsoftware.com/cups-cloud-print/]("http://www.niftiestsoftware.com/cups-cloud-print/")

---

