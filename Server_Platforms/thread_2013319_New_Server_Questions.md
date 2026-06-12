---
title: "New Server Questions"
date: 2012-06-30
forum: Server Platforms
---

### Post by d4m1r on 2012-06-30
Hey guys, so I just install 11.10 Server (32 bit) on an old Dell PC and I have a few questions....

1) Where do I go to check that the network settings were confiuquired properly?

2) It will install SSH by default correct? So I can move the server into a corner with only a power and ethernet cord?

3) Using command line, how can I check all the hardware the OS detects? I want to make sure everything is recognized including a new D-Link gigabit NIC I installed.....

4) How to scan the HDD for bad sectors/issues and repair them using the command line? Can I check SMART health via command line? How many bad sectors can a HDD have before causing issues? I think the HDD has 5-6 but I want to double check them using some kind of built in tool....


Thanks and let me know guys! ;)

---

### Post by CharlesA on 2012-06-30
1) Network settings are configured in:

```
/etc/network/interfaces
```

2) You will have to select openssh-server during install, or install it after installation is complete. I have installed my server with a monitor attached, then moved it to it's final resting place where it only had power and network hooked up.

3) As long as it is working fine, you should be good. I haven't run into any problems with network cards on the server version.

4) The smartmontools package includes all the SMART checking stuff you will need. You can run fsck from the command line or after a reboot as well.

SMART will tell you how many bad sectors a drive has. If that number keeps increasing, it is a good idea to replace the drive.

---

### Post by d4m1r on 2012-06-30
Thanks! So far so good....and a final question, how do I disable telnet connections to the server?

---

### Post by d4m1r on 2012-06-30
Also, find the SMART information about my HDD below, how does it look? I know it has a few bad sectors but is it on its way out? :confused:

