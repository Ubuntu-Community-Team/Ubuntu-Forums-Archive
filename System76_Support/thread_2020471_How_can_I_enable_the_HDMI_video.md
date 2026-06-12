---
title: "How can I enable the HDMI video"
date: 2012-07-08
forum: System76 Support
---

### Post by savoym on 2012-07-08
I have a Sony 40" HDMI TV and I connected my Bonobo laptop to it via the HDMI port but I could find the signal. Do I have to do something to enable the HDMI video?  After searching within this forum and google I could only find how to enable the AUDIO and NOT the video.

Any help/direction would be appreciated.

Regards.

---

### Post by Carborundum on 2012-07-08
In Ubuntu I have to go to **System Settings > Displays** for my GazP7 to recognize my TV, connected via HDMI. Don't know what the Lubuntu equivalent would be.

---

### Post by savoym on 2012-07-08
Thanks for the quick reply.  I'll give it a try.

---

### Post by 3Miro on 2012-07-08
IIRC Bonobo comes with Nvidia video card. If so, then you can use the Nvidia-Settins look that should be installed by the Nvidia driver. In fact, this is the correct way to do it for the proprietary Nvidia driver, other tools will not work properly.

If I am wrong and Bonobo your doesn't come with Nvidia, then you should use some tool available for your Desktop Environment. Gnome 3 has the Display Settings and XFCE has a Display setting section in their settings. I think KDE should have display section in KDE System Settings. I don't know about LXDE, LXDE comes with very limited settings tools by default, you may have to install something extra.

---

### Post by Newbunto on 2012-07-10
I have a Bonobo and it comes with dedicated nVidia graphics. I don't know whether all Bonobo laptops do however.

If you boot up from scratch with the TV connected it should enable it automatically. However I have experienced oddities with the resolution on the laptop in that scenario (which are easy to correct - if you care).

As a previous reply said, use

[FONT=Courier New][SIZE=3]nvidia-settings[/SIZE][/FONT]

to play around with the configuration. You can have the external monitor display exactly what's on the screen (as if connected to a projector - presentation mode, if you like) or you can have the two displays combined into one large desktop (share broker mode, if you like) or you can just disable the laptop display (laptop as desktop replacement when at the desk).

As long as you don't save the settings from nvidia-settings, you can run it as the logged in user, rather than running it as root. (Saving the settings doesn't make a lot of sense most of the time.)

I've found nvidia-settings to be a bit quirky i.e. you have to work out the right set of changes to make and that can take some time the first time you use it.

There's no doubt that Windows Fn+whatever is more user-friendly.

Edit: Ubuntu 11.10 or 12.04 this is how it works. For an earlier version YMMV.

---

