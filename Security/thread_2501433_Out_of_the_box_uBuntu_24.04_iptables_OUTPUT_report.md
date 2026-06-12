---
title: "Out of the box uBuntu 24.04 iptables OUTPUT reports security issues"
date: 2024-10-07
forum: Security
---

### Post by page-cal on 2024-10-07
I've just installed an out of the box Ubuntu 24.04 LTS box. I've set the iptables OUTPUT chain to log (and drop) suspicious activity. I've noticed some.
I look up the ip's on AbuseIPDB, and get the following report:

Ip Address: 103.203.57.21
{
    "data": {
        "abuseConfidenceScore": 100,
        "countryCode": "CN",
        "domain": "ipip.net",
        "hostnames": [
            "scan-57-21.security.ipip.net"
        ],
        "ipAddress": "103.203.57.21",
        "ipVersion": 4,
        "isPublic": true,
        "isTor": false,
        "isWhitelisted": false,
        "isp": "Beijing Tiantexin Tech. Co. Ltd.",
        "lastReportedAt": "2024-10-07T10:04:10+00:00",
        "numDistinctUsers": 60,
        "totalReports": 3564,
        "usageType": "Data Center/Web Hosting/Transit"
    }
}

There are lots more from LT, CN, GP, and DE. They seem to be hitting ports 22, 80, and 443.

There is no corresponding traffic on INPUT, so obviously, these OUTPUT requests are internally generated.

Obviously, these are security issues. How do I resolve them? Has someone else seen this?

---

### Post by page-cal on 2024-10-07
I installed auditd to try and find who is doing this. Here are my rules
-a always,exit -F arch=b64 -S connect -F key=network-connect
-a always,exit -F arch=b64 -S sendto -F key=sendto-monitoring
-a always,exit -F arch=b64 -S sendmsg -F key=sendmsg-monitoring
-a always,exit -F arch=b64 -S socket -F a0=0x2 -F a1=0x3 -F key=raw-socket-monitoring
-a always,exit -F arch=b64 -S sendto,sendmsg -F a0=0x2 -F key=udp-out-ipv4
-a always,exit -F arch=b64 -S sendto,sendmsg -F a0=0xA -F key=udp-out-ipv6

The iptables
Chain ufw-blocklist-output (1 references)
 pkts bytes target     prot opt in     out     source               destination
  249 12256 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 10 LOG flags 0 level 4 prefix "zDROP ufw-blocklist-output: "
  269 13392 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0
catch the packet and kill it, but nothing shows up in auditd logs in journalctl -f

It may be that the hack is in the kernel, as I'm monitoring user space calls. Or, they are using some RAW output I'm not catching. Any ideas?

---

### Post by 0f4d0335 on 2024-10-07
It appears the host in your first post is a geolocator, which may be a library used in either the base Ubuntu build or an application you installed (perhaps extension or even website you visited) that checks where your geo location is. This outbound traffic would be indicative of expected desktop behavior. You can of course block the IP and hostname in your hosts file.

Why would you think this is a hack?

Example of what to write in your host file:

127.0.0.1 x.y.z //direct lookup to localhost address

(source) [URL="https://superuser.com/a/1193394"]https://superuser.com/a/1193394
[/URL]

---

### Post by page-cal on 2024-10-07
I think it's a a hack because I looked it up a number of reported addresses on AbuseIPDB.com, as I'm a subscriber.

Look specifically for the abuseConfidenceScore. It's the percentage of badness, 100 being totall bad, and 0 being ok. 

Here's the printout of a few addresses:

