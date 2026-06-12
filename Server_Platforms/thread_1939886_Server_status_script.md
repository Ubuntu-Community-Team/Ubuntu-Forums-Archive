---
title: "Server status script"
date: 2012-03-12
forum: Server Platforms
---

### Post by jmr423 on 2012-03-12
hey i would like a script that displays system load, hard drive usage, memory usage, swap usage, system temperature, processes, users accessing my website, users accessing ssh, and my ip address. Can anyone help me make this? I'm using ubuntu server edition 10.04.  Thanks in advance.

---

### Post by matt_symes on 2012-03-12
Hi

I can help get the ball rolling here..

Programs to use to get (some of the) required information

```
free       : Amount of memory and swap
sensors    : Temperatures
procinfo   : Lots of information from /proc
ifconfig   : current IP address
ps         : Snapshot of running processes
```

You will need to install

```
sudo apt-get install procinfo lm-sensors
```

EDIT: Here are some examples

Memory usage.

```
matthew@matthew-Aspire-7540:~$ free -m                                                                                                                                     
             total       used       free     shared    buffers     cached
Mem:          2758       2583        175          0        106        318
-/+ buffers/cache:       2158        600
Swap:         3592        151       3441
matthew@matthew-Aspire-7540:~$ 
```

Temperatures.

```
matthew@matthew-Aspire-7540:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +61.0°C  (crit = +98.0°C)
temp2:        +55.0°C  (crit = +98.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +61.5°C  (high = +70.0°C)

matthew@matthew-Aspire-7540:~$
```

procinfo supplies loads of information

```
matthew@matthew-Aspire-7540:~$ procinfo
Memory:        Total        Used        Free     Buffers                       
RAM:         2824496     2651528      172968      109652                       
Swap:        3678848      154672     3524176                                   

Bootup: Mon Mar 12 11:49:45 2012   Load average: 0.04 0.06 0.09 1/577 20334    

user  :   01:37:55.22  10.5%  page in :          2025380                       
nice  :   00:00:25.12   0.0%  page out:          2250179                       
system:   00:25:41.21   2.7%  page act:           938774                       
IOwait:   00:08:07.07   0.9%  page dea:           410586                       
hw irq:   00:00:00.73   0.0%  page flt:         21045094                       
sw irq:   00:00:22.48   0.0%  swap in :            17179                       
idle  :   13:23:54.58  85.8%  swap out:            48521                       
uptime:   09:31:30.04         context :         30730613                       

irq   0:    5770848  timer               irq  17:     204892  ehci_hcd:usb1, at
irq   1:      76160  i8042               irq  18:    1258888  ohci_hcd:usb5, oh
irq   7:          1                      irq  19:        306  ehci_hcd:usb2, sn
irq   8:          1  rtc0                irq  22:     357002  ahci             
irq   9:      66500  acpi                irq  40:          0  PCIe PME         
irq  12:    1729147  i8042               irq  41:          0  PCIe PME         
irq  16:       3999  ohci_hcd:usb3, oh   irq  42:     178543  eth0             

sda           141782r          101277w                                         

eth0        TX 9.54MiB       RX 135.41MiB     wlan0       TX 5.20MiB       RX 90.68MiB     
lo          TX 932.01KiB     RX 932.01KiB                                      
matthew@matthew-Aspire-7540:~$
```

ip addresses..

```
matthew@matthew-Aspire-7540:~$ ifconfig | grep "inet a"
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet addr:127.0.0.1  Mask:255.0.0.0
matthew@matthew-Aspire-7540:~$
```

top 10 processes

Top ten running commands with pids and user.

```
matthew@matthew-Aspire-7540:~$ ps -eo pcpu,pid,user | sort  -r | head -10
%CPU   PID USER
 8.8  3523 matthew
 3.0  2252 root
 2.1  2511 matthew
 1.8  2888 matthew
 1.3  2938 matthew
 0.4  2969 matthew
 0.3 20423 root
 0.2  2963 matthew
 0.2  2556 matthew
matthew@matthew-Aspire-7540:~$ 
```

Kind regards

---

### Post by matt_symes on 2012-03-12
Hi

> hard drive usage,

What do you mean by hard drive usage ? space available as in df or processes accessing the hard drive as iotop ?

df

