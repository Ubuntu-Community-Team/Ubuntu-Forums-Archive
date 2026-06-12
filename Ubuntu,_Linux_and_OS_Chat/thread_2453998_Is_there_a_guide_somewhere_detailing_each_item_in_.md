---
title: "Is there a guide somewhere detailing each item in the startup applications app?"
date: 2020-11-20
forum: Ubuntu, Linux and OS Chat
---

### Post by user1397 on 2020-11-20
I recently realized that for the life of me I can't find any good documentation on what each startup item exactly is/does (in the Ubuntu startup applications app).  Some are obvious but others not as much, and I think it would be helpful to keep an up-to-date guide on which startup items are safe to disable and which ones are more critical (would be good for new users and seasoned users who just want a quick and dirty guide).  If there is nothing out there, I'd be interested in doing the research myself and posting it somewhere (most likely the community wiki).

I am aware that to see all the hidden startup items, you have to execute this command:
```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop
```

Thanks in advance.

---

### Post by TheFu on 2020-11-21
Everything is on your system already.  Start in /etc/  then use the manpages for each command configured to run there.

Every system is a little different, so there are different things that get started. It depends on the packages installed.
As for what each does, that's constantly changing due to the millions of programmers around the world working on the code. From week to week, packages don't change too much, but if you look from release to release or over multiple releases, they can.

What I consider safe to disable would be considered critical by many people.  Some things I remove/purge or disable/mask:
[LIST]
[*] nano
[*] systemd-resolved
```
$ sudo systemctl status systemd-resolved
&#9679; systemd-resolved.service
     Loaded: **masked** (Reason: Unit systemd-resolved.service is masked.)
     Active: inactive (dead)
```
[*] resolvconf
[*] iscsi stuff
[*] all bluetooth stuff
[*] avahi (everything)
[*] gedit
[*] ibus
[*] update-notifier (everything)
[/LIST]

This is a large project.
```
$ dpkg -l |egrep -v '^ii  lib'|wc -l
992
```
There are 1000 packages installed on my minimal 20.04 desktop, not counting libraries. How much detail do you really want to replicate or will the **apropos** output be sufficient?
```
$ apropos thunderbird
thunderbird (1)      - thunderbird - Mail User Agent (MUA) and newsgroup/RSS clie..
$ apropos systemd-resolved
systemd-resolved (8) - Network Name Resolution manager
systemd-resolved.service (8) - Network Name Resolution manager

```
The manpages will have much more detail, but GUI program manpages have really stopped being too useful. 

What about all the non-GUI things that cause slow booting or eat memory?
```
$ systemd-analyze critical-chain 
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @8.925s
&#9492;&#9472;multi-user.target @8.924s
  &#9492;&#9472;postfix.service @8.916s +5ms
    &#9492;&#9472;postfix@-.service @3.463s +5.451s
      &#9492;&#9472;basic.target @3.243s
        &#9492;&#9472;sockets.target @3.243s
          &#9492;&#9472;snapd.socket @3.241s +1ms
            &#9492;&#9472;sysinit.target @3.235s
              &#9492;&#9472;systemd-timesyncd.service @2.928s +307ms
                &#9492;&#9472;systemd-tmpfiles-setup.service @2.692s +233ms
                  &#9492;&#9472;local-fs.target @2.672s
                    &#9492;&#9472;run-user-1000.mount @5.010s
                      &#9492;&#9472;swap.target @2.302s
                        &#9492;&#9472;dev-vgubuntu\x2dmate-swap_1.swap @2.278s +23ms
                          &#9492;&#9472;dev-dm\x2d1.device @2.276s
```
I consider postfix absolutely critical on all my systems, but average people wouldn't be interested in sending email through an MTA.  Anyway, taking less than 9 seconds to boot is pretty great, yes?  Trust me, that system boot speed is not normal.

Or did I completely miss what you'd hoped to accomplish?

I'm curious. How do you plan to update this Guide for the next 5 years?  For example, systemd is constantly changing. Soon, we'll be forced to have portable HOME directories.  And they sneak in things like systemd-timesyncd that aren't really announced outside the time-keeping and systemd crowds.

---

### Post by SeijiSensei on 2020-11-21
Are you desperate for free space? If not, don't bother. 

"sudo systemctl list-units" will list all the services managed by systemd and their current statuses. Here's snippet from my Kubuntu 20.04 machine.

```

  apache2.service   loaded active running   The Apache HTTP Server  
  apparmor.service  loaded active exited    Load AppArmor profiles  
  apport.service    loaded active exited    LSB: automatic crash report generation      
  avahi-daemon.service        loaded active running   Avahi mDNS/DNS-SD Stack 
  bluetooth.service loaded active running   Bluetooth service       
  colord.service    loaded active running   Manage, Install and Generate Color Profiles 
  console-setup.service       loaded active exited    Set console font and keymap       
  cron.service      loaded active running   Regular background program processing daemon
  cups-browsed.service        loaded active running   Make remote CUPS printers available locally 
  cups.service      loaded active running   CUPS Scheduler
  dbus.service      loaded active running   D-Bus System Message Bus
  finalrd.service   loaded active exited    Create final runtime dir for shutdown pivot root      
  grub-common.service         loaded active exited    LSB: Record successful boot for GRUB        
  haveged.service   loaded active running   Entropy daemon using the HAVEGE algorithm   
  irqbalance.serviceloaded active running   irqbalance daemon       
  kerneloops.serviceloaded active running   Tool to automatically collect and submit kernel crash signatures
  keyboard-setup.service      loaded active exited    Set the console keyboard layout   
  kmod-static-nodes.service   loaded active exited    Create list of static device nodes for the current kernel       
  ModemManager.service        loaded active running   Modem Manager 
  mysql.service     loaded active running   MySQL Community Server  
  networkd-dispatcher.service loaded active running   Dispatcher daemon for systemd-networkd      
  NetworkManager-wait-online.service    loaded active exited    Network Manager Wait Online       
  NetworkManager.service      loaded active running   Network Manager         
  nvidia-persistenced.service loaded active running   NVIDIA Persistence Daemon         
 
```

See [man systemctl]("http://manpages.ubuntu.com/manpages/focal/man1/systemctl.1.html") for more details.

---

### Post by user1397 on 2020-11-21
Thanks for the detailed response as always TheFu.  I really was only asking about the GUI app called "Startup Applications" in stock Ubuntu w/ Gnome, and all the entries mentioned in there (perhaps I wasn't clear enough with that in my original post).  

Some entries in there are pretty self explanatory and some others are not as much.  For example, "Orca Screen Reader" is an accessibility app, and doesn't need further explanation, pretty self explanatory and most users can disable this unless they have a disability and need it.  However, say,  "AT-SPI D-Bus Bus" is not immediately evident what it is without doing more research (and think about especially less experienced users and the confusion they would have when seeing this entry).

---

