---
title: "System --&gt; Preferences --&gt; Display: gives error message"
date: 2009-12-12
forum: System76 Support
---

### Post by watchpocket on 2009-12-12
When  I navigate to** System --> Preferences --> Display** , I get the following dialogue box: 

"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"

I can choose "yes" or "no". 

 If I choose "no" (the default choice), I get a sort of minimal system "Display Preferences" window that has a few drop-down menus (Resolution, Refresh rate, Rotation), but otherwise says "Monitor: Unknown".

If I choose "yes", the "NVIDIA X Server Settings" window appears, with its several different configuration settings to make / chooose from.

(This NVIDIA window is identical to what appears when I navigate to 
**System --> Administration --> NVIDIA X Server Settings**.)

My question:  Is it normal / okay to be getting this error-message?  Should I be completely unconcerned about it?  Or should it not appear?

I am running Karmic with Gnome on a month-old System76 Wild Dog Performance desktop unit, model wilp6.  My graphics card is the 1 GB nVidia GeForce GTS 250.  Thanks for any help.

---

### Post by marshmallow1304 on 2009-12-12
Yep, this is normal.  I just edit the menus and uncheck Display, for once the NVIDIA driver is installed, Display is useless.

---

### Post by poikiloid on 2009-12-29
I would like to hear from system76 staff on this. I am also experiencing this behavior after upgrading from 9.04 to 9.10. 

I was able to use the "Display" settings window in 9.04. I liked it, as its interface was simple. The options in the nvidia x server gui are more than I want, and I can't even see where to change the resolution from 1280 X 800 to something else.

Is it intentional that system76 computers now use only the x server gui instead of "Display" in karmic, or is something wrong?

Also, possibly related (this is weeks after upgrading), suddenly found that it is hard to get the screen bright. I have to turn it all the way up. I think it was able to get brighter than this before. This was when I tried to open "Display", and found it was no longer working.

Thanks.

---

### Post by robtg on 2009-12-29
This behavior is normal.  Once the nVidia drivers are installed, you should use NVIDA X Server Settings.  

To change the resolution, open the nVidia application and then click on "X Server Display Configuration"  In the panel that appears on the right, click the Resolution drop-down box on the Display tab to choose the resolution you want.

Rob

---

### Post by poikiloid on 2009-12-30
Thanks for your reply Rob.

I'd just like to point out that the nvidia driver was installed long time ago in my jaunty (don't recall why I had done so), and I never got the message from the original post when using the basic "Display". Don't know what changed now to trigger this allegedly expected behavior.

So, if I uninstalled "nvidia-settings" package in synaptic, I could go back to using the "Display" preference screen without incurring any problems?

---

### Post by thomasaaron on 2009-12-30
Yes, marshmallow and robtg are both correct.

They have basically bypassed Sys > Prefs > Display in favor of nvidia-settings.

---

