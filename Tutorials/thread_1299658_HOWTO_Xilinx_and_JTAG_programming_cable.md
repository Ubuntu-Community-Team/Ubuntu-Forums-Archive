---
title: "HOWTO Xilinx and JTAG programming cable"
date: 2009-10-24
forum: Tutorials
---

### Post by dimamali on 2009-10-24
UPDATE: Works with 10.04.

I 've spend a really long time trying to install and use the Xilinx Webpack suite on various Linux distros. I have finaly made it and i wouldn't have without the serious efforts of a lot of people out there. So this is my contribution to the community. I hope it works for most of you as it did for me with various editions of the software in various machines with almost all the up-to-date Ubuntu distros (8.04 and beyond).

I am currently using the Xilinx Webpack 11.1, updated on 9.04, 32-bit. 

**1.DOWNLOAD**
To begin with, visit the xilinx site and download the Xilinx Webpack software. Do not try the webinstall as it has never worked for a lot of people, incuding me.

**2.INSTALL**
Make sure you have _root privileges_ before you begin so you won't have any problems in touching system folders.
```
>sudo su
(it will prompt you for your password)
```Install webpack ignoring any driver errors that will occur. You can do that by typing: 
```
> cd /opt/Xilinx_11.1_WebPack_SFD/
> ./xsetup

```It will take a long time and it will take a llot longer if you coose to update the software.
You should have a Xilinx folder in your /opt folder now. JFYI if you ever feel that you don't need Xilinx anymore, you can just delete the folder and you are done.

**3.RUN**
Running Webpack components can be a real pain for linux newbies. It was for me, anyway.
You can run any of the components by navigating to the folder where all the Xilinx commads lay.
```
>cd /opt/Xilinx/11.1/ISE/bin/lin
```Being there you just have to give the command you need. 
For example you can run ISE with
```
>ise
```or you can run IMPACT with
```
>impact
```What troubled me most was running Xilinx componets with 3rd party scripts, such as the scripts for Gaisler Aeroflex IPcores and Leon3.
Adding the xilinx executable files to your path will do the job and since you want to use that again and again adding that path to your .bashrc file is the solution.

```
>gedit /home/*username*/.bashrc
```Navigate to the end of the file and add the line
```
export PATH=$PATH:/opt/Xilinx/11.1/ISE/bin/lin
```Save and exit gedit.
Now you should be able to run Xilinx components from anywhere without having to navigate to the /opt/Xilinx/11.1/ISE/bin/lin folder

**4.JTAG**
Using the JTAG was the biggest trouble of all. After reading hundreds of posts around the web, following some dozens of HOWTOs and even managing to crush my whole system once i came across to THE post. The only one that was followed only from Thanking replies.
Thanks to mr Michael Gernoth and his magnificent work my jtag works as a charm and my Spartan3E board is up and running my latest project.
You can find all the info in
[http://groups.google.com/group/comp.arch.fpga/browse_frm/thread/f149e5b6028e2c70](http://groups.google.com/group/comp.arch.fpga/browse_frm/thread/f149e5b6028e2c70)
but i prefer rewritting everything than making you jump from one link to another

Dowload the library source from
[http://cvs.zerfleddert.de/cgi-bin/viewcvs.cgi/usb-driver.tar.gz?view=tar](http://cvs.zerfleddert.de/cgi-bin/viewcvs.cgi/usb-driver.tar.gz?view=tar) 
untar it and place it in the desired folder. I choose to place it in the /opt folder.
```
> cp -r /*path/to/dowloaded*/usb-driver /opt
```Before building the library you need to be sure that you have the latest libusb-dev and libftdi-dev files.
You can do that by typing
```
> apt-get install libusb-dev
> apt-get install libftdi-dev
```Now you should be ready to build the library.
```
> cd /opt/usb-drivers
> make
```The last step is common to the last step of installing Xilinx.
Since the library needs to be preloaded before you start IMPACT and since you want that to be done for you everytime all you need is to add one more line to you .bashrc.
```
> gedit /home/*username*/.bashrc
```At the end of the file add the line
```
export LD_PRELOAD=/*path/to*/libusb-driver.so
```Save and exit gedit.

There might be an issue in using the library as a plain user (not root).
To solve that you can add your user to the lp group.
do that by typing 
```
> useradd -G lp username
```Some minor changes need to be done for 64bit versions of Ubuntu. All you need to know is in the README file located in the usb-driverfolder.

Done!
Community, have fun with your FPGA experiments!

Best regards
Dimitris

---

### Post by crazy_fox on 2010-05-07
Hi,

Do you know if in 10.04 we can just set the LD_PRELOAD to the libusb already in the system? (Found using "whereis libusb")

---

### Post by dimamali on 2010-05-22
Hello,
i'm afraid i don't know if you can do this. Why do you want to do this? I haven't tested it in 10.04 so if there is any kind of problem please let me know.


> **crazy_fox said:**
> Hi,

Do you know if in 10.04 we can just set the LD_PRELOAD to the libusb already in the system? (Found using "whereis libusb")

---

### Post by crazy_fox on 2010-05-22
I wasnt sure if it was using libusb.

It turns out it was, but the libusb is not recognising the Digilent JTAG-USB programmer :/

Thats why it was switching to the other driver.

---

### Post by dimamali on 2010-06-04
Hello crazy_fox. 
I'm pretty sure that just settin the LD_PRELOAD to the libusb has never worked for me.
I just tried the whole process as described in the HOWTO, in a fresh 10.04 distro with Xilinx 11.1 and it seems to work perfect. I'm using a parallel-JTAG cable that comes with the PENDER gr-xc3s-1500 board.

---

### Post by sukigenseki on 2010-08-06
Nevermind

---

### Post by dimamali on 2013-01-10
Dear Community,

I was pleased to be informed that the HOWTO still works for Ubuntu 12.04. Have fun with it!

Regards,
Dimitris

---

### Post by johnnymopo on 2013-04-29
THANK YOU, to you and the supplier of the software (Micheal?)  couple of notes, though.
On the first try, I did not have success on 64 bit Mint (Ubuntu 12.04) with ISE 13.2

running make will create the 64 bit library, and make lib32 creates the 32 bit version.

I'm new to linux/ISE combination, and running >ise or >impact with your exports runs the 32 bit version of ISE/impact, I've finally discovered and the shared libraries will not work if simply running "make"

The export directory for 64 bit versions (at least ISE 13.2) is /opt/Xilinx/13.2/ISE_DS/ISE/bin/lin64

now >ise or >impact will run 64 bit version and link to the shared object.  IT WORKS!! FOR THE FIRST TIME EVER.

Thanks again, and great tutorial, my notes are to help with 64/32 bit complications.

>> for other newbies like me.  Mint uses .profile instead of .bashrc.  .profile will look for .bashrc, though, so creating the file will work fine.

---

### Post by dimamali on 2013-04-30
I am happy it is still useful. If anybody can try it in 13.04 please let us know if it is still working in latest distros. I also plan to move this to the Ubuntu Wiki.

---

