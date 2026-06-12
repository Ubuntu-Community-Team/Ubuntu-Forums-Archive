---
title: "Virtualized installation: Time has been changed in syslog. Two time sources?"
date: 2016-03-06
forum: Virtualisation
---

### Post by gijs007 on 2016-03-06
I'm running ubuntu 15.10 server in Hyper-V and noticed that in my syslog I have entries like these:
> Mar  6 13:15:09 london systemd[1]: Time has been changed
Mar  6 13:15:09 london systemd[2174]: Time has been changed
Mar  6 13:15:04 london systemd[2174]: Time has been changed


> ar  6 14:32:41 france systemd[1]: Time has been changed
Mar  6 14:32:46 france systemd[1525]: Time has been changed
Mar  6 14:32:46 france systemd[1]: Time has been changed
Mar  6 14:32:51 france systemd[1525]: Time has been changed
Mar  6 14:32:51 france systemd[1]: Time has been changed
Mar  6 14:32:56 france systemd[1525]: Time has been changed
Mar  6 14:32:56 france systemd[1]: Time has been changed
Mar  6 14:33:01 france systemd[1525]: Time has been changed
Mar  6 14:33:01 france systemd[1]: Time has been changed
Mar  6 14:33:06 france systemd[1525]: Time has been changed
Mar  6 14:33:06 france systemd[1]: Time has been changed
Mar  6 14:33:11 france systemd[1525]: Time has been changed
Mar  6 14:33:11 france systemd[1]: Time has been changed
Mar  6 14:33:16 france systemd[1525]: Time has been changed
Mar  6 14:33:16 france systemd[1]: Time has been changed
Mar  6 14:33:21 france systemd[1525]: Time has been changed


I believe something might be wrong.
I think this might be happening because Linux updates the system time from a timeserver and also receives the time from the host OS(Windows)/Hyper-V.

I have installed the linux-cloud-tools-common and linux-cloud-tools-virtual packges.

I already tried disabling the NTP timeservices with the following commands:
sudo update-rc.d -f ntp remove
sudo timedatectl set-ntp 0

Is this indeed an error where the system gets the time from two sources? If so how can I prevent this? I believe best practises are to only use the host OS time and date.

---

### Post by MAFoElffen on 2016-03-07
From a cmd window on your Win Host, please post the results of 
```

w32tm /query /configuration

```

---

### Post by houstonbofh on 2016-03-08
By default, Windows pulls time from time.microsoft.com and Ubuntu does not. :)  So they are fighting.  Set the to the same server.  The file for Ubuntu is here. /etc/default/ntpdate

---

### Post by gijs007 on 2016-03-14
> **MAFoElffen said:**
> From a cmd window on your Win Host, please post the results of 
```

w32tm /query /configuration

```
This outputs: The following error occurred: The service has not been started. (0x80070426)

When I start the service Windows Time it outputs:
```
[Configuration]

EventLogFlags: 2 (Local)
AnnounceFlags: 10 (Local)
TimeJumpAuditOffset: 28800 (Local)
MinPollInterval: 10 (Local)
MaxPollInterval: 15 (Local)
MaxNegPhaseCorrection: 54000 (Local)
MaxPosPhaseCorrection: 54000 (Local)
MaxAllowedPhaseOffset: 1 (Local)

FrequencyCorrectRate: 4 (Local)
PollAdjustFactor: 5 (Local)
LargePhaseOffset: 50000000 (Local)
SpikeWatchPeriod: 900 (Local)
LocalClockDispersion: 10 (Local)
HoldPeriod: 5 (Local)
PhaseCorrectRate: 1 (Local)
UpdateInterval: 360000 (Local)


[TimeProviders]

NtpClient (Local)
DllName: C:\Windows\system32\w32time.dll (Local)
Enabled: 1 (Local)
InputProvider: 1 (Local)
AllowNonstandardModeCombinations: 1 (Local)
ResolvePeerBackoffMinutes: 15 (Local)
ResolvePeerBackoffMaxTimes: 7 (Local)
CompatibilityFlags: 2147483648 (Local)
EventLogFlags: 1 (Local)
LargeSampleSkew: 3 (Local)
SpecialPollInterval: 604800 (Local)
Type: NTP (Local)
NtpServer: time.windows.com,0x9 (Local)

VMICTimeProvider (Local)
DllName: C:\Windows\System32\vmictimeprovider.dll (Local)
Enabled: 1 (Local)
InputProvider: 1 (Local)
NtpServer (Local)
DllName: C:\Windows\system32\w32time.dll (Local)
Enabled: 0 (Local)
InputProvider: 0 (Local)
```

