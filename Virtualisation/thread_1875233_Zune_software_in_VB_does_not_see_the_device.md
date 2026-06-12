---
title: "Zune software in VB does not see the device"
date: 2011-11-04
forum: Virtualisation
---

### Post by mystmaiden on 2011-11-04
I'm running Ubuntu Lucid with Virtualbox installed (Windows XP). I struggled at first getting the zune software to installed but it finally worked. Unfortunately, even though the usb drop down at the bottom of the screen shows the zune, the zune software says I need to connect a device. I tried unplugging it while vbox was running and plugging it in again, same result. Am I missing something? I got the impression that other folks had gotten vbox/zune combo working. The software does see my music.
The zune is 4gb model 1124

thanks for any help,

mystmaiden

---

### Post by CharlesA on 2011-11-04
Are you using the version of vbox from the virtualbox website?

If so, do you have the extension pack installed?

---

### Post by mystmaiden on 2011-11-04
> **CharlesA said:**
> Are you using the version of vbox from the virtualbox website?

If so, do you have the extension pack installed?

Thanks for the reply, CharlesA
I used the one in synaptic and installed the guest additions. Should I have used the one on the vbox website?

---

### Post by CharlesA on 2011-11-04
> **mystmaiden said:**
> Thanks for the reply, CharlesA
I used the one in synaptic and installed the guest additions. Should I have used the one on the vbox website?
Yeah, the one in the repos doesn't support USB.

---

### Post by mystmaiden on 2011-11-05
Thanks I had read that back in an older post but had it in my head that changed when they changed the free/nonfree thing. 

I'll be so glad to get the zune working, its a much better player than the one I use now.

Thanks again

---

### Post by CharlesA on 2011-11-05
> **mystmaiden said:**
> Thanks I had read that back in an older post but had it in my head that changed when they changed the free/nonfree thing. 

I'll be so glad to get the zune working, its a much better player than the one I use now.

Thanks again
Just be sure to install the extension pack since that is what enables USB.

---

### Post by mystmaiden on 2011-11-05
Thanks. I've installed vbox and the extensions but I'm still getting the same result. Do I need to add a usb filter? Honestly, reading the manual, the information on the usb filters seems pretty sketchy to me because it doesn't give any examples.

```
$ VBoxManage list usbfilters
Global USB Device Filters:

<none>


```

---

### Post by CharlesA on 2011-11-05
Yeah, you have to add a usb filter. It might be easier to just use the GUI to do that though.

---

### Post by mystmaiden on 2011-11-07
well, I got it all set up and it worked once but only once. I'm not sure what to try now.

---

### Post by CharlesA on 2011-11-07
> **mystmaiden said:**
> well, I got it all set up and it worked once but only once. I'm not sure what to try now.
Not sure what else to do either.

I don't have a Zune, but I have not had any problems with USB devices. :(

---

### Post by haqking on 2011-11-07
have you selected it from the devices menu to force a dismount from it in the host ?

also make sure you are in the vboxusers group which you should be as it worked once already.

---

### Post by mystmaiden on 2011-11-07
Thank you for the reply. 
I've selected it from the menu, but if its forcing a dismount from the host should the zune device still show on my Ubuntu desktop? (Because it does)

All is well with users and groups

mystmaiden

---

### Post by Ken Mick on 2011-11-09
Hi, This my first post and I wanted to let you know that I just installed VBox on Ubuntu 11.10 then loaded Zune software in it. I love the Zune and hated to let it go when switching to Linux. 
As others have said you need to get the Extension Package and then add vboxusers as user of that machine. I ended up going to [http://www.webupd8.org/2011/02/get-your-usb-drives-to-work-with.html](http://www.webupd8.org/2011/02/get-your-usb-drives-to-work-with.html) and using terminal. That was the tough part. When the reboot was complete and I plugged the Zune in I had to right click on the USB icon on the VB right hand bottom corner, it gave me the option of the devices, I selected Zune and Windows immediatly recognized the hardware.
Yes it can be done!

---

