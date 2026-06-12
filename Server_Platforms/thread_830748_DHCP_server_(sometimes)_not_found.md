---
title: "DHCP server (sometimes) not found"
date: 2008-06-16
forum: Server Platforms
---

### Post by Nurionn on 2008-06-16
Hi everyone

I have some trouble with my Edubuntu 8.04 LTSP server:

Sometimes my ThinClients cannot find any DHCP server. This error often occours, when I start multiple clients at the same time.
In /var/log/syslog, I find the dhcprequest/dhcpoffer but the client doesent "accept" the adress.


I tried already to change switches / cables between server and clients, but it still doesnt work (or at least not always).

btw: on the same hardware, it worked using Edubuntu 7.10.



Is there any known bug?

---

### Post by Paulo Páscoa on 2008-07-02
I work at a School and we were preparing a class with the Ubuntu LTSP, and we are having the same problem (that's why i just registered).
If we boot the clients each at a time, it goes well, but when we boot two clients with little time between them, the server seems to hang the dhcpd and the only thing we can do is to reboot the server. :(
The problem is the same using Ubuntu or Edubuntu LTSP.
We wanted to use this system at several places as the Library and common working rooms, but we need this to be solved.
Despite that, this is a wonderfull system to work with. :KS
Hope someone can help.

---

### Post by promodus on 2008-07-02
Can you output the following:
```
dpkg -l dhcp*
```

```
dpkg -l tftp*
```

```
cat /etc/inetd.conf
```

---

### Post by Paulo Páscoa on 2008-07-08
Hi promodus,
Was some days away from school.
Here is the results you asked for.
Thank you for your time :)


Result of:	dpkg -l dhcp*
-----------------------------

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Nome           Versão        Descrição
+++-==============-==============-============================================
un  dhcp           <nenhum>       (sem descrição disponível)
un  dhcp-client    <nenhum>       (sem descrição disponível)
ii  dhcp3-client   3.0.6.dfsg-1ub DHCP client
ii  dhcp3-common   3.0.6.dfsg-1ub common files used by all the dhcp3* packages
ii  dhcp3-server   3.0.6.dfsg-1ub DHCP server for automatic IP address assignm

***********************************************************************

Result of:	dpkg -l tftp*
-----------------------------

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Nome           Versão        Descrição
+++-==============-==============-============================================
un  tftpd          <nenhum>       (sem descrição disponível)
ii  tftpd-hpa      0.48-1ubuntu1  HPA's tftp server

***********************************************************************

Result of:	cat /etc/inetd.conf
-----------------------------------

# /etc/inetd.conf:  see inetd( 8 ) for further informations.
#
# Internet superserver configuration database
#
#
# Lines starting with "#:LABEL:" or "#<off>#" should not
# be changed unless you know what you are doing!
#
# If you want to disable an entry so it isn't touched during
# package updates just comment it out with a single '#' character.
#
# Packages should modify this file by using update-inetd( 8 )
#
# <service_name> <sock_type> <proto> <flags> <user> <server_path> <args>
#
#:INTERNAL: Internal services
#discard		stream	tcp	nowait	root	internal
#discard		dgram	udp	wait	root	internal
#daytime		stream	tcp	nowait	root	internal
#time		stream	tcp	nowait	root	internal

#:STANDARD: These are standard services.

#:BSD: Shell, login, exec and talk are BSD protocols.

#:MAIL: Mail, news and uucp services.

#:INFO: Info services

#:BOOT: TFTP service is provided primarily for booting.  Most sites
#       run this only on machines acting as "boot servers."
tftp           dgram   udp     wait    root  /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /var/lib/tftpboot

#:RPC: RPC based services

#:HAM-RADIO: amateur-radio services

#:OTHER: Other services

9571           stream  tcp     nowait  nobody /usr/sbin/tcpd /usr/sbin/ldminfod
9572			stream  tcp 	nowait 	nobody /usr/sbin/tcpd /usr/sbin/nbdswapd
2000               stream  tcp            nowait  nobody /usr/sbin/tcpd /usr/sbin/nbdrootd /opt/ltsp/images/i386.img

---

### Post by promodus on 2008-07-20
Could you give the output of
```

cat /etc/dhcp3/dhcpd.conf
```

Also, are there any other DHCP servers on the network?

---

### Post by choup on 2008-08-03
Hello, I too am having this same problem that did not exist with 7.10 release. I have attached all the output you requested, except that since this is related to LTSP, I provided the LTSP dhcpd.conf file. As you can see, the results for the first three files are identical to the ones Paulo Páscoa provided except that mine are in english. This problem is a real show stopper. Please help...

dpkg -l dhcp:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name              Version                Description
+++-=================-======================-============================================
un  dhcp              <none>                 (no description available)
un  dhcp-client       <none>                 (no description available)
ii  dhcp3-client      3.0.6.dfsg-1ubuntu9    DHCP client
ii  dhcp3-common      3.0.6.dfsg-1ubuntu9    common files used by all the dhcp3* packages
ii  dhcp3-server      3.0.6.dfsg-1ubuntu9    DHCP server for automatic IP address assignm


dpkg -l tftp:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name              Version                 Description
+++-=========+=======-=========+=============-============================================
un  tftpd             <none>                  (no description available)
ii  tftpd-hpa         0.48-1ubuntu1           HPA's tftp server

cat /etc/inetd.conf:

# /etc/inetd.conf:  see inetd(8) for further informations.
#
# Internet superserver configuration database
#
#
# Lines starting with "#:LABEL:" or "#<off>#" should not
# be changed unless you know what you are doing!
#
# If you want to disable an entry so it isn't touched during
# package updates just comment it out with a single '#' character.
#
# Packages should modify this file by using update-inetd(8)
#
# <service_name> <sock_type> <proto> <flags> <user> <server_path> <args>
#
#:INTERNAL: Internal services
#discard		stream	tcp	nowait	root	internal
#discard		dgram	udp	wait	root	internal
#daytime		stream	tcp	nowait	root	internal
#time		stream	tcp	nowait	root	internal

#:STANDARD: These are standard services.

#:BSD: Shell, login, exec and talk are BSD protocols.

#:MAIL: Mail, news and uucp services.

#:INFO: Info services

#:BOOT: TFTP service is provided primarily for booting.  Most sites
#       run this only on machines acting as "boot servers."
tftp           dgram   udp     wait    root  /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /var/lib/tftpboot

#:RPC: RPC based services

#:HAM-RADIO: amateur-radio services

#:OTHER: Other services

9571   stream  tcp   nowait  nobody /usr/sbin/tcpd /usr/sbin/ldminfod
9572   stream  tcp   nowait  nobody /usr/sbin/tcpd /usr/sbin/nbdswapd
2000   stream  tcp   nowait  nobody /usr/sbin/tcpd /usr/sbin/nbdrootd /opt/ltsp/images/i386.img

cat /etc/ltsp/dhcpd.conf:
 
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.20 192.168.0.250;
    option domain-name "hgbcaa.local";
    option domain-name-servers 192.168.0.1;
    option broadcast-address 192.168.0.255;
    option routers 192.168.0.1;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}

