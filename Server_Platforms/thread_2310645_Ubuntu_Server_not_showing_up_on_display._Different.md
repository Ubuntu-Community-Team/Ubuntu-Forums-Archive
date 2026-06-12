---
title: "Ubuntu Server not showing up on display. Different resolution or frequency?"
date: 2016-01-21
forum: Server Platforms
---

### Post by Jacob_Peterson on 2016-01-21
Hello,

I am new to ubuntu and I just installed ubuntu server 14.04.3 LTS (32-bit) on a Dell Poweredge 2650 (a fairly old server that I got for cheap). The installation process was perfect and flawless. Then, after installing and configuring the server to boot from the hard drive and then restarting the server, the server completes POST and then as soon as it boots into the OS my LCD monitor has small text on it saying, "Not Optimum Resolution - Recommended settings: 1920x1080@60Hz". I have tried different monitors, but no luck. I am using a VGA connection because that is the only connection type my server takes. I also cannot access it from my mac via ssh because I keep getting a permissions denied whenever I try to connect. I have looked everywhere on google and also had no luck.

Any help is greatly appreciated!
Thanks.

---

### Post by bab1 on 2016-01-21
> **Jacob_Peterson said:**
> Hello,

I am new to ubuntu and I just installed ubuntu server 14.04.3 LTS (32-bit) on a Dell Poweredge 2650 (a fairly old server that I got for cheap). The installation process was perfect and flawless. Then, after installing and configuring the server to boot from the hard drive and then restarting the server, the server completes POST and then as soon as it boots into the OS my LCD monitor has small text on it saying, "Not Optimum Resolution - Recommended settings: 1920x1080@60Hz". I have tried different monitors, but no luck. I am using a VGA connection because that is the only connection type my server takes. I also cannot access it from my mac via ssh because I keep getting a permissions denied whenever I try to connect. I have looked everywhere on google and also had no luck.

Any help is greatly appreciated!
Thanks.
Modern digital monitors provide their specs and setup parameters when the host is booted up.  This info is used by X-server to configure the video output.  You can configure it manually if you have the experience.  It is confusing and obscure at best.  Does the monitor have a DVI connection?  If so, do you have the ability to add a video card that supports a DVI output?

The default SSH install on the server should allow you to access the server from another host?  Did you configure something with SSH.

---

### Post by Jacob_Peterson on 2016-01-21
The Dell Poweredge 2650 does not have any DVI ports and I do not have a compatible video card either. How can I set the parameters when the server is booting?

And no, I have not configured SSH other than installing it during the ubuntu server installation.

Thanks!

---

### Post by slickymaster on 2016-01-21
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by bab1 on 2016-01-21
> **Jacob_Peterson said:**
> The Dell Poweredge 2650 does not have any DVI ports and I do not have a compatible video card either. How can I set the parameters when the server is booting?

Without the card you are left with configuring the resolution manually.  Here is a [**Google search**]("https://www.google.com/search?client=ubuntu&channel=fs&q=configure+x-server+maunually+ubuntu+14.04&ie=utf-8&oe=utf-8#channel=fs&nfpr=1&q=configure+x-server+manually+ubuntu+14.04+xrandr") of the terms: configure x-server manually ubuntu 14.04 xrandr.  The last term (xrander) is the Ubuntu tool.   The first listing is the Ubuntu Wiki page re:[** X/Config/Resolution**]("https://wiki.ubuntu.com/X/Config/Resolution").

The problem you are tackling is not trivial.  I for one was glad to move to a better video card.
> 

And no, I have not configured SSH other than installing it during the Ubuntu server installation.
Then you should be able to SSH to the server from a SSH client. What is the exact error message? What is the ssh command (i.e. ssh user@hostname).  Is the username the same on both hosts?

---

### Post by Jacob_Peterson on 2016-01-22
I cannot use any commands without SSH or a display to see the interface.

Here is the ssh command that I used and its output (I am connecting to it on the same network as my mac)   

```
Kellys-iMac:~ Jacob$ ssh -v jacob@10.0.1.255
OpenSSH_5.9p1, OpenSSL 0.9.8za 5 Jun 2014
debug1: Reading configuration data /etc/ssh_config
debug1: /etc/ssh_config line 20: Applying options for *
debug1: Connecting to 10.0.1.255 [10.0.1.255] port 22.
debug1: connect to address 10.0.1.255 port 22: Permission denied
ssh: connect to host 10.0.1.255 port 22: Permission denied
```

---

### Post by bab1 on 2016-01-22
> **Jacob_Peterson said:**
> I cannot use any commands without SSH or a display to see the interface.

Here is the ssh command that I used and its output (I am connecting to it on the same network as my mac)   

```
Kellys-iMac:~ Jacob$ ssh -v jacob@10.0.1.255
OpenSSH_5.9p1, OpenSSL 0.9.8za 5 Jun 2014
debug1: Reading configuration data /etc/ssh_config
debug1: /etc/ssh_config line 20: Applying options for *
debug1: Connecting to 10.0.1.255 [10.0.1.255] port 22.
debug1: connect to address 10.0.1.255 port 22: Permission denied
ssh: connect to host 10.0.1.255 port 22: Permission denied
```

What is the subnet mask for this network?   If this is a 24 bit (/24) network then the address is the broadcast address and should not be assigned to any host on the network.  Are you sure of the IP address for the Ubuntu host?

