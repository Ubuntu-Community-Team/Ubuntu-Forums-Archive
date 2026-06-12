---
title: "Howto Get Eyetoy Webcam working for Ubuntu"
date: 2006-10-06
forum: Tutorials
---

### Post by Josh1 on 2006-10-06
Welcome to my second guide, "Howto: Get Eyetoy Webcam working for Ubuntu". **This guide cannot be copied, or ripped, but instead just link to this post if you want to tell people about it, thanks. This way when I update this post, everyone always has the latest version!**

[CENTER][B][COLOR="Red"][SIZE="4"]Before you do anything, you are required to have an Eyetoy Webcam, here is a picture:
[IMG]http://images.google.com.au/images?q=tbn:4puQV2ht5j__nM:http://analogik.com/_images/pic_eyetoy_camera.jpg[/IMG][/SIZE][/COLOR][/B][/CENTER]

**Step 1: Inserting the Eyetoy and checking if it is detected by Ubuntu.**
First, plug in the USB into the USB slot, and enter Device Manager (System>Administration>Device Manager).
Scroll down, and see if the Eyetoy was detected by Ubuntu. It should look something like [this]("http://i100.photobucket.com/albums/m4/jtaylor231/devicemanager.png").

**Step 2: Downloading and Installing the drivers needed.**
Load Terminal (Applications>Accesories>Terminal) and type in these commands:

```

sudo apt-get install build-essential linux-headers-`uname -r`

```
This will download and install the things needed to install the drivers. It will also download and install the headers for the kernel you are using.

```

wget http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz

```
This will begin to download the driver. Make sure you save it into your **home directory.**

Now, type in the following commands:
```
tar -xvf ov51x-jpeg-0.5.4.tar.gz
cd ov51x-jpeg-0.5.4
```
This will enter the directory for the drivers.

Now, lets install the drivers:
```

sudo make install
sudo modprobe videodev
sudo modprobe i2c_core
sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
sudo insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko

```
Type these in 1 line at a time!.

Now, to see if it worked, type into terminal:
```
sudo apt-get install xawtv
```
This will install "xawtv" where you can view the webcam, and see if it was working.
Here is mine (note that I am mucking around with settings, so the hue and stuff is mucked up so its brighter then it really is:
[http://i100.photobucket.com/albums/m4/jtaylor231/xawtv.png](http://i100.photobucket.com/albums/m4/jtaylor231/xawtv.png)

**[CENTER]If anyone has the sound working, please PM me ASAP.[/CENTER]**

---

### Post by stalefries on 2006-10-06
Very nicely written, though I'm sorry to sya I don't have an Eye Toy, so I fail!

---

### Post by Darrious on 2006-10-08
Mine is working, but same as you I can't seem to get the sound working.
Also I need better webcam software than xawtv.

---

### Post by Darrious on 2006-11-02
I would really like to know if anyone has gotten sound working yet.

---

### Post by davim on 2006-12-12
I didn't but someone did:

"Hi, I've found that the audio device of the camera is /dev/dsp1, so I've tried it with VLC media player...In VLC go to the File menù and then to "Open Capture Device", and on audio peripheral line, change this "/dev/dsp"to"/dev/dsp1"... If you don't do it,a terrible sound will go out from your speakers! I think it should work with the other programs that can use the same config. For example, "Skype" in it's "Sound Device" options,(ALSA mode)allow you to use "Logitech Eye Toy USB Camera" as Audio In, or (in OSS mode) /dev/dsp - /dev/dsp1. That's all! :)"

from: [http://www.smorgasbord.net/howto_get_eyetoy_webcam_working_for_ubuntu](http://www.smorgasbord.net/howto_get_eyetoy_webcam_working_for_ubuntu)

---

### Post by xlyz on 2006-12-24
I tested it in ekiga and it autodetected the eyetoy as audio source: the sound is working :)

---

### Post by davim on 2006-12-28
Mine doesn't say Logitech EyeToy, it says it's a Namtai eyetoy and it's working now :)

---

### Post by zehntagebart on 2007-01-13
This installation guide is great.
My Hercules Classic Deluxe works with it.
But if i restart i have to do

sudo modprobe videodev
sudo modprobe i2c_core
sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
sudo insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko

sudo modprobe i realised by adding them to /etc/modules

but what do i have to do with the last twho lines so that the cam works after a reboot?

---

### Post by gentle_turtle on 2007-01-20
I have the same problem with the hercules classic webcam too: every time i reboot I have to restart the modules by hand..... Well, actually, just the ov519_decomp one, because the ov51x module gets indeed started, even at bootup. How does one start the ov519_decomp at bootup?

Also, does one know how to avoid that the LEDs of the cam remain on with little light??

---

### Post by dvarsam on 2007-01-20
Hello!

I just added your product on the Ubuntu wiki Hardware Page:

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)

Look under the brand "Sony" & you will find your product.
IF you happen to know the details missing (on some of those cells) please edit that Page & add the necessary info.

Thanks.

P.S.> In the future, if you happen to own other Hardware & have added a post inside the "Faqs, Howto, Tips & Tricks" section of Ubuntu Forums, on how to make it work, please don't forget to add it also in the wiki.

---

### Post by gentle_turtle on 2007-01-21
I have taken a look a little bit deeper: recall my problem was I could
not get my Hercules Webcam classic working from bootup but only by
typing the single "insmod" line in the shell.

Having added to /etc/modules the following lines:

videodevice
i2c_core

starts these two modules as expected, and the modules can be seen through
doing a "sudo lsmod". The module for the camera itself, which is ov51x, 
gets loaded at bootup correctly if I have the webcam plugged in in my USB.

The problem seems to be the ov519_decomp module:
if I type i the shell "sudo insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko"
the camera gets loaded properly and works just fine....

if instead I type "sudo modprobe ov519_decomp", then the ov511 module gets loaded 
automatically, and the operation generates errors, because ov519_decomp tries
to access the functions through ov511 and not through ov51x. 
In this case, I cannot use the cam.
The error message says things about unknown symbols in the ov519_decomp module.

Dmesg reports the following (as a consequence of "modprobe ov519_decomp"):

[42950435.810000] usbcore: registered new driver ov511
[42950435.810000] drivers/usb/media/ov511/ov511.c: v1.64 for Linux 2.5 : ov511 USB Camera Driver
[42950435.810000] ov519_decomp: disagrees about version of symbol ov511_deregister_decomp_module
[42950435.810000] ov519_decomp: Unknown symbol ov511_deregister_decomp_module
[42950435.810000] ov519_decomp: disagrees about version of symbol ov511_register_decomp_module
[42950435.810000] ov519_decomp: Unknown symbol ov511_register_decomp_module

My question is: How can I avoid that the module ov511 gets gets loaded when I
modprobe the ov519_decomp module? Or, alternatively, where should I insert
in the "sudo insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko"
line in the /etc/init.d bootup scripts so as to load the module through "insmod"?

Many thanks in advance

Turtle

---

### Post by Enverex on 2007-01-21
> **dvarsam said:**
> Hello!

I just added your product on the Ubuntu wiki Hardware Page:

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)

Look under the brand "Sony" & you will find your product.
IF you happen to know the details missing (on some of those cells) please edit that Page & add the necessary info.

Thanks.

P.S.> In the future, if you happen to own other Hardware & have added a post inside the "Faqs, Howto, Tips & Tricks" section of Ubuntu Forums, on how to make it work, please don't forget to add it also in the wiki.

Is this the OFFICIAL Hardware support page? I was looking at another Wiki (for Ubuntu) that seemed to have a bit more but was offsite and I can't figure out which ones are real and if any of them are actually still active (the one on the Ubuntu domain seems very, very sparse).

---

### Post by gentle_turtle on 2007-01-22
I have solved the problem with the Hercules classic webcam. I will post in a separate HowTo thread how to do it.

---

### Post by gentle_turtle on 2007-01-22
It toook me quite a while to figure this one out, so I post how I did it: I also do not seem to be able to open up a new thread for this (partially new) HowTo, so I post here. The info I collected stems from this thread and from [http://blog.thedarkmere.net/index.php?/archives/14-Ubuntu-ov51x-jpeg-guide.html](http://blog.thedarkmere.net/index.php?/archives/14-Ubuntu-ov51x-jpeg-guide.html). I had to modify the latter end steps though to make it work properly.

The preliminaries: My machine is an IBM Netvista PC (PIII 1Gig), Ubuntu 6.06 Dapper, server installation with additional XUbuntu interface addon.

The Hercules Classic Webcam is an el-chepo webcam incorporating 4LEDs for low lighting usage. "lsusb" sees the camera as "Omnivision Technologies, Inc". The drivers needed to make it work are the ov51x and ov519_decomp modules.

I assume in this description that your camera is seen on the USB bus, otherwise yuo have to activate and make sure that USB works properly by activating the bus. You can find in this site enough descriptions on how to do that..

Once the cam is seen on the USB bus, the following procedure gives you a fuly functional cam on your Ubuntu 6.06 dapper machine:

1. Get the linux headers for your system, so that you can compile the drivers once you downloaded them. To do this, open a terminal window (Applications -> Terminal on XUbuntu) and type

sudo apt-get install build-essential linux-headers-`uname -r`

2. Get the modules for your webcam: 

wget [http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-0.5.4.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-0.5.4.tar.gz)

Ensure the drivers landed into a directory you know ;-)

3. Move to the directory where your downloaded drivers are, and extract the source files from the tar files.

tar -xvf ov51x-jpeg-0.5.4.tar.gz

4. Change directory to where your sources are:

cd ov51x-jpeg-0.5.4

5. Compile and install the modules:

sudo make install

This will compile the  drivers and install them into the subdirectory of /lib/modules/your-linux-version called extra

6. If all went well, we can install the modules by hand now:

sudo modprobe videodev
sudo modprobe i2c_core
sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
sudo insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko

7. test your installation by using a camera viewing application, such as xawtv.

If all goes well, you will be able to see the output of your webcam in xawtv.

Now comes the tricky part: making such modules permanent, so that your machine recognizes the Hercules webcam both at bootup as well when you plug it in. The problem here with respect to other module installations is that for some obscure reason, the ov519_decomp module insists in loading the ov511 module when loading through modprobe, and ov511 knows nothing of some of the functions in ov519_decomp and therefore complains. 

We will thus load ov51x normally through modprobe, but we will load ov519_decomp through insmod. Let us look at the steps to do this:

1. Make sure you load the vidoedev and i2c_core modules at bootup: to do this, in the terminal type:

sudo vi /etc/modules

We use here vi, but you can actually substitute vi with any other text editor of your preference (I know, I am old and I used vi for decades ;-P). At the end of the files, add the following two lines:

videodev
i2c_core

Now save the file and quit the editor. This will guarantee that from now on at bootup the videodev and the i2c_core modules are loaded.

2. Tell Ubuntu what to do whenever it notices the camera is plugged in:

sudo touch /etc/modprobe.d/ov51x
sudo vi /etc/modprobe.d/ov51x

add to the file the following line: 

install ov51x /sbin/modprobe --ignore-install ov51x; insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko

This has to be ONLY on one line.
Save the file and quit the editor.

And voila, at next rebbot your Hercules Classic webcam is there, ready to use.... Have fun!

---

### Post by barney_1 on 2007-02-14
Trying to get this working on Kubuntu Feisty:
```
mike@krusty:~/ov51x-jpeg-0.5.4$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 054c:0155 Sony Corp.
Bus 001 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 003: ID 043d:0057 Lexmark International, Inc. Z35 Printer
Bus 001 Device 001: ID 0000:0000

```

Followed this when I had compile difficulties: [http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall](http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall)
> Please note that with newer kernels linux/config.h has been removed. To fix this simple comment the lines in ov511_decomp.c, ov518_decomp.c, ov519_decomp.c and ov51x.c, that includes the file (or remove it entirely).

Seemed to compile just fine after that.  Unfortunately it doesn't work.  Here some info that may help:
```
mike@krusty:~/ov51x-jpeg-0.5.4$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-8-generic)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  65
  Current serial number in output stream:  65
mike@krusty:~/ov51x-jpeg-0.5.4$ sudo modprobe ov51x
mike@krusty:~/ov51x-jpeg-0.5.4$ sudo modprobe ov519_decomp
WARNING: Error inserting ov511 (/lib/modules/2.6.20-8-generic/kernel/ubuntu/media/ov511/ov511.ko): Invalid module format

```

Any advice to get this working?

Thanks!

---

### Post by barney_1 on 2007-02-15
I've made some more progress in getting this to work:

