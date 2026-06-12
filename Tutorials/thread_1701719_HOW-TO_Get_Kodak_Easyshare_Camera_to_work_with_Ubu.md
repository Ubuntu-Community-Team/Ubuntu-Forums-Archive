---
title: "HOW-TO: Get Kodak Easyshare Camera to work with Ubuntu"
date: 2011-03-06
forum: Tutorials
---

### Post by HazelIced on 2011-03-06
This is a short tutorial for anybody having problems with a Kodak Easyshare Camera.

I'm no master at this, but after looking for different things to make my M530 Kodak Easyshare camera work with Ubuntu, I finally got it.
So I thought I might as well post it all to show anybody else who might have problems how to use it.

This has worked with my M530 and Ubuntu 10.04 64bit. Not sure about other Kodaks or other Easyshare-cameras.

You should have libgphoto2 installed.

1) Plug the camera into the USB, turn it on.
2) If nothing happens, open up the terminal.

                ```
lsusb
```

Write down the Device ID number on the line that says "Kodak Co."

3) On the terminal...

             ```
sudo sh -c '/usr/lib/libgphoto2/print-camera-list udev-rules mode 0660 group plugdev > /etc/udev/rules.d/45-libgphoto2.rules'
```

4) Run....
            ```
sudo gedit /etc/udev/rules.d/45-libgphoto2.rules
```

5) Go to the bottom of the file. Before the end where it says: LABEL="libgphoto2_rules_end"
Add
            ```
ATTRS{idVendor}=="VENDORID", ATTRS{idProduct}=="PRODUCTID", MODE="0660", GROUP="plugdev"
```
         where VENDORID and PRODUCTID are in the device ID number, shown as VENDORID : PRODUCTID.

6) Save the rules file.
7) Reboot the computer.
8 ) Turn on camera. Everything should work.

Hope this helps some people!

---

### Post by luisjaime on 2011-12-29
Thanks a lot, now I've photos.  A question: ¿can this device play rolle of webcam?

---

### Post by ceanes on 2012-04-16
Thank you very much !!!!  as a owner of one Kodak K990 i got it recognized but  barely get some pics transfer to the pc, 3 out of 10 usually ,
but now i can copy the entire file DCIM . I have been googling for days before get across this tutorial ,
I think it is the one solution on the net until now. :lolflag:):P:p:p:p

---

### Post by buntujunkie on 2012-07-13
> **HazelIced said:**
> **[Re: HOW-TO: Get Kodak Easyshare Camera to work with Ubuntu]("http://www.squidoo.com/nikond3200review")**
This is a short tutorial for anybody having problems with a Kodak Easyshare Camera.

I'm no master at this, but after looking for different things to make my M530 Kodak Easyshare camera work with Ubuntu, I finally got it.
So I thought I might as well post it all to show anybody else who might have problems how to use it.
Thanks, trying to make it work on my ubuntu 12.04. Does it get detected as a mass storage device or as a camera?

---