Ip Address: 103.203.57.21
{
    "data": {
        "abuseConfidenceScore": 100,
        "countryCode": "CN",
        "domain": "ipip.net",
        "hostnames": [
            "scan-57-21.security.ipip.net"
        ],
        "ipAddress": "103.203.57.21",
        "ipVersion": 4,
        "isPublic": true,
        "isTor": false,
        "isWhitelisted": false,
        "isp": "Beijing Tiantexin Tech. Co. Ltd.",
        "lastReportedAt": "2024-10-07T16:09:46+00:00",
        "numDistinctUsers": 60,
        "totalReports": 3567,
        "usageType": "Data Center/Web Hosting/Transit"
    }
}
Ip Address: 141.98.11.79
{
    "data": {
        "abuseConfidenceScore": 100,
        "countryCode": "LT",
        "domain": "serveroffer.lt",
        "hostnames": [
            "eletrire.halffail.com"
        ],
        "ipAddress": "141.98.11.79",
        "ipVersion": 4,
        "isPublic": true,
        "isTor": false,
        "isWhitelisted": false,
        "isp": "UAB Host Baltic",
        "lastReportedAt": "2024-10-07T16:03:54+00:00",
        "numDistinctUsers": 167,
        "totalReports": 2555,
        "usageType": "Data Center/Web Hosting/Transit"
    }
}
Ip Address: 78.153.140.78
{
    "data": {
        "abuseConfidenceScore": 0,
        "countryCode": "GB",
        "domain": "interlan.ru",
        "hostnames": [
            "hostglobal.plus"
        ],
        "ipAddress": "78.153.140.78",
        "ipVersion": 4,
        "isPublic": true,
        "isTor": false,
        "isWhitelisted": null,
        "isp": "LLC Company Interlan Communications",
        "lastReportedAt": null,
        "numDistinctUsers": 0,
        "totalReports": 0,
        "usageType": "Fixed Line ISP"
    }
}
Ip Address: 154.213.184.15
{
    "data": {
        "abuseConfidenceScore": 100,
        "countryCode": "DE",
        "domain": "pfcloud.io",
        "hostnames": [],
        "ipAddress": "154.213.184.15",
        "ipVersion": 4,
        "isPublic": true,
        "isTor": false,
        "isWhitelisted": false,
        "isp": "PFCloud UG",
        "lastReportedAt": "2024-10-07T16:16:05+00:00",
        "numDistinctUsers": 873,
        "totalReports": 15493,
        "usageType": "Data Center/Web Hosting/Transit"
    }
}
Ip Address: 93.123.85.155
{
    "data": {
        "abuseConfidenceScore": 42,
        "countryCode": "GB",
        "domain": "mortalsoft.online",
        "hostnames": [],
        "ipAddress": "93.123.85.155",
        "ipVersion": 4,
        "isPublic": true,
        "isTor": false,
        "isWhitelisted": false,
        "isp": "MortalSoft Ltd.",
        "lastReportedAt": "2024-10-07T11:14:12+00:00",
        "numDistinctUsers": 7,
        "totalReports": 13,
        "usageType": "Data Center/Web Hosting/Transit"
    }
}

---

### Post by 0f4d0335 on 2024-10-07
Oh, I'm confused then by your question. Because you specified this is going "out," but in reality, you're talking about IPs hitting your ports. This is very common on the Internet. You shouldn't have your box exposed directly to the Internet, otherwise you should expect to get hit with bots trying to figure out if you're vulnerable to common attacks. With a patched system you will be okay, but you should also harden your OS to prevent attacks.

---

### Post by page-cal on 2024-10-07
IP's don't hit the INPUT port, only OUTPUT - that's the point. I have the same iptables rules for INPUT, OUTPUT, and FORWARD. Nobody should ever be able to hit the OUTPUT port if they
were stopped by INPUT. Further, after installing tool auditd, and setting it up as above, I don't see anyone from user space hitting connect, sendto, sendmsg, or the raw interefaces.
The tool does report legitimate users from my box, but nothing happens around the time when the OUTPUT port is hit.

Another data point: Iget the same violations on 22.04-Ubuntu LTS, and on another box with a later revision 24.04 Ubuntu LTS. To keep the boxes up-to-date, I subscribe to [https://ubuntu.com/aws/pro](https://ubuntu.com/aws/pro).

It could be the aws builds I'm using, so I'd like to hear from the greater Ubuntu community on this. If you want to recreate the problem:

  1. curl down - curl -sS -f --compressed -o ../control/ipsum.3.ctl 'https://raw.githubusercontent.com/stamparm/ipsum/master/levels/3.txt'
  2. grep out your boxes IP
  3. load the above file into ipset
  3. setup ip firewall rules to block and report (and drop) based on the ipset you create.

I can publish a python3 program that does these steps if the community is interested. One point though, you can't be sitting on a home WiFi, but rather out there in the wild west internet.

---

### Post by 0f4d0335 on 2024-10-07
> IP's don't hit the INPUT port, only OUTPUT - that's the point.

That is incorrect. Public IPs when talking to your device will go the input port. They won't use the output port. Your device uses the output port.

[https://sudamtm.medium.com/iptables-a-comprehensive-guide-276b8604eff1](https://sudamtm.medium.com/iptables-a-comprehensive-guide-276b8604eff1)

> Further, after installing tool auditd, and setting it up as above, I  don't see anyone from user space hitting connect, sendto, sendmsg, or  the raw interefaces.

I think wireshark would be a better tool.

> I can publish a python3 program that does these steps if the community  is interested. One point though, you can't be sitting on a home WiFi,  but rather out there in the wild west internet.

It is very normal for random public IPs to connect to your device when it's on the public routeable Internet. They can do a port knock or other methods to check which port is open. The most common is 22 as you mentioned above.

As I said, I think this is pretty normal. You shouldn't rely on host firewall to protect your machine but a T3 router or a virtual router if on AWS like VPC firewall.

---

