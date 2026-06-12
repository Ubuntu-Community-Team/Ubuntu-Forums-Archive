---
title: "Booting without full network configuration then no GUI?"
date: 2013-06-26
forum: System76 Support
---

### Post by kajari on 2013-06-26
I'm not sure exactly what the issue is here so I'll go in chronological order:

Yesterday I tried connecting my laptop (PANP9, recently upgraded to 13.04 and running smoothly for about a month with no problems) to the ethernet in my office. Unfortunately what I didn't realise was that about a month ago IT removed the cable elsewhere and I was no longer connected. I thought it was an issue I'd had with the upgrade, not the ethernet port in the office. I don't think I immediately installed the System76 drivers after the upgrade (or I installed the drivers but didn't do restore settings). The ethernet has now been fixed now. However, I took the laptop home last night and connected it to an ethernet cable to check if that was the issue or not, and booted into ubuntu. Then this happened, and keeps recurring:


[LIST=1]
[*]In the ubuntu loading screen (purple with orange dots) it would first say "[FONT=courier new]Waiting for network configuration[/FONT]" then "[FONT=courier new]Waiting up to 60s more for network configuration...[/FONT]"
[*]It then says "[FONT=courier new]Loading system without full network configuration[/FONT]" and goes to a black screen with terminal-like settings. It says "[FONT=courier new]Ubuntu 13.04 Pangolin tty1[/FONT]" and then "[FONT=courier new]Pangolin login:[/FONT]" with a waiting cursor. I can login but I'm still in tty (black screen terminal?). Even though I'm *connected to the ethernet*.
[/LIST]

