---
title: "Console screen shows at starting up + how to remove a driver"
date: 2012-08-11
forum: System76 Support
---

### Post by Maien on 2012-08-11
Hi, I got my Lemu4 two days ago (Ubuntu 12.04). But now when I start the laptop, I get the console screen mode. I can't get into the desktop. I asked the folks at System76, I got a reply to type: sudo apt-get update and sudo apt-get upgrade, then reboot. I did this but I still get the console mode on start up. I tried typing Ctrl+Alt+F7, but this took me nowhere. 

Now I remember I configured my wireless HP photosmart printer as a network printer. Ubuntu found the driver automatically. But I'm thinking now maybe this caused the problem!? So, my question is how to remove the driver or de-configure the printer from that console mode?

Also, if anyone has any suggestions, please let me know while I wait for System76 to reply to me.

---

### Post by Carborundum on 2012-08-12
I have occasionally seen this on my Gazelle Professional. I haven't been able to figure out what causes it, but I have found a solid workaround: 'sudo restart lightdm'. See if it works for you.

---

### Post by Maien on 2012-08-12
Thank you Carborundum! 

This managed to get me to the password screen that gets me to the desktop. But unfortunately it didn't fix the issue since when I restart the laptop I get the console screen again. But at least now I know how to get in. I hope System76 technical support will help me fix it.

Many thanks,

---

### Post by Carborundum on 2012-08-12
Since this seems to be a bug in LightDM, a more permanent workaround would be to install GDM instead.

Run 'sudo apt-get install gdm'. After the installation completes, you will automatically be prompted to choose which display manager you wish to use. To switch between LightDM and GDM, run 'sudo dpkg-reconfigure lightdm'.

This will make the login-screen look a bit different, so it's not a perfect solution.

---

### Post by isantop on 2012-08-13
> **Carborundum said:**
> Since this seems to be a bug in LightDM, a more permanent workaround would be to install GDM instead.

Run 'sudo apt-get install gdm'. After the installation completes, you will automatically be prompted to choose which display manager you wish to use. To switch between LightDM and GDM, run 'sudo dpkg-reconfigure lightdm'.

This will make the login-screen look a bit different, so it's not a perfect solution.

On the contrary, we'd recommend against installing GDM as we don't do any testing or support. Any issues it causes will be difficult to purge from the system.

We have determined that this issue is being caused by a race condition in the lightdm startup script.

---

### Post by Carborundum on 2012-08-14
> **isantop said:**
> On the contrary, we'd recommend against installing GDM as we don't do any testing or support. Any issues it causes will be difficult to purge from the system.
Well, it s*hould *be as simple as
```
sudo dpkg-reconfigure lightdm
sudo apt-get purge gdm
sudo apt-get autoremove
```

> We have determined that this issue is being caused by a race condition in the lightdm startup script.
Interesting. Is there a Launchpad bug I can subscribe to?

---

### Post by isantop on 2012-08-14
> **Carborundum said:**
> Well, it s*hould *be as simple as
```
sudo dpkg-reconfigure lightdm
sudo apt-get purge gdm
sudo apt-get autoremove
```


Interesting. Is there a Launchpad bug I can subscribe to?

I want to hold off until we know specifically what causes the problem. So far, we haven't been able to replicate the bug in the shop.

By the way, for anyone here experiencing this bug, it would be very useful to know what hardware configuration you ordered. This will allow us to track this and find the common hardware. Once we have that, we can replicate the issue here and begin solving it/ file bugs, etc.

---

### Post by Carborundum on 2012-08-14
It happens on my GazP7 (order ID 23192) sometimes. It is far from common though, and thus not easy to reproduce.

---

### Post by MoebusNet on 2012-08-14
Hmmm, I got the console-at-bootup scenario this morning. I was able to log in using my username and password, then used 'startx' to attempt to get to a graphical desktop. After a bunch of hard drive thrashing, everything stopped at:

```

Log file: /var/log/Xorg.0.log

System configuration directory: /usr/share/X11/xorg.conf.d 17:03:23 UTC

```

which is where everything hung. I used Ctrl-Alt-SysRq REISUB to reboot and things are back to normal.

