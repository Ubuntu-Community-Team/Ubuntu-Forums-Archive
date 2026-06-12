---
title: "Installing Ubuntu Phone on vanilla Aquaris E5 HD"
date: 2015-06-29
forum: Ubuntu Phone and Tablet
---

### Post by seizurebattlerobot on 2015-06-29
Hi, I purchased a vanilla BQ Aquaris E5 HD as soon as I heard that it was going to be the next Ubuntu phone with the hopes of flashing Ubuntu to replace the stock Android OS because I figured the official hardware was going to be unobtainable due to "flash sales", like the E4.5 was.  Now I've got the phone which is capable of running Ubuntu, but I'm having trouble getting the OS installed.

Questions:
* Has anyone else done this or is currently attempting to do this?
* Are there Ubuntu firmware images for this phone out there? (I was surprised I could only find Ubuntu firmware for the Aquaris E4.5, not E5)
* Is there any hope this [1] procedure will work for me?  (Currently it hangs at the bootloader unlock step: "sudo fastboot oem unlock")

[1] [https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/)

---

### Post by seizurebattlerobot on 2015-07-03
Good news, I was able to install the OS relatively easily - here's how I did it:
* Goto [http://www.mibqyyo.com/descargas/2015/06/26/firmware-ubuntu-14-10-r2/](http://www.mibqyyo.com/descargas/2015/06/26/firmware-ubuntu-14-10-r2/) and download the Ubuntu firmware zip (you have to put your phone's serial # in the text box).
* Goto [http://www.mibqyyo.com/descargas/2015/05/22/herramienta-flash-tool-ubuntu/](http://www.mibqyyo.com/descargas/2015/05/22/herramienta-flash-tool-ubuntu/) and download the windows drivers & tools
* Find a windows machine (I tried using Virtualbox under linux, but was unable to get the usb support to detect the phone long enough to flash)
* Extract the firmware and drivers/tools archives on the Windows machine
* Install the "Hard reset" version of the drivers using the supplied install batch file
* Run the flash_tool program in the "Herramienta MTK Flash Tool" directory
* Load the scatter file from the Ubuntu firmware extraction
* Set the dropdown on the flash tool to "Firmware upgrade"
* Disconnect and power off your phone
* Click the Download button (the flash tool is waiting for your phone to attach now)
* Connect your powered off phone to the computer via USB
* If all goes well you should start seeing activity on the flash tool
* The flash operation is complete when you see the green checkbox window
* Turn on your phone and enjoy - the first boot may take longer than normal

My first impressions of Ubuntu phone have been great, congratz to the Ubuntu phone team for making a very cool product.

---

### Post by uzbeka on 2015-12-09
linux tool is available by following link; [http://storage.googleapis.com/otas/2014/Smartphones/Aquaris_E4.5/Ubuntu/Web%20version/Web%20version/KRILIN01A-S15A_BQ_L100EN_1006_150508.zip](http://storage.googleapis.com/otas/2014/Smartphones/Aquaris_E4.5/Ubuntu/Web%20version/Web%20version/KRILIN01A-S15A_BQ_L100EN_1006_150508.zip)

---

