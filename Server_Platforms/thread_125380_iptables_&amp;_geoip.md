---
title: "iptables &amp; geoip"
date: 2006-02-03
forum: Server Platforms
---

### Post by Greyice on 2006-02-03
Ladies & Gents,

I've hit a brick wall and would like some help please...

**Overview:**
I would like to set iptables to allow the geoip mode/method.
EG. iptables -A INPUT -m geoip --src-cc XX -j DROP

**Error Message:**
iptables v1.3.1: Couldn't load match `geoip':/lib/iptables/libipt_geoip.so: cannot open shared object file: No such file or directory

**Working(s):**
I've created the script "get_GeoIP_Dat.sh" to fetch and place the BIN and IDX files. 
---
#!/bin/sh
wget [http://www.maxmind.com/download/geoip/database/GeoIP.dat.gz](http://www.maxmind.com/download/geoip/database/GeoIP.dat.gz)
wget [http://www.maxmind.com/download/geoip/database/GeoIPCountryCSV.zip](http://www.maxmind.com/download/geoip/database/GeoIPCountryCSV.zip)
unzip GeoIPCountryCSV.zip
csv2bin GeoIPCountryWhois.csv
sudo mv geoipdb.bin /var/geoip/geoipdb.bin
sudo mv geoipdb.idx /var/geoip/geoipdb.idx
---

I'm having a hard time trying to find out where to get libipt_geoip.so or how to compile my kernel to allow the geoip method to be enabled. All the docco os for Debian and although I'm familiar with it, I cannot find the approriate Ubuntu files or information.

Has anyone here run iptables with geoip enabled? I'd appreciate any help on this as I've run out of thoghts on it and I want to get this running.

Sincerely, 

G.

---

