---
title: "Issue with launch vmware after after have upgraded from 14.04 to 16.04"
date: 2016-07-02
forum: Virtualisation
---

### Post by alexnsk777 on 2016-07-02
Hi,

I faced with problem launch vmware workstation 11 after have upgraded from 14.04 to 16.04. When I try to launch vmware service, I see the following:

root@mypc:~# /etc/init.d/vmware start
Starting VMware services:
[COLOR=red]   Virtual machine monitor                                            failed
[/COLOR]   Virtual machine communication interface                             done
   VM communication interface socket family                            done
   Blocking file system                                                done
[COLOR=red]   Virtual ethernet                                                   failed
[/COLOR]   VMware Authentication Daemon                                       done
root@mypc:~#

[LEFT]root@mypc:~# uname -a
Linux mypc 4.4.0-28-generic #47-Ubuntu SMP Fri Jun 24 10:09:13 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
root@mypc:~# 

root@mypc:~# /etc/init.d/vmware status
Module vmmon not loaded
Module vmnet not loaded
root@mypc:~#

Please help me to resolve this issue. Thank you very much in advance. 
[/LEFT]

---

### Post by MAFoElffen on 2016-07-02
After you did a release upgrade from 14.04 to 16.04... did you then do 
```

sudo apt-get update
sudo apt-get dist-upgrade

```
to apply any updates since the last release upgrade image?

---

### Post by skyway2 on 2016-08-13
I am also getting same problem

My vmware is :-> VMware Workstation 10.0.3 build-1895310
I upgraded too

Please help me
Thanks

---

### Post by MAFoElffen on 2016-08-13
Wait a minute. I just noticed that I missed something in your posts... 

Why are you two trying to start VMware Workstation via a commandline? (Is not called vmware... either vmware-cmd with switches or vmrun)
Why are you trying to start it as a service instead of as the software "application" that it is? (see commands above)

Not that I doubt you, but I do not see that listed anywhere in the VMware Doc's. I see it elsewhere, in a round about way...

EDIT-- AFter doing some more research and digging, I don't see /etc/init.d/vmware noted since around 2006... for autostarting VM's on boot. To do that you have to set Workstation up as a server, providing virtualization services. It used to be common practice to add a script in init-d to do that in upstart... The difference between 14.04 LTS and 16.04 LTS in upstart, is that now in 16.04, it uses systemd. Now you might have to convert your VM autosart script over to be compliant with systemd.

Was that a VMware supplied script or user script? Because this is what I find on converting the old autorun upstart scripts to systemd (from the Arch Linux Wiki):
> 
systemd services
(Optional) Instead of using /etc/init.d/vmware (start|stop|status|restart) and /usr/bin/vmware-usbarbitrator directly to manage the services, you may also use .service files (also available in the vmware-systemd-servicesAUR package, and also included in vmware-patchAUR):
/etc/systemd/system/vmware.service
```

[Unit]
Description=VMware daemon
Requires=vmware-usbarbitrator.service
Before=vmware-usbarbitrator.service
After=network.target


[Service]
ExecStart=/etc/init.d/vmware start
ExecStop=/etc/init.d/vmware stop
PIDFile=/var/lock/subsys/vmware
RemainAfterExit=yes


[Install]
WantedBy=multi-user.target

```
/etc/systemd/system/vmware-usbarbitrator.service
```

[Unit]
Description=VMware USB Arbitrator
Requires=vmware.service
After=vmware.service


[Service]
ExecStart=/usr/bin/vmware-usbarbitrator
ExecStop=/usr/bin/vmware-usbarbitrator --kill
RemainAfterExit=yes


[Install]
WantedBy=multi-user.target

```
Add this service as well, if you want to connect to your VMware Workstation installation from another Workstation Server Console:
/etc/systemd/system/vmware-workstation-server.service
```

[Unit]
Description=VMware Workstation Server
Requires=vmware.service
After=vmware.service


[Service]
ExecStart=/etc/init.d/vmware-workstation-server start
ExecStop=/etc/init.d/vmware-workstation-server stop
PIDFile=/var/lock/subsys/vmware-workstation-server


[Install]
WantedBy=multi-user.target

```


---

