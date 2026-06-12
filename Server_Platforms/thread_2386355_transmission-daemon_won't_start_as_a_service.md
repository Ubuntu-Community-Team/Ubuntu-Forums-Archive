---
title: "transmission-daemon won't start as a service"
date: 2018-03-04
forum: Server Platforms
---

### Post by m-dw on 2018-03-04
I'm running transmission-daemon as a service, installed from the transmissionbt PPA. It was upgraded from 2.92 to 2.93 today, but the upgrade didn't complete. The software seems to have been installed, but the service refuses to start. After installation the message I get is this:

```
Setting up transmission-daemon (2.93-1ubuntu1~16.04.1ubuntu1) ...
Job for transmission-daemon.service failed because the control process exited with error code. See "systemctl status transmission-daemon.service" and "journalctl -xe" for details.
invoke-rc.d: initscript transmission-daemon, action "start" failed.
&#9679; transmission-daemon.service - Transmission BitTorrent Daemon
   Loaded: loaded (/lib/systemd/system/transmission-daemon.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2018-03-04 22:31:39 GMT; 26ms ago
  Process: 1152 ExecStart=/usr/bin/transmission-daemon -f --log-error (code=exited, status=217/USER)
 Main PID: 1152 (code=exited, status=217/USER)


Mar 04 22:31:39 srvbuntu systemd[1]: Starting Transmission BitTorrent Daemon...
Mar 04 22:31:39 srvbuntu systemd[1152]: transmission-daemon.service: Failed at step USER spawning /usr/bin/transmission-daemon: No such process
Mar 04 22:31:39 srvbuntu systemd[1]: transmission-daemon.service: Main process exited, code=exited, status=217/USER
Mar 04 22:31:39 srvbuntu systemd[1]: Failed to start Transmission BitTorrent Daemon.
Mar 04 22:31:39 srvbuntu systemd[1]: transmission-daemon.service: Unit entered failed state.
Mar 04 22:31:39 srvbuntu systemd[1]: transmission-daemon.service: Failed with result 'exit-code'.
dpkg: error processing package transmission-daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 transmission-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
The daemon runs manually from the CLI invoked with sudo -u debian-transmission, so I'm guessing that systemd is having a problem dropping the privileges of the daemon after it starts. How can I fix this?

---

### Post by marcosbl2 on 2018-03-04
Exact same error and versions, in my case I must use the sudo -u debian-transmission + config path for it to work manually, update never finish

>  sudo -u debian-transmission transmission-daemon -g /etc/transmission-daemon/

---

### Post by o1dalex on 2018-03-05
The same here.

If I change in  */lib/systemd/system/transmission-daemon.service* user name from 'transmission' to 'debian-transmission' - it starts (the service  is available for some time), but it stops by systemctl timeout.

---

### Post by m-dw on 2018-03-05
I hadn't tried that... yes I get the same symptom.

---

### Post by Casperutz87 on 2018-03-05
Same problem here... :mad:

---

### Post by auveele on 2018-03-05
I've got the same problem since the last update to 2.93.
I tried to uninstall and purge the transmission packets, but the daemon still fails on start.
 :(

---

### Post by greven2 on 2018-03-05
Same here, hoping for a solution

---

### Post by hooghs on 2018-03-05
Yeah, also the same issue, appeared with the latest update.

---

### Post by mizled2 on 2018-03-05
Just wanted to comment and say I am also having this issue

---

### Post by pperp on 2018-03-05
Ahh...so I'm not the only one.  Same issue, same version here.

---

### Post by auveele on 2018-03-05
I've just published the issue in the Transmission Github.
I hope that we can find a solution for this.

[https://github.com/transmission/transmission/issues/537](https://github.com/transmission/transmission/issues/537)



**EDIT:**
I solved the problem. But installing a previous version: 2.84
I had a PPA repository for the transmission, and this version have a problem with the user and the init.d

I remove the transmission.list from the **/etc/apt/sources.list.d**
After that, I unistall the transmission with purge, and install again from Ubuntu repository.

Before doing that remember to make a copy of your config file: 
[B]/etc/transmission-daemon/settings.json

[/B]
I hope this solve your problem.

---

### Post by mizled2 on 2018-03-05
> **auveele said:**
> I've just published the issue in the Transmission Github.
I hope that we can find a solution for this.

[https://github.com/transmission/transmission/issues/537](https://github.com/transmission/transmission/issues/537)



**EDIT:**
I solved the problem. But installing a previous version: 2.84
I had a PPA repository for the transmission, and this version have a problem with the user and the init.d

I remove the transmission.list from the **/etc/apt/sources.list.d**
After that, I unistall the transmission with purge, and install again from Ubuntu repository.

Before doing that remember to make a copy of your config file: 
[B]/etc/transmission-daemon/settings.json

[/B]
I hope this solve your problem.

Downgrading is only a temporary solution and not a true resolution of the problem. I am staying on version 2.92 which is before the problem began. The issue is with 2.93.

---

### Post by santiagosnchez on 2018-03-05
I case someone would like to go back to version 2.92. Here is a way to do it that worked for me:

```
# remove transmission and ppa
sudo apt purge transmission*
sudo add-apt-repository --remove ppa:transmissionbt/ppa
sudo apt update
# get packages
wget [http://mirrors.kernel.org/ubuntu/pool/main/libe/libevent/libevent-2.1-6_2.1.8-stable-4_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/libe/libevent/libevent-2.1-6_2.1.8-stable-4_amd64.deb)
wget [http://security.ubuntu.com/ubuntu/pool/universe/t/transmission/transmission-cli_2.92-2ubuntu3.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/t/transmission/transmission-cli_2.92-2ubuntu3.1_amd64.deb)
wget [http://security.ubuntu.com/ubuntu/pool/universe/t/transmission/transmission-daemon_2.92-2ubuntu3.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/t/transmission/transmission-daemon_2.92-2ubuntu3.1_amd64.deb)
wget [http://security.ubuntu.com/ubuntu/pool/main/t/transmission/transmission-common_2.92-2ubuntu3.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/transmission/transmission-common_2.92-2ubuntu3.1_all.deb)
# install them
# first libevent
sudo dpkg -i libevent-2.1-6_2.1.8-stable-4_amd64.deb
sudo dpkg -i transmission-common_2.92-2ubuntu3.1_all.deb
sudo dpkg -i transmission-cli_2.92-2ubuntu3.1_amd64.deb
sudo dpkg -i transmission-daemon_2.92-2ubuntu3.1_amd64.deb
# check if transmission-daemon is running
sudo systemctl status transmission-daemon.service
# copy your settings
**# change user to your actual user name**
sudo systemctl stop transmission-daemon.service
sudo cp /home/**user**/.config/transmission-daemon/settings.json /etc/transmission-daemon/
sudo systemctl start transmission-daemon.service
```

---

### Post by jfabaf2 on 2018-03-05
I solved this issue creatting this file:

/etc/systemd/system/transmission-daemon.service.d/override.conf

with this content:
*[Service]*
*User=*
*Type=*
*Type=simple*
*User=debian-transmission*
*Group=debian-transmission*

then you must execute this in order to reload systemd config:
$systemctl daemon-reload

and finally you must execute:
$systemctl start transmission-daemon.service

After that transmission 2.93 works perfectly.

---

### Post by m-dw on 2018-03-05
Perfect, it has fixed it here for me also. Not sure I should mark the thread solved. The issue raised on the transmission GitHub page has been closed, with no work-around, but this intervention fixes the issue by saying "ignore a setting in the config file provided by the developer." Not an Ubuntu specific issue though.

---

### Post by #&amp;thj^% on 2018-03-05
> **m-dw said:**
> Not an Ubuntu specific issue though.
+1 No it's not a Ubuntu specific issue: Also affects Fedora, Arch, CentsOS Debian is all I saw so far! ;)
So far it seems to be a systemd permission problem. Regards

---

### Post by robfish on 2018-03-05
Yep. Me too.

---

### Post by talz1979 on 2018-03-06
Hi,

I have found the problem and posted the solution on github [https://github.com/transmission/transmission/issues/537#issuecomment-370660548](https://github.com/transmission/transmission/issues/537#issuecomment-370660548).

basically there are 3 options to solve the issue:
[LIST=1]
[*]build your own from source and do not forget to install libsystemd-dev before building.
[*]wait for the PPA maintainer to do the above and build a new version.
[*]change the type in ** /etc/systemd/system/transmission-daemon.service** from "notify" to "simple"
[/LIST]

have a great day,
Tal

---

### Post by mizled2 on 2018-03-06
> **talz1979 said:**
> Hi,

I have found the problem and posted the solution on github [https://github.com/transmission/transmission/issues/537#issuecomment-370660548](https://github.com/transmission/transmission/issues/537#issuecomment-370660548).

basically there are 3 options to solve the issue:
[LIST=1]
[*]build your own from source and do not forget to install libsystemd-dev before building.
[*]wait for the PPA maintainer to do the above and build a new version.
[*]change the type in ** /etc/systemd/system/transmission-daemon.service** from "notify" to "simple"
[/LIST]

have a great day,
Tal

Thank you for taking the time to detail the possible fixes. That definitely helps! I changed the service to "simple" for now until the PPA maintainer updates the package with a fix.

---

### Post by shadowyangweb on 2018-03-06
> **jfabaf2 said:**
> I solved this issue creatting this file:/etc/systemd/system/transmission-daemon.service.d/override.confwith this content:*[Service]**User=**Type=**Type=simple**User=debian-transmission**Group=debian-transmission*then you must execute this in order to reload systemd config:$systemctl daemon-reloadand finally you must execute:$systemctl start transmission-daemon.serviceAfter that transmission 2.93 works perfectly.Thank you so much!!! This fix my problem.

---

### Post by cobie2 on 2018-03-06
> **talz1979 said:**
> Hi,

I have found the problem and posted the solution on github [https://github.com/transmission/transmission/issues/537#issuecomment-370660548](https://github.com/transmission/transmission/issues/537#issuecomment-370660548).

basically there are 3 options to solve the issue:
[LIST=1]
[*]build your own from source and do not forget to install libsystemd-dev before building.
[*]wait for the PPA maintainer to do the above and build a new version.
[*]change the type in ** /etc/systemd/system/transmission-daemon.service** from "notify" to "simple"
[/LIST]

have a great day,
Tal

Hi Tal,

I tried using the 3rd option, however i'm unable to find [B]/etc/systemd/system/transmission-daemon.service
[/B]
By any chance do you mean **/lib/systemd/system/**[B]transmission-daemon.service 

[/B]If so I have edited the file from notify to simple; restarted the daemon it and looks okay.. however i'm unable access my transmission web GUI.

[B]Steve.
[/B]

---

### Post by cobie2 on 2018-03-06
I've solved this issue with the following:

updated config file [B]/lib/systemd/system/[B]transmission-daemon.service 

[/B][/B][Service]
Type=simple
User=debian-transmission
Group=debian-transmission

You may have the **User=transmission** just replace it with **User=debian-transmission**
By adding in both the user and group [B]debian-transmission
[/B]
Do a system reboot or:

$systemctl daemon-reload

Then 

$systemctl start transmission-daemon.service

This worked for me, hopefully this helps.

**Steve.**

---

### Post by dayn on 2018-03-06
Awesome. Worked for me. Thx!

---

### Post by naz7 on 2018-03-09
Thank you for the updates, this solved the issue of transmission not starting. However it no longer shows any of my transfers. Is there a way to reload those from the previous version without manually restarting them all?

---

### Post by cristian-agustoni on 2018-03-10
> **jfabaf2 said:**
> I solved this issue creatting this file:

/etc/systemd/system/transmission-daemon.service.d/override.conf

with this content:
*[Service]*
*User=*
*Type=*
*Type=simple*
*User=debian-transmission*
*Group=debian-transmission*

then you must execute this in order to reload systemd config:
$systemctl daemon-reload

and finally you must execute:
$systemctl start transmission-daemon.service

After that transmission 2.93 works perfectly.

Thanks a lot!

This solution fixed my issue!

Cheers

---

### Post by JohnyBeGood on 2018-03-15
> **cobie2 said:**
> I've solved this issue with the following:

updated config file [B]/lib/systemd/system/[B]transmission-daemon.service 

[/B][/B][Service]
Type=simple
User=debian-transmission
Group=debian-transmission

You may have the **User=transmission** just replace it with **User=debian-transmission**
By adding in both the user and group [B]debian-transmission
[/B]
Do a system reboot or:

$systemctl daemon-reload

Then 

$systemctl start transmission-daemon.service

This worked for me, hopefully this helps.

**Steve.**
This worked for me on 16.04
Thanks!

---

