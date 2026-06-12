---
title: "DNS help on AWS EC2 Ubuntu instance server"
date: 2016-08-05
forum: Server Platforms
---

### Post by gte861s on 2016-08-05
Hello, I would like to request some help. I am setting up and EC2 Ubuntu mail server and it is named mail.tp2engineering.com. My domain registrar is GoDaddy and I have my records there pointing to Route53 DNS. 


Here are my DNS record entries:


```
tp2engineering.com. A <Elastic IP address>
tp2engineering.com. MX mail.tp2engineering.com.
tp2engineering.com. NS ns-381.awsdns-47.com. ns-557.awsdns-05.net. ns-1416.awsdns-49.org. ns-1704.awsdns-21.co.uk.


tp2engineering.com. SOA ns-381.awsdns-47.com. awsdns-hostmaster.amazon.com. 1 7200 900 1209600 86400


tp2engineering.com. SPF "v=spf1 mx a ?all"
mail._domainkey.tp2engineering.com. TXT "v=DKIM1; h=sha256; k=rsa; s=email; p=xxx"


_text_.tp2engineering.com. TXT "_text_tp2engineering.com." "tp2engineering.com." "mail.tp2engineering.com." "www.tp2engineering.com."
```


I'm not receiving emails on the server with this configuration. I have tested the server internally that it can send/receive messages to proper inboxes. I have the security group AMIs setup and on. Is there anything obvious I have wrong and I'm overlooking? Perhaps something more subtle?


Edited by: gte861s on Aug 5, 2016 2:17 PM

---

### Post by wildmanne39 on 2016-08-05
*Thread moved to **Server Platforms**.*

---

### Post by Graham_Willis on 2016-08-06
[quote="gte861s"]Is there anything obvious I have wrong and I'm overlooking?[/quote]

The missing trailing dot in mail.tp2engineering.com in your MX record.

---

### Post by darkod on 2016-08-06
I don't understand. According to this it looks like you are trying to set up your own DNS server (zone).

But GoDaddy offers very nice DNS service and you already have your domain there. You can control DNS records very easy there. No need to bother with configuring your own DNS server.

Also, if you have a firewall on the VM (and you should because it has public IP), you need to make sure you allow the ports needed for mail communication (TCP 25, 465, 587).

---

### Post by gte861s on 2016-08-06
> **Wild Man said:**
> *Thread moved to **Server Platforms**.*

Corrected the typos. All the dots are there in my record.

---

### Post by gte861s on 2016-08-06
> **darkod said:**
> Also, if you have a firewall on the VM (and you should because it has public IP), you need to make sure you allow the ports needed for mail communication (TCP 25, 465, 587).

Yes, I have a FW on the VM. I have security groups setup and opened ports for the appropriate services back to my network (SSH, SMTP, SMTPS, IMAP, IMAPS).

As to your other comment, I'm moving away from GoDaddy toward AWS for all my needs.

---

### Post by Habitual on 2016-08-06
Ports aren't "opened", exactly:
25/tcp filtered smtp

Filtered gets, well filtered.
and if the edit was recent enough, might have to wait for cache to "catch up" or propagate.

---

### Post by darkod on 2016-08-06
I don't understand the output from your first post, is that something from AWS and not from bind? If it's AWS you should really ask for help in their forums/support, there will be people that know it in detail.

If you are using bind to set up your own dns server please post the zone file content, because what you have in port #1 doesn't look like it.

One thing I can notice is that there is no mail A record listed. You have the MX pointing to mail.tp2engineering.com but there is no A record for mail pointing to the VM public IP. You need that too.

---

### Post by gte861s on 2016-08-06
> **darkod said:**
> I don't understand the output from your first post, is that something from AWS and not from bind? If it's AWS you should really ask for help in their forums/support, there will be people that know it in detail.

If you are using bind to set up your own dns server please post the zone file content, because what you have in port #1 doesn't look like it.

One thing I can notice is that there is no mail A record listed. You have the MX pointing to mail.tp2engineering.com but there is no A record for mail pointing to the VM public IP. You need that too.

Thanks darkrod. I have a forum post* on that user community as well but it doesn't have near the traffic of the Ubuntu forums. Yes, the content from above is on AWS and not my own DNS bind. I have added an A record for mail.tp2engineering.com which is resolving now which points to the same ip address as tp2engineering.com. Still no mail so I'm going to explore the firewalls more.

*edit to add "post" above.

---

### Post by gte861s on 2016-08-06
Here is the output of my iptables -L command:

```
[COLOR=#000000][FONT=Menlo]Chain INPUT (policy ACCEPT)target     prot opt source               destination         [/FONT]
[FONT=Menlo]ACCEPT     all  --  mail.tp2engineering.com  anywhere            [/FONT]
[FONT=Menlo]           tcp  --  anywhere             anywhere             tcp dpt:imaps state NEW recent: SET name: imapssl side: source mask: 255.255.255.255[/FONT]
[FONT=Menlo]LOG_AND_DROP  tcp  --  anywhere             anywhere             tcp dpt:imaps state NEW recent: UPDATE seconds: 10 hit_count: 20 name: imapssl side: source mask: 255.255.255.255[/FONT]
[FONT=Menlo]ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:imaps[/FONT]
[FONT=Menlo]           tcp  --  anywhere             anywhere             tcp dpt:submission state NEW recent: SET name: imap side: source mask: 255.255.255.255[/FONT]
[FONT=Menlo]LOG_AND_DROP  tcp  --  anywhere             anywhere             tcp dpt:submission state NEW recent: UPDATE seconds: 10 hit_count: 20 name: imap side: source mask: 255.255.255.255[/FONT]
[FONT=Menlo]ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:submission[/FONT]
[FONT=Menlo]           tcp  --  anywhere             anywhere             tcp dpt:urd state NEW recent: SET name: smtps side: source mask: 255.255.255.255[/FONT]
[FONT=Menlo]LOG_AND_DROP  tcp  --  anywhere             anywhere             tcp dpt:urd state NEW recent: UPDATE seconds: 10 hit_count: 20 name: smtps side: source mask: 255.255.255.255[/FONT]
[FONT=Menlo]ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:urd[/FONT]
[FONT=Menlo]           tcp  --  anywhere             anywhere             tcp dpt:smtp state NEW recent: SET name: smtp side: source mask: 255.255.255.255[/FONT]
[FONT=Menlo]LOG_AND_DROP  tcp  --  anywhere             anywhere             tcp dpt:smtp state NEW recent: UPDATE seconds: 10 hit_count: 20 name: smtp side: source mask: 255.255.255.255[/FONT]
[FONT=Menlo]ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:smtp[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Chain FORWARD (policy ACCEPT)[/FONT]
[FONT=Menlo]target     prot opt source               destination         [/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Chain OUTPUT (policy ACCEPT)[/FONT]
[FONT=Menlo]target     prot opt source               destination         [/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Chain LOG_AND_DROP (4 references)[/FONT]
[FONT=Menlo]target     prot opt source               destination         [/FONT]
[FONT=Menlo]LOG        all  --  anywhere             anywhere             LOG level debug prefix "iptables deny: "[/FONT]
[FONT=Menlo]DROP       all  --  anywhere             anywhere[/FONT][/COLOR][COLOR=#FFFFFF][FONT=Menlo]

```[/FONT][/COLOR]

---

### Post by darkod on 2016-08-06
This is difficult to follow, but I think you are blocking the mail by your rules. To make it more readable try:
```
sudo iptables -L -n -v
```

And be careful not to lose the formatting when copying the output in the code tags.

---

### Post by gte861s on 2016-08-06
Using iptables -L -n -v...sorry but it looks hard to read even from the console. Thank you in advance for helping with this...I'm certainly not very versed in this part and need to get smarter...I'm reading up more in iptables now while seeking the help from the community:

```

[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]Chain INPUT (policy ACCEPT 47053 packets, 46M bytes)[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000] pkts bytes target     prot opt in     out     source               destination         [/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    0     0 ACCEPT     all  --  eth0   *       52.36.208.29         0.0.0.0/0           [/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    0     0            tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:993 state NEW recent: SET name: imapssl side: source mask: 255.255.255.255[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    0     0 LOG_AND_DROP  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:993 state NEW recent: UPDATE seconds: 10 hit_count: 20 name: imapssl side: source mask: 255.255.255.255[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:993[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    0     0            tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:587 state NEW recent: SET name: imap side: source mask: 255.255.255.255[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    0     0 LOG_AND_DROP  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:587 state NEW recent: UPDATE seconds: 10 hit_count: 20 name: imap side: source mask: 255.255.255.255[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:587[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    0     0            tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:465 state NEW recent: SET name: smtps side: source mask: 255.255.255.255[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    0     0 LOG_AND_DROP  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:465 state NEW recent: UPDATE seconds: 10 hit_count: 20 name: smtps side: source mask: 255.255.255.255[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:465[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    3   180            tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:25 state NEW recent: SET name: smtp side: source mask: 255.255.255.255[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    0     0 LOG_AND_DROP  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:25 state NEW recent: UPDATE seconds: 10 hit_count: 20 name: smtp side: source mask: 255.255.255.255[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]   69  3967 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:25[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000] pkts bytes target     prot opt in     out     source               destination         [/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]Chain OUTPUT (policy ACCEPT 25208 packets, 3548K bytes)[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000] pkts bytes target     prot opt in     out     source               destination         [/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]Chain LOG_AND_DROP (4 references)[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000] pkts bytes target     prot opt in     out     source               destination         [/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 7 prefix "iptables deny: "[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0[/COLOR][/FONT][/COLOR]

```

---

### Post by darkod on 2016-08-06
Hmmm, I forgot for a moment that this is from AWS. You don't need to modify iptables directly, instead you need to work with the security settings for your VM.

