---
title: "gnokii to send sms"
date: 2010-08-16
forum: Server Platforms
---

### Post by Tutigan on 2010-08-16
so, I am using ubuntu server 10.04, with gnokii installed (the latest from apt-get) but have had a few problems...
I've searched on the gnokii wiki, looked through the FAQ and googled 'til my fingers dropped off...
Basically, I have set it up exactly as per instructions on their website, and am using the config they give for the phone (Nokia 6120c), where I think I am falling down is this line of the config:
```
port = /dev/ttyACM0
```
How can I be sure that that is the correct port?
I have plugged the phone in via USB cable, but get errors about the port it is plugged into (I'm not on-site atm, but will post errors when I'm back)

---

### Post by gobbledigook on 2010-08-17
i have never used this, but a quick search reveals :

lots of information in the [**_user guide_**]("http://wiki.gnokii.org/index.php/User's_Guide") on [**_configuration_**]("http://wiki.gnokii.org/index.php/User's_Guide#Configuration") also info on which [**_port_**]("http://wiki.gnokii.org/index.php/Config#Port") to use. Looks like that is the correct port for a USB connection... however i would check the model of the cable, also check out the [**_man page_**]("http://linux.die.net/man/1/gnokii") for gnokii esp the section on sms.

:)

---