I should have taken a photo of the screen, I suppose.

Serp7: Intel Core i7-2860QM w/ 7.8Gb RAM, GeForce/560M PCIe/SSE2, 491 Gb hybrid HDD, Ubuntu 11.10 upgraded to 12.04

---

### Post by MoebusNet on 2012-08-14
Perhaps the output of these commands would be useful:

```
nano .xsession-errors

(gnome-settings-daemon:2003): color-plugin-WARNING **: failed to get edid: unable to get EDID for output
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done

(gnome-settings-daemon:2003): color-plugin-WARNING **: unable to get EDID for xrandr-default: unable to get EDID for output

(gnome-settings-daemon:2003): color-plugin-WARNING **: failed to reset xrandr-default gamma tables: gamma size is zero
gnome-session[1943]: WARNING: Application 'compiz.desktop' failed to register before timeout
gnome-session[1943]: CRITICAL: We failed, but the fail whale is dead. Sorry....
gnome-session[1943]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1" (No such file or directory)
** Message: Initializing gksu extension...
** Message: applet now removed from the notification area
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)
** Message: using fallback from indicator to GtkStatusIcon
New PolkitAgentListener  0x1423ea0
Adding new listener  PolkitQt1::Agent::Listener(0x7fffbd6a8cf0) for  0x1423ea0
"sni-qt/2033" WARN  07:26:56.202 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE
No systemtrayicon available
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or direc$
Please ask your system administrator to enable user sharing.

Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing move options...done
Initializing vpswitch options...done
Initializing mousepoll options...done
Initializing snap options...done
Initializing wall options...done
Initializing place options...done
Initializing resize options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
I/O warning : failed to load external entity "/home/glenn/.compiz/session/10a436fafda6cf330a134495438476178000000019430037"
Initializing session options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Initializing workarounds options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done

(compiz:2012): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
Initializing staticswitcher options...done
Setting Update "main_menu_key"



glenn@glenn-Serval-Professional:~$ cat /var/log/Xorg.0.log | grep -e EE -e WW
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    13.509] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    13.509] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    13.509] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    13.509] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    13.509] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    13.510] (II) Loading extension MIT-SCREEN-SAVER
[    13.517] (WW) Warning, couldn't open module nv
[    13.517] (EE) Failed to load module "nv" (module does not exist, 0)
[    13.518] (WW) Warning, couldn't open module nv
[    13.518] (EE) Failed to load module "nv" (module does not exist, 0)
[    13.519] (WW) Falling back to old probe method for vesa
[    13.519] (WW) Falling back to old probe method for fbdev
[    14.765] (WW) NVIDIA(0): The EDID for LEN (DFP-0) contradicts itself: mode "1920x1080"
[    14.765] (WW) NVIDIA(0):     is specified in the EDID; however, the EDID's valid
[    14.765] (WW) NVIDIA(0):     HorizSync range (56.502-67.804 kHz) would exclude this
[    14.765] (WW) NVIDIA(0):     mode's HorizSync (45.2 kHz); ignoring HorizSync check for
[    14.765] (WW) NVIDIA(0):     mode "1920x1080".
[    14.765] (WW) NVIDIA(0): The EDID for LEN (DFP-0) contradicts itself: mode "1920x1080"
[    14.765] (WW) NVIDIA(0):     is specified in the EDID; however, the EDID's valid
[    14.765] (WW) NVIDIA(0):     HorizSync range (56.502-67.804 kHz) would exclude this
[    14.765] (WW) NVIDIA(0):     mode's HorizSync (45.2 kHz); ignoring HorizSync check for
[    14.765] (WW) NVIDIA(0):     mode "1920x1080".

```

---

### Post by isantop on 2012-08-14
> **MoebusNet said:**
> Perhaps the output of these commands would be useful:

```
nano .xsession-errors

(gnome-settings-daemon:2003): color-plugin-WARNING **: failed to get edid: unable to get EDID for output
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done

(gnome-settings-daemon:2003): color-plugin-WARNING **: unable to get EDID for xrandr-default: unable to get EDID for output

(gnome-settings-daemon:2003): color-plugin-WARNING **: failed to reset xrandr-default gamma tables: gamma size is zero
gnome-session[1943]: WARNING: Application 'compiz.desktop' failed to register before timeout
gnome-session[1943]: CRITICAL: We failed, but the fail whale is dead. Sorry....
gnome-session[1943]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1" (No such file or directory)
** Message: Initializing gksu extension...
** Message: applet now removed from the notification area
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)
** Message: using fallback from indicator to GtkStatusIcon
New PolkitAgentListener  0x1423ea0
Adding new listener  PolkitQt1::Agent::Listener(0x7fffbd6a8cf0) for  0x1423ea0
"sni-qt/2033" WARN  07:26:56.202 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE
No systemtrayicon available
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or direc$
Please ask your system administrator to enable user sharing.

Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing move options...done
Initializing vpswitch options...done
Initializing mousepoll options...done
Initializing snap options...done
Initializing wall options...done
Initializing place options...done
Initializing resize options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
I/O warning : failed to load external entity "/home/glenn/.compiz/session/10a436fafda6cf330a134495438476178000000019430037"
Initializing session options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Initializing workarounds options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done

(compiz:2012): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
Initializing staticswitcher options...done
Setting Update "main_menu_key"



glenn@glenn-Serval-Professional:~$ cat /var/log/Xorg.0.log | grep -e EE -e WW
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    13.509] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    13.509] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    13.509] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    13.509] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    13.509] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    13.510] (II) Loading extension MIT-SCREEN-SAVER
[    13.517] (WW) Warning, couldn't open module nv
[    13.517] (EE) Failed to load module "nv" (module does not exist, 0)
[    13.518] (WW) Warning, couldn't open module nv
[    13.518] (EE) Failed to load module "nv" (module does not exist, 0)
[    13.519] (WW) Falling back to old probe method for vesa
[    13.519] (WW) Falling back to old probe method for fbdev
[    14.765] (WW) NVIDIA(0): The EDID for LEN (DFP-0) contradicts itself: mode "1920x1080"
[    14.765] (WW) NVIDIA(0):     is specified in the EDID; however, the EDID's valid
[    14.765] (WW) NVIDIA(0):     HorizSync range (56.502-67.804 kHz) would exclude this
[    14.765] (WW) NVIDIA(0):     mode's HorizSync (45.2 kHz); ignoring HorizSync check for
[    14.765] (WW) NVIDIA(0):     mode "1920x1080".
[    14.765] (WW) NVIDIA(0): The EDID for LEN (DFP-0) contradicts itself: mode "1920x1080"
[    14.765] (WW) NVIDIA(0):     is specified in the EDID; however, the EDID's valid
[    14.765] (WW) NVIDIA(0):     HorizSync range (56.502-67.804 kHz) would exclude this
[    14.765] (WW) NVIDIA(0):     mode's HorizSync (45.2 kHz); ignoring HorizSync check for
[    14.765] (WW) NVIDIA(0):     mode "1920x1080".

```

I think you're seeing a different problem. This one is simply lightdm not starting up. The system is still responsicve.

---

### Post by MoebusNet on 2012-08-15
@isantop

Thank you. I guess I'll just try:

```
 sudo restart lightdm 
```

if/when it happens again.

---

### Post by jefty on 2012-08-16
> **isantop said:**
> I want to hold off until we know specifically what causes the problem. So far, we haven't been able to replicate the bug in the shop.

By the way, for anyone here experiencing this bug, it would be very useful to know what hardware configuration you ordered. This will allow us to track this and find the common hardware. Once we have that, we can replicate the issue here and begin solving it/ file bugs, etc.

I think I've been seeing this as well. Sometimes it hangs indefinitely on a blank screen (with moveable mouse cursor). Sometimes it goes to a console login. A hard reboot usually fixes, but it sometimes needs more than one.

Brand new (arrived yesterday) Lemur Ultra, 
 i7-3610QM Processor,
8G Ram
500 GB 7200rpm SATA Hybrid Hard Drive with 4 GB SSD
 Advanced-N 6235 Wireless
Everything else default.

I haven't had the chance to do much debugging on it. I did do a system update and switched to a xubuntu desktop. Other than that I was rebooting a lot trying to get my wireless access point set up properly.

---

