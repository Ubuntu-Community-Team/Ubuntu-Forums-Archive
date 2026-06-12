---
title: "Raspberry Pi Error"
date: 2017-11-21
forum: Ubuntu, Linux and OS Chat
---

### Post by cooleo15 on 2017-11-21
Hi all. I am attempting to make a raspberry pi wind speed sensor that sends data to the pins of the raspberry pi. However when i try to install the GPIO packages needed to use the pins by using 

sudo apt-get update
sudo apt-get install python-dev python-pip
sudo pip install --upgrade distribute
sudo pip install ipython
sudo pip install --upgrade RPi.GPIO

It yields the following error when I run the third line in the terminal:

Cannot fetch index base URL [http://pypi.python.org/simple/Could](http://pypi.python.org/simple/Could) not find any downloads that satisfy the requirement distribute in /usr/lib/python2.7/dist-packages
No distributions at all found for distribute in /usr/lib/python2.7/dist-packages
Storing complete log in /root/.pip/pip.log

I have scoured the internet for solutions but cannot find one. Any help would be much appreciated. Thanks!

---