```

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.7 and 7200.7 Plus
Device Model:     ST340014A
Serial Number:    5JX5L3YZ
Firmware Version: 3.06
User Capacity:    40,020,664,320 bytes [40.0 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Sat Jun 30 16:39:18 2012 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 120) The previous self-test completed having
                                        the read element of the test failed.
Total time to complete Offline
data collection:                (  430) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off supp              ort.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        No General Purpose Logging support.
Short self-test routine
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        (  31) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_              FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   057   056   006    Pre-fail  Always       -                     165414606
  3 Spin_Up_Time            0x0003   098   098   000    Pre-fail  Always       -                     0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -                     39
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -                     9
  7 Seek_Error_Rate         0x000f   086   060   030    Pre-fail  Always       -                     403592262
  9 Power_On_Hours          0x0032   054   054   000    Old_age   Always       -                     41126
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -                     0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -                     72
194 Temperature_Celsius     0x0022   041   051   000    Old_age   Always       -                     41
195 Hardware_ECC_Recovered  0x001a   057   055   000    Old_age   Always       -                     165414606
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -                     0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -                     0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -                     0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -                     0
202 Data_Address_Mark_Errs  0x0032   100   253   000    Old_age   Always       -                     0

SMART Error Log Version: 1
ATA Error Count: 135 (device log contains only the most recent five errors)
        CR = Command Register [HEX]
        FR = Features Register [HEX]
        SC = Sector Count Register [HEX]
        SN = Sector Number Register [HEX]
        CL = Cylinder Low Register [HEX]
        CH = Cylinder High Register [HEX]
        DH = Device/Head Register [HEX]
        DC = Device Command Register [HEX]
        ER = Error register [HEX]
        ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 135 occurred at disk power-on lifetime: 41122 hours (1713 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle              .

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d1 4d 05 e0  Error: UNC at LBA = 0x00054dd1 = 347601

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d0 4d 05 e0 00      00:22:41.840  READ DMA
  27 00 00 00 00 00 e0 00      00:22:41.840  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02      00:22:41.832  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      00:22:41.824  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      00:22:41.824  READ NATIVE MAX ADDRESS EXT

Error 134 occurred at disk power-on lifetime: 41122 hours (1713 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle              .

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d1 4d 05 e0  Error: UNC at LBA = 0x00054dd1 = 347601

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d0 4d 05 e0 00      00:22:41.840  READ DMA
  27 00 00 00 00 00 e0 00      00:22:41.840  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02      00:22:41.832  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      00:22:41.824  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      00:22:41.824  READ NATIVE MAX ADDRESS EXT

Error 133 occurred at disk power-on lifetime: 41122 hours (1713 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle              .

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d1 4d 05 e0  Error: UNC at LBA = 0x00054dd1 = 347601

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d0 4d 05 e0 00      00:22:33.900  READ DMA
  27 00 00 00 00 00 e0 00      00:22:33.900  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02      00:22:33.895  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      00:22:29.894  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      00:22:29.894  READ NATIVE MAX ADDRESS EXT

Error 132 occurred at disk power-on lifetime: 41122 hours (1713 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle              .

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d1 4d 05 e0  Error: UNC at LBA = 0x00054dd1 = 347601

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d0 4d 05 e0 00      00:22:33.900  READ DMA
  27 00 00 00 00 00 e0 00      00:22:33.900  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02      00:22:33.895  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      00:22:29.894  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      00:22:29.894  READ NATIVE MAX ADDRESS EXT

Error 131 occurred at disk power-on lifetime: 41122 hours (1713 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle              .

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d1 4d 05 e0  Error: UNC at LBA = 0x00054dd1 = 347601

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d0 4d 05 e0 00      00:22:22.306  READ DMA
  27 00 00 00 00 00 e0 00      00:22:22.287  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02      00:22:22.276  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      00:22:29.894  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      00:22:29.894  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA              _of_first_error
# 1  Short offline       Completed: read failure       80%     41126         301              016
# 2  Short offline       Completed without error       00%         0         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

---

### Post by CharlesA on 2012-06-30
telnet shouldn't be installed by default.

---

### Post by d4m1r on 2012-06-30
> **CharlesA said:**
> telnet shouldn't be installed by default.

Well it seems to be....when I specify telnet and the port, it connects.....sorta:

```
SSH-2.0-OpenSSH_5.8p1 Debian-7ubuntu1
```

^Displays that when I connect over telnet. I'd like to get it to say "connection refused" like it did on my previous server.

---

### Post by CharlesA on 2012-06-30
That just means openssh-server is running.

---

### Post by d4m1r on 2012-06-30
> **CharlesA said:**
> That just means openssh-server is running.

Ah, well it is possibly to disable that message? I'd like the connection to be refused if someone even tries to connect over telnet so they shouldn't even get that message to know the server is there.

---

### Post by lisati on 2012-06-30
> **d4m1r said:**
> Ah, well it is possibly to disable that message? I'd like the connection to be refused if someone even tries to connect over telnet so they shouldn't even get that message to know the server is there.

If you don't forward the relevant ports from the outside to your server via your router, incoming connections will time out as if the service isn't there.

---

### Post by d4m1r on 2012-06-30
> **lisati said:**
> If you don't forward the relevant ports from the outside to your server via your router, incoming connections will time out as if the service isn't there.

Actually, that is exactly what I DO do :( Is there no way to disable that OpenSSH message when connecting over telnet?

---

### Post by CharlesA on 2012-06-30
> **d4m1r said:**
> Actually, that is exactly what I DO do :( Is there no way to disable that OpenSSH message when connecting over telnet?
No. The port is open and that it OpenSSH just telling you it is there.

Normally you wouldn't connect to ssh via telnet unless you are trying to troubleshoot or do something shady.

In any case, even if you tried to connect via telnet, it wouldn't work because you get disconnected as soon as you hit a key.

Use an SSH client to connect to an ssh server and ensure it is secured properly - strong passwords, new connection limits, etc.

---

### Post by darkod on 2012-07-01
Also, where are you trying the telnet from, your local network?

Unless you forward the SSH port on your router towards the server IP, no one (including you) can access it from outside your network. Try the telnet from outside and you will see.

From inside your network, of course it will show the SSH service as running, otherwise how do you plan to connect to it?

I am confused what are you trying to do. If you want the SSH available only for your computer, you can activate the firewall on the server and allow only the private IP of your computer (in that case it will need to have static IP). That way other computer even from your network can't access it.

---

### Post by CharlesA on 2012-07-01
> **darkod said:**
> 
I am confused what are you trying to do. If you want the SSH available only for your computer, you can activate the firewall on the server and allow only the private IP of your computer (in that case it will need to have static IP). That way other computer even from your network can't access it.

Same. I have the whole internal network whitelisted in iptables so I can SSH in from any machine, which works for me cuz I have SSH locked down to only use keys among other things.

If you only want to connect from a certain machine, you'll need to set either a dhcp reservation or a static IP, as I am not sure if you can use a hostname or not.

---

### Post by d4m1r on 2012-07-01
> **darkod said:**
> Unless you forward the SSH port on your router towards the server IP, no one (including you) can access it from outside your network. Try the telnet from outside and you will see.

This is exactly what I do as I mentioned previous. I forward port 22 (for example) from the outside to a specific local machine via my router. If I try to connect to it from outside my network over SSH, it works as intended. However, if I specify the same port from the outside but select telnet, I get that message.

I'd like to disable that message so people who try to connect over telnet would not even know anything is running there.

---

### Post by darkod on 2012-07-01
As Charles already explained, that is not a telnet connection in reality. telnet can be used to check if there is a service listening on a particular IP and port.

Since you do have the SSH service listening on that server, I don't think you can avoid getting that message if tested with telnet. But that is not an established telnet connection, that is only the reply of the SSH server saying "hello, I'm here".

For example, try the telnet again. Apart from the SSH message you get, can you do anything else? Connect? Issue commands? No...

---

### Post by Doug S on 2012-07-01
I know this is not what you are trying to achieve, but...
You can get rid of a portion of that message by adding this line to /etc/ssh/sshd_config:```
DebianBanner no
```Example (before edit):```
doug@doug-64:~/public_html/network/load_average$ telnet s15.smythies.com 22
Trying 192.168.111.112...
Connected to s15.smythies.com.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1
```Example (after edit):```
doug@doug-64:~/public_html/network/load_average$ telnet s15.smythies.com 22
Trying 192.168.111.112...
Connected to s15.smythies.com.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.9p1
```I don't know of a way to get rid of the rest of it, and actually think (but not sure) that is part of the inital protocol handshake.
You mentioned that your old server replied with "connection refused" and I guess, with respect, I am questioning that assertion as I just don't understand how that could be while still allowing an SSH session.

---

### Post by computerfox on 2012-07-01
wait, you're saying that if you use a different protocol for that port you get a warning on that machine?  :-0  seems kindda normal to me since that's not a telnet.  That's simply the software saying that you have to change a different protocol and personally I don't believe that, that will lead to anyone breaking into the server.  Just make sure that you have a strong password for the ssh.

---

### Post by computerfox on 2012-07-01
> **Doug S said:**
> I know this is not what you are trying to achieve, but...
You can get rid of a portion of that message by adding this line to /etc/ssh/sshd_config:```
DebianBanner no
```Example (before edit):```
doug@doug-64:~/public_html/network/load_average$ telnet s15.smythies.com 22
Trying 192.168.111.112...
Connected to s15.smythies.com.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1
```Example (after edit):```
doug@doug-64:~/public_html/network/load_average$ telnet s15.smythies.com 22
Trying 192.168.111.112...
Connected to s15.smythies.com.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.9p1
```I don't know of a way to get rid of the rest of it, and actually think (but not sure) that is part of the inital protocol handshake.
You mentioned that your old server replied with "connection refused" and I guess, with respect, I am questioning that assertion as I just don't understand how that could be while still allowing an SSH session.


I believe you're correct.  Your software is nice enough to let you know that it's trying to connect and once it did connect, it's okay to continue.  As far as I know you can only take off the welcome banner, the one you get once you are already logged into the server via SSH by editing one of the files(I forgot which file).

---

### Post by d4m1r on 2012-07-01
> **Doug S said:**
> 
You mentioned that your old server replied with "connection refused" and I guess, with respect, I am questioning that assertion as I just don't understand how that could be while still allowing an SSH session.

Is OpenSSH the default SSH service? If it's not, I used the default one that came with 11.10 and it is behaving differently than 11.10 w/OpenSSH I just installed on that old PC.

---

### Post by CharlesA on 2012-07-01
There is only one version of openssh server.

---

