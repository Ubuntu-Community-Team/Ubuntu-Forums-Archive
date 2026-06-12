---
title: "Ubuntu Touch Emulator Blank Screen"
date: 2015-08-23
forum: Ubuntu Phone and Tablet
---

### Post by kagashe on 2015-08-23
I have used following commands to install and use Ubuntu Touch Emulator as per[ this guide]("https://wiki.ubuntu.com/Touch/Emulator#Using_the_emulator"):
sudo apt-get install ubuntu-emulator
sudo ubuntu-emulator create myinstance (you can use any name for "myinstance")
ubuntu-emulator run myinstance

Then I used following command to reduce the window size and make the boot fast:
ubuntu-emulator run myinstance --scale=0.5 --memory=1024

The emulator Window is a Blank Screen although I could login to the terminal.
Please see the attached screenshot
[ATTACH=CONFIG]264007[/ATTACH]

How can I solve the Blank screen problem and use the emulator?

Kamalakar

---

### Post by kagashe on 2015-08-24
Finally I could succeed after installing [ubuntu-sdk]("http://developer.ubuntu.com/en/start/ubuntu-sdk/installing-the-sdk/") through ppa:
sudo add-apt-repository ppa:ubuntu-sdk-team/ppa
sudo apt update && sudo apt install ubuntu-sdk

and install the emulator through ubuntu-sdk

I have opened the browser on the emulator which you can see in the screenshot:
[ATTACH=CONFIG]264026[/ATTACH]

Kamalakar

---

