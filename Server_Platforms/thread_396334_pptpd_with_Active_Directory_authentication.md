---
title: "pptpd with Active Directory authentication"
date: 2007-03-29
forum: Server Platforms
---

### Post by Tuptut on 2007-03-29
Hi, I am trying to configure my VPN server pptpd (poptop) using AD authentication (win2003). My vpn is working fine authenticating against chap-security, with mschap-v2 and mppe-128 implemented. Looking at dump or debug don't help as I have no clue how to approach the configuration in pptpd-options !?
I know i need to use radius plugin for that but my implementation don't work. I've setup IAS (Internet Authentication Server) on windows which to my understanding is windows based radius. I am not sure about how to setup radius client, should I be using fully blown freeradius server on my VPN and configure that to connect to IAS, or  is there a quick way of configuring some sort of radius plugin on VPN that authenticates to IAS radius ? Does anyone know about tutorial on this, or any examples. Please advise. Any help would be greatly appreciated !

---

### Post by carlsnyman on 2007-04-03
I had the exact same problem and after much frustration solved it today. I got a lot of help from this link [http://www.debian-administration.org/articles/245](http://www.debian-administration.org/articles/245) but in summary I did the following because that link didn't solve everything. 

The main problem is that for MS-CHAP protocols to work with the radius server it is critical that the radiusclient setup has the microsoft dictionaries. 

Unfortunately these aren't installed with the radiusclient1 package (Which is required to use radius and IAS with poptop) (apt-get install radiusclient1) I then tried to apt-get install freeradius to get the dictionary.microsoft file (even though I wasn't going to install a radius server) which at least gave me a microsoft.dictionary in /usr/share/freeradius/dictionary.microsoft but that file also didn't work. After I tried following the instructions in the link above to modify my dictionary.microsoft which also didn't work I got a mate of mine to mail me his working dictionary.microsoft file which actually came from a Gentoo installation. 

Here is my current working dictionary.microsoft file (from my mates Gentoo install) 

root@sentinel:/etc/radiusclient# cat dictionary.microsoft
#
#       Microsoft's VSA's, from RFC 2548
#
#       $Id: dictionary.microsoft,v 1.1 2004/11/14 07:26:26 paulus Exp $
#

VENDOR          Microsoft       311     Microsoft

ATTRIBUTE       MS-CHAP-Response        1       string  Microsoft
ATTRIBUTE       MS-CHAP-Error           2       string  Microsoft
ATTRIBUTE       MS-CHAP-CPW-1           3       string  Microsoft
ATTRIBUTE       MS-CHAP-CPW-2           4       string  Microsoft
ATTRIBUTE       MS-CHAP-LM-Enc-PW       5       string  Microsoft
ATTRIBUTE       MS-CHAP-NT-Enc-PW       6       string  Microsoft
ATTRIBUTE       MS-MPPE-Encryption-Policy 7     string  Microsoft
# This is referred to as both singular and plural in the RFC.
# Plural seems to make more sense.
ATTRIBUTE       MS-MPPE-Encryption-Type 8       string  Microsoft
ATTRIBUTE       MS-MPPE-Encryption-Types  8     string  Microsoft
ATTRIBUTE       MS-RAS-Vendor           9       integer Microsoft
ATTRIBUTE       MS-CHAP-Domain          10      string  Microsoft
ATTRIBUTE       MS-CHAP-Challenge       11      string  Microsoft
ATTRIBUTE       MS-CHAP-MPPE-Keys       12      string  Microsoft
ATTRIBUTE       MS-BAP-Usage            13      integer Microsoft
ATTRIBUTE       MS-Link-Utilization-Threshold 14 integer        Microsoft
ATTRIBUTE       MS-Link-Drop-Time-Limit 15      integer Microsoft
ATTRIBUTE       MS-MPPE-Send-Key        16      string  Microsoft
ATTRIBUTE       MS-MPPE-Recv-Key        17      string  Microsoft
ATTRIBUTE       MS-RAS-Version          18      string  Microsoft
ATTRIBUTE       MS-Old-ARAP-Password    19      string  Microsoft
ATTRIBUTE       MS-New-ARAP-Password    20      string  Microsoft
ATTRIBUTE       MS-ARAP-PW-Change-Reason 21     integer Microsoft

ATTRIBUTE       MS-Filter               22      string  Microsoft
ATTRIBUTE       MS-Acct-Auth-Type       23      integer Microsoft
ATTRIBUTE       MS-Acct-EAP-Type        24      integer Microsoft

ATTRIBUTE       MS-CHAP2-Response       25      string  Microsoft
ATTRIBUTE       MS-CHAP2-Success        26      string  Microsoft
ATTRIBUTE       MS-CHAP2-CPW            27      string  Microsoft

ATTRIBUTE       MS-Primary-DNS-Server   28      ipaddr  Microsoft
ATTRIBUTE       MS-Secondary-DNS-Server 29      ipaddr  Microsoft
ATTRIBUTE       MS-Primary-NBNS-Server  30      ipaddr  Microsoft
ATTRIBUTE       MS-Secondary-NBNS-Server 31     ipaddr  Microsoft

#ATTRIBUTE      MS-ARAP-Challenge       33      string  Microsoft


#
#       Integer Translations
#

#       MS-BAP-Usage Values

VALUE           MS-BAP-Usage            Not-Allowed     0
VALUE           MS-BAP-Usage            Allowed         1
VALUE           MS-BAP-Usage            Required        2

#       MS-ARAP-Password-Change-Reason Values

VALUE   MS-ARAP-PW-Change-Reason        Just-Change-Password            1
VALUE   MS-ARAP-PW-Change-Reason        Expired-Password                2
VALUE   MS-ARAP-PW-Change-Reason        Admin-Requires-Password-Change  3
VALUE   MS-ARAP-PW-Change-Reason        Password-Too-Short              4

#       MS-Acct-Auth-Type Values

VALUE           MS-Acct-Auth-Type       PAP             1
VALUE           MS-Acct-Auth-Type       CHAP            2
VALUE           MS-Acct-Auth-Type       MS-CHAP-1       3
VALUE           MS-Acct-Auth-Type       MS-CHAP-2       4
VALUE           MS-Acct-Auth-Type       EAP             5

#       MS-Acct-EAP-Type Values

VALUE           MS-Acct-EAP-Type        MD5             4
VALUE           MS-Acct-EAP-Type        OTP             5
VALUE           MS-Acct-EAP-Type        Generic-Token-Card      6
VALUE           MS-Acct-EAP-Type        TLS             13


root@sentinel:/etc/radiusclient#

Then you need to edit /etc/radiusclient/dictionary and add
INCLUDE /etc/radiusclient/dictionary.microsoft

Also check the your IAS logs in event on your domain controller for any policies blocking your connections. As far as I know you need to have at least one "Remote Access Policy" and at least one "Connection Request Policy" I just created mine with "Day-Night-Restrictions-Match" and selected all applicable times for both policies. Once all working then lock it down properly with decent per user/group polices. 

I also had an issue with my domain controller wanting 128-bit encryption and enabled 

/etc/ppp/pptpd-options

require-mppe-128

You do need to tweak a few other settings in your /etc/ppp/pptpd-options

ms-dns 192.168.0.10 #Your Domain Controller 
auth
plugin radius.so
plugin radattr.so

That should be about it, 
Hope this helps!
Carl

---

