---
title: "Lightdm will not start"
date: 2014-08-30
forum: Ubuntu Development Version
---

### Post by P-I H on 2014-08-30
I don't know if this is related to the thread **"After the last update i get a black screen"**


In my case grub is started OK, but I don't get to the login screen.  
In syslog I get the following about lightdm:

```
Aug 30 23:03:39 pi-GA-990FXA-UD3-1310 systemd[1]: Starting Light Display Manager...
Aug 30 23:03:39 pi-GA-990FXA-UD3-1310 irqbalance[1203]: * Starting SMP IRQ Balancer: irqbalance
Aug 30 23:03:39 pi-GA-990FXA-UD3-1310 dns-clean[1197]: ...done.
Aug 30 23:03:39 pi-GA-990FXA-UD3-1310 apport[1210]: ...done.
Aug 30 23:03:39 pi-GA-990FXA-UD3-1310 systemd[1]: Started LSB: Cleans up any mess left by 0dns-up.
Aug 30 23:03:39 pi-GA-990FXA-UD3-1310 systemd[1]: Started LSB: Start the PulseAudio sound server.
Aug 30 23:03:39 pi-GA-990FXA-UD3-1310 systemd[1]: Started LSB: automatic crash report generation.
Aug 30 23:03:39 pi-GA-990FXA-UD3-1310 irqbalance[1203]: ...done.
Aug 30 23:03:39 pi-GA-990FXA-UD3-1310 systemd[1]: Started LSB: daemon to balance interrupts for SMP systems.
Aug 30 23:03:39 pi-GA-990FXA-UD3-1310 systemd[1]: Started LSB: Tool to automatically collect and submit kernel crash signatures.
Aug 30 23:03:39 pi-GA-990FXA-UD3-1310 systemd[1]: Started Light Display Manager.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Started LSB: start Samba daemons for the AD DC.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 winbind[1199]: * Starting the Winbind daemon winbind
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 nmbd[1202]: * Starting NetBIOS name server nmbd
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 nmbd[1202]: ...done.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Started LSB: start Samba NetBIOS nameserver (nmbd).
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Starting LSB: start Samba SMB/CIFS daemon (smbd)...
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 winbind[1199]: ...done.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Started LSB: start Winbind daemon.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Received SIGRTMIN+21 from PID 296 (plymouthd).
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Started Wait for Plymouth Boot Screen to Quit.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 lightdm[1284]: ** (lightdm:1284): CRITICAL **: x_server_local_get_authority_file_path: assertion 'server != NULL' failed
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 lightdm[1284]: ** (lightdm:1284): CRITICAL **: x_server_get_address: assertion 'server != NULL' failed
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Starting Getty on tty1...
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Started Getty on tty1.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Starting Login Prompts.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Reached target Login Prompts.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 lightdm[1284]: /etc/modprobe.d is not a file
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 smbd[1328]: * Starting SMB/CIFS daemon smbd
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 smbd[1328]: ...done.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Started LSB: start Samba SMB/CIFS daemon (smbd).
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Starting Multi-User System.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Reached target Multi-User System.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Starting Graphical Interface.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Reached target Graphical Interface.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Starting Update UTMP about System Runlevel Changes...
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Started Update UTMP about System Runlevel Changes.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Startup finished in 4.435s (kernel) + 4.776s (userspace) = 9.211s.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 avahi-daemon[627]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::52e5:49ff:fe3e:753a.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 avahi-daemon[627]: New relevant interface eth0.IPv6 for mDNS.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 avahi-daemon[627]: Registering new address record for fe80::52e5:49ff:fe3e:753a on eth0.*.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 sh[646]: [23:03:40] online
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 lightdm[1284]: message repeated 3 times: [ /etc/modprobe.d is not a file]
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 lightdm[1284]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: lightdm.service: main process exited, code=exited, status=1/FAILURE
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Unit lightdm.service entered failed state.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: lightdm.service holdoff time over, scheduling restart.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Cannot add dependency job for unit systemd-vconsole-setup.service, ignoring: Unit systemd-vconsole-setup.service failed to load: No such file or directory.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Stopping Light Display Manager...
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Starting Light Display Manager...
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Started Light Display Manager.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 lightdm[1386]: ** (lightdm:1386): CRITICAL **: x_server_local_get_authority_file_path: assertion 'server != NULL' failed
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 lightdm[1386]: ** (lightdm:1386): CRITICAL **: x_server_get_address: assertion 'server != NULL' failed
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 lightdm[1386]: /etc/modprobe.d is not a file
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 lightdm[1386]: message repeated 3 times: [ /etc/modprobe.d is not a file]
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 lightdm[1386]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: lightdm.service: main process exited, code=exited, status=1/FAILURE
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Unit lightdm.service entered failed state.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: lightdm.service holdoff time over, scheduling restart.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Cannot add dependency job for unit systemd-vconsole-setup.service, ignoring: Unit systemd-vconsole-setup.service failed to load: No such file or directory.
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Stopping Light Display Manager...
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Starting Light Display Manager...
Aug 30 23:03:40 pi-GA-990FXA-UD3-1310 systemd[1]: Started Light Display Manager.
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 lightdm[1435]: ** (lightdm:1435): CRITICAL **: x_server_local_get_authority_file_path: assertion 'server != NULL' failed
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 lightdm[1435]: ** (lightdm:1435): CRITICAL **: x_server_get_address: assertion 'server != NULL' failed
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 lightdm[1435]: /etc/modprobe.d is not a file
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 lightdm[1435]: message repeated 3 times: [ /etc/modprobe.d is not a file]
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 lightdm[1435]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: lightdm.service: main process exited, code=exited, status=1/FAILURE
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: Unit lightdm.service entered failed state.
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: lightdm.service holdoff time over, scheduling restart.
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: Cannot add dependency job for unit systemd-vconsole-setup.service, ignoring: Unit systemd-vconsole-setup.service failed to load: No such file or directory.
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: Stopping Light Display Manager...
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: Starting Light Display Manager...
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: Started Light Display Manager.
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 lightdm[1484]: ** (lightdm:1484): CRITICAL **: x_server_local_get_authority_file_path: assertion 'server != NULL' failed
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 lightdm[1484]: ** (lightdm:1484): CRITICAL **: x_server_get_address: assertion 'server != NULL' failed
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 lightdm[1484]: /etc/modprobe.d is not a file
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 lightdm[1484]: message repeated 3 times: [ /etc/modprobe.d is not a file]
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 lightdm[1484]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: lightdm.service: main process exited, code=exited, status=1/FAILURE
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: Unit lightdm.service entered failed state.
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: lightdm.service holdoff time over, scheduling restart.
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: Cannot add dependency job for unit systemd-vconsole-setup.service, ignoring: Unit systemd-vconsole-setup.service failed to load: No such file or directory.
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: Stopping Light Display Manager...
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: Starting Light Display Manager...
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 sh[646]: [23:03:41] online
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: Started Light Display Manager.
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 lightdm[1533]: ** (lightdm:1533): CRITICAL **: x_server_local_get_authority_file_path: assertion 'server != NULL' failed
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 lightdm[1533]: ** (lightdm:1533): CRITICAL **: x_server_get_address: assertion 'server != NULL' failed
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 lightdm[1533]: /etc/modprobe.d is not a file
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 lightdm[1533]: message repeated 3 times: [ /etc/modprobe.d is not a file]
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 lightdm[1533]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: lightdm.service: main process exited, code=exited, status=1/FAILURE
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: Unit lightdm.service entered failed state.
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: lightdm.service holdoff time over, scheduling restart.
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: Cannot add dependency job for unit systemd-vconsole-setup.service, ignoring: Unit systemd-vconsole-setup.service failed to load: No such file or directory.
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: Stopping Light Display Manager...
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: Starting Light Display Manager...
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: lightdm.service start request repeated too quickly, refusing to start.
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: Failed to start Light Display Manager.
Aug 30 23:03:41 pi-GA-990FXA-UD3-1310 systemd[1]: Unit lightdm.service entered failed state.
Aug 30 21:03:46 pi-GA-990FXA-UD3-1310 systemd[1]: Time has been changed
Aug 30 21:03:46 pi-GA-990FXA-UD3-1310 ntpdate[1190]: step time server 91.189.89.199 offset -7199.954588 sec

```

