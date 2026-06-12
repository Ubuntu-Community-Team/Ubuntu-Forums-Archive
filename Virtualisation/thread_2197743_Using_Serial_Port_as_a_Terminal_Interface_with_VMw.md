---
title: "Using Serial Port as a Terminal Interface with VMware"
date: 2014-01-05
forum: Virtualisation
---

### Post by wkmoritz on 2014-01-05
The givens:
Ubuntu 12.10 as a VMware machine
Host is Windows 8.1
Terminal Program is Putty as a Serial Terminal in Windows 8.1

Process:
Ubuntu VMware machine: hardware is Serial Port 2 using \\.\pipe\com_1
Windows 8.1, Putty is set to Serial line \\.\pipe\com_1 Speed 115200

Terminal in Ubuntu:
billm@ubuntu:~$ echo hello > /dev/ttys1
bash: /dev/ttys1: Permission denied
(of course, nothing shows on the putty terminal window at Windows 8.1)

Can you help me?
What can I do to prove out that Ubuntu can talk serially to putty?
Too complex for a newbie?

Thank you, kindly.

---

### Post by tomearp on 2014-01-05
You need to add your user to the dialout group to give it permission to access that device:

Assuming your username is billm, in a terminal:
```
sudo addgroup billm dialout
```

Reboot, or at least fully log out and back in, and you should be able to access the device.

---

### Post by wkmoritz on 2014-01-05
After logging out:
   
  billm@ubuntu:~$ echo hello > /dev/ttys1
  bash: /dev/ttys1: Permission denied
  billm@ubuntu:~$ echo hello > /dev/ttys0
  billm@ubuntu:~$
 
The last command looked like ‘hello’ went somewhere but it did not appear in the putty terminal.
 
Any more ideas?
Thank you for your help thus far.

---

### Post by wkmoritz on 2014-01-06
As I read in another google search results:
Question: Can you please clarify your question a bit, its not clear what you are trying to achieve. If you want to connect to the Ubuntu VM running on the host, did you try sshing through putty?

Yes I have done SSH with network IP connection and it work without error...but
 
In preparations for a pcDuino v2 and its debug serial port, I want to have a version of Ubuntu in a VMware machine so I can test software results, such as this, and roll back to an earlier ‘snapshot’ if my actions are totally convoluted, confused and I am lost.   Simple enough?
 
I’ll trying time and time again to use what should be a terminal login via putty but with Ubuntu/ Linux no one knows how to connect
 (VMware, Ubuntu, Serial Port 2 as \\. \pipe\com_1) to a (windows host of putty set to \\. \pipe\com_1 and 115200 baud).  That port is ttys1 as I proved it with /etc/default/grub with GRUB_CMDLINE_LINUX="console=tty1 console=ttyS1,115200n8". 
However putty would not accept any key inputs to send to (VMware, Ubuntu, Serial Port 2 as \\. \pipe\com_1).  

Maybe this is too complex for a newbie with Linux?!?!
:lolflag: 
Thank you in any case.

---

### Post by tomearp on 2014-01-06
I have managed to echo messages into the serial port of a Ubuntu VM and see it in PuTTY on my Windows 7 host. Below are the steps I followed:

Create a Ubuntu VM. If you are using VMware Workstation a nifty little trick I use is to maintain a "blank" Ubuntu VM that I occasionally boot up in order to install updates and then take a snapshot but otherwise don't use. Then you can use the clone feature (right click on the blank VM in the Library view > Manage > Clone) to quickly make linked clones from snapshots that can be used to test something and then be thrown away (right click on VM in Library view > Manage > Delete from Disk).

Add a serial port to the VM.
Right-click VM in Library > Settings.
In the hardware tab click Add. Click Serial Port. Click Next.
Click Output to named pipe. Click Next.
Give it a name: I used \\.\pipe\pipe1
Choose "This end is the server"
Choose "The other end is a virtual machine"
Tick Connect at power on.
Click Finish. There is now an entry called Serial Port 2.
Click OK to leave Settings.

Power on the VM.

Start a PuTTY session, select Serial, enter the pipe name and leave the speed at 9600. Click Open. Hit return once in the PuTTY window.