---

### Post by MAFoElffen on 2016-01-22
> **Jacob_Peterson said:**
> ...
Then, after installing and configuring the server to boot from the hard drive and then restarting the server, the server completes POST and then as soon as it boots into the OS my LCD monitor has small text on it saying, "Not Optimum Resolution - Recommended settings: 1920x1080@60Hz". I have tried different monitors, but no luck. I am using a VGA connection because that is the only connection type my server takes. I also cannot access it from my mac via ssh because I keep getting a permissions denied whenever I try to connect. I have looked everywhere on google and also had no luck.

I've posted this solution in this section multiple times, but I'm happy to post it again. Maybe a few more times might be found by search engines better. :rolleyes:

Here goes:

Boot. As the BIOS messages finish, starting pressing the left <Shift> key...

At the Grub Menu, press <E> to edit.

<ArrowDown> to the line that starts with "linux".

Go to the end of that line. Delete "quiet splash" and replace with "text"

Press <Cntrl><X>

It will boot into a text mode so you can work with it and make repairs. Log in with your credentials.
```

sudo vim /etc/default/grub

```
Press <Insert> and <ArrowDown> to the line that says
```

GRUB_CMDLINE_LINUX=""

```
Edit is so that it looks similar to this:
```

GRUB_CMDLINE_LINUX="nomodeset video=VGA:1024x768-16@60m"

```
Note: Adjust those setting to what you want your VGA virtual tty sessions to be in.

Press <Escape><:><w><q>

That will save and exit.
```

sudo update-grub

```
Will pick up those changes to grub2.
```

sudo shutdown -r now

```
Will reboot

What that will do will put the video into a statically set mode. From Grub, to kernel, to tell the system to use that mode. What is will is, while the kernel is booting, since is already set to a mode, it will not probe your GPU and Monitor to search for a mode to try. This is what it is doing currently, and it isn't playing well with that probe. 

For more reference and details on what that all means (and other fixes), please go my "Graphics Resolution" sticky linked in my sigline. To others, there also how to use Server VGA color palates, linked from the second post there... Hope this continues to help people.

---

### Post by ds_cdtech on 2016-02-16
> **Jacob_Peterson said:**
> Hello,

I am new to ubuntu and I just installed ubuntu server 14.04.3 LTS (32-bit) on a Dell Poweredge 2650 (a fairly old server that I got for cheap). The installation process was perfect and flawless. Then, after installing and configuring the server to boot from the hard drive and then restarting the server, the server completes POST and then as soon as it boots into the OS my LCD monitor has small text on it saying, "Not Optimum Resolution - Recommended settings: 1920x1080@60Hz". I have tried different monitors, but no luck. I am using a VGA connection because that is the only connection type my server takes. I also cannot access it from my mac via ssh because I keep getting a permissions denied whenever I try to connect. I have looked everywhere on google and also had no luck.

Any help is greatly appreciated!
Thanks.

I was having the same issues installing 12.04, but was able to get it working with a LiveCD.  Tried using MAFoElffen's suggestions from the "Re: Ubuntu Server not showing up on display. Different resolution or frequency?" set of posts.  Because of the multiple hardware raid and scsi controller startups, could not get into the grub menu.  Using the install/livecd was able to get into a 'repair a broken system' command/shell prompt--eventually (not quite sure if remembering it correctly).

The initial trials using the install CD and updating the Grub did not seem to do a darn thing.  Still could not boot into the grub menu.  Then, using the install CD, did the broken system entry on the install menu, getting to a command prompt, and then did:

> The root partition is mounted read-only. To mount it read/write, enter the command

mount -o remount,rw /
If you have /home, /boot, /tmp, or any other mount point on a separate partition, you can mount them with the command

mount --all

from the [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode) Wiki, before trying to make the changes you want to the /etc/default/grub file.  After changes done, and partitions mounted per the mount -all above, then you can do the:

```
sudo update-grub
```

If I remember correctly, remounting "/ as rw" had no effect by itself.  It was the addition of the "mount -all" that changed things.  After that, the grub update ran without errors (I was getting errors before that point, but did not know what they meant).  It generated a grub menu (which did not happen before that point).  After rebooting, I think it went straight into the grub menu, not quite sure, I was pretty pumped that finally got a different result.

I am doing this with the server version (12.04, not 14.04), not trying to do anything with the gui.  Now trying to get ssh working to work on this system from my windows systems through putty.

Hope this helps.

Edit: I also was installing on a PowerEdge 2650 as a server (v12.04), experiencing the same symptoms that Jacob_Peterson describes in his opening post.  Although, I did not have SSH setup--just wanted to get to the command prompt, or grub, or something.  Finally got it working using the information above.

---

### Post by MAFoElffen on 2016-02-16
Depends what the GPU is... <-- Means each situation has to do with what the hardware is and what the error is.

For most older server hardware, they used a Radeon Rage Graphics chip. If so, then adding "radeon.modeset=0" helps. On most PC's in general, just adding "nomodeset" helps... But tried and true-- If you just say "text", it will put it into a straight text mode, to boot and be able to test to see what it going on and to be able to chek what hardware you do have.

All those boot option are added without the quotation marks.

For more details and workarounds, please refer to my Graphics Resolution Sticky in the link in my signature line

---

