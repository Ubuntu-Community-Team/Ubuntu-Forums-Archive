---
title: "Ubuntu LAMP server on a DMZ; Weird internet issue"
date: 2006-09-02
forum: Server Platforms
---

### Post by FredSambo on 2006-09-02
Hi everyone.

Let me give you some background:

I have a cable internet connection routed through my IPCop firewall.  I have a small Windows workgroup on the Green interface (internal network) with static IP addresses and DHCP set up for the occasional laptop user.  I have an Ubunutu web server set up on the Orange interface, which is the DMZ.  I also have a Blue interface (wireless) set up but it isn't enabled yet.

So A few weeks ago I backed up my configuration and installed ISPConfig on my server, and then I uninstalled it because it was a little more than what i wanted.

I reinstalled Ubuntu (LAMP) Server on my sytem and restored my files.  Then I set up the network interfaces and hosts files to work with my firewall.

So now I am happily back to a nice stable Ubuntu web server, with only one problem, I can't access the internet from the command line on the server.

I can:
ping computers on my windows network
ping all three interfaces on the firewall
ssh to the server
FTP to the server
Browse the server content on the web

I cannot:
ping yahoo.com or its IP address from the server (although i can from the windows network)
apt-get udate/upgrade the server

Now remember, using the exact same network configuration, it all worked fine yesterday.

Any ideas?  I am really just wondering how to approach this, from the IPCop side or from the Ubuntu side.  I an confused, any ideas would be appreciated.

---

### Post by FredSambo on 2006-09-02
Also, if I put the server on my Green network (internal) and set the network interfaces for DHCP it connects fine.  It has something to do with the DMZ but I can't see anything wrong with the IPCop configuration.  I mean I copied the network configuration on the Ubuntu server from a previously working installation on the exact same hardware.

---

### Post by FredSambo on 2006-09-15
well i finally resolved this issue, finally.

ok so here's the story:

it all started when i reinstalled the operating system on my  web server.  now, at one point during the life of the previous install, i installed the ipcop and put the machine on the DMZ; and evrything worked fine.  after the reinstall, with restored backup, the symptoms above arose.

here's why:

when i installed ubuntu, i plugged the server into the green network switch (internal network) so that the installation would be able to do its usual DHCP thing.  once everything was installed i set up my ip address and /etc/hosts files and plugged it into the DMZ.  well, during the installation my /etc/resolv.conf file was set so that the nameserver was the gateway IP of my green network.  for example:  

i have my server on: 
        
        address 192.168.1.2
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

and a network computer on the internal network is on, for example:
        
        address 192.168.10.200
        netmask 255.255.255.0
        network 192.168.10.0
        broadcast 192.168.10.255
        gateway 192.168.10.1

well my /etc/resolv.conf file on the web server was like this:

search fredsambo.com
nameserver 192.168.10.1 

so i changed it to this:

search fredsambo.com
nameserver 192.168.1.2

damn i'm embarassed about that.  i figured it out because i couldn't ping yahoo.com at all, it wouldn't even give me a 100% packet loss error.  so i went back through my debian walkthroughs and decided to try some random nameservers and they worked.

so glad it works now.

---

