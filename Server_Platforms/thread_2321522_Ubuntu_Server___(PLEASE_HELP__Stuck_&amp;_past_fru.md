---
title: "Ubuntu Server   (PLEASE HELP *** Stuck &amp; past frustrated)"
date: 2016-04-22
forum: Server Platforms
---

### Post by mikedennison on 2016-04-22
Hi All I am old but new to Ubuntu.
The Last time I was here was back in 2009 and met some people that where great help.. I am hoping I can find someone that can help me with the problem I am having today

I am using this thread [http://ubuntuforums.org/showthread.php?t=926001](http://ubuntuforums.org/showthread.php?t=926001) to help me thru the build this is exactly what I want.

the computer I am using for my gateway is

Acer Aspire AMD 3800
1 GIG DDR RAM
320 GIG Sata HDD m(I know over kill but it is all I have for this build)
DVD BURNER

I turned off the onboard NIC card and installed 2x TP LINK Gigabit NIC
I have the enp1s5 talking to the outside world (working)
I have enp1s6 active which i want to talk to my internal network..
I also got WEBMIN 1.791 online and working

First Question... WEBMIN seems to be a little outdated for Ubuntu... is there something better to use.. I chose this really because I knew it from my servers in 2009


Now for my real problem I have been searching the forums and trying what people have said in the forums and none has helped...
WEBMIN is not showing my DHCP server... I know WEBMIN is looking for dhcp3-server and Ubuntu is using isc-dchp-server..  can someone help me get this working or suggest something different to use other then web min that will work...

---

### Post by wildmanne39 on 2016-04-22
*Thread moved to **Server Platforms**.*

---

### Post by Seb_Boffen on 2016-04-23
Hi this is my **System configuration** For module DHCP Server

[TABLE="width: 100%"]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, width: 30%"]**DHCP server config file**
[/TD]
[TD="class: ui_form_value"]/etc/dhcp/dhcpd.conf[/TD]
[/TR]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, width: 30%"]** DHCP server executable**
[/TD]
[TD="class: ui_form_value"]/usr/sbin/dhcpd[/TD]
[/TR]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, width: 30%"]** Command to start DHCP server**
[/TD]
[TD="class: ui_form_value"] /etc/init.d/isc-dhcp-server start
[/TD]
[/TR]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, width: 30%"]** Command to apply configuration**
[/TD]
[TD="class: ui_form_value"] /etc/init.d/isc-dhcp-server restart
[/TD]
[/TR]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, width: 30%"]** Command to stop DHCP server**
[/TD]
[TD="class: ui_form_value"] /etc/init.d/isc-dhcp-server stop
[/TD]
[/TR]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, width: 30%"]** Path to DHCP server PID file**
[/TD]
[TD="class: ui_form_value"] /var/run/dhcpd.pid
[/TD]
[/TR]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, width: 30%"]** DHCP server lease file**
[/TD]
[TD="class: ui_form_value"]/var/lib/dhcp/dhcpd.leases[/TD]
[/TR]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, width: 30%"]** Interfaces file type**
[/TD]
[TD="class: ui_form_value"]Debian
[/TD]
[/TR]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, width: 30%"]** DHCP server version**
[/TD]
[TD="class: ui_form_value"] Work out automatically
[/TD]
[/TR]
[/TABLE]

---

### Post by darkod on 2016-04-23
How dependent are you on GUI like webmin or similar?

If this machine is going to be a "simple" gateway, it is very easy to be configured by using only ssh session, even for a command line beginner. As you've used ubuntu before, you might not even be such a beginner.

Also, one alternative for dhcp server is dnsmasq. It is a package that does both dns and dhcp (the dns option can be disabled if you want to), and it is very easy to configure. Not that isc-dhcp-server is difficult too.

Apart from the dhcp, you will also need to do configuration for the gateway (routing) function. Is that part working already, and you need to configure only the dhcp, or you need to configure everything?

---

