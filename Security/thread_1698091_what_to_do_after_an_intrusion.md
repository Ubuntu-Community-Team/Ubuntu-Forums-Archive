---
title: "what to do after an intrusion?"
date: 2011-03-01
forum: Security
---

### Post by RMS71 on 2011-03-01
I have a Ubuntu 10.04 headless fileserver running in my home that sits behind my router which does the NAT translation. This morning I was looking at the router's log file and noticed a certain IP address was able to gain LAN access on port 2222. That just happens to be the port my SSH server is listening on! A whois search revealed that IP address is in Germany.

As soon as I found this out I stopped forwarding all ports to this machine in my router. So now I'm wondering how to tell what had happened, what information this person was able to obtain, and if he left any goodies behind that could hurt me? I've read through some of the logs on my computer and haven't been able to find much at all.

I did have some personal information on the hard drives, but that information is encrypted. I'm thinking if they were able to get my SSH password then that information probably isn't safe either (assuming they have some of it).

This whole experience has me a bit paranoid now. :(

Any suggestions?

---

### Post by mazato on 2011-03-01
If you would want to do some forensics on those machines, I would image the hard drives  and  then I would reinstall everything on all the compromised boxes.
As for how to do the forensics on those machines there are some tutorial online, actually there are hundreds depending on your system.
good luck!!

---

### Post by unspawn on 2011-03-02
> **RMS71 said:**
> I'm wondering how to tell what had happened, what information this person was able to obtain, and if he left any goodies behind that could hurt me?
* It wouldn't hurt to get acquainted with the (deprecated) [CERT Intruder Detection Checklist]("http://web.archive.org/web/20080109214340/http://www.cert.org/tech_tips/intruder_detection_checklist.html"). If nothing else it at least provides you with basic commands to run.

Since you've already mitigated the situation by closing off access, and knowing the IP address and time the port was accessed there's a few things you could do:
* grep your router log for earlier occurrences of:
- TCP/2222 access,
- the IP accessing your router and LAN machines.

* grep your machine (or machines) system logs (see /etc/.*syslog.*.conf) for:
- the IP address,
- any failed logins,
- any successful logins. 

Grepping for IP addresses tells you if others tried to access any services (don't narrow your scope too early on) and looking for failed logins may be an indication of how, if and when the machine was scanned (exposure time frame). For any successful login note the account name and look for any sudo commands, read their shell history (if any and root as well) and look for files created or modified in the time frame.

Simultaneously you could:
0) compare any items with backups you made prior to the first access (if you didn't make backups then you now know one good reason why you should have),
1) verify integrity of core system binaries using debsums (though IIRC Ubuntu nor Debian by default installs 'debsums') or using any file integrity checker like Aide, Samhain or even tripwire you have deployed prior to the (perceived) incident (and if you didn't deploy one, well, another good reason why),
2) run 'logwatch' on your system logs (and --archives) to catch any anomalies you might have missed,
3) run the commands from the CERT Intruder Detection Checklist if you find anything suspicious.

There's more you can do but it would be better to pace things, post back actual log lines or errors (if any) and results before talking next stage as I don't want to speculate and re-installing (or talking security measures) only makes sense if you have determined an account was actually (not) accessed and the system was (not) modified. If attaching doesn't work (size) use pastebin and post the URI. Good luck.

---

### Post by brian_p on 2011-03-02
> **RMS71 said:**
> I have a Ubuntu 10.04 headless fileserver running in my home that sits behind my router which does the NAT translation. This morning I was looking at the router's log file and noticed a certain IP address was able to gain LAN access on port 2222. That just happens to be the port my SSH server is listening on! A whois search revealed that IP address is in Germany.

Please provide the portion of the log which gives cause for concern. Also, how many characters are in your password?

---

### Post by RMS71 on 2011-03-02
Thanks for the replies, especially unspawn for taking the time for all the info.

In retrospect setting up public and private keys and logging in without a password would have been a good idea.

From my router log:

> [LAN access from remote] from 178.162.165.21:2046 to 192.168.0.5:2222, Monday, February 28,2011 20:27:26
[LAN access from remote] from 178.162.165.21:2041 to 192.168.0.5:2222, Monday, February 28,2011 20:27:25
[LAN access from remote] from 178.162.165.21:12200 to 192.168.0.5:2222, Monday, February 28,2011 20:12:10From /var/log/auth.log

