---
title: "disable X startup after installing ubuntu-desktop"
date: 2010-01-02
forum: Server Platforms
---

### Post by dtech on 2010-01-02
Hi,

I've just installed the ubuntu server system on an old PC i'm going to be using as, you guessed it, a server. Because I like (some) graphical tools while configuring I also installed ubuntu-desktop on it afterwards.

The only problem is that I want to keep ubuntu-desktop, but that I don't want to boot into the (memory consuming) graphical interface by default.

Does anyone know how to do that? (set the default boot to command-prompt). Also, does anyone have tips on packages I can safely remove to clear up space and memory? (Like: openoffice, Evolution,Rhythmbox etc. are very obvious, but maybe some more hidden services and alike? Networkmanager e.g.?)

---

### Post by c9-3Rr0r on 2010-01-02
I don't have access to ubuintu box atm 
But u should change startx or gdm(i don't remember atm)
in /etc/init.d/rC(smth) look for bootup section

---

### Post by dtech on 2010-01-02
Hmm. I changed /etc/rcS.D/S70x11-common to /etc/rcS.D/KS70x11-common and ran the command (with rcS instead of scripts) as the README said. However, I'm still booting into graphical mode. Anyone else got an idea?

---

### Post by reidbold on 2010-01-02
Not as easy as debian, which only requires editing /etc/inittab. 

This looks like it might be useful to look at:[http://ubuntuforums.org/showthread.php?t=843646]("http://ubuntuforums.org/showthread.php?t=843646")

---

### Post by geekshlby on 2010-01-02
man update-rc.d

sudo update-rc.d -f gdm remove

The above will remove the GDM symlinks in the various runlevel init directories e.g. /etc/rc0.d, rcS.d, rc2.d.

kdm, xdm, same usage to remove from the various run

---

### Post by squaregoldfish on 2010-01-03
Since Karmic, gdm doesn't use the rc.d system for starting up.

This is what I did to get a text-only boot sequence:

Edit the file /etc/init/gdm.conf (you need sudo for this):

Near the top of the file, you'll find a line that reads:

```
stop on runlevel [016]
```

Change this to 

```
stop on runlevel [0216]
```

This will prevent gdm from starting up.

If you want to start gdm after you've booted, simply type:

```
sudo service gdm start
```

and to shut down gdm and X

```
sudo service gdm stop
```

Alternatively, you could just start X when you've logged in:

```
startx
```

HTH
Steve.

---

### Post by haddog on 2010-04-03
> **squaregoldfish said:**
> Since Karmic, gdm doesn't use the rc.d system for starting up.

This is what I did to get a text-only boot sequence:

Edit the file /etc/init/gdm.conf (you need sudo for this):

Near the top of the file, you'll find a line that reads:

```
stop on runlevel [016]
```

Change this to 

```
stop on runlevel [0216]
```

This will prevent gdm from starting up.

If you want to start gdm after you've booted, simply type:

```
sudo service gdm start
```

and to shut down gdm and X

```
sudo service gdm stop
```

Alternatively, you could just start X when you've logged in:

```
startx
```

HTH
Steve.

I am using Ubuntu Server Lucid Lynx 10.04 Beta1. After the initial server install, I used apt-get and installed xubuntu-desktop so I would have a windows manager if I needed one. 

I tried ```
stop on runlevel [0**2**16]
``` but when I reboot the server, I have to hit esc to to get rid of the xubuntu splash screen and the server never gets to the command prompt. It stops at " *Checking battery state... " and there is a flashing cursor below that statement.

I am able to ssh into the server and edit the gdm.conf file and chage it to the default value. BTW I did look for a xdm.conf file and there is only a gdm.conf.

Any thoughts as to why the server is not booting to the command prompt completely?

---

### Post by haddog on 2010-04-03
> **haddog said:**
> I am using Ubuntu Server Lucid Lynx 10.04 Beta1. After the initial server install, I used apt-get and installed xubuntu-desktop so I would have a windows manager if I needed one. 

I tried ```
stop on runlevel [0**2**16]
``` but when I reboot the server, I have to hit esc to to get rid of the xubuntu splash screen and the server never gets to the command prompt. It stops at " *Checking battery state... " and there is a flashing cursor below that statement.

I am able to ssh into the server and edit the gdm.conf file and chage it to the default value. BTW I did look for a xdm.conf file and there is only a gdm.conf.

Any thoughts as to why the server is not booting to the command prompt completely?

I wimped out and wiped the drive. Was installing debian 5.0.4 but during the install i got an error, had a nasty scratch on the cd. So I just reinstalled Ubuntu Server 10.04 Beta 1. I'll leave the gui alone this time! I promise...

---

### Post by twin-08 on 2010-04-03
This would help you alot, worked for me great using ubuntu server 9.10

> **cdenley said:**
> 
```

sudo apt-get remove ubuntu-desktop
sudo apt-get autoremove

```


> **cdenley said:**
> I think on 9.10 (and probably 10.04), you can edit /etc/init/gdm.conf to prevent GDM, your graphical login manager, from loading at boot.
```

# gdm - GNOME Display Manager
#
# The display manager service manages the X servers running on the
# system, providing login and auto-login services

description     "GNOME Display Manager"
author          "William Jon McCann <mccann@jhu.edu>"

[B][COLOR="Red"]#[/COLOR]start on (filesystem
[COLOR="red"]#[/COLOR]          and started hal
[COLOR="red"]#[/COLOR]          and tty-device-added KERNEL=tty7
[COLOR="red"]#[/COLOR]          and (graphics-device-added or stopped udevtrigger))[/B]
stop on runlevel [016]

emits starting-dm

env XORGCONFIG=/etc/X11/xorg.conf

script
    [ ! -f /etc/X11/default-display-manager -o "$(cat /etc/X11/default-display-manager 2>/dev/null)" = "/usr/sbin/gdm" ] || { stop; exit 0; }

    # Check kernel command-line for inhibitors
    for ARG in $(cat /proc/cmdline)
    do
        case "${ARG}" in
            text|-s|s|S|single)
                exit 0
                ;;
        esac
    done

    if [ -r /etc/default/locale ]; then
        . /etc/default/locale
        export LANG LANGUAGE
    elif [ -r /etc/environment ]; then
        . /etc/environment
        export LANG LANGUAGE
    fi
    export XORGCONFIG

    initctl emit starting-dm DM=gdm

    exec gdm-binary $CONFIG_FILE
end script

```
Then, if that works, when your system boots, you will get a login terminal. If you login, you get a shell. If you need a graphical desktop, start gdm with:
```

sudo service gdm start

```

---

### Post by chaanakya_chiraag on 2010-04-03
```
sudo update-rc.d x11-common remove
``` should do the trick!

---

### Post by macey on 2010-04-14
> **haddog said:**
> I wimped out and wiped the drive. Was installing debian 5.0.4 but during the install i got an error, had a nasty scratch on the cd. So I just reinstalled Ubuntu Server 10.04 Beta 1. I'll leave the gui alone this time! I promise...


Did you try cntl-atl F1 or F2 etc to logon to a another terminal?

---

### Post by atanu1 on 2010-06-13
> **haddog said:**
> I am using Ubuntu Server Lucid Lynx 10.04 Beta1. After the initial server install, I used apt-get and installed xubuntu-desktop so I would have a windows manager if I needed one. 

I tried ```
stop on runlevel [0**2**16]
``` but when I reboot the server, I have to hit esc to to get rid of the xubuntu splash screen and the server never gets to the command prompt. It stops at &quot; *Checking battery state... &quot; and there is a flashing cursor below that statement.

I am able to ssh into the server and edit the gdm.conf file and chage it to the default value. BTW I did look for a xdm.conf file and there is only a gdm.conf.

Any thoughts as to why the server is not booting to the command prompt completely?

You might try to switch to an alternate vterminal using ALT-F<n>...

---

### Post by LoREZ on 2010-06-15
Is there a way to enter a virtual terminal in a VirtualBox VM, so I can stop gdm?  When I try, it just executes the cntrl+alt+backspace/F1/etc... for my host.

---

