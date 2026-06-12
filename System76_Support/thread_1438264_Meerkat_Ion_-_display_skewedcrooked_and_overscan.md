---
title: "Meerkat Ion - display skewed/crooked and overscan"
date: 2010-03-24
forum: System76 Support
---

### Post by Jason Peters on 2010-03-24
When I connected my new Meerkat Ion to my Sony SXRD LCos rear projection TV (KDS-50A2000), the Karmic desktop displayed was slightly larger than the TV's display, and slightly crooked/skewed.  I made no changes to the factory install, and it came with the nvidia 185 drivers out of the box.  The attached poorly taken photo should at least give an idea.  

Since then I've tried several potential fixes including installing the 190 drivers per: 

[http://ubuntuforums.org/showthread.php?t=1335841&highlight=meerkat+ion](http://ubuntuforums.org/showthread.php?t=1335841&highlight=meerkat+ion)

and, installing the 195 drivers, per:

[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

The 190 install via Hardware Drivers and synaptic failed with a 'SystemError: install Archives() failed.'  The 195 install was successful, but the display is still overscanned and crooked.

I may be able to correct the overscan with the overscan compensation slider in the nvidia x server settings, but until I can correct the 'skew' that seems to be a moot point.

My next step will probably be a clean Karmic install.  Any suggestions would be welcome.

---

### Post by isantop on 2010-03-24
I'm not 100% familiar with rear-projection TV's, but does it have any controls that you can use to adjust the picture fit? I have also seen some monitors that can attempt to auto-adjust the display size to fit it perfectly on the screen. In addition, thomasaaron can probably help as well.

---

### Post by Jason Peters on 2010-03-24
I did dig through the Sony's menus quite a few times.  Not much there.  I've seen monitors like you describe too, but the TV appears to have only the very basic, Normal, Full, Wide, Zoom settings--nothing geometry related.  I haven't become desperate enough to try the service menu yet.  Thanks though.

---

### Post by Jason Peters on 2010-03-25
Update:  I just did a clean install of Ubuntu 9.10, and the problem is the same--still skewed and overscanned.  I followed the system76 knowledge base's instructions to restore a desktop.  Installed the nvidia 185 drivers.  The only hiccup came when I tried to launch System | Administration | system76 Driver, which produced an "Unsupported" error.  I logged that with the launchpad.net site, but I don't think it has any relevance to the video.  I also tried a different HDMI cable and my TV's other HDMI port, but the problem remained.  

What would be the best way to approach nvidia or other nvidia driver authority about this?

---

### Post by isantop on 2010-03-25
You might experiment with those settings; one of them may be stretching out the image. On most TV pictures, this is desirable, but it may be cutting out parts of the screen in Ubuntu.

What resolution does the TV support (1080, 720, etc.)? Also, what resolution is Ubuntu configured to use (Go to System > Preferences > Monitors and click on the TV in the upper section to find out).

---

### Post by Jason Peters on 2010-03-25
The settings on the TV are limited to things like Normal, Full, Zoom, Wide Zoom.  There is a couple settings to make the image -1, or -2, which basically zooms in 1 or 2 pixels.  The nvidia settings offer the 'overscan compensation' slider, which would be helpful, if not for the biggest problem--the image being crooked.  If only there were controls on either device to rotate the image, like some monitors as you mentioned, this might be resolved.  Neither appears to have that functionality.  

The TV 1080p, and the nvidia x server utility indicates that it is set for 1920 x 1080 automatically, and recognizes the monitor as a Sony TV.

---

### Post by PatrickVogeli on 2010-03-25
maybe this is a wider issue than one might thing. I'm having the same problem using ubuntu on 2 different machines: one is a desktop with Nvidia 9600 and the other is a laptop with intel x4500. A friend of mine has another laptop and is seeing the same issue with windows 7..

---

### Post by Paul Stone on 2010-03-26
Is it possible that you have a general skew problem with your set, but that you only notice it when the Ubuntu desktop is being displayed?

If so, this may help.

[http://www.avsforum.com/avs-vb/showthread.php?p=8290925&&#post8290925](http://www.avsforum.com/avs-vb/showthread.php?p=8290925&&#post8290925)

Linked to from here:

[http://www.avsforum.com/avs-vb/showthread.php?t=702606](http://www.avsforum.com/avs-vb/showthread.php?t=702606)

Don't miss this part:
> I would strongly encourage use of a calibration pattern to verify that a set truly exhibits rotation prior to making an adjustment. It can be hard to eyeball - especially in the vertical. You may think you have a rotation, but only have a tilt along 1 side/axis. If you do a rotation adjustment in this case, you may fix the apparent tilt, but rotate the other sides or axis out of parallel.

---

### Post by Paul Stone on 2010-03-26
You can get a calibration DVD to display a test pattern to help determine whether you have a general issue with your set's display being skewed/rotated.  Or there might be a test pattern you can download for free and burn to DVD.

---

