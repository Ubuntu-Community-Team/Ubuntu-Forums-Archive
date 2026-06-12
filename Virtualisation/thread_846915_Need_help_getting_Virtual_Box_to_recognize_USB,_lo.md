---
title: "Need help getting Virtual Box to recognize USB, local hard drive and RS232 (Com port)"
date: 2008-07-02
forum: Virtualisation
---

### Post by MR.UNOWEN on 2008-07-02
Hello,

Just as the title says... I need help getting Virtual Box to recognize USB, local(internal) hard drives and RS232 (Com port). I have XP installed in VB. FYI I'm a semi-newb, so please simplify any direction (give me the full commands to type when dealing with stuff in terminal).


Thanks ):P

---

### Post by chochem on 2008-07-03
I haven't used virtualbox in a while but regarding usb this is what the wikipedia has to say:

> In the "full release" (not in the open-source edition), a USB controller is emulated so that any USB devices attached to the host can be seen in the guest. If VirtualBox acts as an RDP server, it can also use USB devices on the remote RDP client as if they were connected to the host.

EDIT: I believe the one in the repos is the open source, i.e. non-USB, version.

As for local harddisk, I believe you can mount specific directories of the host file system. This should be set somewhere in the properties dialog of the XP image (sorry I can't be more epcific).

---

### Post by cszikszoy on 2008-07-03
Perhaps we could help better if you were a little more specific?  Exactly what problem are you having?  What do the error messages say?  Which guides or wiki's have you followed to get everything set up?

If you open up VB and just do a little bit of exploring through the settings menus I think you'll find that VB does a pretty good job of explaining all of the settings.  For each various setting there is a couple of sentences shown at the bottom of the page to explain that specific setting.

---

### Post by MR.UNOWEN on 2008-07-04
First of all does anyone know how to get to "Devices->Install Guest Additions..." ??? I was reading a tutorial and I don't know where everything is.

Supposedly by doing that, I should be able to access my local file system through XP.

> 
"Perhaps we could help better if you were a little more specific? Exactly what problem are you having? "

My problem is I don't know what to do to get it to work. There's no error screen or anything....  I just don't know what to do...

I followed this...
[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)
(I followed every step) and it didn't work (connected a USB storage device...  nothing happened).

So bottom line is I don't know what the hell I'm doing!

---

### Post by MR.UNOWEN on 2008-07-04
Good news, I solved some of the problem (just had to install the version provide by the website and not the one from package manager)

Problems I'm still having:
- how do increase the resolution to that of my screen? Don't see any setting for that.
- nothing happens when I select "Install Guest Additions"
- how do I "seamlessly integrate"?
-how do I access shared folders????

- still having trouble creating serial port...

Settings
com1    HostDevice     path:/dev/ttys0

Error
   Failed to open host device '/dev/ttys0'.
   VBox status code: -250 (VERR_DEV_IO_ERROR).

---

### Post by cszikszoy on 2008-07-07
That error just means that the serial port at /dev/ttys0 doesn't exist.  Are you using a USB --> serial adapter, or a regular serial port?

Depending on the operating system of the virtual machine, there are guides all over the internet on how to install the vbox guest additions.  Doing this will allow you to access shared folders, seamlessly integrate, and set the screen resolution.

Usually selecting "install guest additions" will just mount the guest additions iso to the guest's cd drive.  If your guest is XP, go to my computer, and open the CD drive.  Like I said there are guides all over on how to do this specifically.

---

### Post by MR.UNOWEN on 2008-07-07
Well I tried all the ttys and none of them work....  (FYI it's a regular serial port.) If you can show me how to get it to work, that'll be great.

I'll go looking around for the vbox guest additions.

BTW when you allow an OS to be a guest, does it have full access to the hardware or is it still limited to the virtual environment that its given?

---

### Post by cszikszoy on 2008-07-08
"Guest" is just the term for the OS.  It's still always in the virtual environment, and does not have any access to the physical hardware, unless you grant it access.  In the settings for virtual box, you will see where you can map the physical hardware on your computer to the virtual hardware on the guest.  The CD drive for example, can be mapped from your machine to the guest, so that the guest has full access to the CD drive.

In your case, you are trying to map the serial port to the guest.

Have you verified that the com port works on the host machine?  If it isn't currently working on the host, then there's no way it's going to work on the guest.

Now, for the serial port... can you post the output of these commands?

```

cat /var/log/dmesg | grep tty

setserial -g /dev/ttyS[01]

cat /proc/tty/drivers

stty -a

ls -la /dev/ttyS0

```

each is a separate command.

---

### Post by MR.UNOWEN on 2008-07-08
Well it turned out something wasn't installed, but now I have another problem. As for testing the port on Linux, I don't have anything that works on Linux to test the port with.

error:
NamedPipe#0 failed to bind to local socket /dev/ttyS0.
VBox status code: -448 (VERR_NET_ADDRESS_IN_USE).

Anyway here's what I get from those commands


1
[  289.576823] console [tty0] enabled
[  291.613411] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  291.613576] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[  291.614374] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  291.614726] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
2
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: 16550A, Port: 0x02f8, IRQ: 3
3
/dev/tty             /dev/tty        5       0 system:/dev/tty
/dev/console         /dev/console    5       1 system:console
/dev/ptmx            /dev/ptmx       5       2 system
/dev/vc/0            /dev/vc/0       4       0 system:vtmaster
rfcomm               /dev/rfcomm   216 0-255 serial
serial               /dev/ttyS       4 64-111 serial
pty_slave            /dev/pts      136 0-1048575 pty:slave
pty_master           /dev/ptm      128 0-1048575 pty:master
pty_slave            /dev/ttyp       3 0-255 pty:slave
pty_master           /dev/pty        2 0-255 pty:master
unknown              /dev/tty        4 1-63 console
4
speed 38400 baud; rows 24; columns 80; line = 0;
intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = M-^?; eol2 = M-^?;
swtch = M-^?; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R; werase = ^W;
lnext = ^V; flush = ^O; min = 1; time = 0;
-parenb -parodd cs8 hupcl -cstopb cread -clocal -crtscts
-ignbrk brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr icrnl ixon -ixoff
-iuclc ixany imaxbel iutf8
opost -olcuc -ocrnl onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
isig icanon iexten echo echoe echok -echonl -noflsh -xcase -tostop -echoprt
echoctl echoke
5
ls -la /dev/ttyS0

