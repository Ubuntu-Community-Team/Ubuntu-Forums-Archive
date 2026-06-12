---
title: "HP T5700 Thin Client with Edubuntu 11.04"
date: 2011-11-30
forum: Server Platforms
---

### Post by sindhughanti on 2011-11-30
I have a HP t5700 thin client. how do I start setting up my client-server? i am using edubuntu 11.04 on my laptop as the server.

Please help!
Thanks!

---

### Post by newbie-user on 2011-11-30
First install ltsp-standalone on the server.  Then set up DHCP to tell the hp t5700 to boot to the server.  This option in dhcpd.conf will do that (or something similar depending on your specific setup):

          filename "/ltsp/i386/pxelinux.0";
          option root-path "/opt/ltsp/i386";

Then you build the client image using ltsp-build-client, ltsp-update-sshkeys.  After that, turn on the thin client and it should just work.  Check here for more information, in case I forgot some stuff:

[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

---

### Post by sindhughanti on 2011-12-01
> **newbie-user said:**
> First install ltsp-standalone on the server.  Then set up DHCP to tell the hp t5700 to boot to the server.  This option in dhcpd.conf will do that (or something similar depending on your specific setup):

          filename "/ltsp/i386/pxelinux.0";
          option root-path "/opt/ltsp/i386";

Then you build the client image using ltsp-build-client, ltsp-update-sshkeys.  After that, turn on the thin client and it should just work.  Check here for more information, in case I forgot some stuff:

[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)


Ok so I tried all the above, and all of them are already installed, as I installed LTSP along with edubuntu. I tried network booting (F12 while booting), but does not work. 

When i boot the client, I get the following options on the desktop (of the thin client OS):
1. Telnet
2. VMSTerm
3. Xterm
4. XTerm [fs]

Is there any way I can configure any of the above to work ?

Thanks

---

### Post by newbie-user on 2011-12-04
What are the contents of the /var/lib/tftpboot folder on the LTSP server?

Also, did you configure the "next-server" option in dhcpd.conf to tell the thin client which server hosts the LTSP installation?

The dhcp setting in dhcpd.conf for the client should look something like this:

        host thin-client {
          fixed-address 192.168.5.5;
          hardware ethernet 00:12:34:ab:cd:ef;
          next-server 192.168.5.2;
          filename "/ltsp/i386/pxelinux.0";
          option root-path "/opt/ltsp/i386";
        }

---

### Post by sindhughanti on 2011-12-05
> **newbie-user said:**
> What are the contents of the /var/lib/tftpboot folder on the LTSP server?

Also, did you configure the "next-server" option in dhcpd.conf to tell the thin client which server hosts the LTSP installation?

The dhcp setting in dhcpd.conf for the client should look something like this:

        host thin-client {
          fixed-address 192.168.5.5;
          hardware ethernet 00:12:34:ab:cd:ef;
          next-server 192.168.5.2;
          filename "/ltsp/i386/pxelinux.0";
          option root-path "/opt/ltsp/i386";
        }

the /var/lib/tftpboot folder contains the 'ltsp' directory. Should I include the above lines (host thin-client .... etc) into dhcpd.conf? Do i need to make any changes to the /etc/networks/interfaces file as well?

Thanks

---

### Post by newbie-user on 2011-12-07
Yes, you'll have to include those lines in the dhcp server's dhcpd.conf.  Just remember you'll have to edit the lines to accurately reflect your setup.

The line "next-server 192.168.5.2" assumes that your dhcp is hosted on a different server than your ltsp server.  The lines "filename /ltsp/i386/pxelinux.0" and "option root-path /opt/ltsp/i386" should not change unless you have a customized ltsp setup.

You will probably want to make your ltsp server's ip static and yes, you will have to edit /etc/network/interfaces to do that.

---

