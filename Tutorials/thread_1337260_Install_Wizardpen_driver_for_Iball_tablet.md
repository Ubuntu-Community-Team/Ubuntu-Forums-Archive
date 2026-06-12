---
title: "Install Wizardpen driver for Iball tablet"
date: 2009-11-25
forum: Tutorials
---

### Post by drpjkurian on 2009-11-25
Hi Guys
In this thread you will come to know how to install wizardpen drivers for your Tablets and mousepen in plain and easy steps.

Wizardpen drivers are meant for following pen tablets. They are as following
# Acecad Flair II GT-504
# DigiPro 5.5×4&#8221; Graphics Tablet
# Digital Ink Pad (A4 format)
# G-pen
# Genius Wizardpen
# Genius Mousepen
# Genius
# iBall
# Manhattan
# Pentagram
# QWare
# Trust TB-3100
# Trust TB-5300
# Trust TB-6300
# iBall Tablet PF806
# AIPTEK HyperPen 10000 U ("UC-LOGIC TWA60")
# Medion MD 85673 USB Grafiktablett P82012
# Intellipen Pro(EPOS EPOS Pen Digitizer)
# NGS Draw Master Tablet (UC-LOGIC Tablet WP8060U)

1.The first step is to download the driver. You can download it from here. You can find this at the bottom of this post

Please download this to your desktop.

2.Extract the files in the folder by double clicking on it. You can either use Ark or Archive manager for that. Please extract these files to desktop.

3.Retrieve the developmental packages by using the following command in the terminal. Open terminal by navigating to Applications---> tools---> Terminal
The command is
```
sudo aptitude install xutils libx11-dev libxext-dev build-essential \
            xautomation xinput xserver-xorg-dev
```

4.Type the command ```
cd Desktop
```

5. Type the command```
cd wizardpen-0.7.0-alpha2
```

6.Install the driver by the following command
```
./configure --with-xorg-module-dir=/usr/lib/xorg/modules
        make && sudo make install

```

Check the integrity of the driver installation by typing the command.
```
ls /usr/lib/xorg/modules/input/wizardpen_drv.*
```

It should give you the output as following
```
/usr/lib/xorg/modules/input/wizardpen_drv.la
/usr/lib/xorg/modules/input/wizardpen_drv.so
```
Well the first part is over.

7. Type the following command in the terminal to know the make of the Pentablet.
```
grep -i name /proc/bus/input/devices
```
Please note down the make of the tablet which you have to use in the next step. 

8.Create a new .fdi file by using the following command in terminal
```
sudo vim /etc/hal/fdi/policy/99-x11-wizardpen.fdi
```

Press '**I**' so that INSERT appears

9. Paste the following template in the terminal
```
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="[COLOR="Red"]**NAME OF YOUR TABLET**[/COLOR]">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
                <merge key="input.x11_options.MaxX" type="string">29405</merge>
                <merge key="input.x11_options.MaxY" type="string">29671</merge>
                </match>
            </device>
            </deviceinfo> 
```


Please insert the name of your tablet where i have highlighted in red. This you can do by moving the cursor in the terminal with arrow keys.
Click **Esc** and type **:wq** and press **Enter** to save the file you have created.

Reboot your machine. It should work.

In case if it is not working(which occurs rarely), You can try by adding two more lines in the .fdi file
For editing enter the command
```
gksudo gedit  /etc/hal/fdi/policy/99-x11-wizardpen.fdi
```

The two lines of code which may help you has to be added above the line which appears as '</match>'. The code is as follows
```
<merge key="info.product" type="string">stylus</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
```


I acknowledge the help of [COLOR="Blue"]**Favux**[/COLOR] and give credit to him who helped me a lot to install the wizardpen driver.

With regards
Dr Kurian

---

### Post by donjorge22 on 2009-12-03
Tested and it works correctly in Karmic.

Can I also mention that you may need to calibrate your tablet - this is done by editing the various x and y values in the .fdi document. The following calibrations are taken directly from the Ubuntu Wizardpen wiki, [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen).

Tablet W5540U (UC-Logic):

```
Section "InputDevice"
        Identifier      "WizardPen Tablet"
        Option          "SendCoreEvents"        "true"
        Driver          "wizardpen"
        Option          "Device"        "/dev/tablet-event"
        Option          "TopX"          "2199"
        Option          "TopY"          "3598"
        Option          "BottomX"       "30325"
        Option          "BottomY"       "29278"
        Option          "MaxX"          "30325"
        Option          "MaxY"          "29278"
EndSection
```

Tablet W8060U (UC-Logic):
```

Section "InputDevice"
        Identifier      "WizardPen Tablet"
        Option          "SendCoreEvents"        "true"
        Driver          "wizardpen"
        Option          "Device"        "/dev/tablet-event"
        Option          "TopX"          "826"
        Option          "TopY"          "2626"
        Option          "BottomX"       "32747"
        Option          "BottomY"       "32762"
        Option          "MaxX"          "32747"
        Option          "MaxY"          "32762"
EndSection
```

Tablet PF1209 (UC-LOGIC)
```

Section "InputDevice"
        Identifier      "WizardPen Tablet"
        Option          "SendCoreEvents"        "true"
        Driver          "wizardpen"
        Option          "Device"        "/dev/tablet-event"
        Option          "TopX"          "0"
        Option          "TopY"          "1553"
        Option          "BottomX"       "32541"
        Option          "BottomY"       "32762"
        Option          "MaxX"          "32541"
        Option          "MaxY"          "32762"
EndSection
```

Tablet W8060U (Trust TB-6300)

```
Section "InputDevice"
        Identifier      "WizardPen Tablet"
        Option          "SendCoreEvents"        "true"
        Driver          "wizardpen"
        Option          "Device"        "/dev/tablet-event"
        Option          "TopX"          "0"
        Option          "TopY"          "234"
        Option          "BottomX"       "32747"
        Option          "BottomY"       "32762"
        Option          "MaxX"          "32747"
        Option          "MaxY"          "32762"
EndSection
```

---

### Post by drpjkurian on 2009-12-03
Dear Donjorge
Thank you very much for your updates

With regards
Dr Kurian

---

### Post by yanux on 2009-12-05
drpjkurian, that's amazing! Got my little Genius WizardPen 4x3 (WP4030U) working within a couple of minutes!

In case someone has a same one, in 99-x11-wizardpen.fdi
 you should paste code below (this will allow you use this small tab to the max):
```
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP4030U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">0</merge>
                <merge key="input.x11_options.TopY" type="string">0</merge>
                <merge key="input.x11_options.BottomX" type="string">31410</merge>
                <merge key="input.x11_options.BottomY" type="string">31870</merge>
                <merge key="input.x11_options.MaxX" type="string">31410</merge>
                <merge key="input.x11_options.MaxY" type="string">31870</merge>
                </match>
            </device>
            </deviceinfo>
```

---

### Post by drpjkurian on 2009-12-06
> **yanux said:**
> drpjkurian, that's amazing! Got my little Genius WizardPen 4x3 (WP4030U) working within a couple of minutes!

In case someone has a same one, in 99-x11-wizardpen.fdi
 you should paste code below (this will allow you use this small tab to the max):
```
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP4030U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">0</merge>
                <merge key="input.x11_options.TopY" type="string">0</merge>
                <merge key="input.x11_options.BottomX" type="string">31410</merge>
                <merge key="input.x11_options.BottomY" type="string">31870</merge>
                <merge key="input.x11_options.MaxX" type="string">31410</merge>
                <merge key="input.x11_options.MaxY" type="string">31870</merge>
                </match>
            </device>
            </deviceinfo>
```

Hi Yanux

Your most welcome
Thank you very much for your additional information

With regards
Dr Kurian

---

### Post by Overloader33 on 2009-12-08
I cant get my TB-6300 working with it.

It seems like everything works butons etc. But when i get it to GIMP it cant get the cursor moving .Although it understands the touch of the pen it doesnt paint there.

PLZ help

---

### Post by drpjkurian on 2009-12-09
> **Overloader33 said:**
> I cant get my TB-6300 working with it.

It seems like everything works butons etc. But when i get it to GIMP it cant get the cursor moving .Although it understands the touch of the pen it doesnt paint there.

PLZ help

Hi
Let me know whether your cursor movement is stalled in GIMP alone and working fine in all other programmes.

Let me also have a look at .fdi file, and its location

With regards
Dr Kurian

---

### Post by Overloader33 on 2009-12-10
> **drpjkurian said:**
> Hi
Let me know whether your cursor movement is stalled in GIMP alone and working fine in all other programmes.

Let me also have a look at .fdi file, and its location

With regards
Dr Kurian


My tablet doesent semm to work generally ,i could only get it working with the calibrate tool.

No programm detects movement or presure......(exept wizardpen-calibrate).

It gets  recognized as input on gimp ,inkspace  and blender ,but the is no action or movement . Only it recognizes the touch of the pen and simulates a MMB click but the movement does nothing.

Heres my .fdi file 

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="WP8060U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">0</merge>
                <merge key="input.x11_options.TopY" type="string">103</merge>
                <merge key="input.x11_options.BottomX" type="string">32747</merge>
                <merge key="input.x11_options.BottomY" type="string">32762</merge>
                <merge key="input.x11_options.MaxX" type="string">32747</merge>
                <merge key="input.x11_options.MaxY" type="string">32762</merge>
                </match>
            </device>
            </deviceinfo>

```

---

### Post by drpjkurian on 2009-12-10
> **Overloader33 said:**
> My tablet doesent semm to work generally ,i could only get it working with the calibrate tool.

No programm detects movement or presure......(exept wizardpen-calibrate).

It gets  recognized as input on gimp ,inkspace  and blender ,but the is no action or movement . Only it recognizes the touch of the pen and simulates a MMB click but the movement does nothing.

Heres my .fdi file 

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="[COLOR="Red"]WP8060U[/COLOR]">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">0</merge>
                <merge key="input.x11_options.TopY" type="string">103</merge>
                <merge key="input.x11_options.BottomX" type="string">32747</merge>
                <merge key="input.x11_options.BottomY" type="string">32762</merge>
                <merge key="input.x11_options.MaxX" type="string">32747</merge>
                <merge key="input.x11_options.MaxY" type="string">32762</merge>
                </match>
            </device>
            </deviceinfo>

```

Hi overloader

Let us go step by step from the beginning.

First step check whether the driver is installed properly. To check this, type the command
```
ls /usr/lib/xorg/modules/input/wizardpen_drv.*
```
It should give you following output in your terminal namely this
```
/usr/lib/xorg/modules/input/wizardpen_drv.la
/usr/lib/xorg/modules/input/wizardpen_drv.so
```
If you are getting this output then we can be sure that your driver installation is correct. If not, download the driver from my thread and install it accordingly.

Second step: If your driver installation is fine then your problem might be lurking in your .fdi.
Well i noticed that the name of your tablet which you have mentioned in your .fdi seems to be incomplete. To know the name of your tablet please check by using the command
```
grep -i name /proc/bus/input/devices
```
The name of your tablet should match exactly what is produced from the above command. For eg my tablet is WP5540U, But the name of the tablet according to the above command was 'UC logic WP5540U'. So please check out the name of your tablet once again.

Let me know your outcome
Best of luck
Dr Kurian

---

### Post by pepperlim on 2009-12-15
It worked! And the instructions were so easy to follow! Thanks Favux and drpjkurian!

---

### Post by drpjkurian on 2009-12-15
> **pepperlim said:**
> It worked! And the instructions were so easy to follow! Thanks Favux and drpjkurian!

Hi pepperline

You are most welcome buddy

Dr Kurian

---

### Post by djwkd on 2009-12-20
Hey!
Cheers for this! I'm so chuffed i got my graphics tablet to work! One step further away from Windows :)

---

### Post by drpjkurian on 2009-12-20
> **djwkd said:**
> Hey!
Cheers for this! I'm so chuffed i got my graphics tablet to work! One step further away from Windows :)

Hi djwkd
Thank you very much buddy.

Dr Kurian

---

### Post by KENSAV on 2009-12-25
OK, so I'm stuck at the calibration thing. I honestly have no clue what to do now. How do I edit the .fdi file? Where do I put the whole parameter data? I'm not into programming, and I'm kinda new to using Ubuntu, but I sure want to have a Tablet with pressure sensibility, because I'm getting quite pissed off at my own incompatibility with this whole problem. Could anyone help me out?

---

### Post by gaintsura on 2009-12-25
Worked on debian lenny and ubuntu hardy in 10 minutes or less for WP8060U

ROCKIN!

---

### Post by The knyazzz on 2009-12-26
Hello, [drpjkurian]("http://ubuntuforums.org/member.php?u=805294")
im trying to make my genius G-pen 450 work in ubuntu 9.10.
All pages i found said that its possible and easy.
i have done everything from this page, tried [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) deb package, but its not moving at all.
result of this > ls /usr/lib/xorg/modules/input/wizardpen_drv.*is ```
/usr/lib/xorg/modules/input/wizardpen_drv.la
/usr/lib/xorg/modules/input/wizardpen_drv.so
```result of 
> grep -i name /proc/bus/input/devicesis
```
N: Name="Power Button"
N: Name="Power Button"
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="Genius Optical Mouse"
N: Name="UC-LOGIC Tablet WP5540U"
N: Name="HDA Digital PCBeep"
```and here is received 99-x11-wizardpen.fdi

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
 <deviceinfo version="0.2">
 <device>
 <!-- This MUST match with the name of your tablet -->
 <match key="info.product" contains="UC-LOGIC Tablet WP8060U">[COLOR=Red] changed to WP5540U[/COLOR]
 <merge key="input.x11_driver" type="string">wizardpen</merge>
 <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
 <merge key="input.x11_options.TopX" type="string">2199</merge>
 <merge key="input.x11_options.TopY" type="string">3598</merge>
 <merge key="input.x11_options.BottomX" type="string">30325</merge>
 <merge key="input.x11_options.BottomY" type="string">29278</merge>
 <merge key="input.x11_options.MaxX" type="string">30325</merge>
 <merge key="input.x11_options.MaxY" type="string">29278</merge>
 </match>
 </device>
</deviceinfo>
```everything looks fine for me, but doesnt work. Maybe im missing something?
Hope for your help.wayway
With gratitude and respect The knyazzz.

(after reading my post ive found a mistake... working on it for now...)
after installing deb packege i received 99-x11-wizardpen.fdi with wrong device name.
changing name to correct one makes pen working, but in a very strange way
no movement, but touch and button is working like "back" and "forward" buttons in firefox...

---

### Post by drpjkurian on 2009-12-26
> **KENSAV said:**
> OK, so I'm stuck at the calibration thing. I honestly have no clue what to do now. How do I edit the .fdi file? Where do I put the whole parameter data? I'm not into programming, and I'm kinda new to using Ubuntu, but I sure want to have a Tablet with pressure sensibility, because I'm getting quite pissed off at my own incompatibility with this whole problem. Could anyone help me out?

Dear Kensav
1.How do i edit the .fdi file?
```
gksudo gedit  /etc/hal/fdi/policy/99-x11-wizardpen.fdi
Code:
```

2.Where do you want to put the whole parameter data?
Place the whole parameter data in /etc/hal/fdi/policy/99-x11-wizardpen.fdi

Hope I have answered all your questions

With regards
Dr Kurian

---

### Post by drpjkurian on 2009-12-26
> **gaintsura said:**
> Worked on debian lenny and ubuntu hardy in 10 minutes or less for WP8060U

ROCKIN!

Hi Gaintsura

Happy to hear that

With regards
Dr Kurian

---

### Post by drpjkurian on 2009-12-26
> **The knyazzz said:**
> Hello, [drpjkurian]("http://ubuntuforums.org/member.php?u=805294")
im trying to make my genius G-pen 450 work in ubuntu 9.10.
All pages i found said that its possible and easy.
i have done everything from this page, tried [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) deb package, but its not moving at all.
result of this is ```
/usr/lib/xorg/modules/input/wizardpen_drv.la
/usr/lib/xorg/modules/input/wizardpen_drv.so
```result of 
is
```
N: Name="Power Button"
N: Name="Power Button"
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="Genius Optical Mouse"
N: Name="UC-LOGIC Tablet WP5540U"
N: Name="HDA Digital PCBeep"
```and here is received 99-x11-wizardpen.fdi

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
 <deviceinfo version="0.2">
 <device>
 <!-- This MUST match with the name of your tablet -->
 <match key="info.product" contains="UC-LOGIC Tablet WP8060U">[COLOR=Red] changed to WP5540U[/COLOR]
 <merge key="input.x11_driver" type="string">wizardpen</merge>
 <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
 <merge key="input.x11_options.TopX" type="string">2199</merge>
 <merge key="input.x11_options.TopY" type="string">3598</merge>
 <merge key="input.x11_options.BottomX" type="string">30325</merge>
 <merge key="input.x11_options.BottomY" type="string">29278</merge>
 <merge key="input.x11_options.MaxX" type="string">30325</merge>
 <merge key="input.x11_options.MaxY" type="string">29278</merge>
 </match>
 </device>
</deviceinfo>
```everything looks fine for me, but doesnt work. Maybe im missing something?
Hope for your help.wayway
With gratitude and respect The knyazzz.

(after reading my post ive found a mistake... working on it for now...)
after installing deb packege i received 99-x11-wizardpen.fdi with wrong device name.
changing name to correct one makes pen working, but in a very strange way
no movement, but touch and button is working like "back" and "forward" buttons in firefox...

Hi Knyazzz
Well It is understood that your driver is installed properly.

I think your problem might be in .fdi file.
Well please do the following
1. Please edit the whole .fdi file by typing the following command
```
gksudo gedit  /etc/hal/fdi/policy/99-x11-wizardpen.fdi
```

2. Paste the following passage in your .fdi file

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP5540U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
                <merge key="input.x11_options.MaxX" type="string">29405</merge>
                <merge key="input.x11_options.MaxY" type="string">29671</merge>
<merge key="info.product" type="string">stylus</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
                </match>
            </device>
            </deviceinfo>
```
I hope it should work.

With regards
Dr Kurian

---

### Post by unavenged on 2009-12-26
Hi, Im having problems installing a Genius PenSketch 9x12 tablet but the only thing working is the mouse buttons on the cordless mouse that came with it... The mouse doesn't pick up movement and the pen doesn't work

I followed the instructions on the Tablet Setup Wizardpen Howto 

```
cat /sys/bus/usb/devices/*/product
9x12 Tablet
EHCI Host Controller
OHCI Host Controller
OHCI Host Controller
```

```
ls /usr/lib/xorg/modules/input/wizardpen_drv.*
/usr/lib/xorg/modules/input/wizardpen_drv.la
/usr/lib/xorg/modules/input/wizardpen_drv.so

```

```
grep -i name /proc/bus/input/devices
N: Name="Power Button (FF)"
N: Name="Power Button (CM)"
N: Name="Sleep Button (CM)"
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="                9x12 Tablet"
N: Name="PC Speaker"
N: Name="ImPS/2 Generic Wheel Mouse"

```

And the .fdi file 
```

<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="9x12 Tablet">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
                <merge key="input.x11_options.MaxX" type="string">29405</merge>
                <merge key="input.x11_options.MaxY" type="string">29671</merge>
                <merge key="info.product" type="string">stylus</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
                </match>
            </device>
            </deviceinfo>

```

```
sudo /etc/init.d/rc.local start
Udev did NOT create /dev/tablet-event = tablet NOT present! - Tablet-driver disabled

```

And dmesg output

```
[    4.746495] input:                 9x12 Tablet as /devices/pci0000:00/0000:00:03.0/usb2/2-1/2-1:1.0/input/input5
[    4.760707] generic-usb 0003:5543:0042.0001: input,hidraw0: USB HID v1.10 Mouse [                9x12 Tablet] on usb-0000:00:03.0-1/input0

```

But the funny thing is before i went through the how to the mouse was working fine but the pen wasn't

Thanks in advance

---

### Post by gaintsura on 2009-12-26
drpjkurian So far so good... however, after some toying lastnight, I noticed that the center of the tablet is not center on the screen in ubuntu. 

I tried playing with the TopX, TopY, BottomX, BottomY, MaxX, MaxY Paramaters, but it didn't seem to make things better or worse. 

Not sure if screen resolution matters, it doesn't seem to as my debian laptop has 1280x1024, while my ubuntu laptop has 800x600 on an external screen.

Center of the screen compared to center of the tablet is way off, center on the screen = 4th icon left, 2nd Icon down on the tablet.

If this is fixable, it would be great!

I'd also recommend that the Z paramaters be added into the Xorg Config for the WP8060U because without it, the pen will cause movement even an inch over the tablet.

Thanks in advance!

---

### Post by The knyazzz on 2009-12-26
Thanks a lot ^^
it moves now...
ive seen those two strings on [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen),
but forgot to add them into newly installed fdi from deb package ^^
yeah... i always say better install from source... 
well anyway thanks. i will try to fix problem with touch sencitivity by myself for now.

---

### Post by KENSAV on 2009-12-26
> **drpjkurian said:**
> Dear Kensav
1.How do i edit the .fdi file?
```
gksudo gedit  /etc/hal/fdi/policy/99-x11-wizardpen.fdi
Code:
```2.Where do you want to put the whole parameter data?
Place the whole parameter data in /etc/hal/fdi/policy/99-x11-wizardpen.fdi

Hope I have answered all your questions

With regards
Dr Kurian

So then it doesn't matter where the parameters go inside the file itself? I put them just above the </match> part. I double checked that I have the correct device name at the right place and that I used the right parameters for that device. I have a UC-Logic Tablet W8060U, so I guess it should work, and it woks fine, too, except I can't get any pressure sensibility out of it. Tried different programs as well, such as: Gimp, Pencil and Flash 8 under Wine.

---

### Post by drpjkurian on 2009-12-26
> **The knyazzz said:**
> Thanks a lot ^^
it moves now...
ive seen those two strings on [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen),
but forgot to add them into newly installed fdi from deb package ^^
yeah... i always say better install from source... 
well anyway thanks. i will try to fix problem with touch sencitivity by myself for now.

Hi Knyazz
You are most welcome

Dr Kurian

---

### Post by drpjkurian on 2009-12-26
> **unavenged said:**
> Hi, Im having problems installing a Genius PenSketch 9x12 tablet but the only thing working is the mouse buttons on the cordless mouse that came with it... The mouse doesn't pick up movement and the pen doesn't work

I followed the instructions on the Tablet Setup Wizardpen Howto 

```
cat /sys/bus/usb/devices/*/product
9x12 Tablet
EHCI Host Controller
OHCI Host Controller
OHCI Host Controller
```

```
ls /usr/lib/xorg/modules/input/wizardpen_drv.*
/usr/lib/xorg/modules/input/wizardpen_drv.la
/usr/lib/xorg/modules/input/wizardpen_drv.so

```

```
grep -i name /proc/bus/input/devices
N: Name="Power Button (FF)"
N: Name="Power Button (CM)"
N: Name="Sleep Button (CM)"
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="                9x12 Tablet"
N: Name="PC Speaker"
N: Name="ImPS/2 Generic Wheel Mouse"

```

And the .fdi file 
```

<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="9x12 Tablet">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
                <merge key="input.x11_options.MaxX" type="string">29405</merge>
                <merge key="input.x11_options.MaxY" type="string">29671</merge>
                <merge key="info.product" type="string">stylus</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
                </match>
            </device>
            </deviceinfo>

```

```
sudo /etc/init.d/rc.local start
Udev did NOT create /dev/tablet-event = tablet NOT present! - Tablet-driver disabled

```

And dmesg output

```
[    4.746495] input:                 9x12 Tablet as /devices/pci0000:00/0000:00:03.0/usb2/2-1/2-1:1.0/input/input5
[    4.760707] generic-usb 0003:5543:0042.0001: input,hidraw0: USB HID v1.10 Mouse [                9x12 Tablet] on usb-0000:00:03.0-1/input0

```

But the funny thing is before i went through the how to the mouse was working fine but the pen wasn't

Thanks in advance

Hi

You have done everything perfectly. I am perplexed in your case. 
Well I suggest you to evoke the Help of my friend Favux who is a wizard in these issue. Please do invite him to this thread.

With regards
Dr Kurian

---

### Post by drpjkurian on 2009-12-27
> **KENSAV said:**
> So then it doesn't matter where the parameters go inside the file itself? I put them just above the </match> part. I double checked that I have the correct device name at the right place and that I used the right parameters for that device. I have a UC-Logic Tablet W8060U, so I guess it should work, and it woks fine, too, except I can't get any pressure sensibility out of it. Tried different programs as well, such as: Gimp, Pencil and Flash 8 under Wine.

Hi Kensav

You can insert these options to enable MAX and MIN pressure sensitivity: 
Option "TopZ" "10" Option "BottomZ" "511" Option "MaxZ" "511" 
Where "TopZ" represents the lowest pressure-level to accept, and "BottomZ"/"MaxZ" represents the maximum pressure-level to accept.

Did you try this. 
Please let me know

With regards
Dr Kurian

---

### Post by drpjkurian on 2009-12-27
> **gaintsura said:**
> drpjkurian So far so good... however, after some toying lastnight, I noticed that the center of the tablet is not center on the screen in ubuntu. 

I tried playing with the TopX, TopY, BottomX, BottomY, MaxX, MaxY Paramaters, but it didn't seem to make things better or worse. 

Not sure if screen resolution matters, it doesn't seem to as my debian laptop has 1280x1024, while my ubuntu laptop has 800x600 on an external screen.

Center of the screen compared to center of the tablet is way off, center on the screen = 4th icon left, 2nd Icon down on the tablet.

If this is fixable, it would be great!

I'd also recommend that the Z paramaters be added into the Xorg Config for the WP8060U because without it, the pen will cause movement even an inch over the tablet.

Thanks in advance!

Hi
Please give a try to this instructions

1.Execute the following command: lshal | less
2.Search the section with the name of your tablet, as obtained from Step 2 in the configuration step. The line should read something like: info.product = '[Name of your tablet]'
3.Scroll down until you find the following line: linux.device_file = '/dev/input/eventN' (N will a number)
4.The source package contains a program called 'wizardpen-calibrate', which is in the 'calibrate' folder, which actually echoes the appropriate X11 calibration settings
5.Using a terminal/console, execute the calibration program: calibrate/wizardpen-calibrate /dev/input/eventN (*Note: Subtitute /dev/input/eventN with the one obtained from Step 3)
6.Follow the instructions issued by the program, which will ask you to touch the top-left corner and bottom-right corner. Once completed, the program will echo the corresponding xorg.conf setting
7.Edit the FDI file (/etc/hal/fdi/policy/99-x11-wizardpen.fdi) and subtitute the Top/Bottom/MaxX and Top/Bottom/MaxY values to the one obtained from the wizardpen-calibrate command
8.Once done, restart your computer and test your tablet (UPDATE: Noy noted in the comments that you don't have to restart, but rather unplug and replug the tablet for the new settings to take effect. 

I got these from digital blue wave

Best of luck
Dr Kurian

---

### Post by gaintsura on 2009-12-27
> **drpjkurian said:**
> 
1.Execute the following command: lshal | less
2.Search the section with the name of your tablet, as obtained from Step 2 in the configuration step. The line should read something like: info.product = '[Name of your tablet]'
3.Scroll down until you find the following line: linux.device_file = '/dev/input/eventN' (N will a number)


I ran this, and did some searching. I found two devices for WP8060U

```

udi = '/org/freedesktop/Hal/devices/usb_device_5543_5_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.mouse', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_5543_5_noserial_if0'  (string)
  info.product = 'UC-LOGIC Tablet WP8060U'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_5543_5_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event8'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_5543_5_noserial_if0'  (string)
  input.product = 'UC-LOGIC Tablet WP8060U'  (string)
  input.x11_driver = 'wizardpen'  (string)
  input.x11_options.BottomX = '32371'  (string)
  input.x11_options.BottomY = '32634'  (string)
  input.x11_options.BottomZ = '511'  (string)
  input.x11_options.MaxX = '32371'  (string)
  input.x11_options.MaxY = '32364'  (string)
  input.x11_options.MaxZ = '511'  (string)
  input.x11_options.SendCoreEvents = 'true'  (string)
  input.x11_options.TopX = '0'  (string)
  input.x11_options.TopY = '150'  (string)
  input.x11_options.TopZ = '10'  (string)
  linux.device_file = '/dev/input/event8'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/class/input/input8/event8'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_5543_5_noserial_if0_hiddev'
  hiddev.application_pages = {'Unknown page 0xd0002', 'Generic Desktop Page', 'Generic Desktop Page'} (string list)
  hiddev.device = '/dev/usb/hiddev0'  (string)
  hiddev.product = 'UC-LOGIC Tablet WP8060U'  (string)
  info.capabilities = {'hiddev'} (string list)
  info.category = 'hiddev'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_5543_5_noserial_if0'  (string)
  info.product = 'UC-LOGIC Tablet WP8060U'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_5543_5_noserial_if0_hiddev'  (string)
  input.x11_driver = 'wizardpen'  (string)
  input.x11_options.BottomX = '32371'  (string)
  input.x11_options.BottomY = '32634'  (string)
  input.x11_options.BottomZ = '511'  (string)
  input.x11_options.MaxX = '32371'  (string)
  input.x11_options.MaxY = '32364'  (string)
  input.x11_options.MaxZ = '511'  (string)
  input.x11_options.SendCoreEvents = 'true'  (string)
  input.x11_options.TopX = '0'  (string)
  input.x11_options.TopY = '150'  (string)
  input.x11_options.TopZ = '10'  (string)
  linux.device_file = '/dev/usb/hiddev0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/class/usb/hiddev0'  (string)

```

I'm not sure which of these to use, also, will this 'event' or 'hiddev' always be the same numeric? IE will the tablet _always_ be /dev/input/event8 in this case (because I'm not sure it is) or will hiddev for this device always be hiddev0?

While I wait for your reply, I'm going to try both and see what I get.

> **drpjkurian said:**
> 
4.The source package contains a program called 'wizardpen-calibrate', which is in the 'calibrate' folder, which actually echoes the appropriate X11 calibration settings
5.Using a terminal/console, execute the calibration program: calibrate/wizardpen-calibrate /dev/input/eventN (*Note: Subtitute /dev/input/eventN with the one obtained from Step 3)
6.Follow the instructions issued by the program, which will ask you to touch the top-left corner and bottom-right corner. Once completed, the program will echo the corresponding xorg.conf setting
7.Edit the FDI file (/etc/hal/fdi/policy/99-x11-wizardpen.fdi) and subtitute the Top/Bottom/MaxX and Top/Bottom/MaxY values to the one obtained from the wizardpen-calibrate command
8.Once done, restart your computer and test your tablet (UPDATE: Noy noted in the comments that you don't have to restart, but rather unplug and replug the tablet for the new settings to take effect. 


I did this previously (the make/make install), and got the same output you guys gave for the WP8060U when I did the calibration. I even tried to make the area larger than what had been given after calibration, it did not change.

Also, one last note, you need to 'make clean' before you 'make && sudo make install', it looks like it wasn't made clean before being packaged up for distribution, otherwise you get the error 'No target for "build"'

Thanks again.

---

### Post by Tollkirk on 2009-12-28
> **The knyazzz said:**
> Thanks a lot ^^
it moves now...
ive seen those two strings on [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen),
but forgot to add them into newly installed fdi from deb package ^^
yeah... i always say better install from source... 
well anyway thanks. i will try to fix problem with touch sencitivity by myself for now.

I get the same problem that you had - tapping the tablet activates 'back' in Firefox. Like you, I installed the driver by means of the deb - what exactly did you do to fix the problem? What are the two 'strings' you refer to?

---

### Post by marceze on 2009-12-29
Hi all of you:), I have a tablet genius Gpen F610, and it works fine, except by one thing, it's doesn't draw! when i'm pass throw the pen on tablet, it's only moves the cursor. I try to do what drpjkurian explain, but I have troubles to continue with the step 8, i don't know how to do the insert in terminal part, and when I wrote * [sudo vim /etc/hal/fdi/policy/99-x11-wizardpen.fdi] * and left pres intro button, appears in the terminal this * [sudo: vim: command not fund] * so i don`t know how to continue. 

The name in the terminal for the tablet is "WALTOP International Corp. Slim Tablet"

I'm using Ubuntu 9.10 64bits, please help me! I don't want to go to win just for sketch my designs.:(

---

### Post by drpjkurian on 2009-12-29
> **Tollkirk said:**
> I get the same problem that you had - tapping the tablet activates 'back' in Firefox. Like you, I installed the driver by means of the deb - what exactly did you do to fix the problem? What are the two 'strings' you refer to?

Hi Tollkirk

Please see the post #18. The problem of knyazz was solved by editing the .fdi file.
So please check out your .fdi file and edit it if required. I presume that your driver is installed without any glitches.

Let me know if you need help in editing .fdi 

Dr Kurian

---

### Post by drpjkurian on 2009-12-29
> **marceze said:**
> Hi all of you:), I have a tablet genius Gpen F610, and it works fine, except by one thing, it's doesn't draw! when i'm pass throw the pen on tablet, it's only moves the cursor. I try to do what drpjkurian explain, but I have troubles to continue with the step 8, i don't know how to do the insert in terminal part, and when I wrote * [sudo vim /etc/hal/fdi/policy/99-x11-wizardpen.fdi] * and left pres intro button, appears in the terminal this * [sudo: vim: command not fund] * so i don`t know how to continue. 

