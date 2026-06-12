---
title: "My Ratel is down"
date: 2007-07-20
forum: System76 Support
---

### Post by Paulr-55 on 2007-07-20
It boots to a grub prompt.

I have no idea what to do here.

I have not fooled with any conf. files.

Paul

*Update*

It turns out to have been a flaky hard drive (WD 80g SATA). System76 has sent me a replacement drive. Tom was very helpful in diagnosing this strange crash.

Paul Randall

---

### Post by Paulr-55 on 2007-07-21
I power up, get the Asus splash screen, then it goes straight to grub> prompt.

I booted from an old Ubuntu live CD but I really am lost as to what to look for.

Can anyone please offer a suggestion?

Thanks

---

### Post by Paulr-55 on 2007-07-23
Well, I spent some time trying to learn what could be done with a GRUB> prompt (and I thought the bash shell is cryptic?) and came to the determination (possible erroneously) that grub can't find (hd0,0). I thought -oh crud- my drive is crashed.

But I clean installed Feisty with no problem and I am up and running again. Though I lost all my tweaks and desktop customizations and firefox add-ons etc.

Friday morning I boot up - everything is fine. Friday evening I power up - dead in the water. What does that mean?

---

### Post by thomasaaron on 2007-07-23
Right now, I am at the Ubuntu Live convention in Portland.
Please contact me via support[at]system76[dot]com.

We'll get it taken care of.

Best,
Tom

---

### Post by Paulr-55 on 2007-08-02
Tom,

It's a week later and my box is down again. Update Manager froze with an empty window frame after clicking the notification icon.

I closed firefox and attempted to open a terminal but found no programs would start at all. I hit ctl-alt-backspace to restart X and it went down. X is broken I guess( from the log--)

(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): *** Aborting ***

etc.

Fatal sever error:
no screens found

I snapped some photos of the monitor if that may help:

[http://s99.photobucket.com/albums/l313/marxalot/?action=view&current=00001.jpg]("http://s99.photobucket.com/albums/l313/marxalot/?action=view&current=00001.jpg")
[http://s99.photobucket.com/albums/l313/marxalot/?action=view&current=00002.jpg]("http://s99.photobucket.com/albums/l313/marxalot/?action=view&current=00002.jpg")
[http://s99.photobucket.com/albums/l313/marxalot/?action=view&current=00003.jpg]("http://s99.photobucket.com/albums/l313/marxalot/?action=view&current=00003.jpg")

I tried to call support line but can't get an answer even though it is after 8 mountain time.

I need help please. My in warranty machine keeps dropping dead.

Thank you, Paul

---

### Post by Paulr-55 on 2007-08-02
I have attempted:

sudo dpkg-reconfigure xserver-xorg

but it appears to have crashed in the middle of the process (error messages printed in strange places on the text screen.

I restarted with:

sudo /etc/init.d/gdm restart

and X let me log in but left me crashed in a graphical screen with no panels and a graphical terminal window reading:

"There was an error creating the child process for this terminal"

Mouse is frozen - dead.

I restart X to the same effect.

---

### Post by thomasaaron on 2007-08-02
OK, per our phone conversation, I think that nvidia-glx is hosed. Please try the following steps:

1. Make sure the computer is plugged into the Internet.
2. Turn it on and let it boot to the prompt.
3. Try running: sudo apt-get install nvidia-glx
*If you get errors with step 3, you are not yet connected to the Internet. Try: sudo ifup eth0   Hopefully, this will get you online. Then try step 3 again.
4. Once you succeed with step 3, enter this command:
sudo nvidia-glx-config enable
5. Now we want to run: sudo dpkg-reconfigure xserver-xorg
*Use default settings for pretty much everything, except: you will want to select "nvidia" as the driver; select ALL possible screen resolutions; select "Advanced" when you get to it. Everything else should be default.
6. We need to ensure that your xorg.conf file is correctly configured for nvidia. So enter this command: sudo nano /etc/X11/xorg.conf
*Find the line for the video driver and make sure it says nvidia. It should look something like this:
```
Section "Device"
	Identifier	"blah.blah.blah"
	Driver		"nvidia"
```
7. Once you've made that change (if it needs it), hit CTRL-X, then hit "Y", then press enter.

Now try rebooting the machine.
If X fails again, give me a call.

Best,
TOm

---

### Post by Paulr-55 on 2007-08-02
Tom,

I got as far as dpkg-reconfigure xserver-xorg which crashed at the screen depth page after I selected the default of 24.

Here is a photo of that error which seems to repeat every few minutes or so:

[http://s99.photobucket.com/albums/l313/marxalot/?action=view&current=00004.jpg]("http://s99.photobucket.com/albums/l313/marxalot/?action=view&current=00004.jpg")

I note that /etc/X11/xorg.conf shows that Device - driver is "nvidia"

I restart and get the same broken-X machine.

Paul

---

