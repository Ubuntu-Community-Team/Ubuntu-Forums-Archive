---
title: "Unable to get Netflow stats in ntop"
date: 2017-09-14
forum: Server Platforms
---

### Post by lambchopper71 on 2017-09-14
I hope this is the correct forum, I'm new to this forum.

I've recently installed ntop in to my 16.04 server from the Ubuntu repos.

I've activated and configured netflow and my firewall to send netflow towards my server.  I know that netflow data is getting to my server because I can see the stats increasing:

[TABLE]
[TR="bgcolor: #FFFFFF"]
[TH="bgcolor: #F3F3F3, colspan: 2, align: left"]Flow Senders[/TH]
 [TD="width: 20%, colspan: 3"][TABLE="width: 100%"]
[TR]
[TH="bgcolor: #F3F3F3"]Sender[/TH]
[TH="bgcolor: #F3F3F3"]Pkts[/TH]
[TH="bgcolor: #F3F3F3"]Flows[/TH]
[TH="bgcolor: #F3F3F3"]Lost Flows[/TH]
[/TR]
[TR]
[TD="align: right"]192.168.1.1:10867[/TD]
[TD="align: right"]606[/TD]
[TD="align: right"]606[/TD]
[TD="align: right"]0[/TD]
[/TR]
 [/TABLE]
[/TD]
 [/TR]
 [TR="bgcolor: #FFFFFF"]
 [TH="bgcolor: #F3F3F3, colspan: 2, align: left"]Packets Received[/TH]
 [TD="colspan: 3, align: right"]606[/TD]
 [/TR]
 [TR="bgcolor: #FFFFFF"]
 [TH="bgcolor: #F3F3F3, colspan: 2, align: left"]Packets with Bad Version[/TH]
 [TD="colspan: 3, align: right"]0[/TD]
 [/TR]
 [TR="bgcolor: #FFFFFF"]
 [TH="bgcolor: #F3F3F3, colspan: 2, align: left"]Packets Processed[/TH]
 [TD="colspan: 3, align: right"]606[/TD]
 [/TR]
 [TR="bgcolor: #FFFFFF"]
 [TH="bgcolor: #F3F3F3, colspan: 2, align: left"]Valid Flows Received[/TH]
 [TD="colspan: 3, align: right"]7,747[/TD]
 [/TR]
 [TR="bgcolor: #FFFFFF"]
 [TH="bgcolor: #F3F3F3, colspan: 2, align: left"]Average Number of Flows per Packet[/TH]
 [TD="colspan: 3, align: right"]25.6[/TD]
 [/TR]
 [TR="bgcolor: #FFFFFF"]
 [TH="bgcolor: #F3F3F3, colspan: 2, align: left"]V1 Flows Received[/TH]
 [TD="colspan: 3, align: right"]0[/TD]
 [/TR]
 [TR="bgcolor: #FFFFFF"]
 [TH="bgcolor: #F3F3F3, colspan: 2, align: left"]V5 Flows Received[/TH]
 [TD="colspan: 3, align: right"]0[/TD]
 [/TR]
 [TR="bgcolor: #FFFFFF"]
 [TH="bgcolor: #F3F3F3, colspan: 2, align: left"]V7 Flows Received[/TH]
 [TD="colspan: 3, align: right"]0[/TD]
 [/TR]
 [TR="bgcolor: #FFFFFF"]
 [TH="bgcolor: #F3F3F3, colspan: 2, align: left"]V9 Data Flows Received[/TH]
 [TD="colspan: 3, align: right"]7,747[/TD]
 [/TR]
 [TR="bgcolor: #FFFFFF"]
 [TH="bgcolor: #F3F3F3, colspan: 2, align: left"]V9 Option Flows Received[/TH]
 [TD="colspan: 3, align: right"]0[/TD]
 [/TR]
 [TR="bgcolor: #FFFFFF"]
 [TH="bgcolor: #F3F3F3, colspan: 2, align: left"]Total V9 Templates Received[/TH]
 [TD="colspan: 3, align: right"]2[/TD]
 [/TR]
 [TR]
[TD="colspan: 5"] [/TD]
[/TR]
 [TR="bgcolor: #FFFFFF"]
 [TH="bgcolor: #F3F3F3, colspan: 5"]Discarded Flows[/TH]
 [/TR]
 [TR="bgcolor: #FFFFFF"]
 [TH="bgcolor: #F3F3F3, colspan: 2, align: left"]Flows with Zero Packet Count[/TH]
 [TD="colspan: 3, align: right"]7,747[/TD]
 [/TR]
 [TR="bgcolor: #FFFFFF"]
 [TH="bgcolor: #F3F3F3, colspan: 2, align: left"]Flows with Zero Byte Count[/TH]
 [TD="colspan: 3, align: right"]0[/TD]
 [/TR]
 [TR="bgcolor: #FFFFFF"]
 [TH="bgcolor: #F3F3F3, colspan: 2, align: left"]Flows with Bad Data[/TH]
 [TD="colspan: 3, align: right"]0[/TD]
 [/TR]
 [TR="bgcolor: #FFFFFF"]
 [TH="bgcolor: #F3F3F3, colspan: 2, align: left"]Flows with Unknown Template[/TH]
 [TD="colspan: 3, align: right"]0[/TD]
 [/TR]
 [TR="bgcolor: #FFFFFF"]
 [TH="bgcolor: #F3F3F3, colspan: 2, align: left"]Total Number of Flows Processed
[/TH]
 [TD="colspan: 3, align: right"]0
[/TD]
[/TR]
[/TABLE]

I see that it's discarding flows with zero packet counts.

My probe is a Cisco ASA5505 that only supports Netflow v9.  I have the config as follows:
access-list NETFLOW extended permit ip any any
flow-export destination inside 192.168.1.252 2055

class-map NETFLOW
 match access-list NETFLOW

policy-map GLOBAL
 class NETFLOW
  flow-export event-type all destination 192.168.1.252

service-policy GLOBAL global


I'm not sure why it's not aggregating and flow data, does anyone have any experience with this that might point me in the right direction?

---

### Post by jeremy31 on 2017-09-14
*Thread moved to **Server Platforms**.*

---