BTW how do I get the guest OS to see the physical video card? Can it be done?

---

### Post by bodhi.zazen on 2008-07-08
> **MR.UNOWEN said:**
> BTW how do I get the guest OS to see the physical video card? Can it be done?

This is not yet possible. With virtualization everything is virtual, the videocard, the network card, the CPU ...

---

### Post by p_squared on 2008-07-20
Any luck getting your serial port working?  I am getting the same error as you.

---

### Post by MR.UNOWEN on 2008-07-21
Nope......    -_-.....  at least USB works now. 

I still can't shared folder stuff to work either.

Wonder how long till they develop a way to directly access the graphics card?

---

### Post by IrisBoat on 2008-08-15
New to ubuntu, the first Linux I would like to use (and drop Windows xx as much as possible). I like UBUNTU.

VirtualBox context : 
Host  : Hardy 8.04
Guest : XP SP2

PB is, can't open com ports in VirtualBox : 
===========================================

When I activate com port support the virtual machine doesn't start, I get the msg : Can't start virtual machine xxx

Failed to open host device '/dev/ttys0'.
VBox status code: -250 (VERR_DEV_IO_ERROR).

Result code : 0x80004005
Component   : Console
Interface   : IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}

VirtualBox config options :
Interfaces séries :
Interface série 0 COM1, Périphérique hôte (/dev/ttys0)

Host serial port info :
=======================
The command : ls -l /dev/ttyS0
returns : crw-rw---- 1 root dialout 4, 64 2008-08-15 00:44 /dev/ttyS0

I can get input data in GTKterm from /dev/ttys0

Can somebody help ?

---

### Post by Rhubarb on 2008-08-15
Ok, I've got some semi-good news for you.
I've successfully gotten virtualbox working with my serial port (and usb devices) with xp sp2
The bad news is that it's late, and I can't describe how to do it without messing around for an hour on my other computer.  But it's not too hard to do, and you may figure out how to do it by the time I re-investigate it for myself.  (I'll post here if I find out how I did it).

I initially got it working fine by following some ubuntu virtualbox tutorials (do a google search to find them).

If someone else knows more, please post here.

---

### Post by akelsall on 2008-11-11
In response to Mr. Unknowns' comment "nothing happens when I select "Install Guest Additions"", I noticed that unless you run VirtualBox as superuser, you can't install Guest Additions. To run Vbox as superuser:

         **sudo VirtualBox &**

Here, the word VirtualBox is case-sensitive. The "&" symbol simply puts the process in the brackground, freeing your terminal window so you can still use it.

---

### Post by walfra4 on 2009-02-18
I had the same problem - but the solution was very easy:

Did you really write /dev/ttyS0 ??

The letter "S" must be written as capital-letter!

---

