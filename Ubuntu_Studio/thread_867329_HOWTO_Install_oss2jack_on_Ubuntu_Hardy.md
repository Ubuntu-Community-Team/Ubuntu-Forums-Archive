---
title: "HOWTO: Install oss2jack on Ubuntu Hardy"
date: 2008-07-22
forum: Ubuntu Studio
---

### Post by motin on 2008-07-22
oss2jack allows you to route one or many OSS-based applications' sound to the JACK server - allowing for OSS-based applications to use the sound card simultaneously as well as allow them to be used with music production software.


Howto install:

1. Install prerequisites:
```
sudo apt-get install libfusd1 libfusd-dev libsamplerate0 libsamplerate0-dev
```

2. Download and compile oss2jack
```
cd /tmp/
wget http://fort.xdas.com/~kor/oss2jack/oss2jack-0.24.tar.gz
tar xvzf oss2jack-0.24.tar.gz
cd oss2jack-0.24
./configure --with-fusd=/usr
make
```

3. Install using checkinstall, allowing for easier uninstallaion later - (Use default values for the questions):
```
sudo apt-get install checkinstall
sudo checkinstall
```

Now we need a kernel module (repeat this step if you upgrade or switch kernel):

4. Download module source, compile and install:
```
sudo apt-get install fusd-kor-source
sudo m-a a-i fusd-kor
sudo apt-get install fusd-kor-module

```

5. Add Udev rules so that the device files to interact with the module are created upon module load:
```
echo 'SUBSYSTEM=="fusd", NAME="fusd/%k", MODE="0660", GROUP="audio"' | sudo tee /etc/udev/rules.d/fusd.rules
```

6. In order to run oss2jack as an ordinary user (without sudo), you need to be part of the audio group:
```
sudo adduser $USER audio
```
If you hadn't done this before, log out and log back in now.

7. Here, start JACK (using qjackctl or your preferred method)

8. Unload OSS modules, load the fusd module and start oss2jack:
```
sudo modprobe kfusd
sudo rmmod snd-pcm-oss
sudo rmmod snd-mixer-oss
oss2jack
```

Now start your application that uses /dev/dsp and hear how the sound gets routed through JACK!

To start more than one OSS application, start oss2jack like follows:
```
oss2jack -n 2
```

And then start your second application and tell it to use /dev/dsp2

You can do it for 3 and 4,5,6,7... etc. 

You should be up and running!

Sources (may contain more interesting stuff as well...):
[http://fort2.xdas.com/~kor/oss2jack/install.html](http://fort2.xdas.com/~kor/oss2jack/install.html)
[http://ubuntuforums.org/showthread.php?t=208488&highlight=realtime-lsm](http://ubuntuforums.org/showthread.php?t=208488&highlight=realtime-lsm)
[http://gentoo-wiki.com/HOWTO_Jack#Configuring_software_to_use_JACK](http://gentoo-wiki.com/HOWTO_Jack#Configuring_software_to_use_JACK)
[http://gentoo-wiki.com/HOWTO_oss2jack](http://gentoo-wiki.com/HOWTO_oss2jack)

---

### Post by KoenW on 2008-11-10
forgot a build-package: module-assistant to build the modules and the linux-headers (for your specific kernel).

---

### Post by thorgal on 2008-11-10
last time I compiled kfusd from fusd-kor was against kernel 2.6.24. I tried a week ago against 2.6.27 but to no avail. Some stuff has changed in some structure definition used in the kernel. Unless someone has already updated fusd-kor for recent kernels, you are stuck with older kernels. However, more recent kernels and stable RT operations seem to be 2 exclusive concepts ... 2.6.24 is according to my own experience the most stable RT kernel on the market.

---

