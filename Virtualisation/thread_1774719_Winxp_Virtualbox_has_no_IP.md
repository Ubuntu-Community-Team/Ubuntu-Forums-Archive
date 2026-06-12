---
title: "Winxp Virtualbox has no IP"
date: 2011-06-03
forum: Virtualisation
---

### Post by Jake.Debord on 2011-06-03
I am new to virtualbox, so I may be overlooking something...

I installed Virtualbox with a winxp ISO... I run vboxheadless --startvm Winxp 

when  I run vbmanage showvminfo Winxp  everything looks fine, its even  displaying the port I wanted. But in the I.P it displays 0.0.0.0

Any one have information on how to get it to acquire an i.p????

VRDE:            enabled (Address 0.0.0.0, Ports 5000, MultiConn: off, ReuseSingleConn: off, Authentication type: null)


TIA

---

### Post by CharlesA on 2011-06-03
If that is for the VRDP address, just use the host machine's IP. Usually 0.0.0.0 means it'll be listening on the external address for any connections.

---

### Post by lmarmisa on 2011-06-03
Open Command Prompt and type this command

```

ipconfig

```

The result will show the IP address of your network interface:

```

C:\Documents and Settings\luis>ipconfig

Windows IP Configuration


Ethernet adapter OpenVPN:

        Media State . . . . . . . . . . . : Media disconnected

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : [COLOR="Blue"]192.168.2.71[/COLOR]
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.2.1

C:\Documents and Settings\luis>

```

---

### Post by Jake.Debord on 2011-06-06
Well it will not let me connect with Remote Desktop from my windows computer. I enter the host's ip:port and it can't connect... am I missing something?

It is setup on a headless Ubuntu server 10.10 so its been difficult to make sure I have everything configured correctly.

---

### Post by CharlesA on 2011-06-06
Make sure it's not firewalled.

You can also see if the host is listening on that port or not by running this:

```
netstat -nl
```

---

### Post by Jake.Debord on 2011-06-06
Here is the outcome of the netstat

It doesn't look like vbox is even listed??? :(


```
$ netstat -nl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:55338           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:9101            0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:9102          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:9103          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:8019            0.0.0.0:*               LISTEN
tcp        0      0 192.168.122.1:53        0.0.0.0:*               LISTEN
tcp        0      0 10.0.6.103:53           0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN
tcp        0      0 10.0.6.103:1723         0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:50495           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN
tcp6       0      0 127.0.0.1:8005          :::*                    LISTEN
tcp6       0      0 :::55338                :::*                    LISTEN
tcp6       0      0 :::8080                 :::*                    LISTEN
tcp6       0      0 :::21                   :::*                    LISTEN
tcp6       0      0 :::53                   :::*                    LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
tcp6       0      0 ::1:631                 :::*                    LISTEN
tcp6       0      0 ::1:953                 :::*                    LISTEN
udp        0      0 192.168.122.1:53        0.0.0.0:*
udp        0      0 192.168.122.1:53        0.0.0.0:*
udp        0      0 10.0.6.103:53           0.0.0.0:*
udp        0      0 127.0.0.1:53            0.0.0.0:*
udp        0      0 0.0.0.0:67              0.0.0.0:*
udp        0      0 0.0.0.0:68              0.0.0.0:*
udp        0      0 0.0.0.0:10000           0.0.0.0:*
udp6       0      0 :::53                   :::*
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     10093    @/tmp/fam-root-
unix  2      [ ACC ]     STREAM     LISTENING     8969     /var/run/libvirt/libv                                                                 irt-sock
unix  2      [ ACC ]     STREAM     LISTENING     8971     /var/run/libvirt/libv                                                                 irt-sock-ro
unix  2      [ ACC ]     STREAM     LISTENING     10037    /tmp/.winbindd/pipe
unix  2      [ ACC ]     STREAM     LISTENING     10039    /var/run/samba/winbin                                                                 dd_privileged/pipe
unix  2      [ ACC ]     STREAM     LISTENING     6481     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     10154    /tmp/.SQLAnywhere/qb_                                                                 doraleeii_20/lrm_socket
unix  2      [ ACC ]     STREAM     LISTENING     8823     /var/run/dovecot/dict                                                                 -server
unix  2      [ ACC ]     STREAM     LISTENING     8825     /var/run/dovecot/logi                                                                 n/default
unix  2      [ ACC ]     STREAM     LISTENING     8831     /var/run/dovecot/auth                                                                 -worker.1126
unix  2      [ ACC ]     STREAM     LISTENING     9876     /var/run/mysqld/mysql                                                                 d.sock
unix  2      [ ACC ]     STREAM     LISTENING     9397     /var/run/cups/cups.so                                                                 ck
unix  2      [ ACC ]     STREAM     LISTENING     8148     /var/run/dbus/system_                                                                 bus_socket

```

