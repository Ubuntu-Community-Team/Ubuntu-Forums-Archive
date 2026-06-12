---
title: "AWSats is destroying my happiness in Ubuntu server."
date: 2008-06-19
forum: Server Platforms
---

### Post by cackles on 2008-06-19
I cant seem to get the geoip plugin for awstats to run under the Hardy server edition. I have installed the perl module for it and took away the # in the conf file for my server that stopped it running. I read other peoples woes with a similar problem and there didnt seem to be many replies to them :(

I get this error message:

```
Can't call method "country_code_by_addr" on an undefined value at /usr/share/awstats/plugins/geoip.pm line 96, <LOG> line 34.
```

Any help appreciated.

In true Columbo fashion I decided to say to myself 'Just one more thing, (before I go to bed)'. That was last night and now its 2PM and Ive been awake 29hrs and the answers probably staring me in the face, but thats ok cus Ill get sleep after 40 :lolflag:

Anyway ...

---

### Post by Bodlin on 2010-08-11
I know, this is an old question, but still appears on first place in Google.
So quick solution on my side (just reminder for me :-)

1) # apt-get install  libgeo-ip-perl
2) uncoment geoIP module in your config file(s): LoadPlugin="geoipfree"

For GeoCity functionality:

3) #mkdir /usr/local/share/GeoIP/
4) #cd /usr/local/share/GeoIP/
4) read licence for GeoLiteCity at [http://www.maxmind.com/app/geolitecity](http://www.maxmind.com/app/geolitecity)   ( this is required!! )
5) # wget [http://geolite.maxmind.com/download/geoip/database/GeoLiteCity.dat.gz](http://geolite.maxmind.com/download/geoip/database/GeoLiteCity.dat.gz)
6) #gunzip GeoLiteCity.dat.gz

---

### Post by cackles on 2010-08-13
Thanks, I had forgotten all about this until you post, really appreciated, thank you.

---