---

### Post by Bashing-om on 2014-08-30
P-I H; Hello;

Hard for me to say, but I would suggest to get these out of the way as possibilities.
Let's see if we can get to a terminal:
At the grub boot menu with the latest kernel highlighted press the 'e' key for edit mode -> boot parameters screen,
arrow down and across to the terms "quiet splash" and replace them with the term "text" - with out the quotes,
key combo ctl+x to continue the boot process to the terminal login ( TTY 1). Can you log in here with user name and password ( no response to the screen when pass word is entered).

As we have:
1)
> 
(lightdm:1284): CRITICAL **: x_server_local_get_authority_file_path: assertion 'server != NULL' failed

So let's see that you have the authority to access the GUI:
```

ls -al /home/<your_user_name>/.Xauthority
ls -al /home/<your_user_name>/.ICEauthority

```

2) > 
 update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf

no graphics driver loaded ? Let's look !
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```

Samba ?
> 
Cannot add dependency job for unit systemd-vconsole-setup.service, ignoring: Unit systemd-vconsole-setup.service failed to load: No such file or directory

Remove Samba ? See what results ??

4) I ain't got a clue !
> 
lightdm[1484]: message repeated 3 times: [ /etc/modprobe.d is not a file]

Does the directory exist, and if so what is telling what, that this directory is a file ???
```

ls -al /etc/modprobe.d

```

Good places to start,
[INDENT][INDENT][INDENT]let's see what we find out
[/INDENT][/INDENT][/INDENT]

---

### Post by P-I H on 2014-08-31
The installation of the system was made as Ubuntu 13.10. It's upgraded to Ubuntu 14.04 and then changed to Ubuntu 14.10, I think in May.
Now the boot ends with some lines shown on the screen. The last three are:
            ```
