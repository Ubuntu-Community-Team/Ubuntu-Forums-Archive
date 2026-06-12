---
title: "Need help installing NVIDIA driver"
date: 2013-02-03
forum: System76 Support
---

### Post by volkerbradley on 2013-02-03
Just did a new install of Ubuntu 12.10 on my Serp6. I followed the instructions at [http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)
My video card is a NVIDIA G92[GeForce GTX 258M]
Unfortunately, I am seeing the following error message:

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run 'nvidia-xconfig' as root], and restart the X server.

What steps should I follow to install the correct driver and get it to work?

---

### Post by strid3r on 2013-02-03
I had the same problem installing NVIDIA drivers on 12.10, you probably need to install the headers for your kernel.

Just type the following into terminal:
```
sudo apt-get install linux-headers-$(uname -r)
```

Then just re-install NVIDIA drivers (I'm assuming you're using 310 experimental)
```
sudo apt-get install --reinstall nvidia-experimental-310 
```

Just reboot after that and you should be good to go!

---

### Post by volkerbradley on 2013-02-03
> **strid3r said:**
> I had the same problem installing NVIDIA drivers on 12.10, you probably need to install the headers for your kernel.

Just type the following into terminal:
```
sudo apt-get install linux-headers-$(uname -r)
```

Then just re-install NVIDIA drivers (I'm assuming you're using 310 experimental)
```
sudo apt-get install --reinstall nvidia-experimental-310 
```

Just reboot after that and you should be good to go!
Wow, your response was quick and very helpful.
NVIDIA driver is now installed.
Thank you very much.

---

