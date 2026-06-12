---
title: "Try Lubuntu before installing (in a VM) graphics problem 18.04"
date: 2018-01-09
forum: Virtualisation
---

### Post by Neill_R on 2018-01-09
Hi

I know there are most likely more important issues to solve but the graphic problem in a virtual machine is not beneficial to getting people to try Lubuntu.

 I noticed this problem back with 16.04 and although a simple work around exists the problem has not been solved. Xubuntu (16.04) did not have this problem.

The work around I have used is to allow the "Try Lubuntu with out Installing" to boot up to the X window screen (total graphic garbage).
Then type <Ctrl><Alt><T> to start a terminal window Then typing blind

**sudo service lightdm restart**

Oracle VirtualBox 5.2.4 

Also Bionic_desktop_i386.iso says 17.10 and not 18.04

---

### Post by killuminati2 on 2018-05-15
The graphic issue even exists in the installed version, until the "VirtualBox Guest Additions" are not installed.

   Lubuntu 18.04 (64 Bit)
   Virtual Box v5.2.6

Workaround:
1. Blind login: Enter your password -> Enter
2. Open the terminal: Ctrl + Alt + t
3. Restart the LightDM daemon (blind input): sudo service lightdm restart -> Enter -> Password -> Enter
    Now the graphical interface should work correctly.
4. Load the "VirtualBox Guest Additions": Devices -> Install Guest Additions...
5. Go to the media "VBox_GAs_x.x.x" and start the installation "sudo bash VBoxLinuxAdditions.run"

Thanks to Neill_R for 1., 2. and 3.

K1LLUM1N471

---

### Post by cruzer001 on 2018-05-15
Could a upgrade solve this?

[https://ubuntuforums.org/showthread.php?t=2391807&p=13766409#post13766409](https://ubuntuforums.org/showthread.php?t=2391807&p=13766409#post13766409)

---

### Post by slickymaster on 2018-05-15
Thread moved to **Virtualisation** since 18.04 is released

---

### Post by Claus7 on 2018-06-08
Hello,

> **killuminati2 said:**
> The graphic issue even exists in the installed version, until the "VirtualBox Guest Additions" are not installed.

   Lubuntu 18.04 (64 Bit)
   Virtual Box v5.2.6

Workaround:
1. Blind login: Enter your password -> Enter
2. Open the terminal: Ctrl + Alt + t
3. Restart the LightDM daemon (blind input): sudo service lightdm restart -> Enter -> Password -> Enter
    Now the graphical interface should work correctly.
4. Load the "VirtualBox Guest Additions": Devices -> Install Guest Additions...
5. Go to the media "VBox_GAs_x.x.x" and start the installation "sudo bash VBoxLinuxAdditions.run"

Thanks to Neill_R for 1., 2. and 3.

K1LLUM1N471

just to mention that:
in step2 I pressed Ctrl+Alt+F2
then,for step3, right away I pressed Ctrl+Alt+F7 and logged in as normal
and prior to step 4 I installed build essential (it is required for the installation of guest additions, found under Menu->System Tools)
for step 5,in my case, the exact path was: /media/lubuntu/VBox_GAs_5.2.12 (since Lubuntu is using by default the PCManFM file manager, the open-terminal is activated pressing F4). 

The memory usage using 2 tabs of ubuntu forums in firefox is: 630-680MB
And just the OS: 218MB!

Regards!

---