```
matthew@matthew-Aspire-7540:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       9.3G  7.7G  1.2G  87% /
udev            1.4G  8.0K  1.4G   1% /dev
tmpfs           552M  992K  551M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.4G  352K  1.4G   1% /run/shm
/dev/sda8       9.8G  4.2G  5.2G  45% /home/matthew/my_documents
/dev/sda16       53G   48G  1.8G  97% /home/matthew/virtual_machines
/dev/sda3       9.3G  6.8G  2.1G  78% /home/matthew/sda3
/dev/sda5        43G   39G  2.2G  95% /home/matthew/storage
matthew@matthew-Aspire-7540:~$ 
```

iotop

```

Total DISK READ:       0.00 B/s | Total DISK WRITE:      18.93 K/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN     IO>    COMMAND                                                                                                      
  331 be/3 root        0.00 B/s   11.36 K/s  0.00 %  2.76 % [jbd2/sda2-8]
    1 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % init
    2 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kthreadd]
```
Kind regards

---

### Post by matt_symes on 2012-03-12
Hi


> users accessing ssh,

I think who may help here.

```
matthew@matthew-Aspire-7540:~$ who
matthew  pts/1        2012-03-12 21:38 (:1:S.0)
matthew@matthew-Aspire-7540:~$
```

> users accessing my website, 

Can you elaborate a bit more on this one ?

You can write a script to access these commands and format the information and write it a file.

The script could be called by cron once a minute ?

Kind regards

---

### Post by druhboruch on 2012-03-13
It is not exactly a script, but it just might be what you need.
```
sudo apt-get install phpsysinfo
```

---

### Post by aeiah on 2012-03-13
i used to use conky-cli with some of this kind of info for a couple of servers. just a tail of the backup log, cpu, bandwidth, hdd space

---

### Post by Habitual on 2012-03-13
You'll need/should have ssh keys installed and working for this.

```

#!/bin/bash
# Written by Habitual/JJ
clear
echo "Server Report:"
echo "Server date/time is" $(ssh -qi /path/to/key_rsa root@xxx.xx.xxx.xxx date +%c)
echo "Load Check is" $(ssh -qi /path/to/key_rsa  root@xxx.xx.xxx.xxx uptime | cut -c 33-62)
echo "hda1" $(ssh -qi /path/to/key_rsa  root@xxx.xx.xxx.xxx df -h  | grep dev)
echo "Last reboot was" $(ssh -qi /path/to/key_rsa root@xxx.xx.xxx.xxx reboot | head -1 | awk '{print $5 " "$6 " "$7 " "$8}'
echo "End Server Report"
#EOF

```

NOTE:
last reboot will be empty/void sometimes
If the server was rebooted on 2/28/2012
wtmp will cycle the /var/log/wtmp on the first,
it will be empty.

HTH.

---

### Post by matt_symes on 2012-03-13
Hi

> **Habitual said:**
> You'll need/should have ssh keys installed and working for this.

```

#!/bin/bash
# Written by Habitual/JJ
clear
echo "Server Report:"
echo "Server date/time is" $(ssh -qi /path/to/key_rsa root@xxx.xx.xxx.xxx date +%c)
echo "Load Check is" $(ssh -qi /path/to/key_rsa  root@xxx.xx.xxx.xxx uptime | cut -c 33-62)
echo "hda1" $(ssh -qi /path/to/key_rsa  root@xxx.xx.xxx.xxx df -h  | grep dev)
echo "Last reboot was" $(ssh -qi /path/to/key_rsa root@xxx.xx.xxx.xxx reboot | head -1 | awk '{print $5 " "$6 " "$7 " "$8}'
echo "End Server Report"
#EOF

```

NOTE:
last reboot will be empty/void sometimes
If the server was rebooted on 2/28/2012
wtmp will cycle the /var/log/wtmp on the first,
it will be empty.

HTH.

That's the type of thing i was thinking about, using cron to generate a file. I would not ssh into the server for each command. I generate a file using cron and write the output to a file. I would then SSH into the server and watch the file.

Personally i would export it as an html file (with maybe Javascript or PHP) that could be served by the web browser, but that would be dependent upon how frequently it needs to be updated. 

It would need protected access of course, but i have done similar things in the past.

Things like this are great learning exercises.

Kind regards

---

### Post by jmr423 on 2012-03-13
> **matt_symes said:**
> Hi



That's the type of thing i was thinking about, using cron to generate it.

Personally i would export it as an html file (with maybe Javascript or PHP) that could be served by the web browser, but that would be dependent upon how frequently it needs to be updated.

It would need protected access of course, but i have done similar things in the past.