> Feb 28 20:27:26 ubuntu sshd[27238]: Did not receive identification string from 178.162.165.21
Feb 28 20:27:27 ubuntu sshd[27240]: Did not receive identification string from 178.162.165.21I had a 9 character alpha-numeric password

---

### Post by Kinstonian on 2011-03-02
If you searched your auth.log for 178.162.165.21 and all you found were those "Did not receive identification string" messages then you have probably only been scanned by 178.162.165.21 and haven't been compromised.

---

### Post by pafufta503 on 2011-03-02
doing a google search on the IP address comes up with some interesting information:

[http://www.ipillion.com/ip/178.162.165.21](http://www.ipillion.com/ip/178.162.165.21) <-- there are other users whom have experienced the same access attempts

contact the ip's ISP at [email]abuse@netdirekt.de[/email] and let them know.  this may be the step required to having their ISP revoke their internet service.  more information about the users of that IP:
> [Querying whois.arin.net]
[Redirected to whois.ripe.net:43]
[Querying whois.ripe.net]
[whois.ripe.net]
% This is the RIPE Database query service.
% The objects are in RPSL format.
%
% The RIPE Database is subject to Terms and Conditions.
% See [http://www.ripe.net/db/support/db-terms-conditions.pdf](http://www.ripe.net/db/support/db-terms-conditions.pdf)

% Note: this output has been filtered.
% To receive output for a database update, use the "-B" flag.

% Information related to '178.162.165.0 - 178.162.165.63'

inetnum: 178.162.165.0 - 178.162.165.63
netname: NETDIRECT-NET
descr: NETDIRECT-NET
remarks: INFRA-AW
country: DE
admin-c: WW200-RIPE
tech-c: SR614-RIPE
status: ASSIGNED PA
mnt-by: NETDIRECT-MNT
mnt-lower: NETDIRECT-MNT
mnt-routes: NETDIRECT-MNT
source: RIPE # Filtered

person: Wiethold Wagner
address: netdirekt e. K.
address: Kleyer Strasse 79 / Tor 14
address: 60326 Frankfurt
address: DE
phone: +49 69 90556880
fax-no: +49 69 905568822
abuse-mailbox: [email]abuse@netdirekt.de[/email]
nic-hdl: WW200-RIPE
mnt-by: NETDIRECT-MNT
source: RIPE # Filtered

person: Simon Roehl
address: netdirekt e. K.
address: Kleyer Strasse 79 /Tor 14
address: 60326 Frankfurt
address: DE
phone: +49 69 90556880
fax-no: +49 69 905568822
abuse-mailbox: [email]abuse@netdirekt.de[/email]
nic-hdl: SR614-RIPE
mnt-by: NETDIRECT-MNT
source: RIPE # Filtered

% Information related to '178.162.128.0/17AS28753'

route: 178.162.128.0/17
descr: ORG-nA8-RIPE
origin: AS28753
org: ORG-nA8-RIPE
mnt-lower: NETDIRECT-MNT
mnt-routes: NETDIRECT-MNT
mnt-by: NETDIRECT-MNT
source: RIPE # Filtered

organisation: ORG-nA8-RIPE
org-name: netdirect
org-type: LIR
address: netdirekt e. K.
Kleyer Strasse 79 / Tor 14
60326 Frankfurt
Germany
phone: +49 69 90556880
fax-no: +49 69 905568822
admin-c: SR614-RIPE
admin-c: WW200-RIPE
mnt-ref: NETDIRECT-MNT
mnt-ref: RIPE-NCC-HM-MNT
mnt-by: RIPE-NCC-HM-MNT
source: RIPE # Filtered

---

### Post by pafufta503 on 2011-03-02
also, a blog post from the owner of netdireckt concerning criminal use of their services.

[http://hphosts.blogspot.com/2009/10/crimeware-friendly-isps-netdirekt.htm](http://hphosts.blogspot.com/2009/10/crimeware-friendly-isps-netdirekt.htm)

---

