---
title: "Ubuntu 22.04 in VMWare always logs in with fixed instead of dynamic resolution"
date: 2023-05-15
forum: Virtualisation
---

### Post by galmok on 2023-05-15
After the latest Ubuntu 22.04 updates, my Ubuntu has been acting up. It is running in VMWare on a Windows 10 host.

When I boot it, the graphical login prompt shows up as always, taking the whole screen as it should, but once I log in, the solution is reduced to 800x600 with huge black borders.

I can change the resolution to be higher, but why isn't it using the screen space given by VMWare?

If I in VMWare change the window size, then Ubuntu resizes to use the full space. It seems only to be a problem on login where it wont use the allocated space.

I have tried reinstallen open-vm-tools and open-vm-tools-desktop, but it doesn't fix the issue. Always reduced resolution upon login.

Any suggestion to how I can fix this?

---

### Post by ActionParsnip on 2023-05-15
If you run:
```

xrandr

```
What is the output?

---

### Post by slickymaster on 2023-05-15
*Thread moved to **Virtualisation**.*

---

### Post by galmok on 2023-05-16
> **ActionParsnip said:**
> If you run:
```

xrandr

```
What is the output?

This is the output of xrandr right after I log in without having VMWare resize the client display size. The resolution is one I selected on a previous login as 800x600 was way too small.

```
Screen 0: minimum 1 x 1, current 1280 x 800, maximum 8192 x 8192
Virtual1 connected primary 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1920x1080     60.00 +  59.96  
   3840x2400     59.97  
   3840x2160     59.97  
   2880x1800     59.95  
   2560x1600     59.99  
   2560x1440     59.95  
   1920x1440     60.00  
   1856x1392     60.00  
   1792x1344     60.00  
   1920x1200     59.88  
   1600x1200     60.00  
   1680x1050     59.95  
   1400x1050     59.98  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1360x768      60.02  
   1280x800      59.81* 
   1152x864      75.00  
   1280x768      59.87  
   1280x720      59.86  
   1024x768      60.00  
   800x600       60.32  
   640x480       59.94  
Virtual2 disconnected (normal left inverted right x axis y axis)
Virtual3 disconnected (normal left inverted right x axis y axis)
Virtual4 disconnected (normal left inverted right x axis y axis)
Virtual5 disconnected (normal left inverted right x axis y axis)
Virtual6 disconnected (normal left inverted right x axis y axis)
Virtual7 disconnected (normal left inverted right x axis y axis)
Virtual8 disconnected (normal left inverted right x axis y axis)
```

This is the output from xrandr efter I resized the VMWare client window:

```
Screen 0: minimum 1 x 1, current 1920 x 1080, maximum 8192 x 8192
Virtual1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1920x1080     60.00*+  59.96  
   3840x2400     59.97  
   3840x2160     59.97  
   2880x1800     59.95  
   2560x1600     59.99  
   2560x1440     59.95  
   1920x1440     60.00  
   1856x1392     60.00  
   1792x1344     60.00  
   1920x1200     59.88  
   1600x1200     60.00  
   1680x1050     59.95  
   1400x1050     59.98  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1360x768      60.02  
   1280x800      59.81  
   1152x864      75.00  
   1280x768      59.87  
   1280x720      59.86  
   1024x768      60.00  
   800x600       60.32  
   640x480       59.94  
Virtual2 disconnected (normal left inverted right x axis y axis)
Virtual3 disconnected (normal left inverted right x axis y axis)
Virtual4 disconnected (normal left inverted right x axis y axis)
Virtual5 disconnected (normal left inverted right x axis y axis)
Virtual6 disconnected (normal left inverted right x axis y axis)
Virtual7 disconnected (normal left inverted right x axis y axis)
Virtual8 disconnected (normal left inverted right x axis y axis)
```

This is basically the same output exception the resolution change is reflected.

---

### Post by ActionParsnip on 2023-05-16
If you run:
```

xrandr --output Virtual1 --mode [FONT=inherit]"1920x1080_59.96"

```
Does it adjust the display for you?[/FONT]

---

### Post by MAFoElffen on 2023-05-16
Wait please...

In the VMware Community for VMware Workstation 16 & 17 / Player... It you do not configure the Monitor Settings for your guest, for a Linux VM, the default startup resolution (legacy setting) is 800x600, as you described.

In the VMware Workstation--

Step 1: Open VMware Workstation Player and select the virtual machine name where you have installed the Ubuntu Operating system. After that, click on &#8220;Edit virtual machine settings&#8220;.

Step 2: It will open the virtual machine hardware settings window. Here, click on &#8220;Display&#8221; and select the &#8220;Use host settings for monitors&#8221; option under the &#8220;Monitor&#8221; settings option. Now, to save the changes, click on &#8220;OK&#8220;. After that, run your virtual machine to see the changes.

