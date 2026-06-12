---
title: "Problem establishing a vpn"
date: 2011-05-19
forum: Server Platforms
---

### Post by tapi0n on 2011-05-19
I installed the managent pack for pptp

I added a new vpn in [I]/etc/ppp/peers

[/I]then I added login information in [I]/etc/ppp/chap-secrets
[/I]
this vpn worked in a second. 

Now when tryin to add a new vpn I follow the same steps but the vpn doesn't work (it starts and it stops, but I can't ping the host).

When running (found on [http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml) )

```
pon **vpnname **debug dump logfd 2 nodetacht
```the output I get is this:

```
debug           # (from command line)
nodetach                # (from command line)
logfd 2         # (from command line)
dump            # (from command line)
noauth          # (from /etc/ppp/options)
name **name**# (from /etc/ppp/peers/gernaij)
remotename **remotename**              # (from /etc/ppp/peers/**vpnname**)
                # (from /etc/ppp/options)
pty pptp **xxx.xxx.xxx.xxx** --nolaunchpppd            # (from /etc/ppp/peers/**vpnname**)
crtscts         # (from /etc/ppp/options)
                # (from /etc/ppp/options)
asyncmap 0              # (from /etc/ppp/options)
lcp-echo-failure 4              # (from /etc/ppp/options)
lcp-echo-interval 30            # (from /etc/ppp/options)
hide-password           # (from /etc/ppp/options)
ipparam **vpnname**# (from /etc/ppp/peers/**vpnname**)
proxyarp                # (from /etc/ppp/options)
require-mppe-128                # (from /etc/ppp/peers/**vpnname**)
noipx           # (from /etc/ppp/options)
using channel 64
Using interface ppp1
Connect: ppp1 <--> /dev/pts/0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xc541e747> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x94 <accomp> <pcomp> <mru 1500> <magic 0xefddf976> <auth chap MS-v2>]
sent [LCP ConfAck id=0x94 <accomp> <pcomp> <mru 1500> <magic 0xefddf976> <auth chap MS-v2>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xc541e747> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0xc541e747]
rcvd [CHAP Challenge id=0x1 <bb1e68b236acdbc1ec831fb6f0c308d6>, name = ""]
sent [CHAP Response id=0x1 <427e2369951dd16e18e84dace79e6bb000000000000000000ce70e21d1ab2fbdf64f57be05959eeb3411b1d9e1157a7400>, name = "gil"]
rcvd [LCP EchoRep id=0x0 magic=0xefddf976]
rcvd [CHAP Success id=0x1 "S=8301D8B72CB7C0045EE762C2F2DAE70AE5588CAB"]
CHAP authentication succeeded
sent [CCP ConfReq id=0x1 <mppe +H -M +S -L -D -C>]
rcvd [IPCP ConfReq id=0x6d <addr 192.168.0.9> <compress VJ 0f 00>]
sent [IPCP TermAck id=0x6d]
rcvd [CCP ConfReq id=0x6d <mppe +H +M +S +L -D -C>]
sent [CCP ConfNak id=0x6d <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfAck id=0x1 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfReq id=0x6e <mppe +H -M +S -L -D -C>]
sent [CCP ConfAck id=0x6e <mppe +H -M +S -L -D -C>]
MPPE 128-bit stateless compression enabled
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]
rcvd [IPCP ConfNak id=0x1 <addr 192.168.0.188>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 192.168.0.188>]
rcvd [IPCP ConfAck id=0x2 <compress VJ 0f 01> <addr 192.168.0.188>]
rcvd [IPCP ConfReq id=0x6e <addr 192.168.0.9> <compress VJ 0f 00>]
sent [IPCP ConfAck id=0x6e <addr 192.168.0.9> <compress VJ 0f 00>]
Cannot determine ethernet address for proxy ARP
local  IP address 192.168.0.188
remote IP address 192.168.0.9
Script /etc/ppp/ip-up started (pid 13126)
Script /etc/ppp/ip-up finished (pid 13126), status = 0x0
```at this point the pon command is still running but the blinking cursor appears. 
When I use *Ctrl + c *the following is outputted:

```
Terminating on signal 2
Connect time 3.3 minutes.
Sent 0 bytes, received 0 bytes.
Script /etc/ppp/ip-down started (pid 13212)
MPPE disabled
sent [LCP TermReq id=0x2 "MPPE disabled"]
sent [LCP TermReq id=0x3 "MPPE disabled"]
Child process pptp 87.65.38.145 --nolaunchpppd (pid 13118) terminated with signal 2
Modem hangup
Connection terminated.
Waiting for 1 child processes...
  script /etc/ppp/ip-down, pid 13212
Script /etc/ppp/ip-down finished (pid 13212), status = 0x0
```
Now, the only thing that appears to be wrong is the following (taken from the first part of the output) 

