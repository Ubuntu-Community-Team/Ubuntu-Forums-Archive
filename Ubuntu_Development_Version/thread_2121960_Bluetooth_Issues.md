---
title: "Bluetooth Issues"
date: 2013-03-03
forum: Ubuntu Development Version
---

### Post by EgoGratis on 2013-03-03
I didn't test it much but why is it only LTS releases give me great bluetooth support for my phone? It was Ubuntu 10.04 that worked and it was not until Ubuntu 12.04 (because some things changed in bluetooth layer) it worked again and in Ubuntu 12.04 (when it was in the +1 forum section) i did reported some bugs and almost all was fixed and it was great experience. Then i updated my laptop to Ubuntu 12.10 and only half of functionality worked for me but i said OK i will wait for Ubuntu 13.04 and just now i tested the support and first i paired the device with Ubuntu then tried to Browse files on phone and Send file to phone and all failed with crashes and no result. 

I didn't bother to try to send file from my phone to Ubuntu and if i remember correctly back in Ubuntu 12.04 bug reports i had to install one package to set personal file sharing over bluetooth and i proposed this would be mentioned in GUI but it was declined. I imagine the same is still true and to be able to send file from device to Ubuntu users has to know it won't work by default. 

What i am trying to say is why is bluetooh support so bad between LTS releases? Why does it brake so badly when it worked almost perfect in Ubuntu 12.04 and it still does on the same PC with the same phone i can pair the device with Ubuntu 12.04 and Browse, Send file and Send file from device to Ubuntu works (user has to set it up manually) without problems.

And then in Ubuntu 13.04 nothing works. What has changed again to brake bluetooth so much i don't understand it. Were some new packages used or what happened? Is it too early in developement cycle and i just have to wait a bit more or is this just the way it is every new release brakes this and bugs has to be reported to fix it?

---

### Post by EgoGratis on 2013-03-23
Pressing Send Files... button for example returns this:

"GDBus.Error:org.openobex:Error.Failed: Unable to request session"

[https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/1148033](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/1148033)

Pressing Browse Files... button does not do anything. Pressing the buttons will only sometimes crash gvfsd-obexftp and it might be this bug:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1060054](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1060054)

Pairing work OK and that is about it. The same mobile phone paired with PC works great on Ubuntu 12.04!

---

### Post by EgoGratis on 2013-04-20
Some things improved in these 3 weeks:

**Browse files:**

Browse files... button inside control panel now opens Nautilus and shows files! Great! 

Quick shortcut in bluetooth appindicator for browse files support still doesn't do anything. This doesn't work ATM.

**Send files from mobile device to PC:**

Send files from mobile phone to PC now works! Great! 

Cons: User has to know it has to manually find Personal File Sharing program inside Dash and open it and enable appropriate option and this isn't mentioned inside bluetooth control panel. I don't know from where exactly should user get the info of what he/she is suppose to do. Ask Ubuntu and is  this really the best we can do? I asked the same question in Ubuntu 12.04 development cycle.

**Send files from PC to **[B]mobile device:

[/B]This still doesn’t work:

[https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/1148033](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/1148033)

---

