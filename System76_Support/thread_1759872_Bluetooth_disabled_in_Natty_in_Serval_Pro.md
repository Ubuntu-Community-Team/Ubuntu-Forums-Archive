---
title: "Bluetooth disabled in Natty in Serval Pro?"
date: 2011-05-16
forum: System76 Support
---

### Post by volkerbradley on 2011-05-16
Just did a fresh install of Natty on the Serp 6.
Am trying to use a Bluetooth mouse.  Bluetooth antenna is turned on by doing Fn-F12.  System76 driver was installed but when I ran it a message said that all drivers where supplied by Ubuntu.
When I open the Bluetooth application,  I see a message that Bluetooth is disabled and a button that states "Turn On Bluetooth".
When I click on that button, nothing happens.
Any ideas on how to debug this issue?
Thanks

---

### Post by isantop on 2011-05-16
This is actually a known issue in Ubuntu 11.04, and it affects bluetooth in many different laptops. There is currently a fix sitting in the proposed updates, and it does fix the problem. The only thing left to do is wait for them to send the update down.

---

### Post by volkerbradley on 2011-05-16
Thank you for your response.

---

### Post by madtownmike1 on 2011-05-17
Possible work-around: I have the same problem on my acer aspire one; for me the problem occurs when I first start the machine. After I log in, I immediately reboot and the bluetooth magically starts working. Not the prettiest solution (reminds me of windoze) but it worked.

---

### Post by volkerbradley on 2011-05-18
I found a workaround in [http://dgwings.com/?p=105](http://dgwings.com/?p=105) which states:

"Open the terminal and type these two commands:
sudo killall bluetoothd
sudo bluetoothd
After doing this, everything will going fine."

In my case I did sudo ps ax | grep bluetooth.  This showed that there were two processes running.  I killed both of these processes.
Then I gave the "sudo bluetoothd" command and then clicked on the Bluetooth icon in the Menu. 
Bluetooth now functions properly on my Serp6 running Natty.

---

### Post by isantop on 2011-05-19
Another variation on a theme:

```
sudo service bluetooth restart
```

This is about the same as the others, though it is only one command, which is nice.

---

### Post by volkerbradley on 2011-05-20
Thank you. Very helpful.

---

### Post by pravesh on 2011-06-06
hi,

i have a dell N5110 laptop. i have installed Ubuntu 11.04 and the Bluetooth is disabled. i have tried all the suggested solutions but in vain.

can anyone help me out?

thanks.

---

### Post by volkerbradley on 2011-06-06
Hi,
I don't have your model laptop but do have bluetooth working on my laptop with Natty installed.
According to the specs published by Dell, Bluetooth is optional on your computer.  Are you sure you have an internal Bluetooth Antenna?
Also on some computers which have the wireless and Bluetooth control switch in the same switch as your computer does, it requires that you turn on Fn-<A> (the antenna button), turn it off and then turn it on again to turn on both antennas.
After you have done that and you are sure that your bluetooth antenna is on, then give the:
sudo service bluetooth restart 
command from your terminal.
Now click on the Bluetooth button in Unity to start the service.
If none of this works, then you might consider buying a Bluetooth USB dongle.  There are lots of them out there.  I have a Jabra 29F and find that it works as soon as I plug it into the USB port.
Let us know what happens.

---

### Post by pravesh on 2011-06-09
hi 

thanks for replying.
i do have bluetooth and it works with windows 7 but not with ubuntu, its disabled.
i have tried your suggestions but i still have the same problem.

should i install the previous version of ubuntu?

---

### Post by volkerbradley on 2011-06-10
I guess you could consider trying Meerkat.  Bluetooth worked flawlessly in that version for me.  So did Compiz and a lot of other things.

---

### Post by coatepec on 2011-06-29
> **volkerbradley said:**
> I found a workaround in [http://dgwings.com/?p=105](http://dgwings.com/?p=105) which states:

"Open the terminal and type these two commands:
sudo killall bluetoothd
sudo bluetoothd
After doing this, everything will going fine."

This worked for me. Thanks.

---

### Post by bica on 2011-08-25
I'm also having the same problem on a Dell XPS l502x machine.
bluetoothd failed to start:

```
bluetoothd[2005]: Bluetooth deamon 4.91
bluetoothd[2005]: src/main.c:parse_config() parsing main.conf
bluetoothd[2005]: src/main.c:parse_config() discovto=0
bluetoothd[2005]: src/main.c:parse_config() pairto=0
bluetoothd[2005]: src/main.c:parse_config() pageto=8192
bluetoothd[2005]: src/main.c:parse_config() name=%h-%d
bluetoothd[2005]: src/main.c:parse_config() class=0x000100
bluetoothd[2005]: src/main.c:parse_config() discov_interval=0
bluetoothd[2005]: src/main.c:parse_config() Key file does not have key 'DeviceID'
bluetoothd[2005]: Unable to get on D-Bus
```

---

### Post by mouhammad88 on 2011-10-09
After a long westing time in complicated tuto and tips , i found an easy magic solution :D look at this : [http://www.edwardcrosby.com/2011/06/17/bluetooth-fix-in-linux-mint-11ubuntu-11-04/](http://www.edwardcrosby.com/2011/06/17/bluetooth-fix-in-linux-mint-11ubuntu-11-04/)

---

### Post by hus787 on 2011-11-09
> **isantop said:**
> Another variation on a theme:

```
sudo service bluetooth restart
```This is about the same as the others, though it is only one command, which is nice.

don't have a bluetooth device around to check if things are working but atleast i got a proper bluetooth icon(rather then a dot) on my system try and got ride of the "Bluetooth is disabled" message in the preference menu.

So, thanks a lot!!!

---

### Post by isantop on 2011-11-09
This issue should have been fixed in an update to 11.04, and is included in 11.10. Bluetooth is now working (mostly) fine.

---

### Post by bica on 2011-11-10
Its look like my problem was not software, but hardware related.
My secondary monitor was not shield enough (probably the power adapter inside) and cause some interference which make the bluetooth (and also my webcam - it looks like affected the usb bus in general) not to work.
After moving away the monitor from the laptop the bluetooth was working.

---

