---
title: "Can't ssh into a server after a power outage and a &quot;broken pipe&quot; error"
date: 2019-08-23
forum: Server Platforms
---

### Post by carolog on 2019-08-23
I installed Ubuntu server on an APU2 machine and everything worked great until we had a power outage in our area and my client (Mac terminal) showed a 'broken pipe' error. After the server came back online, I tried SSH'ing to it, but now I constantly get timeouts. Also all ping requests to the server seem are timing out. How do I fix this? I can see the Ethernet port lights blinking randomly where the cable is connected. Also this machine does not have a video output. Hence I cannot connect it to a display to try and troubleshoot it. Any help would be appreciated. Thank you.

---

### Post by Irihapeti on 2019-08-23
I have an APU1, also running Ubuntu Server 18.04.

If the ssh server hasn't come back after a reboot, I think that you'll almost certainly going to need to access it via the serial port. If you still have the install medium (USB stick or whatever), you may be able to access it that way.

Before going into further detail, I'd like to check: I'm assuming you installed it via the serial port, or did you use some other method?

---

### Post by carolog on 2019-08-23
Oh I see! Yes, I installed it via the serial port of another desktop that I have. I do have the installation USB drive which is essentially a TinyCore boot drive with the ubuntu netboot files on it.

---

### Post by TheFu on 2019-08-23
I have an APU2. I use a $7 USB-2-serial cable to access the console from a laptop. Mine doesn't run Linux. It is the WAN router here.

Did the APU2 have a static IP or was it configured for DHCP?  Could the IP have changed?  I'd run an nmap scan on the subnet to find the new IP, if so, then I'd ssh in and set a static IP.

Were all the devices on a UPS?  Power spikes can fry computers or just parts of computers.  I never used the TinyCore install method, though that is what the PCEngines instructions say. Seemed like the long way to drop an OS onto the storage.

---

### Post by carolog on 2019-08-24
So the APU2 did not have a static IP. It is getting one from the router it is connected to. All devices were on a router so not sure if a power cycle did fry something. The problem is that one every power cycle I can't seem to ssh into the device. How did you configure ubuntu to output its console screen to the serial port? I found the SerialConsoleHowTo on the Ubuntu site but that did not work.

---

### Post by TheFu on 2019-08-24
> **carolog said:**
> So the APU2 did not have a static IP. It is getting one from the router it is connected to. All devices were on a router so not sure if a power cycle did fry something. The problem is that one every power cycle I can't seem to ssh into the device. How did you configure ubuntu to output its console screen to the serial port? I found the SerialConsoleHowTo on the Ubuntu site but that did not work.

My APU2 doesn't run Linux. Also, I think the settings are in the APU2 documentation, so check that.  It has been a few years since I needed it.  Getting the settings in minicom right and it "just works."

Since yours isn't the router, why not just configure the router to give it a static IP using DHCP reservations?

---

### Post by Irihapeti on 2019-08-24
To output Linux over the serial console, you need to configure Grub by editing /etc/default/grub and then run update-grub.

This is a copy of my /etc/default/grub file. I've highlighted the important lines in red:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
[COLOR="#B22222"]GRUB_CMDLINE_LINUX="gfxpayload=text fb=false console=ttyS0,115200n8"[/COLOR]


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
[COLOR="#B22222"]GRUB_TERMINAL="serial"           
GRUB_SERIAL_COMMAND="serial --speed=115200 --unit=0 --word=8 --parity=no --stop=1"[/COLOR]

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

```
Don't forget to run 

```
sudo update-grub
```
before rebooting. I've forgotten a few times, and then wondered why it didn't work.

---

### Post by Skaperen on 2019-08-25
because the router rebooted, all the IPs it previously gave out are no longer valid.  just reboot it.

---

### Post by carolog on 2019-08-25
> **TheFu said:**
> My APU2 doesn't run Linux. Also, I think the settings are in the APU2 documentation, so check that.  It has been a few years since I needed it.  Getting the settings in minicom right and it "just works."

Since yours isn't the router, why not just configure the router to give it a static IP using DHCP reservations?

Yeah that was way too confusing for me. I followed the guide by @[COLOR=#000000]Irihapeti and that worked like a charm![/COLOR]

---

### Post by carolog on 2019-08-25
> **Irihapeti said:**
> To output Linux over the serial console, you need to configure Grub by editing /etc/default/grub and then run update-grub.

This is a copy of my /etc/default/grub file. I've highlighted the important lines in red:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
[COLOR=#B22222]GRUB_CMDLINE_LINUX="gfxpayload=text fb=false console=ttyS0,115200n8"[/COLOR]


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
[COLOR=#B22222]GRUB_TERMINAL="serial"           
GRUB_SERIAL_COMMAND="serial --speed=115200 --unit=0 --word=8 --parity=no --stop=1"[/COLOR]

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

```
Don't forget to run 

```
sudo update-grub
```
before rebooting. I've forgotten a few times, and then wondered why it didn't work.
Thank you!! This worked like a charm. I have now given the APU2 a static IP but I was still not able to figure out why I could not SSH into it. I simply reinstalled Ubuntu 18.04. However, I know this is not the solution but if it happens again, at least I'll have console access to debug...

---

### Post by carolog on 2019-08-25
> **Skaperen said:**
> because the router rebooted, all the IPs it previously gave out are no longer valid.  just reboot it.
That did not work and I tried all unknown IPs that my router showed. I guess something went wrong with the SSH service, just not sure how and where it went wrong.

---

### Post by TheFu on 2019-08-25
1st, you must know 3 things:
[LIST=1]
[*]the IP address for the remote device
[*]the username that is allowed ssh access
[*]the password for that username
[/LIST]

After you know the IP, you can check some initial things about the connection using **ssh -vvv userid@serverIP**
[https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections) has more things to try.

---

### Post by carolog on 2019-08-26
> **TheFu said:**
> I have an APU2. I use a $7 USB-2-serial cable to access the console from a laptop. Mine doesn't run Linux. It is the WAN router here.

Did the APU2 have a static IP or was it configured for DHCP? Could the IP have changed? I'd run an nmap scan on the subnet to find the new IP, if so, then I'd ssh in and set a static IP.

Were all the devices on a UPS? Power spikes can fry computers or just parts of computers. I never used the TinyCore install method, though that is what the PCEngines instructions say. Seemed like the long way to drop an OS onto the storage.
Would you know how to configure the USB-to-Serial cable in grub? I have a mac and that shows the port as /dev/tty.usbserial. However, grub takes serial port numbers in the form of --unit.

---

### Post by Irihapeti on 2019-08-26
The ports at each end of the cable don't have to have the same names. On my system, it's /dev/ttyUSB0 at the Ubuntu desktop end and /dev/ttyS0 on the APU1. I would try setting up the terminal program on the mac to the same settings (115200 no parity 8bit, 1 stop bit) and see what happens. Unlike with an ethernet connection, there's nowhere else for the signal to go except to the device at the other end.

---