> **houstonbofh said:**
> By default, Windows pulls time from time.microsoft.com and Ubuntu does not. :)  So they are fighting.  Set the to the same server.  The file for Ubuntu is here. /etc/default/ntpdate
I see, that's why I tried to disable the time service in Ubuntu. So that it only gets the time from Hyper-V. Is it not possible to disable NTP in Ubuntu except for the time it gets from the host? (Also why doesn't this happen automatically? Isn't Ubuntu aware of it running inside a Hyper-V VM?)

---

### Post by MAFoElffen on 2016-03-15
When using Linux servers, I use ntp client to my ntp server to sync the times ... but a Linux guest inside a hyper-v guest is talking different languages. For them to talk the same language and work together...

Dl the [Linux Integration Services iso]("https://www.microsoft.com/en-us/download/details.aspx?id=46842") (<-- Link to Version 4.0). Mount it to the virtual cd of the Linux VM...

```

sudo su
mount /dev/cdrom /mnt
mkdir ~/linux_is
cp –R /mnt/* ~/linux_is
cd /linux_is/
make
make install
umount /mnt
shutdown -r now

```
Reboot VM

Run this as root to verify it worked
```

sudo lsmod | grep vsc

```
After that I should take time from the Windows Time source (in your case, the hyper-v host)

---

### Post by gijs007 on 2016-03-16
> **MAFoElffen said:**
> When using Linux servers, I use ntp client to my ntp server to sync the times ... but a Linux guest inside a hyper-v guest is talking different languages. For them to talk the same language and work together...

Dl the [Linux Integration Services iso]("https://www.microsoft.com/en-us/download/details.aspx?id=46842") (<-- Link to Version 4.0). Mount it to the virtual cd of the Linux VM...

```

sudo su
mount /dev/cdrom /mnt
mkdir ~/linux_is
cp –R /mnt/* ~/linux_is
cd /linux_is/
make
make install
umount /mnt
shutdown -r now

```
Reboot VM

Run this as root to verify it worked
```

sudo lsmod | grep vsc

```
After that I should take time from the Windows Time source (in your case, the hyper-v host)

I've used step 6 from: [https://technet.microsoft.com/en-us/library/dn531029.aspx](https://technet.microsoft.com/en-us/library/dn531029.aspx)
Which I believe is the current best practice. Using the iso image is for users of old kernels ([https://technet.microsoft.com/en-us/library/dn531030.aspx](https://technet.microsoft.com/en-us/library/dn531030.aspx)).

lsmod outputs:
```
gijs@london:~$ sudo lsmod | grep vsc
hv_netvsc              36864  0
hv_storvsc             24576  3
hv_vmbus               65536  7 hv_balloon,hyperv_keyboard,hv_netvsc,hid_hyperv,hv_utils,hyperv_fb,hv_storvsc

```

I believe the system is using the time from the Hyper-V host, but it's also getting the time from NTP which causes these messages in the log files.

---

### Post by MAFoElffen on 2016-03-16
Well then. Check for the existence of the file /etc/ntp.conf. If it does not install ntp. If so then edit the ntp.conf file
```

restrict 202.54.1.5 mask 255.255.255.245 nomodify notrap noquery
server 202.54.1.5

restrict default kod nomodify notrap nopeer noquery
restrict -6 default kod nomodify notrap nopeer noquery
restrict 127.0.0.1
restrict -6 ::1


```
Replace "202.54.1.5" with the address of your hypervisor host. Alternately, you could point it to an NTP host, such as 
```

server 0.ubuntu.pool.ntp.org
server 1.ubuntu.pool.ntp.org
server 2.ubuntu.pool.ntp.org
server 3.ubuntu.pool.ntp.org

``` 
(Replace the top 2 lines with these 4 lines)

What that would do (after the config) is say, only get "one time" from this or these sources. The other restricts use as an npt sererv from other pc's on the same network... but gives itself unrestricted access.

That is sort of a sledge hammer work-around, but it is all I can think of at the moment...I've not noticed that problem on mine... but my main DC is my ntp server for that subnet, where all my virtual host servers are. ...But truthfully, now that I think about it, I might be just assuming that they are working that way. I never looked into to it to confirm that what is going on with you is nt happening with mine....

LOL. Now you have me curious.

---

### Post by Marc_Rouleau on 2017-03-06
I encountered this issue of "systemd[...]Time has been changed" messages logged every five seconds in /var/log/syslog on a 16.04 server running under Windows 8.1 Hyper-V. Instead of turning off ntp in the VM, I disabled time synchronization on the Hyper-V side. In Hyper-V Manager, I highlighted the VM, selected "Settings...", then "Integration Services", unchecked "Time synchronization", and clicked Apply. The messages stopped instantly - no VM restart was required.

---

### Post by DuckHook on 2017-03-06
Please don't necropost. The original thread is a year old and deals with an obsolete version. Please start a new thread for your problem.

*Thread Closed.*

---

