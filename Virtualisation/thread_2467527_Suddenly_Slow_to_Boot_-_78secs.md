---
title: "Suddenly Slow to Boot - 78secs"
date: 2021-09-29
forum: Virtualisation
---

### Post by Quarkrad on 2021-09-29
I have a number of windows and ubuntu kvms - all in the same pool.  Up to a few days ago they all booted within seconds - but two of the ubuntu mate (20.04) vms now take 78sec to boot to the Desktop(?).  Having played around a bit, today I install a fresh ubuntu mate vm with the same basic parameters (cpu cores, memory etc) in the same pool and it boots in seconds.  I'm now trawling through the xml code of each section to see where any differences are.  I'm new to all this (kvm, virsh, virt etc) - is there anything obvious I should look at before examining all the xml code?

---

### Post by ajgreeny on 2021-09-29
Have a look at the output of a couple of the Linux VMs, one fast booting, the other slow, when running command ```
systemd-analyze blame
``` and compare the two to see if any obvious differences can offer any clues.

This assumes that the two VMs use systemd, which is now a large majority of Linux OSs and that the command is usable on them both; I know almost only Ubuntu or Ubuntu based distros nowadays.

---

### Post by MAFoElffen on 2021-09-29
Two things... Look at the domain logs in /var/lib/libvirt/qemu for any startup warnings...

Then on the VM itself, install bootchart... We used to use this for benchmarking DEV Cycle builds and what they did while booting/startup. Not sure, but now I think it is called systemd-bootchart. Will create a graphical chart of all that went on during the starup, including load.
```

sudo apt install -y systemd-bootchart

```
Is a great tool for startup diagnostics...

---

### Post by Quarkrad on 2021-09-30
I've installed systemd.bootchart but here is the first problem:  how is it used?   Been trawling the web for hours - lots of info on how to install it but nothing on how to actually use it. I've gone though the man page and changed somethings in /etc/systemd/bootchart.conf but not sure what to do next. Entering systemd.bootchart in the terminal does nothing.

---

### Post by MAFoElffen on 2021-10-01
To get it to start logging
```

sudo systemctl enable systemd-bootchart
sudo systemctl start systemd-bootchart
sudo reboot

```
You can view, convert or export to other formats with InkScape... 

See attachment. That is my last boot up, converted to a PDF file.

Chart will be located at /run/log/bootchart-<date-timestamp>.svg

---

### Post by Quarkrad on 2021-10-01
Unfortunately I cannot find my first systemd-analyze blame out put but there was, potentially, a big clue to my issue.  A service, that I created, called backup.service was taking 8min something (although 8min seems crazy).  (I have been testing attempting to get a backup script to run automatically each time I power down).  I deleted the backup.service

```
systemctl stop [servicename]
systemctl disable [servicename]
rm /etc/systemd/system/[servicename]
rm /etc/systemd/system/[servicename] # and symlinks that might be related
rm /usr/lib/systemd/system/[servicename] 
rm /usr/lib/systemd/system/[servicename] # and symlinks that might be related
systemctl daemon-reload
systemctl reset-failed
```

I rebooted (now 98sec) and got:

```
dad@dadkvm:~$ systemd-analyze blame
Bootup is not yet finished (org.freedesktop.systemd1.Manager.FinishTimestampMonotonic=0).
Please try again later.
Hint: Use 'systemctl list-jobs' to see active jobs
dad@dadkvm:~$ systemctl list-jobs
JOB UNIT                                 TYPE  STATE  
151 systemd-update-utmp-runlevel.service start waiting
2   multi-user.target                    start waiting
124 backup.service                       start running
1   graphical.target                     start waiting

4 jobs listed.
```

followed by:

```
dad@dadkvm:~$ systemd-analyze blame
2.006s postfix@-.service                                    
1.058s networking.service                                   
 212ms udisks2.service                                      
 193ms blueman-mechanism.service                            
 154ms apport-autoreport.service                            
 145ms apparmor.service                                     
 127ms accounts-daemon.service                              
 126ms dev-vda5.device                                      
 120ms iwatch.service                                       
  94ms networkd-dispatcher.service                          
  86ms systemd-resolved.service                             
  85ms NetworkManager-wait-online.service                   
  74ms avahi-daemon.service                                 
  74ms NetworkManager.service                               
  72ms lightdm.service                                      
  71ms systemd-timesyncd.service                            
  70ms plymouth-quit-wait.service                           
  65ms polkit.service                                       
  58ms systemd-logind.service                               
  55ms wpa_supplicant.service                               
  54ms user@1000.service                                    
  51ms apport.service                                       
  49ms ModemManager.service
```

