---
title: "My Impressions on System76 Gazelle Professional"
date: 2011-07-25
forum: The Cafe
---

### Post by nerdy_kid on 2011-07-25
Hi everyone, I thought I would share my experience with my new Gazelle Professional :)

I needed a new laptop mainly for virtualization, I run a small little business doing tech support and my Core 2 Duo @ 1.4GHZ wasn't quite fast enough for me.  I was comparing a Dell XPS17 with System76's Gazelle Professional, and after hearing about overheating with the XPS, I decided to go the System76 route.

A few days (!) after my order the laptop was shipped.
It came well packaged, along with a laptop bag (which I can't remember ordering, but maybe they always send a bag), the charger, two "Powered by Ubuntu" stickers, a HDMI to VGA converter, and a rather cheap looking system76 branded flyer explaining where to get support.  The laptop itself is quite impressive, it is quite wide, about 15 inches -- so wide that they added a number pad to the right of the standard keyboard.  The laptop shell is a slightly textured plastic, a nice touch in my opinion.  The plastic cased Dells that I have used feel very cheap; this laptop does not feel cheap at all.  It is fairly light imo, given it's size, but it feels quite sturdy.  The screen looks amazing, everything is crystal clear, and the LED backlight gets quite bright.  The backlight fades in and out which is nice, I'm used to the jerky backlight dimming on my last laptop.  
My main complaint is the touchpad.  The touchpad itself is quite nice, it is indented into the actual laptop case, giving a very consistent look.  However, sandwhiched between the left and right touchpad buttons, there is the fingerprint reader.  This is a terrible layout in my opinion.  I use the touchpad with my index finger doing moving the cursor, and my thumb resting on the left mouse button.  On my last laptop, all I had to do is press down with the joint in my thumb to right click.  On this, I pretty much have to shift my entire hand to hit the right touchpad button.  I would have put the fingerprint reader probably in the left corner of the laptop, not between the touchpad buttons.  The issue can be worked around however -- the touchpad is multitouch sensitive, so I can just tab two fingers to right click, but I would far rather be able to reach the right touchpad button easier.  
Another thing I would have changed is the location of the microphone.  The mic is currently located directly above the top right corner of the touchpad.  I think this is a poor design because as I type, my palm sometimes hits the mic, making talking and typing difficult.  Also, perhaps I'm being a little paranoid, but I can't help but think that oil from my hands and dirt is going to get down there.  I would have put it in the laptop lid by the webcam.

Now, onto how well Ubuntu behaves:

On first boot(after finishing the Ubuntu setup), I immediately noticed the missing plymouth, which I was expecting.  This is a really easy thing to fix, and I wonder why the System76 driver doesn't do it. (See [here]("http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/") for how I fixed it) 
The fingerprint reader doesn't work in 11.04, but this is a known issue to be fixed in 11.10.  
I turned the webcam off via the hardware hotkey, and had to reboot to turn it back on, but no big deal. 
There is a hotkey to turn off the LCD screen, which unfortunately only works for about one second.  
The biggest thing in my opinion, is the fact that the i7 Turbo Boost is NOT enabled by default, which I was horrified about.  In order to enable it, I had to append "msr" (without quotes) to /etc/modules and reboot (or do sudo modprobe msr instead of rebooting)  This I think /really/ needs to be done by the System76 driver.  I'm going to report this and the plymouth issue as bugs in the driver.

I am having a little trouble with one of the USB3 ports, details [here]("http://ubuntuforums.org/showthread.php?p=11086029#post11086029"), but hopefully that will be resolved soon.

Other then that, Ubuntu is working great, I have noticed a little trouble when I try to pause/play music via the hardware hotkey (it sometimes takes two tries) but maybe that is me not pressing keys hard enough.  I also had a little trouble with pulseaudio crashing, but that's not at all system76's fault.  

The laptop runs cool, even under heavy load, which impressed me greatly.  My old laptop used to heat up almost to the point that it hurt to let it rest on my lap too long.  Granted I have used this laptop mostly on a flat surface, but it still runs very cool, with fans quieting down seconds after a resume of idling. 

So in review, I like this laptop a lot, with it's major flaw in my opinion being the location of the fingerprint reader.  
I would recommend this as a great alternative to Dell.

---

### Post by isaacj87 on 2011-07-25
I have an older Pangolin Performance (panp4n) and can agree with your complaints. The mic is located in the space between the space bar and touchpad. My fingerprint reader is also wedged between the left and right trackpad buttons. The build quality on mine is decidedly poor. It's very plastic-y and the body bends in multiple locations. Also, the fan randomly goes haywire.

However, I'm very impressed with their customer support. My fiancee lost a key from the keyboard (don't ask me how...) and years later, they were more than willing to send me a replacement. It was quick too!

Oh, by the way, it seems that Fedora 15 detects and allows me to record a print, but every time I try to log in with the FP reader, it never works.

---