Step 3: If you are still facing the same screen size problem, you can specify the monitor resolution for the virtual machine. To do so, click on &#8220;Display&#8221; and select the &#8220;Specify monitor settings&#8221; option under the &#8220;Monitor&#8221; settings. Select the desired resolution from the drop-down menu and click &#8220;OK&#8221; to save the changes.

After that, run your virtual machine to see the changes. These should fix the VMware screen size issue. If you are still facing the same problem, ***then*** you can try to change the display resolution from the Ubuntu settings.

What I suggest first, if you are trying to set a Linux VM to boot in a certain resolution, is to set the resolution i Grub, and use KMS via kernel boot parameters... That way it is in that mode, when it starts the Grub menu, and Graphical Login screen.

If you do it by a setting any other way (via user settings), then it will not change resolutions until after the login (remember VMware's default resolution without configuration is 800x600) 

So edit with previledge, file /etc/default/grub
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="-- quiet splash [COLOR=#ff0000]video=uvesafb:1280 x 800-24@60,mtrr:3,ywrap,noblank[/COLOR]"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
[COLOR=#ff0000]GRUB_GFXMODE=1280 x 800x24[/COLOR]

```
After making the changes, saving and exiting... Then run
```

sudo update-grub

```
To update the changes...

If still not, then the VMware Workstation player passes on psuedo video EDID information to an Ubuntu Guest, and you will find your resolutions populated, where you can choose what resolution you want it to be (after login).

---

### Post by galmok on 2023-05-17
Thank you for the very elaborate answer. I will try out each and every suggestion.

But first I want to point out the very first thing I wrote: "After the latest Ubuntu 22.04 updates"

My point is that the resolution adaption upon login was working just fine until I made the latest Ubuntu 22.04 updates. To me, this indicates something stopped working due to the latest Ubuntu updates.


Regarding the suggestion about VMWare monitor setting: VMWare Workstation is already set to use host setting for monitors (was always like that).

Also, Ubuntu remembers the resolution I switch to (e.g. 1280x800) from login to login, but as soon as I make VMWare change "monitor size" (resize window for VM), Ubuntu catches that and adapts correctly to the changed windows size. It is only upon login where Ubuntu now fails to adapt to the VMWare resolution.

I tried checking all log files in /var/log (all log files updated since boot) but none say anything about the resolution choice/change. I think my user profile may be the one having overridden the initial resolution.

---

### Post by galmok on 2023-05-17
> **ActionParsnip said:**
> If you run:
```

xrandr --output Virtual1 --mode [FONT=inherit]"1920x1080_59.96"
[/FONT]
```[FONT=inherit]
Does it adjust the display for you?[/FONT]

It does not. It claims to not know about the resolution.

```

ser@vmbmedevcw:~$ xrandr --output Virtual1 --mode "1920x1080_59.96"
xrandr: cannot find mode 1920x1080_59.96
user@vmbmedevcw:~$ sudo xrandr --output Virtual1 --mode "1920x1080_59.96"
[sudo] password for user: 
xrandr: cannot find mode 1920x1080_59.96
user@vmbmedevcw:~$ xrandr --output Virtual1 --mode "1920x1080_60"
xrandr: cannot find mode 1920x1080_60
user@vmbmedevcw:~$ xrandr --output Virtual1 --mode "1920x1080_60.00"
xrandr: cannot find mode 1920x1080_60.00
user@vmbmedevcw:~$ sudo xrandr --output Virtual1 --mode "1920x1080_60.00"
xrandr: cannot find mode 1920x1080_60.00
user@vmbmedevcw:~$ sudo xrandr --output Virtual1 --mode "1920x1080_60"
xrandr: cannot find mode 1920x1080_60

```

---

### Post by galmok on 2023-05-17
I found this file in the users home directory:

/home/user/.config/monitors.xml

And it contained this information:

```

<monitors version="2">
  <configuration>
    <logicalmonitor>
      <x>0</x>
      <y>0</y>
      <scale>1</scale>
      <primary>yes</primary>
      <monitor>
        <monitorspec>
          <connector>Virtual1</connector>
          <vendor>unknown</vendor>
          <product>unknown</product>
          <serial>unknown</serial>
        </monitorspec>
        <mode>
          <width>1280</width>
          <height>800</height>
          <rate>59.810325622558594</rate>
        </mode>
      </monitor>
    </logicalmonitor>
  </configuration>
</monitors>

```

I deleted the file (with backup) and now I get the correct resolution upon login again. :)

I know I didn't manually change the resolution, but I may have changed some other settings and maybe the monitor.xml file got written by the Settings app when it shouldn't have been?

---