```
Cannot determine ethernet address for proxy ARP
local  IP address 192.168.0.188
remote IP address 192.168.0.9
```But seeing how I get that in my first vpn too I don't think that's the issue.

when I do
```

pon vpnname
```the following is show when doing [I]tail /var/log/syslog

[/I]```
May 19 15:29:46 ubuntuNagios pptp[13368]: anon log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
May 19 15:29:46 ubuntuNagios pptp[13368]: anon log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
May 19 15:29:47 ubuntuNagios pptp[13368]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
May 19 15:29:47 ubuntuNagios pptp[13368]: anon log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
May 19 15:29:47 ubuntuNagios pptp[13368]: anon log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 944).
May 19 15:29:47 ubuntuNagios pppd[13360]: CHAP authentication succeeded
May 19 15:29:47 ubuntuNagios pppd[13360]: MPPE 128-bit stateless compression enabled
May 19 15:29:49 ubuntuNagios pppd[13360]: Cannot determine ethernet address for proxy ARP
May 19 15:29:49 ubuntuNagios pppd[13360]: local  IP address 192.168.0.188
May 19 15:29:49 ubuntuNagios pppd[13360]: remote IP address 192.168.0.9
```when running 

```
poff vpnname
```[I]
tail /var/log/syslog [/I]gives me this:

```
May 19 15:32:09 ubuntuNagios pppd[13360]: Connect time 2.4 minutes.
May 19 15:32:09 ubuntuNagios pppd[13360]: Sent 0 bytes, received 0 bytes.
May 19 15:32:09 ubuntuNagios pptp[13368]: anon log[callmgr_main:pptp_callmgr.c:258]: Closing connection (shutdown)
May 19 15:32:09 ubuntuNagios pptp[13368]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
May 19 15:32:09 ubuntuNagios pptp[13368]: anon log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
May 19 15:32:09 ubuntuNagios pppd[13360]: MPPE disabled
May 19 15:32:09 ubuntuNagios pppd[13360]: Child process pptp 87.65.38.145 --nolaunchpppd (pid 13361) terminated with signal 15
May 19 15:32:09 ubuntuNagios pppd[13360]: Modem hangup
May 19 15:32:09 ubuntuNagios pppd[13360]: Connection terminated.
May 19 15:32:09 ubuntuNagios pppd[13360]: Exit.

```
Has anyone experienced something alike? Maybe someone knows where (perhaps some log I'm forgetting) I can look for additional information?

Cheers

---

### Post by elico on 2011-05-19
i am having similar issue but it wasnt related to my settings.
also did tou made sure the routes?
use:
> route -n
and check the "defaultroute" in the peer vpn file.

---

### Post by tapi0n on 2011-05-19
ye I added the route using

```
route add -net xxx.xxx.xxx.xxx netmask xxx.xxx.xxx.xxx
```Someone who worked there pointed out that they're using a small firewall and that perhaps stopping the first vpn and running the second vpn would clarify things. But alas no luck there, even with the succesful vpn offline I couldn't get the second one up :(

But still adding the route wouldn't be necessary. Well it is to get to the network, but I can't even ping the host (which doesn't require you to add a route I'd guess?).

---

### Post by tapi0n on 2011-05-20
Ok so now for some reason I'm able to ping the host (the one whom I made a vpn with). But when adding the network address I'm still not able to get to the hosts located on the network. 

This is strange tho because when setting up the vpn in windows (ye I know, but it's what they work with :)) I am able to get to the hosts.

When checking syslog I'm also getting output like

```
May 20 09:45:22 ubuntuNagios pptp[4873]: anon log[logecho:pptp_ctrl.c:677]: Echo Request received.
May 20 09:45:22 ubuntuNagios pptp[4873]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 6 'Echo-Reply'
```

So I assume the vpn is actually correct?

---

### Post by tapi0n on 2011-05-20
I found the solution! This is a reply just to inform people who might experience the same thing later on. 

So seemed my vpn was being established correctly but when trying to access the network I couldn't get past the firewall.

When checking the firewall with a real time monitor we saw that the user that was establishing the vpn was being blocked for IP spoofing.

So checking the routes I saw that my vpn was being sent out of ppp1, but I was adding the route to the network on ppp0.

Deleted the route and added it again with the right interface. Solved the problem :) Hope this will be of help to someone someday.

Cheers!

---

