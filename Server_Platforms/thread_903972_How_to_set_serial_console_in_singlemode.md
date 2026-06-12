---
title: "How to set serial console in singlemode?"
date: 2008-08-28
forum: Server Platforms
---

### Post by 2smooth on 2008-08-28
Hi,

I'm running Hardy and i want to configure my system for use of IPMI 2.0 Serial over Lan.

I want configure Text Console Redirection in singel user mode, so that in case of serious problems i can remotely logging with IPMI view.

This is what the manual amongst other things says:

```

 c) LINUX OS: 
   (i) Add the following line into /etc/inittab. 
       s0:2345:respawn:/sbin/agetty ttyS1 19200 
  (ii) Edit /etc/securetty and add ttyS1

```


Searching through the forums i understand that ubuntu doesnt use inittab anymore but upstart. And that i have to to look in /etc/event.d

So i guess that i have to modify rc0.

```

# rc1 - runlevel 1 compatibility
#
# This task runs the old sysv-rc runlevel 1 ("single-user") scripts.

start on runlevel 1

stop on runlevel [!1]

console output
script
        set $(runlevel --set 1 || true)
        if [ "$1" != "unknown" ]; then
            PREVLEVEL=$1
            RUNLEVEL=$2
            export PREVLEVEL RUNLEVEL
        fi

        exec /etc/init.d/rc 1
end script

```


But what should i change?

---

### Post by 2smooth on 2008-08-29
after doing some more research i found this article:

[Setting up a serial console]("http://www.howtoforge.com/setting_up_a_serial_console")

In the comment section someone else added this:

> 
...cut..
3.  On Ubuntu Edgy Eft (6.10) or later, Upstart is used instead of init.  To configure ttyS0, create a new entry in /etc/event.d by copying one of the existing tty# entries and modifying it.  Example ttyS0:

------------------------------------------------------
# ttyS0 - getty
#
# This service maintains a getty on ttyS0 from the point the system is
# started

start on runlevel-2
start on runlevel-3
start on runlevel-4
start on runlevel-5
.......

Go to article to read further.

With this knowledge a find out that in single user mode
This script is being run
```
/usr/share/recovery-mode/recovery-menu
```

Which displays a menu

After selecting menu item "root"

This script is being run:
```
/usr/share/recovery-mode/options/root
```

So i thougt this would do the trick

change this line
```
/sbin/sulogin
```

to this line

```
/sbin/sulogin /dev/ttyS1
```

And add ttyS1 to the file /etc/securetty

But unfortunately not.

First the menu after running grub is still being displayed on the console attached to the server.
Second there is some prompt showing on my IPMIview virtual terminal, but i cannot loggin?

Help please?

---

### Post by promodus on 2008-08-31
This help?
[https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)

As for IPMI serial over LAN that should be independent from the OS.

---

### Post by 2smooth on 2008-09-02
> **promodus said:**
> This help?
[https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)

As for IPMI serial over LAN that should be independent from the OS.

Thanks, but it doesn's explain howto do this in single user mode.

Or let me phrase my question differently:

How can i login via sulogin on the ttyS1?

> **promodus said:**
> This help?
As for IPMI serial over LAN that should be independent from the OS.
My ipmi card doesnt have a KVM but redirects the output of the serial port through the lan. So if you want to see you promt, you have to configure your system to use the serial port.

---

### Post by 2smooth on 2008-09-02
Yeah!!!!!!!!!! It finally works :popcorn:
I can now access my server in both single and multy user mode

**First read the serial console howto**

For others who want to the same in Hardy, 

**To get a console on the serial line/ipmi SOL in multy user mode**

Add this to the file ttyS0 or ttyS1 (depending on which serial port you are going to use)

```

# ttyS1 - getty
#
# This service maintains a getty on ttyS1 from the point the system is
# started until it is shut down again.

start on stopped rc2
start on stopped rc3
start on stopped rc4
start on stopped rc5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
exec /sbin/getty 115200 ttyS1

```

if you want to login as root also add your terminal to the file /etc/securetty

**for single user/maintenance mode do the following**

edit this file in /boot/grub/menu.lst

find this section:
title           Ubuntu 8.04.1, kernel 2.6.24-19-server (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.24-19-server root=/dev/mapper/lvm--group-lv--root ro single
initrd          /initrd.img-2.6.24-19-server

and change this line

kernel          /vmlinuz-2.6.24-19-server root=/dev/mapper/lvm--group-lv--root ro single 

to

kernel          /vmlinuz-2.6.24-19-server root=/dev/mapper/lvm--group-lv--root ro single serial console=ttyS1,115200n8


edit the file /usr/share/recovery-mode/options/root

and change this line:
/sbin/sulogin
to
/sbin/sulogin /dev/ttyS1

That's it

---

