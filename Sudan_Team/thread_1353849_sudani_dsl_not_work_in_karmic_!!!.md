---
title: "sudani dsl not work in karmic !!!"
date: 2009-12-13
forum: Sudan Team
---

### Post by mhmdfoss on 2009-12-13
my mdsl -sudani zte usb modem- not work in ubuntu 9.10
what can i do to fix it

---

### Post by mhmdfoss on 2009-12-17
[LEFT][INDENT][SIZE=5][COLOR=Black]i am waiting you guys
[/COLOR][/SIZE][SIZE=5][COLOR=Black]please help me if you have the answer:([/COLOR][/SIZE][/INDENT][/LEFT]

---

### Post by zero-n on 2009-12-17
Plug your modem run this command & paste your result here :

```
lsusb
```

---

### Post by mhmdfoss on 2009-12-18
thank you for respone mr.ZERO

this my result

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 05c6:6000 Qualcomm, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by zero-n on 2009-12-18
I have asked you to run **[COLOR="Red"]lsusb[/COLOR]** to know your modem type cause i am using CanarGo not Sudani mDSL.

My result after running lsusb is :

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 16d8:6803 CMOTECH Co., Ltd. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

**[COLOR="Red"]Notice[/COLOR]**: The third result is my CanarGo modem and [**CMOTECH**]("http://www.cmotech.com/") is the manufacturer of the modem & your modem manufacturer is [**Qualcomm**]("http://www.qualcomm.com/") or at least the chip manufacturer.

Your modem driver name is [COLOR="Red"]**ZTE AC8700**[/COLOR] and it  have problems with the new [COLOR="Red"]**Network Manager**[/COLOR] in Karmic koala & this bug have not been assigned to any developer until now so for the mean time the bug can still disturbing us but no problem.

Cause the problem is from Network Manager so your driver is ok but we need another way to access it.

we can [COLOR="Red"]**[Gnome PPP]("http://www.gnomefiles.org/app.php?soft_id=41")**[/COLOR] (modem dialup too)

let's roll:

1- Install **Gnome-PPP** :
```
sudo apt-get install gnome-ppp
```

2- Open **Gnome-PPP** from : Applications >> Internet >> Gnome-PPP

[CENTER][IMG]http://i299.photobucket.com/albums/mm286/zero-n10/Screenshot-GNOMEPPP.png[/IMG][/CENTER]



3- Click **[COLOR="Red"]Setup[/COLOR]**.

[CENTER][img]http://i299.photobucket.com/albums/mm286/zero-n10/Screenshot-Setup.png[/img][/CENTER]


4- Change **[COLOR="Red"]/dev/modem[/COLOR]** to **[COLOR="Red"]/dev/ttyS0[/COLOR]** & click Detect it will recognise your modem automatically.

5- Close this window and enter your username, password and phone number to enjoy surfing again.



**[COLOR="Red"]Sorry[/COLOR]** you need to do one more thing (make it run as Root) **Gnome-ppp** uses **[COLOR="Red"][Wvdial]("http://en.wikipedia.org/wiki/Wvdial")[/COLOR]** and it needs to access it as Root so do the following:

1- Right click on Application menu & select **[COLOR="Red"]Edit Menus[/COLOR]**.

2- From the left select [COLOR="Red"]**Internet**[/COLOR] then select **[COLOR="Red"]Gnome-PPP[/COLOR]** & click properties you will get Launcher properties screen.

[CENTER][IMG]http://i299.photobucket.com/albums/mm286/zero-n10/Screenshot-LauncherProperties.png[/IMG][/CENTER]

3- In Command change it to **[COLOR="Red"]gksudo gnome-ppp[/COLOR]** instead of **[COLOR="Red"]gnome-ppp[/COLOR]**.

[CENTER][IMG]http://i299.photobucket.com/albums/mm286/zero-n10/Screenshot-LauncherProperties-1.png[/IMG][/CENTER]

4- I think after this step you will need to enter the setting again for **Gnome-PPP**.

5- **[COLOR="Red"][SIZE="5"]Done[/SIZE][/COLOR]**.


I hope this will work for you ( Insah2 allah ).



**_Refrences:_**

[**Google Images**]("http://images.google.com/images?hl=en&source=hp&q=zte+modem&gbv=2&aq=f&oq=&aqi=g10"). (so i know it's zte ac8700)
[**Network Manager Not Working with ZTE AC8700**]("http://ubuntuforums.org/showthread.php?p=8489939").
**[Setting up Dial-up connection in Ubuntu]("http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html")**.

---

### Post by mhmdfoss on 2009-12-18
[B]i will try to install gnome-ppp without being online

i think it will work

thank you for your nice and complete report mr ZERO 
[/B]

---

### Post by zero-n on 2009-12-18
Ok

keep us informed

---

### Post by zero-n on 2009-12-18
Another way to do it using just **Wvdial** but it uses terminal:

1- Install Wvdial if you don't have it.
```
sudo apt-get install wvdial
```or install it form Ubuntu CD:

dependices are locate in :
```

[COLOR=Red]**pool/main/w/wvstreams**[/COLOR]

```and wvdial package is located in:
```

[COLOR=Red]**pool/main/w/wvdial**[/COLOR] 

```2- Run Wvdialconf command to detect you modem:
```
sudo wvdialconf
```This will save the configuration in this file **[COLOR=Red]/etc/wvdial.conf[/COLOR]**

3- Edit you file and type your username, password ,phone number & baud rate if you want.
```
sudo gedit /etc/wvdial.conf
```This is my **wvdial.conf** file:

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = yes
ISDN = 0
Modem Type = Analog Modem
Phone = #777
Modem = /dev/ttyUSB0
Username = *******@canar.go
Carrier Check = no
Password = ********
Baud = 9600
```4- Run Wvidal it will automatically look to hte content of wvdial.conf
```
sudo wvdial
```In my case this is the result:
```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Dec 19 05:03:06 2009
--> Pid of pppd: 11883
--> Using interface ppp0
--> pppd: H%&#65533;[08]&#65533;'&#65533;[08]
--> pppd: H%&#65533;[08]&#65533;'&#65533;[08]
--> pppd: H%&#65533;[08]&#65533;'&#65533;[08]
--> pppd: H%&#65533;[08]&#65533;'&#65533;[08]
--> pppd: H%&#65533;[08]&#65533;'&#65533;[08]
--> local  IP address 41.202.185.208
--> pppd: H%&#65533;[08]&#65533;'&#65533;[08]
--> remote IP address 10.30.20.2
--> pppd: H%&#65533;[08]&#65533;'&#65533;[08]
--> primary   DNS address 196.29.180.19
--> pppd: H%&#65533;[08]&#65533;'&#65533;[08]
--> secondary DNS address 196.29.164.29

```5- If you are done you can press **[COLOR=Red]Ctrl+c[/COLOR]** to exit.

[COLOR=Red]**Notice**[/COLOR]: Username & password in wvdial.conf are stored as clear text, in your cause that is not important but in my case this is totally different.

---

### Post by mhmdfoss on 2009-12-24
thank you mr ZERO
command line way is very simple and clear

thank you again

---

### Post by zero-n on 2009-12-24
I am happy for you

But could you please mark your post as **[COLOR="Red"]SOLVED [/COLOR]**so anyone can use it instead of posting a new one.

---

### Post by mhmdfoss on 2009-12-24
sure mr ZERO-N
i am hppy too 4 result and ur cooperation

---

