---
title: "Windows 7 install on a Windows 8 machine"
date: 2014-09-10
forum: Windows
---

### Post by user1397 on 2014-09-10
I have an acer aspire v5-552g-x852 laptop and it originally came with windows 8.  I still had a copy of windows 7 and since I didn't particularly like the metro interface of 8 I decided to install windows 7 instead.  

I backed up win8 to a usb so worst case scenario I can reinstall it.

I installed win7 successfully, and through some google searching, found an alternate driver for wifi and a couple other things.  The win8 drivers from the acer site worked for a couple things too (note: the acer support site for this model only includes win8 drivers, no win7 drivers).

Anyway, I'm getting closer to my question.  I looked in device manager to see if it has any missing drivers, and there's 3 (I attached a screenshot).  One is for bluetooth (which I'm not concerned about since I don't use that feature) and the other two I'm not sure about.  One is called "SM Bus Controller" and the other is "USB Controller".  Windows can't automatically find drivers for them, and I don't see anything on the acer website for these either.

Is it bad to not have these drivers installed?  SM Bus from the little research I did seems fairly important.  And I'm not sure what exactly the USB controller entails as far as functionality.

Thanks in advance.

---

### Post by Tar_Ni on 2014-09-10
SM BUS (System Management Bus) is basically a chipset driver for your motherboard. You usually have a default Windows driver but if you want, you can install the manifacturer driver. Since you are using a Windows 8 era laptop, I recommend that you get it for Windows 7 if available, because the OS doesn't support your hardware out-of-the-box.

Just use DriverMax, it scans your computer and tells you what driver are available for your hardware and offer you to install or update them right there. A great tool for Windows and it's free.

[http://www.drivermax.com/](http://www.drivermax.com/)

---

### Post by user1397 on 2014-09-10
> **Tar_Ni said:**
> SM BUS (System Management Bus) is basically a chipset driver for your motherboard. You usually have a default Windows driver but if you want, you can install the manifacturer driver. Since you are using a Windows 8 era laptop, I recommend that you get it for Windows 7 if available, because the OS doesn't support your hardware out-of-the-box.

Just use DriverMax, it scans your computer and tells you what driver are available for your hardware and offer you to install or update them right there. A great tool for Windows and it's free.

[http://www.drivermax.com/](http://www.drivermax.com/)Thank you for the reply and the information.  

I tried using drivermax, but it requires me to create an account and it seems like its function is very limited for the free edition, and I'm definitely not about to pay for the "pro" version.  

Any other suggestions?

---

### Post by Tar_Ni on 2014-09-11
It requires  to create an account which is not unusual for free editions these days. The free edition has a lot to offer, as I said it scans your hardware for drivers found and updates available. You can then choose to install them if you wish. It's very useful. Searching for drivers can be very time consumming, this tool saves me a lot of time. The pro edition basically add an auto-updater and a ''high priority download''. This can be interesting for hardcore gamers or inexperienced users but unnecessery for people who just want to find drivers and install them.

I suggest you to compare between the free and pro edition and see by yourself: [http://www.drivermax.com/driver/buypro.php](http://www.drivermax.com/driver/buypro.php)

I recommend DriverMax before any other because it's approved by Microsoft and gets the drivers directly from the manifacturers, so there is no risk of infecting your computer with a dubious software.

---

### Post by user1397 on 2014-09-11
> **Tar_Ni said:**
> It requires  to create an account which is not unusual for free editions these days. The free edition has a lot to offer, as I said it scans your hardware for drivers found and updates available. You can then choose to install them if you wish. It's very useful. Searching for drivers can be very time consumming, this tool saves me a lot of time. The pro edition basically add an auto-updater and a ''high priority download''. This can be interesting for hardcore gamers or inexperienced users but unnecessery for people who just want to find drivers and install them.

I suggest you to compare between the free and pro edition and see by yourself: [http://www.drivermax.com/driver/buypro.php](http://www.drivermax.com/driver/buypro.php)

I recommend DriverMax before any other because it's approved by Microsoft and gets the drivers directly from the manifacturers, so there is no risk of infecting your computer with a dubious software.
I see, well thank you for your advice, I'll try it again tonight.

---

### Post by Sasha_Aderolop on 2014-10-27
please read next good article about your question - [http://bit](http://bit)[dot]ly/11mbSxe

---