The name in the terminal for the tablet is "WALTOP International Corp. Slim Tablet"

I'm using Ubuntu 9.10 64bits, please help me! I don't want to go to win just for sketch my designs.:(

Hi
I am sorry to say that i have no idea why it is not working in your machine.
The possible reasons could be
1. Your sudo password could be wrong.
2. You might have copied the command wrongly.

Well please try once again by copying the command from the first post using Ctrl C.

Dr Kurian

---

### Post by marceze on 2009-12-30
Hi again please take look this...

---------------terminal---------------
marceze@marceze-desktop:~$ grep -i name /proc/bus/input/devices
N: Name="Power Button"
N: Name="Power Button"
N: Name="Macintosh mouse button emulation"
N: Name="Microsoft Microsoft® Digital Media Keyboard 3000"
N: Name="Microsoft Microsoft® Digital Media Keyboard 3000"
[COLOR="Red"]N: Name="WALTOP International Corp. Slim Tablet"[/COLOR](my gpen f610)
N: Name="DragonRise Inc.   Generic   USB  Joystick  "
N: Name="HDA Digital PCBeep"
N: Name="ImPS/2 Generic Wheel Mouse"
marceze@marceze-desktop:~$ sudo vim /etc/hal/fdi/policy/99-x11-wizardpen.fdi    *[COLOR="Red"][SIZE="2"][press intro here][/SIZE][/COLOR]*
[sudo] password for marceze: 
sudo: vim: command not found
---------------------------------------

this is what apears in the terminal in step 8...
I don't know how to continue, the password is ok, I'm new in terminal things:mad:...

---

### Post by marceze on 2009-12-31
I don't know how to do the step 8!!Please somebody explain to me this like a child! 
I'm have troubles whit the insert part, where i have to press i?? in the terminal? if i pres don't happening anything just appear that thing, one i.. INSERT doesn't appears :(

---

### Post by drpjkurian on 2010-01-01
> **marceze said:**
> I don't know how to do the step 8!!Please somebody explain to me this like a child! 
I'm have troubles whit the insert part, where i have to press i?? in the terminal? if i pres don't happening anything just appear that thing, one i.. INSERT doesn't appears :(

Hi marceze
Before trying step 8, please use the following command namely```
sudo -i
```
And then try step 8.
Just paste this when you see 'I' in your terminal
```
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="WALTOP International Corp. Slim Tablet">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
                <merge key="input.x11_options.MaxX" type="string">29405</merge>
                <merge key="input.x11_options.MaxY" type="string">29671</merge>
                </match>
            </device>
            </deviceinfo>
```

Click Esc and type :wq and press Enter to save the file you have created.
Let me know your outcome

Dr Kurian

---

### Post by djftl on 2010-01-02
Hi

I hae the same challenge as Marceze, I copied the code and entered in the terminal and it produced: 
"djftl@ubuntu:~$ sudo vim /etc/hal/fdi/policy/99-x11-wizardpen.fdi
[sudo] password for djftl: 
sudo: vim: command not found"
My password is correct and I have copied and entered the code properly. What could be the problem? Isn't any other command to use instead of 'vim'?

Regards

---

### Post by drpjkurian on 2010-01-02
> **djftl said:**
> Hi

I hae the same challenge as Marceze, I copied the code and entered in the terminal and it produced: 
"djftl@ubuntu:~$ sudo vim /etc/hal/fdi/policy/99-x11-wizardpen.fdi
[sudo] password for djftl: 
sudo: vim: command not found"
My password is correct and I have copied and entered the code properly. What could be the problem? Isn't any other command to use instead of 'vim'?



Hi
I found out the solution for your problem.Well vim is version of the UNIX editor.
I think that is not installed in your machine by default. So please install  GVim Text Editor from Add remove programmes fearture or Ubuntu software.

Please let me know your outcome.

With regards
Dr Kurian

---

### Post by marceze on 2010-01-02
thanks drpjkurian!! you roks! that was the problem!! :) I'm very happy! now I can continue with the steps! thanks again!

------EDIT-----

[COLOR="Red"]
WORKS!![/COLOR] yeah!! now just I have to calibrate...

---

### Post by drpjkurian on 2010-01-03
> **marceze said:**
> thanks drpjkurian!! you roks! that was the problem!! :) I'm very happy! now I can continue with the steps! thanks again!

------EDIT-----

[COLOR="Red"]
WORKS!![/COLOR] yeah!! now just I have to calibrate...

Hi Marceze
You are most welcome.

Dr Kurian

---

### Post by Andreas.Neubacher on 2010-01-03
> **drpjkurian said:**
> 
Wizardpen drivers are meant for following pen tablets. They are as following
# Acecad Flair II GT-504
#DigiPro 5.5×4&#8221; Graphics Tablet
# Digital Ink Pad (A4 format)
# G-pen
# Genius Wizardpen
# Genius Mousepen
# Genius
# iBall
# Manhattan
# Pentagram
# QWare
# Trust TB-3100
# Trust TB-5300
# Trust TB-6300
# UC-LOGIC
# iBall Tablet PF806


Tested successfully on Jaunty with my AIPTEK HyperPen 10000 U which identifies itself as "UC-LOGIC TWA60".

I just had to use "UC-LOGIC TWA60" in the "info.product" line of the .fdi file and changed the various values according to my calibration output

```

Driver		"wizardpen"
	Option		"Device"	"/dev/input/event12"
	Option		"TopX"		"553"
	Option		"TopY"		"2861"
	Option		"BottomX"	"39262"
	Option		"BottomY"	"25884"
	Option		"MaxX"		"39262"
	Option		"MaxY"		"25884"

```

---

### Post by drpjkurian on 2010-01-03
> **Andreas.Neubacher said:**
> Tested successfully on Jaunty with my AIPTEK HyperPen 10000 U which identifies itself as "UC-LOGIC TWA60".

I just had to use "UC-LOGIC TWA60" in the "info.product" line of the .fdi file and changed the various values according to my calibration output

```

Driver		"wizardpen"
	Option		"Device"	"/dev/input/event12"
	Option		"TopX"		"553"
	Option		"TopY"		"2861"
	Option		"BottomX"	"39262"
	Option		"BottomY"	"25884"
	Option		"MaxX"		"39262"
	Option		"MaxY"		"25884"

```

Hi Andreas

Thank you very much for informing. I will definitely update my post..

With regards
Dr Kurian

---

### Post by manolomanolo on 2010-01-04
WOW thanks for the instructions.

Unfortunately I went in weird panic after rebooting and seeing that all of my desktop was messed up!!!

At the beginning, the desktop didn't load. So I rebooted and my panels disappeared, no right mouse click, just the possibility of rebooting.

So, after a couple of reboots, I decided to change my desktop resolution (downgraded and upgraded it) and the situation got considerably better. The situation was completely restored at the following reboot.

Ubuntu 9.10 - kernel 2.6.31-16-generic

---

### Post by Tollkirk on 2010-01-04
> **drpjkurian said:**
> Hi Tollkirk

Please see the post #18. The problem of knyazz was solved by editing the .fdi file.
So please check out your .fdi file and edit it if required. I presume that your driver is installed without any glitches.

Let me know if you need help in editing .fdi 

Dr Kurian

Thanks for your response. Yes - the drivers are correctly installed. My .fdi is as follows -

<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP5540U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">2199</merge>
                <merge key="input.x11_options.TopY" type="string">3598</merge>
                <merge key="input.x11_options.BottomX" type="string">30325</merge>
                <merge key="input.x11_options.BottomY" type="string">29278</merge>
                <merge key="input.x11_options.MaxX" type="string">30325</merge>
                <merge key="input.x11_options.MaxY" type="string">29278</merge>
		<merge key="info.product" type="string">stylus</merge>
      		<merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
                </match>
            </device>
            </deviceinfo>


Any thoughts?

Thanks in advance!

---

### Post by manolomanolo on 2010-01-04
I just installed the same tablet on another Ubuntu 9.10 PC and it did not mess up my desktop.
Maybe because of the different video card. 
My "messing" one is Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07).

I forgot to check the type of the "non messing" video card.

---

### Post by drpjkurian on 2010-01-04
> **manolomanolo said:**
> WOW thanks for the instructions.

Hi Manolomanolo
You are most welcome.

Dr Kurian

---

### Post by drpjkurian on 2010-01-04
> **Tollkirk said:**
> Thanks for your response. Yes - the drivers are correctly installed. My .fdi is as follows -

<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP5540U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">2199</merge>
                <merge key="input.x11_options.TopY" type="string">3598</merge>
                <merge key="input.x11_options.BottomX" type="string">30325</merge>
                <merge key="input.x11_options.BottomY" type="string">29278</merge>
                <merge key="input.x11_options.MaxX" type="string">30325</merge>
                <merge key="input.x11_options.MaxY" type="string">29278</merge>
		<merge key="info.product" type="string">stylus</merge>
      		<merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
                </match>
            </device>
            </deviceinfo>


Any thoughts?

Thanks in advance!

Hi Tollkirk

Please overhaul your .fdi file by using the command```
gksudo gedit  /etc/hal/fdi/policy/99-x11-wizardpen.fdi
```Delete every thing in it and paste the following text in it.

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP5540U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
                <merge key="input.x11_options.MaxX" type="string">29405</merge>
                <merge key="input.x11_options.MaxY" type="string">29671</merge>
<merge key="info.product" type="string">stylus</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
                </match>
            </device>
            </deviceinfo>

```
               
Please reboot and let me know your outcome

With regards
Dr Kurian

---

### Post by Tollkirk on 2010-01-05
> **drpjkurian said:**
> Hi Tollkirk

Please overhaul your .fdi file by using the command```
gksudo gedit  /etc/hal/fdi/policy/99-x11-wizardpen.fdi
```Delete every thing in it and paste the following text in it.

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP5540U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
                <merge key="input.x11_options.MaxX" type="string">29405</merge>
                <merge key="input.x11_options.MaxY" type="string">29671</merge>
<merge key="info.product" type="string">stylus</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
                </match>
            </device>
            </deviceinfo>

```
               
Please reboot and let me know your outcome

With regards
Dr Kurian
That fixed it! Thanks ever so much for spending time on this one - you're a real credit to the Ubuntu community!

---

### Post by drpjkurian on 2010-01-05
> **Tollkirk said:**
> That fixed it! Thanks ever so much for spending time on this one - you're a real credit to the Ubuntu community!

Hi Tollkirk
You are most welcome and thank you very much for your kind words.

Dr Kurian

---

### Post by Thomas the Solitary on 2010-01-08
Hey everything works just fine!
Had to compile from source, the package is i386 and I'm amd_64...  I'm used to Slakware & Gentoo, so that's no problem.

The problem I'm having is that I have a dual screen setup and of course the tablet runs across both screens, naturally.  This however BADLY messes up the aspect ratio, both screens are 1920x1080.  

I'm looking for a way to constrain the tablet to one screen only.  The aspect ratio still won't be perfect, but it'll be a *whole lot better* :)

Now that xorg has gone to the whole dynamic loading, I really don't know what to change; I've spent way too long in windows the last couple years... 

(and don't get me started about how KDE doesn't like dual monitors... -> technically, kubuntu)

Google has lots of answers for a WACOM tablet, using wacom programs which obviously won't work here.

Any ideas?

(ATI fglrx driver ubuntu karmic/9.10 amd_64)

---

### Post by drpjkurian on 2010-01-08
> **Thomas the Solitary said:**
> Hey everything works just fine!
Had to compile from source, the package is i386 and I'm amd_64...  I'm used to Slakware & Gentoo, so that's no problem.

The problem I'm having is that I have a dual screen setup and of course the tablet runs across both screens, naturally.  This however BADLY messes up the aspect ratio, both screens are 1920x1080.  

I'm looking for a way to constrain the tablet to one screen only.  The aspect ratio still won't be perfect, but it'll be a *whole lot better* :)

Now that xorg has gone to the whole dynamic loading, I really don't know what to change; I've spent way too long in windows the last couple years... 

(and don't get me started about how KDE doesn't like dual monitors... -> technically, kubuntu)

Google has lots of answers for a WACOM tablet, using wacom programs which obviously won't work here.

Any ideas?

(ATI fglrx driver ubuntu karmic/9.10 amd_64)

Hi Thomas

Hmmm....., This seems to be beyond my capacity to solve it. Well... How about discussing this issue with Favux ? He is better than me in solving tablet issues.

Dr Kurian

---

### Post by Thomas the Solitary on 2010-01-08
I "fixed" it by setting the calibration numbers to correspond to the (double) screen ratio.
Sucks because I can only use a quarter of the pad to write on.  

But the aspect ratio is spot on ;)

---

### Post by drpjkurian on 2010-01-08
> **Thomas the Solitary said:**
> I "fixed" it by setting the calibration numbers to correspond to the (double) screen ratio.
Sucks because I can only use a quarter of the pad to write on.  

But the aspect ratio is spot on ;)

Hi thomas
Good. You got it working to some extent.

Dr Kurian

---

### Post by gaintsura on 2010-01-08
I'm having problems getting my tablet to act like the same screen size. One laptop runs 1280x1024, the other is 800x600 or 1024x768, both of them lock the tablets space in about 3 inches wide by 2 inches high, leaving the rest of the tablet to put the mouse off screen. I tried working with the x,y paramaters in both the .fdi and the xorg config, but no matter what numbers I've set here I cannot get this to change.

One system is debian lenny [which btw, this all works on]

The other is ubuntu hardy.

Thanks in advance!

---

### Post by Favux on 2010-01-08
Hi Dr Kurian, Thomas the Solitary, and gaintsura,

Has anyone tried the "ScreenX" and "ScreenY" settings yet?

Thomas the Solitary would try:
```
<merge key="input.x11_options.ScreenX" type="string">1920</merge>
<merge key="input.x11_options.ScreenY" type="string">1080</merge>
```
Added under the last tablet coordinate line:
```
<merge key="input.x11_options.MaxY" type="string">32762</merge>
```
And gaintsura would use:
```
<merge key="input.x11_options.ScreenX" type="string">1280</merge>
<merge key="input.x11_options.ScreenY" type="string">1024</merge>
```
and the for the other laptop it would depend on the resolution.

To check on the screen coordinates (dimensions) the wizardpen driver sees try entering in a terminal:
```
xinput list Tablet
```

If that does map the tablet to the screen you could vary it a little to get the aspect ratio "spot on".

---

### Post by drpjkurian on 2010-01-08
> **Favux said:**
> Hi Dr Kurian, Thomas the Solitary, and gaintsura,

Has anyone tried the "ScreenX" and "ScreenY" settings yet?

Thomas the Solitary would try:
```
<merge key="input.x11_options.ScreenX" type="string">1920</merge>
<merge key="input.x11_options.ScreenY" type="string">1080</merge>
```
Added under the last tablet coordinate line:
```
<merge key="input.x11_options.MaxY" type="string">32762</merge>
```
And gaintsura would use:
```
<merge key="input.x11_options.ScreenX" type="string">1280</merge>
<merge key="input.x11_options.ScreenY" type="string">1024</merge>
```
and the for the other laptop it would depend on the resolution.

To check on the screen coordinates (dimensions) the wizardpen driver sees try entering in a terminal:
```
xinput list Tablet
```

If that does map the tablet to the screen you could vary it a little to get the aspect ratio "spot on".

Dear Favux

Thank you very much. I feel that I have learnt something new from you.


With regards
Dr Kurian

---

### Post by Tony Flury on 2010-01-09
OK - I have the table working sort of - it detects movement - but only can use a very small proportion of the tablet - and not the full screen 

I attach my fdi file and xorg.conf file :

