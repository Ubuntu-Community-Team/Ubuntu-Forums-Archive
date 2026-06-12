---
title: "IPBLock operated Before or After?"
date: 2010-11-09
forum: Security
---

### Post by VcDeveloper on 2010-11-09
Does anyone know if IIPBlock does it's operation before IPTables completes or after?  I'm using a KVM as a Router and GuideDog is Forwarding all HTTP/HTTPS to my KVM Web Server.  When looking at my web access.log I see CHINA doing it's stuff, but IPBlock is not blocking that IP (58.218.199.147) on the KVM Router.

Before doing the KVM Router and just receiving HTTP to mu KVM Web Server, I always had logs of CHINA, but now I don't.  So I'm assuming GuideDog is rendering IPBlock useless.

Any Suggestions? 

Can anyone let me know if your able to connect to my web server at [www.thegardenofedenblessing.com](www.thegardenofedenblessing.com) I would like to check even if this setup is working.  Because I have a seperate access-thegardenofedenblessing.log for my domain then I do for my localhost (access.log) and CHINA is showing up on my localhost log.

Thanks for your help!...

---

### Post by Diametric on 2010-11-10
I wasn't able to get to the site.

---

### Post by uljanow on 2010-11-10
Which KVM network configuration do you use ?

---

### Post by VcDeveloper on 2010-11-10
> **uljanow said:**
> Which KVM network configuration do you use ?

I'm using Ubuntu's **libvirt library**, w/**bridge-utils** and using the GUI Virtual Manager to manage the **kvm's**.  I have two NIC's, both connect to my 2Wire Router to the internet.  The **kvm's** are using the one of them (192.168.1.66), the main server 192.168.1.65..., I have HTTP forward to my **kvm Router**.....

My kvm network looks like this:

Ubuntu 10.10 Desktop Server w/qemu-kvm (main server) 192.168.1.65
----------| Ubuntu 10.10 Desktop Server - As my Router (connection HTTP forward to **Web server**) 192.168.1.70
----------| Ubuntu 9.10 Desktop Server - Web 192.168.1.71
----------| Ubuntu 10.10 Desktop Server - MySql 192.168.1.72
----------| Ubuntu 10.10 Desktop Server - Postfix 192.168.1.73

---

### Post by VcDeveloper on 2010-11-10
> **Diametric said:**
> I wasn't able to get to the site.

Thanks for your help! If I can't get this IP forwarding working, I'll just connect it directly until I do...

---

### Post by uljanow on 2010-11-10
Have you enabled the FORWARD chain in the ipblock.conf ? If that doesn't help installing iplist in the router kvm might work, although packets should traverse iptables before they reach kvms.

---

### Post by VcDeveloper on 2010-11-10
> **uljanow said:**
> Have you enabled the FORWARD chain in the ipblock.conf ? If that doesn't help installing iplist in the router kvm might work, although packets should traverse iptables before they reach kvms.

I do have it installed and I do have the Settings|Connection|Forward enabled, but my ipblock.conf is:

```

AUTOSTART="Yes"
IPTABLES_CHAIN_BLOCK="INPUT OUTPUT "
IPTABLES_CHAIN_ALLOW="INPUT OUTPUT"
LESS_MEMORY="No"
BLOCK_LIST="level1.gz ads-trackers-and-bad-pr0n.gz edu.gz spyware.gz china.p2p.gz japan.p2p.gz usa.p2p.gz spider.gz bogon.gz "
BLOCK_LIST_INPUT=""
BLOCK_LIST_OUTPUT=""
BLOCK_LIST_FORWARD=""
ALLOW_LIST=""
ALLOW_LIST_INPUT="allow-perm.p2p allow-temp.p2p"
ALLOW_LIST_OUTPUT="allow-perm.p2p allow-temp.p2p"
ALLOW_LIST_FORWARD=""
IGN_TCP_INPUT=""
IGN_UDP_INPUT=""
IGN_TCP_OUTPUT="http https "
IGN_UDP_OUTPUT="domain"
IGN_TCP_FORWARD=""
IGN_UDP_FORWARD=""
IGN_PROTO_INPUT=""
IGN_PROTO_OUTPUT=""
IGN_PROTO_FORWARD=""
IPLIST_LISTDIR="/var/cache/iplist"
LOG_FILE="/tmp/ipblock.log"
LOG_LEVEL="match"
LOG_IPTABLES="No"
VERBOSE="Yes"
URL_FILE="/etc/ipblock.lists"
UPDATE_STAMP="/var/cache/iplist/.update-stamp"
UPDATE_INTERVAL="1"
http_proxy=""
GUI_START_HIDDEN="No"
GUI_AUTOSCROLL="Yes"
GUI_THEME="Gtk"
GUI_WHITELIST_PERM="/var/cache/iplist/allow-perm.p2p"
GUI_WHITELIST_TEMP="/var/cache/iplist/allow-temp.p2p"
```What do the forwards mean here and do they have anything to do with the Settings|Connection|Forward checkbox?

---

### Post by VcDeveloper on 2010-11-10
What do you think about this..., I was about to close down my Kvm Router and just direct connect to the Kvm Web.  And, while I had the **ipblock.conf** open in **gedit** I had to reload it after closing IPBlock.  I notice this change:

IPTABLES_CHAIN_BLOCK="INPUT OUTPUT "

**to**

IPTABLES_CHAIN_BLOCK="INPUT OUTPUT FORWARD"

...this tells me IPBlocks is not updating the **.conf** dynamically.  So, let me see if it will do it's blocking now....

---

### Post by VcDeveloper on 2010-11-10
Oh yea.... I notice something else!..  How do I create the:

BLOCK_LIST_FORWARD=""

.....do I just copy the BLOCK_LIST into it?  ....I will give it a try!

---

### Post by VcDeveloper on 2010-11-10
Yea, that is what I needed to do, IPBlock needs to be closed and restart the iplist deamon..., 

.....buy the way, how do you restart it without rebooting.  Because, I tried **service iplist restart** and **/etc/init.d/iplist restart** with no success.

---

