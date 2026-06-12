---
title: "A Script to Check Your Distro for SSP/PIE/RELRO/ASLR/NX"
date: 2010-02-05
forum: Security
---

### Post by rookcifer on 2010-02-05
This is a cool script I came across while ago that is used to check the status of things like stack smashing protection, ASLR, the NX bit, RELRO, and PIE (it will also check for PaX).  It's a simple shell script (I looked over the script and it appears to be legit with no funny business).  Basically it checks all processes on your machine and shows you whether each of them is "hardened."

I ran it against my Ubuntu install and got the following output:

```
sudo ./checksec.sh --proc-all                                              
[sudo] password for chrono:                                                                            
* System-wide ASLR (kernel.randomize_va_space): On (Setting: 2)                                        

  Description - Make the addresses of mmap base, heap, stack and VDSO page randomized.
  This, among other things, implies that shared libraries will be loaded to random    
  addresses. Also for PIE-linked binaries, the location of code start is randomized.  

  See the kernel file 'Documentation/sysctl/kernel.txt' for more details.

* Does the CPU support NX: Yes

         COMMAND    PID RELRO             STACK CANARY           NX/PaX        PIE
            init      1 Full RELRO        Canary found           NX enabled    PIE enabled             
          auditd   1022 Partial RELRO     Canary found           NX enabled    PIE enabled             
         audispd   1024 Partial RELRO     Canary found           NX enabled    PIE enabled             
 hald-addon-acpi   1084 Partial RELRO     Canary found           NX enabled    No PIE                  
 hald-addon-stor   1090 Partial RELRO     Canary found           NX enabled    No PIE                  
 hald-addon-inpu   1091 Partial RELRO     Canary found           NX enabled    No PIE                  
           getty   1146 Partial RELRO     Canary found           NX enabled    No PIE                  
           getty   1148 Partial RELRO     Canary found           NX enabled    No PIE                  
           getty   1153 Partial RELRO     Canary found           NX enabled    No PIE                  
           getty   1154 Partial RELRO     Canary found           NX enabled    No PIE                  
           getty   1156 Partial RELRO     Canary found           NX enabled    No PIE                  
           acpid   1167 Partial RELRO     Canary found           NX enabled    No PIE                  
             atd   1170 Partial RELRO     Canary found           NX enabled    No PIE                  
            cron   1171 Partial RELRO     Canary found           NX enabled    No PIE                  
            Xorg   1225 Partial RELRO     Canary found           NX enabled    No PIE                  
             kdm   1625 Partial RELRO     Canary found           NX enabled    No PIE                  
        startkde   1647 Partial RELRO     Canary found           NX enabled    No PIE                  
           udevd  16815 Full RELRO        Canary found           NX enabled    PIE enabled             
           udevd  17298 Full RELRO        Canary found           NX enabled    PIE enabled             
 hald-addon-stor  17312 Partial RELRO     Canary found           NX enabled    No PIE                  
       ssh-agent   1785 Partial RELRO     Canary found           NX enabled    PIE enabled             
       gpg-agent   1786 Partial RELRO     Canary found           NX enabled    No PIE                  
     dbus-launch   1789 Partial RELRO     Canary found           NX enabled    No PIE                  
     dbus-daemon   1790 Partial RELRO     Canary found           NX enabled    PIE enabled             
       gpg-agent   1818 Partial RELRO     Canary found           NX enabled    No PIE                  
        kdeinit4   1832 Partial RELRO     Canary found           NX enabled    No PIE                  
       klauncher   1833 Partial RELRO     Canary found           NX enabled    No PIE                  
           kded4   1835 Partial RELRO     Canary found           NX enabled    No PIE                  
    kglobalaccel   1935 Partial RELRO     Canary found           NX enabled    No PIE                  
          master   2024 Full RELRO        Canary found           NX enabled    PIE enabled             
         privoxy   2033 Partial RELRO     Canary found           NX enabled    No PIE                  
            qmgr   2034 Full RELRO        Canary found           NX enabled    PIE enabled             
            ntpd   2060 Full RELRO        Canary found           NX enabled    PIE enabled             
       kwrapper4   2064 Partial RELRO     Canary found           NX enabled    No PIE                  
       ksmserver   2065 Partial RELRO     Canary found           NX enabled    No PIE                  
            kwin   2067 Partial RELRO     No canary found        NX enabled    No PIE                  
            nmbd   2083 Partial RELRO     Canary found           NX enabled    PIE enabled             
            smbd   2087 Partial RELRO     Canary found           NX enabled    PIE enabled             
            smbd   2088 Partial RELRO     Canary found           NX enabled    PIE enabled             
             tor   2101 Partial RELRO     Canary found           NX enabled    No PIE                  
          xinetd   2145 Full RELRO        Canary found           NX enabled    PIE enabled             
           cupsd   2186 Full RELRO        Canary found           NX enabled    PIE enabled             
  plasma-desktop   2188 Partial RELRO     Canary found           NX enabled    No PIE                  
        knotify4   2190 Partial RELRO     No canary found        NX enabled    No PIE                  
           getty   2246 Partial RELRO     Canary found           NX enabled    No PIE                  
      ksysguardd   2255 Partial RELRO     Canary found           NX enabled    No PIE                  
        gconfd-2  22580 Partial RELRO     Canary found           NX enabled    No PIE                  
         kwrited   2262 Partial RELRO     No canary found        NX enabled    No PIE                  
         kaccess   2268 Partial RELRO     Canary found           NX enabled    No PIE                  
         krunner   2276 Partial RELRO     Canary found           NX enabled    No PIE                  
   nepomukserver   2278 Partial RELRO     Canary found           NX enabled    No PIE                  
 nepomukservices   2283 Partial RELRO     No canary found        NX enabled    No PIE                  
 nepomukservices   2299 Partial RELRO     No canary found        NX enabled    No PIE                  
 nepomukservices   2300 Partial RELRO     No canary found        NX enabled    No PIE                  
 nepomukservices   2301 Partial RELRO     No canary found        NX enabled    No PIE                  
 nepomukservices   2302 Partial RELRO     No canary found        NX enabled    No PIE                  
 nepomukservices   2303 Partial RELRO     No canary found        NX enabled    No PIE                  
            kmix   2311 Partial RELRO     Canary found           NX enabled    No PIE                  
            kgpg   2315 Partial RELRO     Canary found           NX enabled    No PIE                  
          kopete   2317 Partial RELRO     Canary found           NX enabled    No PIE                  
          amarok   2319 Partial RELRO     No canary found        NX enabled    No PIE                  
          python   2337 Partial RELRO     Canary found           NX enabled    No PIE                  
 polkit-gnome-au   2338 Partial RELRO     No canary found        NX enabled    No PIE                  
          python   2340 Partial RELRO     Canary found           NX enabled    No PIE                  
         klipper   2342 Partial RELRO     Canary found           NX enabled    No PIE                  
 knetworkmanager   2347 Partial RELRO     No canary found        NX enabled    No PIE                  
         polkitd   2351 Partial RELRO     No canary found        NX enabled    No PIE                  
        kwalletd   2362 Partial RELRO     Canary found           NX enabled    No PIE                  
         ossxmix   2440 Partial RELRO     Canary found           NX enabled    No PIE                  
            smbd   2446 Partial RELRO     Canary found           NX enabled    PIE enabled             
         firefox  24545 Partial RELRO     Canary found           NX enabled    No PIE                  
   mount.ntfs-3g  25120 Partial RELRO     Canary found           NX enabled    No PIE                  
          pickup  26502 Full RELRO        No canary found        NX enabled    PIE enabled             
        kio_file  26871 Partial RELRO     Canary found           NX enabled    No PIE                  
     kio_desktop  27039 Partial RELRO     Canary found           NX enabled    No PIE                  
         dolphin  27041 Partial RELRO     No canary found        NX enabled    No PIE                  
       kio_trash  27043 Partial RELRO     Canary found           NX enabled    No PIE                  
        kio_file  27044 Partial RELRO     Canary found           NX enabled    No PIE                  
        kio_file  27046 Partial RELRO     Canary found           NX enabled    No PIE                  
        kio_file  27047 Partial RELRO     Canary found           NX enabled    No PIE                  
   kio_thumbnail  27048 Partial RELRO     Canary found           NX enabled    No PIE                  
   kio_thumbnail  27049 Partial RELRO     Canary found           NX enabled    No PIE                  
        kio_file  27058 Partial RELRO     Canary found           NX enabled    No PIE                  
         konsole  27068 Partial RELRO     Canary found           NX enabled    No PIE                  
            bash  27070 Partial RELRO     Canary found           NX enabled    No PIE                  
 kpackagekitsmar   2722 Partial RELRO     No canary found        NX enabled    No PIE                  
           gvfsd   2983 Partial RELRO     Canary found           NX enabled    No PIE
 gvfs-gdu-volume   2997 Partial RELRO     Canary found           NX enabled    No PIE
 devkit-disks-da   2999 Partial RELRO     Canary found           NX enabled    No PIE
 devkit-disks-da   3000 Partial RELRO     Canary found           NX enabled    No PIE
 gvfs-gphoto2-vo   3003 Partial RELRO     Canary found           NX enabled    No PIE
 upstart-udev-br    497 Full RELRO        Canary found           NX enabled    PIE enabled
           udevd    499 Full RELRO        Canary found           NX enabled    PIE enabled
              dd    845 Partial RELRO     Canary found           NX enabled    No PIE
        rsyslogd    848 Partial RELRO     Canary found           NX enabled    No PIE
     dbus-daemon    862 Partial RELRO     Canary found           NX enabled    PIE enabled
            hald    870 Partial RELRO     Canary found           NX enabled    No PIE
    avahi-daemon    871 Partial RELRO     Canary found           NX enabled    No PIE
    avahi-daemon    872 Partial RELRO     Canary found           NX enabled    No PIE
  NetworkManager    873 Partial RELRO     Canary found           NX enabled    No PIE
             kdm    874 Partial RELRO     Canary found           NX enabled    No PIE
   modem-manager    879 Partial RELRO     Canary found           NX enabled    No PIE
       kio_trash   8835 Partial RELRO     Canary found           NX enabled    No PIE
        kio_file   8836 Partial RELRO     Canary found           NX enabled    No PIE
        kio_file   8837 Partial RELRO     Canary found           NX enabled    No PIE
        kio_file   8858 Partial RELRO     Canary found           NX enabled    No PIE
             ark   8863 Partial RELRO     No canary found        NX enabled    No PIE
 console-kit-dae    910 Partial RELRO     Canary found           NX enabled    No PIE
     hald-runner    975 Partial RELRO     No canary found        NX enabled    No PIE
  wpa_supplicant    982 Partial RELRO     Canary found           NX enabled    No PIE
        dhclient    983 Full RELRO        Canary found           NX enabled    PIE enabled
```

As you can see, it says at the top that I have ASLR (setting: 2) turned on.  It also says my CPU supports the NX bit (almost all x86 64 bit processors do).  Below that it shows each process and what hardening features are enabled for it.

You can download the script [here]("http://www.trapkit.de/tools/checksec.html").  Simply download it, make it executable and then run:

```
sudo ./checksec.sh --proc-all
```

A very handy little tool.

(Again, it is trustworthy.  Look at the website and you will see it is from Tobias Klein, a well-respected Linux security researcher).

---

