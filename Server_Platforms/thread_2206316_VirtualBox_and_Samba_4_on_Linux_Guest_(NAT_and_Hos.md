---
title: "VirtualBox and Samba 4 on Linux Guest (NAT and Host Only)"
date: 2014-02-18
forum: Server Platforms
---

### Post by eduardolucioac on 2014-02-18
Gentlemen,


I really need a help from you to configure the "Samba 4" using the "Virtual Box".


Here's the situation:


In certain networks where I work, the Samba 4 works, in other does not. The guest in Virtual box is configured with a network "Host Only" for Samba 4 and other "NAT" for the internet. The only situation where the samba works on all networks is if I disable the "NAT" network and leave only "Host Only". That is, apparently the NAT network (which should be isolated from the external network by using it only as a proxy) is suffering from some kind of negative effect in some cases.


Then... Comes the question that is worth a million:


What causes it?


Believe me, I tried everything and nothing seems to resolve the situation.


Note I: I can not use the guest network with Bridge!
Note II: Apparently this only occurs with Samba 4 as the Samba 3 works on any network!


This has been a really difficult situation to solve and I'm "stuck" on it almost 3 weeks.


Someone is also with this problem?


I ask you to help! Thanks!


**MORE INFORMATION ABOUT THE PROBLEM:**


If I were to venture an answer to this question, I would say that the problem could be in the gateway. Well, it seems that Samba 4 receives the request from the "Host Only" interface, but attempts to answer by "NAT" interface (as there is only one gateway, "NAT" gateway). I've tried to solve this by entering the following in the section "[global]" in the file "/etc/samba/smb.conf"...


```
    interfaces = enp0s3 lo
    bind interfaces only = yes
```


... what actually works (only accepts requests coming in "Host Only" interface). But it does not solve the problem.


**PLUS:**


**Output of the "ifconfig" command:**


```
enp0s3    Link encap:Ethernet  HWaddr 08:00:27:AB:52:E3  
          inet addr:192.168.56.100  Bcast:192.168.56.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:feab:52e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:602 errors:0 dropped:0 overruns:0 frame:0
          TX packets:849 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:81307 (79.4 Kb)  TX bytes:127690 (124.6 Kb)


enp0s8    Link encap:Ethernet  HWaddr 08:00:27:09:CC:37  
          inet addr:10.0.3.15  Bcast:10.0.3.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe09:cc37/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5889 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6668637 (6.3 Mb)  TX bytes:432330 (422.1 Kb)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:519 errors:0 dropped:0 overruns:0 frame:0
          TX packets:519 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39728 (38.7 Kb)  TX bytes:39728 (38.7 Kb)
```


**"/etc/samba/smb.conf"**


```
# smb.conf is the main Samba configuration file. You find a full commented
# version at /usr/share/doc/packages/samba/examples/smb.conf.SUSE if the
# samba-doc package is installed.
[global]
        workgroup = WORKGROUP
        passdb backend = tdbsam
        printing = cups
        printcap name = cups
        printcap cache time = 750
        cups options = raw
        map to guest = Bad User
        include = /etc/samba/dhcp.conf
        logon path = \\%L\profiles\.msprofile
        logon home = \\%L\%U\.9xprofile
        logon drive = P:
        usershare allow guests = Yes
        add machine script = /usr/sbin/useradd  -c Machine -d /var/lib/nobody -s /bin/false %m$
        domain logons = Yes
        domain master = Yes
        local master = Yes
        os level = 65
        preferred master = Yes
        security = user
        usershare max shares = 100
        wins server =
        wins support = No
        interfaces = enp0s3 lo
        bind interfaces only = yes
[homes]
        comment = Home Directories
        valid users = %S, %D%w%S
        browseable = No
        read only = No
        inherit acls = Yes
[profiles]
        comment = Network Profiles Service
        path = %H
        read only = No
        store dos attributes = Yes
        create mask = 0600
        directory mask = 0700
[users]
        comment = All users
        path = /home
        read only = No
        inherit acls = Yes
        veto files = /aquota.user/groups/shares/
[groups]
        comment = All groups
        path = /home/groups
        read only = No
        inherit acls = Yes
[printers]
        comment = All Printers
        path = /var/tmp
        printable = Yes
        create mask = 0600
        browseable = No
[print$]
        comment = Printer Drivers
        path = /var/lib/samba/drivers
        write list = @ntadmin root
        force group = ntadmin
        create mask = 0664
        directory mask = 0775


[SES_DF]
        comment = SES_DF
        inherit acls = Yes
        path = /home/brlight/DEV_GUESTS/SES_DF
        read only = No


[netlogon]
        comment = Network Logon Service
        path = /var/lib/samba/netlogon
        write list = root
```


**Output of the "route" command when "NAT" interface is active:**


```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.0.3.2        0.0.0.0         UG    0      0        0 enp0s8
10.0.3.0        *               255.255.255.0   U     1      0        0 enp0s8
192.168.56.0    *               255.255.255.0   U     1      0        0 enp0s3
```


!!!Important: If I disable the host network, Samba 4 works and I have the same output as above!!!


**Output of the "route" command when "NAT" interface is not active (cable unplugged on Virtual Box)(Samba 4 works!):**


```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.56.0    *               255.255.255.0   U     1      0        0 enp0s3
```


Note: There is no gateway...


**In this scenario I would propose two hypothetical solutions:**



[LIST]
[*]Make the Samba 4 see just "enp0s3" interface in any situation (request and response);
[/LIST]


[LIST]
[*]Try to set something in VirtualBox to not allow negative influences from the external network on the "NAT". Since the virtual machine works on some networks but not others;
Note: The distro I am using for the guest is the OpenSUSE 13.1 and for the host is Linux Mint 16 KDE (Ubuntu Based).
[/LIST]



**PLUS PLUS:**


I tried to change the range of the "NAT" because the host network is in a similar range (192.168.1.x). I used the range "169.254.0.x" to the "NAT" network, but the problem continued.


As you can see, this is a difficult problem and difficult to diagnose, and I need all the help from you!

---

