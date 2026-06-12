---
title: "USB device error Hardy 8.04 Server"
date: 2008-05-22
forum: Server Platforms
---

### Post by sderrick on 2008-05-22
I am using a usb acquisition device with its own usb driver. 

Compiled and run on 8.04 Desktop it works fine.

Run on 8.04 server I am getting an error when calling usb_submit_urb

init_completion (&dev->write_finished);
atomic_set (&dev->write_busy, 1);
retval = usb_submit_urb(dev->write_urb[ep], GFP_KERNEL);
if (retval) {
	atomic_set (&dev->write_busy, 0);
	err("%s - failed submitting write urb, error %d",
    		__FUNCTION__, retval);			
} 

usb_submit_urb is returning EINVAL?? (error code 22)

The driver loads fine, it does complain about tainted kernel because its compiled with the desktop headers.
When I plug in the device it is recognized

But when I call into the driver to write to the device, its a bad thing!

any ideas?

thanks,

Scott

---

### Post by windependence on 2008-05-22
Are you in the device directory? If you are (try pwd in the terminal) try switching to another directory and then try to acces the device. You may be making the device appear to be busy because you are currently in it.


-Tim

---

### Post by sderrick on 2008-05-22
As soon as I types this I wondered why I didn't use the server headers to compile the drive. 

I downloaded them, recompiled the driver and I'm back in business! :KS

sorry for the false alarm and useless chatter.

Scott

---

