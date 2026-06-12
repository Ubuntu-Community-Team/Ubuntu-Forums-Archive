---
title: "How to Schedule Unattended-Upgrades to Run Once a Month"
date: 2019-12-05
forum: Server Platforms
---

### Post by dnp60 on 2019-12-05
Hi Everyone,

I am trying to get Unattended-Upgrades to run on my Ubuntu 18.04 servers. I would like it to run
once a month (OnCalendar=Tue *-*-1..7 7:00:00). It's currently running every day. I am not sure 
how to modify the systemd timers to achieve this. Any help would be appreciated. I have been working with 
Ubuntu support since 10/22/19 and haven't been able to solve the problem.

```
# cat /etc/apt/apt.conf.d/50unattended-upgrades
Unattended-Upgrade::Allowed-Origins {
        "${distro_id}:${distro_codename}";
        "${distro_id}:${distro_codename}-security";
        // Extended Security Maintenance; doesn't necessarily exist for
        // every release and this system may not have it installed, but if
        // available, the policy for updates is such that unattended-upgrades
        // should also install from here by default.
        "${distro_id}ESM:${distro_codename}";
        "${distro_id}:${distro_codename}-updates";
//      "${distro_id}:${distro_codename}-proposed";
//      "${distro_id}:${distro_codename}-backports";
};
// List of packages to not update (regexp are supported)
Unattended-Upgrade::Package-Blacklist {
//      "vim";
//      "libc6";
//      "libc6-dev";
//      "libc6-i686";
};
Unattended-Upgrade::DevRelease "false";
Unattended-Upgrade::Mail "dnp@ams.org";
Unattended-Upgrade::Remove-Unused-Kernel-Packages "true";
Unattended-Upgrade::Remove-Unused-Dependencies "true";
Unattended-Upgrade::Automatic-Reboot "true";
Unattended-Upgrade::Automatic-Reboot-Time "now";
```

```
# cat /etc/apt/apt.conf.d/20auto-upgrades
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "7";
APT::Periodic::Unattended-Upgrade "1";
```
```

# cat /etc/apt/apt.conf.d/20auto-upgrades
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "7";
APT::Periodic::Unattended-Upgrade "1";
```

```
# cat /etc/systemd/system/apt-daily.timer                        
[Unit]
Description=Daily apt dailey upgrade activities

[Timer]
#DayOfWeek Year-Month-Day Hour:Minute:Second
OnCalendar=*-*-* 4:00:00
RandomizedDelaySec=10min
Persistent=true

[Install]
WantedBy=timers.target
```

```
# cat /lib/systemd/system/apt-daily-upgrade.timer
[Unit]
Description=Daily apt upgrade and clean activities
After=apt-daily.timer

[Timer]
OnCalendar=*-*-* 7:00
RandomizedDelaySec=20m
Persistent=true

[Install]
WantedBy=timers.target
```


```
# systemctl list-timers --all
NEXT                         LEFT          LAST                         PASSED       UNIT                       
Thu 2019-12-05 10:04:21 EST  4min 27s left Thu 2019-12-05 09:01:43 EST  58min ago    anacron.timer              
Thu 2019-12-05 17:07:51 EST  7h left       Thu 2019-12-05 07:06:54 EST  2h 52min ago motd-news.timer            
Fri 2019-12-06 04:05:14 EST  18h left      Thu 2019-12-05 04:06:43 EST  5h 53min ago apt-daily.timer            
Fri 2019-12-06 07:02:01 EST  21h left      Thu 2019-12-05 07:06:43 EST  2h 53min ago apt-daily-upgrade.timer    
Fri 2019-12-06 07:39:16 EST  21h left      Thu 2019-12-05 07:39:16 EST  2h 20min ago systemd-tmpfiles-clean.time
Mon 2019-12-09 00:00:00 EST  3 days left   Mon 2019-12-02 00:00:01 EST  3 days ago   fstrim.timer               
n/a                          n/a           n/a                          n/a          snap-repair.timer          
n/a                          n/a           n/a                          n/a          snapd.refresh.timer        
n/a                          n/a           n/a                          n/a          snapd.snap-repair.timer    
n/a                          n/a           n/a                          n/a          ureadahead-stop.timer   
```   

Thanks,
Dan

---

### Post by mörgæs on 2019-12-05
The idea behind unattended updates is that they can be run often. Why do you want to block this?

---

### Post by dnp60 on 2019-12-05
My management only wants to patch monthly. I can't convince them that more frequently is to our benefit.

---

### Post by LHammonds on 2019-12-06
> **dnp60 said:**
> My management only wants to patch monthly. I can't convince them that more frequently is to our benefit.
Sounds like management making the wrong choice.

However, I already install my servers without the option to do unattended upgrades...because I [run my own script](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=244).

I would find out "why" they are not wanting to do updates more frequently.  If they want to ensure the system does not reboot but one time per month (uptime metric reasons), the upgrade does not force a reboot.  You could have it check for an apply upgrades daily and on the 1st of every month, check if you see /var/run/reboot.required (iirc) and if you do, have the system auto-reboot.

If they want the server to remain "stable" because of no changes (avoid site failures due to deprecated functions being removed...like PHP does), then I could understand why they desire a frozen system for a while...unless that system is exposed to the Internet which makes the risk of it not being patch far worse than the potential of a patch breaking the system.

LHammonds

---

