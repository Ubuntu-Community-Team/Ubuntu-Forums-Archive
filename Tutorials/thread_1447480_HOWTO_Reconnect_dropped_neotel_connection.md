---
title: "HOWTO: Reconnect dropped neotel connection"
date: 2010-04-05
forum: Tutorials
---

### Post by aquavitae on 2010-04-05
This is a howto for all those frustrated South Africans using Neotel's somewhat erratic network.

I've found that the connection occasionally drops, for no apparent reason, and can't be reconnected without physically reconnecting the modem. So I've written a startup script to automatically redial when the connection is lost. 

To install:
[LIST=1]
[*]Download the attached tar file and save it to your home folder.
[*]Open a terminal and run the following commands:
[*]Untar the downloaded file:
```
tar -xf redialneotel.tar
```
[*]Copy the two files it extracts to the correct system folders:
```

sudo cp redialneotel.sh /usr/bin
sudo cp redialneotel /etc/init.d

```
[*]Create symlinks to the init directories:
```

sudo ln -s /etc/init.d/redialneotel /etc/rc2.d/S99redialneotel
sudo ln -s /etc/init.d/redialneotel /etc/rc3.d/S99redialneotel
sudo ln -s /etc/init.d/redialneotel /etc/rc4.d/S99redialneotel
sudo ln -s /etc/init.d/redialneotel /etc/rc5.d/S99redialneotel
[code]
[*]Make sure that the ppp name is correct
[code]sudo gedit /usr/bin/redialneotel.sh
```
and change the variable PPPNAME from neotel to whatever you've set it up as (using pppoe).
[*]Start the service
```
sudo /etc/init.d/redialneotel start
```

To uninstall simply delete the following files (as root):
```

sudo rm /usr/bin/redialneotel.sh
sudo rm /etc/init.d/redialneotel
sudo rm /etc/rc2.d/redialneotel
sudo rm /etc/rc3.d/S99redialneotel
sudo rm /etc/rc4.d/S99redialneotel
sudo rm /etc/rc5.d/S99redialneotel

```
[/LIST]

This is my first real attempt at bash scripting and writing an init daemon, so I would welcome any suggestions on how to improve what I've done. I hope its helpful to someone in the meantime!

---

### Post by Nick Kruger on 2012-03-24
Hi Aquavitae,

I see this is a very old post .... 

I have managed to get my old Neotel phone working with Ubuntu, but of course, I've encountered this problem of not being able to reconnect after the connection drops - except by unplugging and replugging the usb connection back in.

I'm trying to understand what exactly causes this problem - your fix is a little above me. Can you briefly explain the issue ?

Thanks,
Nick

---

