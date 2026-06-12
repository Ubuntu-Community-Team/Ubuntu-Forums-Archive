---
title: "Virtualbox help"
date: 2010-07-22
forum: Virtualisation
---

### Post by TimEnid on 2010-07-22
recently, i have been having this issue. when i start up w7 in vb, im unable to press my control key to get out of the window. i press it repeatedly, and it wont let me out the box. not only that, but there is my regular mouse pointer, and then there is a frozen one inside the box. the only way to get out of virtualbox is to shut down the os thats running in it. any help?

---

### Post by Drone4four on 2010-07-22
This thread should be posted under [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") not Absolute Beginner Talk. Perhaps a mod can move it for us?

---

### Post by QIII on 2010-07-22
Use RIGHT control.  Do you have guest additions installed?

---

### Post by QIII on 2010-07-22
> **Drone4four said:**
> This thread should be posted under [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") not Absolute Beginner Talk. Perhaps a mod can move it for us?

How about we answer the OP's question and let the moderators make that call?

---

### Post by QIII on 2010-07-22
TimEnid.  I'm on a bus right now on my mobile.  Slow typing.  Did you try documentation at virtualbox.org?

---

### Post by theozzlives on 2010-07-22
> **Drone4four said:**
> This thread should be posted under [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") not Absolute Beginner Talk. Perhaps a mod can move it for us?

If the OP is an absolute beginner, then it belong here. DON'T BE RUDE!

---

### Post by TimEnid on 2010-07-22
sorry for the confusion everyone. i am a beginner in both ubuntu and virtualbox.

thats the thing, i cant get out of the virtualbox by press the right control key. therefore, i cant access the guest additions.

---

### Post by QIII on 2010-07-23
A couple of things to try:

1.  Reinstall VirtualBox.  You never know.  Things happen.  Reinstalling VirtualBox will not get rid of your virtual drive, so you can just add a new machine and point it at that virtual drive again.

2.  Start VirtualBox and start the virtual machine.  But DON'T capture the mouse or keyboard.  (That is, don't click in the guest OS and don't click the pop-up that says you have to capture the mouse.  Just let it start up.)  

Depending on which version you have (OSE or PEUL) and how new it is, you might find a button that says "Devices" in a couple of places.  Select "Devices" and then select Install Guest Additions.

Follow the directions here to complete the installation:

[http://www.virtualbox.org/manual/ch04.html#additions-windows](http://www.virtualbox.org/manual/ch04.html#additions-windows)

---

### Post by TimEnid on 2010-07-24
^^^this did not work for me. I am going to start from scratch. How do i remove the guest os so that its notavailable when i reinstall virtualbox?

---

### Post by TimEnid on 2010-07-24
ok, so i got it back up and running again. everythings fine. but, when i click Guest Additions, nothing happens. I am unable to find a folder that i am trying to share. Any help?

---

### Post by bigboy_pdb on 2010-07-24
For the future, if you have another problem with the host key being detected, you can try changing it in the "Input" tab under File -> Preferences.

When you say that you clicked "Guest Additions", do you mean that you mean that you clicked "Install Guest Additions"? If that's the case, then clicking that button downloads the guest additions CD image if it hasn't been downloaded and mounts the image. Sometimes it gets mounted but the folder doesn't get opened. Just check if the CD is being detected under Windows Explorer (or under the Places menu in Ubuntu). If it is then you can run the setup from there.

---

### Post by TimEnid on 2010-07-24
> **bigboy_pdb said:**
> For the future, if you have another problem with the host key being detected, you can try changing it in the "Input" tab under File -> Preferences.

When you say that you clicked "Guest Additions", do you mean that you mean that you clicked "Install Guest Additions"? If that's the case, then clicking that button downloads the guest additions CD image if it hasn't been downloaded and mounts the image. Sometimes it gets mounted but the folder doesn't get opened. Just check if the CD is being detected under Windows Explorer (or under the Places menu in Ubuntu). If it is then you can run the setup from there.

yes, thats what i mean. i looked in both places and i dont see anything

---

### Post by TimEnid on 2010-07-24
so i went to Devices>cd/dvd devices and vboxguestadditions.iso is checked. But when i click Install Guest Additions, nothing happens.
i followed the directions here, and i see something about Autostart, but i am not sure if its on or off, and how to turn it on or off.
[http://www.virtualbox.org/manual/ch04.html#additions-windows](http://www.virtualbox.org/manual/ch04.html#additions-windows)

---

### Post by TimEnid on 2010-07-24
ok, got everything working. now the issues is, my zune drivers wont install in the virtual os. its a zune hd. i went into device manager to update the driver, but nothing happens. still doesnt work.

---

### Post by bigboy_pdb on 2010-07-25
I'm guessing that your hard drive is a USB drive.

Are you using the open source edition? If you are, [I don't think the open source edition supports USB devices]("http://www.virtualbox.org/wiki/Editions") and you might want to [download the version which includes closed source code]("http://www.virtualbox.org/wiki/Downloads").

---

### Post by TimEnid on 2010-07-25
> **bigboy_pdb said:**
> I'm guessing that your hard drive is a USB drive.

Are you using the open source edition? If you are, [I don't think the open source edition supports USB devices]("http://www.virtualbox.org/wiki/Editions") and you might want to [download the version which includes closed source code]("http://www.virtualbox.org/wiki/Downloads").

i got this to work. now im just trying to see my blackberry and zune. the drivers wont install for either.

---