Starting Light Display Manager ....
[OK]     Started LSB: daemon to balance interrupts from SMP system
[OK]     Started LSB: Tool to automatically collect and submi...ash signatures.
```The login screen never shows up.

I can start a terminal and login with Ctrl+Alt+F1. However the keybord is not the correct one.
```
ls -al /home/<your_user_name>/.Xauthority
```gives
```
-rw------- 1 user user 313 "date" /home/user/.Xauthority
```
```
ls -al /home/<your_user_name>/.ICEauthority
```gives
```
-rw------- 1 user user 239422 "date" /home/user/.ICEauthority
```

```
spci -nnk | grep -iA3 vga
sudo lshw -C display
```both tells that the graphic card is a Geforce GTX 660. The 2:nd command gives some more details.

I don't think Samba is related to the problem.

```
[COLOR=#000000]*lightdm[1484]: message repeated 3 times: [ /etc/modprobe.d is not a file]*[/COLOR]
```/etc/modeprobe.d is a directory that contains config information.
Most files are since 2012 and 2013. The newest are modesettings.conf from May 2014 and fbdev-blacklist.conf from April 2014.

---

### Post by Bashing-om on 2014-08-31
P-I H; Welp;

All looks in order to this point, let's see if we can get a bit more info:
From the console (Ctrl+Alt+F1), what results with terminal command:
```

sudo service lightdm start

```

Maybe in executing the GUI startup routines from the login manager a problem exists that will not be prevalent when starting only lightdm from console.
Or get least provide some additional info.

[INDENT][INDENT]gotta be a cause
[/INDENT][/INDENT]

---

### Post by P-I H on 2014-08-31
Tried that, but the same happend as with the boot. The process stops and the lines I mentioned above is shown.

I had a problem with blank desktop before. That was fixed when i removed some configuration files in Home with the command:
```
rm ~/.gconf ~/.gconfd ~/.metacity ~/.compiz-1 ~/.config/compiz-1 ~/.config/dconf -rf
```

I can try that.

---

### Post by Bashing-om on 2014-08-31
P-I H; Well:

Removing the .configs files might have a positive affect.
But; let's try resetting to defaults in compiz and unity .. see what effect that has on lightdm before moving up to look at how lightdm is configured.
```

dconf reset -f /org/compiz/
unity --reset-icons
setsid unity

```
then log out and back in and see if there is a change.

[INDENT][INDENT]fault isolation,

[INDENT][INDENT][INDENT][INDENT]Oh where oh where
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Elfy on 2014-08-31
just a thought here - but wouldn't it be better to know that the current issue lots of people are having is fixed before doing anything else - how are you going to know if this is fixed - if it's not in fact the same thing ;)

---

### Post by P-I H on 2014-08-31
dconf reset -f /org/compiz/
unity --reset-icons
setsid unity
These commands didn't work. The system complained about no X and no upstart. The system uses systemd.

I also tried the more brutal version with
rm ~/.gconf ~/.gconfd ~/.metacity ~/.compiz-1 ~/.config/compiz-1 ~/.config/dconf -rf
That didn't work either.

---

### Post by P-I H on 2014-08-31
The system started OK. I then made these upgrades and got the problem:
  ```
2014-08-29 06:28:37 startup packages configure2014-08-29 06:28:37 configure nfs-common:amd64 1:1.2.8-9ubuntu1 <none>
2014-08-29 06:28:37 status half-configured nfs-common:amd64 1:1.2.8-9ubuntu1
2014-08-29 06:28:38 configure gsettings-ubuntu-schemas:all 0.0.3+14.10.20140827-0ubuntu1 <none>
2014-08-29 06:28:38 status unpacked gsettings-ubuntu-schemas:all 0.0.3+14.10.20140827-0ubuntu1
2014-08-29 06:28:38 status half-configured gsettings-ubuntu-schemas:all 0.0.3+14.10.20140827-0ubuntu1
2014-08-29 06:28:38 status installed gsettings-ubuntu-schemas:all 0.0.3+14.10.20140827-0ubuntu1
2014-08-29 06:28:38 configure libsignon-extension1:amd64 8.57+14.10.20140827-0ubuntu1 <none>
2014-08-29 06:28:38 status unpacked libsignon-extension1:amd64 8.57+14.10.20140827-0ubuntu1
2014-08-29 06:28:38 status half-configured libsignon-extension1:amd64 8.57+14.10.20140827-0ubuntu1
2014-08-29 06:28:38 status installed libsignon-extension1:amd64 8.57+14.10.20140827-0ubuntu1
2014-08-29 06:28:38 status triggers-pending libc-bin:amd64 2.19-4ubuntu2
2014-08-29 06:28:38 configure libsignon-plugins-common1:amd64 8.57+14.10.20140827-0ubuntu1 <none>
2014-08-29 06:28:38 status unpacked libsignon-plugins-common1:amd64 8.57+14.10.20140827-0ubuntu1
2014-08-29 06:28:38 status half-configured libsignon-plugins-common1:amd64 8.57+14.10.20140827-0ubuntu1
2014-08-29 06:28:38 status installed libsignon-plugins-common1:amd64 8.57+14.10.20140827-0ubuntu1
2014-08-29 06:28:38 configure libsignon-qt1:amd64 8.57+14.10.20140827-0ubuntu1 <none>
2014-08-29 06:28:38 status unpacked libsignon-qt1:amd64 8.57+14.10.20140827-0ubuntu1
2014-08-29 06:28:38 status half-configured libsignon-qt1:amd64 8.57+14.10.20140827-0ubuntu1
2014-08-29 06:28:38 status installed libsignon-qt1:amd64 8.57+14.10.20140827-0ubuntu1
2014-08-29 06:28:38 configure libsignon-qt5-1:amd64 8.57+14.10.20140827-0ubuntu1 <none>
2014-08-29 06:28:38 status unpacked libsignon-qt5-1:amd64 8.57+14.10.20140827-0ubuntu1
2014-08-29 06:28:38 status half-configured libsignon-qt5-1:amd64 8.57+14.10.20140827-0ubuntu1
2014-08-29 06:28:38 status installed libsignon-qt5-1:amd64 8.57+14.10.20140827-0ubuntu1
2014-08-29 06:28:39 configure signond:amd64 8.57+14.10.20140827-0ubuntu1 <none>
2014-08-29 06:28:39 status unpacked signond:amd64 8.57+14.10.20140827-0ubuntu1
2014-08-29 06:28:39 status unpacked signond:amd64 8.57+14.10.20140827-0ubuntu1
2014-08-29 06:28:39 status unpacked signond:amd64 8.57+14.10.20140827-0ubuntu1
2014-08-29 06:28:39 status half-configured signond:amd64 8.57+14.10.20140827-0ubuntu1
2014-08-29 06:28:39 status installed signond:amd64 8.57+14.10.20140827-0ubuntu1
2014-08-29 06:28:39 configure signon-plugin-password:amd64 8.57+14.10.20140827-0ubuntu1 <none>
2014-08-29 06:28:39 status unpacked signon-plugin-password:amd64 8.57+14.10.20140827-0ubuntu1
2014-08-29 06:28:39 status half-configured signon-plugin-password:amd64 8.57+14.10.20140827-0ubuntu1
2014-08-29 06:28:39 status installed signon-plugin-password:amd64 8.57+14.10.20140827-0ubuntu1
2014-08-29 06:28:39 trigproc libc-bin:amd64 2.19-4ubuntu2 <none>
2014-08-29 06:28:39 status half-configured libc-bin:amd64 2.19-4ubuntu2
2014-08-29 06:28:39 status installed libc-bin:amd64 2.19-4ubuntu2
2014-08-29 06:28:39 startup packages configure
2014-08-29 06:28:39 configure nfs-common:amd64 1:1.2.8-9ubuntu1 <none>
2014-08-29 06:28:39 status half-configured nfs-common:amd64 1:1.2.8-9ubuntu1
```

---

### Post by Bashing-om on 2014-08-31
P-I H; Yuk !

Release 14.10 I guess is now systemD rather than upstart. I had not even given that a thought as I have yet to even see 14.10.
Let's wait for those who do have experience with 14.10 to chime in here, see what their advise is.
Else we can see how the package manager tools - as known from earlier releases - perform in 14.10. Try to fix those broken dependencies ??

[INDENT][INDENT]going where few have gone before
[/INDENT][/INDENT]

---

### Post by jerrylamos on 2014-08-31
Intel Core 2 Duo 3 gHz 64 bit Intel® Q45/Q43  graphics, utopic since 7/31 boots to desktop no unity with 14.10 amd64.
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1359299](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1359299)
Confirmed.  Other user(s) similar failure.

Thrashing around for a month, difficulty my opinion compiz decides the hardware doesn't support 3D.  It does.  Very well.
I'm not a developer, my guess from symptoms, something in the newer Compiz and/or the kernel is now causing the Intel driver to fail.

utopic 64 7/31 and before run fine.  
utopic i386 32 bit runs fine, 32 bit version of kernel & compiz..  
utopic 64 Kubuntu, Xubuntu, Lubuntu run fine.  I don't think they use compiz?
Currently utopic 64 running O.K. with amd & ATI on my duo processor notebook.  
utopic 64 Running O.K. on my Acer duo processor netbook, intel Atom, though the added code (!) is slowing things down.  Fix is Lubuntu utopic 64 instead of unity.  Debian 64 LXDE is the fastest thing I've run on that hardware.

Past experience as a tester/user, compiz is extremely (!) dependent on hardware characteristics and driver..  Compiz has given me fits since Intrepid on Intel and ATI videos....

I've got one install with utopic 3.16.0-6 runs fine but booting 3.16.0-11 out of the same boot, everything the same except kernel, 3.16.0-11 fails.  

Go figure.

BTW, as a tester, I install frequently (!) since 14.10 is an unstable (!) development release.  My caution, be prepared to re-install when the code crashes.  Backups of course.

Good luck, I've gotten key advice from these forums.

---

### Post by P-I H on 2014-09-01
You only need to be a little patient. These updates fixed the problem:
```
2014-09-01 21:28:30 startup archives unpack
2014-09-01 21:28:30 upgrade libpopt0:amd64 1.16-8ubuntu1 1.16-10
2014-09-01 21:28:30 status half-configured libpopt0:amd64 1.16-8ubuntu1
2014-09-01 21:28:30 status unpacked libpopt0:amd64 1.16-8ubuntu1
2014-09-01 21:28:30 status half-installed libpopt0:amd64 1.16-8ubuntu1
2014-09-01 21:28:30 status half-installed libpopt0:amd64 1.16-8ubuntu1
2014-09-01 21:28:30 status unpacked libpopt0:amd64 1.16-10
2014-09-01 21:28:30 status unpacked libpopt0:amd64 1.16-10
2014-09-01 21:28:30 upgrade libgcc-4.8-dev:amd64 4.8.3-9ubuntu1 4.8.3-10ubuntu1
2014-09-01 21:28:30 status half-configured libgcc-4.8-dev:amd64 4.8.3-9ubuntu1
2014-09-01 21:28:30 status unpacked libgcc-4.8-dev:amd64 4.8.3-9ubuntu1
2014-09-01 21:28:30 status half-installed libgcc-4.8-dev:amd64 4.8.3-9ubuntu1
2014-09-01 21:28:31 status half-installed libgcc-4.8-dev:amd64 4.8.3-9ubuntu1
2014-09-01 21:28:31 status unpacked libgcc-4.8-dev:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:31 status unpacked libgcc-4.8-dev:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:31 upgrade gcc-4.8:amd64 4.8.3-9ubuntu1 4.8.3-10ubuntu1
2014-09-01 21:28:31 status half-configured gcc-4.8:amd64 4.8.3-9ubuntu1
2014-09-01 21:28:31 status unpacked gcc-4.8:amd64 4.8.3-9ubuntu1
2014-09-01 21:28:31 status half-installed gcc-4.8:amd64 4.8.3-9ubuntu1
2014-09-01 21:28:31 status triggers-pending man-db:amd64 2.6.7.1-1
2014-09-01 21:28:31 status half-installed gcc-4.8:amd64 4.8.3-9ubuntu1
2014-09-01 21:28:31 status unpacked gcc-4.8:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:31 status unpacked gcc-4.8:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:31 upgrade cpp-4.8:amd64 4.8.3-9ubuntu1 4.8.3-10ubuntu1
2014-09-01 21:28:31 status half-configured cpp-4.8:amd64 4.8.3-9ubuntu1
2014-09-01 21:28:31 status unpacked cpp-4.8:amd64 4.8.3-9ubuntu1
2014-09-01 21:28:31 status half-installed cpp-4.8:amd64 4.8.3-9ubuntu1
2014-09-01 21:28:32 status half-installed cpp-4.8:amd64 4.8.3-9ubuntu1
2014-09-01 21:28:32 status unpacked cpp-4.8:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:32 status unpacked cpp-4.8:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:32 upgrade libasan0:amd64 4.8.3-9ubuntu1 4.8.3-10ubuntu1
2014-09-01 21:28:32 status half-configured libasan0:amd64 4.8.3-9ubuntu1
2014-09-01 21:28:32 status unpacked libasan0:amd64 4.8.3-9ubuntu1
2014-09-01 21:28:32 status half-installed libasan0:amd64 4.8.3-9ubuntu1
2014-09-01 21:28:32 status half-installed libasan0:amd64 4.8.3-9ubuntu1
2014-09-01 21:28:32 status unpacked libasan0:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:32 status unpacked libasan0:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:32 upgrade gcc-4.8-base:amd64 4.8.3-9ubuntu1 4.8.3-10ubuntu1
2014-09-01 21:28:32 status half-configured gcc-4.8-base:amd64 4.8.3-9ubuntu1
2014-09-01 21:28:32 status unpacked gcc-4.8-base:amd64 4.8.3-9ubuntu1
2014-09-01 21:28:32 status half-installed gcc-4.8-base:amd64 4.8.3-9ubuntu1
2014-09-01 21:28:32 status half-installed gcc-4.8-base:amd64 4.8.3-9ubuntu1
2014-09-01 21:28:32 status unpacked gcc-4.8-base:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:32 status unpacked gcc-4.8-base:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:32 upgrade libatkmm-1.6-1:amd64 2.22.7-2ubuntu1 2.22.7-2.1
2014-09-01 21:28:32 status half-configured libatkmm-1.6-1:amd64 2.22.7-2ubuntu1
2014-09-01 21:28:32 status unpacked libatkmm-1.6-1:amd64 2.22.7-2ubuntu1
2014-09-01 21:28:32 status half-installed libatkmm-1.6-1:amd64 2.22.7-2ubuntu1
2014-09-01 21:28:32 status half-installed libatkmm-1.6-1:amd64 2.22.7-2ubuntu1
2014-09-01 21:28:32 status unpacked libatkmm-1.6-1:amd64 2.22.7-2.1
2014-09-01 21:28:32 status unpacked libatkmm-1.6-1:amd64 2.22.7-2.1
2014-09-01 21:28:33 upgrade enchant:amd64 1.6.0-10ubuntu1 1.6.0-10.1
2014-09-01 21:28:33 status half-configured enchant:amd64 1.6.0-10ubuntu1
2014-09-01 21:28:33 status unpacked enchant:amd64 1.6.0-10ubuntu1
2014-09-01 21:28:33 status half-installed enchant:amd64 1.6.0-10ubuntu1
2014-09-01 21:28:33 status half-installed enchant:amd64 1.6.0-10ubuntu1
2014-09-01 21:28:33 status unpacked enchant:amd64 1.6.0-10.1
2014-09-01 21:28:33 status unpacked enchant:amd64 1.6.0-10.1
2014-09-01 21:28:33 upgrade libenchant1c2a:amd64 1.6.0-10ubuntu1 1.6.0-10.1
2014-09-01 21:28:33 status half-configured libenchant1c2a:amd64 1.6.0-10ubuntu1
2014-09-01 21:28:33 status unpacked libenchant1c2a:amd64 1.6.0-10ubuntu1
2014-09-01 21:28:33 status half-installed libenchant1c2a:amd64 1.6.0-10ubuntu1
2014-09-01 21:28:33 status half-installed libenchant1c2a:amd64 1.6.0-10ubuntu1
2014-09-01 21:28:33 status unpacked libenchant1c2a:amd64 1.6.0-10.1
2014-09-01 21:28:33 status unpacked libenchant1c2a:amd64 1.6.0-10.1
2014-09-01 21:28:33 upgrade libgee-0.8-2:amd64 0.14.0-1ubuntu1 0.14.0-2
2014-09-01 21:28:33 status half-configured libgee-0.8-2:amd64 0.14.0-1ubuntu1
2014-09-01 21:28:33 status unpacked libgee-0.8-2:amd64 0.14.0-1ubuntu1
2014-09-01 21:28:33 status half-installed libgee-0.8-2:amd64 0.14.0-1ubuntu1
2014-09-01 21:28:33 status half-installed libgee-0.8-2:amd64 0.14.0-1ubuntu1
2014-09-01 21:28:33 status unpacked libgee-0.8-2:amd64 0.14.0-2
2014-09-01 21:28:33 status unpacked libgee-0.8-2:amd64 0.14.0-2
2014-09-01 21:28:33 upgrade libpangomm-1.4-1:amd64 2.34.0-1ubuntu1 2.34.0-1.1
2014-09-01 21:28:33 status half-configured libpangomm-1.4-1:amd64 2.34.0-1ubuntu1
2014-09-01 21:28:33 status unpacked libpangomm-1.4-1:amd64 2.34.0-1ubuntu1
2014-09-01 21:28:33 status half-installed libpangomm-1.4-1:amd64 2.34.0-1ubuntu1
2014-09-01 21:28:33 status half-installed libpangomm-1.4-1:amd64 2.34.0-1ubuntu1
2014-09-01 21:28:33 status unpacked libpangomm-1.4-1:amd64 2.34.0-1.1
2014-09-01 21:28:33 status unpacked libpangomm-1.4-1:amd64 2.34.0-1.1
2014-09-01 21:28:33 upgrade libgtkmm-2.4-1c2a:amd64 1:2.24.4-1ubuntu1 1:2.24.4-1.1
2014-09-01 21:28:33 status half-configured libgtkmm-2.4-1c2a:amd64 1:2.24.4-1ubuntu1
2014-09-01 21:28:33 status unpacked libgtkmm-2.4-1c2a:amd64 1:2.24.4-1ubuntu1
2014-09-01 21:28:33 status half-installed libgtkmm-2.4-1c2a:amd64 1:2.24.4-1ubuntu1
2014-09-01 21:28:33 status half-installed libgtkmm-2.4-1c2a:amd64 1:2.24.4-1ubuntu1
2014-09-01 21:28:33 status unpacked libgtkmm-2.4-1c2a:amd64 1:2.24.4-1.1
2014-09-01 21:28:33 status unpacked libgtkmm-2.4-1c2a:amd64 1:2.24.4-1.1
2014-09-01 21:28:33 upgrade libgtkmm-3.0-1:amd64 3.12.0-1ubuntu1 3.12.0-1.1
2014-09-01 21:28:33 status half-configured libgtkmm-3.0-1:amd64 3.12.0-1ubuntu1
2014-09-01 21:28:33 status unpacked libgtkmm-3.0-1:amd64 3.12.0-1ubuntu1
2014-09-01 21:28:33 status half-installed libgtkmm-3.0-1:amd64 3.12.0-1ubuntu1
2014-09-01 21:28:34 status half-installed libgtkmm-3.0-1:amd64 3.12.0-1ubuntu1
2014-09-01 21:28:34 status unpacked libgtkmm-3.0-1:amd64 3.12.0-1.1
2014-09-01 21:28:34 status unpacked libgtkmm-3.0-1:amd64 3.12.0-1.1
2014-09-01 21:28:34 upgrade libilmbase6:amd64 1.0.1-6ubuntu1 1.0.1-6.1
2014-09-01 21:28:34 status half-configured libilmbase6:amd64 1.0.1-6ubuntu1
2014-09-01 21:28:34 status unpacked libilmbase6:amd64 1.0.1-6ubuntu1
2014-09-01 21:28:34 status half-installed libilmbase6:amd64 1.0.1-6ubuntu1
2014-09-01 21:28:34 status half-installed libilmbase6:amd64 1.0.1-6ubuntu1
2014-09-01 21:28:34 status unpacked libilmbase6:amd64 1.0.1-6.1
2014-09-01 21:28:34 status unpacked libilmbase6:amd64 1.0.1-6.1
2014-09-01 21:28:34 upgrade libmircommon1:amd64 0.6.1+14.10.20140814-0ubuntu1 0.7.0+14.10.20140829-0ubuntu1
2014-09-01 21:28:34 status half-configured libmircommon1:amd64 0.6.1+14.10.20140814-0ubuntu1
2014-09-01 21:28:34 status unpacked libmircommon1:amd64 0.6.1+14.10.20140814-0ubuntu1
2014-09-01 21:28:34 status half-installed libmircommon1:amd64 0.6.1+14.10.20140814-0ubuntu1
2014-09-01 21:28:34 status half-installed libmircommon1:amd64 0.6.1+14.10.20140814-0ubuntu1
2014-09-01 21:28:34 status unpacked libmircommon1:amd64 0.7.0+14.10.20140829-0ubuntu1
2014-09-01 21:28:34 status unpacked libmircommon1:amd64 0.7.0+14.10.20140829-0ubuntu1
2014-09-01 21:28:34 upgrade libmirclient8:amd64 0.6.1+14.10.20140814-0ubuntu1 0.7.0+14.10.20140829-0ubuntu1
2014-09-01 21:28:34 status half-configured libmirclient8:amd64 0.6.1+14.10.20140814-0ubuntu1
2014-09-01 21:28:34 status unpacked libmirclient8:amd64 0.6.1+14.10.20140814-0ubuntu1
2014-09-01 21:28:34 status half-installed libmirclient8:amd64 0.6.1+14.10.20140814-0ubuntu1
2014-09-01 21:28:34 status half-installed libmirclient8:amd64 0.6.1+14.10.20140814-0ubuntu1
2014-09-01 21:28:34 status unpacked libmirclient8:amd64 0.7.0+14.10.20140829-0ubuntu1
2014-09-01 21:28:34 status unpacked libmirclient8:amd64 0.7.0+14.10.20140829-0ubuntu1
2014-09-01 21:28:34 upgrade libmirclientplatform-mesa:amd64 0.6.1+14.10.20140814-0ubuntu1 0.7.0+14.10.20140829-0ubuntu1
2014-09-01 21:28:34 status half-configured libmirclientplatform-mesa:amd64 0.6.1+14.10.20140814-0ubuntu1
2014-09-01 21:28:34 status unpacked libmirclientplatform-mesa:amd64 0.6.1+14.10.20140814-0ubuntu1
2014-09-01 21:28:34 status half-installed libmirclientplatform-mesa:amd64 0.6.1+14.10.20140814-0ubuntu1
2014-09-01 21:28:34 status half-installed libmirclientplatform-mesa:amd64 0.6.1+14.10.20140814-0ubuntu1
2014-09-01 21:28:34 status unpacked libmirclientplatform-mesa:amd64 0.7.0+14.10.20140829-0ubuntu1
2014-09-01 21:28:34 status unpacked libmirclientplatform-mesa:amd64 0.7.0+14.10.20140829-0ubuntu1
2014-09-01 21:28:34 upgrade libpth20:amd64 2.0.7-19ubuntu1 2.0.7-20
2014-09-01 21:28:34 status half-configured libpth20:amd64 2.0.7-19ubuntu1
2014-09-01 21:28:34 status unpacked libpth20:amd64 2.0.7-19ubuntu1
2014-09-01 21:28:34 status half-installed libpth20:amd64 2.0.7-19ubuntu1
2014-09-01 21:28:34 status half-installed libpth20:amd64 2.0.7-19ubuntu1
2014-09-01 21:28:34 status unpacked libpth20:amd64 2.0.7-20
2014-09-01 21:28:34 status unpacked libpth20:amd64 2.0.7-20
2014-09-01 21:28:35 upgrade libthumbnailer0:amd64 1.2+14.10.20140827.1-0ubuntu1 1.2+14.10.20140901-0ubuntu1
2014-09-01 21:28:35 status half-configured libthumbnailer0:amd64 1.2+14.10.20140827.1-0ubuntu1
2014-09-01 21:28:35 status unpacked libthumbnailer0:amd64 1.2+14.10.20140827.1-0ubuntu1
2014-09-01 21:28:35 status half-installed libthumbnailer0:amd64 1.2+14.10.20140827.1-0ubuntu1
2014-09-01 21:28:35 status half-installed libthumbnailer0:amd64 1.2+14.10.20140827.1-0ubuntu1
2014-09-01 21:28:35 status unpacked libthumbnailer0:amd64 1.2+14.10.20140901-0ubuntu1
2014-09-01 21:28:35 status unpacked libthumbnailer0:amd64 1.2+14.10.20140901-0ubuntu1
2014-09-01 21:28:35 upgrade libxp6:amd64 1:1.0.2-1ubuntu1 1:1.0.2-2
2014-09-01 21:28:35 status half-configured libxp6:amd64 1:1.0.2-1ubuntu1
2014-09-01 21:28:35 status unpacked libxp6:amd64 1:1.0.2-1ubuntu1
2014-09-01 21:28:35 status half-installed libxp6:amd64 1:1.0.2-1ubuntu1
2014-09-01 21:28:35 status half-installed libxp6:amd64 1:1.0.2-1ubuntu1
2014-09-01 21:28:35 status unpacked libxp6:amd64 1:1.0.2-2
2014-09-01 21:28:35 status unpacked libxp6:amd64 1:1.0.2-2
2014-09-01 21:28:35 upgrade ubuntu-drivers-common:amd64 1:0.2.98 1:0.2.98.1
2014-09-01 21:28:35 status half-configured ubuntu-drivers-common:amd64 1:0.2.98
2014-09-01 21:28:35 status unpacked ubuntu-drivers-common:amd64 1:0.2.98
2014-09-01 21:28:35 status half-installed ubuntu-drivers-common:amd64 1:0.2.98
2014-09-01 21:28:35 status triggers-pending ureadahead:amd64 0.100.0-16
2014-09-01 21:28:35 status half-installed ubuntu-drivers-common:amd64 1:0.2.98
2014-09-01 21:28:35 status half-installed ubuntu-drivers-common:amd64 1:0.2.98
2014-09-01 21:28:35 status unpacked ubuntu-drivers-common:amd64 1:0.2.98.1
2014-09-01 21:28:35 status unpacked ubuntu-drivers-common:amd64 1:0.2.98.1
2014-09-01 21:28:35 upgrade libxcb-keysyms1:amd64 0.3.9-1ubuntu1 0.3.9-2
2014-09-01 21:28:35 status half-configured libxcb-keysyms1:amd64 0.3.9-1ubuntu1
2014-09-01 21:28:35 status unpacked libxcb-keysyms1:amd64 0.3.9-1ubuntu1
2014-09-01 21:28:35 status half-installed libxcb-keysyms1:amd64 0.3.9-1ubuntu1
2014-09-01 21:28:35 status half-installed libxcb-keysyms1:amd64 0.3.9-1ubuntu1
2014-09-01 21:28:35 status unpacked libxcb-keysyms1:amd64 0.3.9-2
2014-09-01 21:28:35 status unpacked libxcb-keysyms1:amd64 0.3.9-2
2014-09-01 21:28:36 upgrade libxcb-util0:amd64 0.3.8-2ubuntu1 0.3.8-3
2014-09-01 21:28:36 status half-configured libxcb-util0:amd64 0.3.8-2ubuntu1
2014-09-01 21:28:36 status unpacked libxcb-util0:amd64 0.3.8-2ubuntu1
2014-09-01 21:28:36 status half-installed libxcb-util0:amd64 0.3.8-2ubuntu1
2014-09-01 21:28:36 status half-installed libxcb-util0:amd64 0.3.8-2ubuntu1
2014-09-01 21:28:36 status unpacked libxcb-util0:amd64 0.3.8-3
2014-09-01 21:28:36 status unpacked libxcb-util0:amd64 0.3.8-3
2014-09-01 21:28:36 upgrade tzdata-java:all 2014f-1 2014g-1
2014-09-01 21:28:36 status half-configured tzdata-java:all 2014f-1
2014-09-01 21:28:36 status unpacked tzdata-java:all 2014f-1
2014-09-01 21:28:36 status half-installed tzdata-java:all 2014f-1
2014-09-01 21:28:36 status half-installed tzdata-java:all 2014f-1
2014-09-01 21:28:36 status unpacked tzdata-java:all 2014g-1
2014-09-01 21:28:36 status unpacked tzdata-java:all 2014g-1
2014-09-01 21:28:36 upgrade tzdata:all 2014f-1 2014g-1
2014-09-01 21:28:36 status half-configured tzdata:all 2014f-1
2014-09-01 21:28:36 status unpacked tzdata:all 2014f-1
2014-09-01 21:28:36 status half-installed tzdata:all 2014f-1
2014-09-01 21:28:37 status half-installed tzdata:all 2014f-1
2014-09-01 21:28:37 status unpacked tzdata:all 2014g-1
2014-09-01 21:28:37 status unpacked tzdata:all 2014g-1
2014-09-01 21:28:37 trigproc man-db:amd64 2.6.7.1-1 <none>
2014-09-01 21:28:37 status half-configured man-db:amd64 2.6.7.1-1
2014-09-01 21:28:38 status installed man-db:amd64 2.6.7.1-1
2014-09-01 21:28:38 trigproc ureadahead:amd64 0.100.0-16 <none>
2014-09-01 21:28:38 status half-configured ureadahead:amd64 0.100.0-16
2014-09-01 21:28:38 status installed ureadahead:amd64 0.100.0-16
2014-09-01 21:28:39 startup packages configure
2014-09-01 21:28:39 configure tzdata:all 2014g-1 <none>
2014-09-01 21:28:39 status unpacked tzdata:all 2014g-1
2014-09-01 21:28:39 status half-configured tzdata:all 2014g-1
2014-09-01 21:28:39 status installed tzdata:all 2014g-1
2014-09-01 21:28:39 startup archives unpack
2014-09-01 21:28:40 upgrade psensor:amd64 1.0.2-1ubuntu3 1.0.2-1ubuntu4
2014-09-01 21:28:40 status half-configured psensor:amd64 1.0.2-1ubuntu3
2014-09-01 21:28:40 status unpacked psensor:amd64 1.0.2-1ubuntu3
2014-09-01 21:28:40 status half-installed psensor:amd64 1.0.2-1ubuntu3
2014-09-01 21:28:40 status triggers-pending man-db:amd64 2.6.7.1-1
2014-09-01 21:28:40 status triggers-pending hicolor-icon-theme:all 0.13-1
2014-09-01 21:28:40 status half-installed psensor:amd64 1.0.2-1ubuntu3
2014-09-01 21:28:40 status triggers-pending bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu3
2014-09-01 21:28:40 status half-installed psensor:amd64 1.0.2-1ubuntu3
2014-09-01 21:28:40 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu2
2014-09-01 21:28:40 status half-installed psensor:amd64 1.0.2-1ubuntu3
2014-09-01 21:28:40 status triggers-pending mime-support:all 3.55ubuntu1
2014-09-01 21:28:40 status triggers-pending gnome-menus:amd64 3.10.1-0ubuntu2
2014-09-01 21:28:40 status triggers-pending gconf2:amd64 3.2.6-2ubuntu1
2014-09-01 21:28:40 status half-installed psensor:amd64 1.0.2-1ubuntu3
2014-09-01 21:28:40 status half-installed psensor:amd64 1.0.2-1ubuntu3
2014-09-01 21:28:40 status unpacked psensor:amd64 1.0.2-1ubuntu4
2014-09-01 21:28:40 status unpacked psensor:amd64 1.0.2-1ubuntu4
2014-09-01 21:28:40 upgrade psensor-common:all 1.0.2-1ubuntu3 1.0.2-1ubuntu4
2014-09-01 21:28:40 status half-configured psensor-common:all 1.0.2-1ubuntu3
2014-09-01 21:28:40 status unpacked psensor-common:all 1.0.2-1ubuntu3
2014-09-01 21:28:40 status half-installed psensor-common:all 1.0.2-1ubuntu3
2014-09-01 21:28:40 status triggers-pending doc-base:all 0.10.5
2014-09-01 21:28:40 status half-installed psensor-common:all 1.0.2-1ubuntu3
2014-09-01 21:28:40 status unpacked psensor-common:all 1.0.2-1ubuntu4
2014-09-01 21:28:40 status unpacked psensor-common:all 1.0.2-1ubuntu4
2014-09-01 21:28:40 trigproc man-db:amd64 2.6.7.1-1 <none>
2014-09-01 21:28:40 status half-configured man-db:amd64 2.6.7.1-1
2014-09-01 21:28:41 status installed man-db:amd64 2.6.7.1-1
2014-09-01 21:28:41 trigproc hicolor-icon-theme:all 0.13-1 <none>
2014-09-01 21:28:41 status half-configured hicolor-icon-theme:all 0.13-1
2014-09-01 21:28:42 status installed hicolor-icon-theme:all 0.13-1
2014-09-01 21:28:42 trigproc bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu3 <none>
2014-09-01 21:28:42 status half-configured bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu3
2014-09-01 21:28:42 status installed bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu3
2014-09-01 21:28:42 trigproc desktop-file-utils:amd64 0.22-1ubuntu2 <none>
2014-09-01 21:28:42 status half-configured desktop-file-utils:amd64 0.22-1ubuntu2
2014-09-01 21:28:42 status installed desktop-file-utils:amd64 0.22-1ubuntu2
2014-09-01 21:28:42 trigproc mime-support:all 3.55ubuntu1 <none>
2014-09-01 21:28:42 status half-configured mime-support:all 3.55ubuntu1
2014-09-01 21:28:42 status installed mime-support:all 3.55ubuntu1
2014-09-01 21:28:42 trigproc gnome-menus:amd64 3.10.1-0ubuntu2 <none>
2014-09-01 21:28:42 status half-configured gnome-menus:amd64 3.10.1-0ubuntu2
2014-09-01 21:28:42 status installed gnome-menus:amd64 3.10.1-0ubuntu2
2014-09-01 21:28:42 trigproc gconf2:amd64 3.2.6-2ubuntu1 <none>
2014-09-01 21:28:42 status half-configured gconf2:amd64 3.2.6-2ubuntu1
2014-09-01 21:28:42 status installed gconf2:amd64 3.2.6-2ubuntu1
2014-09-01 21:28:42 trigproc doc-base:all 0.10.5 <none>
2014-09-01 21:28:42 status half-configured doc-base:all 0.10.5
2014-09-01 21:28:42 status installed doc-base:all 0.10.5
2014-09-01 21:28:43 startup packages configure
2014-09-01 21:28:43 configure nfs-common:amd64 1:1.2.8-9ubuntu1 <none>
2014-09-01 21:28:43 status half-configured nfs-common:amd64 1:1.2.8-9ubuntu1
2014-09-01 21:28:44 configure libpopt0:amd64 1.16-10 <none>
2014-09-01 21:28:44 status unpacked libpopt0:amd64 1.16-10
2014-09-01 21:28:44 status half-configured libpopt0:amd64 1.16-10
2014-09-01 21:28:44 status installed libpopt0:amd64 1.16-10
2014-09-01 21:28:44 status triggers-pending libc-bin:amd64 2.19-10ubuntu1
2014-09-01 21:28:44 configure gcc-4.8-base:amd64 4.8.3-10ubuntu1 <none>
2014-09-01 21:28:44 status unpacked gcc-4.8-base:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:44 status half-configured gcc-4.8-base:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:44 status installed gcc-4.8-base:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:44 configure libasan0:amd64 4.8.3-10ubuntu1 <none>
2014-09-01 21:28:44 status unpacked libasan0:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:44 status half-configured libasan0:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:44 status installed libasan0:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:44 configure libgcc-4.8-dev:amd64 4.8.3-10ubuntu1 <none>
2014-09-01 21:28:44 status unpacked libgcc-4.8-dev:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:44 status half-configured libgcc-4.8-dev:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:44 status installed libgcc-4.8-dev:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:44 configure cpp-4.8:amd64 4.8.3-10ubuntu1 <none>
2014-09-01 21:28:44 status unpacked cpp-4.8:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:44 status half-configured cpp-4.8:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:44 status installed cpp-4.8:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:44 configure gcc-4.8:amd64 4.8.3-10ubuntu1 <none>
2014-09-01 21:28:44 status unpacked gcc-4.8:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:44 status half-configured gcc-4.8:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:44 status installed gcc-4.8:amd64 4.8.3-10ubuntu1
2014-09-01 21:28:44 configure libatkmm-1.6-1:amd64 2.22.7-2.1 <none>
2014-09-01 21:28:44 status unpacked libatkmm-1.6-1:amd64 2.22.7-2.1
2014-09-01 21:28:44 status half-configured libatkmm-1.6-1:amd64 2.22.7-2.1
2014-09-01 21:28:44 status installed libatkmm-1.6-1:amd64 2.22.7-2.1
2014-09-01 21:28:44 configure libenchant1c2a:amd64 1.6.0-10.1 <none>
2014-09-01 21:28:44 status unpacked libenchant1c2a:amd64 1.6.0-10.1
2014-09-01 21:28:44 status half-configured libenchant1c2a:amd64 1.6.0-10.1
2014-09-01 21:28:44 status installed libenchant1c2a:amd64 1.6.0-10.1
2014-09-01 21:28:44 configure enchant:amd64 1.6.0-10.1 <none>
2014-09-01 21:28:44 status unpacked enchant:amd64 1.6.0-10.1
2014-09-01 21:28:44 status half-configured enchant:amd64 1.6.0-10.1
2014-09-01 21:28:44 status installed enchant:amd64 1.6.0-10.1
2014-09-01 21:28:44 configure libgee-0.8-2:amd64 0.14.0-2 <none>
2014-09-01 21:28:44 status unpacked libgee-0.8-2:amd64 0.14.0-2
2014-09-01 21:28:44 status half-configured libgee-0.8-2:amd64 0.14.0-2
2014-09-01 21:28:44 status installed libgee-0.8-2:amd64 0.14.0-2
2014-09-01 21:28:44 configure libpangomm-1.4-1:amd64 2.34.0-1.1 <none>
2014-09-01 21:28:44 status unpacked libpangomm-1.4-1:amd64 2.34.0-1.1
2014-09-01 21:28:44 status half-configured libpangomm-1.4-1:amd64 2.34.0-1.1
2014-09-01 21:28:44 status installed libpangomm-1.4-1:amd64 2.34.0-1.1
2014-09-01 21:28:44 configure libgtkmm-2.4-1c2a:amd64 1:2.24.4-1.1 <none>
2014-09-01 21:28:44 status unpacked libgtkmm-2.4-1c2a:amd64 1:2.24.4-1.1
2014-09-01 21:28:44 status half-configured libgtkmm-2.4-1c2a:amd64 1:2.24.4-1.1
2014-09-01 21:28:44 status installed libgtkmm-2.4-1c2a:amd64 1:2.24.4-1.1
2014-09-01 21:28:44 configure libgtkmm-3.0-1:amd64 3.12.0-1.1 <none>
2014-09-01 21:28:44 status unpacked libgtkmm-3.0-1:amd64 3.12.0-1.1
2014-09-01 21:28:44 status half-configured libgtkmm-3.0-1:amd64 3.12.0-1.1
2014-09-01 21:28:44 status installed libgtkmm-3.0-1:amd64 3.12.0-1.1
2014-09-01 21:28:44 configure libilmbase6:amd64 1.0.1-6.1 <none>
2014-09-01 21:28:44 status unpacked libilmbase6:amd64 1.0.1-6.1
2014-09-01 21:28:44 status half-configured libilmbase6:amd64 1.0.1-6.1
2014-09-01 21:28:44 status installed libilmbase6:amd64 1.0.1-6.1
2014-09-01 21:28:44 configure libmircommon1:amd64 0.7.0+14.10.20140829-0ubuntu1 <none>
2014-09-01 21:28:44 status unpacked libmircommon1:amd64 0.7.0+14.10.20140829-0ubuntu1
2014-09-01 21:28:44 status half-configured libmircommon1:amd64 0.7.0+14.10.20140829-0ubuntu1
2014-09-01 21:28:44 status installed libmircommon1:amd64 0.7.0+14.10.20140829-0ubuntu1
2014-09-01 21:28:44 configure libmirclientplatform-mesa:amd64 0.7.0+14.10.20140829-0ubuntu1 <none>
2014-09-01 21:28:44 status unpacked libmirclientplatform-mesa:amd64 0.7.0+14.10.20140829-0ubuntu1
2014-09-01 21:28:44 status half-configured libmirclientplatform-mesa:amd64 0.7.0+14.10.20140829-0ubuntu1
2014-09-01 21:28:44 status installed libmirclientplatform-mesa:amd64 0.7.0+14.10.20140829-0ubuntu1
2014-09-01 21:28:44 configure libmirclient8:amd64 0.7.0+14.10.20140829-0ubuntu1 <none>
2014-09-01 21:28:44 status unpacked libmirclient8:amd64 0.7.0+14.10.20140829-0ubuntu1
2014-09-01 21:28:44 status half-configured libmirclient8:amd64 0.7.0+14.10.20140829-0ubuntu1
2014-09-01 21:28:44 status installed libmirclient8:amd64 0.7.0+14.10.20140829-0ubuntu1
2014-09-01 21:28:44 configure libpth20:amd64 2.0.7-20 <none>
2014-09-01 21:28:44 status unpacked libpth20:amd64 2.0.7-20
2014-09-01 21:28:44 status half-configured libpth20:amd64 2.0.7-20
2014-09-01 21:28:44 status installed libpth20:amd64 2.0.7-20
2014-09-01 21:28:44 configure libthumbnailer0:amd64 1.2+14.10.20140901-0ubuntu1 <none>
2014-09-01 21:28:44 status unpacked libthumbnailer0:amd64 1.2+14.10.20140901-0ubuntu1
2014-09-01 21:28:44 status half-configured libthumbnailer0:amd64 1.2+14.10.20140901-0ubuntu1
2014-09-01 21:28:44 status installed libthumbnailer0:amd64 1.2+14.10.20140901-0ubuntu1
2014-09-01 21:28:44 configure libxp6:amd64 1:1.0.2-2 <none>
2014-09-01 21:28:44 status unpacked libxp6:amd64 1:1.0.2-2
2014-09-01 21:28:44 status half-configured libxp6:amd64 1:1.0.2-2
2014-09-01 21:28:44 status installed libxp6:amd64 1:1.0.2-2
2014-09-01 21:28:44 configure ubuntu-drivers-common:amd64 1:0.2.98.1 <none>
2014-09-01 21:28:44 status unpacked ubuntu-drivers-common:amd64 1:0.2.98.1
2014-09-01 21:28:44 status unpacked ubuntu-drivers-common:amd64 1:0.2.98.1
2014-09-01 21:28:44 status half-configured ubuntu-drivers-common:amd64 1:0.2.98.1
2014-09-01 21:28:44 status installed ubuntu-drivers-common:amd64 1:0.2.98.1
2014-09-01 21:28:44 configure libxcb-keysyms1:amd64 0.3.9-2 <none>
2014-09-01 21:28:44 status unpacked libxcb-keysyms1:amd64 0.3.9-2
2014-09-01 21:28:44 status half-configured libxcb-keysyms1:amd64 0.3.9-2
2014-09-01 21:28:44 status installed libxcb-keysyms1:amd64 0.3.9-2
2014-09-01 21:28:44 configure libxcb-util0:amd64 0.3.8-3 <none>
2014-09-01 21:28:44 status unpacked libxcb-util0:amd64 0.3.8-3
2014-09-01 21:28:44 status half-configured libxcb-util0:amd64 0.3.8-3
2014-09-01 21:28:44 status installed libxcb-util0:amd64 0.3.8-3
2014-09-01 21:28:45 configure tzdata-java:all 2014g-1 <none>
2014-09-01 21:28:45 status unpacked tzdata-java:all 2014g-1
2014-09-01 21:28:45 status half-configured tzdata-java:all 2014g-1
2014-09-01 21:28:45 status installed tzdata-java:all 2014g-1
2014-09-01 21:28:45 configure psensor-common:all 1.0.2-1ubuntu4 <none>
2014-09-01 21:28:45 status unpacked psensor-common:all 1.0.2-1ubuntu4
2014-09-01 21:28:45 status half-configured psensor-common:all 1.0.2-1ubuntu4
2014-09-01 21:28:45 status installed psensor-common:all 1.0.2-1ubuntu4
2014-09-01 21:28:45 configure psensor:amd64 1.0.2-1ubuntu4 <none>
2014-09-01 21:28:45 status unpacked psensor:amd64 1.0.2-1ubuntu4
2014-09-01 21:28:45 status half-configured psensor:amd64 1.0.2-1ubuntu4
2014-09-01 21:28:45 status installed psensor:amd64 1.0.2-1ubuntu4
2014-09-01 21:28:45 trigproc libc-bin:amd64 2.19-10ubuntu1 <none>
2014-09-01 21:28:45 status half-configured libc-bin:amd64 2.19-10ubuntu1
2014-09-01 21:28:45 status installed libc-bin:amd64 2.19-10ubuntu1

```
They also fixed the problem with psensor and the update of nfs-common

---

### Post by Bashing-om on 2014-09-01
P-I H; Great !

(wheewwhh) Construction zone, development in progress

---

### Post by jerrylamos on 2014-09-01
> **P-I H said:**
> You only need to be a little patient. These updates fixed the problem:
```
2014-09-01 21:28:30 startup archives unpack....
```Didn't fix it for me on utopic amd64 Intel Core 2 Duo 3 gHz.

unity & compiz don't start.  Only way to boot is with nomodeset on the linux boot line, which limits resolution to 1024x768.

---

### Post by jerrylamos on 2014-09-02
3.16.0-12 boots normally today, several times already on this Intel Core 2 Duo 3 gHz.  Booted 3.16.0-11 with nomodeset on the linux line, (ugly) did sudo apt-get update, sudo apt-get dist-upgrade which brought in 3.16.0-12

Whatever is in 3.16.0-12 is working today.  Dread the next update.....

---

