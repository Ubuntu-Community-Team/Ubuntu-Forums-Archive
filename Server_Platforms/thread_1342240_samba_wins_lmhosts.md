---
title: "samba wins lmhosts"
date: 2009-11-30
forum: Server Platforms
---

### Post by cdenley on 2009-11-30
I'm trying to configure samba to act as a WINS server, then use /etc/samba/lmhosts to create custom entries. I have no idea why it won't work.

```

cdenley@ns:~$ grep "^[^;#]" /etc/samba/smb.conf
[global]
   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
   wins support = yes
   dns proxy = no
   name resolve order = lmhosts
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   unix password sync = yes
map to guest = bad user
   socket options = TCP_NODELAY
cdenley@ns:~$ nmblookup -U 127.0.0.1 -R ns
querying ns on 127.0.0.1
192.168.0.5 ns<00>
cdenley@ns:~$ nmblookup -U 127.0.0.1 -R winstest
querying winstest on 127.0.0.1
name_query failed to find name winstest
cdenley@ns:~$ cat /etc/samba/lmhosts
192.168.0.1 winstest

```

---

### Post by cdenley on 2009-12-01
Nevermind. I just created my own simple WINS server. It only sends a response for a specific computer name, and replies with whichever IP I choose. I can even reply with a different IP depending on the source network.
```

#!/usr/bin/python
from twisted.internet.protocol import DatagramProtocol
from twisted.internet import reactor, protocol
import binascii


class Wins(DatagramProtocol):
    def datagramReceived(self, data, address):
        hostname="NETBIOS_NAME"
        debug=True
        ip=[0,0,0,0]
        index=data.find(chr(0),13)
        if index<14:
            if debug:
                print "null terminator not found"
            return
        temp=data[13:index]
        name=""
        for i in range(0,len(temp),2):
            if i+1>=len(temp):
                if debug:
                    print "uneven nibbles"
                return
            name+=chr((ord(temp[i])-65)*16+(ord(temp[i+1])-65))
        name=name.rstrip(" "+chr(28)+chr(0))
        if name.upper()!=hostname:
            if debug:
                print "not resolving \""+name+"\""
            return
        if address[0][:7]=="10.3.0.":
            ip=[10,4,0,1]
        else:
            if debug:
                print "ignoring "+address[0]
            return
        reply=data[:2]
        reply+=binascii.unhexlify("8580000000010000")
        reply+=data[len(reply):]
        reply+=binascii.unhexlify("0000000000066000")
        for num in ip:
            reply+=chr(num)
        self.transport.write(reply, address)
        if debug:
            print "sent reply for "+name
            print "to "+address[0]+":"+str(address[1])


def main():
    reactor.listenUDP(137,Wins())
    reactor.run()

# this only runs if the module was *not* imported
if __name__ == '__main__':
    main()

```

---

### Post by beadrifle on 2010-08-02
Hello, I'm the network admin for a network of about 400 users, 95% of whom are windows users. We use a single subnet and have poor equipment; desktops being forced to run as servers. Our servers run on ubuntu with a shorewall machine and a squid cache proxy server. I've experienced the problem of NBNS storm for a long time now and I've tried a host of solutions (such as passing around .reg files to clients and so on) but none of them are a fool proof solution.  The problem with the NBNS requests is that the shorewall machine is finally diverting traffic to a cheap router which has no rules and is being merely used as a convertor of sorts, simply routing all traffic from one of its interfaces (RJ45) to our leased line modem, a V.35.   So the issue is that this router hangs very frequently when the NBNS requests (and other junk windows traffic such as SSDP, LLMNR, MDNS, IPv6 tunnelling, none of which are used on our network) and we are having to constantly restart it.  Recently I installed Samba and turned on options to make it the WINS server and the master local browser. But this isn't really stopping the requests from going to the router. I haven't configured an LMHOSTS file yet, and wanted to know if there's any way of generating that automatically, manually adding 400 odd clients will be quite a cumbersome task. We use static IPs. This is my samba config file. I merely use it as a WINS server and i've hashed out all rules regarding file and printer sharing.

[PHP][global]
        log file = /var/log/samba/log.%m
        name resolve order = bcast lmhosts host wins
        interfaces = 192.168.4.0/22 eth1
        hosts allow = 192.168.4.0/22 127.0.0.1
        smb ports = 139
        wins support = yes
        dns proxy = no
        netbios name = sentinel
        security = user
        default = global
        local master = yes
        preferred master = yes
        workgroup = WORKGROUP
        domain master = yes
        os level = 255
        hosts deny = ALL
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        max log size = 1000[/PHP]
 ** More importantly, what does the program you created do? Will it in any way help my issue? ** Any help would be immensely appreciated as this program has been troubling the network for nearly a year now. Thanks!

---

