---
title: "Apache 2 GeoIp Forwarding To Ip With Header On"
date: 2012-02-18
forum: Server Platforms
---

### Post by Cracken226 on 2012-02-18
Ok, i hope i will get few answers to this, as im stuck in nowhere with this, would like it to get working somehow, just dont know how. If its gonna work, im willing to pay something to developer as a bounty.

1. There is a main server in London, where incoming domain names are coming to it, based on dns server to ip forwarding, so server can listening to all domain names forwarded to this server from dns server by registrator. lets say 175.175.175.1

2. I would like to build ubuntu server with apache2 and libapache2-mod-geoip using country codes from [http://www.maxmind.com/app/iso3166](http://www.maxmind.com/app/iso3166) . All domain names pointing to this server going thru main server and using geoip module country code are forwarded to ip addresses to servers 175.175.175.2-5, where ips ... 2-5 are squid reverse proxies listening to main web servers on intranet.

3. Main server should be forwarding all original informations towards to these reverse proxies, so reverse proxy is listening to them and forwarding to accepted web server. It should be able to accepting all incoming domain names and forwarding them toward to proxies based on geoip location of requesting user.

4. I would like to see a sample, or better, tutorial howto build this, i have knowledge of apache and squid but geoip is something new for me. Main server should have not list of incoming domain names to accept, they just should be forwarded. Accepting and or rejecting will be on squid reverse proxy servers. There will be only list of countries based on geoip, what country will be forwarded to wich ip address keeping the header and all incoming informations on.

If somebody will be able to help me with this to get it done, bounty will be yours. Contact me thru post and or mail. Much appreciated. John.

---

