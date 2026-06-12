---
title: "Issues with Squid"
date: 2011-09-11
forum: Server Platforms
---

### Post by talk2montu on 2011-09-11
Hello All,

I am trying to setup a proxy server for my motel.  I am currently having the following issue below and would like to understand why is it failing and how to fix it.  Also my second question is there a "pre-setup" config file that you guys would recommend having for a business.  Currently, I am using open DNS for block all bad requests (porno).  I  would like to know how to configure the proxy server (if needed) to help increase web requests.  Last but not least, does squid support any type of ip masking?  I am using ubuntu server 11.04 with gadmin-squid 0.1..3.  Just another thought, would it be wise to have a proxy server (squid) running on the main server (or virtual) or on another physical computer?  

2011/09/11 19:19:34| decode_addr: Invalid IP address '100'
2011/09/11 19:19:34| squid.conf line 155: acl our_networks src 192.168.5.0/100 
2011/09/11 19:19:34| aclParseIpData: Ignoring invalid IP acl entry: unknown netmask '100'
2011/09/11 19:19:34| aclParseAclLine: WARNING: empty ACL: acl our_networks src 192.168.5.0/100 
2011/09/11 19:19:34| ACL name 'all' not defined!
FATAL: Bungled squid.conf line 176: http_reply_access allow all
Squid Cache (Version 2.7.STABLE9): Terminated abnormally.

---

### Post by SeijiSensei on 2011-09-12
[http://en.wikipedia.org/wiki/CIDR_notation](http://en.wikipedia.org/wiki/CIDR_notation)

---

### Post by talk2montu on 2011-09-12
So I fixed the issue by removing everything and starting again.  However this time around I am not able to keep the squid service running for more than a second.  See results below

montu@VIRUS:~$ sudo service squid start
squid start/running, process 5067
montu@VIRUS:~$ sudo service squid status
squid stop/waiting

I have read several places that I may need to log rotate as well, but doesn't seem to help, see results as well
montu@VIRUS:~$ sudo logrotate -f -s /var/lib/logrotate.status /etc/logrotate.d/squid


When I am editing the file I keep getting the following message in command prompt when I save the file.
montu@VIRUS:/etc/squid$ sudo gedit squid.conf &
[1] 5081
montu@VIRUS:/etc/squid$ 
(gedit:5082): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.YX3M1V': No such file or directory

(gedit:5082): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

---

### Post by talk2montu on 2011-09-19
Can somebody help me about this issue?

---

### Post by SeijiSensei on 2011-09-19
Can you edit the file with a text editor like nano from the terminal prompt?

Does root have a /root/.local/share directory with the correct ownerships and permissions?

The error message is pretty clear-cut.  There's a problem writing a file into /root/.local/share.  It's nearly always either a missing directory, or problems with permissions.

---

### Post by talk2montu on 2011-09-25
Thanks for the information!  I guess my latest problem is how to I set a small number of IP's to the squid server.  For example, on my DHCP server I have the following IP address being done 

192.168.5.50- 192.168.5.100

How do I write that in the squid file?  I have tried to put in the following and it doesn't seem to like it and I dont know why

192.168.5.50/100

Also I am trying to make it transparent server as well, so that people are pointed to the proxy server directly.  Currently, I only have one NIC (ETH0).  The following command was being used but proxy doesn't seem to like "iptables"

[COLOR=#800000]iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128
[/COLOR]

I am also trying to mascuerade this process as well.  Any line of code would help or references.

thanks

---

### Post by Gone fishing on 2011-09-25
I found this howto on transparent proxying with squid [http://www.debian-administration.org/articles/71](http://www.debian-administration.org/articles/71) which looks good. I personally use Webmin to help me set up squid, which, I find makes it comparatively easy [http://www.webmin.com/standard.html](http://www.webmin.com/standard.html). I also use squid guard (the Webmin module isn't great here in my opinion and I don't use it) with these blacklists [http://urlblacklist.com/?sec=download](http://urlblacklist.com/?sec=download)

---