I also attached a bootchart image but I think it needs some config work!

---

### Post by Quarkrad on 2021-10-01
I started the machine precisely at 17.55 - a few seconds I press Esc and on a black screen got:

/dev/vda5 clean, 336.......
-.mount
systemd-bootchart.service
...
...
...
boot-efi.mount


the boot process (i.e. looking at the screen) appears to hang at this point - before eventually booting to Desktop 1min 40secs later.   I then got an oouput from journalctl:

```
4e)
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0801] device (enp1s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0809] manager: NetworkManager state is now CONNECTING
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0815] device (enp1s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0823] device (enp1s0): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0828] dhcp4 (enp1s0): activation: beginning transaction (timeout in 45 seconds)
Oct 01 17:56:45 dadkvm avahi-daemon[466]: Joining mDNS multicast group on interface enp1s0.IPv6 with address fe80::95b1:8c51:e95a:90ee.
Oct 01 17:56:45 dadkvm avahi-daemon[466]: New relevant interface enp1s0.IPv6 for mDNS.
Oct 01 17:56:45 dadkvm avahi-daemon[466]: Registering new address record for fe80::95b1:8c51:e95a:90ee on enp1s0.*.
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0899] dhcp4 (enp1s0): option dhcp_lease_time      => '3600'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0899] dhcp4 (enp1s0): option domain_name_servers  => '192.168.122.1'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0899] dhcp4 (enp1s0): option expiry               => '1633111005'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): option host_name            => 'dadkvm'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): option ip_address           => '192.168.122.104'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): option next_server          => '192.168.122.1'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): option requested_broadcast_address => '1'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): option requested_domain_name => '1'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): option requested_domain_name_servers => '1'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): option requested_domain_search => '1'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): option requested_host_name  => '1'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): option requested_interface_mtu => '1'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): option requested_ms_classless_static_routes => '1'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): option requested_nis_domain => '1'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): option requested_nis_servers => '1'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): option requested_ntp_servers => '1'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): option requested_rfc3442_classless_static_routes => '1'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): option requested_root_path  => '1'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): option requested_routers    => '1'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): option requested_static_routes => '1'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): option requested_subnet_mask => '1'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): option requested_time_offset => '1'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): option requested_wpad       => '1'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): option routers              => '192.168.122.1'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): option subnet_mask          => '255.255.255.0'
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0900] dhcp4 (enp1s0): state changed unknown -> bound
Oct 01 17:56:45 dadkvm avahi-daemon[466]: Joining mDNS multicast group on interface enp1s0.IPv4 with address 192.168.122.104.
Oct 01 17:56:45 dadkvm avahi-daemon[466]: New relevant interface enp1s0.IPv4 for mDNS.
Oct 01 17:56:45 dadkvm avahi-daemon[466]: Registering new address record for 192.168.122.104 on enp1s0.IPv4.
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0912] device (enp1s0): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'managed')
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0926] device (enp1s0): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'managed')
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0929] device (enp1s0): state change: secondaries -> activated (reason 'none', sys-iface-state: 'managed')
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0935] manager: NetworkManager state is now CONNECTED_LOCAL
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0951] manager: NetworkManager state is now CONNECTED_SITE
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0955] policy: set 'eth' (enp1s0) as default for IPv4 routing and DNS
Oct 01 17:56:45 dadkvm systemd[1]: Started Bluetooth management mechanism.
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.0988] device (enp1s0): Activation: successful, device activated.
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.1000] manager: NetworkManager state is now CONNECTED_GLOBAL
Oct 01 17:56:45 dadkvm NetworkManager[473]: <info>  [1633107405.1054] manager: startup complete
Oct 01 17:56:45 dadkvm systemd[1]: Finished Network Manager Wait Online.
Oct 01 17:56:45 dadkvm nm-dispatcher[628]: postconf: fatal: open /etc/postfix/main.cf: No such file or directory
Oct 01 17:56:45 dadkvm avahi-daemon[466]: Server startup complete. Host name is dadkvm.local. Local service cookie is 765687134.
Oct 01 17:56:45 dadkvm systemd[1]: Finished Raise network interfaces.
Oct 01 17:56:45 dadkvm systemd[1]: Reached target Network.
Oct 01 17:56:45 dadkvm systemd[1]: Reached target Network is Online.
Oct 01 17:56:45 dadkvm systemd[1]: Starting LSB: disk temperature monitoring daemon...
Oct 01 17:56:45 dadkvm systemd[1]: Starting realtime filesystem monitoring program using inotify...
Oct 01 17:56:45 dadkvm systemd[1]: Starting Tool to automatically collect and submit kernel crash signatures...
Oct 01 17:56:45 dadkvm systemd[1]: Starting OpenVPN service...
Oct 01 17:56:45 dadkvm systemd[1]: Starting Postfix Mail Transport Agent (instance -)...
Oct 01 17:56:45 dadkvm systemd[1]: Condition check resulted in fast remote file copy program daemon being skipped.
Oct 01 17:56:45 dadkvm systemd[1]: Starting Permit User Sessions...
Oct 01 17:56:45 dadkvm systemd[1]: Started crash report submission daemon.
Oct 01 17:56:45 dadkvm systemd[1]: Starting Process error reports when automatic reporting is enabled...
Oct 01 17:56:45 dadkvm configure-instance.sh[643]: postconf: fatal: open /etc/postfix/main.cf: No such file or directory
Oct 01 17:56:45 dadkvm systemd[1]: Finished OpenVPN service.
Oct 01 17:56:45 dadkvm systemd[1]: Finished Permit User Sessions.
Oct 01 17:56:45 dadkvm systemd[1]: kerneloops.service: Found left-over process 646 (kerneloops) in control group while starting unit. Ignoring.
Oct 01 17:56:45 dadkvm systemd[1]: This usually indicates unclean termination of a previous run, or service implementation deficiencies.
Oct 01 17:56:46 dadkvm systemd[1]: Starting Light Display Manager...
Oct 01 17:56:46 dadkvm systemd[1]: Starting Hold until boot process finishes up...
Oct 01 17:56:46 dadkvm whoopsie[641]: [17:56:46] Using lock path: /var/lock/whoopsie/lock
Oct 01 17:56:46 dadkvm systemd[1]: Started LSB: disk temperature monitoring daemon.
Oct 01 17:56:46 dadkvm systemd[1]: Started Tool to automatically collect and submit kernel crash signatures.
Oct 01 17:56:46 dadkvm lightdm[656]: Seat type 'xlocal' is deprecated, use 'type=local' instead
Oct 01 17:56:46 dadkvm whoopsie[641]: [17:56:46] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/1
Oct 01 17:56:46 dadkvm whoopsie[641]: [17:56:46] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/1
Oct 01 17:56:46 dadkvm whoopsie[641]: [17:56:46] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/1
Oct 01 17:56:46 dadkvm systemd[1]: Received SIGRTMIN+21 from PID 227 (plymouthd).
Oct 01 17:56:46 dadkvm systemd[1]: plymouth-quit-wait.service: Succeeded.
Oct 01 17:56:46 dadkvm systemd[1]: Finished Hold until boot process finishes up.
Oct 01 17:56:46 dadkvm systemd[1]: Received SIGRTMIN+21 from PID 227 (plymouthd).
Oct 01 17:56:46 dadkvm systemd[1]: Starting Set console scheme...
Oct 01 17:56:46 dadkvm systemd[1]: Started Light Display Manager.
Oct 01 17:56:46 dadkvm systemd[1]: Finished Set console scheme.
Oct 01 17:56:46 dadkvm systemd[1]: Created slice system-getty.slice.
Oct 01 17:56:46 dadkvm systemd[1]: Started Getty on tty1.
Oct 01 17:56:46 dadkvm systemd[1]: Reached target Login Prompts.
Oct 01 17:56:46 dadkvm nm-dispatcher[678]: postconf: fatal: open /etc/postfix/main.cf: No such file or directory
Oct 01 17:56:46 dadkvm systemd[1]: Started realtime filesystem monitoring program using inotify.
Oct 01 17:56:46 dadkvm whoopsie-upload-all[645]: /var/crash/_usr_bin_marco.1000.crash already marked for upload, skipping
Oct 01 17:56:46 dadkvm whoopsie-upload-all[645]: /var/crash/_usr_bin_ubuntu-cleaner.1000.crash already marked for upload, skipping
Oct 01 17:56:46 dadkvm whoopsie-upload-all[645]: All reports processed
Oct 01 17:56:46 dadkvm systemd[1]: apport-autoreport.service: Succeeded.
Oct 01 17:56:46 dadkvm systemd[1]: Finished Process error reports when automatic reporting is enabled.
Oct 01 17:56:46 dadkvm lightdm[699]: pam_unix(lightdm-autologin:session): session opened for user dad by (uid=0)
Oct 01 17:56:46 dadkvm systemd[1]: Created slice User Slice of UID 1000.
Oct 01 17:56:46 dadkvm systemd[1]: Starting User Runtime Directory /run/user/1000...
Oct 01 17:56:46 dadkvm systemd-logind[504]: New session c1 of user dad.
Oct 01 17:56:46 dadkvm systemd[1]: Finished User Runtime Directory /run/user/1000.
Oct 01 17:56:46 dadkvm systemd[1]: Starting User Manager for UID 1000...
Oct 01 17:56:46 dadkvm systemd[704]: pam_unix(systemd-user:session): session opened for user dad by (uid=0)
Oct 01 17:56:46 dadkvm systemd[704]: Started Pending report trigger for Ubuntu Report.
Oct 01 17:56:46 dadkvm systemd[704]: Reached target Paths.
Oct 01 17:56:46 dadkvm systemd[704]: Reached target Timers.
Oct 01 17:56:46 dadkvm systemd[704]: Starting D-Bus User Message Bus Socket.
Oct 01 17:56:46 dadkvm systemd[704]: Listening on GnuPG network certificate management daemon.
Oct 01 17:56:46 dadkvm systemd[704]: Listening on GnuPG cryptographic agent and passphrase cache (access for web browsers).
Oct 01 17:56:46 dadkvm systemd[704]: Listening on GnuPG cryptographic agent and passphrase cache (restricted).
Oct 01 17:56:46 dadkvm systemd[704]: Listening on GnuPG cryptographic agent (ssh-agent emulation).
Oct 01 17:56:46 dadkvm systemd[704]: Listening on GnuPG cryptographic agent and passphrase cache.
Oct 01 17:56:46 dadkvm systemd[704]: Listening on debconf communication socket.
Oct 01 17:56:46 dadkvm systemd[704]: Listening on Sound System.
Oct 01 17:56:46 dadkvm systemd[704]: Listening on D-Bus User Message Bus Socket.
Oct 01 17:56:46 dadkvm systemd[704]: Reached target Sockets.
Oct 01 17:56:46 dadkvm systemd[704]: Reached target Basic System.
Oct 01 17:56:46 dadkvm systemd[1]: Started User Manager for UID 1000.
Oct 01 17:56:46 dadkvm systemd[1]: Started Session c1 of user dad.
Oct 01 17:56:46 dadkvm systemd[704]: Starting Sound Service...
Oct 01 17:56:46 dadkvm dbus-daemon[472]: [system] Activating via systemd: service name='org.freedesktop.RealtimeKit1' unit='rtkit-daemon.service' requested by ':1.29' (uid=1000 pid=710 comm="/usr/bin/pulseaudio --daemonize=no --log-target=jo" label="unconfined")
Oct 01 17:56:46 dadkvm systemd[1]: Starting RealtimeKit Scheduling Policy Service...
Oct 01 17:56:46 dadkvm dbus-daemon[472]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Oct 01 17:56:46 dadkvm systemd[1]: Started RealtimeKit Scheduling Policy Service.
Oct 01 17:56:46 dadkvm rtkit-daemon[717]: Successfully called chroot.
Oct 01 17:56:46 dadkvm rtkit-daemon[717]: Successfully dropped privileges.
Oct 01 17:56:46 dadkvm rtkit-daemon[717]: Successfully limited resources.
Oct 01 17:56:46 dadkvm rtkit-daemon[717]: Running.
Oct 01 17:56:46 dadkvm rtkit-daemon[717]: Canary thread running.
Oct 01 17:56:46 dadkvm rtkit-daemon[717]: Watchdog thread running.
Oct 01 17:56:46 dadkvm rtkit-daemon[717]: Successfully made thread 710 of process 710 owned by '1000' high priority at nice level -11.
Oct 01 17:56:46 dadkvm rtkit-daemon[717]: Supervising 1 threads of 1 processes of 1 users.
Oct 01 17:56:46 dadkvm systemd[704]: Started D-Bus User Message Bus.
Oct 01 17:56:46 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] AppArmor D-Bus mediation is enabled
Oct 01 17:56:46 dadkvm pulseaudio[710]: Disabling timer-based scheduling because running inside a VM.
Oct 01 17:56:46 dadkvm rtkit-daemon[717]: Supervising 1 threads of 1 processes of 1 users.
Oct 01 17:56:46 dadkvm rtkit-daemon[717]: Successfully made thread 762 of process 710 owned by '1000' RT at priority 5.
Oct 01 17:56:46 dadkvm rtkit-daemon[717]: Supervising 2 threads of 1 processes of 1 users.
Oct 01 17:56:46 dadkvm pulseaudio[710]: Disabling timer-based scheduling because running inside a VM.
Oct 01 17:56:46 dadkvm rtkit-daemon[717]: Supervising 2 threads of 1 processes of 1 users.
Oct 01 17:56:46 dadkvm rtkit-daemon[717]: Successfully made thread 764 of process 710 owned by '1000' RT at priority 5.
Oct 01 17:56:46 dadkvm rtkit-daemon[717]: Supervising 3 threads of 1 processes of 1 users.
Oct 01 17:56:46 dadkvm dbus-daemon[472]: [system] Activating via systemd: service name='org.bluez' unit='dbus-org.bluez.service' requested by ':1.33' (uid=1000 pid=710 comm="/usr/bin/pulseaudio --daemonize=no --log-target=jo" label="unconfined")
Oct 01 17:56:46 dadkvm systemd[1]: Condition check resulted in Bluetooth service being skipped.
Oct 01 17:56:46 dadkvm systemd[704]: Started Sound Service.
Oct 01 17:56:46 dadkvm systemd[704]: Reached target Main User Target.
Oct 01 17:56:46 dadkvm systemd[704]: Startup finished in 160ms.
Oct 01 17:56:46 dadkvm configure-instance.sh[897]: postconf: fatal: open /etc/postfix/main.cf: No such file or directory
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Activating via systemd: service name='org.gtk.vfs.Daemon' unit='gvfs-daemon.service' requested by ':1.6' (uid=1000 pid=711 comm="mate-session " label="unconfined")
Oct 01 17:56:47 dadkvm systemd[704]: Starting Virtual filesystem service...
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Successfully activated service 'org.gtk.vfs.Daemon'
Oct 01 17:56:47 dadkvm systemd[704]: Started Virtual filesystem service.
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Activating via systemd: service name='org.a11y.Bus' unit='at-spi-dbus-bus.service' requested by ':1.9' (uid=1000 pid=711 comm="mate-session " label="unconfined")
Oct 01 17:56:47 dadkvm systemd[704]: Starting Accessibility services bus...
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Successfully activated service 'org.a11y.Bus'
Oct 01 17:56:47 dadkvm systemd[704]: Started Accessibility services bus.
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Activating service name='ca.desrt.dconf' requested by ':1.6' (uid=1000 pid=711 comm="mate-session " label="unconfined")
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Successfully activated service 'ca.desrt.dconf'
Oct 01 17:56:47 dadkvm gnome-keyring-daemon[986]: couldn't access control socket: /run/user/1000/keyring/control: No such file or directory
Oct 01 17:56:47 dadkvm mate-session[711]: WARNING: Unable to find provider '' of required component 'dock'
Oct 01 17:56:47 dadkvm at-spi-bus-launcher[948]: dbus-daemon[948]: Activating service name='org.a11y.atspi.Registry' requested by ':1.0' (uid=1000 pid=711 comm="mate-session " label="unconfined")
Oct 01 17:56:47 dadkvm at-spi-bus-launcher[948]: dbus-daemon[948]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 01 17:56:47 dadkvm at-spi-bus-launcher[992]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Activating via systemd: service name='org.gtk.vfs.UDisks2VolumeMonitor' unit='gvfs-udisks2-volume-monitor.service' requested by ':1.16' (uid=1000 pid=990 comm="/usr/bin/mate-settings-daemon " label="unconfined")
Oct 01 17:56:47 dadkvm systemd[704]: Starting Virtual filesystem service - disk device monitor...
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Successfully activated service 'org.gtk.vfs.UDisks2VolumeMonitor'
Oct 01 17:56:47 dadkvm systemd[704]: Started Virtual filesystem service - disk device monitor.
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Activating via systemd: service name='org.gtk.vfs.GPhoto2VolumeMonitor' unit='gvfs-gphoto2-volume-monitor.service' requested by ':1.16' (uid=1000 pid=990 comm="/usr/bin/mate-settings-daemon " label="unconfined")
Oct 01 17:56:47 dadkvm systemd[704]: Starting Virtual filesystem service - digital camera monitor...
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Successfully activated service 'org.gtk.vfs.GPhoto2VolumeMonitor'
Oct 01 17:56:47 dadkvm systemd[704]: Started Virtual filesystem service - digital camera monitor.
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Activating via systemd: service name='org.gtk.vfs.GoaVolumeMonitor' unit='gvfs-goa-volume-monitor.service' requested by ':1.16' (uid=1000 pid=990 comm="/usr/bin/mate-settings-daemon " label="unconfined")
Oct 01 17:56:47 dadkvm systemd[704]: Starting Virtual filesystem service - GNOME Online Accounts monitor...
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Successfully activated service 'org.gtk.vfs.GoaVolumeMonitor'
Oct 01 17:56:47 dadkvm systemd[704]: Started Virtual filesystem service - GNOME Online Accounts monitor.
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Activating via systemd: service name='org.gtk.vfs.AfcVolumeMonitor' unit='gvfs-afc-volume-monitor.service' requested by ':1.16' (uid=1000 pid=990 comm="/usr/bin/mate-settings-daemon " label="unconfined")
Oct 01 17:56:47 dadkvm systemd[704]: Starting Virtual filesystem service - Apple File Conduit monitor...
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Successfully activated service 'org.gtk.vfs.AfcVolumeMonitor'
Oct 01 17:56:47 dadkvm systemd[704]: Started Virtual filesystem service - Apple File Conduit monitor.
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Activating via systemd: service name='org.gtk.vfs.MTPVolumeMonitor' unit='gvfs-mtp-volume-monitor.service' requested by ':1.16' (uid=1000 pid=990 comm="/usr/bin/mate-settings-daemon " label="unconfined")
Oct 01 17:56:47 dadkvm systemd[704]: Starting Virtual filesystem service - Media Transfer Protocol monitor...
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Successfully activated service 'org.gtk.vfs.MTPVolumeMonitor'
Oct 01 17:56:47 dadkvm systemd[704]: Started Virtual filesystem service - Media Transfer Protocol monitor.
Oct 01 17:56:47 dadkvm ModemManager[587]: <info>  [base-manager] couldn't check support for device '/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0': not supported by any plugin
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Activating service name='org.mate.panel.applet.WnckletFactory' requested by ':1.19' (uid=1000 pid=1011 comm="mate-panel " label="unconfined")
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Activating service name='org.mate.panel.applet.TrashAppletFactory' requested by ':1.19' (uid=1000 pid=1011 comm="mate-panel " label="unconfined")
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Activating service name='org.mate.panel.applet.BriskMenuFactory' requested by ':1.19' (uid=1000 pid=1011 comm="mate-panel " label="unconfined")
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Activating service name='org.mate.panel.applet.IndicatorAppletCompleteFactory' requested by ':1.19' (uid=1000 pid=1011 comm="mate-panel " label="unconfined")
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Activating service name='org.mate.panel.applet.NotificationAreaAppletFactory' requested by ':1.19' (uid=1000 pid=1011 comm="mate-panel " label="unconfined")
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Successfully activated service 'org.mate.panel.applet.TrashAppletFactory'
Oct 01 17:56:47 dadkvm spice-vdagent[1074]: vdagent started
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Successfully activated service 'org.mate.panel.applet.BriskMenuFactory'
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Successfully activated service 'org.mate.panel.applet.IndicatorAppletCompleteFactory'
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Successfully activated service 'org.mate.panel.applet.WnckletFactory'
Oct 01 17:56:47 dadkvm systemd[1]: Starting Agent daemon for Spice guests...
Oct 01 17:56:47 dadkvm systemd[1]: Started Agent daemon for Spice guests.
Oct 01 17:56:47 dadkvm spice-vdagent[1074]: No guest output map, using output index as display id
Oct 01 17:56:47 dadkvm spice-vdagent[1074]: No guest output map, using output index as display id
Oct 01 17:56:47 dadkvm spice-vdagent[1074]: No guest output map, using output index as display id
Oct 01 17:56:47 dadkvm spice-vdagent[1074]: No guest output map, using output index as display id
Oct 01 17:56:47 dadkvm spice-vdagentd[1098]: opening vdagent virtio channel
Oct 01 17:56:47 dadkvm kernel: input: spice vdagent tablet as /devices/virtual/input/input5
Oct 01 17:56:47 dadkvm spice-vdagent[1074]: Received Graphics Device Info:
Oct 01 17:56:47 dadkvm spice-vdagent[1074]: Device /dev/dri/card0 is at /sys/devices/pci0000:00/0000:00:01.0/drm/card0
Oct 01 17:56:47 dadkvm spice-vdagent[1074]: Found card '/sys/devices/pci0000:00/0000:00:01.0/drm/card0' with Vendor ID 0x100, Device ID 0x1b36
Oct 01 17:56:47 dadkvm spice-vdagentd[1098]: Set max clipboard: 104857600
Oct 01 17:56:47 dadkvm spice-vdagentd[1098]: Set max clipboard: 104857600
Oct 01 17:56:47 dadkvm spice-vdagent[1074]: Found matching X Output: name=Virtual-1 id=67
Oct 01 17:56:47 dadkvm spice-vdagent[1074]: Adding graphics device info: channel_id: 0 monitor_id: 0 device_address: pci/0000/01.0, device_display_id: 0 xrandr output ID: 67
Oct 01 17:56:47 dadkvm spice-vdagent[1074]: Unable to find a display id for output index 1)
Oct 01 17:56:47 dadkvm spice-vdagent[1074]: Unable to find a display id for output index 2)
Oct 01 17:56:47 dadkvm spice-vdagent[1074]: Unable to find a display id for output index 3)
Oct 01 17:56:47 dadkvm spice-vdagent[1074]: Received Graphics Device Info:
Oct 01 17:56:47 dadkvm spice-vdagent[1074]: Device /dev/dri/card0 is at /sys/devices/pci0000:00/0000:00:01.0/drm/card0
Oct 01 17:56:47 dadkvm spice-vdagent[1074]: Found card '/sys/devices/pci0000:00/0000:00:01.0/drm/card0' with Vendor ID 0x100, Device ID 0x1b36
Oct 01 17:56:47 dadkvm spice-vdagent[1074]: Found matching X Output: name=Virtual-1 id=67
Oct 01 17:56:47 dadkvm spice-vdagent[1074]: Adding graphics device info: channel_id: 0 monitor_id: 0 device_address: pci/0000/01.0, device_display_id: 0 xrandr output ID: 67
Oct 01 17:56:47 dadkvm spice-vdagent[1074]: Unable to find a display id for output index 1)
Oct 01 17:56:47 dadkvm spice-vdagent[1074]: Unable to find a display id for output index 2)
Oct 01 17:56:47 dadkvm spice-vdagent[1074]: Unable to find a display id for output index 3)
Oct 01 17:56:47 dadkvm dbus-daemon[472]: [system] Activating via systemd: service name='org.freedesktop.timedate1' unit='dbus-org.freedesktop.timedate1.service' requested by ':1.40' (uid=1000 pid=1080 comm="/usr/lib/x86_64-linux-gnu/indicator-datetime/indic" label="unconfined")
Oct 01 17:56:47 dadkvm systemd[1]: Starting Time & Date Service...
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Activating via systemd: service name='org.gnome.evolution.dataserver.Sources5' unit='evolution-source-registry.service' requested by ':1.33' (uid=1000 pid=1080 comm="/usr/lib/x86_64-linux-gnu/indicator-datetime/indic" label="unconfined")
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Activation via systemd failed for unit 'evolution-source-registry.service': Unit evolution-source-registry.service not found.
Oct 01 17:56:47 dadkvm dbus-daemon[472]: [system] Successfully activated service 'org.freedesktop.timedate1'
Oct 01 17:56:47 dadkvm systemd[1]: Started Time & Date Service.
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Successfully activated service 'org.mate.panel.applet.NotificationAreaAppletFactory'
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Activating via systemd: service name='org.gtk.vfs.Metadata' unit='gvfs-metadata.service' requested by ':1.29' (uid=1000 pid=1063 comm="/usr/lib/mate-indicator-applet/mate-indicator-appl" label="unconfined")
Oct 01 17:56:47 dadkvm systemd[704]: Starting Virtual filesystem metadata service...
Oct 01 17:56:47 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Successfully activated service 'org.gtk.vfs.Metadata'
Oct 01 17:56:47 dadkvm systemd[704]: Started Virtual filesystem metadata service.
Oct 01 17:56:47 dadkvm mate-session[711]: WARNING: Could not launch application 'ubuntu-mate-welcome-autostart.desktop': Unable to start application: Failed to execute child process “/snap/bin/ubuntu-mate-welcome” (No such file or directory)
Oct 01 17:56:47 dadkvm systemd[1]: postfix@-.service: Control process exited, code=exited, status=1/FAILURE
Oct 01 17:56:47 dadkvm systemd[1]: postfix@-.service: Failed with result 'exit-code'.
Oct 01 17:56:47 dadkvm systemd[1]: Failed to start Postfix Mail Transport Agent (instance -).
Oct 01 17:56:47 dadkvm systemd[1]: Condition check resulted in Postfix Mail Transport Agent being skipped.
Oct 01 17:56:47 dadkvm systemd[1]: Reached target Multi-User System.
Oct 01 17:56:47 dadkvm systemd[1]: Reached target Graphical Interface.
Oct 01 17:56:47 dadkvm systemd[1]: Starting Update UTMP about System Runlevel Changes...
Oct 01 17:56:47 dadkvm systemd[1]: systemd-update-utmp-runlevel.service: Succeeded.
Oct 01 17:56:47 dadkvm systemd[1]: Finished Update UTMP about System Runlevel Changes.
Oct 01 17:56:47 dadkvm systemd[1]: Startup finished in 1.539s (kernel) + 1min 34.566s (userspace) = 1min 36.105s.
Oct 01 17:56:48 dadkvm gnome-keyring-daemon[986]: The PKCS#11 component was already initialized
Oct 01 17:56:48 dadkvm systemd[1]: dmesg.service: Succeeded.
Oct 01 17:56:48 dadkvm gnome-keyring-daemon[986]: The Secret Service was already initialized
Oct 01 17:56:48 dadkvm brisk-menu[1049]: gdk_window_get_origin: assertion 'GDK_IS_WINDOW (window)' failed
Oct 01 17:56:48 dadkvm brisk-menu[1049]: gdk_window_get_origin: assertion 'GDK_IS_WINDOW (window)' failed
Oct 01 17:56:48 dadkvm NetworkManager[473]: <info>  [1633107408.1325] agent-manager: agent[35851f18c6706c38,:1.47/org.freedesktop.nm-applet/1000]: agent registered
Oct 01 17:56:48 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Activating service name='org.mate.ScreenSaver' requested by ':1.28' (uid=1000 pid=1049 comm="/usr/lib/x86_64-linux-gnu/brisk-menu//brisk-menu " label="unconfined")
Oct 01 17:56:48 dadkvm dbus-daemon[725]: [session uid=1000 pid=725] Successfully activated service 'org.mate.ScreenSaver'
Oct 01 17:56:48 dadkvm brisk-menu[1049]: Negative content width -10 (allocation 1, extents 5x6) while allocating gadget (node button, owner GtkToggleButton)
Oct 01 17:56:48 dadkvm brisk-menu[1049]: Negative content height -7 (allocation 1, extents 4x4) while allocating gadget (node button, owner GtkToggleButton)
Oct 01 17:56:48 dadkvm notification-ar[1064]: GDBus.Error:org.freedesktop.DBus.GLib.ErrorError: Method invoked for RegisterStatusNotifierHost returned FALSE but did not set error
Oct 01 17:56:48 dadkvm polkitd(authority=local)[499]: Registered Authentication Agent for unix-session:c1 (system bus name :1.49 [/usr/lib/x86_64-linux-gnu/polkit-mate/polkit-mate-authentication-agent-1], object path /org/mate/PolicyKit1/AuthenticationAgent, locale en_GB.UTF-8)
Oct 01 17:56:51 dadkvm spice-vdagent[1074]: vdagent_audio_playback_sync mute=no nchannels=2
Oct 01 17:56:51 dadkvm spice-vdagent[1074]: vdagent-audio: (playback-left) 65535 (%99.00)
Oct 01 17:56:51 dadkvm spice-vdagent[1074]: vdagent-audio: (playback-right) 65535 (%99.00)
Oct 01 17:56:51 dadkvm spice-vdagent[1074]: vdagent_audio_record_sync mute=no nchannels=2
Oct 01 17:56:51 dadkvm spice-vdagent[1074]: vdagent-audio: (capture-left) 65535 (%99.00)
Oct 01 17:56:51 dadkvm spice-vdagent[1074]: vdagent-audio: (capture-right) 65535 (%99.00)
Oct 01 17:56:56 dadkvm systemd[1]: NetworkManager-dispatcher.service: Succeeded.
Oct 01 17:57:11 dadkvm pulseaudio[710]: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Oct 01 17:57:11 dadkvm dbus-daemon[472]: [system] Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
Oct 01 17:57:15 dadkvm systemd-timesyncd[440]: Initial synchronization to time server 91.189.89.198:123 (ntp.ubuntu.com).
Oct 01 17:57:15 dadkvm systemd[1]: blueman-mechanism.service: Succeeded.
Oct 01 17:57:18 dadkvm systemd[1]: systemd-hostnamed.service: Succeeded.
Oct 01 17:57:18 dadkvm systemd[1]: systemd-timedated.service: Succeeded.

```

What is interesting to me is that the journal does not start until 17.56 .  Is my problem to do with **boot-efi.mount**?

---

### Post by Quarkrad on 2021-10-02
At last - and apologies for the time you have spent on this; although I did learn a number of things along the way.  My problem was nothing anybody could have 'seen' without spending a lot of time on my set up.  Yet another 'play thing' ( I guess potentially a common problem with VM machines).  For another project, I was looking backing up to a usb stick and had an entry in fstab that enabled this.  If the usb stick was not pugged in I got this long boot - looking for the usb.  Directly I commented out the fstab entry I booted in normal time.  Thank you again for your time. (I forgot about this fstab entry when I first noticed the slow boot).

---

### Post by MAFoElffen on 2021-10-02
LOL. You are not alone or "the first person" in that. 

I am gad that you tracked that down and that all is well now.

---

### Post by ajgreeny on 2021-10-02
Great news!
Can you now please use the **Thread Tools** at the top of this thread and mark it as **SOLVED**.
It is a great help to those searching the forum.

---