I followed the suggestion from this link: [http://www.rastageeks.org/ov51x-jpeg/index.php/FAQ](http://www.rastageeks.org/ov51x-jpeg/index.php/FAQ)

> When I modprobe ov519_decomp it complains about unknown symbols. What's wrong?

If you're getting similar messages in dmesg:

ov519_decomp: disagrees about version of symbol ov511_deregister_decomp_module
ov519_decomp: Unknown symbol ov511_deregister_decomp_module
ov519_decomp: disagrees about version of symbol ov511_register_decomp_module
ov519_decomp: Unknown symbol ov511_register_decomp_module

It's likely that the ov511 driver included in the 2.6 kernel is getting in the way. Move it someplace and try again:

# mv /lib/modules/`uname -r`/kernel/drivers/usb/media/ov511.ko \
     /lib/modules/`uname -r`/kernel/drivers/usb/media/ov511.ko.orig
# depmod -a
# modprobe ov519_decomp


It seemed to work as I'm now able to modprobe the two modules I need:
```
mike@krusty:~$ sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
mike@krusty:~$ sudo insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko

```

Unfortunately I can't run xawtv:
```
mike@krusty:~$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-8-generic)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  65
  Current serial number in output stream:  65

```

I'm fairly certain that's because the camera is not being ported to /dev/video0.  I get errors in the syslog when I plug it in:
```
[ 3497.572000] usb 1-2: new full speed USB device using ohci_hcd and address 9
[ 3497.784000] usb 1-2: configuration #1 chosen from 1 choice
[ 3497.788000] /home/mike/ov51x-jpeg-0.5.4/ov51x.c: USB OV519 video device found
[ 3497.924000] kobject_add failed for ov51x with -EEXIST, don't try to register things with the same name in the same directory.
[ 3497.924000]  [<c01ec869>] kobject_add+0x119/0x1a0
[ 3497.924000]  [<c01ec9d1>] kobject_register+0x21/0x50
[ 3497.924000]  [<c02554fe>] bus_add_driver+0x6e/0x1a0
[ 3497.924000]  [<f88826fb>] usb_register_driver+0x7b/0x100 [usbcore]
[ 3497.924000]  [<f8a5d012>] usb_ov511_init+0x12/0x37 [ov51x_jpeg]
[ 3497.924000]  [<c0143ded>] sys_init_module+0x15d/0x1ba0
[ 3497.924000]  [<c0107a3d>] sys_mmap2+0xcd/0xd0
[ 3497.924000]  [<c01031d0>] sysenter_past_esp+0x69/0xa9
[ 3497.924000]  =======================
[ 3497.924000] usbcore: error -17 registering interface         driver ov51x
[ 3498.248000] /home/mike/ov51x-jpeg-0.5.4/ov51x.c: Sensor is an OV7648
[ 3498.556000] /home/mike/ov51x-jpeg-0.5.4/ov51x.c: Device at usb-0000:00:02.0-2 registered to minor 0
[ 3498.736000] kobject_add failed for ov51x with -EEXIST, don't try to register things with the same name in the same directory.
[ 3498.736000]  [<c01ec869>] kobject_add+0x119/0x1a0
[ 3498.736000]  [<c01ec9d1>] kobject_register+0x21/0x50
[ 3498.736000]  [<c02554fe>] bus_add_driver+0x6e/0x1a0
[ 3498.736000]  [<f88826fb>] usb_register_driver+0x7b/0x100 [usbcore]
[ 3498.736000]  [<f8a5d012>] usb_ov511_init+0x12/0x37 [ov51x_jpeg]
[ 3498.736000]  [<c0143ded>] sys_init_module+0x15d/0x1ba0
[ 3498.736000]  [<c0107a3d>] sys_mmap2+0xcd/0xd0
[ 3498.736000]  [<c01031d0>] sysenter_past_esp+0x69/0xa9
[ 3498.736000]  =======================
[ 3498.736000] usbcore: error -17 registering interface         driver ov51x
[ 3499.072000] kobject_add failed for ov51x with -EEXIST, don't try to register things with the same name in the same directory.
[ 3499.072000]  [<c01ec869>] kobject_add+0x119/0x1a0
[ 3499.072000]  [<c01ec9d1>] kobject_register+0x21/0x50
[ 3499.072000]  [<c02554fe>] bus_add_driver+0x6e/0x1a0
[ 3499.072000]  [<f88826fb>] usb_register_driver+0x7b/0x100 [usbcore]
[ 3499.072000]  [<f8a5d012>] usb_ov511_init+0x12/0x37 [ov51x_jpeg]
[ 3499.072000]  [<c0143ded>] sys_init_module+0x15d/0x1ba0
[ 3499.072000]  [<c0107a3d>] sys_mmap2+0xcd/0xd0
[ 3499.072000]  [<c01031d0>] sysenter_past_esp+0x69/0xa9
[ 3499.072000]  =======================
[ 3499.072000] usbcore: error -17 registering interface         driver ov51x
[ 3949.692000] usb 1-2: USB disconnect, address 9
[ 4070.004000] /home/mike/ov51x-jpeg-0.5.4/ov519_decomp.c: deregistered
[ 4083.892000] usbcore: deregistering interface driver ov51x
[ 4083.892000] /home/mike/ov51x-jpeg-0.5.4/ov51x.c: driver deregistered
[ 4122.580000] usbcore: registered new interface driver ov51x
[ 4122.584000] /home/mike/ov51x-jpeg-0.5.4/ov51x.c: v1.65-1.11-mark : ov51x USB Camera Driver
[ 4129.836000] /home/mike/ov51x-jpeg-0.5.4/ov519_decomp.c: v1.4 : OV519 JPEG Decompression Module
[ 4142.312000] usb 1-2: new full speed USB device using ohci_hcd and address 10
[ 4142.520000] usb 1-2: configuration #1 chosen from 1 choice
[ 4142.520000] /home/mike/ov51x-jpeg-0.5.4/ov51x.c: USB OV519 video device found
[ 4142.688000] kobject_add failed for ov51x with -EEXIST, don't try to register things with the same name in the same directory.
[ 4142.688000]  [<c01ec869>] kobject_add+0x119/0x1a0
[ 4142.688000]  [<c01ec9d1>] kobject_register+0x21/0x50
[ 4142.688000]  [<c02554fe>] bus_add_driver+0x6e/0x1a0
[ 4142.688000]  [<f88826fb>] usb_register_driver+0x7b/0x100 [usbcore]
[ 4142.688000]  [<f8a5d012>] usb_ov511_init+0x12/0x37 [ov51x_jpeg]
[ 4142.688000]  [<c0143ded>] sys_init_module+0x15d/0x1ba0
[ 4142.688000]  [<c0107a3d>] sys_mmap2+0xcd/0xd0
[ 4142.688000]  [<c01031d0>] sysenter_past_esp+0x69/0xa9
[ 4142.688000]  =======================
[ 4142.688000] usbcore: error -17 registering interface         driver ov51x
[ 4142.980000] /home/mike/ov51x-jpeg-0.5.4/ov51x.c: Sensor is an OV7648
[ 4143.288000] /home/mike/ov51x-jpeg-0.5.4/ov51x.c: Device at usb-0000:00:02.0-2 registered to minor 0
[ 4143.492000] kobject_add failed for ov51x with -EEXIST, don't try to register things with the same name in the same directory.
[ 4143.492000]  [<c01ec869>] kobject_add+0x119/0x1a0
[ 4143.492000]  [<c01ec9d1>] kobject_register+0x21/0x50
[ 4143.492000]  [<c02554fe>] bus_add_driver+0x6e/0x1a0
[ 4143.492000]  [<f88826fb>] usb_register_driver+0x7b/0x100 [usbcore]
[ 4143.492000]  [<f8a5d012>] usb_ov511_init+0x12/0x37 [ov51x_jpeg]
[ 4143.492000]  [<c0143ded>] sys_init_module+0x15d/0x1ba0
[ 4143.492000]  [<c0107a3d>] sys_mmap2+0xcd/0xd0
[ 4143.492000]  [<c01031d0>] sysenter_past_esp+0x69/0xa9
[ 4143.492000]  =======================
[ 4143.492000] usbcore: error -17 registering interface         driver ov51x
[ 4143.744000] kobject_add failed for ov51x with -EEXIST, don't try to register things with the same name in the same directory.
[ 4143.744000]  [<c01ec869>] kobject_add+0x119/0x1a0
[ 4143.744000]  [<c01ec9d1>] kobject_register+0x21/0x50
[ 4143.744000]  [<c02554fe>] bus_add_driver+0x6e/0x1a0
[ 4143.744000]  [<f88826fb>] usb_register_driver+0x7b/0x100 [usbcore]
[ 4143.744000]  [<f8a5d012>] usb_ov511_init+0x12/0x37 [ov51x_jpeg]
[ 4143.744000]  [<c0143ded>] sys_init_module+0x15d/0x1ba0
[ 4143.744000]  [<c0107a3d>] sys_mmap2+0xcd/0xd0
[ 4143.744000]  [<c01031d0>] sysenter_past_esp+0x69/0xa9
[ 4143.744000]  =======================
[ 4143.744000] usbcore: error -17 registering interface         driver ov51x
[ 4476.952000] usb 1-2: USB disconnect, address 10
[ 4481.568000] usb 1-2: new full speed USB device using ohci_hcd and address 11
[ 4481.772000] usb 1-2: configuration #1 chosen from 1 choice
[ 4481.776000] /home/mike/ov51x-jpeg-0.5.4/ov51x.c: USB OV519 video device found
[ 4481.892000] kobject_add failed for ov51x with -EEXIST, don't try to register things with the same name in the same directory.
[ 4481.892000]  [<c01ec869>] kobject_add+0x119/0x1a0
[ 4481.892000]  [<c01ec9d1>] kobject_register+0x21/0x50
[ 4481.892000]  [<c02554fe>] bus_add_driver+0x6e/0x1a0
[ 4481.892000]  [<f88826fb>] usb_register_driver+0x7b/0x100 [usbcore]
[ 4481.892000]  [<f8a5d012>] usb_ov511_init+0x12/0x37 [ov51x_jpeg]
[ 4481.892000]  [<c0143ded>] sys_init_module+0x15d/0x1ba0
[ 4481.896000]  [<c0107a3d>] sys_mmap2+0xcd/0xd0
[ 4481.896000]  [<c01031d0>] sysenter_past_esp+0x69/0xa9
[ 4481.896000]  =======================
[ 4481.896000] usbcore: error -17 registering interface         driver ov51x
[ 4482.236000] /home/mike/ov51x-jpeg-0.5.4/ov51x.c: Sensor is an OV7648
[ 4482.544000] /home/mike/ov51x-jpeg-0.5.4/ov51x.c: Device at usb-0000:00:02.0-2 registered to minor 0
[ 4482.672000] kobject_add failed for ov51x with -EEXIST, don't try to register things with the same name in the same directory.
[ 4482.672000]  [<c01ec869>] kobject_add+0x119/0x1a0
[ 4482.672000]  [<c01ec9d1>] kobject_register+0x21/0x50
[ 4482.672000]  [<c02554fe>] bus_add_driver+0x6e/0x1a0
[ 4482.672000]  [<f88826fb>] usb_register_driver+0x7b/0x100 [usbcore]
[ 4482.672000]  [<f8a5d012>] usb_ov511_init+0x12/0x37 [ov51x_jpeg]
[ 4482.672000]  [<c0143ded>] sys_init_module+0x15d/0x1ba0
[ 4482.676000]  [<c0107a3d>] sys_mmap2+0xcd/0xd0
[ 4482.676000]  [<c01031d0>] sysenter_past_esp+0x69/0xa9
[ 4482.676000]  =======================
[ 4482.676000] usbcore: error -17 registering interface         driver ov51x
[ 4483.112000] kobject_add failed for ov51x with -EEXIST, don't try to register things with the same name in the same directory.
[ 4483.112000]  [<c01ec869>] kobject_add+0x119/0x1a0
[ 4483.112000]  [<c01ec9d1>] kobject_register+0x21/0x50
[ 4483.112000]  [<c02554fe>] bus_add_driver+0x6e/0x1a0
[ 4483.112000]  [<f88826fb>] usb_register_driver+0x7b/0x100 [usbcore]
[ 4483.112000]  [<f8a5d012>] usb_ov511_init+0x12/0x37 [ov51x_jpeg]
[ 4483.112000]  [<c0143ded>] sys_init_module+0x15d/0x1ba0
[ 4483.112000]  [<c0107a3d>] sys_mmap2+0xcd/0xd0
[ 4483.112000]  [<c01031d0>] sysenter_past_esp+0x69/0xa9
[ 4483.112000]  =======================
[ 4483.112000] usbcore: error -17 registering interface         driver ov51x

```

Anyone have any ideas?

---

### Post by freefrags on 2007-02-22
Hi 
i tried this tutorial for my trust spacecam 320 however when i got to 
sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko 
i got an error msg which said:
insmod: error inserting '/lib/modules/2.6.20-8-generic/extra/ov519_decomp.ko': -1 Unknown symbol in module

i cant seem to get this working i hope you can help me out 

Raymond


> **gentle_turtle said:**
> It toook me quite a while to figure this one out, so I post how I did it: I also do not seem to be able to open up a new thread for this (partially new) HowTo, so I post here. The info I collected stems from this thread and from [http://blog.thedarkmere.net/index.php?/archives/14-Ubuntu-ov51x-jpeg-guide.html](http://blog.thedarkmere.net/index.php?/archives/14-Ubuntu-ov51x-jpeg-guide.html). I had to modify the latter end steps though to make it work properly.

The preliminaries: My machine is an IBM Netvista PC (PIII 1Gig), Ubuntu 6.06 Dapper, server installation with additional XUbuntu interface addon.

The Hercules Classic Webcam is an el-chepo webcam incorporating 4LEDs for low lighting usage. "lsusb" sees the camera as "Omnivision Technologies, Inc". The drivers needed to make it work are the ov51x and ov519_decomp modules.

I assume in this description that your camera is seen on the USB bus, otherwise yuo have to activate and make sure that USB works properly by activating the bus. You can find in this site enough descriptions on how to do that..

Once the cam is seen on the USB bus, the following procedure gives you a fuly functional cam on your Ubuntu 6.06 dapper machine:

1. Get the linux headers for your system, so that you can compile the drivers once you downloaded them. To do this, open a terminal window (Applications -> Terminal on XUbuntu) and type

sudo apt-get install build-essential linux-headers-`uname -r`

2. Get the modules for your webcam: 

wget [http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-0.5.4.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-0.5.4.tar.gz)

Ensure the drivers landed into a directory you know ;-)

3. Move to the directory where your downloaded drivers are, and extract the source files from the tar files.

tar -xvf ov51x-jpeg-0.5.4.tar.gz

4. Change directory to where your sources are:

cd ov51x-jpeg-0.5.4

5. Compile and install the modules:

sudo make install

This will compile the  drivers and install them into the subdirectory of /lib/modules/your-linux-version called extra

6. If all went well, we can install the modules by hand now:

sudo modprobe videodev
sudo modprobe i2c_core
sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
sudo insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko

7. test your installation by using a camera viewing application, such as xawtv.

If all goes well, you will be able to see the output of your webcam in xawtv.

Now comes the tricky part: making such modules permanent, so that your machine recognizes the Hercules webcam both at bootup as well when you plug it in. The problem here with respect to other module installations is that for some obscure reason, the ov519_decomp module insists in loading the ov511 module when loading through modprobe, and ov511 knows nothing of some of the functions in ov519_decomp and therefore complains. 

We will thus load ov51x normally through modprobe, but we will load ov519_decomp through insmod. Let us look at the steps to do this:

1. Make sure you load the vidoedev and i2c_core modules at bootup: to do this, in the terminal type:

sudo vi /etc/modules

We use here vi, but you can actually substitute vi with any other text editor of your preference (I know, I am old and I used vi for decades ;-P). At the end of the files, add the following two lines:

videodev
i2c_core

Now save the file and quit the editor. This will guarantee that from now on at bootup the videodev and the i2c_core modules are loaded.

2. Tell Ubuntu what to do whenever it notices the camera is plugged in:

sudo touch /etc/modprobe.d/ov51x
sudo vi /etc/modprobe.d/ov51x

add to the file the following line: 

install ov51x /sbin/modprobe --ignore-install ov51x; insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko

This has to be ONLY on one line.
Save the file and quit the editor.

And voila, at next rebbot your Hercules Classic webcam is there, ready to use.... Have fun!

---

### Post by DownshiftEVA on 2007-03-05
I'm experiencing the same xawtv error as barney_1. Does anybody have an idea of what the problem is?

---

### Post by jtreach on 2007-03-30
This guide needs to be updated as the following code is now out of date:
```
wget http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-0.5.4.tar.gz
```

It should be ```
wget http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz
```

As this package has been updated and anyone entering the original gets a 404 error message.

---

### Post by Josh1 on 2007-03-31
> **jtreach said:**
> This guide needs to be updated as the following code is now out of date:
```
wget http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-0.5.4.tar.gz
```

It should be ```
wget http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz
```

As this package has been updated and anyone entering the original gets a 404 error message.

Good idea. :).

---

### Post by jtreach on 2007-03-31
Sorry should've mentioned it but didn't realise until I finished the last post but there are some other lines of code that need updating in the same way.

Thanks for the guide btw I got my eyetoy working! :)

---

### Post by Mikiupdown2 on 2007-04-04
Hello, I have been following this tutorial but when I get to:
```

sudo apt-get install build-essential linux-headers-`uname -r`

```

My terminal just says: ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-uname -r
```

What could I be doing wrong? I'm sorry if this is a silly question, but I started using Ubuntu (properly) just 3 days ago.

I am using Ubuntu 6.10.

Thank you all in advance,
From Michael.

---

### Post by Arlanthir on 2007-04-10
Is this for eyetoy silver too?
EDIT: Yes it is =X
Had to run xawtv with -nodga, though :P

---

### Post by xpod on 2007-04-12
Thanks for the guide....

Just set it up on my girls machne and it all works great:D 
Had a couple of minor issues but somehow it still works so i`m not complaining.

Good stuff!!

---

### Post by nitewing98 on 2007-04-26
Hoping someone here can help.  I've got an Argus PC300 cam that also uses the Omnivision chipset.  When I bring up camorama, I get a flickering black and white square, no real picture.  It's obvious that it's getting SOMETHING, though.

I went through the instructions in this thread, but when I enter:
> sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
I get:
> insmod: error inserting '/lib/modules/2.6.20-15-386/extra/ov51x.ko': -1 Operation not permitted

Similarly, when I enter:
> sudo insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko
I get:
> insmod: error inserting '/lib/modules/2.6.20-15-386/extra/ov519_decomp.ko': -1 Unknown symbol in module

I'm using Feisty, and DID remember to remove the #includes from the .c files (as mentioned in the earlier post).

