---
title: "Brother Multi-Function Laser Jet"
date: 2019-12-19
forum: Tutorials
---

### Post by dan508 on 2019-12-19
Hello all.  This is a quick guide to getting a Brother Laser printer/scanner working in Ubuntu.  IF you are using version 19.10 you will need to enable the software sources for 18.04 LTS in order to get the scanner to work using sane.  I wanted to write this because there is no real place that had all the answers need to make all the functions work.  Please keep in mind this will work only on USB connection and I did not configure this for networking.  

If you go to this link there is a helpful tool to help get the drivers : [https://support.brother.com/g/b/productsearch.aspx?c=eu_ot&lang=en&content=dl]("https://support.brother.com/g/b/productsearch.aspx?c=eu_ot&lang=en&content=dl")

Step1. Download the tool.(linux-brprinter-installer-*.*.*-*.gz)

The tool will be downloaded into the default "Download" directory.
(The directory location varies depending on your Linux distribution.)
e.g. /home/(LoginName)/Download

Step2. Open a terminal window.

Step3. Go to the directory you downloaded the file to in the last step. By using the cd command.

e.g. cd Downloads

Step4. Enter this command to extract the downloaded file:

Command: gunzip linux-brprinter-installer-*.*.*-*.gz

e.g. gunzip linux-brprinter-installer-2.1.1-1.gz

Step5. Get superuser authorization with the "su" command or "sudo su" command.

Step6. Run the tool:

Command: bash linux-brprinter-installer-*.*.*-* Brother machine name
e.g. bash linux-brprinter-installer-2.1.1-1 MFC-J880DW

Step7. The driver installation will start. Follow the installation screen directions.
 

 When you see the message "Will you specify the DeviceURI ?",

 For USB Users: Choose N(No)
 For Network Users: Choose Y(Yes) and DeviceURI number.

The install process may take some time. Please wait until it is complete.

This will get your printer online as long as you have followed the steps in the setup in the terminal.  However, your scanner will not work.  To get your scanner to work on Ubuntu 19.10 you will need to to the following.

```
sudo apt-add-repository http://cz.archive.ubuntu.com/ubuntu
```
```
sudo apt-get update
```
```
sudo apt-get install libsane-extras
```
```
cd /lib/udev/rules.d/
```

From here you will need to find your libsane.rules file. Mine was located at 60-libsane.rules but depending on version you are using you will need to find yours.  This is a quick bit of info I took from a German website that had published some info on this as well:

In the file /lib/udev/rules.d/55-libsane.rules (in version 16.04 the file is called /lib/udev/rules.d/60-libsane.rules and in version 18.04 /lib/udev/rules.d / 60-libsane.rules !) Add this line to the end of the file:

```
sudo nano xx-libsane.rules
```  Replace the xx with your corresponding number for where the file is located on the system.  

Add this line to the end of the file and save it.

```
# Brother scanners
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="00ab", MODE="0660", GROUP="scanner", ENV{libsane_matched}="yes"
```

Reboot

Now your scanner should be working.  IF you get a message when trying to scan that you cannot connect to the scanner you have one last step.  You will need to add your non non root user name to the group lp.

sudo adduser YOURNONROOTUSERNAME lp

to make sure scanner belongs to lp group:

```
sudo sane-find-scanner

found USB scanner (vendor=0x04f9, product=0x02a5) at libusb:001:002

ls -al /dev/bus/usb/001/002

crw-rw-r-- 1 root lp 189, 1 Nov 24 12:43 /dev/bus/usb/001/002
```

Reboot and everything should work perfectly.  Hope this helps someone.  Here are the links that I went through as I compiled this guide here:

[https://superuser.com/questions/298298/scanning-only-works-under-sudo-ubuntu](https://superuser.com/questions/298298/scanning-only-works-under-sudo-ubuntu)
[https://wiki.ubuntuusers.de/Scanner/Brother/](https://wiki.ubuntuusers.de/Scanner/Brother/)
[https://askubuntu.com/questions/791556/brother-scanner-not-working-in-ubuntu-16-04-though-driver-installed](https://askubuntu.com/questions/791556/brother-scanner-not-working-in-ubuntu-16-04-though-driver-installed)

---

### Post by coffeecat on 2019-12-19
*Thread moved to **Tutorials** sub-forum*.

[https://ubuntuforums.org/showthread.php?t=2143602](https://ubuntuforums.org/showthread.php?t=2143602)

---