---

### Post by Jake.Debord on 2011-06-06
Is there a service or something I need running that may be missing? I thought installing the exp pack may help, but I can't find a good howto, and I'm afraid to mess it up... 

If I do install the exp pack will that help?

---

### Post by Jake.Debord on 2011-06-06
I have to be missing something I just tried the Vboxaddif command and it said no such command found

:(

---

### Post by CharlesA on 2011-06-06
I think you do have to install the extension pack to access VRDP.

Power off the VM then run this command:

```
VBoxHeadless -s Winxp -p 5000
```

See what happens.

---

### Post by Jake.Debord on 2011-06-06
Ok, can you point me in the direction of a good howto install it on headless machine? Everything I find is for the gui :(

Here is code for your suggestion

```
$ vboxheadless -s Winxp -p 5000
Oracle VM VirtualBox Headless Interface 4.0.8
(C) 2008-2011 Oracle Corporation
All rights reserved.

Warning: '-p' or '-vrdpport' are deprecated. Use '-e "TCP/Ports=5000"'

```

I tried again with the suggested -e tcp/ports=5000 and it didn't kick back any errors, but when i ran netstat-nl I still didn't see port 5000 anywhere.

---

### Post by Jake.Debord on 2011-06-06
FYI: 
Below is the results of my showvminfo In case that will help in any way. 

Look at my network stuff if you don't mind and just double check it looks correct please :)

```
$ vboxmanage showvminfo Winxp
Name:            Winxp
Guest OS:        Windows XP
UUID:            5d335fbc-1c06-437a-adef-57ffd86e99dd
Config file:     /home/jdebord/VirtualBox VMs/Winxp/Winxp.vbox
Snapshot folder: /home/jdebord/VirtualBox VMs/Winxp/Snapshots
Log folder:      /home/jdebord/VirtualBox VMs/Winxp/Logs
Hardware UUID:   5d335fbc-1c06-437a-adef-57ffd86e99dd
Memory size:     800MB
Page Fusion:     off
VRAM size:       8MB
HPET:            off
Chipset:         piix3
Firmware:        BIOS
Number of CPUs:  1
Synthetic Cpu:   off
CPUID overrides: None
Boot menu mode:  message and menu
Boot Device (1): DVD
Boot Device (2): DVD
Boot Device (3): HardDisk
Boot Device (4): Not Assigned
ACPI:            on
IOAPIC:          off
PAE:             on
Time offset:     0 ms
RTC:             local time
Hardw. virt.ext: on
Hardw. virt.ext exclusive: on
Nested Paging:   on
Large Pages:     off
VT-x VPID:       on
State:           running (since 2011-06-06T19:44:02.303000000)
Monitor count:   1
3D Acceleration: off
2D Video Acceleration: off
Teleporter Enabled: off
Teleporter Port: 0
Teleporter Address:
Teleporter Password:
Storage Controller Name (0):            IDE Controller
Storage Controller Type (0):            PIIX4
Storage Controller Instance Number (0): 0
Storage Controller Max Port Count (0):  2
Storage Controller Port Count (0):      2
Storage Controller Bootable (0):        on
IDE Controller (0, 0): /var/vbox/Winxp.vdi (UUID: 9ea03cf1-b3a1-4739-a332-f2af39db373d)
IDE Controller (0, 1): /var/vbox/Winxp.iso (UUID: c7fe0704-2b33-47fb-aff7-b92c4da6bc10)
NIC 1:           MAC: 080027A0F48D, Attachment: Bridged Interface 'eth0', Cable connected: on, Trace: off (file: none), Type: Am79C973, Reported speed: 0 Mbps, Boot priority: 0
NIC 2:           disabled
NIC 3:           disabled
NIC 4:           disabled
NIC 5:           disabled
NIC 6:           disabled
NIC 7:           disabled
NIC 8:           disabled
Pointing Device: PS/2 Mouse
Keyboard Device: PS/2 Keyboard
UART 1:          disabled
UART 2:          disabled
Audio:           disabled
Clipboard Mode:  Bidirectional
Video mode:      720x396x0
VRDE:            enabled (Address 0.0.0.0, Ports 5000, MultiConn: off, ReuseSingleConn: off, Authentication type: null)
Video redirection: disabled
USB:             disabled

USB Device Filters:

<none>

Available remote USB devices:

<none>

Currently Attached USB Devices:

<none>

Shared folders:  <none>

VRDE Connection:    not active
Clients so far:     0

Guest:

OS type:                             WindowsXP
Additions run level:                 0
Configured memory balloon size:      0 MB

```

---

### Post by Jake.Debord on 2011-06-06
SOLVED!!! :D

In case anyone looks this over for an answer, here it is:

Must install extenstion pack

sudo vboxmanage extpack install /directory/to/extensionfile

then, make sure VRDE is on

vboxmanage "vmname" --vrde on

Then run the command as suggested by Charles

vboxheadless -s "vmname" -e TCP/Ports="Port to listen on"

should get an outcome like :

```
$ vboxheadless -s Winxp -e TCP/Ports=5000
Oracle VM VirtualBox Headless Interface 4.0.8
(C) 2008-2011 Oracle Corporation
All rights reserved.

VRDE server is listening on port 5000.

```

Then, remote to the hosts IP and port you picked and wha-la :)


Thanks a bunch Charles!

---

### Post by CharlesA on 2011-06-06
Glad to help.

Looks like they've changed some stuff a bit since 4.0. :)

---

### Post by Jake.Debord on 2011-06-06
Any idea why it closes the connection when I close SSH terminal?

Its a little annoying that I must have SSH open in order to be able to remote in...

Any way around this???

---

### Post by CharlesA on 2011-06-06
Do you have to start the VM after closing out the SSH session?

If it's still running, then check your firewall rules.

---

### Post by Jake.Debord on 2011-06-06
I think I may have confused you, or myself... lol

1) I use ssh to start the vm 

2) I connect with rdp

3) I closed ssh, and it knocked me off the RDP :(

I need to be able to start the VM with ssh and it still be accessible if ssh is closed.

Did I clear that up?

---

### Post by CharlesA on 2011-06-06
Kinda. So you don't need to start the VM up again after disconnecting, then reconnecting?

Are there any firewall rules in place? Check with:

```
sudo iptables -L
```

---

### Post by Jake.Debord on 2011-06-06
Not that I know of :(

```
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     udp  --  anywhere             anywhere            udp dpt:doma                                                                                                        in
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:doma                                                                                                        in
ACCEPT     udp  --  anywhere             anywhere            udp dpt:boot                                                                                                        ps
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:boot                                                                                                        ps
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:mysq                                                                                                        l dpt:mysql
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:5000                                                                                                         dpt:5000

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             192.168.122.0/24    state RELATE                                                                                                        D,ESTABLISHED
ACCEPT     all  --  192.168.122.0/24     anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

---

### Post by CharlesA on 2011-06-06
Check the settings from phpvirtualbox. It should tell you the "server port."

---

