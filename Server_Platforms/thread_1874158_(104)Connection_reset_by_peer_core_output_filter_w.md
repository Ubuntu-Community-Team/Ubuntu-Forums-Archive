---
title: "(104)Connection reset by peer: core_output_filter: writing data to the network"
date: 2011-11-02
forum: Server Platforms
---

### Post by Malac on 2011-11-02
Hi,
I'm running an apache server and suddenly the site started rendering no images and no css files.
So far it only seems to be on the local network that this is happening. At home or on other outside computers seems to be okay.

To the best of my knowledge no alterations were made to the system between it running okay and not.
I've set up another simpler html site with minimal css, one page and 8 small gif files and the same thing happens.

I have seen similar threads on other sites which recommend adding: "EnableSendfile off" and "EnableMMAP off" to the apache2.conf file but this has made know difference.
I've also tried with all caching disabled.

I am truly flummoxed as to what the cause could be.
I'm coming to the conclusion that it is some sort of weird router problem that is only affecting calls out from the local net to the internet and back to the server on the local net.
I will be trying another router asap but wondered if anyone has come across this before.

Server version of original server: Apache/2.2.17 (Ubuntu)
Server version of temp server for testing: Apache/2.2.20 (Ubuntu)

Log file at time of calls to webpage:```
[Wed Nov 02 17:22:00 2011] [debug] mod_deflate.c(615): [client XXX.XXX.XXX.XXX] Zlib: Compressed 20708 to 4435 : URL /shop/components/com_virtuemart/themes/vm_mynxx/theme.css, referer: http://www.mirrorsandglass.co.uk/shop/index.php
[Wed Nov 02 17:22:00 2011] [info] [client XXX.XXX.XXX.XXX] (104)Connection reset by peer: core_output_filter: writing data to the network
[Wed Nov 02 17:22:00 2011] [info] [client XXX.XXX.XXX.XXX] (104)Connection reset by peer: core_output_filter: writing data to the network
[Wed Nov 02 17:22:00 2011] [debug] mod_deflate.c(615): [client XXX.XXX.XXX.XXX] Zlib: Compressed 48668 to 8991 : URL /shop/templates/rt_mynxx_j15/css/template.css, referer: http://www.mirrorsandglass.co.uk/shop/index.php
[Wed Nov 02 17:22:00 2011] [debug] mod_deflate.c(615): [client XXX.XXX.XXX.XXX] Zlib: Compressed 9247 to 1686 : URL /shop/templates/rt_mynxx_j15/css/typography.css, referer: http://www.mirrorsandglass.co.uk/shop/index.php
[Wed Nov 02 17:22:00 2011] [info] [client XXX.XXX.XXX.XXX] (104)Connection reset by peer: core_output_filter: writing data to the network
[Wed Nov 02 17:22:00 2011] [debug] mod_deflate.c(615): [client XXX.XXX.XXX.XXX] Zlib: Compressed 20708 to 4435 : URL /shop/components/com_virtuemart/themes/vm_mynxx/theme.css, referer: http://www.mirrorsandglass.co.uk/shop/index.php
[Wed Nov 02 17:22:00 2011] [debug] mod_deflate.c(615): [client XXX.XXX.XXX.XXX] Zlib: Compressed 20708 to 4435 : URL /shop/components/com_virtuemart/themes/vm_mynxx/theme.css, referer: http://www.mirrorsandglass.co.uk/shop/index.php
[Wed Nov 02 17:22:01 2011] [info] [client XXX.XXX.XXX.XXX] (104)Connection reset by peer: core_output_filter: writing data to the network
[Wed Nov 02 17:22:01 2011] [info] [client XXX.XXX.XXX.XXX] (104)Connection reset by peer: core_output_filter: writing data to the network
[Wed Nov 02 17:22:02 2011] [info] [client XXX.XXX.XXX.XXX] (104)Connection reset by peer: core_output_filter: writing data to the network
```

---

### Post by Malac on 2011-11-07
I have found a response on the excellent site, [http://bt2700hgv.tripod.com](http://bt2700hgv.tripod.com).
It seems a automatic firmware upgrade breaks local net access to web servers on that network.
I hope they don't mind my quoting it here.:> 
_**Missing content from web pages delivered from internal web server when using an external URL/address**_
 (3 Nov 11)
 [COLOR=#000080][FONT=Arial, sans-serif]**Kinmel**[/FONT][/COLOR] reports:
 [FONT=Arial, sans-serif][SIZE=2]One of my 2700HGV v6s updated yesterday and for some reason is causing problems for my webserver across the LAN. [/SIZE][/FONT] 
 [FONT=Arial, sans-serif][SIZE=2]If I access the pages from outside my LAN, or through a proxy from my LAN, then everything works perfectly. However, with the updated V6, pages delivered locally from the webserver are lacking all CSS rendered elements.[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]I can do a work around by adding the domains into the hosts file pointing directly to the server IP, which suggests it DNS related.[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]A brand new 2700HGV with v6.1.1.48.1 renders the pages correctly.[/SIZE][/FONT]
 
[COLOR=#000080][FONT=Arial, sans-serif]**J1mbo**[/FONT][/COLOR] provides a likely technical explanation:
 [FONT=Arial, sans-serif][SIZE=2]My router updated recently, and I noticed that accessing externally accessible web servers from an internal host (but using the external address - hope this makes sense!) is broken with this firmware.[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Anyway, here is the issue:[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]- Internel web server **192.168.1.1**[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]- Internal client 192.168.1.10[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]- BT router 192.168.1.254[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]- External static IP say **200.200.200.200**[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]- Port forwarding for port 80 configured to 192.168.1.1[/SIZE][/FONT]
 
[FONT=Arial, sans-serif][SIZE=2]So, externally the web server is accessible as [http://200.200.200.200](http://200.200.200.200).[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Internally, under v6.1.48 it would also be accessible using the same address (sometimes called 'loop back').[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]However with the new firmware, while external access works OK, access from within the network to [http://200.200.200.200](http://200.200.200.200) results in much missing content and hence incorrectly displayed web pages in certain cases.[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Packet traces on the client itself show the router serving dupe ACKs on each GET then after some point reset all connections (literally, TCP reset). Obviously that stops the browser dead. More odd is that it seems to serve content from IIS OK, but not from apache.[/SIZE][/FONT]
 The discussion is continued on the Idnetters forum in this [**thread**]("http://www.idnetters.co.uk/forums/index.php/topic,27491.0.html?PHPSESSID=0257f7b2e8fa640839a3f9ad5b244e07")
 The issue can be resolved by adding entries to local HOSTS file on each computer, or if your computers make use of the hub's internal DNS server, try adding entries to the [COLOR=#000080][FONT=Arial, sans-serif]Settings > Broadband > DNS Resolution[/FONT][/COLOR] page.
This last solution didn't work for me but changing the hosts files on internal machines did.

---