dmesg says this:
> [   66.652753] Linux video capture interface: v2.00
[   66.873511] /home/Shared/Installers/ov51x-jpeg-1.0.0/ov51x-jpeg-core.c: USB OV518+ video device found
[   66.876480] /home/Shared/Installers/ov51x-jpeg-1.0.0/ov51x-jpeg-core.c: Device revision 2
[   66.912468] /home/Shared/Installers/ov51x-jpeg-1.0.0/ov51x-jpeg-core.c: Compression required with OV518...enabling


Anyone got a clue?

---

### Post by ghandi2 on 2007-04-30
I have the Namai version of the Eyetoy and when I tried your howto after d/l'ing a different build of the ov51x I got from here:
[URL="http://alpha.dyndns.org/ov511/download.html#ov51x"]

http://alpha.dyndns.org/ov511/download.html#ov51x[/URL]

I tried to run the following out of the directory I extracted the package to and got the following output in terminal.  Any suggestions?

sudo make install
make -C /lib/modules/2.6.17-11-generic/build M=/home/ghandi2/Eyetoy modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /home/ghandi2/Eyetoy/ov51x.o
/home/ghandi2/Eyetoy/ov51x.c:207: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:209: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:211: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:213: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:216: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:220: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:223: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:227: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:229: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:231: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:234: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:236: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:239: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:242: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:244: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:246: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:248: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:250: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:252: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:254: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:256: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:258: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:260: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:262: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:264: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:267: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:270: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:272: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:274: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:276: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:278: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:280: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:282: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:285: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:288: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:290: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:292: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:294: error: expected ‘)’ before string constant
/home/ghandi2/Eyetoy/ov51x.c:8464: error: unknown field ‘owner’ specified in initializer
/home/ghandi2/Eyetoy/ov51x.c:8464: warning: initialization from incompatible pointer type
make[2]: *** [/home/ghandi2/Eyetoy/ov51x.o] Error 1
make[1]: *** [_module_/home/ghandi2/Eyetoy] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [all] Error 2

---

### Post by williamts99 on 2007-05-07
Yes, this might want to be updated for 
[http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.0.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.0.tar.gz)

---

### Post by k3v1nf on 2007-05-30
i using ubuntu Feisty Fawn

i did that
sudo apt-get install build-essential linux-headers-`uname -r`

wget [http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-)[COLOR="Blue"]1.5.1[/COLOR].tar.gz

tar -xvf ov51x-jpeg-[COLOR="Blue"]1.5.1[/COLOR].tar.gz

cd ov51x-jpeg-[COLOR="Blue"]1.5.1[/COLOR]

sudo make install
sudo modprobe videodev
sudo modprobe i2c_core

and when i put that line  sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko

its tell me that 
kevin@kevin-desktop:~/ov51x-jpeg-1.5.1$ sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
insmod: can't read '/lib/modules/2.6.20-16-generic/extra/ov51x.ko': No such file or directory
kevin@kevin-desktop:~/ov51x-jpeg-1.5.1$ sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
insmod: can't read '/lib/modules/2.6.20-16-generic/extra/ov51x.ko': No such file or directory

what can i do? 
srry for mi english

---

### Post by patsfan on 2007-06-06
i know im stupid but what is uname -r mean?

---

### Post by Chris Sharman on 2007-06-09
The rastageeks website has changed - the ov51x-jpeg download has moved/changed.
I used the 1.5.1 version.
The tar & cd commands following need changing appropriately - they don't refer to the version just wget'ed anyway.
I changed the insmod commands too:
$ ls /lib/modules/2.6.17-11-386/extra/
ov51x-jpeg.ko
$ sudo insmod /lib/modules/`uname -r`/extra/ov51x-jpeg.ko

Camorama gives me a working camera, with 3 images replicated horizontally.
The red light wasn't lit to show the camera was on.
Kopete hangs - I stopped it, but now nothing can see the camera.

This is on Edgy Eft 
Any help appreciated - rebooting now to hopefully recover camera access.

Thanks
Chris

---

### Post by Chris Sharman on 2007-06-09
to patsfan: `uname -r` often embedded in another command surrounded by back ticks (as here), returns your kernel version number - so you can reference the right stuff for your kernel.
to k3v1nf: try "ls /lib/modules/`uname -r`/extra/" - this will probably show you ov51x-jpeg.ko
"sudo insmod" that/those, rather than the ones in the instructions.

kopete & xawtv still hang for me, and camorama still shows me 3 elongated images, side by side. If I take a snapshot I get 6, slightly ghosted - cropped & quality reduced copy attached, but it was originally 640*480, with the bottom 160 or so rows black