/etc/hal/fdi/policy/99-x11-wizardpen.fdi (as you can see I am using the screen options as suggested.
```
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP5540U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">1919</merge>
                <merge key="input.x11_options.TopY" type="string">3455</merge>
                <merge key="input.x11_options.BottomX" type="string">30616</merge>
                <merge key="input.x11_options.BottomY" type="string">29941</merge>
                <merge key="input.x11_options.MaxX" type="string">30616</merge>
                <merge key="input.x11_options.MaxY" type="string">29941</merge>
		<merge key="input.x11_options.ScreenX" type="string">1440</merge>
		<merge key="input.x11_options.ScreenY" type="string">900</merge>
                </match>
            </device>
            </deviceinfo>

```

xorg.conf extract
```

Section "InputDevice"
        Identifier      "WizardPen Tablet"
        Option          "SendCoreEvents"        "true"
	Driver		"wizardpen"
	Option		"TopX"		"1919"
	Option		"TopY"		"3455"
	Option		"BottomX"	"30616"
	Option		"BottomY"	"29941"
	Option		"MaxX"		"30616"
	Option		"MaxY"		"29941"
EndSection

```

xlist input (extract)
```

"UC-LOGIC Tablet WP5540U"	id=5	[XExtensionPointer]
	Num_buttons is 6
	Num_axes is 3
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 1440
		Resolution is 1000
	Axis 1 :
		Min_value is 0
		Max_value is 900
		Resolution is 1000
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1000

```

I would prefer clearly to be able to use the whole tablet.

---

### Post by gaintsura on 2010-01-09
Well, unfortunately, to no avail; I have not gotten any of the settings on my tablet to get my tablet to the right resolution or center properly. I've included my fdi and xorg, I did modify the input information because I found that this information is actually created when the device is there, but not there when it is not and seems much more reliable than a /dev/input/eventX to determine if the device exits. 

Xorg.conf: 
```
Section "InputDevice"
        Identifier      "WizardPen Tablet"
        Option          "SendCoreEvents"        "true"
        Driver          "wizardpen"
        Option          "Device"        "/dev/input/by-id/usb-UC-LOGIC_Tablet_WP8060U-event-mouse"
        Option          "TopX"          "200"
        Option          "TopY"          "200"
	Option		"TopZ"		"-10"
        Option          "BottomX"       "323710"
        Option          "BottomY"       "323640"
	Option		"BottomZ"	"511"
        Option          "MaxX"          "323710"
        Option          "MaxY"          "323640"
	Option		"MaxZ"		"511"
EndSection
```

.fdi file
```

<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP8060U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">200</merge>
                <merge key="input.x11_options.TopY" type="string">200</merge>
		<merge key="input.x11_options.TopZ" type="string">-10</merge>
                <merge key="input.x11_options.BottomX" type="string">323710</merge>
                <merge key="input.x11_options.BottomY" type="string">326340</merge>
		<merge key="input.x11_options.BottomZ" type="string">511</merge>
                <merge key="input.x11_options.MaxX" type="string">323710</merge>
                <merge key="input.x11_options.MaxY" type="string">323640</merge>
		<merge key="input.x11_options.MaxZ" type="string">511</merge>
		<merge key="input.x11_options.ScreenX" type="string">1280</merge>
                <merge key="input.x11_options.ScreenY" type="string">800</merge>
                </match>
            </device>
            </deviceinfo>

```

xinput list
```

"UC-LOGIC Tablet WP8060U"	id=7	[XExtensionPointer]
	Num_buttons is 6
	Num_axes is 3
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 1280
		Resolution is 1000
	Axis 1 :
		Min_value is 0
		Max_value is 800
		Resolution is 1000
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1000

```

None of this seems to actually help the situation. Center is still 2 inches down and 3 inches in on the tablet. End of screen to end of tablet is about center on the tablet.

Also note that in an effort to fix this. I did change the X,Y settings by adding a 0 to the end of the digits to see if this might fix the problem, however it did not. 

Does the Z value accept negative numbers? even at '10' the pen is still about 2/3 inches above the tablet before it activates, I thought the tablet was suppose to be touched, which I assume means negative numbers now?

Thanks

---

### Post by drpjkurian on 2010-01-10
> **gaintsura said:**
> Well, unfortunately, to no avail; I have not gotten any of the settings on my tablet to get my tablet to the right resolution or center properly. I've included my fdi and xorg, I did modify the input information because I found that this information is actually created when the device is there, but not there when it is not and seems much more reliable than a /dev/input/eventX to determine if the device exits. 

Xorg.conf: 
```
Section "InputDevice"
        Identifier      "WizardPen Tablet"
        Option          "SendCoreEvents"        "true"
        Driver          "wizardpen"
        Option          "Device"        "/dev/input/by-id/usb-UC-LOGIC_Tablet_WP8060U-event-mouse"
        Option          "TopX"          "200"
        Option          "TopY"          "200"
	Option		"TopZ"		"-10"
        Option          "BottomX"       "323710"
        Option          "BottomY"       "323640"
	Option		"BottomZ"	"511"
        Option          "MaxX"          "323710"
        Option          "MaxY"          "323640"
	Option		"MaxZ"		"511"
EndSection
```

.fdi file
```

<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP8060U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">200</merge>
                <merge key="input.x11_options.TopY" type="string">200</merge>
		<merge key="input.x11_options.TopZ" type="string">-10</merge>
                <merge key="input.x11_options.BottomX" type="string">323710</merge>
                <merge key="input.x11_options.BottomY" type="string">326340</merge>
		<merge key="input.x11_options.BottomZ" type="string">511</merge>
                <merge key="input.x11_options.MaxX" type="string">323710</merge>
                <merge key="input.x11_options.MaxY" type="string">323640</merge>
		<merge key="input.x11_options.MaxZ" type="string">511</merge>
		<merge key="input.x11_options.ScreenX" type="string">[COLOR="Red"]**1280**[/COLOR]</merge>
                <merge key="input.x11_options.ScreenY" type="string">**[COLOR="Red"]800[/COLOR]**</merge>
                </match>
            </device>
            </deviceinfo>

```

xinput list
```

"UC-LOGIC Tablet WP8060U"	id=7	[XExtensionPointer]
	Num_buttons is 6
	Num_axes is 3
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 1280
		Resolution is 1000
	Axis 1 :
		Min_value is 0
		Max_value is 800
		Resolution is 1000
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1000

```

None of this seems to actually help the situation. Center is still 2 inches down and 3 inches in on the tablet. End of screen to end of tablet is about center on the tablet.

Also note that in an effort to fix this. I did change the X,Y settings by adding a 0 to the end of the digits to see if this might fix the problem, however it did not. 

Does the Z value accept negative numbers? even at '10' the pen is still about 2/3 inches above the tablet before it activates, I thought the tablet was suppose to be touched, which I assume means negative numbers now?

Thanks

Hi Giantsure
Please note that you have mentioned the resolution of your external screen as 800 x 600 in post #21 of this thread. I presume that the problem lies in your .fdi.  I have highlighted the mistake in your .fdi file in bold red. In the light of Favux's advice your .fdi file should be like this
```
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP8060U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">200</merge>
                <merge key="input.x11_options.TopY" type="string">200</merge>
		<merge key="input.x11_options.TopZ" type="string">-10</merge>
                <merge key="input.x11_options.BottomX" type="string">323710</merge>
                <merge key="input.x11_options.BottomY" type="string">326340</merge>
		<merge key="input.x11_options.BottomZ" type="string">511</merge>
                <merge key="input.x11_options.MaxX" type="string">323710</merge>
                <merge key="input.x11_options.MaxY" type="string">323640</merge>
		<merge key="input.x11_options.MaxZ" type="string">511</merge>
		<merge key="input.x11_options.ScreenX" type="string">800</merge>
                <merge key="input.x11_options.ScreenY" type="string">600</merge>
                </match>
            </device>
            </deviceinfo>
```

Dr Kurian

---

### Post by drpjkurian on 2010-01-10
> **Tony Flury said:**
> OK - I have the table working sort of - it detects movement - but only can use a very small proportion of the tablet - and not the full screen 

I attach my fdi file and xorg.conf file :

/etc/hal/fdi/policy/99-x11-wizardpen.fdi (as you can see I am using the screen options as suggested.
```
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP5540U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">1919</merge>
                <merge key="input.x11_options.TopY" type="string">3455</merge>
                <merge key="input.x11_options.BottomX" type="string">30616</merge>
                <merge key="input.x11_options.BottomY" type="string">29941</merge>
                <merge key="input.x11_options.MaxX" type="string">30616</merge>
                <merge key="input.x11_options.MaxY" type="string">29941</merge>
		<merge key="input.x11_options.ScreenX" type="string">1440</merge>
		<merge key="input.x11_options.ScreenY" type="string">900</merge>
                </match>
            </device>
            </deviceinfo>

```

xorg.conf extract
```

Section "InputDevice"
        Identifier      "WizardPen Tablet"
        Option          "SendCoreEvents"        "true"
	Driver		"wizardpen"
	Option		"TopX"		"1919"
	Option		"TopY"		"3455"
	Option		"BottomX"	"30616"
	Option		"BottomY"	"29941"
	Option		"MaxX"		"30616"
	Option		"MaxY"		"29941"
EndSection

```

xlist input (extract)
```

"UC-LOGIC Tablet WP5540U"	id=5	[XExtensionPointer]
	Num_buttons is 6
	Num_axes is 3
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 1440
		Resolution is 1000
	Axis 1 :
		Min_value is 0
		Max_value is 900
		Resolution is 1000
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1000

```

I would prefer clearly to be able to use the whole tablet.

Hi Tony
Please overhaul your.fdi file by using the command
```
gksudo gedit  /etc/hal/fdi/policy/99-x11-wizardpen.fdi
```

Delete everything and paste the following text in it

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP5540U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
                <merge key="input.x11_options.MaxX" type="string">29405</merge>
                <merge key="input.x11_options.MaxY" type="string">29671</merge>
<merge key="info.product" type="string">stylus</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
                </match>
            </device>
            </deviceinfo>
```

Let me know the outcome
Dr Kurian

---

### Post by gaintsura on 2010-01-10
> **drpjkurian said:**
> Hi Giantsure
Please note that you have mentioned the resolution of your external screen as 800 x 600 in post #21 of this thread. I presume that the problem lies in your .fdi.  I have highlighted the mistake in your .fdi file in bold red. In the light of Favux's advice your .fdi file should be like this
```
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP8060U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">200</merge>
                <merge key="input.x11_options.TopY" type="string">200</merge>
		<merge key="input.x11_options.TopZ" type="string">-10</merge>
                <merge key="input.x11_options.BottomX" type="string">323710</merge>
                <merge key="input.x11_options.BottomY" type="string">326340</merge>
		<merge key="input.x11_options.BottomZ" type="string">511</merge>
                <merge key="input.x11_options.MaxX" type="string">323710</merge>
                <merge key="input.x11_options.MaxY" type="string">323640</merge>
		<merge key="input.x11_options.MaxZ" type="string">511</merge>
		<merge key="input.x11_options.ScreenX" type="string">800</merge>
                <merge key="input.x11_options.ScreenY" type="string">600</merge>
                </match>
            </device>
            </deviceinfo>
```

Dr Kurian

Dr Kurian,

I am using this tablet on two different systems, one has a resolution of 1280x800, the other is 800x600. I also made the same changes (but used 800 and 600) on my second system, this also did not work on that system. 

System one has the settings I pasted above (using 1280x800)

Thanks.

---

### Post by manolomanolo on 2010-01-10
Hi. I installed all the necessary packages to use the Trust Tablet, just to make some tests.
Now I do not have the tablet any more. How to uninstall all the related packages, please?

Take in account I've been installing
```
~$ sudo aptitude install xutils libx11-dev libxext-dev build-essential xautomation xinput xserver-xorg-dev

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  libpciaccess-dev{a} libpixman-1-dev{a} libpthread-stubs0{a} 
  libpthread-stubs0-dev{a} libx11-dev libxau-dev{a} libxcb1-dev{a} 
  libxdmcp-dev{a} libxext-dev x11proto-core-dev{a} x11proto-dri2-dev{a} 
  x11proto-fonts-dev{a} x11proto-input-dev{a} x11proto-kb-dev{a} 
  x11proto-randr-dev{a} x11proto-render-dev{a} x11proto-video-dev{a} 
  x11proto-xext-dev{a} xautomation xserver-xorg-dev xtrans-dev{a} xutils 
0 packages upgraded, 22 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,721kB of archives. After unpacking 10.4MB will be used.
```

before installing wizardpen-0.7.0-alpha2.

Also, take in account that after installing those packages and rebooting the system I had some video problems, as described before in this thread.
Actually I suppose I should run 'sudo make uninstall' into the wizardpen folder, then remove that folder and eventually remove all of those packages through Synaptic.

I'm afraid to run into video problems once more, this time because of uninstalling. That's why I'm waiting for some suggestion before making some mess.

Thanks for your time.
Regards.

---

### Post by Favux on 2010-01-11
Hi gaintsura and Tony Flury,

You both are indicating that you have, in addition to the 99-x11-wizardpen.fdi, a xorg.conf configuring your tablet.  You should use one or the other.  While you can theoretically use both, in practice it tends not to work so well.

The xorg.conf is executed after the .fdi and since it is last it's settings should control.  So changes made in the .fdi will/can be overridden.  Since both of you are making the ScreenX or Y changes in the .fdi but not the xorg.conf that may be the problem.  Although since there are no Screen entries in the xorg.conf's the entries in the .fdi should theoretically apply.

---

### Post by Tony Flury on 2010-01-12
Part of my problem I think I have is that each time i plug in the tablet or restart Linux I get a new /dev/input/event<xx>

Which means that the tablet tends to stop working and i need to recalibrate.

So is there anyway of making this permanent.

---

### Post by Favux on 2010-01-12
Hi gaintsura and Tony Flury,

Well the .fdi should handle that automatically.

To do it through the xorg.conf you have to use the actual usb pci by-path or construct a symlink rule to add to &#8220;/etc/udev/rules.d/&#8221; (the old location).  Which is where custom rules are suppose to go, not in "/lib/udev/rules.d/"

Otherwise you are correct.  Event numbers can change.

---

### Post by Tony Flury on 2010-01-12
> **drpjkurian said:**
> Hi Tony
Please overhaul your.fdi file by using the command
```
gksudo gedit  /etc/hal/fdi/policy/99-x11-wizardpen.fdi
```

Delete everything and paste the following text in it

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP5540U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
                <merge key="input.x11_options.MaxX" type="string">29405</merge>
                <merge key="input.x11_options.MaxY" type="string">29671</merge>
<merge key="info.product" type="string">stylus</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
                </match>
            </device>
            </deviceinfo>
```

Let me know the outcome
Dr Kurian

Adding in those two lines effectively disabled the tablet completely. I was able to use calibrate (so something was working), but the tablet stopped moving the mouse pointer.

I am not sure which line is the problem - but I note that the SendCoreEvents is a duplicate - is that the problem ?

---

### Post by Favux on 2010-01-12
Hi Tony Flury,

Likely.  Remove:
```
<merge key="info.product" type="string">stylus</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

```
And add just:
```
<merge key="info.product" type="string">stylus</merge>
```
here:
```
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="info.product" type="string">stylus</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

```
At least I think that's what Dr. Kurian is saying.

---

### Post by manolomanolo on 2010-01-13
Quoting myself.
Hope there will be some reply.
Thanks.

> **manolomanolo said:**
> Hi. I installed all the necessary packages to use the Trust Tablet, just to make some tests.
Now I do not have the tablet any more. How to uninstall all the related packages, please?

Take in account I've been installing
```
~$ sudo aptitude install xutils libx11-dev libxext-dev build-essential xautomation xinput xserver-xorg-dev

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  libpciaccess-dev{a} libpixman-1-dev{a} libpthread-stubs0{a} 
  libpthread-stubs0-dev{a} libx11-dev libxau-dev{a} libxcb1-dev{a} 
  libxdmcp-dev{a} libxext-dev x11proto-core-dev{a} x11proto-dri2-dev{a} 
  x11proto-fonts-dev{a} x11proto-input-dev{a} x11proto-kb-dev{a} 
  x11proto-randr-dev{a} x11proto-render-dev{a} x11proto-video-dev{a} 
  x11proto-xext-dev{a} xautomation xserver-xorg-dev xtrans-dev{a} xutils 
0 packages upgraded, 22 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,721kB of archives. After unpacking 10.4MB will be used.
```

before installing wizardpen-0.7.0-alpha2.

Also, take in account that after installing those packages and rebooting the system I had some video problems, as described before in this thread.
Actually I suppose I should run 'sudo make uninstall' into the wizardpen folder, then remove that folder and eventually remove all of those packages through Synaptic.

I'm afraid to run into video problems once more, this time because of uninstalling. That's why I'm waiting for some suggestion before making some mess.

Thanks for your time.
Regards.

---

### Post by Tony Flury on 2010-01-13
> **Favux said:**
> Hi Tony Flury,

Likely.  Remove:
```
<merge key="info.product" type="string">stylus</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

```
And add just:
```
<merge key="info.product" type="string">stylus</merge>
```
here:
```
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="info.product" type="string">stylus</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

```
At least I think that's what Dr. Kurian is saying.

Ok - following advice elsewhere in this thread - I have gone with an FDI only solution - and got rid of the Section in xorg.conf. I know that the device works - i can calibrate it each time i boot without a problem - I just can't get the Tablet to consistently move the mouse cursor at all - as i type this the tablet is not recognised as a mouse.

either including (or not) the stylus line in the fdi file has made no difference.

SO where else do i need to look to ensure that the config is right and that I can get this tablet working consistently.

/etc/hal/fdi/policy/99-x11-wizardpen.fdi
```

<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP5540U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">1919</merge>
                <merge key="input.x11_options.TopY" type="string">3455</merge>
                <merge key="input.x11_options.BottomX" type="string">30616</merge>
                <merge key="input.x11_options.BottomY" type="string">29941</merge>
                <merge key="input.x11_options.MaxX" type="string">30616</merge>
                <merge key="input.x11_options.MaxY" type="string">29941</merge>
		<merge key="input.x11_options.ScreenX" type="string">1440</merge>
		<merge key="input.x11_options.ScreenY" type="string">900</merge>
                </match>
            </device>
            </deviceinfo>

```

---

### Post by Tony Flury on 2010-01-14
Any help would be appreciated - I have tried to follow all the advice in this thread - and to be honest the only time it sort of worked was when i had both the fdi and the xorg.conf at the same time (but then I was limited to the tope 1/4 of the tablet).

---

### Post by Favux on 2010-01-14
Hi Tony Flury,

Alright, let's see what's happening with the wizardpen driver.  Assuming your using the .fdi in post #68 please attach the ouput of the following:
```
xinput --list
```
```
lshal>TonyFlury_lshal.txt
```
And the Xorg.0.log in /var/log/.

The lshal and Xorg.0.log will be too large to upload through Manage Attachments so right click on them and compress them with Create Archive.


Hi manolomanolo,

It looks like you're having a problem with your Intel video chipset.  You could probably find a fix for that.  There's a couple good threads for that.

In the unpacked wizardpen-0.7.0-alpha2 "sudo ./uninstall".  And then remove the dependency packages through Synaptic Package Manager or "sudo  aptitude remove etc.".

---

### Post by Tony Flury on 2010-01-15
OK - I just plugged the tablet back in - and now it moves the mouse - although only the top left corner of the tablet is available.

I attach an archive of the relevant fdi and diagnostic files. The dimensions in the fdi are those derived from an earlier calibration.

I just want to say that I am incredibly impressed by the contributors to this thread who seem to me to be displaying exactly the Ubuntu ethos, and going the extra mile to help solve the wide variety of challenges that people are facing.

---

### Post by Favux on 2010-01-16
Hi Tony Flury,

Are you using Hardy Heron (8.04)?  That's what I'm seeing in your Xorg.0.log.  Because it says:
```
X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux laptop 2.6.24-26-generic #1 SMP Tue Dec 1 18:37:31 UTC 2009 i686
Build Date: 13 June 2008  01:08:21AM
```

I had thought your info. on the side just wasn't updated and you're actually in Karmic or maybe Jaunty.  But looking over your posts I don't see that you've really said what you are using.

If you are using Hardy the "mystery" is solved and we can probably get you setup.

---

### Post by Tony Flury on 2010-01-16
Yes - still on Hardy 8.04.

---

### Post by Favux on 2010-01-16
Hi Tony,

OK.  With Hardy you have to use the xorg.conf.  So the first thing you need to do is to remove the .fdi.

You can use the xorg.conf with the other releases too if you want.  Intrepid is the first release you can use the .fdi with.

One of the reasons for the switch to HAL/.fdi is to support usb hot plugging.  So with the xorg.conf you do not get hot plugging.  However there is a method that may give you pseudo hot plugging.  First, after you've plugged in, ctrl-alt-F1 followed by ctrl-alt-F7.  That works for a lot of usb devices and hopefully will work with your tablet.

I've attached a xorg.conf that should work.  Notice that it has a WizardPen line in "ServerLayout".  That's what you were missing.  As always back up your current working xorg.conf and be prepared to restore it from the command line in case X doesn't start.  If you don't know how to do that just ask.  Leave the tablet plugged in when you reboot for now until you know the xorg.conf works.

Good luck!

---

### Post by Tony Flury on 2010-01-16
Favux,

ok - I have removed the fdi - and installed the xorg.conf you sent me - just done a diff between the file you sent and the /etc/X11/xorg.conf and there are no differences.

The laptop starts ok - and the tablet is listed in lshal.

I can calibrate the tablet - on /dev/input/event9 - but the tablet wont move the mouse cursor - and nothing is listed in "xinput list".

I am struggling with how to diagnose the problem - where do i look now ?

---

### Post by Favux on 2010-01-16
Hi Tony,

OK, the line in "ServerLayout" should make the tablet section "active".  So now we need to look at the wizardpen driver, which means we need to look at the Xorg.0.log again.  I think your last one was truncated near the end just where we would have seen any driver errors listed.

Were there any errors when you compiled?

---

### Post by Tony Flury on 2010-01-16
No compiler errors - and as I say I think the driver is fine as I can calibrate the tablet.

just looked at Xorg0.log and there is no reference to /dev/input/event9 - which is the dev that the tablet is mounted on right now - not sure if there should be.

I do get this though

```

tony@laptop:~$ grep -i wizard /var/log/Xorg.0.log
(**) |-->Input Device "WizardPen Tablet"
(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules/input//wizardpen_drv.so
(II) Module wizardpen: vendor="X.Org Foundation"
(**) WizardPen Tablet: TopX = 1919
(**) WizardPen Tablet: TopY = 3455
(**) WizardPen Tablet: BottomX = 30616
(**) WizardPen Tablet: BottomY = 29941
(II) WizardPen Tablet: probing event devices for WizardPen tablets
(WW) WizardPen Tablet: no WizardPen event device found (checked 22 nodes, no device name started with '  TABL')
(EE) WizardPen Tablet: unable to find device
(EE) PreInit returned NULL for "WizardPen Tablet"
(II) evaluating device (WizardPen Tablet)
tony@laptop:~$ 


```

So for some reason it can't find the device - although it is loading the driver -  which is odd ?

---

### Post by manolomanolo on 2010-01-16
[http://ubuntuforums.org/showpost.php?p=8640613&postcount=61]("http://ubuntuforums.org/showpost.php?p=8640613&postcount=61")
Please, reply. Thank you.

---

### Post by Favux on 2010-01-16
Hi Tony,

Your right, that is odd.  I'd appreciate seeing the whole Xorg.0.log.

Try in a terminal:
```
dmesg | grep wizardpen
```

Make sure the usb cable is seated firmly on both ends and boot with it connected.

The error message looks something like the ones in troubleshooting here:  [https://help.ubuntu.com/community/TabletSetupWizardpenHardy173](https://help.ubuntu.com/community/TabletSetupWizardpenHardy173)  Really the only difference I can see is by following Dr. Kurian's HOW TO you've added  x-dev to the dependencies.

---

### Post by Favux on 2010-01-16
Hi manolomanolo,

I did:  [http://ubuntuforums.org/showpost.php?p=8663892&postcount=70](http://ubuntuforums.org/showpost.php?p=8663892&postcount=70)

---

### Post by Tony Flury on 2010-01-16
> **Favux said:**
> Hi Tony,

Your right, that is odd.  I'd appreciate seeing the whole Xorg.0.log.

Try in a terminal:
```
dmesg | grep wizardpen
```

I have just rebooted : 

I get no output from the dmesg - but interestingly 

```

[   36.808178] input: UC-LOGIC Tablet WP5540U as /devices/pci0000:00/0000:00:1a.2/usb3/3-2/3-2:1.0/input/input11
[   36.890699] input,hiddev96,hidraw1: USB HID v1.00 Mouse [UC-LOGIC Tablet WP5540U] on usb-0000:00:1a.2-2

```
So that implies to me that the hardware is plugged in correctly 

Also : 
```

tony@laptop:~$ grep -i wizard /var/log/Xorg.0.log
(**) |-->Input Device "WizardPen Tablet"
(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules/input//wizardpen_drv.so
(II) Module wizardpen: vendor="X.Org Foundation"
(**) WizardPen Tablet: TopX = 1919
(**) WizardPen Tablet: TopY = 3455
(**) WizardPen Tablet: BottomX = 30616
(**) WizardPen Tablet: BottomY = 29941
(II) WizardPen Tablet: probing event devices for WizardPen tablets
(WW) WizardPen Tablet: no WizardPen event device found (checked 22 nodes, no device name started with '  TABL')
(EE) WizardPen Tablet: unable to find device
(EE) PreInit returned NULL for "WizardPen Tablet"
(II) evaluating device (WizardPen Tablet)

```

> 

Make sure the usb cable is seated firmly on both ends and boot with it connected.

The fact i can calibrate the tablet - and i get the demsg output above suggests that it is not connectivity.

Worryingly even though I am running Hardy Heron - the tablet was working with the fdi file in place, ever since deleting the fdi file, I have not had any function.

> 
The error message looks something like the ones in troubleshooting here:  [https://help.ubuntu.com/community/TabletSetupWizardpenHardy173](https://help.ubuntu.com/community/TabletSetupWizardpenHardy173)  Really the only difference I can see is by following Dr. Kurian's HOW TO you've added  x-dev to the dependencies.

---

### Post by Tony Flury on 2010-01-16
I rebuilt the drivers according to this : [https://help.ubuntu.com/community/TabletSetupWizardpenHardy173](https://help.ubuntu.com/community/TabletSetupWizardpenHardy173) - and rebooted.

I previously did not have x-dev installed - and I now do - 
I am still getting the same messages in both dmesg and Xorg0.log - the only difference is of course the device is now /dev/input/event3.

---

### Post by Favux on 2010-01-16
I don't think so, I think you should see the wizardpen.ko in dmesg.  I think you may be dealing with another driver (probably mouse or touchpad), I guess through HAL(?), which I thought wasn't active in Hardy.  So I'm confused.  I think you're looking at basic support through the usb hid portion of the kernel and another driver, not the wizardpen driver.  I don't think your compile worked.  That's why I'd like to see the entire Xorg.0.log.

I'm sitting here wondering if Hardy 8.04-4 now has some HAL support?

---

### Post by Tony Flury on 2010-01-17
Believe me - as far as I can tell the compile worked :-0

and the Xorg.0.log reports loading the module ok - suggesting no problems with the module.

I attach my Xorg0.log.

---

### Post by Favux on 2010-01-17
Hi Tony,

Maybe you need a udev rule?  Open up Synaptics Package Manager and search 'xorg'.  What we want to find out is is your version before or after version 1.7.3.  The Xorg.0.log says your Xserver is:
```
X.Org X Server 1.4.0.90
Release Date: 5 September 2007
```
It'll look something like:
```
xorg	1:7.3~ubunut etc.	X.Org X Window System
```
Need to know the exact number.

The other option would seem to be the newest driver doesn't work with Hardy and we need an older one?  I haven't seen anything about that.

---

### Post by Tony Flury on 2010-01-17
I have xorg 1:7.3+10ubuntu10.2

---

### Post by Favux on 2010-01-17
Hi Tony,

OK, I'm not sure what this is telling us:  [https://help.ubuntu.com/community/TabletSetupWizardpenHardy173](https://help.ubuntu.com/community/TabletSetupWizardpenHardy173)  It's at:
```
Setting up your tablet

General information
```
It looks to me like it is saying for your Xorg version you do need a udev rule.  But when I go to:  [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)  I don't see a udev rule.  But what I do see is a .fdi(?) along with xorg.conf settings.  But when I look at "For an *ubuntu 7.10 (Gutsy Gibbon)-version, see TabletSetupWizardpenGutsy" I find the udev rule.  It's under "Setting up udev (If the tablet is USB)" and basically looks right.  Maybe not the location I'd place it or exactly how I'd do it, but OK.

It seems like that's what you need but I admit to being confused and uncertain what to tell you.  Is the newer driver suppose to handle this or is this the problem with it on your Hardy?

---

### Post by Tony Flury on 2010-01-17
well the only time i got anything to work was with an fdi in place - but then  i could not get full movement on the tablet (only the top left 1/4 was active), so i will re-instate the fdi (as well as xorg) and see where that gets me.

stll not sure how to get the tablet to work over its full area.

I would agree that the instructions are not exactly clear - the way i read it is that on 1.73 and above i don't need UDEV - but it does not say that explicitly. The pages say about being before 1.73 - or after 1.73 - but not what happens when you have 1.73.

---

### Post by enebre on 2010-01-26
Hi,
I try to install the tablet to karmic gnome 
Trust TB7300   N: Name="WALTOP International Corp. Media Tablet"

may work with NEW VERSION (0.7.0-alpha2)
[http://download354.mediafire.com/yne99dhfy0jg/nyzyynygiyy/wizardpen_0.7.0-alpha2_i386.deb](http://download354.mediafire.com/yne99dhfy0jg/nyzyynygiyy/wizardpen_0.7.0-alpha2_i386.deb)
but how to make new calibration ?
This is not working...
> Calibration

8060 IconsPage/IconHint2.png Note: In the subsection, you'll find output from calibrate! If you tablet is listed there, you can just use that output instead!
    * If you tablet isn't listed, I would love to recieve an email with the output, and the model of your tablet! (See email at the end of the page!) 
If you want to calibrate yourself, just proceed.

Enter the "calibrate"-directory - Run this command:
cd calibrate
cd: calibrate: Aucun fichier ou dossier de ce type
Build the calibration tool - Run this command:make
Calibrate in order to find the edges of your tablet/digitizer - Run this command:
sudo ./wizardpen-calibrate /dev/tablet-event.....
sudo: ./wizardpen-calibrate: command not found 
any help please ?

---

### Post by manolomanolo on 2010-01-26
How to uninstall the drivers?

---

### Post by drpjkurian on 2010-01-26
> **manolomanolo said:**
> How to uninstall the drivers?

Hi
Select the package known as wizardepen drivers in synaptic package manger and uninstall it.
System-->Administration-->Synaptic package manager

---

### Post by manolomanolo on 2010-01-27
drpjkurian, thanks for your reply. I have been waiting for it for two weeks :) and I am very glad that eventually it is my turn to get help! Thank you!:KS

As I show in my original post, I did not use Synaptic to install the driver
[http://ubuntuforums.org/showpost.php?p=8640613&postcount=61]("http://ubuntuforums.org/showpost.php?p=8640613&postcount=61")

so I have just tried to look for "wizard" in Synaptic but no package was selected and consequently removable, as I expected.

Is there another way to remove this driver and all the stuff I've been installing as shown in the post of above?

Thank you again!

---

### Post by ste4lth on 2010-01-27
Hi!
Please help
What is code of 99-x11-wizardpen.fdi ? My tablet genius g-pen 560

---

### Post by shaka_zulu on 2010-01-28
Hello everybody

I got following problem: 

sasa@Kubuntu:~/Downloads/wizardpen-0.7.0-alpha2$ ./configure --with-xorg-module-dir=/usr/lib/xorg/modules
checking for a BSD-compatible install... /usr/bin/install -c                                             
checking whether build environment is sane... yes                                                        
checking for a thread-safe mkdir -p... /bin/mkdir -p                                                     
checking for gawk... no                                                                                  
checking for mawk... mawk                                                                                
checking whether make sets $(MAKE)... yes                                                                
checking whether to enable maintainer-specific portions of Makefiles... no                               
checking build system type... x86_64-unknown-linux-gnu                                                   
checking host system type... x86_64-unknown-linux-gnu                                                    
checking for style of include used by make... GNU                                                        
checking for gcc... gcc                                                                                  
checking for C compiler default output file name... a.out                                                
checking whether the C compiler works... yes                                                             
checking whether we are cross compiling... no                                                            
checking for suffix of executables...                                                                    
checking for suffix of object files... o                                                                 
checking whether we are using the GNU C compiler... yes                                                  
checking whether gcc accepts -g... yes                                                                   
checking for gcc option to accept ISO C89... none needed                                                 
checking dependency style of gcc... gcc3                                                                 
checking for a sed that does not truncate output... /bin/sed                                             
checking for grep that handles long lines and -e... /bin/grep                                            
checking for egrep... /bin/grep -E                                                                       
checking for ld used by gcc... /usr/bin/ld                                                               
checking if the linker (/usr/bin/ld) is GNU ld... yes                                                    
checking for /usr/bin/ld option to reload object files... -r                                             
checking for BSD-compatible nm... /usr/bin/nm -B                                                         
checking whether ln -s works... yes                                                                      
checking how to recognise dependent libraries... pass_all                                                
checking how to run the C preprocessor... gcc -E                                                         
checking for ANSI C header files... yes                                                                  
checking for sys/types.h... yes                                                                          
checking for sys/stat.h... yes                                                                           
checking for stdlib.h... yes                                                                             
checking for string.h... yes                                                                             
checking for memory.h... yes                                                                             
checking for strings.h... yes                                                                            
checking for inttypes.h... yes                                                                           
checking for stdint.h... yes                                                                             
checking for unistd.h... yes                                                                             
checking dlfcn.h usability... yes                                                                        
checking dlfcn.h presence... yes                                                                         
checking for dlfcn.h... yes                                                                              
checking for g++... g++                                                                                  
checking whether we are using the GNU C++ compiler... yes                                                
checking whether g++ accepts -g... yes                                                                   
checking dependency style of g++... gcc3                                                                 
checking how to run the C++ preprocessor... g++ -E                                                       
checking for g77... no                                                                                   
checking for xlf... no                                                                                   
checking for f77... no                                                                                   
checking for frt... no                                                                                   
checking for pgf77... no                                                                                 
checking for cf77... no                                                                                  
checking for fort77... no                                                                                
checking for fl32... no                                                                                  
checking for af77... no                                                                                  
checking for xlf90... no                                                                                 
checking for f90... no                                                                                   
checking for pgf90... no                                                                                 
checking for pghpf... no                                                                                 
checking for epcf90... no                                                                                
checking for gfortran... no                                                                              
checking for g95... no                                                                                   
checking for xlf95... no                                                                                 
checking for f95... no                                                                                   
checking for fort... no                                                                                  
checking for ifort... no                                                                                 
checking for ifc... no                                                                                   
checking for efc... no                                                                                   
checking for pgf95... no                                                                                 
checking for lf95... no                                                                                  
checking for ftn... no                                                                                   
checking whether we are using the GNU Fortran 77 compiler... no                                          
checking whether  accepts -g... no                                                                       
checking the maximum length of command line arguments... 32768                                           
checking command to parse /usr/bin/nm -B output from gcc object... ok                                    
checking for objdir... .libs                                                                             
checking for ar... ar                                                                                    
checking for ranlib... ranlib                                                                            
checking for strip... strip                                                                              
checking if gcc supports -fno-rtti -fno-exceptions... no                                                 
checking for gcc option to produce PIC... -fPIC                                                          
checking if gcc PIC flag -fPIC works... yes                                                              
checking if gcc static flag -static works... yes                                                         
checking if gcc supports -c -o file.o... yes                                                             
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes             
checking whether -lc should be explicitly linked in... no                                                
checking dynamic linker characteristics... GNU/Linux ld.so                                               
checking how to hardcode library paths into programs... immediate                                        
checking whether stripping libraries is possible... yes                                                  
checking if libtool supports shared libraries... yes                                                     
checking whether to build shared libraries... yes                                                        
checking whether to build static libraries... no                                                         
configure: creating libtool                                                                              
appending configuration tag "CXX" to libtool                                                             
checking for ld used by g++... /usr/bin/ld -m elf_x86_64                                                 
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes                                      
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes             
checking for g++ option to produce PIC... -fPIC                                                          
checking if g++ PIC flag -fPIC works... yes                                                              
checking if g++ static flag -static works... yes                                                         
checking if g++ supports -c -o file.o... yes                                                             
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes             
checking dynamic linker characteristics... GNU/Linux ld.so                                               
checking how to hardcode library paths into programs... immediate                                        
appending configuration tag "F77" to libtool                                                             
checking for gcc... (cached) gcc                                                                         
checking whether we are using the GNU C compiler... (cached) yes                                         
checking whether gcc accepts -g... (cached) yes                                                          
checking for gcc option to accept ISO C89... (cached) none needed                                        
checking dependency style of gcc... (cached) gcc3                                                        
checking if RANDR is defined... yes                                                                      
checking if XINPUT is defined... no                                                                      
checking for pkg-config... /usr/bin/pkg-config                                                           
checking pkg-config is at least version 0.9.0... yes                                                     
checking for XORG... yes                                                                                 
checking for ANSI C header files... (cached) yes                                                         
checking linux/input.h usability... yes                                                                  
checking linux/input.h presence... yes                                                                   
checking for linux/input.h... yes                                                                        
checking sysfs/libsysfs.h usability... no                                                                
checking sysfs/libsysfs.h presence... no
checking for sysfs/libsysfs.h... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating man/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
sasa@Kubuntu:~/Downloads/wizardpen-0.7.0-alpha2$ ls /usr/lib/xorg/modules/input/wizardpen_drv.*
ls: cannot access /usr/lib/xorg/modules/input/wizardpen_drv.*: No such file or directory

It seems that there is no problem with compiling but with something else. Do you have any hint on this one? BTW i am using Kubuntu 9.10 64-bit.

---

### Post by drpjkurian on 2010-01-29
> **ste4lth said:**
> Hi!
Please help
What is code of 99-x11-wizardpen.fdi ? My tablet genius g-pen 560

Hi
I did not understand your question

---

### Post by drpjkurian on 2010-01-29
> **manolomanolo said:**
> drpjkurian, thanks for your reply. I have been waiting for it for two weeks :) and I am very glad that eventually it is my turn to get help! Thank you!:KS

As I show in my original post, I did not use Synaptic to install the driver
[http://ubuntuforums.org/showpost.php?p=8640613&postcount=61]("http://ubuntuforums.org/showpost.php?p=8640613&postcount=61")

so I have just tried to look for "wizard" in Synaptic but no package was selected and consequently removable, as I expected.

Is there another way to remove this driver and all the stuff I've been installing as shown in the post of above?

Thank you again!

Hi
I am still searching. I will definitely inform you when i get it

---

### Post by tvcasualty on 2010-01-29
MEDION brand
MD 85637 USB Graphics Pad P82012
WORKS!!! Thank you!!!

---

### Post by drpjkurian on 2010-01-30
> **tvcasualty said:**
> MEDION brand
MD 85637 USB Graphics Pad P82012
WORKS!!! Thank you!!!

Hi
Happy to know that it works for you

---

### Post by drpjkurian on 2010-01-30
Hi Manolomaolo

Please go to the folder where you have compiled it and enter the command for uninstallation

```
cd /usr/lib/xorg/modules
```
```
sudo make uninstall
```

---

### Post by spoilingmyself on 2010-02-01
Hi Dr. Kurian and favux

You people are really quite helpful as it looks! great job

I just want to tell that I have done what the tablesetupwizardpen had to tell.
I created fdi file that is:
<?xml version="1.0" encoding="ISO-8859-1" ?>
<deviceinfo version=”0.2”>
<device>
<!-- UC-LOGIC Tablet WP5540U -->
<match key="info.product" contains="UC-LOGIC WP5540U">
<merge key="input.x11_driver" type="string">wizardpen</merge>
<merge key="info.product" type="string">stylus</merge>
<merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
<merge key="input.x11_options.TopX" type="string">2199</merge>
<merge key="input.x11_options.TopY" type="string">3598</merge>
<merge key="input.x11_options.BottomX" type="string">30325</merge>
<merge key="input.x11_options.BottomY" type="string">29278</merge>
<merge key="input.x11_options.MaxX" type="string">30325</merge>
<merge key="input.x11_options.MaxY" type="string">29278</merge>
</match>
</device>
</deviceinfo>

and I also edited xorg.conf to include
Section "InputDevice"
        Identifier      "WizardPen Tablet"
        Option          "SendCoreEvents"        "true"
        Driver          "wizardpen"
        Option          "Name"          "UC-LOGIC tablet WP5540U"
        Option          "Device"        "/dev/tablet-event"
        Option          "TopX"          "2199"
        Option          "TopY"          "3598"
        Option          "BottomX"       "30325"
        Option          "BottomY"       "29278"
        Option          "MaxX"          "30325"
        Option          "MaxY"          "29278"
EndSection
InputDevice "WizardPen Tablet" "AlwaysCore"

I don't understand what server layout is.... so what they told to do in serverlayout I did like this..
What happens is it doesnot detect movements from pen as well as mouse..
I don't have any output in case of grep -i wizard /var/log/Xorg.0.log
I don't have any idea how to move forward..

one more thing..
the out put of this command..
cat /sys/bus/usb/devices/*/product
USB2.0-CRW
Tablet WP5540U
EHCI Host Controller
EHCI Host Controller
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller


I appreciate any assistance as soon as possible...
Tons of Thanks in advance!!!!

---

### Post by spoilingmyself on 2010-02-01
Hey I got this all working finally..
using the link..
[http://digitalbluewave.blogspot.com/2008/04/genius-wizardpen-with-hardy-heron-and.html](http://digitalbluewave.blogspot.com/2008/04/genius-wizardpen-with-hardy-heron-and.html)
do exactly what he has to say.. and you will sit smilling finally.
this is all for newbies like me.. :)

---

### Post by Ant59 on 2010-02-11
Thank you very much, this really helped me :)

---

### Post by drpjkurian on 2010-02-12
> I've been using Ubuntu a long time, but never really got involved in these forums. However, I'd now like to be able to help new users, so I'm giving some of my time to the support forum here. Hope I can help you! -Antony
Hi
Good Keep up the spirit

---

### Post by apamak on 2010-02-16
I'm using xubuntu, with a Trust TB-6300, it's working fine except for the pressure sensitivity. 

I was following the set up instructions here: [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

All going well until it instructed me to edit the xorg.conf, which appears to be absent, is this a peculiarity of the Xfce environment? (i'm not too familiar with it)

Any suggestions?

---

### Post by drpjkurian on 2010-02-16
> **apamak said:**
> I'm using xubuntu, with a Trust TB-6300, it's working fine except for the pressure sensitivity. 

I was following the set up instructions here: [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

All going well until it instructed me to edit the xorg.conf, which appears to be absent, is this a peculiarity of the Xfce environment? (i'm not too familiar with it)

Any suggestions?

Hi Apamak
Please note that the later portion of that help.ubuntu page is pretty outdated. Well regarding your problem I think, After the advent of .fdi file, the method of xorg.conf has brcome obsolte.
I think I am right

---

### Post by apamak on 2010-02-16
Well that shows how long it's been since I last used ubuntu to any great length, any idea about the pressure sensitivity? Does the Z-axis need to be defined in the fdi file or elsewhere?

EDIT: Sorted, just didn't have GIMP set up properly,

---

### Post by thezuq on 2010-02-18
Thanks for this great howto !! 
Now my tablet is finally working under Ubuntu. Here is my fdi file for "WALTOP International Corp. Media Tablet"

```

<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="WALTOP International Corp. Media Tablet">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">1</merge>
                <merge key="input.x11_options.TopY" type="string">1</merge>
                <merge key="input.x11_options.BottomX" type="string">16383</merge>
                <merge key="input.x11_options.BottomY" type="string">16383</merge>
                <merge key="input.x11_options.MaxX" type="string">16383</merge>
                <merge key="input.x11_options.MaxY" type="string">16383</merge>
                </match>
            </device>
            </deviceinfo>

```

---

### Post by petaloid on 2010-02-18
Hello,

I am running Ubuntu _9.10 Karmic on 64bit_ architecture.

```
**howl@themovingcastle:~/Desktop/wizardpen-0.7.0-alpha2$ ./configure --with-xorg-module-dir=/usr/lib/xorg/modules make && sudo make install**

configure: WARNING: you should use --build, --host, --target
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
[B]checking build system type... Invalid configuration `make': machine `make' not recognized
configure: error: /bin/bash ./config.sub make failed[/B]
```

That was my progress and the error that I encounter. Do you have any advice on how I should proceed?

---

### Post by drpjkurian on 2010-02-19
> **thezuq said:**
> Thanks for this great howto !! 
Now my tablet is finally working under Ubuntu. Here is my fdi file for "WALTOP International Corp. Media Tablet"

```

<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="WALTOP International Corp. Media Tablet">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">1</merge>
                <merge key="input.x11_options.TopY" type="string">1</merge>
                <merge key="input.x11_options.BottomX" type="string">16383</merge>
                <merge key="input.x11_options.BottomY" type="string">16383</merge>
                <merge key="input.x11_options.MaxX" type="string">16383</merge>
                <merge key="input.x11_options.MaxY" type="string">16383</merge>
                </match>
            </device>
            </deviceinfo>

```

hi
Happy to know that it has worked
You are most welcome

---

### Post by drpjkurian on 2010-02-19
> **petaloid said:**
> Hello,

I am running Ubuntu _9.10 Karmic on 64bit_ architecture.

```
**howl@themovingcastle:~/Desktop/wizardpen-0.7.0-alpha2$ ./configure --with-xorg-module-dir=/usr/lib/xorg/modules make && sudo make install**

configure: WARNING: you should use --build, --host, --target
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
[B]checking build system type... Invalid configuration `make': machine `make' not recognized
configure: error: /bin/bash ./config.sub make failed[/B]
```

That was my progress and the error that I encounter. Do you have any advice on how I should proceed?
Hi
Did you executed the command```
sudo aptitude install xutils libx11-dev libxext-dev build-essential \
            xautomation xinput xserver-xorg-dev
```

---

### Post by whitered on 2010-02-21
failed to make my G-Pen 560 work. after all actions I can move cursor in wrong area in top left part of the screen (and bottom right part of the tablet). calibration ran fine.
I think the problem in my xorg.conf file, it does not contain ServerLayout section, and when I try to add it, the system loads in low-graphics mode. here is the xorg.conf:

```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "InputDevice"
	Identifier	"G-Pen"
	Option		"SendCoreEvents"	"true"
	Driver		"wizardpen"
	Option		"Device"	"/dev/input/by-id/usb-KYE_SYSTEM_Corp._G-Pen-event-if00"
	Option		"TopX"		"81"
	Option		"TopY"		"295"
	Option		"BottomX"	"11999"
	Option		"BottomY"	"8999"
	Option		"MaxX"		"11999"
	Option		"MaxY"		"8999"
EndSection

```

so how should I add ServerLayout section?

---

### Post by drpjkurian on 2010-02-22
> **whitered said:**
> 

Hi
After yhe advent of .fdi, The tablet and the machine communucate through .fdi
In your .fdi please edit the following line ```
<merge key="input.x11_options.ScreenX" type="string">[COLOR="Red"]1920[/COLOR]</merge>
<merge key="input.x11_options.ScreenY" type="string">[COLOR="Red"]1080[/COLOR]</merge>
```
The numbers in red should correspond to your resolution.I think it should solve your problem

---

### Post by whitered on 2010-02-22
It didn't help

---

### Post by Favux on 2010-02-22
Hi whitered,

Based on your xorg.conf so far and the fact that you chose "G-Pen" as the identifier it should look like:
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"G-Pen"		"SendCoreEvents"
EndSection
```
You can add it below the rest of the stuff.  You were probably leaving out the video lines.

A sample xorg.conf is on this thread at post #74.

---

### Post by whitered on 2010-02-23
Thank you Favux. I've found that there is duplicate data in xorg.conf and 99-x11-wizardpen.fdi files. I restored the original xorg.conf and changed the .fdi file to make it correspond the calibrate results, so everything works fine now.
The only thing I was unable to do is to make my pen buttons work. I've tryed ```
xinput set-buttons-map
``` with no results.

---

### Post by Yueka on 2010-03-02
Hi,
I've installed the driver (compiled it for 64bit) with checkinstall (I dislike make install..).
```

@:~$ ls /usr/lib/xorg/modules/input/wizardpen_drv.*
/usr/lib/xorg/modules/input/wizardpen_drv.la
/usr/lib/xorg/modules/input/wizardpen_drv.so

```

my "final" *.fdi-file:
```
@:~$ cat /etc/hal/fdi/policy/99-x11-wizardpen.fdi
<?xml version="1.0" encoding="ISO-8859-1" ?>
        <deviceinfo version="0.2">
                <device>
                        <match key="info.product" contains="    Tablet PF1209">
                                <merge key="info.product" type="string">stylus</merge>
                                <merge key="input.x11_driver" type="string">wizardpen</merge>
                                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
                                <merge key="input.x11_options.TopX" type="string">0</merge>
                                <merge key="input.x11_options.TopY" type="string">1553</merge>
                                <merge key="input.x11_options.BottomX" type="string">32541</merge>
                                <merge key="input.x11_options.BottomY" type="string">32762</merge>
                                <merge key="input.x11_options.MaxX" type="string">32541</merge>
                                <merge key="input.x11_options.MaxY" type="string">32762</merge>
                                <merge key="input.x11_options.ScreenX" type="string">1680</merge>
                                <merge key="input.x11_options.ScreenY" type="string">1050</merge>
                        </match>
                </device>
        </deviceinfo>

```
(I've tried it with/without x11_optionsScreenX/Y and info.product)

So - I've got mystical problems with my tablet:
The whole area doesnt work, except touching on the left or right border which moves my mouse into the top-right corner - triggering a normal mouseclick... 
My screen-resolution by the way is 1680x1050 and my xorg.conf is only filled with GPU-settings...

last lines from dmesg after device plugged in:
```
[ 1878.322523] usb 8-2: new low speed USB device using uhci_hcd and address 4
[ 1878.512237] usb 8-2: configuration #1 chosen from 1 choice
[ 1878.582797] input:     Tablet PF1209 as /devices/pci0000:00/0000:00:1d.3/usb8/8-2/8-2:1.0/input/input9
[ 1878.582892] input:     Tablet PF1209 as /devices/pci0000:00/0000:00:1d.3/usb8/8-2/8-2:1.0/input/input10
[ 1878.582961] input:     Tablet PF1209 as /devices/pci0000:00/0000:00:1d.3/usb8/8-2/8-2:1.0/input/input11
[ 1878.583021] generic-usb 0003:5543:0042.0004: input,hidraw1: USB HID v1.00 Mouse [    Tablet PF1209] on usb-0000:00:1d.3-2/input0
```
last lines from Xorg.log after device plugged in:
```
(II) config/hal: Adding input device stylus
(**) stylus: TopX = 0
(**) stylus: TopY = 1553
(**) stylus: BottomX = 32541
(**) stylus: BottomY = 32762
(**) Option "Device" "/dev/input/event7"
(--) Wizardpen Tablet MaxX:0 MaxY:0 MaxZ:0
(**) stylus is in absolute mode
(**) Option "SendCoreEvents" "true"
(**) stylus: always reports core events
(II) XINPUT: Adding extended input device "stylus" (type: WizardPen Tablet)
(II) stylus Increment: 1
(II) config/hal: Adding input device stylus
(**) stylus: TopX = 0
(**) stylus: TopY = 1553
(**) stylus: BottomX = 32541
(**) stylus: BottomY = 32762
(**) Option "Device" "/dev/input/event5"
(--) Wizardpen Tablet MaxX:0 MaxY:0 MaxZ:0
(**) stylus is in absolute mode
(**) Option "SendCoreEvents" "true"
(**) stylus: always reports core events
(II) XINPUT: Adding extended input device "stylus" (type: WizardPen Tablet)
(II) stylus Increment: 1
(II) config/hal: Adding input device stylus
(**) stylus: TopX = 0
(**) stylus: TopY = 1553
(**) stylus: BottomX = 32541
(**) stylus: BottomY = 32762
(**) Option "Device" "/dev/input/event6"
(--) Wizardpen Tablet MaxX:0 MaxY:0 MaxZ:0
(**) stylus is in absolute mode
(**) Option "SendCoreEvents" "true"
(**) stylus: always reports core events
(II) XINPUT: Adding extended input device "stylus" (type: WizardPen Tablet)
(II) stylus Increment: 1

```
```
@:~$ grep -i name /proc/bus/input/devices
N: Name="Power Button"
N: Name="Power Button"
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="Logitech USB Receiver"
N: Name="HDA Digital PCBeep"
N: Name="    Tablet PF1209"
N: Name="    Tablet PF1209"
N: Name="    Tablet PF1209"
```
```
@:~$ cat /sys/bus/usb/devices/*/product
Beanbag Emulation Device
USB2.0-CRW
USB2.0 Hub
USB Receiver
Tablet PF1209
EHCI Host Controller
EHCI Host Controller
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller
```


is there any clue?
Thanks for help and sorry for my broken english :S

---

### Post by schkovich on 2010-03-03
Driver compiled on Karmic 64 working perfectly well with WizardPen but when Rhythmbox starts playing music tablet stops working. :confused:

I couldn't find in logs anything that will point to the problem. :sad:

Help will be highly appreciated. :)

---

### Post by drpjkurian on 2010-03-03
Hi Yueka
I do not know your problem. Please contact Favux

---

### Post by drpjkurian on 2010-03-03
> **schkovich said:**
> Driver compiled on Karmic 64 working perfectly well with WizardPen but when Rhythmbox starts playing music tablet stops working. :confused:

I couldn't find in logs anything that will point to the problem. :sad:

Help will be highly appreciated. :)

Hi
This sounds strange, Iam hearing this for first time

---

### Post by schkovich on 2010-03-03
> **drpjkurian said:**
> Hi
This sounds strange, Iam hearing this for first time
Indeed it does. I have no idea where to start looking at. The first idea was that it might have something with audio configuration but I disregarded that option since system sounds, flash player, etc. are played without interference with WizardPen. Further on, only opening of Rhythmbox will knockout tablet after few seconds. Perhaps I might contact Rhythmbox develepers. :)

---

### Post by schkovich on 2010-03-04
> **schkovich said:**
> ... Perhaps I might contact Rhythmbox develepers. :)
With a help from guys on Rhythmbox IRC it turned out that problem is caused by libmtp mode probe.

Bug #2963267 against libmtp filed as [mtp-detect freezes WizardPen]("http://sourceforge.net/tracker/?func=detail&aid=2963267&group_id=158745&atid=809061").

---

### Post by jhoney142 on 2010-03-04
Hi,
 Thank you very much for your updates. its very helpful to me
With regards
 Jhoney:)

---

### Post by drpjkurian on 2010-03-04
> **schkovich said:**
> With a help from guys on Rhythmbox IRC it turned out that problem is caused by libmtp mode probe.

Bug #2963267 against libmtp filed as [mtp-detect freezes WizardPen]("http://sourceforge.net/tracker/?func=detail&aid=2963267&group_id=158745&atid=809061").

Hi
That sounds great you have done good

---

### Post by MAR71N on 2010-03-06
Greetings for everyone.
I am new in UBUNTU and Linux stuffs.
I try to install my TB 6300 and in STEP 8 the terminal give me this error:

sudo: vim: command not found

What have i done wrong? Can you help me?

I have just copy/paste yours commands to my terminal.
Sorry about my ignorance.:D

P.S.
I have found this error to in the first STEP of my instalation:

Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Err [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) karmic-updates/main libstdc++6-4.4-dev 4.4.1-4ubuntu9
  403  Forbidden
Get:1 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) karmic-updates/main g++-4.4 4.4.1-4ubuntu9 [4,701kB]
Fetched 1B in 0s (6B/s) 
E: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/libstdc++6-4.4-dev_4.4.1-4ubuntu9_i386.deb:](http://pt.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/libstdc++6-4.4-dev_4.4.1-4ubuntu9_i386.deb:) 403  Forbidden

What can you say?

---

### Post by drpjkurian on 2010-03-06
> **MAR71N said:**
> Greetings for everyone.
I am new in UBUNTU and Linux stuffs.
I try to install my TB 6300 and in STEP 8 the terminal give me this error:

sudo: vim: command not found

What have i done wrong? Can you help me?

I have just copy/paste yours commands to my terminal.
Sorry about my ignorance.:D

P.S.
I have found this error to in the first STEP of my instalation:

Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Err [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) karmic-updates/main libstdc++6-4.4-dev 4.4.1-4ubuntu9
  403  Forbidden
Get:1 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) karmic-updates/main g++-4.4 4.4.1-4ubuntu9 [4,701kB]
Fetched 1B in 0s (6B/s) 
E: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/libstdc++6-4.4-dev_4.4.1-4ubuntu9_i386.deb:](http://pt.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/libstdc++6-4.4-dev_4.4.1-4ubuntu9_i386.deb:) 403  Forbidden

What can you say?

Hi
Hi
 Well vim is version of the UNIX editor.
 I think that is not installed in your machine by default. So please install GVim Text Editor from Add remove programmes fearture or Ubuntu software.

Well I think the error 403 means that the server was down
 
 Please let me know your outcome.

---

### Post by yos_o on 2010-03-06
Hi!!!
I just install a Trust TB-6300
It works, but not so good. I can only use a small part of the tablet. I don't know how I can resolve this problem. Please help me!!!!

the result of grep -i name /proc/bus/input/devices is:

N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="PC Speaker"
N: Name="Power Button (FF)"
N: Name="Lid Switch"
N: Name="Power Button (CM)"
N: Name="Sleep Button (CM)"
N: Name="Video Bus"
N: Name="UC-LOGIC Tablet WP8060U"
N: Name="PS/2+USB Mouse"
N: Name="SynPS/2 Synaptics TouchPad"

the /etc/hal/fdi/policy/99-x11-wizardpen.fdi is as follow:

<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP8060U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">0</merge>
                <merge key="input.x11_options.TopY" type="string">234</merge>
                <merge key="input.x11_options.BottomX" type="string">32747</merge>
                <merge key="input.x11_options.BottomY" type="string">32762</merge>
                <merge key="input.x11_options.MaxX" type="string">32747</merge>
                <merge key="input.x11_options.MaxY" type="string">32762</merge>
                </match>
            </device>
            </deviceinfo>

the xlist --list:

"UC-LOGIC Tablet WP8060U"    id=5    [XExtensionPointer]
    Num_buttons is 6
    Num_axes is 3
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 1280
        Resolution is 1000
    Axis 1 :
        Min_value is 0
        Max_value is 800
        Resolution is 1000
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1000

---

### Post by drpjkurian on 2010-03-07
> **yos_o said:**
> Hi!!!
I just install a Trust TB-6300
It works, but not so good. I can only use a small part of the tablet. I don't know how I can resolve this problem. Please help me!!!!

the result of grep -i name /proc/bus/input/devices is:

N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="PC Speaker"
N: Name="Power Button (FF)"
N: Name="Lid Switch"
N: Name="Power Button (CM)"
N: Name="Sleep Button (CM)"
N: Name="Video Bus"
N: Name="UC-LOGIC Tablet WP8060U"
N: Name="PS/2+USB Mouse"
N: Name="SynPS/2 Synaptics TouchPad"

the /etc/hal/fdi/policy/99-x11-wizardpen.fdi is as follow:

<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP8060U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">0</merge>
                <merge key="input.x11_options.TopY" type="string">234</merge>
                <merge key="input.x11_options.BottomX" type="string">32747</merge>
                <merge key="input.x11_options.BottomY" type="string">32762</merge>
                <merge key="input.x11_options.MaxX" type="string">32747</merge>
                <merge key="input.x11_options.MaxY" type="string">32762</merge>
                </match>
            </device>
            </deviceinfo>

the xlist --list:

"UC-LOGIC Tablet WP8060U"    id=5    [XExtensionPointer]
    Num_buttons is 6
    Num_axes is 3
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 1280
        Resolution is 1000
    Axis 1 :
        Min_value is 0
        Max_value is 800
        Resolution is 1000
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1000
Hi
Please edit those lines in your ,fdi
```
<merge key="input.x11_options.ScreenX" type="string">[COLOR="Red"]**32747**[/COLOR]</merge>
<merge key="input.x11_options.ScreenY" type="string">[COLOR="red"]**32762**[/COLOR]</merge>
```
Those numbers in red should correspond to your screen resolution

---

### Post by yos_o on 2010-03-07
> **drpjkurian said:**
> Hi
Please edit those lines in your ,fdi
```
<merge key="input.x11_options.ScreenX" type="string">[COLOR=Red]**32747**[/COLOR]</merge>
<merge key="input.x11_options.ScreenY" type="string">[COLOR=red]**32762**[/COLOR]</merge>
```Those numbers in red should correspond to your screen resolution

it doesn't work!!
I check the screen resolution at System->Preferences->Screen Resolution
Resolution: 1280X800 so:

<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP8060U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">0</merge>
                <merge key="input.x11_options.TopY" type="string">234</merge>
                <merge key="input.x11_options.BottomX" type="string">32747</merge>
                <merge key="input.x11_options.BottomY" type="string">32762</merge>
                <merge key="input.x11_options.MaxX" type="string">32747</merge>
                <merge key="input.x11_options.MaxY" type="string">32762</merge>
                <merge key="input.x11_options.ScreenX" type="string">[COLOR=Red]1280[/COLOR]</merge>
                <merge key="input.x11_options.ScreenY" type="string">[COLOR=Red]800[/COLOR]</merge>
                </match>
            </device>
            </deviceinfo>

I don't know where is the problem, It should work!!

---

### Post by MAR71N on 2010-03-08
Good day.

The error 403 still aprears.

Now i can install the drivers but don´t work. Only the "select" button work.

What have i done wrong?:D

---

### Post by drpjkurian on 2010-03-09
> **MAR71N said:**
> Good day.

The error 403 still aprears.

Now i can install the drivers but don´t work. Only the "select" button work.

What have i done wrong?:D
Hi
The error is server problem. Can you change Server locations in System > Administration > Software Sources > Download from:

---

### Post by Sirolf10 on 2010-03-09
**At the command** cd Desktop **the terminal says he can't find the document** 

>          make && sudo make install
make: *** Geen doelen opgegeven en geen makefile gevonden.  Gestopt.
floris@floris-desktop:~$ ls /usr/lib/xorg/modules/input/wizardpen_drv.*
ls: kan geen toegang krijgen tot /usr/lib/xorg/modules/input/wizardpen_drv.*: Bestand of map bestaat niet


(The scary language is Dutch, sorry)

---

### Post by yos_o on 2010-03-09
> **yos_o said:**
> it doesn't work!!
I check the screen resolution at System->Preferences->Screen Resolution
Resolution: 1280X800 so:

<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP8060U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">0</merge>
                <merge key="input.x11_options.TopY" type="string">234</merge>
                <merge key="input.x11_options.BottomX" type="string">32747</merge>
                <merge key="input.x11_options.BottomY" type="string">32762</merge>
                <merge key="input.x11_options.MaxX" type="string">32747</merge>
                <merge key="input.x11_options.MaxY" type="string">32762</merge>
                <merge key="input.x11_options.ScreenX" type="string">[COLOR=Red]1280[/COLOR]</merge>
                <merge key="input.x11_options.ScreenY" type="string">[COLOR=Red]800[/COLOR]</merge>
                </match>
            </device>
            </deviceinfo>

I don't know where is the problem, It should work!!

nobody have the solution of my problem??

---

### Post by hjolli on 2010-03-20
Finaly something that works!!! Thank you very much.  I have Genius M712X and this is how my 99-x11-wizardpen.fdi looks like.  I added one line from the original file, since it was way to sensitive.  Tried it with MyPaint and it worked like a charm :)

The wizardpen-calibrate didn't work for me so I just tried some settings and this is what I ended with, which works fine for me!

This is the line I added <merge key="input.x11_options.TopZ" type="string">64</merge>

I started with 512 in sensitivity and worked my way down until I was satisfied and ended in 64.

The /etc/hal/fdi/policy/99-x11-wizardpen.fdi file:

<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="WALTOP International Corp. Media Tablet">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">0</merge>
                <merge key="input.x11_options.TopY" type="string">0</merge>
                <merge key="input.x11_options.TopZ" type="string">64</merge>
                <merge key="input.x11_options.BottomX" type="string">16400</merge>
                <merge key="input.x11_options.BottomY" type="string">16400</merge>
                <merge key="input.x11_options.MaxX" type="string">16400</merge>
                <merge key="input.x11_options.MaxY" type="string">16400</merge>
                </match>
            </device>
            </deviceinfo>

---

### Post by drpjkurian on 2010-03-21
Hi hjolli
You are most welcome.Thank you very much for sharing your tips

---

### Post by Charger85 on 2010-03-21
Hey guys, i cant get my Genius Easypen i405 to work. I've done everything posted in this topic and still cant get it to run, some help would be much appreciated. Also, kind of new to Ubuntu.

---

### Post by drpjkurian on 2010-03-22
> **Charger85 said:**
> Hey guys, i cant get my Genius Easypen i405 to work. I've done everything posted in this topic and still cant get it to run, some help would be much appreciated. Also, kind of new to Ubuntu.

Hi
May I know the output of
```
grep -i name /proc/bus/input/devices
```

---

### Post by Charger85 on 2010-03-22
N: Name="Power Button" N: Name="Power Button" N: Name="Sleep Button" N: Name="Macintosh mouse button emulation" N: Name="AT Translated Set 2 keyboard" N: Name="Logitech USB-PS/2 Optical Mouse" N: Name="UC-LOGIC Tablet WP5540U"

---

### Post by drpjkurian on 2010-03-23
> **Charger85 said:**
> N: Name="Power Button" N: Name="Power Button" N: Name="Sleep Button" N: Name="Macintosh mouse button emulation" N: Name="AT Translated Set 2 keyboard" N: Name="Logitech USB-PS/2 Optical Mouse" N: Name="UC-LOGIC Tablet WP5540U"

Hi
Well the wizardpen driver should definitely work with your machine.

Let us try to solve your problem in a systematic way. The problem should be in two areas namely the 

1) Driver installation
2) .fdi file

1.To check the driver integrity, please give the output of the following command
```
ls /usr/lib/xorg/modules/input/wizardpen_drv.*
```

2.please paste your .fdi file.(While pasting your .fdi file,please paste it in between code tags. ie use the icon #)

---

### Post by Charger85 on 2010-03-23
/usr/lib/xorg/modules/input/wizardpen_drv.la  /usr/lib/xorg/modules/input/wizardpen_drv.so     ```
&#8722;  &#8722;  &#8722;  &#8722;  &#8722;  wizardpen true  &#8722;  &#8722;  5619 6554 29405 29671 29405 29671 stylus       true   
```

---

### Post by drpjkurian on 2010-03-24
Hi
Your driver is installed properly. Well I did not get your .fdi file....

---

### Post by drpjkurian on 2010-03-24
/etc/hal/fdi/policy/99-x11-wizardpen.fdi

.fdi file will be in above mentioned location

---

### Post by Charger85 on 2010-03-24
When I tried to post my .fdi it just posted what came up in the code box. Sorry, I'm not very good at BB coding either.

---

### Post by drpjkurian on 2010-03-25
Ok
Please follow my instruction.
1. click 'Places' in top panel
2.Select 'Computer'
3.Open 'File system'
4.Open 'etc'
5.open 'hal'
6.open'fdi'
7.open 'policy'
8.open '99-x11-wizardpen.fdi'

Open and paste it in the code box for review.

---

### Post by Charger85 on 2010-03-25
I did those exact instructions when i tried the first time, so here goes a second shot at it.  ```
#&#8722;  &#8722;  &#8722;  &#8722;  &#8722;  wizardpen true  &#8722;  &#8722;  5619 6554 29405 29671 29405 29671 stylus       true   #
```

---

### Post by drpjkurian on 2010-03-26
Hi
I think that the problem exist in your .fdi
rewrite it and fire your tablet....

1. please install Gvim text editor from Ubuntu software centre.

2. type the following command in terminal
```
sudo vim /etc/hal/fdi/policy/99-x11-wizardpen.fdi
```

3.Delete what is there in it

4.Press 'I' so that INSERT appears
Paste the following template in the terminal
```
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP5540U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
                <merge key="input.x11_options.MaxX" type="string">29405</merge>
                <merge key="input.x11_options.MaxY" type="string">29671</merge>
                <merge key="info.product" type="string">stylus</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
                </match>
            </device>
            </deviceinfo>
```

Click **Esc** and type **:wq** and press Enter to save the file you have created.
Reboot your machine, It should work.

---

### Post by drpjkurian on 2010-03-29
Hi Charger
You gave up?..

---

### Post by rachaelistic on 2010-03-30
Thanks for the advice, drpjkurian! Took me a while to get it working, but someone else (Tollkirk) seemed to have the same trouble I was having. Now I'm off to explore Ubuntu!

---

### Post by Ant59 on 2010-03-30
I cannot seem to get this working on the Lucid Beta 1.

---

### Post by drpjkurian on 2010-03-30
> **Ant59 said:**
> I cannot seem to get this working on the Lucid Beta 1.

Hi
Please visit this thread by technomole, It might help you
[http://ubuntuforums.org/showthread.php?t=1437648](http://ubuntuforums.org/showthread.php?t=1437648)

---

### Post by drpjkurian on 2010-03-30
> **rachaelistic said:**
> Thanks for the advice, drpjkurian! Took me a while to get it working, but someone else (Tollkirk) seemed to have the same trouble I was having. Now I'm off to explore Ubuntu!

Hi
You are most welcome

---

### Post by Charger85 on 2010-04-08
No, sorry,I haven't given up, I was just unable to come here to do time constraints. I tried what you said and still cannot seem to get my tablet to work. Could there be a problem with the tablet being set to cover a different resolution than my screen?

---

### Post by drpjkurian on 2010-04-09
> **Charger85 said:**
> No, sorry,I haven't given up, I was just unable to come here to do time constraints. I tried what you said and still cannot seem to get my tablet to work. Could there be a problem with the tablet being set to cover a different resolution than my screen?

Hi Charger
I ve tried my level best to solve your problem, I think now it is beyond my knowledge to solve it. Please ask the assistance of Favux for this in this forum.

---

### Post by Charger85 on 2010-04-10
Okay, thank you for the help. I'm not quite sure what went wrong with it. Good thing I still have good old pencil and paper for the time being,

---

### Post by Jontom on 2010-05-10
Well that was a bit of a mission but I just got my tablet working under Kubuntu Lucid (x64). The driver would originally not compile until I applied a patch (see attachment wizardpenpatch.zip). To do this I just typed:

patch < xorg-x11-1.7.x-api-changes.patch

in the src directory of the wizardpen driver after extracting the patch file to the src directory. The driver then compiled and installed fine. Following that the driver would not work once the normal steps had been completed, pushing the pointer into the top left of the screen. Googling indicated that you need to do this :

Add the 70-wizardpen.conf in /usr/lib/X11/xorg.conf.d/ by typing:
sudo kate /usr/lib/X11/xorg.conf.d/70-wizardpen.conf and paste the following in.

Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver "wizardpen"
   Option "TopX" "2199"
   Option "TopY" "3598"
   Option "BottomX" "30325"
   Option "BottomY" "29278"
   Option "TopZ" "10"
   Option "BottomZ" "1023"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/mouse*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSection 

save the file and reboot.

This lets the correct driver be used, and after rebooting it all worked fine.

---

### Post by manolomanolo on 2010-05-10
Hi. I installed wizardpen in Karmic from source and I would like to ininstalle here in Lucid.

How can I uninstall wizardpen?

Thanks.

---

### Post by Jontom on 2010-05-10
I assume you mean you upgraded from karmic, anyway, you shouldn't really need to uninstall, just follow the steps and the wizardpen drivers should be overwritten.

---

### Post by manolomanolo on 2010-05-10
Jontom, thanks for your reply.

You are right, I upgraded from Karmic.
I just want to remove the drivers since I do not have the device anymore.

So, again, how to remove those drivers here in Lucid taking in account that I installed them from source when I was in karmic?

Thanks.

---

### Post by Jontom on 2010-05-10
Well uninstalling them wont really do much other than free up a few kb, but you can delete the drivers in:

/usr/lib/xorg/modules/input/wizardpen_drv.la
/usr/lib/xorg/modules/input/wizardpen_drv.so

by typing sudo rm -rf /usr/lib/xorg/modules/input/wizardpen_drv.la
etc

sudo make uninstall in the source directory may also work, but I am no expert.

---

### Post by MAR71N on 2010-05-14
ramalhais@ramalhais-laptop:~/Desktop/wizardpen-0.7.0-alpha2$ sudo vim /etc/hal/fdi/policy/99-x11-wizardpen.fdi
sudo: vim: command not found
ramalhais@ramalhais-laptop:~/Desktop/wizardpen-0.7.0-alpha2$ 

this is my terminal.

What am i doing wrong? Can you help me?

---

### Post by drpjkurian on 2010-05-15
> **MAR71N said:**
> ramalhais@ramalhais-laptop:~/Desktop/wizardpen-0.7.0-alpha2$ sudo vim /etc/hal/fdi/policy/99-x11-wizardpen.fdi
sudo: vim: command not found
ramalhais@ramalhais-laptop:~/Desktop/wizardpen-0.7.0-alpha2$ 

this is my terminal.

What am i doing wrong? Can you help me?

Hi
VIM is a text editor, Please install GVim text editor

---

### Post by MAR71N on 2010-05-16
Sorry it's me again.
Now i can't go on after this. I hit "ENTER" or "ESC" and nothing happen.
Help me.

<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="TRUST TB-6300">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
                <merge key="input.x11_options.MaxX" type="string">29405</merge>
                <merge key="input.x11_options.MaxY" type="string">29671</merge>
                </match>
            </device>
            </deviceinfo>

:confused:

---

### Post by blablu on 2010-05-16
Hey MAR71N 

instead of ```
sudo vim /etc/hal/fdi/policy/99-x11-wizardpen.fdi
```

do

```
sudo gedit /etc/hal/fdi/policy/99-x11-wizardpen.fdi
```

and you can learn vim some other time.:P

---

### Post by MAR71N on 2010-05-17
I try Vim and can install but don't work. This is my fdi file:

<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="TRUST TB-6300">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
                <merge key="input.x11_options.MaxX" type="string">29405</merge>
                <merge key="input.x11_options.MaxY" type="string">29671</merge>
                <merge key="info.product" type="string">stylus</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
                </match>
            </device>
            </deviceinfo>

When i use my tablet the cursor goes to the upper left corner of the screen. I read the calibration and can't figure out how to do this.

---

### Post by fady_fod on 2010-05-23
> **MAR71N said:**
> I try Vim and can install but don't work. This is my fdi file:

<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="TRUST TB-6300">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
                <merge key="input.x11_options.MaxX" type="string">29405</merge>
                <merge key="input.x11_options.MaxY" type="string">29671</merge>
                <merge key="info.product" type="string">stylus</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
                </match>
            </device>
            </deviceinfo>

When i use my tablet the cursor goes to the upper left corner of the screen. I read the calibration and can't figure out how to do this.

Same problem ..
Please , Help..

---

### Post by drpjkurian on 2010-05-24
```
<merge key="input.x11_options.ScreenX" type="string">**[COLOR="Red"]1920[/COLOR]**</merge>
<merge key="input.x11_options.ScreenY" type="string">[COLOR="Red"]**1080**[/COLOR]</merge>
```

The numbers in red should match the resolution of your screen. I think it should solve your problem

---

### Post by xioneg on 2010-05-26
Hi all!

I've a problem and can not solve it on my own. I installed this driver and it work quite well with genius easypen i405 in Gimp. But when i tried tablet in Photoshop CS4 Extended under Wine - pressure sensivity did not work at all. Is there any way to get it work?

---

### Post by manolomanolo on 2010-05-26
just wanted to remove notifications :)
bye

---

### Post by fady_fod on 2010-05-27
Sorry , It's me again ..
Where exactly should I paste :
<merge key="input.x11_options.ScreenX" type="string">1920</merge>
<merge key="input.x11_options.ScreenY" type="string">1080</merge>

---

### Post by drpjkurian on 2010-05-30
> **fady_fod said:**
> Sorry , It's me again ..
Where exactly should I paste :
<merge key="input.x11_options.ScreenX" type="string">1920</merge>
<merge key="input.x11_options.ScreenY" type="string">1080</merge>

Hi
Please edit your .fdi file. If you need step by step instructions let me know..

---

### Post by drpjkurian on 2010-05-30
> **xioneg said:**
> Hi all!

I've a problem and can not solve it on my own. I installed this driver and it work quite well with genius easypen i405 in Gimp. But when i tried tablet in Photoshop CS4 Extended under Wine - pressure sensivity did not work at all. Is there any way to get it work?

Hi 
I think the compatibility between Wine and Wizardpen is not smooth. Happy to know that it works well in Gimp. What else do you need ? Gimp is enough why go for photoshop??

---

### Post by fady_fod on 2010-05-30
Thanks for your fast replies... You are very helpful..  ^__^
I have a new problem ,, I installed UBUNTU 10.04 for netbooks ..
When I try to edit & save fdi file I get this problem ::

"/etc/hal/fdi/policy/99-x11-wizardpen.fdi" E212: Can't open file for writing

I can Open It and edit It ,, but I can't save With :wq Command

Any suggestions ?
Thanks in advance..

---

### Post by drpjkurian on 2010-05-31
> **fady_fod said:**
> Thanks for your fast replies... You are very helpful..  ^__^
I have a new problem ,, I installed UBUNTU 10.04 for netbooks ..
When I try to edit & save fdi file I get this problem ::

"/etc/hal/fdi/policy/99-x11-wizardpen.fdi" E212: Can't open file for writing

I can Open It and edit It ,, but I can't save With :wq Command

Any suggestions ?
Thanks in advance..

Hi
Try this command
```
gksudo gedit  /etc/hal/fdi/policy/99-x11-wizardpen.fdi
```

and then change those numbers in red(earlier post) to your screen resolution

---

### Post by fady_fod on 2010-05-31
Dr Kurian,,

Now , I can edit & save the file 

[IMG]http://img413.imageshack.us/img413/8029/screenshotwi.png[/IMG]


But . After editing & restarting Same problem !!
Mouse pointer go to the left side of the screen and can't be moved...

If You have any Suggestions Please Tell Me


But,, I don't want You to bother Yourself with this problem I have already  wasted a lot of your precious Time..

It was my pleasure to Meet someone so helpful like you Dr Kurian...

Thanks a alot ....

---

### Post by drpjkurian on 2010-06-01
> **fady_fod said:**
> Dr Kurian,,

Now , I can edit & save the file 

[IMG]http://img413.imageshack.us/img413/8029/screenshotwi.png[/IMG]


But . After editing & restarting Same problem !!
Mouse pointer go to the left side of the screen and can't be moved...

If You have any Suggestions Please Tell Me


But,, I don't want You to bother Yourself with this problem I have already  wasted a lot of your precious Time..

It was my pleasure to Meet someone so helpful like you Dr Kurian...

Thanks a alot ....


Hi Fady fod
Thanks for your comments
Please try the following instruction, Which is last shot I can give but worth giving a try

You can try by adding two more lines in the .fdi file
For editing enter the command
```
gksudo gedit  /etc/hal/fdi/policy/99-x11-wizardpen.fdi
```
The two lines of code which may help you has to be added above the line which appears as '</match>'. The code is as follows
```
<merge key="info.product" type="string">stylus</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
```

---

### Post by swapnil_bhartiya on 2010-06-03
This is somehow not working for me...I have a i5 750 machine with GTX 470. I am running 64 bit Ubuntu 10.04...tablet is detected but the cursor remains on the top left corner. Touching the pen opens Application Menu that is all it does. Please suggest. 

<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="    Tablet PF8060">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
                <merge key="input.x11_options.MaxX" type="string">29405</merge>
                <merge key="input.x11_options.MaxY" type="string">29671</merge>
                </match>
            </device>
            </deviceinfo>

---

### Post by plitocz on 2010-06-04
Hi,

I am quite new to this, but i was trying to do everything I can to make Genius EasyPen i450 work properly....but always i end up at the point, when the cursor ends in the left upper corner and dont move anywhere else (the button works fine thought :) )
Anybody have any other ideas?

Thx for everything....

---

### Post by techno-mole on 2010-06-04
if you are running 10.4 (lucid) you no longer need to edit fdi files, all you need to do is install the driver from the ppa and then if you want adjust a file to suit your needs, see [here]("http://ubuntuforums.org/showpost.php?p=8515936&postcount=1")

I have had my tablet running for a couple of weeks on 64bit lucid and had no issues with it, I don't know about the pressure sensitivity in photoshop under wine, but I have cs2 running on a virtual machine and I seem to get pressure sensitivity on that, as well as elements.

I would also recommend removing all aspects of the wizardpen driver before trying the steps in the post I linked to, also you should check in synaptic for xserver-xorg-input-wacom this gets installed by default for me, it may be the same for others, you can remove it and the other package that it says will also be removed as well.

---

### Post by swapnil_bhartiya on 2010-06-04
I infact started with adding ppa to the repository and then installing the driver, but nothing happened...it stays at the right corner. I have given up hope on this matter...:(

---

### Post by techno-mole on 2010-06-04
have you looked at the launchpad page for wizardpen ? there was a bug on there that kept the cursor in the top left, but its fixed now, at least for genius tablets I guess, I would have thought it would also be fixed for others, which version of ubuntu are you using ?

launchpad bug - [https://bugs.launchpad.net/wizardpen/+bug/526003]("https://bugs.launchpad.net/wizardpen/+bug/526003")

if you arent having any luck I would recommend posting a bug on launchpad under the wizardpen section.

---

### Post by dr_smit on 2010-06-13
Mine remains stuck in top left corner..
UC LOGIC WP8060 Brand iBall

---

### Post by drpjkurian on 2010-06-18
> **techno-mole said:**
> have you looked at the launchpad page for wizardpen ? there was a bug on there that kept the cursor in the top left, but its fixed now, at least for genius tablets I guess, I would have thought it would also be fixed for others, which version of ubuntu are you using ?

launchpad bug - [https://bugs.launchpad.net/wizardpen/+bug/526003]("https://bugs.launchpad.net/wizardpen/+bug/526003")

if you arent having any luck I would recommend posting a bug on launchpad under the wizardpen section.

Hi
I also have the same problem of cursor stucking in the left corner. But the solution mentioned in the launchpad did not solve my problem, Instead I lost my keypad function. I had to rewrite my xorg.config

---

### Post by techno-mole on 2010-06-18
I'm beginning to think this is a specific tablet issue, all the iball tablets seem to have the same issue, the genius ones seem to be fine (at least from what I can tell) by specific I mean there seems to be something about this tablet that operates in a slightly different way to the genius tablets, although I'm stuffed if I know what the difference is.

I shouldn't really comment as I'm using linux mint at the moment, fancied a change (and it's not that different to ubuntu anyway) but I installed the wizardpen driver this morning and it runs fine, no issues, which again points at there being a slight difference in the operation of the 2 tablet makes.

Again all I can suggest is post a bug report on launchpad and include your xorg logs.

---

### Post by Favux on 2010-06-18
Hi,

> I'm beginning to think this is a specific tablet issue, all the iball tablets seem to have the same issue:  i.e. "cursor stuck in the left corner"
That's exactly the sort of thing DoctorMO is trying to get feedback from testers on to improve the driver.  See:  [https://launchpad.net/~wizardpen-testers](https://launchpad.net/~wizardpen-testers)

---

### Post by Offoffoff on 2010-06-21
wizardpen driver does not work in my configuration... Cursor runs to the left upper corner and stands there.

I have 
```
5543:0004 UC-Logic Technology Corp. Genius MousePen 5x4 Tablet
```
as lsusb said.
```
N: Name="UC-LOGIC Tablet WP5540U"
```
as grep -i  name /proc/bus/input/devices said.
And market name is Genius Easypen i405.
And I have Ubuntu 10.04.
I have two displays. I think this is a problem for that driver. Because it works with my notebook. Or Ubuntu version - at notebook I have Ubuntu 9.10.

---

### Post by drpjkurian on 2010-06-23
> **Offoffoff said:**
> wizardpen driver does not work in my configuration... Cursor runs to the left upper corner and stands there.

I have 
```
5543:0004 UC-Logic Technology Corp. Genius MousePen 5x4 Tablet
```
as lsusb said.
```
N: Name="UC-LOGIC Tablet WP5540U"
```
as grep -i  name /proc/bus/input/devices said.
And market name is Genius Easypen i405.
And I have Ubuntu 10.04.
I have two displays. I think this is a problem for that driver. Because it works with my notebook. Or Ubuntu version - at notebook I have Ubuntu 9.10.

Hi
Hope it will be resolved

---

### Post by huit_six on 2010-06-23
Hello,
I use lucid lynx (amd64, cleanly updated), with a genius tablet which by typing :
```
cat /sys/bus/usb/devices/*/product
```
is detected as :
```
Tablet WP5540U
```
I installed the driver with apt-get using the ppa indicated in the [tutorial from the doc]("https://help.ubuntu.com/community/TabletSetupWizardpen") (from ppa:doctormo/xorg-wizardpen)
I restarted and the cursor moves but it seems to jump between 2 positions fast and hence isn't usable at all.
To be clearer, here's an example of what I got with GIMP while trying to trace a simple strait line :
[IMG]http://carriernicolas.open-web.fr/ressources/images/externe/bug_tablette.png[/IMG]
:confused:
Do you have any idea of what I can do ? Does anybody experiments the same bug ?
Thank you !

---

### Post by Robbyx on 2010-06-23
I have just bought the Trust 1526 tablet and it does not work at all. When I started the computer it did originally light up the led and immediately go out, and  it did not react to the pen. That has not changed since I have installed the wizardpen drivers.

Can anyones please suggest what  I have done wrongly?

I have followed the advice here except I am using the synaptic version of wizardpen in Lucid.

 
I can see from the following it is properly installed:

```
rob@rob-desktop:~$ ls /usr/lib/xorg/modules/input/wizardpen_drv.*
/usr/lib/xorg/modules/input/wizardpen_drv.la
/usr/lib/xorg/modules/input/wizardpen_drv.so
rob@rob-desktop:~$ 


```

Device Name

```
grep -i name /proc/bus/input/devices
N: Name="Power Button"
N: Name="Power Button"
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="UVC Camera (046d:0990)"
N: Name="HDA Digital PCBeep"
N: Name="Logitech USB-PS/2 Optical Mouse"
N: Name="C-Media USB Headphone Set  "
N: Name="UC-LOGIC Tablet WP5540U"
rob@rob-desktop:~$ 

```

gksudo gedit  /etc/hal/fdi/policy/99-x11-wizardpen.fdi

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP5540U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="info.product" type="string">stylus</merge>
		<merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
                <merge key="input.x11_options.MaxX" type="string">29405</merge>
                <merge key="input.x11_options.MaxY" type="string">29671</merge>
      
                </match>
            </device>
            </deviceinfo>
```


Robin
PS
Is it possible the failure is to do with my upgrading to Lucid rather than a fresh install? I am wondering if I am still using Xorg and thus it needs adjusting as well.

---

### Post by huit_six on 2010-06-26
Well the problem seems to be solved. But it's quite weird.
I edited the /etc/X11/xorg.conf file (generated by the installation of ATI proprietary driver, and edited automatically by the installation of wizardpen driver) and commented the line 
InpudDevice "Wizardpen Tablet" "AlwaysCore"
in the ServerLayout section. and after reloading gdm, it worked. It seems like the tablet was detected two times, with 2 different calibrations, hence my problem.

---

### Post by Favux on 2010-06-26
Hi huit_six,

Interesting.  "AlwaysCore" and "SendCoreEvent" are obsolete with Lucid's Xserver 1.7.  But that's the first time I've seen it cause a problem.  You can just remove them, like you did.

---

### Post by Robbyx on 2010-06-26
Any chance of a reply to my message no 187?

I have looked in the xorg.conf and their is no mention of wizardpen.

---

### Post by huit_six on 2010-06-27
> **Favux said:**
> Hi huit_six,

Interesting.  "AlwaysCore" and "SendCoreEvent" are obsolete with Lucid's Xserver 1.7.  But that's the first time I've seen it cause a problem.  You can just remove them, like you did.
Hello Favux,
Thank you for the information, so it could be a bug from the installer of the proprietary ATI driver ? I have to add that it's a fresh Lucid install.

I think I will try to move the xorg.conf to see if the tablet works well, but I fear that my dual screen will not work.
I'll see it when i'll be back home.

@Robbyx : Don't have any solution but you could try to launch a lucid live cd and install the tablet to see if it works and if the problem comes from the fact that you upgraded rather than fresh installed.

---

### Post by enixon on 2010-06-27
I recently switched from ubuntu 9 to 10.04 by installing in a new partition. These install instructions worked fine on 9 and I am attempting to replicate the results on 10.

However, after this line
```
./configure --with-xorg-module-dir=/usr/lib/xorg/modules
        make && sudo make install
```
It produces the following errors at the bottom of the output.
I simply don't know where to go from here. I've googled the errors only to find people not experiencing the same thing.

Any help would be sincerely appreciated.

```

eliot@blackLaptop:~/Desktop/wizardpen-0.7.0-alpha2$ sudo vim /etc/hal/fdi/policy/99-x11-wizardpen.fdi
sudo: vim: command not found
eliot@blackLaptop:~/Desktop/wizardpen-0.7.0-alpha2$ sudo gedit /etc/hal/fdi/policy/99-x11-wizardpen.fdi
eliot@blackLaptop:~/Desktop/wizardpen-0.7.0-alpha2$ gksudo gedit  /etc/hal/fdi/policy/99-x11-wizardpen.fdi
eliot@blackLaptop:~/Desktop/wizardpen-0.7.0-alpha2$ cd
eliot@blackLaptop:~$ sudo aptitude install xutils libx11-dev libxext-dev build-essential \
>             xautomation xinput xserver-xorg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

eliot@blackLaptop:~$ cd Desktop
eliot@blackLaptop:~/Desktop$ cd wizardpen-0.7.0-alpha2
eliot@blackLaptop:~/Desktop/wizardpen-0.7.0-alpha2$ ./configure --with-xorg-module-dir=/usr/lib/xorg/modules
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... 
yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking if RANDR is defined... yes
checking if XINPUT is defined... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XORG... yes
checking for ANSI C header files... (cached) yes
checking linux/input.h usability... yes
checking linux/input.h presence... yes
checking for linux/input.h... yes
checking sysfs/libsysfs.h usability... no
checking sysfs/libsysfs.h presence... no
checking for sysfs/libsysfs.h... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating man/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
eliot@blackLaptop:~/Desktop/wizardpen-0.7.0-alpha2$         make && sudo make install
make  all-recursive
make[1]: Entering directory `/home/eliot/Desktop/wizardpen-0.7.0-alpha2'
Making all in src
make[2]: Entering directory `/home/eliot/Desktop/wizardpen-0.7.0-alpha2/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..     -g -O2 -fvisibility=hidden -I/usr/include/xorg -I/usr/include/pixman-1    -I../src -MT wizardpen.lo -MD -MP -MF .deps/wizardpen.Tpo -c -o wizardpen.lo wizardpen.c
 gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -fvisibility=hidden -I/usr/include/xorg -I/usr/include/pixman-1 -I../src -MT wizardpen.lo -MD -MP -MF .deps/wizardpen.Tpo -c wizardpen.c  -fPIC -DPIC -o .libs/wizardpen.o
wizardpen.c: In function 'DeviceInit':
wizardpen.c:636: warning: passing argument 3 of 'InitButtonClassDeviceStruct' from incompatible pointer type
/usr/include/xorg/input.h:290: note: expected 'Atom *' but argument is of type 'unsigned char *'
wizardpen.c:636: error: too few arguments to function 'InitButtonClassDeviceStruct'
wizardpen.c:662: warning: passing argument 3 of 'InitValuatorClassDeviceStruct' makes pointer from integer without a cast
/usr/include/xorg/input.h:296: note: expected 'Atom *' but argument is of type 'unsigned int'
wizardpen.c:662: error: too few arguments to function 'InitValuatorClassDeviceStruct'
wizardpen.c:677: error: too few arguments to function 'InitValuatorAxisStruct'
wizardpen.c:685: error: too few arguments to function 'InitValuatorAxisStruct'
wizardpen.c:693: error: too few arguments to function 'InitValuatorAxisStruct'
make[2]: *** [wizardpen.lo] Error 1
make[2]: Leaving directory `/home/eliot/Desktop/wizardpen-0.7.0-alpha2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/eliot/Desktop/wizardpen-0.7.0-alpha2'
make: *** [all] Error 2


```

---

### Post by enixon on 2010-06-27
I notice there is a package called xserver-xorg-input-wizardpen in the synaptic package manager. Should I be using that instead of this guide?

---

### Post by Favux on 2010-06-27
Hi enixon,

For Lucid (10.4) you want to use the xserver-xorg-input-wizardpen - 0.7.3-1ubuntu1 driver at:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+packages](https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+packages)

---

### Post by enixon on 2010-06-28
Should I be downloading the deb file from that link and using the deb installer, or downloading the file and using the directions on this forum with the new version instead of the old? Or maybe just use synaptic package manager? I've done all three and none seem to work. Is this common, It must be some thing stupid I'm doing. Thanks for your time.

---

### Post by Favux on 2010-06-28
The deb should be fine.

Maybe you're not matching in the 70-wizardpen.conf in /usr/lib/X11/xorg.conf.d/.

---

### Post by enixon on 2010-06-28
OK I found it, this is what it says. What is supposed to match within this file to what? 
> 
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver "wizardpen"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/mouse*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSection

---

### Post by switzel on 2010-06-30
Hi,

I'm trying to get a Trust TB-6300 (internal "UC-LOGIC Tablet WP8060U") to run on Debian Squeeze and one of my problems is that all instructions I found are for some Ubuntu version rather than for some xorg/udev/whatever version.

/var/log/Xorg.0.log says:
```

(II) config/udev: Adding input device "UC-LOGIC Tablet WP8060U" (/dev/input/event3)
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
    compiled for 1.7.3.902, module version = 0.10.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/input/event3"
(II) "UC-LOGIC Tablet WP8060U": type not specified, assuming 'stylus'.
(II) "UC-LOGIC Tablet WP8060U": other types will be automatically added.
(**) "UC-LOGIC Tablet WP8060U": always reports core events
(II) "UC-LOGIC Tablet WP8060U": hotplugging dependent devices.
(II) "UC-LOGIC Tablet WP8060U": hotplugging completed.
(II) XINPUT: Adding extended input device ""UC-LOGIC Tablet WP8060U"" (type: STYLUS)
(--) "UC-LOGIC Tablet WP8060U": using pressure threshold of 61 for button 1
(--) "UC-LOGIC Tablet WP8060U": Wacom Unknown USB tablet speed=38400 maxX=16000 maxY=12000 maxZ=1023 resX=1016 resY=1016  tilt=enabled
(--) "UC-LOGIC Tablet WP8060U": top X=0 top Y=0 bottom X=16000 bottom Y=12000 resol X=1016 resol Y=1016

```This is strange for two reasons: it uses the driver "wacom" while it should use "wizardpen". And it does not configure /dev/input/mouse1 as a mouse (which I think it should). As far as I understand it, the driver should (in my case still) be determined by /lib/udev/rules.d/67-xorg-wizardpen.rules which reads:
```

# to configure the active area, pressure sensitivity and other settings see
# /etc/udev/rules.d/70-xorg-wizardpen-settings.rules

ACTION!="add|change", GOTO="xorg_wizardpen_end"
SUBSYSTEM!="input", GOTO="xorg_wizardpen_end"

# KYE Systems Corp Wide Screen Design Tablet TB-7300
ENV{ID_VENDOR_ID}=="0458",  ENV{ID_MODEL_ID}=="5003", ENV{x11_driver}="wizardpen"
# KYE Systems Corp Wide Screen Design Tablet TB-7300
ENV{ID_VENDOR_ID}=="0458",  ENV{ID_MODEL_ID}=="5004", ENV{x11_driver}="wizardpen"
# AceCad Corp Flair II GT-504
ENV{ID_VENDOR_ID}=="0460",  ENV{ID_MODEL_ID}=="0004", ENV{x11_driver}="wizardpen"

# UC-Logic Technology Corp
# SuperPen WP3325U Tablet
ENV{ID_VENDOR_ID}=="5543", ENV{ID_MODEL_ID}=="0002", ENV{x11_driver}="wizardpen"
# WP4030, Genius MousePen 4x3 Tablet/Aquila L1 Tablet
ENV{ID_VENDOR_ID}=="5543", ENV{ID_MODEL_ID}=="0003", ENV{x11_driver}="wizardpen"
# WP5540, Genius MousePen 5x4 Tablet
ENV{ID_VENDOR_ID}=="5543", ENV{ID_MODEL_ID}=="0004", ENV{x11_driver}="wizardpen"
# WP8060, Genius MousePen 8x6 Tablet, Trust TB-6300
ENV{ID_VENDOR_ID}=="5543", ENV{ID_MODEL_ID}=="0005", ENV{x11_driver}="wizardpen"
# Genius PenSketch 6x8 Tablet
ENV{ID_VENDOR_ID}=="5543", ENV{ID_MODEL_ID}=="0041", ENV{x11_driver}="wizardpen"
# Genius PenSketch 12x9 Tablet
ENV{ID_VENDOR_ID}=="5543", ENV{ID_MODEL_ID}=="0042", ENV{x11_driver}="wizardpen"
# Digital Organizer (may not exist)
ENV{ID_VENDOR_ID}=="5543", ENV{ID_MODEL_ID}=="6000", ENV{x11_driver}="wizardpen"
# Genius G-Note 5000
ENV{ID_VENDOR_ID}=="5543", ENV{ID_MODEL_ID}=="6001", ENV{x11_driver}="wizardpen"

# disable the /dev/input/mouseX device
ENV{x11_driver}=="wizardpen", KERNEL=="mouse*", ENV{x11_driver}=""

# Specify this device as a tablet to the xorg config
ENV{x11_driver}=="wizardpen", KERNEL=="event*", ENV{ID_INPUT.tags}="wizardpen"
ENV{x11_driver}=="wizardpen", KERNEL=="event*", ENV{ID_INPUT_TABLET}="1"

LABEL="xorg_wizardpen_end"

```Indeed lsusb gives:
```

Bus 001 Device 007: ID 5543:0005 UC-Logic Technology Corp. Genius MousePen 8x6 Tablet

```What am I missing? Thanks in advance for any help!
Stefan

---

### Post by switzel on 2010-06-30
Ok, now I upgraded xorg and it seems to notice the file

/usr/share/X11/xorg.conf.d/70-wizardpen.conf

I am now in the state that is already richly documented: cursor stays in the upper left corner. Is it correct that this has not yet been resolved?

Edit: setting MaxX etc. in /etc/X11/xorg.conf worked.

---

### Post by enixon on 2010-06-30
I ended up reinstalling ubuntu 9. I simply couldn't live without a tablet. Thanks any way for your help.

---

### Post by zuzkafuska on 2010-07-29
Hi guys, I'm a Ubuntu 10.04 Lucid Lynx newbie and I had the exact same problem as enixon: Despite my following the instructions the 0.7.0 driver simply wouldn't install and would spew (an identical) screenful of error messages. In the end I found the advice here at page 20 of the thread: I manually installed the 0.7.3 version from [https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+files/xserver-xorg-input-wizardpen_0.7.3-1ubuntu1_i386.deb](https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+files/xserver-xorg-input-wizardpen_0.7.3-1ubuntu1_i386.deb) and it worked wonders. Yahoo! 
(Although I wonder...shouldn't adding the PPA: doctorMO thingy to Software Sources and reloading have done the same thing? Coz it certainly didn't.)
Thanks a bunch! :KS I wish installing the driver weren't such a tiresome experience...having to rake for some bits of useful info in the forums and such :-(

---

### Post by AlexDS on 2010-07-31
Does anybody get to make his/her tablet work on ubuntu 10.10 ???

---

### Post by AlexDS on 2010-07-31
Do you have any idea if it works on ubuntu 10.10 (pre-release) ?

---

### Post by AlexDS on 2010-07-31
[QUOTE=drpjkurian;8384507]Hi Guys
In this thread you will come to know how to install wizardpen drivers for your Tablets and mousepen in plain and easy steps.

Wizardpen drivers are meant for following pen tablets. They are as following
# Acecad Flair II GT-504
# DigiPro 5.5×4” Graphics Tablet
# Digital Ink Pad (A4 format)
# G-pen
# Genius Wizardpen
# Genius Mousepen
# Genius
# iBall
# Manhattan
# Pentagram
# QWare
# Trust TB-3100
# Trust TB-5300
# Trust TB-6300
# iBall Tablet PF806
# AIPTEK HyperPen 10000 U ("UC-LOGIC TWA60")
# Medion MD 85673 USB Grafiktablett P82012
# Intellipen Pro(EPOS EPOS Pen Digitizer)
# NGS Draw Master Tablet (UC-LOGIC Tablet WP8060U)

Do you have any idea if it works on Ubuntu 10.10 (pre-release)???

---

### Post by drpjkurian on 2010-08-01
Wait and watch buddy

---

### Post by enixon on 2010-09-09
I've installed the new drivers zuzkafuska mentioned on 10.10. I currently have a tablet which works but only moves the mouse when I touch it as apposed to hover over the tablet with the pen. The buttons work, Just this one little detail to fix. Is there a calibration process for these new drivers I can use?
Thanks for your time.

---

### Post by techno-mole on 2010-09-13
That's more than I had under 10.10 all I got was the cursor moving to the top left all the time, different tablet though.
As far as I know it's not fixed yet ? but then the rc for 10.10 isn't out yet.

---

### Post by Tango91 on 2010-09-18
Hey there,

I've got a genius G-Pen F350 and i've managed to get it working well(almost). It tracks nicely and was properly calibrated from the get-go. The buttons work, but there is something strange happening.

the cursor can be moved until a any of the buttons (or the nib) is used to click on something, at which point the cursor will stay in place. 
Keeping the button pressed down and moving the stylus will drag whatever you clicked on until the button is released, at which point the cursor stops responding to the stylus movements.

To get the cursor to move again, you can click a button somewhere else on the tablet, and the cursor will jump there (and then you have the same problem again)
or you can lift the stylus out of the tablet's range (1-2 inches) and put it back, at which point it functions normally until you next click.

There are a few other guys i've seen with the same problem with this tablet, and any help would be appreciated.

Oh, i'm using 10.04, and the 9.04 'fix' doesn't seem to work.

Thanks, :)
Tango91

EDIT: i fixed it although i'm not sure how. the last thing i did was change both instances of  MatchDevicePath in 70-wizardpen.conf to "/dev/input/event6"

i'm not sure quite why this is favoured over the device name in this field, as specified in the howto, but it seems to work now. I've been playing with it for hours but apparently this was the magic combination.

i'll post the entirety of my 70-wizardpen.conf just in case anyone is in a similar situation.

Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event6"

    Option        "Device"    "/dev/input/event6"
    Option        "TopX"        "158"
    Option        "TopY"        "185"
    Option        "BottomX"    "10000"
    Option        "BottomY"    "6000"


   Driver "wizardpen"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event6"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSection

---

### Post by coffeeaddict_nl on 2010-10-02
Hi!

I just installed the wizardpen driver (from ppa:doctormo/xorg-wizardpen)  for 10.10 (x86_64). It works fine, but it killed the splashscreen/upstart

It just falls back to a regular linux login prompt. When i log in and run 'sudo service gdm start' from there I get a regular gdm login-screen and the tablet (a UC-Logic clone branded by Trust) works perfectly.

Any suggestions as to what is wrong or how to fix?

Many TIA!

---

### Post by radpal on 2010-10-28
Hi Dr. Kurian,

     I have installed WP8060U iball tablet on ubuntu and it is working fine. I want the pen to work on a specific application. Is this possible to do? 
     I have a browser based application and I want the pen to be active only in the writable area and should be inactive in other places. Basically i would like to map the tablet scope to a particular area in the screen. How do i go about?

Regards,
Radpal

---

### Post by unyuwarrior on 2010-10-31
hey, i'm using Genius easypen i405 and i'm running lucid lynx 32bit
before i use this tutorial everytime i use my pen the cursor always 
at the upside left corner,
and at the 6th step at this tutorial i got this 

audi@audi-supremeultimatethemostpowerfullandcoolestnetbook-laptop:~/Desktop/wizardpen-0.7.0-alpha2$ ./configure --with-xorg-module-dir=/usr/lib/xorg/modules

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking if RANDR is defined... yes
checking if XINPUT is defined... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XORG... yes
checking for ANSI C header files... (cached) yes
checking linux/input.h usability... yes
checking linux/input.h presence... yes
checking for linux/input.h... yes
checking sysfs/libsysfs.h usability... yes
checking sysfs/libsysfs.h presence... yes
checking for sysfs/libsysfs.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating man/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
audi@audi-supremeultimatethemostpowerfullandcoolestnetbook-laptop:~/Desktop/wizardpen-0.7.0-alpha2$         make && sudo make install
make  all-recursive
make[1]: Entering directory `/home/audi/Desktop/wizardpen-0.7.0-alpha2'
Making all in src
make[2]: Entering directory `/home/audi/Desktop/wizardpen-0.7.0-alpha2/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..     -g -O2 -fvisibility=hidden -I/usr/include/xorg -I/usr/include/pixman-1    -I../src -MT wizardpen.lo -MD -MP -MF .deps/wizardpen.Tpo -c -o wizardpen.lo wizardpen.c
 gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -fvisibility=hidden -I/usr/include/xorg -I/usr/include/pixman-1 -I../src -MT wizardpen.lo -MD -MP -MF .deps/wizardpen.Tpo -c wizardpen.c  -fPIC -DPIC -o .libs/wizardpen.o
wizardpen.c:219: warning: initializer-string for array of chars is too long
wizardpen.c: In function 'DeviceInit':
wizardpen.c:636: warning: passing argument 3 of 'InitButtonClassDeviceStruct' from incompatible pointer type
/usr/include/xorg/input.h:290: note: expected 'Atom *' but argument is of type 'unsigned char *'
wizardpen.c:636: error: too few arguments to function 'InitButtonClassDeviceStruct'
wizardpen.c:662: warning: passing argument 3 of 'InitValuatorClassDeviceStruct' makes pointer from integer without a cast
/usr/include/xorg/input.h:296: note: expected 'Atom *' but argument is of type 'unsigned int'
wizardpen.c:662: error: too few arguments to function 'InitValuatorClassDeviceStruct'
wizardpen.c:677: error: too few arguments to function 'InitValuatorAxisStruct'
wizardpen.c:685: error: too few arguments to function 'InitValuatorAxisStruct'
wizardpen.c:693: error: too few arguments to function 'InitValuatorAxisStruct'
make[2]: *** [wizardpen.lo] Error 1
make[2]: Leaving directory `/home/audi/Desktop/wizardpen-0.7.0-alpha2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/audi/Desktop/wizardpen-0.7.0-alpha2'
make: *** [all] Error 2

is it right?? because when i use the next one,it says there's no directory?

---

### Post by tom67 on 2010-11-20
> **Tango91 said:**
> 
...
To get the cursor to move again, you can click a button somewhere else on the tablet, and the cursor will jump there (and then you have the same problem again)
or you can lift the stylus out of the tablet's range (1-2 inches) and put it back, at which point it functions normally until you next click.
...
I fixed it although i'm not sure how. the last thing i did was change both instances of  MatchDevicePath in 70-wizardpen.conf to "/dev/input/event6"
...
 I've been playing with it for hours but apparently this was the magic combination.
...

I had the same problem, spending whole day on the net. Having ubuntu 10.10 (maverick) and Waltop family (G-Pen F610) tablet, for me the magic trick was to remove
MatchTag    "wizardpen" 
from 70-wizardpen.conf file.
Now it looks like:
```

Section "InputClass"
   Identifier      "wizardpen"
   MatchIsTablet   "on"
   MatchDevicePath "/dev/input/event*"
   Driver          "wizardpen"
   Option          "Device"        "/dev/input/event6"
   Option          "TopX"          "152"
   Option          "TopY"          "42"
   Option          "BottomX"       "20000"
   Option          "BottomY"       "12500"
EndSection

Section "InputClass"
   Identifier      "wizardpen ignore mouse dev"
   MatchDevicePath "/dev/input/mouse*"
   Option          "MouseSpeed" "16"
   Option          "ignore"     "true"
   Driver          ""

```

---

### Post by F15h3r on 2010-11-25
> **tom67 said:**
> I had the same problem, spending whole day on the net. Having ubuntu 10.10 (maverick) and Waltop family (G-Pen F610) tablet, for me the magic trick was to remove
MatchTag    "wizardpen" 
from 70-wizardpen.conf file.
Now it looks like:
```

Section "InputClass"
   Identifier      "wizardpen"
   MatchIsTablet   "on"
   MatchDevicePath "/dev/input/event*"
   Driver          "wizardpen"
   Option          "Device"        "/dev/input/event6"
   Option          "TopX"          "152"
   Option          "TopY"          "42"
   Option          "BottomX"       "20000"
   Option          "BottomY"       "12500"
EndSection

Section "InputClass"
   Identifier      "wizardpen ignore mouse dev"
   MatchDevicePath "/dev/input/mouse*"
   Option          "MouseSpeed" "16"
   Option          "ignore"     "true"
   Driver          ""

```

Hey, i had exactly the same problem, and also removed MatchTag. Now my Genius G-pen M712 works perfectly on Maverick. thanks for solution!
Regards!

---

### Post by Antricola on 2011-01-28
Hi, I have been tried and I have a problem with the step 8.

When I write:
 
sudo vim /etc/hal/fdi/policy/99-x11-wizardpen.fdi
Said: sudo: vim: command not found

Anybody can help me?

Thanks...

---

### Post by schkovich on 2011-01-28
> **Antricola said:**
> When I write:
sudo vim /etc/hal/fdi/policy/99-x11-wizardpen.fdi
Said: sudo: vim: command not found

Try instead: ```
sudo nano /etc/hal/fdi/policy/99-x11-wizardpen.fdi
```

---

### Post by Locoluis on 2011-02-07
Just to report. I'm using Debian Squeeze.

I used the wizardpen driver from doctormo's ppa for Ubuntu Lucid. It installed flawlessly.

I also followed the instructions at [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

But I couldn't get my tablet (UC-LOGIC Tablet WP8060U) to work correctly. The pointer stayed at top left of the screen.

What else did I do to make it work? I noticed the following lines in my Xorg.0.log:

(**) UC-LOGIC Tablet WP8060U: Applying InputClass "evdev pointer catchall"
(**) UC-LOGIC Tablet WP8060U: Applying InputClass "evdev tablet catchall

That meant it didn't match the InputClass specification that was in the howto, and used a generic one. So I commented the "MatchVendor" line in the InputClass section, restarted X, and it started working.

I hope this helps someone else.

---

### Post by G@@D on 2011-02-12
Does anyone get working Genius Easypen m610? I can't get it works on my Linux Mint 10, I fallow the instructions here [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen), but it's stil not working. I'm new in linux, please somebody help me with this problem.
My 70-wizardpen.conf looks like that now:

Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/by-id/6x10 Tablet"
   Driver "wizardpen"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/by-id/6x10 Tablet"
   Driver "wizardpen"
EndSection

---

### Post by ubuntosh on 2011-03-25
I can't get my UC-LOGIC Tablet WP8060U to work with 10.10.

I followed your guide and when I try to save the .fdi file a message appears saying that this file does not exist. 

What can I do?

---

### Post by madkapitolist on 2011-03-26
> **tom67 said:**
> I had the same problem, spending whole day on the net. Having ubuntu 10.10 (maverick) and Waltop family (G-Pen F610) tablet, for me the magic trick was to remove
MatchTag    "wizardpen" 
from 70-wizardpen.conf file.
Now it looks like:
```

Section "InputClass"
   Identifier      "wizardpen"
   MatchIsTablet   "on"
   MatchDevicePath "/dev/input/event*"
   Driver          "wizardpen"
   Option          "Device"        "/dev/input/event6"
   Option          "TopX"          "152"
   Option          "TopY"          "42"
   Option          "BottomX"       "20000"
   Option          "BottomY"       "12500"
EndSection

Section "InputClass"
   Identifier      "wizardpen ignore mouse dev"
   MatchDevicePath "/dev/input/mouse*"
   Option          "MouseSpeed" "16"
   Option          "ignore"     "true"
   Driver          ""

```


Hi Im having the same problem as you and tried taking out that line from the conf file, however i still cannot create that fdi file b/c the directory does not exist. Any advice?

---

### Post by Favux on 2011-03-26
Karmic is the last release of Ubuntu that uses HAL/.fdi.  Starting with Lucid things change to xorg.conf.d/.conf file.

You probably need a keyword for the match with MatchProduct to place it on the WizardPen driver.  Enter in a terminal:
```
xinput list
```
The line that has your tablet will have keyword(s) you can use for the match in the 70-wizardpen.conf

---

### Post by Sef on 2011-03-26
Moved to T & T. Another Howto thread.

---

### Post by Ethcelon on 2011-04-05
hello, I'm new to ubuntu and i'm tryin to install my trust-5300 tablet. When i type the ./configure --with-xorg-module-dir=/usr/lib/xorg/modules
make && sudo make install

[FONT=Verdana]I get this..[/FONT]
make  all-recursive
make[1]: Entering directory `/home/janani/Desktop/xorg-input-wizardpen-0.3.8.0'
Making all in src
make[2]: Entering directory `/home/janani/Desktop/xorg-input-wizardpen-0.3.8.0/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..     -g -O2 -fvisibility=hidden -I/usr/include/xorg -I/usr/include/pixman-1    -I../src -MT wizardpen.lo -MD -MP -MF .deps/wizardpen.Tpo -c -o wizardpen.lo wizardpen.c
libtool: Version mismatch error.  This is libtool 2.2.6 Debian-2.2.6a-4, but the
libtool: definition of this LT_INIT comes from libtool 2.2.6b.
libtool: You should recreate aclocal.m4 with macros from libtool 2.2.6 Debian-2.2.6a-4
libtool: and run autoconf again.
make[2]: *** [wizardpen.lo] Error 63
make[2]: Leaving directory `/home/janani/Desktop/xorg-input-wizardpen-0.3.8.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/janani/Desktop/xorg-input-wizardpen-0.3.8.0'
make: *** [all] Error 2

What am I doing wrong?

---

### Post by Favux on 2011-04-05
Hi Ethcelon,

Welcome to Ubuntu forums!

You don't mention what release of Ubuntu you are using.  Is that because you're on a Debian release?  I don't recognize that version of the WizardPen driver.  Where did you get it from?  You should be able to use DoctorMO's PPA:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen](https://launchpad.net/~doctormo/+archive/xorg-wizardpen)

The error seems to be from a xorg-macros mismatch.  For example the version is 1.5 in Lucid and some drivers now need version 1.8.  In Ubuntu though the macros are in the xutils-dev package, so I'm not sure.  You can get 1.8 directly from Xorg:  [http://xorg.freedesktop.org/releases/individual/util/util-macros-1.8.0.tar.bz2](http://xorg.freedesktop.org/releases/individual/util/util-macros-1.8.0.tar.bz2)  If you use the:
```
./configure --prefix=/usr

```
flag when you compile it will install the macros in the correct /usr/share/aclocal/xorg-macros.m4 directory.

I suppose it could just be a libtool mismatch so maybe try this first:
```

sudo apt-get update

sudo apt-get install libtool

sudo apt-get upgrade

```

---

### Post by mont29 on 2011-04-12
Hi Ethcelon

I’m under Debian Testing and, since the kernel was updated, I had to rebuild that driver… And I just run into the same error !

In fact, it seems the default configure script (built under ubuntu I guess) is not compatible with debian’s autotools version, so you just have to rebuild it by running ```
./autogen.sh
``` (and then the standard make && su make install…).

However, I wonder why you stick to 0.3.8 ? I used 0.8.0 (trunk version), but you could at least use stable 0.7.4 !

---

### Post by orimosenzon on 2011-04-26
Hi! 

I'm trying to make my Genius's EasyPen i405 work on my lucid 10.04 system. while trying: 
./configure --with-xorg-module-dir=/usr/lib/xorg/modules make && sudo make install

I get the following: 

---configure: WARNING: you should use --build, --host, --target
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... Invalid configuration `make': machine `make' not recognized
configure: error: /bin/bash ./config.sub make failed

(o: 
I tried to reinstall the build-essential package but it didn't help. 

Any idea would be greatly appricieted..

---

### Post by skotadopsyxos on 2011-05-24
anybody here running natty,having a tablet with bundled mouse that works as good as the stylus? if yes can you please post config files (xorg.conf.d and udev/rules.d)

---

### Post by Silvernail on 2011-07-17
Message deleted because it became irrelevant. I found pre-compiled drivers. My Digipro WP8060 drawing tablet works.

---

### Post by Silvernail on 2011-07-19
Works out of the box with Gimp, Pencil, Open Office Drawing, Agave, Inkscape, Krita, and Ktoon. No go on  Blender, Scribus, but that may be just a configuration problem.

---

### Post by random_jc on 2011-08-28
Hi everybody,

I am trying to install a Genius EasyPen i405x on Ubuntu 10.4. Control of the position of the cursor is working fine, but the action of pressing with the pen on the tablet does not do what I would like it to. For instance, I cannot draw with gimp, pressure does nothing at all. Yet, under certain circumstances pressure does have an effect. For instance, I can use pressure to open the "System" menu usually appearing on the top of Ubuntu desktop, I can open Gimp, click on "File > Open" using pressure. But then things stop to work, I cannot click OK (although pressure "highlights" the button I want to click on), and then nothing happens when I try to draw something.

Under firefox, pressure has the effect of the "go back" button (while some button of the pen does the "go forward" button). 

So my problem is this: how can I have my computer understand what I mean when I press on the tablet with the pen ?

I followed instructions from [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen), using "method 1" to install the driver. I think that driver installation went well, since 
```

ls /usr/lib/xorg/modules/input/wizardpen_drv.*

```gives what it should.

Then I messed up /usr/lib/X11/xorg.conf.d/70-wizardpen.conf, which at first looked like this :
```

Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver "wizardpen"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/mouse*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSection

```to which i tried to add various things, ending up with something like this
```

Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/by-id/usb-Genius_EasyPen_i405X-event-mouse"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver "wizardpen"
   Option "SendCoreEvents" "true"
   Option "TopX" "2199"
   Option "TopY" "3598"
   Option "BottomX" "30325"
   Option "BottomY" "29278"
   Option "TopZ" "10"
   Option "BottomZ" "1023"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/by-id/usb-Genius_EasyPen_i405X-mouse"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSection

```But it did not change anything. I also tried to create some .fdi file in /etc/hal/fdi/policy/, but if I understood correctly what people said here, I should not do this with my Ubuntu 10.4. In any case, it didn't work either.

So I'm coming short of ideas to solve the problem... Any sugestions ?

Maybe a look at the end of my /var/log/Xorg.0.log may help people :
```

(II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event11)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic (/dev/input/event12)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic (/dev/input/event13)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event14)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Genius EasyPen i405X (/dev/input/event6)
(**) Genius EasyPen i405X: Applying InputClass "evdev pointer catchall"
(**) Genius EasyPen i405X: Applying InputClass "evdev keyboard catchall"
(**) Genius EasyPen i405X: Applying InputClass "evdev tablet catchall"
(**) Genius EasyPen i405X: always reports core events
(**) Genius EasyPen i405X: Device: "/dev/input/event6"
(II) Genius EasyPen i405X: Found 10 mouse buttons
(II) Genius EasyPen i405X: Found scroll wheel(s)
(II) Genius EasyPen i405X: Found relative axes
(II) Genius EasyPen i405X: Found x and y relative axes
(II) Genius EasyPen i405X: Found absolute axes
(II) Genius EasyPen i405X: Found x and y absolute axes
(II) Genius EasyPen i405X: Found absolute tablet.
(II) Genius EasyPen i405X: Found keys
(II) Genius EasyPen i405X: Configuring as tablet
(II) Genius EasyPen i405X: Configuring as keyboard
(**) Genius EasyPen i405X: YAxisMapping: buttons 4 and 5
(**) Genius EasyPen i405X: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Genius EasyPen i405X" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "ch"
(**) Option "xkb_variant" "fr"
(**) Option "xkb_options" "grp:alts_toggle"
(WW) Genius EasyPen i405X: touchpads, tablets and touchscreens ignore relative axes.
(II) Genius EasyPen i405X: initialized for absolute axes.
(II) config/udev: Adding input device Genius EasyPen i405X (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "ch"
(**) Option "xkb_variant" "fr"
(**) Option "xkb_options" "grp:alts_toggle"
(II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/event10)
(**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev pointer catchall"
(**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev touchpad catchall"
(**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event10"
(II) AlpsPS/2 ALPS DualPoint TouchPad: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS DualPoint TouchPad: y-axis range 0 - 767
(II) AlpsPS/2 ALPS DualPoint TouchPad: pressure range 0 - 127
(II) AlpsPS/2 ALPS DualPoint TouchPad: finger width range 0 - 0
(II) AlpsPS/2 ALPS DualPoint TouchPad: buttons: left right middle
(--) AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
(**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration profile 0
(**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration factor: 2.000
(**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration threshold: 4
(--) AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
(II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device DualPoint Stick (/dev/input/event9)
(**) DualPoint Stick: Applying InputClass "evdev pointer catchall"
(**) DualPoint Stick: always reports core events
(**) DualPoint Stick: Device: "/dev/input/event9"
(II) DualPoint Stick: Found 3 mouse buttons
(II) DualPoint Stick: Found relative axes
(II) DualPoint Stick: Found x and y relative axes
(II) DualPoint Stick: Configuring as mouse
(**) DualPoint Stick: YAxisMapping: buttons 4 and 5
(**) DualPoint Stick: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "DualPoint Stick" (type: MOUSE)
(II) DualPoint Stick: initialized for relative axes.
(II) config/udev: Adding input device DualPoint Stick (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event7)
(**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
(**) ThinkPad Extra Buttons: always reports core events
(**) ThinkPad Extra Buttons: Device: "/dev/input/event7"
(II) ThinkPad Extra Buttons: Found keys
(II) ThinkPad Extra Buttons: Configuring as keyboard
(II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "ch"
(**) Option "xkb_variant" "fr"
(**) Option "xkb_options" "grp:alts_toggle"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) intel(0): EDID vendor "LEN", prod id 16500
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0  102.00  1440 1488 1520 1836  900 903 909 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1440x900"x0.0   85.00  1440 1488 1520 1836  900 903 909 926 -hsync -vsync (46.3 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16500
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0  102.00  1440 1488 1520 1836  900 903 909 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1440x900"x0.0   85.00  1440 1488 1520 1836  900 903 909 926 -hsync -vsync (46.3 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16500
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0  102.00  1440 1488 1520 1836  900 903 909 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1440x900"x0.0   85.00  1440 1488 1520 1836  900 903 909 926 -hsync -vsync (46.3 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16500
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0  102.00  1440 1488 1520 1836  900 903 909 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1440x900"x0.0   85.00  1440 1488 1520 1836  900 903 909 926 -hsync -vsync (46.3 kHz)

```In case it helps, my computer is a laptop with touchpad and trackpoint. 

Many thanks for your help !

---

### Post by Favux on 2011-08-28
Hi random_jc,

Welcome to Ubuntu forums!

According to your Xorg.0.log the tablet hasn't been matched to the WizardPen X driver:
```
(II) config/udev: Adding input device Genius EasyPen i405X (/dev/input/event6)
(**) Genius EasyPen i405X: Applying InputClass "evdev pointer catchall"
(**) Genius EasyPen i405X: Applying InputClass "evdev keyboard catchall"
(**) Genius EasyPen i405X: Applying InputClass "evdev tablet catchall"
(**) Genius EasyPen i405X: always reports core events
(**) Genius EasyPen i405X: Device: "/dev/input/event6"

```
Instead it has been picked up by the evdev X driver, specifically the "evdev tablet catchall" snippet.

Let's check your tablets vendor and product ID with:
```
lsusb
```
in a terminal.  Post the output line with the tablet in it.  Let's also see what keywords xinput is seeing and if they are the problem with the match.  Run this command in a terminal.
```
xinput list
```
And post the output.

---

### Post by random_jc on 2011-08-28
Thanks for your warm welcome, and for your dedication to helping people with their graphic tablets.

Here is what I get from the first command:

```

:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0458:5010 KYE Systems Corp. (Mouse Systems) 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a5c:2145 Broadcom Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 08ff:2810 AuthenTec, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 17ef:4807 Lenovo 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```and now from the second one:
```

:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Genius EasyPen i405X                        id=10    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad            id=12    [slave  pointer  (2)]
&#9116;   &#8627; DualPoint Stick                             id=13    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; UVC Camera (17ef:4807)                      id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=14    [slave  keyboard (3)]


```

---

### Post by Favux on 2011-08-28
Sure.  :)

It's a KYE:
```
Bus 006 Device 002: ID 0458:5010 KYE Systems Corp. (Mouse Systems) 
```
And it looks like we need to add a keyword since we're seeing:
```
&#9116;   &#8627; Genius EasyPen i405X                        id=10    [slave  pointer  (2)]

```
I guess i405X would be the most specific so then the 70-wizardpen.conf turns into something like this:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|i405X|Ace Cad"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|i405X|Ace Cad"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```

---

### Post by random_jc on 2011-08-29
Hi,

I copy-pasted the 70-wizardpen.conf you proposed, but the behavior is unchanged. The lines you quoted from my Xorg.0.log in message #230 are still there, except that "event6" has changed for "event7".

---

### Post by random_jc on 2011-08-29
Well, I don't think it has any relevance at all, but after shuting down the computer completely and restarting it (instead of doing a "restart"), I got back to the "event6" version of Xorg.0.log.

---

### Post by Favux on 2011-08-29
Hi random_jc,

Yes, the event number can change which is why you want to match to event* rather than a specific event #.

Assuming the WizardPen driver installed correctly (although it is getting a little more likely there was a problem with that) then let's try:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchProduct "i405X"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchProduct "i405X"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```
If we're lucky this will get the tablet on the WizardPen X driver and off the evdev driver.

---

### Post by random_jc on 2011-08-29
Hi,

so the new 70-wizardpen.conf you proposed changes a bit the effects of pressing and of the buttons, but not in the way we hope. In fact, pressing doesn't have any effect with the new version, while the behaviour of the buttons changed. Anyways, the Xorg.0.log continues to look like in message #230.

The first thing I did with the tablet was to plug it in, before installing any driver. Could it be that when plugged for the first time, it was matched permanently with the wrong driver ?

---

### Post by Favux on 2011-08-29
Interesting thought, but no that isn't how it works.  Can you give me a little more description.  What did the stylus buttons start doing?  And what does *xinput list* and:
```
xinput list-props "Genius EasyPen i405X"
```
look like?

I need to see you Xorg.0.log in case you missed something in the excerpt.  Right click on it and compress it with Create Archive.  Attach it to your next post with Manage Attachments below.

---

### Post by random_jc on 2011-08-29
One of the stylus buttons does a "middle click" and the other one a "right click". Here is the answer to the command you asked:

```

:~$ xinput list-props "Genius EasyPen i405X"
Device 'Genius EasyPen i405X':
    Device Enabled (125):    1
    Device Accel Profile (245):    0
    Device Accel Constant Deceleration (246):    1.000000
    Device Accel Adaptive Deceleration (248):    1.000000
    Device Accel Velocity Scaling (249):    10.000000

```

and attached is my Xorg.0.log.

Many thanks again.

---

### Post by random_jc on 2011-08-29
Well, in fact I was not correct when I said my Xorg.0.log did not change. It continues to contain
```

(**) Genius EasyPen i405X: Applying InputClass "evdev tablet catchall"

```
which I understood as the "very bad line", but after that you will see that things get quite different.

---

### Post by random_jc on 2011-08-29
To be sure, I tried again with the version you proposed in message #232. So I confirm that in this case, the extra lines appearing with the version of message #235 do not appear (in coherence with the fact that the behavior of the tablet is not changed). Sorry about my lack of precision.

---

### Post by Favux on 2011-08-29
No the line itself isn't bad it is just that it was the last line or driver matched and that was the evdev driver.  The last thing matched controls.

The MatchProduct WizardPen .conf file did what we wanted.  It matched to the WizardPen X driver:
```
(II) config/udev: Adding input device Genius EasyPen i405X (/dev/input/event6)
(**) Genius EasyPen i405X: Applying InputClass "evdev pointer catchall"
(**) Genius EasyPen i405X: Applying InputClass "evdev keyboard catchall"
(**) Genius EasyPen i405X: Applying InputClass "evdev tablet catchall"
(**) Genius EasyPen i405X: Applying InputClass "WizardPen class"
(II) LoadModule: "wizardpen"
```
Which is why your stylus buttons now work correctly.  So now you have:
```
(II) config/udev: Adding input device Genius EasyPen i405X (/dev/input/event6)
(**) Genius EasyPen i405X: Applying InputClass "evdev pointer catchall"
(**) Genius EasyPen i405X: Applying InputClass "evdev keyboard catchall"
(**) Genius EasyPen i405X: Applying InputClass "evdev tablet catchall"
(**) Genius EasyPen i405X: Applying InputClass "WizardPen class"
(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules/input/wizardpen_drv.so
(II) Module wizardpen: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.7.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/input/event6"
(--) Genius EasyPen i405X: MaxX:14080 MaxY:10240 MaxZ:1023
(--) Genius EasyPen i405X: aspect ratio:1.38:1
(**) Genius EasyPen i405X is in absolute mode
(**) Genius EasyPen i405X: TopX not set, defaulting to "5%"
(**) Genius EasyPen i405X: TopY not set, defaulting to "5%"
(**) Genius EasyPen i405X: BottomX not set, defaulting to "95%"
(**) Genius EasyPen i405X: BottomY not set, defaulting to "95%"
(II) Genius EasyPen i405X: ScreenX = 1440, ScreenY = 900
(**) Genius EasyPen i405X: TopX                   = 704
(**) Genius EasyPen i405X: TopY                   = 512
(**) Genius EasyPen i405X: BottomX                = 13376
(**) Genius EasyPen i405X: BottomY                = 9728
(**) Genius EasyPen i405X: TopZ    (min pressure) = 0
(**) Genius EasyPen i405X: BottomZ (max pressure) = 1023
(**) Genius EasyPen i405X: always reports core events
(II) XINPUT: Adding extended input device "Genius EasyPen i405X" (type: WizardPen Tablet)
(II) Genius EasyPen i405X Increment: 9
(II) config/udev: Adding input device Genius EasyPen i405X (/dev/input/mouse1)
(**) Genius EasyPen i405X: Ignoring device from InputClass "WizardPen ignore mouse dev class"
```
Which all looks good.  Aside from it complaining about the coordinates a little.

So do you still have a problem?

---

### Post by random_jc on 2011-08-29
Yes, the problem is that pressure on the tablet has no effect, which makes any action fairly complicated.

---

### Post by Favux on 2011-08-29
Since you are now on the right driver we have to wonder about a hardware problem i.e. the stylus tip.  Are you able to test the tablet on another OS, say Windows.  Do you have pressure in that?  Also does the spec.s on your tablet say it has 1024 pressure levels?

---

### Post by random_jc on 2011-08-29
Yes, the number of pressure levels is correct. Just to be sure, the thing is that nothing happens at all when I press the tablet, not only that it is not pressure-sensitive. 

At present I don't have another OS to test the tablet, but pressure did have an effect when with the wrong driver, so it's probably not a hardware problem (although I am quite puzzled now that we seem to have ruled out both driver problems and hardware problems...)

---

### Post by Favux on 2011-08-29
Let's make sure we're using the same terms.

The stylus tip by default should emit the equivalent of a left mouse click.

Pressure is variation of line width in applications like Gimp, Inkscape, and MyPaint when drawing a line or whatever.  With some applications such as Gimp you need to enable the extended input device.

The stylus has a battery and its fresh?  Are there replaceable nibs for the tip?  If so have you tried a new nib?

---

### Post by random_jc on 2011-08-29
Sorry if my expressions are not accurate (as you may have guessed, english is not my mother tongue). So my problem is that there is no "left mouse click" effect whatsoever. I doubt it comes from a hardware problem, since if I come back to an older version of 70-wizardpen.conf, then the stylus tip has an effect, although not a left mouse click in this case. The tablet is brand new, I took the battery from inside the box, so I suspect it is ok. To be sure, I just turned back to the old version of 70-wizardpen.conf, and I confirm the stylus tip is doing something in this case.

---

### Post by Favux on 2011-08-29
Alright, we have a bit of a mystery.  It would be nice if you could test it on a Windows PC.

The only thing I don't recognize in the Xorg.0.log is:
> (II) Genius EasyPen i405X Increment: 9
That's a new one on me.

Let's see if telling the WizardPen driver what the coordinates are changes anything:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchProduct "i405X"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
    Option "TopX"    "704"
    Option "TopY"    "512"
    Option "BottomX" "13376"
    Option "BottomY" "9728"
    Option "TopZ"    "0"
    Option "BottomZ" "1023"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchProduct "i405X"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```

---

### Post by random_jc on 2011-08-29
Hmm, it did not solve the problem. The mysterious line you refer to is still there. Here is now how a part of Xorg.0.log looks like:

```

(II) config/udev: Adding input device Genius EasyPen i405X (/dev/input/event6)
(**) Genius EasyPen i405X: Applying InputClass "evdev pointer catchall"
(**) Genius EasyPen i405X: Applying InputClass "evdev keyboard catchall"
(**) Genius EasyPen i405X: Applying InputClass "evdev tablet catchall"
(**) Genius EasyPen i405X: Applying InputClass "WizardPen class"
(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules/input/wizardpen_drv.so
(II) Module wizardpen: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.7.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/input/event6"
(--) Genius EasyPen i405X: MaxX:14080 MaxY:10240 MaxZ:1023
(--) Genius EasyPen i405X: aspect ratio:1.38:1
(**) Genius EasyPen i405X is in absolute mode
(II) Genius EasyPen i405X: ScreenX = 1440, ScreenY = 900
(**) Genius EasyPen i405X: TopX                   = 704
(**) Genius EasyPen i405X: TopY                   = 512
(**) Genius EasyPen i405X: BottomX                = 13376
(**) Genius EasyPen i405X: BottomY                = 9728
(**) Genius EasyPen i405X: TopZ    (min pressure) = 0
(**) Genius EasyPen i405X: BottomZ (max pressure) = 1023
(**) Genius EasyPen i405X: always reports core events
(II) XINPUT: Adding extended input device "Genius EasyPen i405X" (type: WizardPen Tablet)
(II) Genius EasyPen i405X Increment: 9
(II) config/udev: Adding input device Genius EasyPen i405X (/dev/input/mouse1)
(**) Genius EasyPen i405X: Ignoring device from InputClass "WizardPen ignore mouse dev class"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)

```To be really really sure, I will try once more to go back to an old version of 70-wizardpen.conf and check again if it's not a hardware problem. But it's really because I don't know what else to do...

---

### Post by Favux on 2011-08-29
Lets try a couple of different values for TopZ.  That's the opposite of what we should be doing because that will raise the pressure threshold not make it more sensitive.  But what the heck, maybe there's some sort of overload.  Say maybe 10, or 40, or 80?
```
    Option "TopZ"    "10"

```

---

### Post by random_jc on 2011-08-29
I tried with 10, 40, and 200, but I could not obtain any effect. From my mutliple trials, I realized that i did not need to shut down and restart the computer each time, but that closing the session was sufficient. Is it ok ?

---

### Post by random_jc on 2011-08-29
Just to mention my stupid attempts, i tried the command

```

xinput set-button-map "Genius EasyPen i405X" 1 1 1 

```

which indeed turned all buttons to a left mouse click, but left the stylus tip without effect. I tried to add a great wealth of extra 1's, but it did not change anything.

---

### Post by Favux on 2011-08-29
Restarting X should be OK.  I doubted changing the button map would work since what you said seemed to indicate that the stylus tip was mapped to Button 1 by default, which is what it should be.

How new is this tablet?  Did it just come out?

I'm wondering if it isn't supported by the X driver yet or maybe the kernel driver.

---

### Post by random_jc on 2011-08-29
I just bought it. The model is described _[there]("http://www.geniusnet.com/wSite/ct?xItem=48471&ctNode=174&mp=1")_. I don't think it is so new though, since before buying it I had googled it to check that one could make it work with ubuntu, and I had found comments saying that.

---

### Post by Favux on 2011-08-29
OK, that says 2010.  Don't know if that was after Lucid (10.04) but odds are good.  But since you installed the PPA the X driver should be good.  That only leaves the kernel driver.

Did you try one of your spare Pen tips yet?

---

### Post by random_jc on 2011-08-29
No I didn't, but I tried several times to go back to the initial version of wizardpen.conf, and each time I do it the tip works again, although not in the way I want. Considering this, do you really think I should try to change the tip ?

(btw, I may go to bed soon, so don't be surprised in case I stop to answer for some time.)

---

### Post by Favux on 2011-08-29
Well the fact that evdev gives some sort of tip response indicates that it may be something to do with the X drivers.  But yes, try changing the tip.  After all you want the .conf that matches to the WizardPen driver after all.  But from what you said the evdev X driver isn't giving you a left click either, is it?

---

### Post by random_jc on 2011-08-29
No, the evdev driver makes the tip act in a way that I don't know how to describe properly, since it does not match any usual mouse button. Under firefox, it does the "go back" button. I can browse through menus like the "System" menu of the traditional Ubuntu bar, and "click" on items. But I cannot click on an icon on the Desktop for instance, nor can I close a window using the little red cross. There is no effect on the drawing zone of Gimp.

---

### Post by Favux on 2011-08-29
It sounds like evdev is translating the stylus tip as BTN_BACK.  That doesn't make sense.  But I guess it does fit into the stylus tip not working with the WizardPen driver since it probably can't handle a BTN_BACK.  Where the heck is that coming from, the kernel?  I do not understand.

The only thing I can think of is to install a newer release of Ubuntu, say Maverick (10.10)?  And see if that straightens it out.

---

### Post by random_jc on 2011-08-30
So I tried the tablet on a desktop computer, which unfortunately runs also with Ubuntu 10.04. Exactly the same behavior was observed: with the initial installation, the tip is interpreted as "BTN_BACK". After changing the 70-wizardpen.conf according to message #247, I got the same situation as with my laptop, that is, the tip does not have any effect, while the other buttons become middle and right mouse clicks. 

Going into the /var/log/Xorg.0.log, I observed the same as in message #248, except that the "increment" that was 9 becomes a 10. To be really precise, values of Screen# and numbering of "mouse" are also different, here it is in full :

```

(II) config/udev: Adding input device Genius EasyPen i405X (/dev/input/event6)
(**) Genius EasyPen i405X: Applying InputClass "evdev pointer catchall"
(**) Genius EasyPen i405X: Applying InputClass "evdev keyboard catchall"
(**) Genius EasyPen i405X: Applying InputClass "evdev tablet catchall"
(**) Genius EasyPen i405X: Applying InputClass "WizardPen class"
(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules/input/wizardpen_drv.so
(II) Module wizardpen: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.7.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/input/event6"
(--) Genius EasyPen i405X: MaxX:14080 MaxY:10240 MaxZ:1023
(--) Genius EasyPen i405X: aspect ratio:1.38:1
(**) Genius EasyPen i405X is in absolute mode
(II) Genius EasyPen i405X: ScreenX = 1280, ScreenY = 1024
(**) Genius EasyPen i405X: TopX                   = 704
(**) Genius EasyPen i405X: TopY                   = 512
(**) Genius EasyPen i405X: BottomX                = 13376
(**) Genius EasyPen i405X: BottomY                = 9728
(**) Genius EasyPen i405X: TopZ    (min pressure) = 0
(**) Genius EasyPen i405X: BottomZ (max pressure) = 1023
(**) Genius EasyPen i405X: always reports core events
(II) XINPUT: Adding extended input device "Genius EasyPen i405X" (type: WizardPen Tablet)
(II) Genius EasyPen i405X Increment: 10
(II) config/udev: Adding input device Genius EasyPen i405X (/dev/input/mouse2)
(**) Genius EasyPen i405X: Ignoring device from InputClass "WizardPen ignore mouse dev class"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)

```I will try to have access to other versions of Ubuntu or to other OS, but this may take some time.

---

### Post by random_jc on 2011-08-31
Hi,

I found another laptop which I upgraded to Ubuntu 10.10, and gave it a try. So I installed the driver, and the same behavior as usual was what I got. That is, the tablet is driven by evdev, and the tip makes a "BTN_BACK". But this time no file 70-wizardpen.conf appeared in /usr/lib/X11/xorg.conf.d. I created one anyways, but it had no effect. 

The laptop I'm now using had some problems with its trackpoint at some time, and it may be that I messed up the configuration a long time ago because of that.

---

### Post by random_jc on 2011-09-01
I finally understood why my 70-wizardpen.conf had no effect. With Ubuntu 10.10, it should be located in /usr/share/X11/xorg.conf.d, and no longer in /usr/lib/X11/xorg.conf.d...

Ok, so in the right folder now, there was indeed a 70-wizardpen.conf which looked like this :

```

Section "InputClass"
   Identifier      "wizardpen"
   MatchIsTablet   "on"
   MatchDevicePath "/dev/input/event*"
   MatchTag        "wizardpen"
   Driver          "wizardpen"
EndSection

Section "InputClass"
   Identifier      "wizardpen ignore mouse dev"
   MatchDevicePath "/dev/input/mouse*"
   MatchTag        "wizardpen"
   Driver          "mouse"
   Option          "MouseSpeed" "16"
   Option          "ignore"     "true"
EndSection

```

I tried to add one of these lines
```

MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
MatchVendor "UC-LOGIC|KYE Systems|i405X|Ace Cad"
MatchProduct "i405X"

```
but the tablet remained with its evdev driver. So in the end I re-used the exact same 70-wizardpen.conf as in message #235, to get the same result as with Ubuntu 10.04. That is, the tablet is now matched with the right driver, the /var/log/Xorg.0.log looks just the same, and the tip has no effect.

Does someone have any suggestion ?

---

### Post by Muy-burro on 2011-09-01
Hi, I'm new in the forum.

I not a real user of ubuntu, I using **gnu/linux canaima 3** who is a distro based on debian 6 in Venezuela. I have download the lastest version driver from [http://launchpad.net/wizardpen/trunk/0.8/+download/xorg-input-wizardpen-0.8.1.tar.bz2]("http://launchpad.net/wizardpen/trunk/0.8/+download/xorg-input-wizardpen-0.8.1.tar.bz2"). In the terminal executed this as root:
```
./configure
make
make install
```

And that worked with a genius mousepen 8x6... But 3 days later I brought a Kanvus Life H85 (ID 5543:0782 UC-Logic Technology Corp) and connected it to the computer... Inmediatly the driver worked but the cursor do not move from the screen left top. I need this tablet because the mousepen have died in a accident with my little brother (he is ok, but the tablet..... ).

Trying with ```
xinput --list --long
``` it return this:
```
&#9116;   &#8627; H850S                                     id=9    [slave  pointer  (2)]
        Reporting 6 classes:
                Class originated from: 9
                Buttons supported: 14
                Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down Button Horiz Wheel Left Button Horiz Wheel Right Button Side Button Extra Button Forward Button Unknown Button Unknown Button Unknown Button Unknown
                Button state:
                Class originated from: 9
                Detail for Valuator 0:
                  Label: Abs X
                  Range: 0.000000 - 32000.000000
                  Resolution: 10000 units/m
                  Mode: absolute
                  Current value: 640.000000
                Class originated from: 9
                Detail for Valuator 1:
                  Label: Abs Y
                  Range: 0.000000 - 20000.000000
                  Resolution: 10000 units/m
                  Mode: absolute
                  Current value: 400.000000
                Class originated from: 9
                Detail for Valuator 2:
                  Label: Abs Z
                  Range: 0.000000 - 32000.000000
                  Resolution: 10000 units/m
                  Mode: absolute
                  Current value: 0.000000
                Class originated from: 9
                Detail for Valuator 3:
                  Label: Abs Rotary X
                  Range: 0.000000 - 20000.000000
                  Resolution: 10000 units/m
                  Mode: absolute
                  Current value: 0.000000
                Class originated from: 9
                Detail for Valuator 4:
                  Label: Abs Pressure
                  Range: 0.000000 - 1023.000000
                  Resolution: 10000 units/m
                  Mode: absolute
                  Current value: 0.000000
```
and with ```
xinput --test 9
``` show every movement whit the pencil and pressure in the button 8(pencil tip), 9 and 10 but the cursor still does not move from the screen left top.

```
nano /usr/share/X11/xorg.conf.d/70-wizardpen.conf
```
show
```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchTag "wizardpen"
   Driver "wizardpen"
   Option               "TopX"          "1506"
   Option               "TopY"          "2705"
   Option               "BottomX"       "31225"
   Option               "BottomY"       "30892"
EndSection

```

The ```
ls /usr/lib/xorg/modules/input/wizardpen_drv.*
``` show: ```
/usr/lib/xorg/modules/input/wizardpen_drv.la  /usr/lib/xorg/modules/input/wizardpen_drv.so
```

cat /proc/bus/input/devices show:
```
I: Bus=0003 Vendor=5543 Product=0782 Version=0110
N: Name="H850S"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input17
U: Uniq=
H: Handlers=mouse0 event4 
B: PROP=0
B: EV=1f
B: KEY=c03 0 3f0001 0 0 0 0 0 0 0 0
B: REL=303
B: ABS=100000f
B: MSC=10

I: Bus=0003 Vendor=5543 Product=0782 Version=0110
N: Name="H850S"
P: Phys=usb-0000:00:1d.1-1/input1
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input18
U: Uniq=
H: Handlers=kbd mouse4 event13 
B: PROP=0
B: EV=17
B: KEY=70000 0 0 0 10000000 20000 0 0 0
B: REL=303
B: MSC=10

```

And thats everything I know about this tablet... if anyone can help me with this?...

And.. yes, I have a bad orthography... is my second time writing in english. =P

---

### Post by Favux on 2011-09-01
Hi Muy-burro,

Welcome to Ubuntu forums!

You are in luck.  We set one up in June.  See post #35:  [http://ubuntuforums.org/showthread.php?t=1788415](http://ubuntuforums.org/showthread.php?t=1788415)  Hopefully all you will need to do is change the 70-wizardpen.conf as shown.

---

### Post by Muy-burro on 2011-09-03
> **Favux said:**
> Hi Muy-burro,

Welcome to Ubuntu forums!

You are in luck.  We set one up in June.  See post #35:  [http://ubuntuforums.org/showthread.php?t=1788415](http://ubuntuforums.org/showthread.php?t=1788415)  Hopefully all you will need to do is change the 70-wizardpen.conf as shown.

Thanks, I will try it... but I have to say that I'm using the 0.8.1 version of the driver and it have a some deferences compared with  0.7.4 version. (how I uninstall this?... make unistall?).

---

### Post by Favux on 2011-09-03
I don't think the differences will hurt anything.  You're just changing the wizardpen.conf file.  So I'd keep the newer driver rather than install an older one over it.

---

### Post by Muy-burro on 2011-09-03
It worked perfect... thank you!

---

### Post by random_jc on 2011-09-04
Hi,

I finally managed to find a computer working with windows 7, and on it the tablet works just fine.

I'm getting a bit desperate about finding a way to make this tablet work on Ubuntu, I don't know what to try... Any suggestion someone ?

---

### Post by t3h m00kz on 2011-09-06
Hey guys,

New to the forums and to Ubuntu/Linux in general (about two days so far!). Been trying to get my TWA60 working to no avail. I've been following the instructions in the OP, however I'm getting stuck on step 9:

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC TWA60">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
                <merge key="input.x11_options.MaxX" type="string">29405</merge>
                <merge key="input.x11_options.MaxY" type="string">29671</merge>
                </match>
		<merge key="info.product" type="string">stylus</merge>
		<merge key="input.x11_options.SendCoreEvents" type="string">true
	    </merge>
            </device>
            </deviceinfo>
```

Every time I run this and type :wq into the terminal, it outputs the error:

```

"/etc/hal/fdi/policy/99-x11-wizardpen.fdi" E212: Can't open file for writing

```

When I browse through my folders, I don't see /etc/hal, I can't create folders in /etc, and when I open it in gedit, it won't allow me to save, giving me the error:

"Could not find the file /etc/hal/fdi/policy/99-x11-wizardpen.fdi. Please check that you typed the location correctly and try again."

Sorry for the nubbish question. Hopefully it isn't too hard to resolve.

---

### Post by random_jc on 2011-09-13
Hi t3h m00kz,

Well, I'm not so knowledgeable about the topic, since I don't manage to have my tablet working, but as far as I understand, you should not go for the /etc/hal/fdi/policy/99-x11-wizardpen.fdi file if you have Ubuntu version 10.04 or higher. See 

[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

Yet, you should be free to create any folder or file you want, but sometimes you need special rights. For this, you may type "sudo gedit ..." in a terminal, and file in your password.

Sincerly,
Jc

---

### Post by xl0 on 2011-11-21
Hi.

This is probably not specific to wizardpen, but is it possible to to map the tablet to a part of the screen?
I've got a 2-monitor setup, and want the tablet to correspond to a single display, or even better, a part of the display.

Otherwise, my M610 works just perfectly, thanks for the great job!

---

### Post by Favux on 2011-11-21
Hi xl0,

Welcome to Ubuntu forums!

Yes it is possible.  A non-Wacom tablet can use xinput's CTM method.  See:  [http://ubuntuforums.org/showthread.php?t=1656089](http://ubuntuforums.org/showthread.php?t=1656089)

---

### Post by drpjkurian on 2011-11-27
Hi Favux
I have installed the wizardpen driver from Doctor MO PPA for my UBUNTU LUCID. The tablet mouse as well as the stylus gets stuck to the left top corner. What am i supposed to do. It seems I am back to square one... 
My /usr/lib/X11/xorg.conf.d/70-wizardpen.conf is as follows

```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/by-id/usb-UC-LOGIC_Tablet_WP5540U-event-mouse"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad|WALTOP|Waltop"
   Driver "wizardpen"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/by-id/usb-UC-LOGIC_Tablet_WP5540U-event-mouse"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad|WALTOP|Waltop"
   Driver ""
EndSection
```

My grep -i name /proc/bus/input/devices is
```
N: Name="Power Button"
N: Name="Power Button"
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="USB Optical Mouse"
N: Name="UC-LOGIC Tablet WP5540U"

```

My Xinput is
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                       	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=11	[slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP5540U                 	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]

```

With regards
Dr Kurian

---

### Post by drpjkurian on 2011-11-27
Bump

---

### Post by Favux on 2011-11-27
Hi drpjkurian,

Everything looks OK so far.  Both the .conf and *xinput list*.  Although we might have room to play with the .conf match lines.

Alright, so stuck in upper left corner (0,0) implies that X input isn't receiving any coordinate values.  Since the WizardPen X driver in DoctorMO's PPA has been working let's assume it is something else for now.

Do you know when this happened?  It seems to me there was a kernel update for Lucid in the last week.  Also an Intel video update among other stuff I think.

So if you can, try booting into the previous kernel and see if that fixes things.

Let's try a quick check to see if we can determine what X driver has the tablet.  Run in a terminal:
```
xinput list-props "UC-LOGIC Tablet WP5540U"
```
and post the output.  If it is evdev that's the problem.

Then let's look at your Xorg.0.log in /var/log and see if that tells us anything.  If list-props doesn't show us the driver Xorg.0.log will.  You might want to compress and attach it.

Is it possible the stylus battery died?

---

### Post by drpjkurian on 2011-11-28
Hi Favux
I did a fresh installation in my wife's machine. I messed up the X11 file. now my machine boots to a black screen. I've decided to reinstall Ubuntu Lucid. Will bother you if wizardpen fails again. 
Thank you very much for your prompt reply.

With regards
Dr Kurian

---

### Post by drpjkurian on 2011-11-28
Hi Favux.

I reinstalled Lucid. I am having the same old problem.My new /usr/lib/X11/xorg.conf.d/70-wizardpen.conf is as follows
```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver "wizardpen"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/mouse*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSection
```


My grep -i name /proc/bus/input/devices is

```
rose@rose-desktop:~$ grep -i name /proc/bus/input/devices is
/proc/bus/input/devices:N: Name="Power Button"
/proc/bus/input/devices:N: Name="Power Button"
/proc/bus/input/devices:N: Name="Macintosh mouse button emulation"
/proc/bus/input/devices:N: Name="AT Translated Set 2 keyboard"
/proc/bus/input/devices:N: Name="USB Optical Mouse"
/proc/bus/input/devices:N: Name="UC-LOGIC Tablet WP5540U"

```

My xinput list
```
rose@rose-desktop:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                       	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=10	[slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP5540U                 	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
```


And xinput list-props "UC-LOGIC Tablet WP5540U" gives

```
rose@rose-desktop:~$ xinput list-props "UC-LOGIC Tablet WP5540U"
Device 'UC-LOGIC Tablet WP5540U':
	Device Enabled (121):	1
	Device Accel Profile (238):	0
	Device Accel Constant Deceleration (239):	1.000000
	Device Accel Adaptive Deceleration (241):	1.000000
	Device Accel Velocity Scaling (242):	10.000000
	Evdev Reopen Attempts (236):	10
	Evdev Axis Inversion (243):	0, 0
	Evdev Axis Calibration (244):	<no items>
	Evdev Axes Swap (245):	0
	Axis Labels (246):	"Abs X" (484), "Abs Y" (485), "Abs Z" (486), "Abs Rotary X" (487), "Abs Pressure" (488)
	Button Labels (247):	"Button Left" (122), "Button Middle" (123), "Button Right" (124), "Button Wheel Up" (125), "Button Wheel Down" (126), "Button Horiz Wheel Left" (127), "Button Horiz Wheel Right" (128), "Button Side" (481), "Button Extra" (482), "Button Forward" (483), "Button Unknown" (237), "Button Unknown" (237), "Button Unknown" (237), "Button Unknown" (237)
	Evdev Middle Button Emulation (248):	2
	Evdev Middle Button Timeout (249):	50
	Evdev Wheel Emulation (250):	0
	Evdev Wheel Emulation Axes (251):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (252):	10
	Evdev Wheel Emulation Timeout (253):	200
	Evdev Wheel Emulation Button (254):	4
	Evdev Drag Lock Buttons (255):	0

```

---

### Post by Favux on 2011-11-28
Alright.  Assuming you've installed the PPA and that went OK then it appears to be a match problem since it is on the evdev X driver.  You should actually be able to get it working on that in Oneiric I think, but maybe not with the evdev version in Lucid.

So let's try something quick.  Try changing the wizardpen.conf to:
```

Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
#   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   MatchProduct "WP5540U"
   MatchDevicePath "/dev/input/event*"
   Driver "wizardpen"
EndSection

Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
#   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   MatchProduct "WP5540U"
   MatchDevicePath "/dev/input/mouse*"
   Driver ""
EndSection
```
Reboot and repeat the list-props.

---

### Post by drpjkurian on 2011-11-28
Dear Favux

You are great.My pen mouse works fine. But my tablet mouse is stuck.the buttons on the tablet mouse works fine.

My 
```
rose@rose-desktop:~$ xinput list-props "UC-LOGIC Tablet WP5540U"
Device 'UC-LOGIC Tablet WP5540U':
	Device Enabled (121):	1
	Device Accel Profile (238):	0
	Device Accel Constant Deceleration (239):	1.000000
	Device Accel Adaptive Deceleration (241):	1.000000
	Device Accel Velocity Scaling (242):	10.000000

```

Thanks a ton for your help. You are an asset to the community.

With regards Dr Kurian

---

### Post by Favux on 2011-11-28
Good, so the stylus is working correctly again?

You have a tablet mouse also?  As far as I know that isn't supported by the WizardPen driver, and least we haven't gotten it working before that I remember.  But yours was working?

Right now the tablet mouse snippet is set up to keep the mouse off any driver.  That's what DoctorMO has used.  We could try placing it on the evdev driver.  But that would probably break X unless the mouse is exported from the kernel as a separate device from the stylus.  If you know how to fix the wizardpen.conf from the Recovery Mode command line we could give it a shot.  I'm thinking if it was working it must have been evdev that picked it up.

---

### Post by drpjkurian on 2011-11-29
Hi Favux

The tablet mouse was not working earlier. I think it is better to be satisfied without tablet mouse. Thanking you once again for solving my stylus problem

With regards
Dr Kurian

---

### Post by Wasabi2007 on 2012-01-19
hi i have a little Problem with a Tablet.
it is the same Problem as here

[http://comments.gmane.org/gmane.linux.drivers.wacom/6127](http://comments.gmane.org/gmane.linux.drivers.wacom/6127)
and it seems to be solved.

But i don't know how to do this:

"
You may also be able to redirect this tablet to use xf86-input-evdev instead.  You'll lose ability to treat eraser as a different input device but it may at least work. 
"

---

### Post by Favux on 2012-01-19
Hi Wasabi2007,

Welcome to Ubuntu forums!

Some more information would be helpful.  What release of Ubuntu are you using?  Also the output of some commands run in a terminal would be good.  For example:
```
lsusb
```
will have a line in the output with the tablet in it and that will give us the manufacturer and model ID.  And:
```
xinput list
```
will tell us the "device name" the tablet is using.

---

### Post by Wasabi2007 on 2012-01-19
Sorry for my harsh and short post. And Thank you for your welcome.

At first I can not post the needed information at the moment, because it was a Laptop from a friend of mine and he needed it back.

I wanted to make him [this]("http://www.davidrevoy.com/index.php?article110/kubuntu-11-10-for-digital-painting") set-up but his tablet was not detected. So tried the Wizardpen Drivers and see there the tablet is detected. 
But the tablet didn't send any feedback. So i searched for that problem and found [this]("http://comments.gmane.org/gmane.linux.drivers.wacom/6127") mailing list conversation.
It is the same Tablet device and the same error and it seemed to be solved by replacing the the "xf86-input-wacom" driver through "xf86-input-evdev". 

Unfortunately i have not enough linux/(k)ubuntu in deep knowledge to know were i have to replace the driver.

---

### Post by Favux on 2012-01-19
Not a problem at all.

I followed your link, but I ***really*** want to verify the Vendor ID = 172f = Waltop and the Product ID = 0502 from the *lsusb*.
```
Bus 002 Device 012: ID 172f:0502 Waltop International Corp. Sirius Battery Free Tablet
```
See from Nick's site:  [http://digimend.sourceforge.net/](http://digimend.sourceforge.net/)  that Waltop model isn't included yet in the kernel:  [http://digimend.git.sourceforge.net/git/gitweb.cgi?p=digimend/kernel-patches.git;a=blob_plain;f=COMPATIBILITY](http://digimend.git.sourceforge.net/git/gitweb.cgi?p=digimend/kernel-patches.git;a=blob_plain;f=COMPATIBILITY)  And that is what they are saying on that thread you link too.

Nick offers to add it to the kernel if the usbhid-dump information his site requests is sent to him and his kernel patch/driver is tested.

You see the Waltop tablets are suppose to use the Wacom driver now, and tablets that don't use the Wacom X driver are suppose to use evdev.  And that is suppose to happen automatically if the tablet is in the kernel.  What you are asking about is the xorg.conf.d .conf (configuration) files.  For the distribution the files would be in /usr/share/X11/xorg.conf.d.  Custom .conf files by the user are suppose to go in /etc/X11/xorg.conf.d.  Here's some more information on xorg.conf.d .conf files:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d)

But you should not have to make a custom file, it should happen automatically.  It looks like the problem is that model of Waltop tablet is not yet in the kernel.  In which case I don't think pressure, despite what is reported on that thread, would be working.  Unless some generic hid kernel driver I don't know about processes unclaimed Waltop tablets.  They are just transitioning to this system having just dropped the WizardPen driver for the evdev driver.  And unfortunately a number of tablets are not in the kernel yet.  They mainly seem to be KYE Systems tablets though.

---

### Post by Wasabi2007 on 2012-01-19
I think at Saturday or Sunday, I can deliver the device information.

I hope we get that tablet to fly ^^

And I hope there is some day in the Linux Future where are no driver Issues with new devices.

---

### Post by Wasabi2007 on 2012-01-21
Finalay I have the Laptop again ^^

so here is the lsusb output:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0408:2fb1 Quanta Computer, Inc. 
Bus 002 Device 003: ID 413c:8184 Dell Computer Corp. F3607gw v2 Mobile Broadband Module
Bus 002 Device 004: ID 172f:0502 Waltop International Corp. Sirius Battery Free Tablet

```

edit:
sorry i forgot the xinput list result:
```
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=13   [slave  pointer  (2)]
&#9116;   &#8627;          WALTOP     Batteryless Tablet  stylus    id=15   [slave  pointer  (2)]
&#9116;   &#8627;          WALTOP     Batteryless Tablet  eraser    id=16   [slave  pointer  (2)]
&#9116;   &#8627;          WALTOP     Batteryless Tablet  pad       id=17   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=8    [slave  keyboard (3)]
    &#8627; Power Button                              id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=10   [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_2HDM             id=11   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=12   [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                          id=14   [slave  keyboard (3)]

```

---

### Post by Wasabi2007 on 2012-01-21
sorry i clicked on quote rather than on edit

---

### Post by Favux on 2012-01-21
Good.  Now what does the tablet do?  Does the stylus get recognized?  In other words does the pointer arrow track the stylus tip?

Although the 502 model is not in Nick's compatibility tablet (i.e. not yet in the kernel) the Wacom X driver xf86-input-wacom is picking the tablet up.  That's why you see stylus, eraser, and pad appended to the device name in *xinput list*.

You can verify that by posting the ouput in a terminal of:
```
xinput list-props 15
```
And you should also see the tablet setting up on the Wacom driver in Xorg.0.log in /var/log.

---

### Post by Wasabi2007 on 2012-01-21
Ok xinput list-props 15 delivers me that:
```
Device '         WALTOP     Batteryless Tablet  stylus':
        Device Enabled (132):   1
        Coordinate Transformation Matrix (134): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (252):     0
        Device Accel Constant Deceleration (253):       1.000000
        Device Accel Adaptive Deceleration (254):       1.000000
        Device Accel Velocity Scaling (255):    10.000000
        Wacom Tablet Area (509):        0, 0, 20000, 12000
        Wacom Rotation (510):   0
        Wacom Pressurecurve (511):      0, 0, 100, 100
        Wacom Serial IDs (512): 1282, 0, 2, 0
        Wacom Capacity (513):   -1
        Wacom Pressure Threshold (514): 27
        Wacom Sample and Suppress (515):        2, 4
        Wacom Enable Touch (516):       0
        Wacom Hover Click (517):        0
        Wacom Enable Touch Gesture (518):       0
        Wacom Touch Gesture Parameters (519):   50, 20, 250
        Wacom Tool Type (520):  "STYLUS" (412)
        Wacom Button Actions (521):     "Wacom button action 1" (529), "Wacom button action 2" (528), "Wacom button action 3" (527), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
        Wacom Debug Levels (522):       0, 0
        Wacom button action 1 (529):    1572865
        Wacom button action 2 (528):    1572866
        Wacom button action 3 (527):    1572867


```

And the Tablet doesn't do anything visual Noticiable. The only thing that happens is that the tablet get automatically register. The stylus or the Tablet integrate Buttons doesn't seems to do anything.

---

### Post by Favux on 2012-01-21
From my understanding of how things are currently suppose to work and what you've showed it appears to me everything is working correctly.

The 50-wacom.conf is correctly picking up the WALTOP keyword and configuring your tablet on the Wacom X driver which it is suppose to.  As I said Waltops go to Wacom and the other tablets that used the former WizardPen driver are picked up by the 10-evdev.conf.  So it is all happening as it should.

The problem is of course your tablet's usb descriptor is not in the kernel.  So values like ABS_PRESSURE or ABS_Z or whatever it is the Wacom driver is looking for are null.  That's why there is no reaction to the stylus tip.  No tracking, left click, and pressure.

So to get it working you need to go to Nick's DIGImend sourceforge site and send in the information he requests on the link at the bottom of the site.  You can see an example of the information on this post by [viktoria.s]("http://ubuntuforums.org/showpost.php?p=11580830&postcount=22"), which she recently sent in for another tablet.  Nick will tell you if the information is good or if he needs anything else.  Then he'll make patches for the kernel and ask you to test them and if they are good he will submit them to the kernel so your tablet model is included for now on.  So you get to help with linux kernel development!  :)

Patching the kernel sounds a little daunting but it isn't actually that hard and Nick will walk you through it.  And I will try to help if you need me to.

And by the way the hotkeys on the tablet don't work.  No one has yet written code to get them working as far as I know.  Maybe Nick is thinking about doing that at some point?

---

### Post by Wasabi2007 on 2012-01-21
I would love to help to Improve the Linux Driver Support but i can only inspect the Laptop and it's behaviors till Tuesday.

And I get first wired result if i try to usbhid-dump the tablet:
```
sudo usbhid-dump 002 004
```
```

Failed to retrieve interface #0 report descriptor: Pipe error (ERROR_PIPE)

```

or do i need to write the output direct into a file?


btw:
It semes that the using from the xf86-input-evdev drivers work for Mypaint, and that would be the key point for my friend. I would like to use the xf86-input-evdev driver till there is an official support for that tablet. But i still have no idea were i have to set the used driver.

---

### Post by Favux on 2012-01-21
I haven't used usbhid-dump before.  Would it be?
```
sudo usbhid-dump --model=172f:0502
```
I get the impression that it is suppose to create a txt file and you don't need to pipe the output into one.

For a 52-waltop-on-evdev.conf you could try:
```
Section "InputClass"
    Identifier "waltop-on-evdev class"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/event*"
    Driver "evdev"
EndSection
```
Using
```
gksudo gedit /etc/X11/xorg.conf.d/52-waltop-on-evdev.conf
```

---

### Post by Wasabi2007 on 2012-01-21
nope your usbhid-dump command doesn't work ether.

and my ubuntu dosen't seems to have gksudo installed, but it is already late in my country so i try it tomorrow.

Thanks for your help. Big open source Community's are the best :D

---

### Post by Wasabi2007 on 2012-01-22
ok
after i force the tablet to use the evdev driver it seems to work al right
here are some commando output's

"lsusb":
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0408:2fb1 Quanta Computer, Inc. 
Bus 002 Device 005: ID 172f:0502 Waltop International Corp. Sirius Battery Free Tablet
Bus 002 Device 004: ID 413c:8184 Dell Computer Corp. F3607gw v2 Mobile Broadband Module

```"xinput list":
```

&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=14   [slave  pointer  (2)]
&#9116;   &#8627;          WALTOP     Batteryless Tablet    id=12   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=8    [slave  keyboard (3)]
    &#8627; Power Button                              id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=10   [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_2HDM             id=11   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=13   [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                          id=15   [slave  keyboard (3)]

```and "xinput list-props 12":
```

Device '         WALTOP     Batteryless Tablet ':
        Device Enabled (132):   1
        Coordinate Transformation Matrix (134): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (260):     0
        Device Accel Constant Deceleration (261):       1.000000
        Device Accel Adaptive Deceleration (262):       1.000000
        Device Accel Velocity Scaling (263):    10.000000
        Evdev Axis Inversion (264):     0, 0
        Evdev Axis Calibration (265):   <no items>
        Evdev Axes Swap (266):  0
        Axis Labels (267):      "Abs X" (256), "Abs Y" (257), "Abs Pressure" (258), "Abs Misc" (259), "Abs Misc" (259)
        Button Labels (268):    "Button Left" (135), "Button Middle" (136), "Button Right" (137), "Button Wheel Up" (138), "Button Wheel Down" (139), "Button Horiz Wheel Left" (140), "Button Horiz Wheel Right" (141), "Button Side" (254), "Button Extra" (255), "Button Unknown" (252), "Button Unknown" (252), "Button Unknown" (252), "Button Unknown" (252)
        Evdev Middle Button Emulation (269):    0
        Evdev Middle Button Timeout (270):      50
        Evdev Wheel Emulation (271):    0
        Evdev Wheel Emulation Axes (272):       0, 0, 4, 5
        Evdev Wheel Emulation Inertia (273):    10
        Evdev Wheel Emulation Timeout (274):    200
        Evdev Wheel Emulation Button (275):     4
        Evdev Drag Lock Buttons (276):  0

```he registers even the special buttons left and right from the device.
but the Button Mapping seems to be wrong.

is there a way that i could map a button to say "shift" with that in the .conf file:
```

**Option "ButtonMapping" "***string***"**
```if it's not gonna working, it is not that bad.

---

### Post by Favux on 2012-01-22
That is good news.  Is pressure working with evdev?  In the Xorg.0.log is it the "evdev tablet class" snippet that is picking up the tablet?

> he registers even the special buttons left and right from the device.
but the Button Mapping seems to be wrong.

Are you talking about the stylus side buttons?  Does the stylus have two side buttons, i.e. a rocker switch?  What is wrong with the mapping?
> Option "ButtonMapping" "string"
Yes, exactly as you can see from *man evdev* entered in a terminal.  So we just need to know what the current button map is.  Unfortunately *list-props* doesn't seem to tell us.  Say something like:
```
Section "InputClass"
    Identifier "waltop-on-evdev class"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/event*"
    Driver "evdev"
    Option "ButtonMapping" "1,3,2"
EndSection
```

You could also do it through xinput.  See *man xinput*.  Be careful about the "device name" though.  From previous experience the malformed one you are seeing in *xinput list* is what you have to use, i.e.:
```
"         WALTOP     Batteryless Tablet"
```
I'm pretty sure you have to include the erroneous white spaces.

---

### Post by Wasabi2007 on 2012-01-22
Yes the Pressure sensetivity works without problems.
Tested in Gimp and Mypaint.

To the buttons.
I doesn't mean the stylus buttons.
that is the tablet device:
[http://www.trust.com/products/product.aspx?ProductCategory=INPUT&ProductGroup=GRAPHIC-TABLETS&artnr=16938](http://www.trust.com/products/product.aspx?ProductCategory=INPUT&ProductGroup=GRAPHIC-TABLETS&artnr=16938)

and it has those configurable buttons left and right.
and those buttons i want to map to "shift", "ctrl", "alt" and "r"

is that waht you wanted out of the Xorg0.log?
```

[  2144.790] (II) config/udev: Adding input device          WALTOP     Batteryless Tablet  (/dev/input/event5)
[  2144.790] (**)          WALTOP     Batteryless Tablet : Applying InputClass "evdev pointer catchall"
[  2144.790] (**)          WALTOP     Batteryless Tablet : Applying InputClass "evdev keyboard catchall"
[  2144.790] (**)          WALTOP     Batteryless Tablet : Applying InputClass "evdev tablet catchall"
[  2144.790] (**)          WALTOP     Batteryless Tablet : Applying InputClass "Wacom class"
[  2144.790] (**)          WALTOP     Batteryless Tablet : Applying InputClass "waltop-on-evdev class"
[  2144.790] (II) Using input driver 'evdev' for '         WALTOP     Batteryless Tablet '
[  2144.790] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2144.790] (**)          WALTOP     Batteryless Tablet : always reports core events
[  2144.790] (**)          WALTOP     Batteryless Tablet : Device: "/dev/input/event5"
[  2144.790] (--)          WALTOP     Batteryless Tablet : Found 9 mouse buttons
[  2144.790] (--)          WALTOP     Batteryless Tablet : Found scroll wheel(s)
[  2144.790] (--)          WALTOP     Batteryless Tablet : Found relative axes
[  2144.790] (--)          WALTOP     Batteryless Tablet : Found x and y relative axes
[  2144.790] (--)          WALTOP     Batteryless Tablet : Found absolute axes
[  2144.790] (II) evdev-grail: failed to open grail, no gesture support
[  2144.790] (--)          WALTOP     Batteryless Tablet : Found x and y absolute axes
[  2144.790] (--)          WALTOP     Batteryless Tablet : Found absolute tablet.
[  2144.790] (--)          WALTOP     Batteryless Tablet : Found keys
[  2144.790] (II)          WALTOP     Batteryless Tablet : Configuring as tablet
[  2144.790] (II)          WALTOP     Batteryless Tablet : Configuring as keyboard
[  2144.790] (II)          WALTOP     Batteryless Tablet : Adding scrollwheel support
[  2144.790] (**)          WALTOP     Batteryless Tablet : YAxisMapping: buttons 4 and 5
[  2144.790] (**)          WALTOP     Batteryless Tablet : EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  2144.790] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input5/event5"
[  2144.790] (II) XINPUT: Adding extended input device "         WALTOP     Batteryless Tablet " (type: KEYBOARD)
[  2144.790] (**) Option "xkb_rules" "evdev"
[  2144.790] (**) Option "xkb_model" "pc105"
[  2144.790] (**) Option "xkb_layout" "de"
[  2144.790] (WW)          WALTOP     Batteryless Tablet : touchpads, tablets and touchscreens ignore relative axes.
[  2144.790] (II)          WALTOP     Batteryless Tablet : initialized for absolute axes.
[  2144.791] (**)          WALTOP     Batteryless Tablet : (accel) keeping acceleration scheme 1
[  2144.791] (**)          WALTOP     Batteryless Tablet : (accel) acceleration profile 0
[  2144.791] (**)          WALTOP     Batteryless Tablet : (accel) acceleration factor: 2.000
[  2144.791] (**)          WALTOP     Batteryless Tablet : (accel) acceleration threshold: 4
[  2144.791] (II) config/udev: Adding input device          WALTOP     Batteryless Tablet  (/dev/input/mouse0)

```

---

### Post by Favux on 2012-01-22
> Yes the Pressure sensetivity works without problems.
Tested in Gimp and Mypaint.

Wow, outstanding!  Now how the heck is that happening?  Clearly I am missing something.

With the new .conf file to put the Waltop on the evdev driver we're overriding the Wacom X driver match in the 50-wacom.conf.  So now the situation is getting complicated.  Some Waltops work on Wacom and others on evdev?  I am confused.


Alright, tablet buttons.  Thanks that link was helpful for me to see what you were talking about.  Wacom calls those ExpressKeys, but since that is trademarked by Wacom in linux we call them pad or tablet buttons.  The Wacom driver has a bunch of code to support those, both in the kernel driver and the X driver I believe.  Then the xsetwacom code in the Wacom X driver has code to handle setting the pad buttons to modifiers and/or keys.  As far as I'm aware the evdev driver has no code at all to support those, other than the keyboard stuff I suppose.

I have no idea how to set those up.  You could see if they are sending a signal (button/key press and release or whatever) by either trying *xev* or *evtest*.  With xev you enter xev in a terminal and then press a button and see if you get a key code.  With evtest you may need to run it in a console as root and you need to know the device node the tablet is on.

If you can get a keycode then you may be able to do a keybinding with the CompizConfigurationManager (CCSM) or say Xbindkeys.

---

### Post by Wasabi2007 on 2012-01-22
Except for the Eraser Button i get those events by xev.

and they seemed to be already mapped to the right keys.

```

KeyPress event, serial 34, synthetic NO, window 0x1e00001,
    root 0xb7, subw 0x0, time 1458993, (242,614), root:(245,637),
    state 0x0, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x1e00001,
    root 0xb7, subw 0x0, time 1459181, (242,614), root:(245,637),
    state 0x1, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x1e00001,
    root 0xb7, subw 0x0, time 1461381, (242,614), root:(245,637),
    state 0x0, keycode 23 (keysym 0xff09, Tab), same_screen YES,
    XLookupString gives 1 bytes: (09) " "
    XmbLookupString gives 1 bytes: (09) "       "
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x1e00001,
    root 0xb7, subw 0x0, time 1461525, (242,614), root:(245,637),
    state 0x0, keycode 23 (keysym 0xff09, Tab), same_screen YES,
    XLookupString gives 1 bytes: (09) " "
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x1e00001,
    root 0xb7, subw 0x0, time 1462385, (242,614), root:(245,637),
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x1e00001,
    root 0xb7, subw 0x0, time 1462521, (242,614), root:(245,637),
    state 0x8, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x1e00001,
    root 0xb7, subw 0x0, time 1464393, (242,614), root:(245,637),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x1e00001,
    root 0xb7, subw 0x0, time 1464537, (242,614), root:(245,637),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

---

### Post by Favux on 2012-01-22
Hmmm.  It sure is looking like your model Waltop tablet has support from a kernel driver somewhere.  You're using Oneiric, so the 3.0 kernel, correct?

Changing a key's mapping can be done a bunch of ways.  Changing the mapping in the kernel driver's code, udev, or X.  And along with that keybinding.  See appendix 2 of the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1") to get a feel for what is involved.

---

### Post by nmitsis on 2012-03-13
Dear Favux and Drkurian i tried to read almost all topics before telling you my problem because i see that you do everything you can to help us.
I have a trust/16937 tablet and i use ubuntu 10.04.I have a really bizare problem.When pc boots up i can move the pen without touching the tablet and cursor moves in screen.As soon as i touch pen in tablet or press the button the movement stops and i can move the cursor only if pen touches tablet.Iam really sorry for my bad english,Ty in advance.:p

---

### Post by Favux on 2012-03-13
Hi nmitsis,

I think I've seen that before.  I'll try to remember where, and what we did.

In the meantime let us do some diagnostics.  What is the output of the following commands in a terminal?
```
lsusb
```
```
xinput list
```

---

### Post by nmitsis on 2012-03-13
Favux iam speechless.The work you guys do is umbelivable.Today i managed to make it work without even knowing what i was doing,but you r the best.Your response to everyone and your knowledge is awesome.I wish some day i can give others what you give to us.Iam goin to post my 70- wizardpen.conf incase someone else has the same problem.

70- wizardpen.conf

Section "InputClass"
Identifier "wizardpen"
MatchIsPointer "on"
MatchDevicePath "/dev/input/event*"
MatchProduct "WALTOP|Tablet"
Driver "wizardpen"
EndSection

Section "InputClass"
Identifier "wizardpen ignore mouse dev"
MatchIsTablet "on"
MatchDevicePath "/dev/input/mouse*"
MatchVendor "WALTOP|Tablet"
Driver ""
EndSection


I think the problem was with MatchisPointer and MatchisTablet!!!Tke care

---

### Post by Favux on 2012-03-13
Thank you nmitsis for your kind words.  I'm glad you got your Trust 16937 tablet working in Lucid.  :)


**[SIZE="4"]FYI everyone:[/SIZE]**   **[SIZE="3"]The DIGI*mend* project's [mediawiki]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend") is live![/SIZE]**  It already has a lot of information on these tablets and how to get them working in linux using the new method, i.e. the evdev driver for Oneiric and later.  Please take a look.

---

### Post by Zeealex on 2012-06-23
Hey,
my trust TB5300 refuses to work at all on the ubuntu 11.10 supplied xorg graphic tabet driver it worked fine with my laptop when it was on 11.10 and on the same driver version.

i checked the xorg.conf file and the tablet section hasn't turned up.

what do i need to do to get it to work?

---

### Post by Favux on 2012-06-23
Hi Zealex,

I think your Trust TB-5300 is the "UC-Logic Tablet WP5540U".  You can run in a terminal:
```
xinput list
```
to confirm that.  Please post the output.  (Posting the output of **lsusb** would also be good.)

If so it should work out of the box.  There should be a kernel driver supporting it and it should run on the evdev X driver:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

The match to the evdev driver would be at /usr/share/X11/xorg.conf.d in the 10-evdev.conf:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_xf86-input-evdev](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_xf86-input-evdev)

After running **xinput list** use the <device name> you find for the tablet in the following terminal command:
```
xinput list-props "device name"
```
And that should tell us if it is on evdev.  Go ahead and post the output.

---

### Post by immanuelb on 2012-06-28
hi 
i have a uclogic wp4030u tablet. My cursor is moving and buttons are working but the pressure sensitivity is not working. please help me

I am running ubuntu 12.04

i have tried installing wizard pen as mentioned in the tutorial in ubuntu forums 
i downloaded this xorg-input-wizardpen-0.8.1

**immy@immy-Lenovo-B460e:~$ ls /usr/lib/xorg/modules/input/wizardpen_drv.***
/usr/lib/xorg/modules/input/wizardpen_drv.la
/usr/lib/xorg/modules/input/wizardpen_drv.so

**i have the following in the .fdi file**
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP4030U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
		     </match>
            </device>
            </deviceinfo>

**immy@immy-Lenovo-B460e:~$ xinput list**
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP4030U                 	id=9	[slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; Ideapad extra buttons                   	id=12	[slave  keyboard (3)]


**immy@immy-Lenovo-B460e:~$ lsusb**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 5543:0003 UC-Logic Technology Corp. Tablet WP4030U

[B]immy@immy-Lenovo-B460e:~$ xinput list-props 9
[/B]Device 'UC-LOGIC Tablet WP4030U':
	Device Enabled (132):	1
	Coordinate Transformation Matrix (134):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (253):	0
	Device Accel Constant Deceleration (254):	1.000000
	Device Accel Adaptive Deceleration (255):	1.000000
	Device Accel Velocity Scaling (256):	10.000000

**vi /usr/share/X11/xorg.conf.d/70-wizardpen.conf**

Section "InputClass"
* *Identifier "wizardpen"
* *MatchIsTablet "on"
* *MatchDevicePath "/dev/input/event*"
* *MatchTag "wizardpen"
* *Driver "wizardpen"
* *Option * * * * * * * "TopX" * * * * *"1506"
* *Option * * * * * * * "TopY" * * * * *"2705"
* *Option * * * * * * * "BottomX" * * * "31225"
* *Option * * * * * * * "BottomY" * * * "30892"
EndSection

Edit: I tried to do an **sudo add-apt-repository ppa:doctormo/xorg-wizardpen** the ppa repository was set to natty ... now even the cursor movement stopped

Edit2: I reinstalled the wizardpen 0.8.1 and got back control over cursor movement and buttons ... still no pressure sensitivity.

ps: i ve read through a lot of posts and i see a drive called endev ... if u think i d have better chance of success with that please tell me how to remove wizardpen and install that

SOLVED: i got the pressure to work on gimp and my paint but not on krita

i tried to do the thing as seen in comments here but i am not able to find that file in ubuntu12.04

[https://bugreports.qt-project.org/browse/QTBUG-25329?focusedCommentId=178238&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-178238](https://bugreports.qt-project.org/browse/QTBUG-25329?focusedCommentId=178238&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-178238)



Please help get my tablet working. Thank you in advance :).

---

### Post by Zeealex on 2012-07-01
> **Favux said:**
> Hi Zealex,

I think your Trust TB-5300 is the "UC-Logic Tablet WP5540U".  You can run in a terminal:
```
xinput list
```to confirm that.  Please post the output.  (Posting the output of **lsusb** would also be good.)

If so it should work out of the box.  There should be a kernel driver supporting it and it should run on the evdev X driver:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

The match to the evdev driver would be at /usr/share/X11/xorg.conf.d in the 10-evdev.conf:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_xf86-input-evdev](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_xf86-input-evdev)

After running **xinput list** use the <device name> you find for the tablet in the following terminal command:
```
xinput list-props "device name"
```And that should tell us if it is on evdev.  Go ahead and post the output.

My apologies for not getting back to you, it turns out that a simple restart of the computer was needed, the PC was going a bit loopy. thank you for your efforts though ;)

---

### Post by NoReflection on 2012-08-20
I am running into a problem, I didn't look threw all 31 pages though so I am sorry. I kept running into errors while running the make and install commands with out being root. 

I used sudo and no more errors but when I check the install it gives me this error. 

```
patrick@ubuntu:~/Desktop/wizardpen-0.7.0-alpha2$ ls /usr/lib/xorg/modules/input/wizardpen_drv.*ls: cannot access /usr/lib/xorg/modules/input/wizardpen_drv.*: No such file or directory
```I am assuming it didn't install but why if it didn't give me any errors on installing it

---

### Post by Favux on 2012-08-20
Hi NoReflection,

WizardPen is no more in Precise.  I'm guessing you are using Precise, correct?

Depending on the tablet it probably either uses the evdev or wacom X driver.  What is the tablet model?  And post the output of **xinput list** in a terminal so we can check the oem and product ID.

And I tried compiling WizardPen in Precise and it seemed to go OK except I didn't see the X driver either.  Also got no errors.  So maybe not the best Makefile or whatever.  I haven't had time to look into it further but I plan to at some point.

---

### Post by NoReflection on 2012-08-22
I see! That explains a lot. I am able to get it to "work" but calibration is all off. It is a DigiPro 4x5.  Here is the xinput list:

```
patrick@ubuntu:~$ xinput list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627;   TABLET DEVICE                           id=8    [slave  pointer  (2)]
&#9116;   &#8627; 2.4G Wireless Mouse                       id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=10   [slave  keyboard (3)]
```

---

### Post by Favux on 2012-08-22
Alright it is showing up in **xinput list** as "TABLET DEVICE" as you already know.  Oops sorry, looks like I forgot to say we really need the output of **lsusb** in a terminal too.  That's the one that has the oem and product ID.

---

### Post by NoReflection on 2012-08-22
There ya go."WP5540U"

```
patrick@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1058:1021 Western Digital Technologies, Inc. Elements 2TB
Bus 002 Device 004: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 64MB QDI U2 DISK
Bus 003 Device 002: ID 5543:0004 UC-Logic Technology Corp. Tablet WP5540U
Bus 003 Device 003: ID 04f3:02f4 Elan Microelectronics Corp. 2.4G Cordless Mouse
patrick@ubuntu:~$ 

```

---

### Post by Favux on 2012-08-22
Alright.
```
Bus 003 Device 002: ID 5543:0004 UC-Logic Technology Corp. Tablet WP5540U
```
Vendor ID (VID) = 5543 = UC-Logic
Product ID (PID) = 0004 = WP5540U

The DIGI*mend* project calls it the UC-Logic Tablet WP5540U and says it is supported by the kernel and evdev:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

So supposedly it should work out of the box in Precise with the tablet on the evdev X driver.  Let's check what's going on with:
```
xinput list-props 8
```
ID number can change if you hot plug or restart.  So you might want to check it with **xinput list** again.  And of course the tablet's usb cable should be plugged in.

---

### Post by NoReflection on 2012-08-23
would I be correct to assume that this is saying it is only taking  242-243 px of the tablet? I have dual 23" wide screens. And it only  allows me to move the pen about half of that on only one screen. I am  not able to move the pen from one monitor to the next. 

Well it sort of made a lier out of me. seems I can move from screen to screen.  But as soon as I press down on the tip the courser locks up and only way I can move it is my pressing down and moving where I should be able to hover and move

```
patrick@ubuntu:~/Documents$ xinput list-props 8
Device '  TABLET DEVICE':
        Device Enabled (121):   1
        Coordinate Transformation Matrix (123): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (245):     0
        Device Accel Constant Deceleration (246):       1.000000
        Device Accel Adaptive Deceleration (247):       1.000000
        Device Accel Velocity Scaling (248):    10.000000
        Device Product ID (238):        21827, 4
        Device Node (239):      "/dev/input/event5"
        Evdev Axis Inversion (249):     0, 0
        Evdev Axis Calibration (250):   <no items>
        Evdev Axes Swap (251):  0
        Axis Labels (252):      "Abs X" (242), "Abs Y" (243), "Abs Pressure" (244)
        Button Labels (253):    "Button Left" (124), "Button Middle" (125), "Button Right" (126), "Button Wheel Up" (127), "Button Wheel Down" (128)
        Evdev Middle Button Emulation (254):    0
        Evdev Middle Button Timeout (255):      50
        Evdev Third Button Emulation (256):     0
        Evdev Third Button Emulation Timeout (257):     1000
        Evdev Third Button Emulation Button (258):      3
        Evdev Third Button Emulation Threshold (259):   20
        Evdev Wheel Emulation (260):    0
        Evdev Wheel Emulation Axes (261):       0, 0, 4, 5
        Evdev Wheel Emulation Inertia (262):    10
        Evdev Wheel Emulation Timeout (263):    200
        Evdev Wheel Emulation Button (264):     4
        Evdev Drag Lock Buttons (265):  0

```

---

### Post by Favux on 2012-08-23
OK, so it is on the evdev driver according to **list-props**.
> I have dual 23" wide screens. And it only allows me to move the pen about half of that on only one screen.  I can move from screen to screen.
To map the tablet to one screen you'll have to use the CTM method because your tablet doesn't use the Wacom X driver.  The CTM is the Coordinate Transformation Matrix you see in **list-props**.  See the dual monitor HOW TO:  [http://ubuntuforums.org/showthread.php?t=1656089](http://ubuntuforums.org/showthread.php?t=1656089)
> But as soon as I press down on the tip the courser locks up and only way I can move it is my pressing down and moving where I should be able to hover and move
Now that's a good question.  I don't know if the evdev X driver supports hover mode, i.e. it detects pen tip proximity and after a distance threshold (pen close enough to the tablet) has been passed it gives control of the pointer to the pen.  Since it gives the tablet Absolute axes maybe it acts like the TabletPCButton on parameter in Wacom and the pen tip actually has to be touching the tablet.  So what we want to know is does evdev detect proximity?  I don't see a proximity Option in 'man evdev'.

Now it seems to me some pen's have a physical proximity adjustment in the pen.  You might want to check your manual for that.  Maybe your pen's is set very low/close and you just need to adjust it.

---

### Post by NoReflection on 2012-08-23
I guess I should say first that when I plug in the tablet and "wake it up" I am able to move around the way it should be with hovering. but as soon as  I try to draw it "locks" to the screen, still moves around. and right click works. I am not sure how to get into settings with the pen since the configuration is controlled by software and It is only supported for Mac or Windows.

---

### Post by Crissie on 2012-10-03
Hi. Im really new to this so I don't really know how to use ubuntu well. I found this and tried it but still my tablet doesn't work. I'm using ubuntu 12.04 and I have a Genius MousePen i608X. When I connect it I can move the pen around the screen but when I'm going to click (for example, using a web browser) it goes one page back, if I click again, it does the same. Someone could help me please?

---

### Post by Favux on 2012-10-03
Hi Crissie,

Welcome to Ubuntu forums!


This HOW TO is outdated now and doesn't apply to Ubuntu Precise (12.04).

Your Genius MousePen i608X is a fairly new tablet and isn't supported by the 3.2 kernel in Precise.  If you look at the DIGI*mend* site:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend)  you'll see the link to "Tablet support status" page:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)  There you'll see that your **KYE MousePen i608X** (0458:5011) is supported by the 3.4 kernel.

So you have 3 choices.  Wait for Quantal (12.10) which is due out in a couple of weeks.  Or use one of the kernels Nick has compiled with support for your tablet:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Kernel_packages](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Kernel_packages)  Or apply the patches yourself:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Kernel_patches](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Kernel_patches)  Rather than rolling an entire kernel you can take a shortcut:  [http://ubuntuforums.org/showthread.php?t=1946486](http://ubuntuforums.org/showthread.php?t=1946486)

Of course the last two options are a bit advanced for a newbie.  :)

---

### Post by Crissie on 2012-10-04
Thank you Favux! I think I'll better wait for Quantal. ^^'

---

### Post by cereyanakapilma on 2012-10-24
I use wp8060 (UC-Logic Tablet WP8060U)
It'snt work in ubuntu 12.04 and ubuntu 12.10. In old version of ubuntu, I use wizardpen but now I can't use it. And I tried to use Digimed but It does'nt work on ubuntu 12.04 and ubuntu 12.10.

---

### Post by Favux on 2012-10-24
Hi cereyanakapilma,

Your tablet should work out of the box according the [DIGI*mend*]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend") site:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

How does your tablet behave when on the evdev driver?  Could you post the tablet line in the output of?:
```
lsusb
```


**[SIZE="3"]FYI Everybody[/SIZE]**

We've just learned how to compile the WizardPen driver in Precise and it seems to work.  So I imagine it should work in Oneiric and it would be interesting to try it in Quantal.  The "HOW TO" needs a little polishing still but you can find it here:  [http://ubuntuforums.org/showpost.php?p=12307583&postcount=27](http://ubuntuforums.org/showpost.php?p=12307583&postcount=27)  [It is on the  HOW TO Add Support for KYE, UC-logic, and Waltop Tablets in Ubuntu]("http://ubuntuforums.org/showthread.php?t=1946486") thread.

So folks whose tablet is not yet supported, see DIGI*mend* link above, should have a work around.  Don't forget to submit [tablet diagnostics]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Collecting_tablet_diagnostics") if you have an unsupported/new tablet.

**Also DIGI*mend* is actively soliciting developers to help with the workload.**

---

### Post by cereyanakapilma on 2012-10-24
[QUOTE=Favux;12315576]Hi cereyanakapilma,

Your tablet should work out of the box according the [DIGI*mend*]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend") site:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

How does your tablet behave when on the evdev driver?  Could you post the tablet line in the output of?:
```
lsusb
```

```
onuruluturhan@onuruluturhan:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. Bluetooth Controller
Bus 004 Device 002: ID 5543:0041 UC-Logic Technology Corp. Genius PenSketch 6x8 Tablet
```

---

### Post by Favux on 2012-10-24
Thank you for the lsusb output.  Okay your UC-Logic Technology Corp. Genius PenSketch 6x8 Tablet is not supported.  While the 0042 (Genius PenSketch 12x9) is supported the 0041 isn't.  Mystery solved.

Muy-buro has the same tablet and already submitted the diagnostics for it to the DIGI*mend* site.  You could monitor the mailing list and help test the kernel driver when Nick posts it.

In the meantime we have it working using the WizardPen driver.  See the link I gave above.  The example .conf file on the HOW TO for Muy-buro applies to your tablet too.

---

### Post by barneyjoseph on 2012-12-11
Hi,

I have an iBall PF1209 Drawing Tablet. The Tablet works and the sensitivity fine too. I do have one problem and I am not sure how to explain it. I'll try my best however. Here goes:

My computer has Windows Vista and Ubuntu installed side by side. The Tablet works fine on Vista as you can see below: Working on Gimp in Vista:
[IMG]http://i1082.photobucket.com/albums/j375/barney_joseph/Misc/test_vista.jpeg[/IMG]

In Ubuntu the pointer moves and sometimes gets stuck while moving/when a button is pressed/when a menu opens up. There is no telling when the pointer will stop following. The solution for me is to lift my hand off the tablet and place it back again. The pointer will jump to which ever position it wants and will return to the point that I want it to. The effect is like this: Using MyPaint in Ubuntu:
[IMG]http://i1082.photobucket.com/albums/j375/barney_joseph/Misc/test_ubuntu.jpg[/IMG]

Can someone please help me? This used to work before. I had to reinstall my computer and therefore reinstall Wizardpen. I know that this has worked very well in Ubuntu, Windows Xp Sp2, Sp3 and Windows Vista Business. I have no clue as to how to make this work now!

Thanks in advance for ANY help!

---

### Post by barneyjoseph on 2012-12-12
In case anyone was following.... I've checked for duplicity in the xinput list.... that didn't work. There was a troubleshooting tip about the double click problem.... commented out the settings in 70-wizardpen.conf. But it still happens!

I've found out that the jumping happens only when there is a hard press on the pen and not for a slight stroke..... Please help! I've added a picture from MyPaint:
[IMG]http://i1082.photobucket.com/albums/j375/barney_joseph/Misc/test2_ubuntu.jpg[/IMG]

---

### Post by barneyjoseph on 2012-12-12
The same thing happens in Gimp too... just in case anyone has the question! It's just that MyPaint shows the return stroke while Gimp doesn't show. In Gimp, if the pressure hits a max and goes below in the same stroke itself, the pointer gets stuck at the position of change of pressure!

I've tried to reinstall wizard pen! 

I have an iBall PF1209 Tablet. But:```
lsusb

Bus 005 Device 004: ID 19d2:fff1 ONDA Communication S.p.A. 
Bus 005 Device 003: ID 5543:0042 UC-Logic Technology Corp. Genius PenSketch 12x9 Tablet
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0079:0006 DragonRise Inc. Generic USB Joystick
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0461:4d22 Primax Electronics, Ltd 
Bus 002 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```If this is the case the iBall PF1209 is internally known as UC-Logic Genius PenSketch 12x9 Tablet.  What then is the MatchVendor value?

I've also set the "TopZ" to "10" and the "BottomZ" to "1024" in  /etc/X11/xorg.conf.
```
Section "InputDevice"
    Identifier     "WizardPen Tablet"
    Driver         "wizardpen"
    Option         "Device" "/dev/input/by-id/usb-_TabletPF1209_-event-mouse"
    Option         "TopX" "0"
    Option         "TopY" "1553"
    Option         "BottomX" "32541"
    Option         "BottomY" "32762"
    Option       "TopZ"  "10"
    Option       "BottomZ"  "1024"
EndSection

```Here is the output of the events:
```
grep -i name /proc/bus/input/devices
N: Name="Power Button"
N: Name="Power Button"
N: Name="Dell Dell USB Keyboard"
N: Name="USB Optical Mouse"
N: Name="                TabletPF1209"
N: Name="                TabletPF1209"
N: Name="                TabletPF1209"
N: Name="DragonRise Inc.   Generic   USB  Joystick  "
``` Yup... the name shows up in a weird way :( I hope I have given all the data to any kind soul who is willing to help me. And yes, I did try changing the pen's nib :(

---

### Post by Favux on 2012-12-14
Hi barneyjoseph,

OK, so a iBall PF1209 Drawing Tablet.  And with **lsusb** you've identified the Vendor ID (VID) and Product ID (PID):  5543:0042

You can see the DIGImend project says it is a supported tablet:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)  calling it the UC-Logic Tablet PF1209.

So what we need to know is what release of Ubuntu are you using?  The ouput of the following command in a terminal will tell us the same thing:
```
Xorg -version
```

---

### Post by barneyjoseph on 2012-12-17
Hi Fauvx,

Thanks for replying... here's what you asked for:

```
X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux barney-OptiPlex-360 2.6.35-32-generic #67-Ubuntu SMP Mon Mar 5 19:35:26 UTC 2012 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-32-generic root=UUID=78c47e03-e705-4d1a-8296-e9078fec647d ro quiet splash
Build Date: 20 October 2011  03:03:54PM
xorg-server 2:1.9.0-0ubuntu7.6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
```

---

### Post by Favux on 2012-12-17
That appears to be Maverick.  Vanilla Maverick Gnome?

While Maverick was my favorite release so far since it is no longer supported we probably shouldn't spend much time trying to set your tablet up on it unless you confirm that you want to continue using it.

Anyway with Maverick we're still using the WizardPen driver that I assume you got from Martin Owen's PPA?:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen/](https://launchpad.net/~doctormo/+archive/xorg-wizardpen/)  I ask because your wizardpen.conf file seems custom and not the one that would have come from the PPA package.

Also please post the output of the following command in a terminal:
```
xinput list
```
That will help us with the match in the .conf file.

---

### Post by barneyjoseph on 2012-12-18
I followed the tutorial posted here: [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen). I am using Ubuntu Maverick Meerkat 10.10.

```
xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=9    [slave  pointer  (2)]
&#9116;   &#8627;                 TabletPF1209               id=10    [slave  pointer  (2)]
&#9116;   &#8627;                 TabletPF1209               id=11    [slave  pointer  (2)]
&#9116;   &#8627;                 TabletPF1209               id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Dell Dell USB Keyboard                      id=8    [slave  keyboard (3)]
```This is what I've added to my xorg.conf file [etc/X11/xorg.conf]:
```
Section "InputDevice"
    Identifier     "WizardPen Tablet"
    Driver         "wizardpen"
    Option         "Device" "/dev/input/by-id/usb-_TabletPF1209_-event-mouse"
    Option         "TopX" "0"
    Option         "TopY" "1553"
    Option         "BottomX" "32541"
    Option         "BottomY" "32762"
    Option       "TopZ"  "10"
    Option       "BottomZ"  "1024"
EndSection
```And here is usr/share/X11/xorg.conf.d/70-wizardpen.conf:
```
Section "InputClass"
   Identifier      "wizardpen"
   MatchIsTablet   "on"
   MatchDevicePath "/dev/input/by-id/usb-_TabletPF1209_-event-mouse"
   MatchProduct    "TabletPF1209"
   MatchVendor     "UC-LOGIC|Genius|PenSketch|TabletPF1209"
   MatchTag        "wizardpen"
   Driver          "wizardpen"
EndSection

Section "InputClass"
   Identifier      "wizardpen ignore mouse dev"
   MatchDevicePath "/dev/input/by-id/usb-_TabletPF1209_-mouse"
   MatchTag        "wizardpen"
   Driver          "mouse"
   Option          "MouseSpeed" "16"
   Option          "ignore"     "true"
EndSection

```Thanks once again!

---

### Post by Favux on 2012-12-18
OK, so method 1, in other words the PPA?

Let's try to clean up your .conf files a bit.  First remove the xorg.conf section with the coordinate options.  Those can go in the wizardpen.conf.  Or you could use a custom .conf file for them, called say 72-wizardpen.conf in the /etc/X11/xorg.conf.d directory.
```
#Section "InputDevice"
#    Identifier     "WizardPen Tablet"
#    Driver         "wizardpen"
#    Option         "Device" "/dev/input/by-id/usb-_TabletPF1209_-event-mouse"
#    Option         "TopX" "0"
#    Option         "TopY" "1553"
#    Option         "BottomX" "32541"
#    Option         "BottomY" "32762"
#    Option       "TopZ"  "10"
#    Option       "BottomZ"  "1024"
#EndSection
```
The original 0.7.4 wizardpen.conf file that comes from the PPA for Maverick reads:
```
Section "InputClass"
   Identifier      "wizardpen"
   MatchIsTablet   "on"
   MatchDevicePath "/dev/input/event*"
   MatchTag        "wizardpen"
   Driver          "wizardpen"
EndSection

Section "InputClass"
   Identifier      "wizardpen ignore mouse dev"
   MatchDevicePath "/dev/input/mouse*"
   MatchTag        "wizardpen"
   Driver          "mouse"
   Option          "MouseSpeed" "16"
   Option          "ignore"     "true"
EndSection
```
And should work provided you have the 67-wizardpen.rules in /lib/udev/rules.d.  But I believe I have run into it not working for the PF1209 before.  Maybe the MatchTag line doesn't work.

Now the **TabletPF1209** keyword can only be used in a MatchProduct line not a MatchVendor line.  No need for the explicit MatchPath.  The driver does not support a tablet mouse.  You can use all of the coordinates in the wizardpen.conf, no need for the xorg.conf entry.
```
Section "InputClass"
   Identifier      "wizardpen"
#   MatchIsTablet   "on"
   MatchProduct    "TabletPF1209"
   MatchDevicePath "/dev/input/event*"
   Driver          "wizardpen"
   Option          "TopX" "0"
   Option          "TopY" "1553"
   Option          "BottomX" "32541"
   Option          "BottomY" "32762"
   Option          "TopZ"  "10"
   Option          "BottomZ"  "1024"
EndSection

Section "InputClass"
   Identifier      "wizardpen ignore mouse dev"
   MatchProduct    "TabletPF1209"
   MatchDevicePath "/dev/input/mouse*"
   Option          "ignore"     "true"
EndSection
```
If you want to try MatchTablet and it works, fine.

---

### Post by barneyjoseph on 2012-12-18
Dear Fauvx,

Thank you so much for helping me fix the jumping problem. The pointer doesn't get stuck anymore. There is one teensy problem.... the Tablet seems to be mapped to only a small rectangle area of the display. It isn't somehow reading in the Top and Bottom X&Y sizes put into any of the .conf files.

Here's what I've done.... I've commented out all the entries in the xorg.conf file. I've put them into 72-wizardpen.conf in the /etc/X11/xorg.conf.d.


```
Section "InputDevice"     Identifier     "WizardPen Tablet"     Driver         "wizardpen"     Option         "Device" "/dev/input/by-id/usb-_TabletPF1209_-event-mouse"     Option         "TopX" "0"     Option         "TopY" "1553"     Option         "BottomX" "32541"     Option         "BottomY" "32762"     Option       "TopZ"  "10"     Option       "BottomZ"  "1024" EndSection
```

And this is what is there in the 70-wizardpen.conf in /usr/share/X11/xorg.conf.d folder
```

Section "InputClass"    Identifier      "wizardpen" #   MatchIsTablet   "on"    MatchProduct    "TabletPF1209"    MatchDevicePath "/dev/input/event*"    Driver          "wizardpen"    Option          "TopX" "0"    Option          "TopY" "1553"    Option          "BottomX" "32541"    Option          "BottomY" "32762"    Option          "TopZ"  "10"    Option          "BottomZ"  "1024" EndSection  Section "InputClass"    Identifier      "wizardpen ignore mouse dev"    MatchProduct    "TabletPF1209"    MatchDevicePath "/dev/input/mouse*"    Option          "ignore"     "true" EndSection
```

---

### Post by Favux on 2012-12-18
Good!
> the Tablet seems to be mapped to only a small rectangle area of the display
If I understand you correctly you do not need the 72-wizardpen.conf in the /etc/X11/xorg.conf.d because it is duplicating your 70-wizardpen.conf file in /usr/share/X11/xorg.conf.d. Besides matching to the specific mouse device path for coordinates wouldn't work, the coordinates have to apply to the pen not the unsupported mouse.

Let's make sure it is on the WizardPen driver.  Enter the following command in a terminal:
```
xinput list-props 10
```
First check in **xinput list** that 10 is the ID number for the first TabletPF1209 line in the output.  ID numbers can change.  And post the output.

Or you could also look at the Xorg.0.log in /var/log.

But the coordinates you had in the xorg.conf don't look correct anyway.  Try changing:
```
   Option          "TopY" "1553"
```
to.
```
   Option          "TopY" "0"
```
and see where that gets you.  You could also comment out the X and Y coordinates and see if the driver comes up with the correct ones on its own.

Another option is to use xinput_calibrator to determine the coordinates.  It should be in the repositories.

---

### Post by barneyjoseph on 2012-12-18
Here's the output:

```
xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; WizardPen Tablet                            id=6    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=10    [slave  pointer  (2)]
&#9116;   &#8627;                 TabletPF1209               id=11    [slave  pointer  (2)]
&#9116;   &#8627;                 TabletPF1209               id=12    [slave  pointer  (2)]
&#9116;   &#8627;                 TabletPF1209               id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Dell Dell USB Keyboard                      id=9    [slave  keyboard (3)]
barney@barney-OptiPlex-360:~$ xinput list-props 11
Device '                TabletPF1209':
    Device Enabled (121):    1
    Coordinate Transformation Matrix (123):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (239):    0
    Device Accel Constant Deceleration (240):    1.000000
    Device Accel Adaptive Deceleration (241):    1.000000
    Device Accel Velocity Scaling (242):    10.000000
barney@barney-OptiPlex-360:~$ xinput list-props 12
Device '                TabletPF1209':
    Device Enabled (121):    1
    Coordinate Transformation Matrix (123):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (239):    0
    Device Accel Constant Deceleration (240):    1.000000
    Device Accel Adaptive Deceleration (241):    1.000000
    Device Accel Velocity Scaling (242):    10.000000
barney@barney-OptiPlex-360:~$ xinput list-props 13
Device '                TabletPF1209':
    Device Enabled (121):    1
    Coordinate Transformation Matrix (123):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (239):    0
    Device Accel Constant Deceleration (240):    1.000000
    Device Accel Adaptive Deceleration (241):    1.000000
    Device Accel Velocity Scaling (242):    10.000000

```

---

### Post by barneyjoseph on 2012-12-18
And this is what is there inside Xorg.0.log:

```
[    21.883] (II) config/udev: Adding input device                 TabletPF1209 (/dev/input/event4)
[    21.883] (**)                 TabletPF1209: Applying InputClass "evdev tablet catchall"
[    21.883] (**)                 TabletPF1209: Applying InputClass "wizardpen"
[    21.883] (**) Option "Device" "/dev/input/event4"
[    21.896] (--)                 TabletPF1209: MaxX:24000 MaxY:18000 MaxZ:1023
[    21.896] (--)                 TabletPF1209: aspect ratio:2.00:1
[    21.896] (**)                 TabletPF1209 is in absolute mode
[    21.896] (II)                 TabletPF1209: ScreenX = 1024, ScreenY = 768
[    21.896] (**)                 TabletPF1209: TopX                   = 0
[    21.896] (**)                 TabletPF1209: TopY                   = 1553
[    21.896] (**)                 TabletPF1209: BottomX                = 32541
[    21.896] (**)                 TabletPF1209: BottomY                = 32762
[    21.896] (**)                 TabletPF1209: TopZ    (min pressure) = 10
[    21.896] (**)                 TabletPF1209: BottomZ (max pressure) = 1024
[    21.896] (**)                 TabletPF1209: always reports core events
[    21.904] (II) XINPUT: Adding extended input device "                TabletPF1209" (type: WizardPen Tablet)
[    21.904] (II)                 TabletPF1209 Increment: 23
[    21.920] (II) config/udev: Adding input device                 TabletPF1209 (/dev/input/mouse1)
[    21.920] (**)                 TabletPF1209: Ignoring device from InputClass "wizardpen ignore mouse dev"
[    21.920] (II) config/udev: Adding input device                 TabletPF1209 (/dev/input/event5)
[    21.920] (**)                 TabletPF1209: Applying InputClass "evdev pointer catchall"
[    21.920] (**)                 TabletPF1209: Applying InputClass "evdev tablet catchall"
[    21.920] (**)                 TabletPF1209: Applying InputClass "wizardpen"
[    21.920] (**) Option "Device" "/dev/input/event5"
[    21.936] (--)                 TabletPF1209: MaxX:1904717 MaxY:2902599 MaxZ:0
[    21.936] (--)                 TabletPF1209: aspect ratio:2.00:1
[    21.936] (**)                 TabletPF1209 is in absolute mode
[    21.936] (II)                 TabletPF1209: ScreenX = 1024, ScreenY = 768
[    21.936] (**)                 TabletPF1209: TopX                   = 0
[    21.936] (**)                 TabletPF1209: TopY                   = 1553
[    21.936] (**)                 TabletPF1209: BottomX                = 32541
[    21.936] (**)                 TabletPF1209: BottomY                = 32762
[    21.936] (**)                 TabletPF1209: TopZ    (min pressure) = 10
[    21.936] (**)                 TabletPF1209: BottomZ (max pressure) = 1024
[    21.936] (**)                 TabletPF1209: always reports core events
[    21.952] (II) XINPUT: Adding extended input device "                TabletPF1209" (type: WizardPen Tablet)
[    21.952] (II)                 TabletPF1209 Increment: 1860
[    21.968] (II) config/udev: Adding input device                 TabletPF1209 (/dev/input/mouse2)
[    21.968] (**)                 TabletPF1209: Ignoring device from InputClass "wizardpen ignore mouse dev"
[    21.968] (II) config/udev: Adding input device                 TabletPF1209 (/dev/input/event6)
[    21.968] (**)                 TabletPF1209: Applying InputClass "evdev tablet catchall"
[    21.968] (**)                 TabletPF1209: Applying InputClass "wizardpen"
[    21.968] (**) Option "Device" "/dev/input/event6"
[    21.984] (--)                 TabletPF1209: MaxX:24000 MaxY:18000 MaxZ:1023
[    21.984] (--)                 TabletPF1209: aspect ratio:2.00:1
[    21.984] (**)                 TabletPF1209 is in absolute mode
[    21.984] (II)                 TabletPF1209: ScreenX = 1024, ScreenY = 768
[    21.984] (**)                 TabletPF1209: TopX                   = 0
[    21.984] (**)                 TabletPF1209: TopY                   = 1553
[    21.984] (**)                 TabletPF1209: BottomX                = 32541
[    21.984] (**)                 TabletPF1209: BottomY                = 32762
[    21.984] (**)                 TabletPF1209: TopZ    (min pressure) = 10
[    21.984] (**)                 TabletPF1209: BottomZ (max pressure) = 1024
[    21.984] (**)                 TabletPF1209: always reports core events
[    22.000] (II) XINPUT: Adding extended input device "                TabletPF1209" (type: WizardPen Tablet)
[    22.000] (II)                 TabletPF1209 Increment: 23
[    22.016] (II) config/udev: Adding input device                 TabletPF1209 (/dev/input/mouse3)
[    22.016] (**)                 TabletPF1209: Ignoring device from InputClass "wizardpen ignore mouse dev"

```

---

### Post by Favux on 2012-12-18
The list-props indicates it is on the WizardPen driver because the evdev driver would announce itself in the output while the WizardPen doesn't.  Xorg.0.log confirms it.

Also from the Xorg.0.log it looks like the driver knows the coordinates and you probably don't need to specify them for X and Y.
> --)                 TabletPF1209: MaxX:24000 MaxY:18000 MaxZ:1023
However if you do this is what it is saying to use:
```
   Option          "TopX" "0"
   Option          "TopY" "0"
   Option          "BottomX" "24000"
   Option          "BottomY" "18000"
```
And you should change:
```
   Option          "BottomZ"  "1024"
```
to.
```
   Option          "BottomZ"  "1023"
```
Since 0 counts as a pressure level 0 to 1023 is 1024 levels whereas 0 to 1024 is 1025 levels.  Sorry should have caught that before.

---

### Post by barneyjoseph on 2012-12-18
[SOLVED]

Thanks a million times million. I eventually commented out all Top and Bottom X&Y values and set BottomZ to "1023"

That did the trick. The tablet works fine in File Explorer, Gimp and MyPaint.

Thanks once again Fauvx.

Check out my [blog]("http://barneyjoseph.blogspot.in") once in a while to see my artwork in clay and on the tablet. It all starts with my tablet :)

Regards,
Barney.

---

### Post by Favux on 2012-12-18
Great.  Nice work!

Thanks for the link to your blog.  :)

---

### Post by barneyjoseph on 2012-12-18
Don't be a stranger :)

---

### Post by mladenkovacevic on 2013-01-19
I tried posting this question in the "Hardware" forum but I'm not getting any responses so I thought I'd try here.

Anyways, I purchased this Chinese made drawing tablet: [http://www.huion-tablet.com/product/...t.php?sku=1004](http://www.huion-tablet.com/product/...t.php?sku=1004)

It works excellent in Windows with the drivers they've provided and I managed to get it working in Linux almost perfectly by installing the wizardpen driver and using the following settings in the 52-tablet.conf file.

```
Code:
Section "InputClass"
    Identifier "UC-Logic tablet"
    MatchIsTablet "on"
    MatchProduct "HUION H610"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
    # Apply custom Options below.
    Option    "TopX"    "0"
    Option    "TopY"    "0"
    Option    "BottomZ"    "2047"
    Option    "BottomX"    "2047"
    Option    "BottomY"    "2047"
EndSection
```

Even after applying these settings I find that the native Windows drives seems to be a little smoother and the button mapping is all wrong on Linux side as well.

How can I modify these settings so that I get the best performance. I set BottomZ to 2047 because the tablet is advertised as having 2048 levels of pressure sensitivity. Am I doing this right? Another concern I have is that when pressure sensitivity is on line thickness, in Linux they look a little bit jagged, while in Windows they are perfect. Hope someone has some ideas. Thanks.

---