Now in a terminal in the VM:
```
tom@tom-virtual-machine:~$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[    3.099663] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.160006] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    3.499342] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.523328] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
tom@tom-virtual-machine:~$

```

So the options are /dev/ttyS0 and /dev/ttyS1.
Since this is effectively a fresh install my user is not in the dialout group so, as expected:
```
tom@tom-virtual-machine:~$ echo moo > /dev/ttyS0
bash: /dev/ttyS0: Permission denied
tom@tom-virtual-machine:~$ echo moo > /dev/ttyS1
bash: /dev/ttyS1: Permission denied
tom@tom-virtual-machine:~$
```

Now add the user to the dialout group:
```
tom@tom-virtual-machine:~$ sudo addgroup tom dialout
Adding user `tom' to group `dialout' ...
Adding user tom to group dialout
Done.
tom@tom-virtual-machine:~$
```

Reboot the VM.

Open a terminal:
```
tom@tom-virtual-machine:~$ echo this is ttyS0 > /dev/ttyS0
tom@tom-virtual-machine:~$ echo this is ttyS1 > /dev/ttyS1
tom@tom-virtual-machine:~$
```

No error messages this time, and the PuTTY window shows the result:
[IMG]http://i.imgur.com/kjab4fW.png[/IMG]

---

### Post by wkmoritz on 2014-01-06
tomearp thanks.

Now I have ttys1 sending to putty but no terminal mode login
I did the grub deal with Edit /etc/default/grub and
GRUB_CMDLINE_LINUX="console=tty1 console=ttyS1,9600n8"

Ubuntu boots and sends text to putty but I cannot use putty for a serial \\:D/login.

How do I get to a serial login with ubuntu and putty?
Anyone know?

---

### Post by wkmoritz on 2014-01-06
I found the missing procedure here [http://2stech.ca/index.php/linux/linuxtutotials/tutorials/207-ubuntu-serial-console-login](http://2stech.ca/index.php/linux/linuxtutotials/tutorials/207-ubuntu-serial-console-login)

***Here's what works***
[CENTER][SIZE=4]**How to make a Serial Login in VMware Ubuntu and Putty**[/SIZE]
[/CENTER]
 
Which I boiled down to this):P
 
The givens:
Ubuntu 12.10 as a VMware machine
Host is Windows 8.1
Terminal Program is Putty as a Serial Terminal in Windows 8.1

Process:
Ubuntu VMware machine: hardware is Serial Port 2 using \\.\pipe\com_1
Windows 8.1, Putty is set to Serial line \\.\pipe\com_1 Speed 115200


  [CENTER][CENTER]**How to make a Serial Login in VMware Ubuntu and Putty**[/CENTER][/CENTER]  
Which I boiled down to this

The givens:
Ubuntu 12.10 as a VMware machine
Host is Windows 8.1
Terminal Program is Putty as a Serial Terminal in Windows 8.1

Process:
Ubuntu VMware machine: hardware is Serial Port 2 using \\.\pipe\com_1
Windows 8.1, Putty is set to Serial line \\.\pipe\com_1 Speed 115200


**billm@ubuntu:~$ sudo cp /etc/init/tty1.conf /etc/init/ttyS1.conf** [B]

billm@ubuntu:~$ sudo gedit /etc/init/ttyS1.conf[/B] 

# ttyS1 - getty
#
# This service maintains a getty on ttyS1 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345] and (
not-container or
container CONTAINER=lxc or
container CONTAINER=lxc-libvirt)

stop on runlevel [!2345]

respawn
exec /sbin/getty -L 115200 ttyS1 vt102

[B]billm@ubuntu:~$ sudo start ttyS1

billm@ubuntu:~$ sudo gedit /etc/default/grub

[/B]# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
# info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX="console=tty1 console=ttyS1,115200n8"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xe fefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console
GRUB_TERMINAL=serial
GRUB_SERIAL_COMMAND="serial --speed=115200 --unit=0 --word=8 --parity=no --stop=1"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"[B]


billm@ubuntu:~$ sudo update-grub[/B]

    [B][FONT=&quot](restart)

phew!!! What an ordeal...[/FONT][/B]

---