I tried this version: [http://ovcam.org/ov511/download/ov51x/ov51x-1.65-1.12-mark.tar.bz2](http://ovcam.org/ov511/download/ov51x/ov51x-1.65-1.12-mark.tar.bz2)
as ghandi2 - I get similar errors - googling suggested replacing MODULE_PARM(whatever, "i") with module_param(whatever, int, 0) for my kernel (2.6.17), which compiles clean, apart from ov51x.c:282:MODULE_PARM(unit_video, "1-" __MODULE_STRING(OV511_MAX_UNIT_VIDEO) "i");
which is a little different, and I don't know how to replace.

Help please!!
Chris

---

### Post by coombera on 2007-06-15
Hi Folks,

I just managed to successfully install the driver from 
[http://www.rastageeks.org/downloads/ov51x-jpeg/](http://www.rastageeks.org/downloads/ov51x-jpeg/)
It works for my EyeToy camera on xawtv and amsn with Edgy Eft.

I found that the step 

```
sudo insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko
```

is no longer required with the current version: ov51x-jpeg-1.5.1

Everything else in:

```
sudo make install
sudo modprobe videodev
sudo modprobe i2c_core
sudo insmod /lib/modules/`uname -r`/extra/ov51x-jpeg.ko
```

is correct.

HTH

Andy

---

### Post by patsfan on 2007-06-17
ive tried everything artoolkit wont install could you give me a step by step instuctin

---

### Post by Gordan on 2007-07-05
> **Chris Sharman said:**
> 
Help please!!
Chris

This is the same output that i get from camorama on fiesty with my Eye Toy cam and ov51x-jpeg-1.5.1 [i refer to your atached picture].

---

### Post by Offoffoff on 2007-07-14
I found out in repositorium ov511-source... Did Anyone try this?

---

### Post by Hugolp on 2007-07-25
> **Offoffoff said:**
> I found out in repositorium ov511-source... Did Anyone try this?

That is the old module. Wont work right now.

The funny thing is that I got my Hercules webcam in the other computer that is running feisty as well, but cant get it working on this one. I cant remember what I did exactly in the other one.

---

### Post by dwdude on 2007-07-29
I'm on Feisty Fawn. Just thought I'd let you all know ;)

Alright, here are the steps I used:

1. I went here, downloaded the files
[http://www.rastageeks.org/downloads/ov51x-jpeg/](http://www.rastageeks.org/downloads/ov51x-jpeg/)
(If that link doesn't work, then you might have to change the next few commands according to their file names)

2. I saved them to my home directory (/home/david in my case)

3. I opened the terminal, then typed these commands (do them one line at a time):

```
tar -xvf home/david/ovx51-jpeg-1.5.2.tar.gz
cd ~/ovx51-jpeg-1.5.2

```

4. Then typed these commands (one line at a time!):

```

sudo make install
sudo modprobe videodev
sudo modprobe i2c_core
sudo insmod /lib/modules/`uname -r`/extra/ov51x-jpeg.ko

```


But the thing is, when I try using the cam, I get a bright green screen, sometimes with a light green rectangle flashing... Here's a photo:

[http://img340.imageshack.us/img340/6493/webcamlc2.jpg](http://img340.imageshack.us/img340/6493/webcamlc2.jpg)

[B]EDIT: Fixed green screen problem. I restarted my computer and then It worked fine.
Heres a link I saw that helped:
[http://www.hitlabnz.org/forum/showthread.php?t=373](http://www.hitlabnz.org/forum/showthread.php?t=373)
It also might help people using ARToolkit with their eyetoy webcam.[/B]

**EDIT: Got the video working and the sound by using VLC!**

Step by step Instructions:

1. Open VLC (of course...)

2. Click "File"

3. From the File menu, click "Open Capture Device..."

4. Configure the boxes according to your preferences:

4a. To make video working:
In the box named "Video device name" change it from "/dev/video" to "dev/video0"

4b. To make sound work:
In the box named "Audio device name" change it from "dev/dsp" to "/dev/dsp1"

4c. To make both work:
Change both boxes (see 4a and 4b)

5. Click "Ok" at the bottom and it should be working!

---

### Post by potrick on 2007-08-23
I don't understand...how did you fix the greenscreen? I tired restarting several times...no dice.

---

### Post by Halfling Rogue on 2007-12-12
```
sudo insmod /lib/modules/`uname -r`/extra/ov51x-jpeg.ko
insmod: error inserting '/lib/modules/2.6.22-14-generic/extra/ov51x-jpeg.ko': -1 Unknown symbol in module
```

Guhbuh? Which symbol is this?

---

### Post by Halfling Rogue on 2007-12-12
Never mind! Went back to an older version and it worked fine.

---

### Post by adrianmak on 2007-12-12
Ive a fairly old qucikcam ( I guess it is  logitech ) but no software can drive this cam.
the usb id is 046d:1133

---

### Post by afallenhope on 2008-06-20
I also got the whole "Unknown Symbol"... I've tried everything to appending escape chars to the module and everything. Still didn't work. So I went to rasta geek's website and followed the module assistant method. It goes like this:

```

sudo apt-get update
sudo apt-get install ov51x-jpeg-source module-assistant
sudo module-assistant -t a-i ov51x-jpeg 

```

Or you could try my method.
```
wget http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.7.tar.gz
tar xvf ov51x-jpeg-1.5.7.tar.gz
sudo make install
sudo modprobe videodev
sudo modprobe i2c-core
sudo insmod /lib/modules/`uname -r`/extra/ov51x-jpeg.ko

```

That should work.. if worse comes to worse type: 
```
sudo modprobe ov51x-jpeg
```

best of luck.
--Pierre

---

### Post by Zantaskan on 2008-07-16
Hello, I am pretty new to Linux, very very new to bash and terminal lol

I tried your steps, but I get to the part about downloading from the site, and I get a 404 not found error

heres what I get in terminal

matthew@matthew-desktop:~$ sudo apt-get install build-essential linux-headers-'matthew-r'
[sudo] password for matthew:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
E: Couldn't find package linux-headers-matthew-r
matthew@matthew-desktop:~$ wget [http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz)
--14:53:26--  [http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz)
           => `ov51x-jpeg-1.0.0.tar.gz'
Resolving [www.rastageeks.org](www.rastageeks.org)... 88.191.17.132
Connecting to [www.rastageeks.org|88.191.17.132|:80](www.rastageeks.org|88.191.17.132|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
14:53:27 ERROR 404: Not Found.


Any help please :)

---

### Post by Chris Sharman on 2008-07-17
> **Zantaskan said:**
> Hello, I am pretty new to Linux, very very new to bash and terminal lol

I tried your steps, but I get to the part about downloading from the site, and I get a 404 not found error

heres what I get in terminal

matthew@matthew-desktop:~$ sudo apt-get install build-essential linux-headers-'matthew-r'
[sudo] password for matthew:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
E: Couldn't find package linux-headers-matthew-r

That should be `uname -r` not 'matthew-r'
uname -r is a command which gives back your kernel version, and the backticks (or grave quotes, not single quotes) get it executed & replaced in the command.

> **Zantaskan said:**
> matthew@matthew-desktop:~$ wget [http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz)
--14:53:26--  [http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz)
           => `ov51x-jpeg-1.0.0.tar.gz'
Resolving [www.rastageeks.org](www.rastageeks.org)... 88.191.17.132
Connecting to [www.rastageeks.org|88.191.17.132|:80](www.rastageeks.org|88.191.17.132|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
14:53:27 ERROR 404: Not Found.

It's moved on a few versions.
Look at the folder to see what is there:
[http://www.rastageeks.org/downloads/ov51x-jpeg/](http://www.rastageeks.org/downloads/ov51x-jpeg/)
The current version is now:
[http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.8.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.8.tar.gz)

Chris

---

### Post by syndr0 on 2008-08-01
thats awesome. anywhoooo.... yeah... i cant get mine to work on aim.com ... you know the flash chat... idk why.. that and hmmm.. ill post if i have anymore problems...you think theyd put these drivers in the module so we dont have to reput them in every upgrade...??? .. sorry,, im a n00bie to this linux stuff but its amazing and i love all the support

---

### Post by HangukMiguk on 2008-08-15
To rehash this, mine worked fine until a reboot, now it "works" except that it gives me nothing but neon colors when viewed.

Any ideas?

---

### Post by Animeniac on 2008-08-16
> **HangukMiguk said:**
> To rehash this, mine worked fine until a reboot, now it "works" except that it gives me nothing but neon colors when viewed.

Any ideas?

The same happens to me, I'm afraid.

---

### Post by eversor88 on 2008-08-19
ok so i m new to ubuntu and its pretty sweet, and i installed this webcam when i had windows no problem. When i go trough the installation  i get this error 

> 
alexander@A-top:~/ov51x-jpeg-1.5.8$ sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
insmod: can't read '/lib/modules/2.6.24-19-generic/extra/ov51x.ko': No such file or directory
         
how do i solve this

---

### Post by Animeniac on 2008-08-20
> **HangukMiguk said:**
> To rehash this, mine worked fine until a reboot, now it "works" except that it gives me nothing but neon colors when viewed.

Any ideas?

Go to *System --> Administration --> Hardware Drivers*

Disable "ov51x USB Camera Driver, and then restart the computer if it says "Requires system restart".

Go back to Hardware Drivers and enable "ov51x USB Camera Driver" and go back to XawTV to see if it worked.

If it didn't work for you, Go to *System --> Administration --> Synaptic Package Manager* and search "ov51x" and install the "ov51x-jpeg-source" package, and then disable "ov51x USB Camera Driver" (and restart the computer if required) and enable it again. At least that's what I did...

---

### Post by ivia77 on 2008-09-07
> **eversor88 said:**
> ok so i m new to ubuntu and its pretty sweet, and i installed this webcam when i had windows no problem. When i go trough the installation  i get this error 


how do i solve this

i had the same error, this worked for me

```
sudo modprobe ov51x-jpeg
```

---

### Post by kyleskimskate on 2008-10-18
OK, so when I do the second code in the guide-the rastageeks one- i put that into the terminal and it comes up with a 404 message. I went to the site and it doesn't exist anymore! What should I do!:confused:

---

### Post by PhoenixP3K on 2008-10-24
The package gets updated all the time. Got to [http://www.rastageeks.org/downloads/ov51x-jpeg/](http://www.rastageeks.org/downloads/ov51x-jpeg/) to see what is the latest version.
Currently it's: [http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.9.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.9.tar.gz)

---

### Post by jvincent08 on 2008-10-29
Ok, I've compiled and installed v1.5.9 and everything went well, but the video coming from the camera is purple and green..

Any ideas?

---

### Post by findingmemo on 2008-10-31
hello, I have a problem and this topic more like it. I have ubuntu 8.10 relaised on my laptop. ( MSI vr330, its my laptop) I m new on ubuntu. so I have harddrivers problem that I cant set up my web cam. how I can set up it? I didnt find a way for setup driver online. its Piranha web camera and model is pc 4000 4.0 Megapixel. 
Cant I set up it? becoz I searched a way on net but there is drivers for Windows. what can I do? 
thanx... 
(Mehmet Demirkeser From Turkey)

---

### Post by jvincent08 on 2008-10-31
> **findingmemo said:**
> hello, I have a problem and this topic more like it. I have ubuntu 8.10 relaised on my laptop. ( MSI vr330, its my laptop) I m new on ubuntu. so I have harddrivers problem that I cant set up my web cam. how I can set up it? I didnt find a way for setup driver online. its Piranha web camera and model is pc 4000 4.0 Megapixel. 
Cant I set up it? becoz I searched a way on net but there is drivers for Windows. what can I do? 
thanx... 
(Mehmet Demirkeser From Turkey)

[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=vzy&q=piranha+pc+4000+linux+webcam+drivers&btnG=Search](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=vzy&q=piranha+pc+4000+linux+webcam+drivers&btnG=Search)

The results are in a foreign language (presumably Turkish), so I can't direct you to anywhere specific, but maybe you'll find a solution after looking around some.

---

### Post by findingmemo on 2008-10-31
yea, I tried so searching in Turkish too. But there isnt a solution for Piranha for Ubuntu. Windows is ok but Linux not available. I want to use my web cam with pidgin mesanger on ubuntu. can it be possible??
thanks for in intrested my problem...

---

### Post by jvincent08 on 2008-10-31
> **findingmemo said:**
> yea, I tried so searching in Turkish too. But there isnt a solution for Piranha for Ubuntu. Windows is ok but Linux not available. I want to use my web cam with pidgin mesanger on ubuntu. can it be possible??
thanks for in intrested my problem...

Even if you find drivers for your webcam, Pidgin does not have video support. There are many other options, though, such as video conferencing applications like Skype, or even setting up a webcam server that people can connect to using their web browser.

---

### Post by Lichig0 on 2008-11-09
I'm pretty sure everything installed fine, but Ubuntu (I'm using 8.10 - Intrepid Ibex) doesn't see the Eye Toy or something. When I type dmesg I get

"[ 1076.260078] hub 1-0:1.0: unable to enumerate USB device on port 3"

How would I get it to be recognized?

---

### Post by Lichig0 on 2008-11-09
Anyone? Please!

---

### Post by trodden on 2008-11-11
> **jvincent08 said:**
> Ok, I've compiled and installed v1.5.9 and everything went well, but the video coming from the camera is purple and green..

Any ideas?

I have the same problem.

---

### Post by Jose Catre-Vandis on 2008-12-21
Been fighting to get a cam working on my box for the last couple of years. I have gspca installed. inserted eyetoy, recognised by Xubuntu. Dmesg gives me this:
```
[18319.520020] usb 2-2: new full speed USB device using ohci_hcd and address 2
[18319.737198] usb 2-2: configuration #1 chosen from 1 choice
[18320.082065] gspca: main v2.2.0 registered
[18320.086496] gspca: probing 054c:0155
[18320.322999] ov519: I2C synced in 1 attempt(s)
[18320.323004] ov519: starting OV7xx0 configuration
[18320.358996] ov519: Sensor is an OV7648
[18320.396699] gspca: probe ok
[18320.396740] gspca: probing 054c:0155
[18320.412769] usbcore: registered new interface driver ov519
[18320.412775] ov519: registered
[18320.417192] usbcore: registered new interface driver snd-usb-audio
```

and eyetoy worked immediately in Cheese and gstreamer-properties.

It also half works in Skype, but I get thick pink & grey horizontal lines across the picture. Still, it's progress! [EDIT] this appears to be a resolution issue, because if I set the output resolution to 320x240 in cheese I get the same pink and green lines. Works for video chat, but my caller gets the lines at their end too.

---

### Post by dorkdork777 on 2008-12-23
I have (almost) the same problem. 64-bit Ubuntu 8.10, works perfect on Cheese at 640x480 but I get the same lines at 320z240. Doesn't work at all in Skype though; before I'd just get funky multicoloured static, now Skype just crashes with this:

```
Skype V4L2: Failed to change capture framerate (15)
Aborted
```

So Skype is a no-go. Damn. :(

Ah well, I've got another cam hanging round that works fine in Skype and not Cheese. Perfect partners :P

---

### Post by Mitchell_ on 2009-01-03
Stuck on step 1. I went System>Administration But I cant find device manager.
Whats wrong

Please help
Mitchell

---

### Post by Jose Catre-Vandis on 2009-01-03
> **Mitchell_ said:**
> Stuck on step 1. I went System>Administration But I cant find device manager.
Whats wrong

Please help
Mitchell

Just open up a terminal and type:
```
lsusb
```
depending on the usb devices you have plugged in, thi should look something like this:
```
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 054c:0155 Sony Corp.  <-<-<---- 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
the second entry being the eyetoy (I put in the arrows!)

This done, you should be good to go on

---

### Post by Kasami on 2009-01-19
Hello, I've been trying to get my eyetoy working for the last hour or so. But it worked last night when I installed the driver and then when I started up this morning I noticed that cheese could not detect the camera. The computer is picking up the cam (Using the lsusb command in the terminal) and the webcam driver is showing up in my hardware drivers dialogue. 

I'm running Intrepid and this cam worked on my Hardy box before I changed over.

Any ideas would be nice?

---

### Post by gardtek on 2009-01-23
> **Mitchell_ said:**
> Stuck on step 1. I went System>Administration But I cant find device manager.
Whats wrong

Please help
Mitchell

In 8.10, go to Applications -> System Tools -> Device Manager.

gard

---

### Post by Kasami on 2009-01-26
Ok, I found a problem with how it's setup. My Device manager is registering the Eyetoy as a sound device with no video device at all. Is there a way to fix this up?

---

### Post by nanotube on 2009-02-02
> **gardtek said:**
> In 8.10, go to Applications -> System Tools -> Device Manager.

gard

it's not installed by default on a clean install of intrepid. you have to install it with

sudo apt-get install gnome-device-manager

---

### Post by nanotube on 2009-02-02
> **Kasami said:**
> Ok, I found a problem with how it's setup. My Device manager is registering the Eyetoy as a sound device with no video device at all. Is there a way to fix this up?

same here - eyetoy looks like a sound-only device in the device manager. any suggestions would be appreciated.

---

### Post by nanotube on 2009-02-10
anyone? :) *bump*

---

### Post by nanotube on 2009-02-12
found the answer to the problem. first question in the linux driver faq clued me in:
[http://www.rastageeks.org/ov51x-jpeg/index.php/FAQ](http://www.rastageeks.org/ov51x-jpeg/index.php/FAQ)

plugged the cam directly into the usb port rather than into the usb hub, and it started working. :)

---

### Post by wlbragg on 2009-02-26
Using ver ov51x-jpeg-1.5.9 when I get to 

sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko

I get the no such (file or directory) error

and if I try 

sudo modprobe ov51x-jpeg

then I get the (unknown symbol in module error) 

Any ideas on what to do now!?

---

### Post by nanotube on 2009-02-26
> **wlbragg said:**
> Using ver ov51x-jpeg-1.5.9 when I get to 

sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko

I get the no such (file or directory) error

and if I try 

sudo modprobe ov51x-jpeg

then I get the (unknown symbol in module error) 

Any ideas on what to do now!?

well, where did you put ov51x.ko?

---

### Post by wlbragg on 2009-02-26
Where the directions told me to although the directions said
```
sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
```
driver name has changed to
```
sudo insmod /lib/modules/`uname -r`/extra/ov51x-jpeg.ko

```
so I tried
```
sudo insmod /lib/modules/`uname -r`/extra/ov51x-jpeg.ko
```
that gave me the 
```
(unknown symbol in module error)
```
I don't get the "file or directory not found anymore" that was a mistake on my part. 
dmesg
```
[  835.946661] ov51x_jpeg: disagrees about version of symbol video_devdata
[  835.946677] ov51x_jpeg: Unknown symbol video_devdata
[  835.947166] ov51x_jpeg: disagrees about version of symbol video_unregister_device
[  835.947168] ov51x_jpeg: Unknown symbol video_unregister_device
[  835.947353] ov51x_jpeg: disagrees about version of symbol video_device_alloc
[  835.947355] ov51x_jpeg: Unknown symbol video_device_alloc
[  835.947450] ov51x_jpeg: disagrees about version of symbol video_register_device
[  835.947453] ov51x_jpeg: Unknown symbol video_register_device
[  835.947759] ov51x_jpeg: disagrees about version of symbol video_usercopy
[  835.947761] ov51x_jpeg: Unknown symbol video_usercopy
[  835.947844] ov51x_jpeg: disagrees about version of symbol video_device_release
[  835.947847] ov51x_jpeg: Unknown symbol video_device_release
```

---

### Post by wlbragg on 2009-02-26
Also I never saw a reply to what to do if your Eyetoy only shows up in device manager under audio as mine does?
And also what does the video device show up as when done right in /dev/?

---

### Post by nanotube on 2009-02-27
Hi
not sure about what's going on with your "unknown symbol" error...

but about the audio-only: that happened to me when i plugged the webcam into a usb hub - once i plugged it directly into a built in usb port, it worked just fine. 

also i'll note that it works even without the special ov51x-jpeg driver - plugged it into the usb port directly, and it worked with stock drivers that come with the ubuntu 8.10 install... so try it.

---

### Post by CarbineMonoxide on 2009-03-03
Heh. My EyeToy isn't even showing up in the device manager. =/

---

### Post by wlbragg on 2009-03-03
Wish I could help you out but I haven't gotten any farther on mine either. I did find out that it will show one frame every now and then in VLC if I keep hitting connect to capture device over and over using /dev/video0 which is where my device is registering. Sometimes I get just a garbled green screen and sometimes nothing at all. Even though both entries in Device Manager show up as audio and streaming audio. The streaming audio is the video portion. The audio portion is working by default. 
Did you try and make sure you plugged it into a direct usb port and not a hub port? I tried all my ports as I have no clue which if any are hub or direct?

---

### Post by nanotube on 2009-03-04
> **wlbragg said:**
> Wish I could help you out but I haven't gotten any farther on mine either. I did find out that it will show one frame every now and then in VLC if I keep hitting connect to capture device over and over using /dev/video0 which is where my device is registering. Sometimes I get just a garbled green screen and sometimes nothing at all. Even though both entries in Device Manager show up as audio and streaming audio. The streaming audio is the video portion. The audio portion is working by default. 
Did you try and make sure you plugged it into a direct usb port and not a hub port? I tried all my ports as I have no clue which if any are hub or direct?

is it working with cheese? (that's what mine works with well)

---

### Post by tehforum on 2009-03-08
[http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz)

404 error?

I was looking forward to this as well. :(

Edit - I just went straight to the website, I guess it blocks hotlinks.

Okay new problem.

sawan@SawanPC:~/ov51x-jpeg-1.5.8$ xawtv
[: 12: (opcode:: unexpected operator
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-16-generic)
xinerama 0: 1280x1024+0+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  69
  Current serial number in output stream:  69

Any ideas? Thanks!

---

### Post by tehforum on 2009-03-09
Bump.

---

### Post by tehforum on 2009-03-10
[COLOR="White"]Bump.[/COLOR]

---

### Post by wlbragg on 2009-03-12
```
is it working with cheese? (that's what mine works with well)
```

As a matter of fact it does work well in cheese. I just tried it. Any idea why it works in cheese and not VLC or Skype? Also, in Skype, the first time I tried Skype it saw the Eyetoy. It only gave me a green screen but the audio worked. Now after trying many things and suggestions to get the eyetoy working in other apps, Skype no longer sees the Eyetoy, at all, not video or audio. Is there a quick method to put Ubuntu back to it's default configuration? I may have gotten a Skype update in the process too that may have some influence.

---

### Post by nanotube on 2009-03-13
> **wlbragg said:**
> ```
is it working with cheese? (that's what mine works with well)
```

As a matter of fact it does work well in cheese. I just tried it. Any idea why it works in cheese and not VLC or Skype? Also, in Skype, the first time I tried Skype it saw the Eyetoy. It only gave me a green screen but the audio worked. Now after trying many things and suggestions to get the eyetoy working in other apps, Skype no longer sees the Eyetoy, at all, not video or audio. Is there a quick method to put Ubuntu back to it's default configuration? I may have gotten a Skype update in the process too that may have some influence.

well... as it happens, i haven't been able to get mine to work with anything but cheese and xawtv, either. specifically not ekiga, which was what i wanted to do. 

there were some changes from v4l to v4l2 and i think we may have to wait until jaunty so that all the code is updated to use v4l2. 

have you tried the jaunty beta livecd, to see if it works? (i haven't... but if you have the inclination, please try and report your experiences :) ).

---

### Post by notfatrob on 2009-04-03
Im having trouble getting this to work.

when i try to dl the file from rasta geeks, it dosent work :[

---

### Post by Kasami on 2009-04-06
> **notfatrob said:**
> Im having trouble getting this to work.

when i try to dl the file from rasta geeks, it dosent work :[

Yeah, they update the driver every now and again so the one in the original post isn't current. Try this instead:

```
wget http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.9.tar.gz
```

You will then have to adjust the number in the steps in the tutorial accordingly.

---

### Post by Redundant Username on 2009-04-06
[How do I fix this?]("http://i230.photobucket.com/albums/ee123/narutoanime99/Screenshot-3.png")

---

### Post by Kasami on 2009-04-07
> **Redundant Username said:**
> [How do I fix this?]("http://i230.photobucket.com/albums/ee123/narutoanime99/Screenshot-3.png")

Does it flicker like that? I get grey lines through the picture in Cheese like that, it flickers on and off. Don't know how to stop it though.

--EDIT--

I just checked in xawtv, the lines are always there and annoying, is there any reason you have to use xawtv? Cheese works great =]

---

### Post by nanotube on 2009-04-07
> **Redundant Username said:**
> [How do I fix this?]("http://i230.photobucket.com/albums/ee123/narutoanime99/Screenshot-3.png")

try using the full resolution of the cam - i got the same things because xawtv by default uses half-res. ('man xawtv' for info on how to change resolution etc.)

---

### Post by Redundant Username on 2009-04-07
Cheese works great, I just now need to get it to work in vlc.

---

### Post by Captain_Glen on 2009-04-15
I can't get my eye toy to work.

I get this error:
```
glen@glen-desktop:~$ sudo modprobe ov51x-jpeg
FATAL: Error inserting ov51x_jpeg (/lib/modules/2.6.24-19-generic/extra/ov51x-jpeg.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

and when I run dmesg:
```
glen@glen-desktop:~$ dmesg | grep ov
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] Movable zone start PFN for each node
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[   36.955212] cpuidle: using governor ladder
[   36.955213] cpuidle: using governor menu
[   50.704771] ov51x_jpeg: disagrees about version of symbol video_devdata
[   50.704773] ov51x_jpeg: Unknown symbol video_devdata
[   50.704935] ov51x_jpeg: disagrees about version of symbol video_unregister_device
[   50.704936] ov51x_jpeg: Unknown symbol video_unregister_device
[   50.704999] ov51x_jpeg: disagrees about version of symbol video_device_alloc
[   50.705001] ov51x_jpeg: Unknown symbol video_device_alloc
[   50.705030] ov51x_jpeg: disagrees about version of symbol video_register_device
[   50.705032] ov51x_jpeg: Unknown symbol video_register_device
[   50.705130] ov51x_jpeg: disagrees about version of symbol video_usercopy
[   50.705132] ov51x_jpeg: Unknown symbol video_usercopy
[   50.705173] ov51x_jpeg: disagrees about version of symbol video_device_release
[   50.705175] ov51x_jpeg: Unknown symbol video_device_release
[   50.716340] ov51x_jpeg: disagrees about version of symbol video_devdata
[   50.716345] ov51x_jpeg: Unknown symbol video_devdata
[   50.716507] ov51x_jpeg: disagrees about version of symbol video_unregister_device
[   50.716509] ov51x_jpeg: Unknown symbol video_unregister_device
[   50.716571] ov51x_jpeg: disagrees about version of symbol video_device_alloc
[   50.716573] ov51x_jpeg: Unknown symbol video_device_alloc
[   50.716601] ov51x_jpeg: disagrees about version of symbol video_register_device
[   50.716603] ov51x_jpeg: Unknown symbol video_register_device
[   50.716701] ov51x_jpeg: disagrees about version of symbol video_usercopy
[   50.716702] ov51x_jpeg: Unknown symbol video_usercopy
[   50.716727] ov51x_jpeg: disagrees about version of symbol video_device_release
[   50.716729] ov51x_jpeg: Unknown symbol video_device_release
[   50.725204] ov51x_jpeg: disagrees about version of symbol video_devdata
[   50.725209] ov51x_jpeg: Unknown symbol video_devdata
[   50.725370] ov51x_jpeg: disagrees about version of symbol video_unregister_device
[   50.725372] ov51x_jpeg: Unknown symbol video_unregister_device
[   50.725434] ov51x_jpeg: disagrees about version of symbol video_device_alloc
[   50.725436] ov51x_jpeg: Unknown symbol video_device_alloc
[   50.725465] ov51x_jpeg: disagrees about version of symbol video_register_device
[   50.725467] ov51x_jpeg: Unknown symbol video_register_device
[   50.725564] ov51x_jpeg: disagrees about version of symbol video_usercopy
[   50.725566] ov51x_jpeg: Unknown symbol video_usercopy
[   50.725591] ov51x_jpeg: disagrees about version of symbol video_device_release
[   50.725593] ov51x_jpeg: Unknown symbol video_device_release
[  497.332820] ov51x_jpeg: disagrees about version of symbol video_devdata
[  497.332830] ov51x_jpeg: Unknown symbol video_devdata
[  497.333014] ov51x_jpeg: disagrees about version of symbol video_unregister_device
[  497.333017] ov51x_jpeg: Unknown symbol video_unregister_device
[  497.333089] ov51x_jpeg: disagrees about version of symbol video_device_alloc
[  497.333092] ov51x_jpeg: Unknown symbol video_device_alloc
[  497.333125] ov51x_jpeg: disagrees about version of symbol video_register_device
[  497.333128] ov51x_jpeg: Unknown symbol video_register_device
[  497.333234] ov51x_jpeg: disagrees about version of symbol video_usercopy
[  497.333237] ov51x_jpeg: Unknown symbol video_usercopy
[  497.333266] ov51x_jpeg: disagrees about version of symbol video_device_release
[  497.333269] ov51x_jpeg: Unknown symbol video_device_release
[ 1135.420501] ov51x_jpeg: disagrees about version of symbol video_devdata
[ 1135.420508] ov51x_jpeg: Unknown symbol video_devdata
[ 1135.420688] ov51x_jpeg: disagrees about version of symbol video_unregister_device
[ 1135.420690] ov51x_jpeg: Unknown symbol video_unregister_device
[ 1135.420761] ov51x_jpeg: disagrees about version of symbol video_device_alloc
[ 1135.420763] ov51x_jpeg: Unknown symbol video_device_alloc
[ 1135.420796] ov51x_jpeg: disagrees about version of symbol video_register_device
[ 1135.420798] ov51x_jpeg: Unknown symbol video_register_device
[ 1135.420905] ov51x_jpeg: disagrees about version of symbol video_usercopy
[ 1135.420907] ov51x_jpeg: Unknown symbol video_usercopy
[ 1135.420936] ov51x_jpeg: disagrees about version of symbol video_device_release
[ 1135.420938] ov51x_jpeg: Unknown symbol video_device_release

```

---

### Post by Kasami on 2009-04-18
Ok so I have a problem with lines through my video if I want to do anything outside of Cheese, I have heard that this may happen due to the set resolution being too small.

The first screenshot is from cheese at the resolution of 640 x 480, makes a good image.

The second screenshot is from cheese at the resolution of 320 x 240, this is basically what I get on aMSN or Stickam when I try to use the cam with them.

Would permanantly setting my cam's res to 640 x 480 help at all? If so how can I do it, I'm pretty sure it's possible I just can't remember where I saw the command.

---

### Post by wlbragg on 2009-04-19
billyg

> Mine webcam is working now with you tip

What tip are you referring to? Share with us!

---

### Post by Chris Sharman on 2009-04-25
Ho hum - really hoped this would have got easier by 9.04. Just upgraded 8.04>8.10>9.04. The little red light is on all the time now. Camorama crashes "Unable to capture image", and turns out the little red light temporarily. xawtv also disables the red light, but does display the image - with pink horizontal stripes (the first time), and pink & green (subsequently). Device Manager's gone too, so I guess this guide needs revision. I've been trying to get this thing working for 4 or 5 versions now ...

---

### Post by Kasami on 2009-04-25
> **Chris Sharman said:**
> Ho hum - really hoped this would have got easier by 9.04. Just upgraded 8.04>8.10>9.04. The little red light is on all the time now. Camorama crashes "Unable to capture image", and turns out the little red light temporarily. xawtv also disables the red light, but does display the image - with pink horizontal stripes (the first time), and pink & green (subsequently). Device Manager's gone too, so I guess this guide needs revision. I've been trying to get this thing working for 4 or 5 versions now ...

Device Manager *Should* be under the menu "System". I can't get Camorama working either. Cheese works really well. Xawtv's pink lines are due to it setting the resolution too low. There is a way to up the resolution.

On a quick test hitting J while having XawTV open will take a pic of full resolution and dump it into your home folder. I'll keep looking though.

--EDIT--

Ok found the easiest way. Open XawTV and press E, this will cause a "Chanel Config" Screen to pop up. Make the station ID webcam or something you can remember then press add then save. Then open the .xawtv file that will appear in your home folder with a text editor change their size demensions to 640 x 480. Save it then open Xawtv, resize the window and you should have no more stripes.

---

### Post by nanotube on 2009-04-25
> **Chris Sharman said:**
> Ho hum - really hoped this would have got easier by 9.04. Just upgraded 8.04>8.10>9.04. The little red light is on all the time now. Camorama crashes "Unable to capture image", and turns out the little red light temporarily. xawtv also disables the red light, but does display the image - with pink horizontal stripes (the first time), and pink & green (subsequently). Device Manager's gone too, so I guess this guide needs revision. I've been trying to get this thing working for 4 or 5 versions now ...

you might have to install package "gnome-device-manager"

---

### Post by Kopasakis on 2009-05-19
i have the problem where the video will show but i will have a series of lines in skype i read somewhere that it might be a resolution issue can anyone help, i don't seem to have the problem in cheese just skype

---

### Post by andersja on 2009-05-19
> **Kopasakis said:**
> i have the problem where the video will show but i will have a series of lines in skype i read somewhere that it might be a resolution issue can anyone help, i don't seem to have the problem in cheese just skype

@Kopasakis: Try the Linux forum on the Skype websites:

[http://forum.skype.com/index.php?showforum=194](http://forum.skype.com/index.php?showforum=194)

guidelines how to report tech problems in Skype forums:
[http://forum.skype.com/index.php?act=announce&f=194&id=16]("http://forum.skype.com/index.php?act=announce&f=194&id=16")

Also check release notes to see if your problem is mentioned:
[https://developer.skype.com/LinuxSkype/ReleaseNotes]("https://developer.skype.com/LinuxSkype/ReleaseNotes")

Last but not least, check their bug system "Jira" (Skype equivalent of Launchpad.net):
[https://developer.skype.com/jira/]("https://developer.skype.com/jira/")
[https://developer.skype.com/SkypeGarage/ReportIssue](https://developer.skype.com/SkypeGarage/ReportIssue)

---

### Post by Kopasakis on 2009-05-26
so its been a week and jira has been no help, anyone have any suggestions? the green lines don't show up in cheese unless you drop the resolution to 320 x 240 does anyone know a way to possibly remove that problem  by allowing me to see a 320x240 resolution (which skype works on) or possibly go through a hack to allow me to use the 640 x 480 that the camera does work on?

---

### Post by Zer0 Suii on 2009-05-27
> **Kopasakis said:**
> so its been a week and jira has been no help, anyone have any suggestions? the green lines don't show up in cheese unless you drop the resolution to 320 x 240 does anyone know a way to possibly remove that problem  by allowing me to see a 320x240 resolution (which skype works on) or possibly go through a hack to allow me to use the 640 x 480 that the camera does work on?

Seriously. A lot of people claim they have a working Skype with Eyetoy on Ubuntu then they never tell us anything. Some of us actually have urgent matters to attend to. I'd like to know how to get this frickin' think working! Every time I find something that is a really close call, I have to do something with an "i2c something" file and it's never there.

If that doesn't hlep, I can't get permission to my filesystem at all. I'm really getting angry after wasting 2 full days taking off from work so I can install a great, 5$ webcam that works great with a crappy system like Windows. Why won't it work on this? I know there's a resolution problem. But someone on Windows got it fixed. And Linux, esp. Ubuntu is made by many VERY smart people. Why can't someone just figure this one problem out??

---

### Post by Pandorco on 2009-06-03
[LEFT]I'm trying to install my PS2 Eyetoy as a webcam 

I have no problem up until the part where it tells me to ```
sudo modprobe i2c_core
```After which it tells me:

```
FATAL: Module i2c_core not found.
```

Any ideas?  Any help would be wonderful.[/LEFT]

---

### Post by nanotube on 2009-06-08
update: just tried my eyetoy (in case it matters, it's the silver edition) on a fresh install of ubuntu 9.04, and it worked right out of the box without any tweaking, recognized by cheese and by ekiga with no problems. only thing is that it has to be set to 640x480 resolution, the lower resolution shows some streaky lines in the output. 

hope this info helps someone. :)

---

### Post by Captain_Glen on 2009-06-11
[http://setdosa.blogspot.com/2009/01/fixing-green-screen-for-skype-video-on.html]("http://setdosa.blogspot.com/2009/01/fixing-green-screen-for-skype-video-on.html")

I just followed the bit about editing /~/.Skype/config.xml and now it works.  YAY! :)

---

### Post by andersja on 2009-06-18
Awesome, nanotube - thank you for this heads up!

---

### Post by Kasami on 2009-07-04
So the Eyetoy works out of the box now, great but there is still a problem with the resolution being too high for programs like Skype and aMsn. Is there a way I can shrink the eyetoy's resolution to 320 x 240?

--EDIT--
Okay I answered my own question if anyone wants the solution. I used Webcam Studio. It lets you choose a large res cam for input and then outputs at lower res through a virtual webcam. Fairly easy to install:

[http://webcamstudio.wiki.sourceforge.net/](http://webcamstudio.wiki.sourceforge.net/)

---

### Post by Jose Catre-Vandis on 2009-07-05
@ Kasami

Can you outline excatly what you did to sort out the eyetoy so that Skype works?

---

### Post by Kasami on 2009-07-05
> **Jose Catre-Vandis said:**
> @ Kasami

Can you outline excatly what you did to sort out the eyetoy so that Skype works?

Sorry, I haven't done much testing with Skype.I installed and started Webcam Studio then I opened Skype and it's webcam options. I chose the virtual webcam yesterday and it crashed Skype. Today however it didn't crash. What exactly isn't working for you?

---

### Post by Jose Catre-Vandis on 2009-07-06
I haven't tried it yet, wanted to know what to do first! :)

I take it you just run Webcan Studio, set some options, then fire up Skype and choose a "virtual" webcam sources generated by Webcam Studio?

---

### Post by Kasami on 2009-07-06
> **Jose Catre-Vandis said:**
> I haven't tried it yet, wanted to know what to do first! :)

I take it you just run Webcan Studio, set some options, then fire up Skype and choose a "virtual" webcam sources generated by Webcam Studio?

That's pretty much it. On start up of Webcam studio a message should say that there is a virtual cam running if not Vloopback is either not running or you don't have permission to use it.

You add the source Eyetoy then right click on it and choose "capture size" then the size you want it to input as. That's pretty much it.

---

### Post by Jose Catre-Vandis on 2009-07-13
Hmmm

Can get a picture in webcam studio but it is very slow, then when I try to run Skype and choose a video source, no sign of a virtual webcam and it just crashes closed (Skype).

---

### Post by Kasami on 2009-07-18
> **Jose Catre-Vandis said:**
> Hmmm

Can get a picture in webcam studio but it is very slow, then when I try to run Skype and choose a video source, no sign of a virtual webcam and it just crashes closed (Skype).

The crashing is a problem, try again. But you may not currently have permission to view the vloopback to start the virtual cam, I had this problem. Open a terminal and type:

```
sudo chmod 666 /dev/video*
```

Then open webcam studio and make a virtual cam. It should now be seen by Skype. I have hit a wall though, Skype pics up the virtual cam but it's like it doesn't know what to do with it. It shows a white screen when in a call.

---

### Post by Jose Catre-Vandis on 2009-07-21
OK, the permissions issue allowed access to the vloopback device, but I think I need more help inside Webcam Studio. My picture is really slow, and when I go to the virtual cam tab I can see an image on the left pane, but nothing on the right.

In Skype I can select the vloopback device but can't test it and see no picture. Not crashing out though :)

---

### Post by Jose Catre-Vandis on 2009-08-17
> **Captain_Glen said:**
> [http://setdosa.blogspot.com/2009/01/fixing-green-screen-for-skype-video-on.html]("http://setdosa.blogspot.com/2009/01/fixing-green-screen-for-skype-video-on.html")

I just followed the bit about editing /~/.Skype/config.xml and now it works.  YAY! :)

Me too Yippee....

And I found I could get the mic to work as well by switching to Mic1 ( I have always needed Mic2 for a conventional mic)

---

### Post by infernowolf36 on 2009-08-23
when i type

wget [http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz)

it says 404 file not found. ... any updated packages that anybody knows of?

-edit-
nvm i found the updated file [http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.9.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.9.tar.gz)

---

### Post by infernowolf36 on 2009-08-23
i couldn't execute these: 

sudo modprobe i2c_core
sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
sudo insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko

it said files not found..

so i skipped them.. but the video is weird now.. it has horizontal lines in it that space out the camera.. :( any suggestions?

---

### Post by Jose Catre-Vandis on 2009-08-25
> **infernowolf36 said:**
> i couldn't execute these: 

sudo modprobe i2c_core
sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
sudo insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko

it said files not found..

so i skipped them.. but the video is weird now.. it has horizontal lines in it that space out the camera.. :( any suggestions?

It should work out of the box now, for 9.04, if you follow the advice in the link above. So this howto and the deb from rastageeks is now somewhat redundant?

---

### Post by Jose Catre-Vandis on 2009-08-25
Sorry to double post, but thought I would update the requirements for eyetoy as webcam under skype:

Close Skype before continuing.

Using K/X/Ubuntu 9.04 +, the gspca module in the kernel will run the eyetoy cam as a webcam, but to use it under Skype, and to prevent the pink and green horizontal lines, you need to edit the config file. This is tucked away in your home directory:
```
/home/user/.Skype/skype-user/config.xml
```
where user is your login, and skype-user is your skype login

If you are the cautious type, back up this file first:
```
 cp /home/user/.Skype/skype-user/config.xml /home/user/.Skype/skype-user/config.xml.bak
```

Open up the config.xml file in your text editor, and browse down through the file, you should find a <Video>...</Video> section.Add the following:
```
<CaptureHeight>480</CaptureHeight>
      <CaptureWidth>640</CaptureWidth>
      <RecvPolicy>callpolicy</RecvPolicy> 
```

Mine looks like this:
```
.....</StatsSender>
    <Video>
      <AutoSend>1</AutoSend>
      <CaptureHeight>480</CaptureHeight>
      <CaptureWidth>640</CaptureWidth>
      <Device>/dev/video3</Device>
      <Disable>0</Disable>
      <RecvPolicy>callpolicy</RecvPolicy>
    </Video>
    <table_insert_history>....
```

Start up Skype and head for video settings to select and test.

You can also select the Eyetoy Microphone to use, you may need to play around with your main sound settings to get this working.

---

### Post by Joomla12 on 2009-09-13
Hmm...I'm still a noob at this stuff. When I try to CD to the folder, it says that there is no such directory.

---

### Post by e0h1 on 2009-09-26
Has anybody been able to use Stickam?

I installed the stuff unnecessarily apparently, because I didn't read ahead to see that video can already be captured from eyetoy in Ubuntu 9.04

Stickam didn't work before I tried the steps on theis thread.  It doesn't work now.


I also have lines on the video and I don't know if it is because I installed the files or not.  I'm not sure how to safely remove these files either.

Feedback would be appreciated, thanks.

---

### Post by Kopasakis on 2009-12-22
help ok here is what happened the eyetoy works in cheese-sort of, it doesn't want to record video don't know why  kinda does a second then laggs like no tomorrow with intermittent audio lapses. when i enter skype and try to set the audio it only gives me pulse audio server as an option. the video gives me the option of "EyeToy USB camera Namtai (/dev/video0)" when i hit test it gives me a 2/5 light green snowy sceen with the rest dark green solid green with a small imobile box of an even darker shade of green my config file looks like this     ```
<?xml version="1.0"?>
<config version="1.0" serial="68" timestamp="1261512056.33">
  <Lib>
    <Account>
      <Credentials2>8A1EF9D821AAECE3D8451D9486148A82D790C697DBBDB2ACD45B15C27ACCE4C5618141B3FEC220F44C61EB6BE6E006AB2407973256AFEC2DE428348EDFE370BDAF71D7D465A4AF33D11D728C932E9AD83364EAD2353CF755DAD709CACD37CCF32F60E638AF6806E1D479EC1B99E080FF88985C50216DEC5D4CC15FFD0837C7F1DE29FD5889AD0A84A2FF61E36883AEA58AFF7597E29FB5034EF7CB081C35EBFCA9700E1E59A9ADFE47B2E8EF5894771F497B9279F878E5D7EECB847D9ED50CBB288A31A55F4C4F4115D20E51DD710A5628AA75CE7AD78D3594CC335663EFEEB933E32A1A2E4E2095BB2A2D93139384119C8E752FBBA631D81410DC94A51FDC3D33B56A3C9F473C8B855E7372664ED4FEC75C006D34FCFD20D212FCA74E8A84D13A704C923E3C117DD4FBD974C3D5A2EE19B61ADD016445369B380224E3A98C6DB16514BD3A438E1A326E5F7D2812D0A4BF9E1716165F03382B5154EF84F7D14B117D61D426FCA7853475004763AD26A54723AE498193CDE08F9F02A4EEB74F4BA76DDDC5B54F367AA6FE7427C3475B7181ADFEDBD37D3AD1DA890137247F314DCBA789E75EE0957310C47344670C346F5533BB30E3F768898BABAA462C9F193F24CF20B7C36513E76259C779D635478C617BAC449E1FB91AD0A9B804330845CEA8B1F75E0A80E0E17FFC25309AD569A20904735BCDAD2AB325595A7506AA0DC017A15F2F666CE48B9F039DC683351E0247E82E8F1CD2EB811722A8E00E159AFC4F0495ABD9E8F879F32EAC65D7610C599A8451CFB61D8806E16472290C134DE4870B98414DFC6972F101F30CD62A6A93EC4DBA2AE558C71F</Credentials2>
      <IdleTimeForAway>300</IdleTimeForAway>
      <IdleTimeForNA>1800</IdleTimeForNA>
      <LastUsed>1261510812</LastUsed>
      <LocalData>42B09F97E6E144</LocalData>
      <Migration>31</Migration>
    </Account>
    <Call>
      <DPC>4100</DPC>
      <VideoEndPoints>B7B2E66E</VideoEndPoints>
    </Call>
    <CentralStorage>
      <LastBackoff>0</LastBackoff>
      <LastFailure>0</LastFailure>
      <LastSync>1261508871</LastSync>
      <NeedSync>0</NeedSync>
      <SyncSet>
        <p>
          <avatar>c13dc0ac:2</avatar>
          <email>a86d4f2e:2</email>
          <mood>1344e6e1:2</mood>
          <profile>1b018107:2</profile>
          <richmood>f16ef728:2</richmood>
        </p>
        <u>
          <**********>e93a439f:2</***************>
          <******************>a8c24249:2</*****************>
          <echo123>b434d231:2</echo123>
          <*************>db9ebbd:2</************>
                   <*************>db9ebbd:2</************>          <*************>db9ebbd:2</************>          <*************>db9ebbd:2</************>          <*************>db9ebbd:2</************>          <*************>db9ebbd:2</************>>
        </u>
      </SyncSet>
    </CentralStorage>
    <Chat>
      <ActivityTS>1</ActivityTS>
      <DialogPartner>3</DialogPartner>
      <MigrationDone>1261508869</MigrationDone>
    </Chat>
    <Contacts>
      <Migration>1</Migration>
    </Contacts>
    <Notification>
      <LastID>1000000022</LastID>
      <LastPoll>1261508870</LastPoll>
      <LastSearch>1261510812</LastSearch>
    </Notification>
    <PM>
      <pslut>1261508872</pslut>
    </PM>
    <ProfilePopulated>2</ProfilePopulated>
    <PropsManager>
      <PermaProps>410900F5010300932001008420DDBEC4D904008920DEBEC4D90400F801B30100FA017D00A9010100FC0125008620F6CAC4D904</PermaProps>
    </PropsManager>
    <StatsSender>
      <Saved>4103000185B2C4D90405024100000300</Saved>
    </StatsSender>
    <Video>
      <CaptureHeight>480</CaptureHeight>
      <CaptureWidth>640</CaptureWidth>
      <RecvPolicy>callpolicy</RecvPolicy>
    </Video>
    <table_insert_history>
      <_82a5388795850ec5f054daecd8ad483f6042b53786df85512e11a4c1a4d51180>1261597212 15652:21600:1261510812 14238:5400:1261510812 56787:28800:1261510812 51977:21600:1261510812 2147485209:86400:1261510812</_82a5388795850ec5f054daecd8ad483f6042b53786df85512e11a4c1a4d51180>
    </table_insert_history>
  </Lib>
</config>
```

i threw in lines of ************* so as to hide the identities of my friends i'm sure they wouldn't want their names showing up in google but any ideas on how to fix this and where to put the 
     Code:
     <CaptureHeight>480</CaptureHeight>
      <CaptureWidth>640</CaptureWidth>
      <RecvPolicy>callpolicy</RecvPolicy>

oh and i'm running jaunty still my mom didn't like karmic so i had to down grade

---

### Post by Jose Catre-Vandis on 2009-12-23
> **Kopasakis said:**
> help ok here is what happened the eyetoy works in cheese-sort of, it doesn't want to record video don't know why  kinda does a second then laggs like no tomorrow with intermittent audio lapses. when i enter skype and try to set the audio it only gives me pulse audio server as an option. the video gives me the option of "EyeToy USB camera Namtai (/dev/video0)" when i hit test it gives me a 2/5 light green snowy sceen with the rest dark green solid green with a small imobile box of an even darker shade of green my config file looks like this     ```
<?xml version="1.0"?>
<config version="1.0" serial="68" timestamp="1261512056.33">
  <Lib>
    <Account>
      <Credentials2>8A1EF9D821AAECE3D8451D9486148A82D790C697DBBDB2ACD45B15C27ACCE4C5618141B3FEC220F44C61EB6BE6E006AB2407973256AFEC2DE428348EDFE370BDAF71D7D465A4AF33D11D728C932E9AD83364EAD2353CF755DAD709CACD37CCF32F60E638AF6806E1D479EC1B99E080FF88985C50216DEC5D4CC15FFD0837C7F1DE29FD5889AD0A84A2FF61E36883AEA58AFF7597E29FB5034EF7CB081C35EBFCA9700E1E59A9ADFE47B2E8EF5894771F497B9279F878E5D7EECB847D9ED50CBB288A31A55F4C4F4115D20E51DD710A5628AA75CE7AD78D3594CC335663EFEEB933E32A1A2E4E2095BB2A2D93139384119C8E752FBBA631D81410DC94A51FDC3D33B56A3C9F473C8B855E7372664ED4FEC75C006D34FCFD20D212FCA74E8A84D13A704C923E3C117DD4FBD974C3D5A2EE19B61ADD016445369B380224E3A98C6DB16514BD3A438E1A326E5F7D2812D0A4BF9E1716165F03382B5154EF84F7D14B117D61D426FCA7853475004763AD26A54723AE498193CDE08F9F02A4EEB74F4BA76DDDC5B54F367AA6FE7427C3475B7181ADFEDBD37D3AD1DA890137247F314DCBA789E75EE0957310C47344670C346F5533BB30E3F768898BABAA462C9F193F24CF20B7C36513E76259C779D635478C617BAC449E1FB91AD0A9B804330845CEA8B1F75E0A80E0E17FFC25309AD569A20904735BCDAD2AB325595A7506AA0DC017A15F2F666CE48B9F039DC683351E0247E82E8F1CD2EB811722A8E00E159AFC4F0495ABD9E8F879F32EAC65D7610C599A8451CFB61D8806E16472290C134DE4870B98414DFC6972F101F30CD62A6A93EC4DBA2AE558C71F</Credentials2>
      <IdleTimeForAway>300</IdleTimeForAway>
      <IdleTimeForNA>1800</IdleTimeForNA>
      <LastUsed>1261510812</LastUsed>
      <LocalData>42B09F97E6E144</LocalData>
      <Migration>31</Migration>
    </Account>
    <Call>
      <DPC>4100</DPC>
      <VideoEndPoints>B7B2E66E</VideoEndPoints>
    </Call>
    <CentralStorage>
      <LastBackoff>0</LastBackoff>
      <LastFailure>0</LastFailure>
      <LastSync>1261508871</LastSync>
      <NeedSync>0</NeedSync>
      <SyncSet>
        <p>
          <avatar>c13dc0ac:2</avatar>
          <email>a86d4f2e:2</email>
          <mood>1344e6e1:2</mood>
          <profile>1b018107:2</profile>
          <richmood>f16ef728:2</richmood>
        </p>
        <u>
          <**********>e93a439f:2</***************>
          <******************>a8c24249:2</*****************>
          <echo123>b434d231:2</echo123>
          <*************>db9ebbd:2</************>
                   <*************>db9ebbd:2</************>          <*************>db9ebbd:2</************>          <*************>db9ebbd:2</************>          <*************>db9ebbd:2</************>          <*************>db9ebbd:2</************>>
        </u>
      </SyncSet>
    </CentralStorage>
    <Chat>
      <ActivityTS>1</ActivityTS>
      <DialogPartner>3</DialogPartner>
      <MigrationDone>1261508869</MigrationDone>
    </Chat>
    <Contacts>
      <Migration>1</Migration>
    </Contacts>
    <Notification>
      <LastID>1000000022</LastID>
      <LastPoll>1261508870</LastPoll>
      <LastSearch>1261510812</LastSearch>
    </Notification>
    <PM>
      <pslut>1261508872</pslut>
    </PM>
    <ProfilePopulated>2</ProfilePopulated>
    <PropsManager>
      <PermaProps>410900F5010300932001008420DDBEC4D904008920DEBEC4D90400F801B30100FA017D00A9010100FC0125008620F6CAC4D904</PermaProps>
    </PropsManager>
    <StatsSender>
      <Saved>4103000185B2C4D90405024100000300</Saved>
    </StatsSender>
    <Video>
      <CaptureHeight>480</CaptureHeight>
      <CaptureWidth>640</CaptureWidth>
      <RecvPolicy>callpolicy</RecvPolicy>
    </Video>
    <table_insert_history>
      <_82a5388795850ec5f054daecd8ad483f6042b53786df85512e11a4c1a4d51180>1261597212 15652:21600:1261510812 14238:5400:1261510812 56787:28800:1261510812 51977:21600:1261510812 2147485209:86400:1261510812</_82a5388795850ec5f054daecd8ad483f6042b53786df85512e11a4c1a4d51180>
    </table_insert_history>
  </Lib>
</config>
```

i threw in lines of ************* so as to hide the identities of my friends i'm sure they wouldn't want their names showing up in google but any ideas on how to fix this and where to put the 
     Code:
     <CaptureHeight>480</CaptureHeight>
      <CaptureWidth>640</CaptureWidth>
      <RecvPolicy>callpolicy</RecvPolicy>

oh and i'm running jaunty still my mom didn't like karmic so i had to down grade

Can't see a video device in your config file. Try adding this to your Video section:
```
<Device>/dev/video0</Device>
```

Given that your cam is at video0

You might need to restart...?

---

### Post by eniali on 2010-01-24
Dear all,
I need some help with K.Koala and EyeToy...
I have used Ubuntu 7.10, 8.10 and 9.04 and have installed EyeToy without problems after each Ubuntu upgrade (using instructions in [http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall]("http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall")).

I recently upgraded to 9.10 and Eyetoy was working perfectly with XAWTV, but was oly showing green and pink lines on Skype.
Thinking I needed to reinstall the drivers, I followed the same procedure and removed the existing driver using:
[HTML]sudo mv /lib/modules/`uname -r`/kernel/drivers/media/video/gspca/ ~/backup.modules.webcams[/HTML]
Tried to compile the ov51x-jpeg-1.5.9 module but got plenty of errors and did not succeed.
Now I have no video at all - neither on XAWTV or in Skype.

Anyone can help?
Thanks!

---

### Post by SagnaB on 2010-03-11
hey guys I have tried this but...

when I sudo make install i get errors

```

bangas@auzziety:~/ov51x-jpeg-1.5.9$ sudo make install
[sudo] password for bangas: 
make -C /lib/modules/2.6.31-9-rt/build M=/home/bangas/ov51x-jpeg-1.5.9 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-9-rt'
  CC [M]  /home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.o
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ‘create_proc_ov511_cam’:
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:677: error: implicit declaration of function ‘info’
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:681: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:689: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:700: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:712: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ‘proc_ov511_create’:
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:766: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ‘ov51x_clear_snapshot’:
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:1691: error: implicit declaration of function ‘warn’
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ‘ov51x_v4l1_ioctl’:
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: warning: passing argument 1 of ‘video_usercopy’ from incompatible pointer type
include/media/v4l2-ioctl.h:298: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: warning: passing argument 2 of ‘video_usercopy’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: warning: passing argument 4 of ‘video_usercopy’ makes pointer from integer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘v4l2_kioctl’ but argument is of type ‘long unsigned int’
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: error: too many arguments to function ‘video_usercopy’
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: At top level:
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6651: warning: initialization from incompatible pointer type
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ‘ov51x_probe’:
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:8307: error: implicit declaration of function ‘init_MUTEX’
make[2]: *** [/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.o] Error 1
make[1]: *** [_module_/home/bangas/ov51x-jpeg-1.5.9] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-9-rt'
make: *** [all] Error 2

```

---

### Post by danadn on 2010-04-06
Nobody nows nothing. Hours looking for the solution and that's the conclusion.

---

### Post by towheedm on 2010-04-06
> **danadn said:**
> Nobody nows nothing. Hours looking for the solution and that's the conclusion.

OK this is not true. When I first bought the Eyetoy for my son's PS2 years ago I tried to get it to work under that other OS, you know, the one with the flag thingy.  But there was no driver around.

I started using Ubuntu abt December last year.   When I first came across a tread that Karmic supported the Eyetoy, I was elated. Ran into my son's room ,grabbed the Eyetoy, read all the threads I could find abt the Eyetoy, only to realize that ov51x-jpeg-1.5.9 just simply does not compile under Karmic.

Read some more, did some checks on my system, decided that the default driver just might work.  So, I installed Cheese, plugged in my Eyetoy and....WHAM!!!! Video in Cheese.  Tried xawtv but got the familiar green lines everyone else gets.  At this point no audio though.  I use PA.  PA just was not detecting the Eyetoy as a source.  Well I was messing with PA and completely screwed it.  Did a complete removal via synaptic, then searched for every PA related file on my system that did not get removed and manually deleted them.  Reinstalled PA, and again......WHAM!!!! It detected the Eyetoy as a source.

Hastily went over to Skype and installed it.  Video and audio off the bat, first shot, no problems.  Still works.

Well just a word of encouragement for those whose who are having problems.  Just got home from the office, si if I get some time later will retrace my steps more precisely and post back.  Don't dispair, it works.

The only caveat I have is if I open the device more than once during a login session, the green lines re-appear.  But no problem for me bacause if I use Skype it remains on until I shutdown and I almost never use Cheese.

---

### Post by Fallen_Enigma on 2010-04-16
> **SagnaB said:**
> hey guys I have tried this but...

when I sudo make install i get errors

```

bangas@auzziety:~/ov51x-jpeg-1.5.9$ sudo make install
[sudo] password for bangas: 
make -C /lib/modules/2.6.31-9-rt/build M=/home/bangas/ov51x-jpeg-1.5.9 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-9-rt'
  CC [M]  /home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.o
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ‘create_proc_ov511_cam’:
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:677: error: implicit declaration of function ‘info’
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:681: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:689: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:700: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:712: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ‘proc_ov511_create’:
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:766: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ‘ov51x_clear_snapshot’:
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:1691: error: implicit declaration of function ‘warn’
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ‘ov51x_v4l1_ioctl’:
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: warning: passing argument 1 of ‘video_usercopy’ from incompatible pointer type
include/media/v4l2-ioctl.h:298: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: warning: passing argument 2 of ‘video_usercopy’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: warning: passing argument 4 of ‘video_usercopy’ makes pointer from integer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘v4l2_kioctl’ but argument is of type ‘long unsigned int’
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: error: too many arguments to function ‘video_usercopy’
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: At top level:
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6651: warning: initialization from incompatible pointer type
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ‘ov51x_probe’:
/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:8307: error: implicit declaration of function ‘init_MUTEX’
make[2]: *** [/home/bangas/ov51x-jpeg-1.5.9/ov51x-jpeg-core.o] Error 1
make[1]: *** [_module_/home/bangas/ov51x-jpeg-1.5.9] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-9-rt'
make: *** [all] Error 2

```

I have the same problem. /bump

---

### Post by Jose Catre-Vandis on 2010-05-02
Just upgraded to Xubuntu 10.04 (Lucid Lynx)
Used the 8.10 deb from Skype.com
Newer "Silver" Eyetoy

To get it working:

Follow steps 3 - 7 in this previously posted blog entry
[http://setdosa.blogspot.com/2009/01/fixing-green-screen-for-skype-video-on.html](http://setdosa.blogspot.com/2009/01/fixing-green-screen-for-skype-video-on.html)

Job done :)

Here are the steps:

> Fixing skype video on Ubuntu 10.04

3. Edited my ~/.Skype/<username>/config.xml to add the Video element. Mine did not have a <Video> element, I put it under <Lib> 

    ...
      <Lib>
         ...
         <Video>
          <CaptureHeight>480</CaptureHeight>
          <CaptureWidth>640</CaptureWidth>
          <RecvPolicy>callpolicy</RecvPolicy>

        </Video>
        ...
      </Lib>
    ...

4. sudo mv /usr/bin/skype /usr/bin/skype.real
   sudo chmod 755 /usr/bin/skype.real
  
5. sudo nano /usr/bin/skype and put the following inside

    #!/bin/bash
    LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.real

 If you use 64 bit then replace with

    #!/bin/bash
    LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype.real

6. sudo chmod 755 /usr/bin/skype

7. Test your skype video. It should work now.

---

### Post by Chris Sharman on 2010-05-02
Brilliant - finally working.
I didn't need step 3 (edit config.xml)

Many thanks

---

### Post by def_mornahan on 2010-05-05
> **Jose Catre-Vandis said:**
> Just upgraded to Xubuntu 10.04 (Lucid Lynx)
Used the 8.10 deb from Skype.com
Newer "Silver" Eyetoy

To get it working:

Follow steps 3 - 7 in this previously posted blog entry
[http://setdosa.blogspot.com/2009/01/fixing-green-screen-for-skype-video-on.html](http://setdosa.blogspot.com/2009/01/fixing-green-screen-for-skype-video-on.html)

Job done :)

I have the silver EyeToy.  None of this Skype advice works for me under Karmic.  Cheese works fine, xawtv is sort of black and white but I would kill for any video in Skype.  I've never gotten the green or pink stripes of death, but when I click "Test" in Skype, nothing happens.

Sagna and Enigma, I get the same errors when I try to install the downloaded driver (on two different computers).  I don't think it compiles under Karmic (9.10).  The driver is already included in the distro anyway.

towheedm, what's PA?  I stick webcam and PA and linux into Google and all I get is stuff about a sex scandal (!!!).

---

### Post by def_mornahan on 2010-05-05
Oh...crumbs.  Sorry about that.  I'm using an Acer Aspire 5102 and naturally used /lib32/ when I needed to use /lib/.  That worked like a charm...I'm videoconfing with my friend right now.

---

### Post by towheedm on 2010-05-05
> **def_mornahan said:**
> towheedm, what's PA?  I stick webcam and PA and linux into Google and all I get is stuff about a sex scandal (!!!).

PA = Pulseaudio sound server.

Did you try this:

Rename the skype binary file:
```
sudo mv /usr/bin/skype /usr/bin/skype.real
```Create a new file named skype:
```
gksudo gedit /usr/bin/skype
```Paste the following two lines into it:
```
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so XLIB_SKIP_ARGB_VISUALS=1 skype.real
```Save the file and close gedit.  Now make it executable:
```
sudo chmod +x /usr/bin/skype
```I had the same problem with the cam working with cheese etc, but no video in the skype test.  The above worked for me.

Hope it helps you to.

---

### Post by Chris Sharman on 2010-05-06
Cam working fine.
Mike isn't though  :-(
I've got a motherboard mike of some kind that's badly muffled, and that seems to be the only available option.
Previously (when the camera didn't work) it did find & use the eyetoy mike.

Anyone know how to enable the logitech eyetoy microphone?

Chris

---

### Post by Mountain Dew Overdose on 2010-06-01
I'm having another issue with this...I installed the drivers, surprisingly they were in Synaptic! I'm running Ubuntu Lucid, and I'm having issues trying to get this working...

tyler@lintmagnet:~$ sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
insmod: can't read '/lib/modules/2.6.32-22-generic/extra/ov51x.ko': No such file or directory

That's one of the commands I'm supposed to run from the howto, any suggestions? :(?

---

### Post by djmashedman on 2010-06-21
Hey guys. Glad to see this thread is still active!

So I dug out my eyetoy, plugged it into my karmic laptop and hey presto, it works. Sorta.

It is recognised, and it shows video (no sound) but the video picture is really weird, it is as though someone turned the saturation and brightness right up, and messed with hue so I'm all green.

Opened up Cheese and started messing with saturation, hue, brightness, contrast, whatever, and it still won't get me a normal image.

Any ideas what's wrong?

---

### Post by owners4life5 on 2010-07-20
works, but wget epicly fails

---

### Post by dwxvi on 2010-07-23
I'm trying to get the Black Eyetoy (Namtai, not Logitech) working in Skype in Ubuntu Jaunty...I've tried SEVERAL things and now I have the mic working fine, but after using towheedm's instructions, I finally have video, but the video looks like an acid trip. There are also greyish-green horizontal lines going all across the frame, but this is the first time I've ever had video working. Anyone know how to solve this problem??

---

### Post by towheedm on 2010-07-24
> **dwxvi said:**
> I'm trying to get the Black Eyetoy (Namtai, not Logitech) working in Skype in Ubuntu Jaunty...I've tried SEVERAL things and now I have the mic working fine, but after using towheedm's instructions, I finally have video, but the video looks like an acid trip. There are also greyish-green horizontal lines going all across the frame, but this is the first time I've ever had video working. Anyone know how to solve this problem??

Could you post a screenshot?  It sounds as though it's a resolution problem.

---

### Post by knil727 on 2010-08-14
I'm running 10.04 and I've tried instructions once.  I found out that on a fresh install of 10.04 that there isn't a video.0 file.  Which to my understanding is needed to install the eyetoy.  Any suggestions?  Or just private message me with instructions for a complete n00b...

---

### Post by Jose Catre-Vandis on 2010-08-15
> **knil727 said:**
> I'm running 10.04 and I've tried instructions once.  I found out that on a fresh install of 10.04 that there isn't a video.0 file.  Which to my understanding is needed to install the eyetoy.  Any suggestions?  Or just private message me with instructions for a complete n00b...

try
```
sudo apt-get install ubuntu-restricted-extras
``` and have another go

---

### Post by knil727 on 2010-08-15
> **Jose Catre-Vandis said:**
> try
```
sudo apt-get install ubuntu-restricted-extras
``` and have another go
I have the restricted extras already.  I realized that I didn't have the file in the right place to extract it in the first place but I can't get all the "insmod" commands to work... I'll past my whole log from my brick call attempts here.

> me@Jad:~$ tar -xvf ov51x-jpeg-1.5.9.tar.gz
ov51x-jpeg-1.5.9/
ov51x-jpeg-1.5.9/test/
ov51x-jpeg-1.5.9/test/Makefile
ov51x-jpeg-1.5.9/test/getjpeg.c
ov51x-jpeg-1.5.9/Makefile
ov51x-jpeg-1.5.9/ov51x-jpeg-core.c
ov51x-jpeg-1.5.9/ov518-decomp.c
ov51x-jpeg-1.5.9/ov51x-jpeg.h
ov51x-jpeg-1.5.9/ov519-decomp.c
ov51x-jpeg-1.5.9/ov511-decomp.c
ov51x-jpeg-1.5.9/ov7670.h
ov51x-jpeg-1.5.9/ChangeLog
me@Jad:~$ cd ov51x-jpeg-1.5.9
me@Jad:~/ov51x-jpeg-1.5.9$ sudo make install
[sudo] password for me: 
make -C /lib/modules/2.6.32-24-generic/build M=/home/me/ov51x-jpeg-1.5.9 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/me/ov51x-jpeg-1.5.9/ov51x-jpeg-core.o
/home/me/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ‘create_proc_ov511_cam’:
/home/me/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:677: error: implicit declaration of function ‘info’
/home/me/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:681: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/me/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:689: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/me/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:700: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/me/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:712: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/me/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ‘proc_ov511_create’:
/home/me/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:766: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/me/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ‘ov51x_clear_snapshot’:
/home/me/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:1691: error: implicit declaration of function ‘warn’
/home/me/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ‘ov51x_v4l1_ioctl’:
/home/me/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: warning: passing argument 1 of ‘video_usercopy’ from incompatible pointer type
include/media/v4l2-ioctl.h:298: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/home/me/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: warning: passing argument 2 of ‘video_usercopy’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/home/me/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: warning: passing argument 4 of ‘video_usercopy’ makes pointer from integer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘v4l2_kioctl’ but argument is of type ‘long unsigned int’
/home/me/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: error: too many arguments to function ‘video_usercopy’
/home/me/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: At top level:
/home/me/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6651: warning: initialization from incompatible pointer type
make[2]: *** [/home/me/ov51x-jpeg-1.5.9/ov51x-jpeg-core.o] Error 1
make[1]: *** [_module_/home/me/ov51x-jpeg-1.5.9] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [all] Error 2
me@Jad:~/ov51x-jpeg-1.5.9$ sudomodprobe videodev
sudomodprobe: command not found
me@Jad:~/ov51x-jpeg-1.5.9$ sudo modprobe videodev
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
me@Jad:~/ov51x-jpeg-1.5.9$ sudo modprobe i2c_core
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
me@Jad:~/ov51x-jpeg-1.5.9$ sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
insmod: can't read '/lib/modules/2.6.32-24-generic/extra/ov51x.ko': No such file or directory
me@Jad:~/ov51x-jpeg-1.5.9$ sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
insmod: can't read '/lib/modules/2.6.32-24-generic/extra/ov51x.ko': No such file or directory
me@Jad:~/ov51x-jpeg-1.5.9$ sudo insmod /lib/modules/`uname -r`/extra/ov51x
insmod: can't read '/lib/modules/2.6.32-24-generic/extra/ov51x': No such file or directory
me@Jad:~/ov51x-jpeg-1.5.9$ sudo insmod /lib/modules/`uname -r`/ov51x.ko
insmod: can't read '/lib/modules/2.6.32-24-generic/ov51x.ko': No such file or directory
me@Jad:~/ov51x-jpeg-1.5.9$ sudo insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko
insmod: can't read '/lib/modules/2.6.32-24-generic/extra/ov519_decomp.ko': No such file or directory
me@Jad:~/ov51x-jpeg-1.5.9$ sudo insmod `uname -r`/ov51x
insmod: can't read '2.6.32-24-generic/ov51x': No such file or directory
me@Jad:~/ov51x-jpeg-1.5.9$ 


---

### Post by Jose Catre-Vandis on 2010-08-16
@ knil

Looks like you are trying the "old" way using the ov51_jpeg module. Things have moved on and you should be getting it to work with gspca.

Look a little bit back in this thread here:

[http://ubuntuforums.org/showpost.php?p=9218147&postcount=127](http://ubuntuforums.org/showpost.php?p=9218147&postcount=127)

and see if you can get success. it should work out of the box, but with a little tweak

---

### Post by spatiegames on 2010-11-07
My eyetoy works out-of-the-box with Cheese. In Kdenlive the video4linux cam source is set to /dev/video0 (which it's also set to in Cheese), and it doesn't work. Also when I record video in Cheese it doesn't record sound...

---

### Post by Jose Catre-Vandis on 2010-12-27
Update for PS2 eyetoys (black and silver) on Xubuntu 10.10 for both Video and Microphone.

Seems that the eyetoy video will work out of the box for cheese and skype. However, the microphone, though identified to some extent does not get picked up by pulseaudio. The workaround for this is to remove pulseaudio and just use alsa.

To remove pulseaudio:
```
sudo apt-get install gstreamer0.10-alsa
sudo apt-get purge gstreamer0.10-pulseaudio vlc-plugin-pulse pulseaudio
```

Adjust your sound levels using alsamixer

Now create / edit ~/.asoundrc.conf and add this to it:
```
pcm.!default {
    type plug
    slave.pcm {
        type asym
        playback.pcm "dmix:NVidia"
        capture.pcm "dsnoop:NVidia"
    }
}  
``` replacing "NVidia" with your sound card name.

Best to reboot now. Microphone should be working. Go into Skype Options, Audio Devices, Click on the drop down for microphone, should be quite a long list. I first tried the dsnoop one which worked, but you may need to try others to get sound from the mic.

---

### Post by Jose Catre-Vandis on 2010-12-29
More fun to be had with your PS2 eyetoy as webcam. (Remember this is without pulseaudio!)

Recording Sound:

First off, define which device is generating the sound from the microphone
```
aplay -l
```
This tells me my eyetoy microphone is card 1, device 0, which translates to plughw:1,0. To record sound from the mic enter this command in a terminal:
```
arecord -f cd -t wav -c 2 -D plughw:1,0 foobar.wav
```
This records a wav file at CD quality.

Video Playback:

Lots of choices here:

```
mplayer tv:// -tv device=/dev/video0
```
```
cvlc v4l2:///dev/video0
```
and the monster that is gstreamer (you'll need to ensure gstreamer-tools is installed)
```
gst-launch v4l2src device=/dev/video0 ! 'video/x-raw-yuv,width=640,height=480,framerate=30/1' ! xvimagesink
```

Capturing Video - Video and Sound:

This proved harder than I thought as vlc, ffmpeg and mencoder flatly refused to do the job with all the command lines I found out on google.

Using gstreamer again, although this is a bit unwieldy:
Capture Video only (no concurrent playback):
```
gst-launch v4l2src device=/dev/video0 ! 'video/x-raw-yuv,width=640,height=480,framerate=30/1' ! queue ! videorate! 'video/x-raw-yuv,framerate=30/1' ! theoraenc ! queue ! oggmux ! filesink location=output.ogg
```
Capture Video and Sound (with concurrent playback):
```
gst-launch v4l2src ! 'video/x-raw-yuv,width=640,height=480,framerate=30/1' ! tee name=t_vid ! queue ! videoflip method=horizontal-flip ! xvimagesink sync=false t_vid. ! queue ! videorate ! 'video/x-raw-yuv,framerate=30/1' ! queue ! mux. alsasrc device=plughw:1,0 ! audio/x-raw-int,rate=48000,channels=2,depth=16 ! queue ! audioconvert ! queue ! mux. avimux name=mux ! filesink location=output.avi
```

FFMPEG
Capture Video and Sound (variants on):
```
ffmpeg -t 10 -f video4linux2 -s 640x480 -r 15 -i /dev/video0 -f alsa -ac 2 -i plughw:1,0  -aspect 4:3 -s 720x400 -qscale 3 video-with-sound.flv
```
```
ffmpeg -t 10 -f video4linux2 -s 640x480 -r ntsc -i /dev/video0 -f alsa -ac 2 -i plughw:1,0 -qscale 3 video-with-sound.avi
```
Just video:
```
ffmpeg -f alsa video4linux2 -s 720x480 -r 30000/1001 -i /dev/video0 -sameq -aspect 4:3 -f avi -vcodec mjpeg -r 30000/1001 -y output.avi
```

Enjoy :)

---

### Post by careerstrokes on 2010-12-29
I am new with Ubuntu. 
 On Ubuntu 8.10, I actually tried the “hacked” ov51xx driver but the camera still wont work!
 This is my dmesg:
 13.261951] Linux video capture interface: v2.00
[   13.448568] ov51x_jpeg: USB OV518 video device found
[   13.450803] ov51x_jpeg: Device revision 9
[   13.462880] ov51x_jpeg: Compression required with OV518…enabling
[   13.482770] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   13.539661] nvidia 0000:01:00.0: [PCI[IMG]http://images.intellitxt.com/ast/adTypes/mag-glass_10x10.gif[/IMG]]("http://www.ubuntugeek.com/tip-getting-your-webcam-to-work-in-ubuntu.html#") INT A -> GSI 16 (level, low) -> IRQ 16
[   13.542369] NVRM: loading [NVIDIA[IMG]http://images.intellitxt.com/ast/adTypes/mag-glass_10x10.gif[/IMG]]("http://www.ubuntugeek.com/tip-getting-your-webcam-to-work-in-ubuntu.html#") Linux x86 Kernel Module  96.43.09  Mon Oct 27 14:23:30 PST 2008
[   13.606260] input: GenPS/2 Genius Mouse as /devices/platform/i8042/serio1/input/input6
[   13.614882] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   13.615057] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   13.905235] phy0: Selected rate control algorithm ‘pid’
[   14.126533] Registered led device: rt2500usb-phy0:radio
[   15.616561] ov51x_jpeg: Sensor is an OV66308AE
[   15.991834] ov51x_jpeg: Device at usb-0000:00:10.1-1 registered to minor 0
[   15.991893] usbcore: registered new interface driver ov51x
[   15.991929] usbcore: registered new interface driver rt2500usb
[   15.992628] ov51x_jpeg: 1.5.9 : ov51x USB Camera Driver
[   17.151656] lp: driver loaded but no devices found
 Is there anything wrong?
 My lsusb, however :
 Bus 004 Device 003: ID 13b1:000d Linksys WUSB54G Wireless Adapter
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 05a9:0518 OmniVision Technologies, Inc. OV518 WebCam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 PLease help!! I know the camera works in windows xp!!
 Appreciate it a lot guys!

---

### Post by Jose Catre-Vandis on 2010-12-29
@ careerstrokes

1. Doesn't look like an eyetoy webcam?
2. Can you get a later version of Ubuntu (e.g. 10.04 / 10.10)?

---

### Post by Favrenation on 2011-01-02
I can confirm that Skype automatically detects my Eyetoy in Ubuntu 10.04. Didn't try sound but the video quality is just as good as the Windows Driver. Also I didn't need to use the guide to install a driver.

---

### Post by taters05456 on 2011-01-05
I know this thread has been going for years now, but I'm stuck. I'm not using an eyetoy, but I am using an ov51x camera, and I'm getting stuck at the make point, for some reason.

> make -C /lib/modules/2.6.32-27-generic/build M=/home/taters/Desktop/ov51x-jpeg-1.5.9 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-27-generic'
  CC [M]  /home/taters/Desktop/ov51x-jpeg-1.5.9/ov51x-jpeg-core.o
/home/taters/Desktop/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function \u2018create_proc_ov511_cam\u2019:
/home/taters/Desktop/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:677: error: implicit declaration of function \u2018info\u2019
/home/taters/Desktop/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:681: error: \u2018struct proc_dir_entry\u2019 has no member named \u2018owner\u2019
/home/taters/Desktop/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:689: error: \u2018struct proc_dir_entry\u2019 has no member named \u2018owner\u2019
/home/taters/Desktop/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:700: error: \u2018struct proc_dir_entry\u2019 has no member named \u2018owner\u2019
/home/taters/Desktop/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:712: error: \u2018struct proc_dir_entry\u2019 has no member named \u2018owner\u2019
/home/taters/Desktop/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function \u2018proc_ov511_create\u2019:
/home/taters/Desktop/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:766: error: \u2018struct proc_dir_entry\u2019 has no member named \u2018owner\u2019
/home/taters/Desktop/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function \u2018ov51x_clear_snapshot\u2019:
/home/taters/Desktop/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:1691: error: implicit declaration of function \u2018warn\u2019
/home/taters/Desktop/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function \u2018ov51x_v4l1_ioctl\u2019:
/home/taters/Desktop/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: warning: passing argument 1 of \u2018video_usercopy\u2019 from incompatible pointer type
include/media/v4l2-ioctl.h:298: note: expected \u2018struct file *\u2019 but argument is of type \u2018struct inode *\u2019
/home/taters/Desktop/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: warning: passing argument 2 of \u2018video_usercopy\u2019 makes integer from pointer without a cast
include/media/v4l2-ioctl.h:298: note: expected \u2018unsigned int\u2019 but argument is of type \u2018struct file *\u2019
/home/taters/Desktop/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: warning: passing argument 4 of \u2018video_usercopy\u2019 makes pointer from integer without a cast
include/media/v4l2-ioctl.h:298: note: expected \u2018v4l2_kioctl\u2019 but argument is of type \u2018long unsigned int\u2019
/home/taters/Desktop/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: error: too many arguments to function \u2018video_usercopy\u2019
/home/taters/Desktop/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: At top level:
/home/taters/Desktop/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6651: warning: initialization from incompatible pointer type
make[2]: *** [/home/taters/Desktop/ov51x-jpeg-1.5.9/ov51x-jpeg-core.o] Error 1
make[1]: *** [_module_/home/taters/Desktop/ov51x-jpeg-1.5.9] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-27-generic'
make: *** [all] Error 2


I'm using lucid, this is the first time I've tried installing this on the updated system, but I've used it before on 9.04 and back. Any advice on this is greatly apreciated. I read through this entire thread, and while I saw a few stabs at this problem, It's always been in relation to skype, and I could care less if skype works with it. I will humbly take a link to another thread in this forum that I've overlooked though, if someone finds one.

Thanks in advance guys

*EDIT* I should add that i've tried updating the headers, and they're updated to the most recent, so I'm utterly confused as to why this isn't working, it used to be so simple...

---

### Post by Jose Catre-Vandis on 2011-01-05
@ taters

I am surprised that your webcam doesn't "just work" now? (without the need for the ov51 compilation)

What is it? (product/model/serial etc)

What is the output from **lsusb**?

What is the output from **dmesg | tail** when you plug it in?

---

### Post by arafey on 2011-02-02
So I followed some of the steps on the past two pages and now my eyetoy is no longer recognized at all. That is, it doesn't show up under the device list. However, the microphone shows up and works fine.

Info: Running ubuntu 10.10 x64, using a Namtai Eyetoy. 

I had it working with Cheese out of the box and I was following the instructions on the previous pages to get it to work with skype. When I was doing the skype video test the record (red) light would go on for a moment and then go out. 

What should I do to get it working in skype?

Thanks for the help!

---

### Post by masterrob213 on 2011-02-04
now i can't do these 
sudo modprobe i2c_core
sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
sudo insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko

---

### Post by GodsDead on 2011-02-20
Which is the best method to do this form scratch on a ubuntu server install, so i can also view the webcam Via  web interface?

---

### Post by Jose Catre-Vandis on 2011-02-20
> **GodsDead said:**
> Which is the best method to do this form scratch on a ubuntu server install, so I can also view the webcam Via  web interface?

Are you running a gui on the server, or just cli ?

What do you see in dmseg / ls usb when you plug the eyetoy in?

Check back and see my earlier post about command lines for viewing and recording webcam.... 

Can you view the webcam output from a ssh -X session?

I've not done a web interface webcam setup with the eyetoy, so will have to do some research about the best way to go about this...but I think "motion" is in the repos and offers a web interface

---

### Post by targon28 on 2011-04-18
I cant get past the part where you 
wget [http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz)
it says 
--2011-04-18 00:01:21--  [http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz)
Resolving [www.rastageeks.org](www.rastageeks.org)... 213.251.174.188
Connecting to [www.rastageeks.org|213.251.174.188|:80](www.rastageeks.org|213.251.174.188|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-04-18 00:01:32 ERROR 404: Not Found
 
any help?
its like the website that im supposed 2 be downloading it from no longer exists? idk
(im new at this btw, so no complex steps please)

---

### Post by sv87411 on 2011-04-18
I haven't tried the rest, but try this:

wget [http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.9.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.9.tar.gz)

The driver name has changed.

---

### Post by Jose Catre-Vandis on 2011-04-19
Also, that's not the way to get it to work now. Read backwards through the thread....

---

### Post by littleslayer15 on 2011-11-21
> **targon28 said:**
> I cant get past the part where you 
wget [http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz)
it says 
--2011-04-18 00:01:21--  [http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz)
Resolving [www.rastageeks.org](www.rastageeks.org)... 213.251.174.188
Connecting to [www.rastageeks.org|213.251.174.188|:80](www.rastageeks.org|213.251.174.188|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-04-18 00:01:32 ERROR 404: Not Found
 
any help?
its like the website that im supposed 2 be downloading it from no longer exists? idk
(im new at this btw, so no complex steps please)

its the same for me and also I am not very good at Linux either

---

### Post by casearis on 2012-06-07
> **Josh1 said:**
> Welcome to my second guide, "Howto: Get Eyetoy Webcam working for Ubuntu". **This guide cannot be copied, or ripped, but instead just link to this post if you want to tell people about it, thanks. This way when I update this post, everyone always has the latest version!**

[CENTER][B][COLOR="Red"][SIZE="4"]Before you do anything, you are required to have an Eyetoy Webcam, here is a picture:
[IMG]http://images.google.com.au/images?q=tbn:4puQV2ht5j__nM:http://analogik.com/_images/pic_eyetoy_camera.jpg[/IMG][/SIZE][/COLOR][/B][/CENTER]

**Step 1: Inserting the Eyetoy and checking if it is detected by Ubuntu.**
First, plug in the USB into the USB slot, and enter Device Manager (System>Administration>Device Manager).
Scroll down, and see if the Eyetoy was detected by Ubuntu. It should look something like [this]("http://i100.photobucket.com/albums/m4/jtaylor231/devicemanager.png").

**Step 2: Downloading and Installing the drivers needed.**
Load Terminal (Applications>Accesories>Terminal) and type in these commands:

```

sudo apt-get install build-essential linux-headers-`uname -r`

```
This will download and install the things needed to install the drivers. It will also download and install the headers for the kernel you are using.

```

wget http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz

```
This will begin to download the driver. Make sure you save it into your **home directory.**

Now, type in the following commands:
```
tar -xvf ov51x-jpeg-0.5.4.tar.gz
cd ov51x-jpeg-0.5.4
```
This will enter the directory for the drivers.

Now, lets install the drivers:
```

sudo make install
sudo modprobe videodev
sudo modprobe i2c_core
sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
sudo insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko

```
Type these in 1 line at a time!.

Now, to see if it worked, type into terminal:
```
sudo apt-get install xawtv
```
This will install "xawtv" where you can view the webcam, and see if it was working.
Here is mine (note that I am mucking around with settings, so the hue and stuff is mucked up so its brighter then it really is:
[http://i100.photobucket.com/albums/m4/jtaylor231/xawtv.png](http://i100.photobucket.com/albums/m4/jtaylor231/xawtv.png)

**[CENTER]If anyone has the sound working, please PM me ASAP.[/CENTER]**
Having problems with 
wget [http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.0.0.tar.gz)

404 not found error.... pls update.....

---

### Post by Jose Catre-Vandis on 2012-06-09
@ caesaris

[http://ubuntuforums.org/showpost.php?p=10695228&postcount=156](http://ubuntuforums.org/showpost.php?p=10695228&postcount=156)

---

### Post by patman1607 on 2013-04-05
[SIZE=2]Hello@all

i tried to install the sony eye toy webcam on my ubuntu server 12.04 to use with zoneminder.
i downloaded the newfiles from[/SIZE] [LEFT][COLOR=#000000][FONT=Ubuntu Mono]http://www.rastageeks.org/downloads/ov51x-jpeg/ [FONT=arial][SIZE=2]and i allready unpack.
i put 
[/SIZE][/FONT][/FONT][/COLOR][/LEFT]> root@server:~/ov51x-jpeg-1.5.9# make install[LEFT][SIZE=2]
[FONT=arial][COLOR=#000000] in the terminal and the output was: [/COLOR][/FONT]
[/SIZE][/LEFT]> make: *** Keine Regel, um »install« zu erstellen.  Schluss.
which rules i have to add to go on with the install?

lsusb output: 
> Bus 004 Device 005: ID 054c:0155 Sony Corp. 

---

### Post by Merrattic on 2013-08-31
Seems that with 12.04 and updates to .2 and .3 the kernel has taken a step backwards and no longer enables the eyetoy. The gspca_ov519 module loads and finds the eyetoy, then craps out when detecting sensors. I have raised a bug on this but not had a response yet.

---

### Post by Merrattic on 2013-10-15
Resolved!
 Not a software bug as such, turned out to be the Intel xHCI mode  setting in the bios for USB for my Asus Z87M-PLUS motherboard. Default  setting was Smart Mode. This made all usb ports usb 3.0 and/or "better"  than 2.0, meaning my webcmas wouldn't play nicely. Changing the bios  setting to Disabled saw the camera fire up instantly, along with routine  connection of my DVB USB stick.
 Other option to try is Auto, and EHCI Hand Off to Enabled

---