Note: 192.168.0.1 is the assigned IP to eth0 of the Terminal Server

---

### Post by promodus on 2008-08-12
Try changes in [COLOR="Red"]RED[/COLOR].

/etc/ltsp/dhcpd.conf:
```


#
# Default LTSP dhcpd.conf config file.
#

authoritative;
[COLOR="Red"]allow bootp;[/COLOR]

subnet 192.168.0.0 netmask 255.255.255.0 {
    [COLOR="Red"]next-server 192.168.0.1;[/COLOR]
    range 192.168.0.20 192.168.0.250;
    option domain-name "hgbcaa.local";
    option domain-name-servers 192.168.0.1;
    option broadcast-address 192.168.0.255;
    option routers 192.168.0.1;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}



```

---

### Post by choup on 2008-08-13
Thanks for the feedback. I will make the edits on Saturday, which is my scheduled volunteer workday. I will give you an update then.

BTW, I am curious as to why the bootp? I haven't seen this before in any of the edubuntu server releases in the past. This problem seems to have only started with release 8.04. 

This thread is the only one I've found that even comes close to zeroing in on the multiple client simultaneous boot problem. I would think there would have been a significant number of others that have run into this issue.

Thanks again for the help...

---

### Post by promodus on 2008-08-15
Actually, you're correct "allow bootp;" isn't needed.

Going from a minimal configuration, all you need is to specify is
```
filename "pxelinux.0"; 
```
within your address scope.

So what you may try is to remove what's in red, as below:
```
[COLOR="Red"]    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {[/COLOR]
        filename "/ltsp/i386/pxelinux.0";
[COLOR="Red"]    } else {
        filename "/ltsp/i386/nbi.img";
    }[/COLOR]
```

---

### Post by choup on 2008-08-17
Thanks for the feedback again. I tried several different changes as well as doing a complete default re-install. The root of the problem here seems to be Ubuntu, period. Ubuntu does a lot of things differently than non-debian based OSs. They seem to have a lot of issues centered around networking, especially the Ubuntu version, and specifically the LTSP changes.

There are very clearly bad configuration files included in the released version 8.04.1 and previous versions, as well as broken functionality, the only difference in why 7.10 worked was that it was based on LTSP v4.2, whereas 8.04 and later are based on LTSP v5. How the maintainers miss these obvious errors is beyond me. Example: the dchp.conf file default references the terminal server server interface as IP address 192.168.0.1, while the default install sets up terminal server server interface (eth0) to be IP address 192.168.0.254, go figure. Another problem is that there are tons of misleading and confusing documentation out there. I am very disapointed with Ubuntu LTSP at this point and have decided to go with something that really works, K12LTSP RHEL5.

Thanks again for your feedback. Sorry to vent, but I have spent countless hours on edubuntu to only expeience poor quality and performance. I think if I spend at least half that much time on K12LTSP and the Fedora K12Linux, I should have something working.

---

### Post by Tallwood on 2009-04-10
Just a heads up, this may or may not be the solution to the problem the OP was having, but it was something we ran in to during an LTSP install.

If you are using any type of smart switch device, make sure you go in to the management console and disable flood control.
We ran in to this problem with some Linksys PoE switches, where they had flood control enabled by default.

---

