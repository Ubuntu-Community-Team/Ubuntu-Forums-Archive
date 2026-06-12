---
title: "DHCP + BIND9 + MAC to IP"
date: 2012-03-10
forum: Server Platforms
---

### Post by adamjseed on 2012-03-10
Hello all,

I have a dhcp and bind9 server running in ubuntu 10.04. It is all working great, new servers get a dynamic IP and their dns record gets updated.

My issue is when I bind a mac to an ip on my dhcp server its hostname doesn't get registered with the dns server.

My dhcpd.conf has an entry like:

host server-test {
    hardware ethernet 00:B0:CF:8B:49:37;
    fixed-address 192.168.0.19;
}

My server (with the mac address 00:B0:CF:8B:49:37) gets the ip 192.168.0.19 but i can not access it via server-test.example.com.

Does anyone know how i can send the hostname to my dns server and create a dns record like they dynamically assigned ip's?

---

### Post by Doug S on 2012-03-10
If you assign IP address by MAC address, then you will also find that your leases file will not contain information about that IP lease either. All I am saying it that dhcpd handles regualar pool address assignment differently than based on MAC address.
Perhaps it is assumed that the name will be in the db.example.com file already because it is already a known MAC address. (That is the way I have my network setup, the pool space is only for guests, otherwise assignment is by MAC address and I already assigned the name).
I know this doesn't actually answer your question, but maybe it helps a little.

---

### Post by adamjseed on 2012-03-11
Hi Doug,

I think your right, what you say will work just fine, I was just trying to avoid editing my dns zones. Thanks for pointing this out, I didn't even think to do that!

---

### Post by Jonathan L on 2012-03-11
> Does anyone know how i can send the hostname to my dns server and create a dns record like they dynamically assigned ip's?Hi Adam


Generally for network infrastructure (DNS, DHCP, routers, ethernet  switches) it saves on headaches to have central configuration and make  the machines accept the central configuraiton on reboot. 

And so for servers, I'd generally recommend doing it the other way round: regard the DNS/DHCP as correct and make the server use the name it gets.

I think the best way is DHCP's "option host-name".  From the manual pages,  I've noted below some of the trickier bits of this kind of config:

**From man dhcpd.conf** section "The host statement":[INDENT]        hostname should be a name identifying the host.  [COLOR=Red]If a  hostname  option[/COLOR]
[COLOR=Red]        is not specified for the host, hostname is used.[/COLOR]
[/INDENT]**From man dhcpd-options**

      option host-name string;[INDENT]          This  option  specifies  the name of the client.  The name may or may
         not be qualified with the local domain name (it is preferable to  use
         the domain-name option to specify the domain name).  See RFC 1035 for
         character set restrictions.  [COLOR=Red]This option is only honored by dhclient-[/COLOR]
[COLOR=Red]          script(8) if the hostname for the client machine is not set.[/COLOR]
[/INDENT]fixed-address address [, address ... ];[INDENT]          The fixed-address declaration is used to assign one or more fixed  IP
         addresses  to a client.  It should only appear in a host declaration.
         If more than one address is supplied, then when the client boots,  it
         will be assigned the address that corresponds to the network on which
         it is booting.  If none of the addresses in the fixed-address  state-
         ment are valid for the network to which the client is connected, that
         client will not match the host  declaration  containing  that  fixed-
         address  declaration.   [COLOR=Red]Each address in the fixed-address declaration[/COLOR]
         should be either an IP address [COLOR=Red]or a domain name that resolves[/COLOR] to  one
         or more IP addresses.
[/INDENT]All off which means you should probably have:

[LIST]
[*] No /etc/hostname on the host
[*] DHCP: [FONT=Courier New]host server-test { hardware ethernet 00:B0:CF:8B:49:37; fixed-address server-test; }[/FONT]
[*]DNS: [FONT=Courier New]server-test A 192.168.0.19[/FONT]
[/LIST]
As I've often got mixed operating systems and try to find general solutions, I'll confess I've often resorted to ugly things in rc.local.  For example, for a current project with a small number of servers (about 10), they are set up to copy /etc/hosts from a central machine, look their name up and use it.  To make this a little less ugly you could use `dig -x $MYIPADDR +short` instead of the /etc/hosts:

Here's a snippet of one of the uglier setups (run from rc.local as root, in /tmp): 
```
logger -s "** Installing host file"
wget http://$SERVER//hosts
cp hosts /etc/hosts

logger -s "** Hostname"
addr="`ifconfig eth0 | tr ':' ' ' | awk '/inet addr/{print $3; exit;}'`"
name="`awk -v addr=$addr '($1==addr) {print $2;exit;}' /etc/hosts`"
hostname "$name"
```Anyways, hope that gives you some ideas for solving this for your network.

Regards,
Jonathan.

---

