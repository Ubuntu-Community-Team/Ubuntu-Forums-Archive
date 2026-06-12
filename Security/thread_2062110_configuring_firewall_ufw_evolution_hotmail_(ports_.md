---
title: "configuring firewall ufw evolution hotmail (ports 587 and 995 already open)"
date: 2012-09-24
forum: Security
---

### Post by lou21 on 2012-09-24
EDIT 25/09-2012
Thank you agillator for trying to help me. iptables are a bit above my head for now I'd rather stick with ufw for the moment.

However the problem was very simple. All I needed to do is realise that my computer is the one that needs to establish the connection for pop3s... So the rules:
995                        ALLOW IN    Anywhere
995                        ALLOW IN    Anywhere (v6)
need to be changed to...
995                        ALLOW OUT    Anywhere
995                        ALLOW OUT    Anywhere (v6)

In fact the set up I had previously seems to be more dangerous than not touching ufw. Since by default Ubuntu only allows connections to be set up outgoing.

-A pattern seems to be emerging I post a cry for help and then I work out what the problem was myself.

The original message is left below so that anyone now smart enough to read the man pages properly (like me) can google their way to answer...
EDIT OVER

Hi all,

So after reading the various stickies I thought it would probably be a good idea to set up a firewall...

Currently I have enabled the firewall using ufw and allowed the various ports that I can work out need to be open... The browser works fine and I can access hotmail in the browser but I can't get evolution to talk to hotmail (works fine with firewall disabled). The error message is "Could not connect to pop3.live.com: Connection timed out".

I am running ubuntu 12.04 (64bit) and am up to date on updates so I guess I have been upgraded to 12.04.1.
 
The output of: "sudo ufw status verbose" is as follows...
(NB evolution is fetching hotmail messages via pop3 with SSL encryption on port 995 and sending via smtp with TLS encryption on port 587 -  I know the usual port for smtp with TLS is 465 but this did not work even without the firewall)

Status: active
Logging: on (low)
Default: deny (incoming), deny (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
995                        ALLOW IN    Anywhere
995                        ALLOW IN    Anywhere (v6)

25,53,80,110,443/tcp       ALLOW OUT   Anywhere
53,67,68/udp               ALLOW OUT   Anywhere
587/tcp                    ALLOW OUT   Anywhere (*
25,53,80,110,443/tcp       ALLOW OUT   Anywhere (v6)
53,67,68/udp               ALLOW OUT   Anywhere (v6)
587/tcp                    ALLOW OUT   Anywhere (v6)

So I have three questions.

1/ My main priority is to get the mail working - currently I have to turn off the firewall to get my email and this is annoying and seems to defeat the point of having a firewall anyway. I guess that some other port needs to be open but I can't work out which one... I've trawled through several google searches to see if there are any solutions but either there aren't or I didn't recognize them.

2/ How do I monitor what the firewall has blocked? I've read the man page for netstat but can't figure this out. Maybe the answer to this could help me solve 1 for myself (teach a man to fish and all that).

3/ presumably this set up could be hardened further and if anyone has any suggestions then this would be nice.
I guess I could close port 25 (pop3 without encryption) and port 110 (smtp without encryption). 
Also can I somehow only allow traffic to certain addresses at the given ports? My laptop is used from several different networks of which I have no admin privileges. Would this cause problems? As far as I can see this has to be done by specifying the IP address, can it be done by specifying the address and allowing dns to resolve the IP address?

---

### Post by agillator on 2012-09-24
UFW is a simplified front end to iptables. To see what is really going on, try getting a log from iptables directly: sudo iptables -L -v -n --line-numbers. It may take a little deciphering, but that will tell you what is going on. The first column is the rule number in a chain, the second column is the number of times that rule has been used. You problem may be that you are trying to contact the server on its port 995 from one of your high ports and you firewall is blocking output on that high port. That shouldn't happen - the firewall should allow most anything to go out unless specifically blocked - but it is a possibility. Try opening port 995  for output and see if that makes a difference. You can try installing wireshark and track an attempt to contact the server, see what port is really being used. You can try going to something like ShieldsUp ([https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)) and run a test to be sure the ports you think are open really are. Then, try contacting the server and immediately upon failure check your system log (tail /var/log/syslog or /var/log/messages depending on your flavor of ubuntu) to see if there is any indication there. If all else fails, you can try turning off the firewall, making sure ALL rules are removed, manually setting all policies to DROP which will block everything in and out, add rules to log traffic and open ports on just the email ports you want to use, try contacting the server and check to iptables log (the command above). By process of elimination you should begin to get some information on what is really going on. 

See if any of these help.

---