Kind regards

I was thinking of making something that could be accessed via ssh so i could use geek tools on my mac laptop to have them displayed on my desktop at all times. I could set it up so it runs the script every 60 seconds. That being said, also having it displayed in a private html file would be amazing. I will play around with some of the scripts as soon as i can, i have exams this week.

---

### Post by Habitual on 2012-03-13
```

#!/bin/bash
# Written by Habitual/JJ
clear
echo "Server Report:"
echo "Server date/time is" $(ssh -qi /path/to/key_rsa root@xxx.xx.xxx.xxx date +%c)
echo "Load Check is" $(ssh -qi /path/to/key_rsa  root@xxx.xx.xxx.xxx uptime | cut -c 33-62)
echo "hda1" $(ssh -qi /path/to/key_rsa  root@xxx.xx.xxx.xxx df -h  | grep dev)
echo "Last reboot was" $(ssh -qi /path/to/key_rsa root@xxx.xx.xxx.xxx reboot | head -1 | awk '{print $5 " "$6 " "$7 " "$8}'
echo "End Server Report"
#EOF
```

save as ~/myserver.rpt

terminal >
```
crontab -e
```
and add entry for 
05 08 * * 6 /home/$user/myserver.rpt > /home/$user/serverreport.out

P.S. I don't ssh "into" anything personally, I let the script do that. :)
password-less ssh is one of the ways to get host info without having to ssh "into" anything.

P.P.S.
Is MAC compatible. :)

My source script actually does the work from my Icinga host using /usr/local/icinga/libexec/check_nrpe commands on the Icinga host and gives me the info to my desktop pc.
I sanitized this to use native bash-equivalent tools.

HTH.

---

### Post by hawkmage on 2012-03-13
Where are you getting your "reboot" executable?  The one that I have on my systems reboots the system.  

```
hawkmage@ubuntu:~$ reboot --help
Usage: reboot [OPTION]...
Reboot the system.

Options:
  -n, --no-sync               don't sync before reboot or halt
  -f, --force                 force reboot or halt, don't call shutdown(8)
  -p, --poweroff              switch off the power when called as halt
  -w, --wtmp-only             don't actually reboot or halt, just write wtmp record
  -q, --quiet                 reduce output to errors only
  -v, --verbose               increase output to include informational messages
      --help                  display this help and exit
      --version               output version information and exit

This command is intended to instruct the kernel to reboot or halt the system; when run without the -f option, or when in a system runlevel other than 0 or 6, it will actually
execute /sbin/shutdown.


Report bugs to <upstart-devel@lists.ubuntu.com>
hawkmage@ubuntu:~$ 
```

---

### Post by matt_symes on 2012-03-14
Hi

> **hawkmage said:**
> Where are you getting your "reboot" executable?  The one that I have on my systems reboots the system.  

```
hawkmage@ubuntu:~$ reboot --help
Usage: reboot [OPTION]...
Reboot the system.

Options:
  -n, --no-sync               don't sync before reboot or halt
  -f, --force                 force reboot or halt, don't call shutdown(8)
  -p, --poweroff              switch off the power when called as halt
  -w, --wtmp-only             don't actually reboot or halt, just write wtmp record
  -q, --quiet                 reduce output to errors only
  -v, --verbose               increase output to include informational messages
      --help                  display this help and exit
      --version               output version information and exit

This command is intended to instruct the kernel to reboot or halt the system; when run without the -f option, or when in a system runlevel other than 0 or 6, it will actually
execute /sbin/shutdown.


Report bugs to <upstart-devel@lists.ubuntu.com>
hawkmage@ubuntu:~$ 
```

A slight typo.

```
last | grep reboot | head -n 1
```

> P.S. I don't ssh "into" anything personally, I let the script do that. Very true :popcorn:

Personally, i would still generate the information on the server and redirect it into a file (or even database). This could be text file, html file, pdf file etc. I would use cron to generate the file at regular intervals. SSHing into the box would then pull out that file.

Storing the information on the server allows you to keep a history, if required, using a database or even files.  If the file is html, it can be served by the web server. Something similar to how ntop delivers it reports.

I wrote something very similar for someone. It would display up the amount of traffic going over a dd-wrt flashed router by IP address and mac address. It sat on the router and delivered ip address, mac address and download and upload traffic via html file.

I like your script :D. I am only trying to give the OP options depending on what they need to achieve.

It's quite possible i'm over engineering this ;)

Kind regards

---