[LIST]
[*]When I try [FONT=courier new]sudo apt-get update [/FONT]I get errors like [FONT=courier new]W: Failed to fetch [http://bla](http://bla).. Something wicked happened resolving 'au.archive.ubuntu.com: http' (-11 - System error)[/FONT] and finally [FONT=courier new]E: Some index files failed to download. They have been ignored, or old ones used instead.[/FONT]
[*]I tried booting from liveUSB but after choosing "try first without installing" it goes straight to a blank screen and no response.
[*][FONT=courier new]ifconfig [/FONT]only shows lo, not eth1 or wlan0
[/LIST]

I'm used to the command line but I don't know how to paste output from my laptop to here while its in this state..
Please help me restore my laptop! :(

---

### Post by isantop on 2013-06-26
Once you're logged in to the terminal, try running this command:

sudo restart lightdm

This will reset the display manager and should let you log in to the desktop. Once you're there, you can try connecting from there.

---

### Post by kajari on 2013-06-26
It says:

Restart: unknown instance

Also: if I press ctrl+alt+f1 during the loading screen I just get a black screen without response, same as when I try loading from a liveusb.

---

### Post by isantop on 2013-06-27
I think a reinstallation would be the best thing at this point. If lightdm can't start in addition to your network troubles, then that indicates multiple low-level system configuration problems.

---

### Post by steeldriver on 2013-06-27
I don't really understand what you did, but regardless if the system is able to boot to a console (virtual terminal) then it should be repairable. First, instead of sudo restart lightdm, try

```
sudo service lightdm start
```

after logging in at the console. If it works then we can try to diagnose your networking issues from the GUI. Otherwise post back with any errors it produces and we will need to figure stuff out from the console.

---

### Post by kajari on 2013-06-27
> **steeldriver said:**
> ```
sudo service lightdm start
```

That seemed to work and gave the following output:
```
lightdm start/running, process 1495
``` 
but then it went to the blank screen just like when I tried to boot from liveusb and when pressing Ctrl+Alt+F1 during the loading screen. :( If I press Ctrl+Alt+F1 again then I go back to the virtual terminal. 

Thanks for the help so far, I really appreciate it.

---

### Post by KlipperKyle on 2013-06-27
> **kajari said:**
> In the ubuntu loading screen (purple with orange dots) it would first say "[FONT=courier new]Waiting for network configuration[/FONT]" then "[FONT=courier new]Waiting up to 60s more for network configuration...[/FONT]"

It is unusual for system startup to wait for a network connection. Are you using static IPs?

> **kajari said:**
> That seemed to work and gave the following output:
```
lightdm start/running, process 1495
``` 
but then it went to the blank screen just like when I tried to boot from liveusb and when pressing Ctrl+Alt+F1 during the loading screen. :( If I press Ctrl+Alt+F1 again then I go back to the virtual terminal.

Sounds like a problem with lightdm. You could try starting X11 directly from tty1. (I am not 100% certain whether this works with Ubuntu's desktop environment, but it is certainly worth a shot.) Log in to tty1 and run:

```
startx
```

This should take you to a graphical environment.

---

### Post by kajari on 2013-06-28
> **KlipperKyle said:**
> It is unusual for system startup to wait for a network connection. Are you using static IPs?
I'm not sure.. how can I find out?

> **KlipperKyle said:**
> ```
startx
```

This should take you to a graphical environment.

After 10 seconds of waiting it did bring my desktop! However no menus.. I got a system error message straight away but when I went to report it nothing else appeared. I opened up a terminal and got another error: 
```
initctl: Unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
```
There is nothing in that directory when I use "ls" but with "ls -la" I get a root and messagebus directory that seemed to be created when I logged in (judging from time).

---

### Post by steeldriver on 2013-06-28
Yeah personally I've never had any luck using startx with the Ubuntu desktop - I don't know if it's supposed to work or not

I agree with KlipperKyle - it's unusual for the Desktop version to wait for your network connection at boot - let's see if there's a competing interface def in /etc/network:

```
cat /etc/network/interfaces
```

---

### Post by kajari on 2013-06-28
I get:
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopbacks
```

---

### Post by steeldriver on 2013-06-28
Looks like a typo there - it should be 

```

auto lo
iface lo inet [COLOR=#0000ff]**loopback**[/COLOR]

```

(no 's')

---

### Post by kajari on 2013-06-28
That was amazing. It got rid of the network configuration message, brought back the login screen and connected straight away to my wireless. I am speechless. 
Thank you. *bow*

I still got a Network Manager stopped working error but its downloading updates now.. hopefully I'll be OK from here.

---

### Post by steeldriver on 2013-06-28
Glad we figured it out - post back (or start a new thread) if you are still having issues with NetworkManager after the updates

---

### Post by kajari on 2013-06-28
OK will do if something comes up. I've restarted a few times however, and it all seems in order.

Thanks again everyone. :)

---

### Post by KlipperKyle on 2013-06-28
It appears that Ubuntu is not configured to use startx. After poking around, I found this file (/usr/share/xsessions/ubuntu.desktop). ubuntu.desktop is what lightdm looks at when you log in.

```

[Desktop Entry]
Name=Ubuntu
Comment=This session logs you into Ubuntu
Exec=gnome-session --session=ubuntu
TryExec=unity
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-3.0

```

This is from Ubuntu 12.10, by the way.

So, let's try to configure startx. From a tty session:

```

cd
cat > .xinitrc
exec unity
^D

```

(That last line is just you pressing Ctl+D. Don't type out "^D". Ctl+D means "end of file".)

This will create a .xinitrc file, which startx runs when you call it. (Please check if you already have a .xinitrc before you do this.)

Now, run startx. I successfully launched a unity session on my 12.10 box this way. (Not everything worked correctly, but it is much better than being stuck in a tty.)

---

### Post by kajari on 2013-06-29
Should I still do this if everything is working ok now? There was a typo in my /etc/network/interfaces file which fixed both my GUI and the network issues..

---

### Post by KlipperKyle on 2013-06-29
> **kajari said:**
> Should I still do this if everything is working ok now? There was a typo in my /etc/network/interfaces file which fixed both my GUI and the network issues..

No, you don't have to. I was merely trying to help you get into the GUI to make things easier. However, I stupidly missed the second page of the thread. <:-) (It's been a long day!)

I'm glad you figured out the problem. I thought there was something fishy with the network.

---

### Post by kajari on 2013-06-29
No worries. Thanks for all your help in any case! ;)

---

