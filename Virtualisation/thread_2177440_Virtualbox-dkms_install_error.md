---
title: "Virtualbox-dkms install error"
date: 2013-09-28
forum: Virtualisation
---

### Post by JonasDeMoor on 2013-09-28
Hello,

I'm running Ubuntu 12.04.3. Whenever I want to install Virtualbox, a system error pops up when Virtualbox is installed. Virtualbox itself installed fine, but it's the virtualbox-dkms that won't install properly. 
I tried installing it with both the Software Centre and Synaptic. Same result.

Then I tried installing virtualbox-dkms via the terminal after removing it first: 
```
jonas@jonas-desktop:~$ sudo apt-get install virtualbox-dkms Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  virtualbox-dkms
0 pakketten opgewaardeerd, 1 pakketten nieuw geïnstalleerd, 0 te verwijderen en 0 niet opgewaardeerd.
Er moeten 0 B/676 kB aan archieven opgehaald worden.
Door deze operatie zal er 3.899 kB extra schijfruimte gebruikt worden.
Selecting previously unselected package virtualbox-dkms.
(Database inlezen ... 237176 files and directories currently installed.)
Uitpakken van virtualbox-dkms (uit .../virtualbox-dkms_4.1.12-dfsg-2ubuntu0.3_all.deb) ...
Instellen van virtualbox-dkms (4.1.12-dfsg-2ubuntu0.3) ...
Loading new virtualbox-4.1.12 DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-31-generic
Building initial module for 3.8.0-31-generic
Error! Bad return status for module build on kernel: 3.8.0-31-generic (x86_64)
Consult /var/lib/dkms/virtualbox/4.1.12/build/make.log for more information.
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                            * No suitable module for running kernel found
                                                                         [fail]
invoke-rc.d: initscript virtualbox, action "restart" failed.
```

It seems it can't build a module for the current kernel. I'm running the default kernel, so no custom compiled one or something.


Does anyone have a solution for this?

Thank you in advance.

---

### Post by TheFu on 2013-09-28
I take it that you have the generic header files loaded and build-essentials packages?  
If, OTOH, you installed the header files using `uname -r`, then that is what is missing.

---

### Post by JonasDeMoor on 2013-10-02
> **TheFu said:**
> I take it that you have the generic header files loaded and build-essentials packages?  
If, OTOH, you installed the header files using `uname -r`, then that is what is missing.

Hello, sorry for the late reply: I have been busy lately. 

I checked in synaptic, I currently have these packeges installed:
[LIST]
[*]linux-headers-3.8.0-29-generic, linux-headers-3.8.0-30-generic, linux-headers-3.8.0-31-generic,linux-headers-generic-lts-raring
[*]build-essential
[/LIST]

The header files were already installed; I didn't install it with uname -r (as far as I know).
I don't have virtualbox installed because of the errors and it doesn't work without the dkms modules.

---

### Post by JonasDeMoor on 2013-10-05
I solved it by adding a PPA which contains backports of the latest Virtualbox packages . This solves the problem: now virtualbox-dkms is able to build a module for the running kernel (3.8.*). Marked thread as SOLVED.

PPA: [https://launchpad.net/~debfx/+archive/virtualbox](https://launchpad.net/~debfx/+archive/virtualbox)

---