But looking at your iptables listed above, you can see that the VM is actually receiving traffic on port 25, which is used for receiving mail. You can clearly see that in the last line of the INPUT chain. The rule to accept port 25 from any source already has allowed 69 packets or 3967 bytes.

If you run it again, that number should be higher now, unless it got reset by reloading the iptables rules.

So you might have misconfiguration in postfix too, if it's still not receiving mail. And you should test with telnet from your home PC or similar. Something like:
```
telnet mail.domain.com 25
```

Should open a connection to your mail server. If it does, the security/firewall rules are OK.

---

### Post by gte861s on 2016-08-06
So I can connect from localhost on port 25 and 587 to my mail server; however, from my home network I'm unable to establish a connection. I have verified my /etc/postfix/main.cf has inet_interfaces = all. There is also a process of paperwork to fill out for AWS which allows one to have port 25 access (i.e. - don't block this port, I'm not a spammer), which I have also completed. I don't know where to go from here. Any emails I send from a gmail account come back and state that "The recipient server did not accept our requests to connect" with a socket error.

---

### Post by SeijiSensei on 2016-08-06
I cannot connect to ports 25, 587, or 143 on mail.tp2engineering.com.

```

$ host -t mx tp2engineering.com
tp2engineering.com mail is handled by 10 mail.tp2engineering.com.

$ telnet mail.tp2engineering.com 25
Trying 52.36.208.29...
^C
$ telnet mail.tp2engineering.com 587
Trying 52.36.208.29...
^C
$ telnet mail.tp2engineering.com 143
Trying 52.36.208.29...

```
Either these ports are firewalled or nothing is listening on them.  I'm guessing the former.

Running nmap against the host reports that it could be down or it could just be ignoring pings.

I ran these tests from my outbound SMTP server which sits directly on the Internet.

---

### Post by gte861s on 2016-08-06
> **SeijiSensei said:**
> I
Either these ports are firewalled or nothing is listening on them.  I'm guessing the former.


Thanks for verifying that it doesn't work from your connection as well. At least that confirms there isn't something on my end of the network. As far as the ports being firewall...AWS EC2 instances use a GUI based Security Groups where you setup up ports to be open which then add the rules to your instance...So on the security group, I have opened up the ports 993, 25, 22, 143, 587, and 465. Here is the output from my iptables 

```
[COLOR=#000000][FONT=Menlo]sudo iptables -L -v -n[/FONT][/COLOR][COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]Chain INPUT (policy ACCEPT 48905 packets, 46M bytes)[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000] pkts bytes target     prot opt in     out     source               destination         [/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    0     0 ACCEPT     all  --  eth0   *       52.36.208.29         0.0.0.0/0           [/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    1    60            tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:993 state NEW recent: SET name: imapssl side: source mask: 255.255.255.255[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    0     0 LOG_AND_DROP  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:993 state NEW recent: UPDATE seconds: 10 hit_count: 20 name: imapssl side: source mask: 255.255.255.255[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]   10  1012 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:993[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    1    60            tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:587 state NEW recent: SET name: imap side: source mask: 255.255.255.255[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    0     0 LOG_AND_DROP  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:587 state NEW recent: UPDATE seconds: 10 hit_count: 20 name: imap side: source mask: 255.255.255.255[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    6   326 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:587[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    0     0            tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:465 state NEW recent: SET name: smtps side: source mask: 255.255.255.255[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    0     0 LOG_AND_DROP  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:465 state NEW recent: UPDATE seconds: 10 hit_count: 20 name: smtps side: source mask: 255.255.255.255[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:465[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    5   300            tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:25 state NEW recent: SET name: smtp side: source mask: 255.255.255.255[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    0     0 LOG_AND_DROP  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:25 state NEW recent: UPDATE seconds: 10 hit_count: 20 name: smtp side: source mask: 255.255.255.255[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]   81  4619 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:25[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000] pkts bytes target     prot opt in     out     source               destination         [/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]Chain OUTPUT (policy ACCEPT 26417 packets, 3740K bytes)[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000] pkts bytes target     prot opt in     out     source               destination         [/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]Chain LOG_AND_DROP (4 references)[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000] pkts bytes target     prot opt in     out     source               destination         [/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 7 prefix "iptables deny: "[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0[/COLOR][/FONT][/COLOR]
```

As for listening on the ports, I have my postfix/main.cf file set to inet_interfaces = all. I'm not really sure where the issue lies either.

---

### Post by SeijiSensei on 2016-08-06
It certainly looks like you received 81 packets of incoming traffic on SMTP port 25.  Does that not show up in the Postfix logs?

---

### Post by gte861s on 2016-08-06
That's probably from localhost queries alone. I just did a localhost connect then quit and it went from 87 to 93.

---

### Post by gte861s on 2016-08-07
Well I think I found the issues and it was within the Security Groups. I created a custom security group for all my security ports and it apparently didn't like that. I made some changes slowly and found the security group which would work...port 25 still doesn't work but at least I have made progress on other ports being opened up!

---

