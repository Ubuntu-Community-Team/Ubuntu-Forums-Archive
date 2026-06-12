---
title: "Awstats &amp; GeoIP"
date: 2010-04-09
forum: Server Platforms
---

### Post by Wingthor on 2010-04-09
Hey,

A question. 

I am using *awstats *to get statistics about webtrafic to my server. Everything works fine but the ***GeoIp ***only ***shows unknown*** in the country and city columns. I have tried several settings in the DNS lookup setting in the configfile without any effect.

Is there others that suffer from this? Or is it I that have configured it wrong?

Regards

Wingthor

---

### Post by Wingthor on 2010-04-15
I have solved this myself. 

The problem was the log file from Apache2. I used the default ubuntu logformat with virtual hosts. The reports from awstats was in matter of fact completly wrong all over. Not just GeoIP. However it looked right except for the GeoIp records.

> LogFormat "%v:%p %h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combinedSo what I did to solve the problem was to use the apache2 tool called split-logfile. This tool divides the instances in the apache access.log file in to seperate files according to virutalhosts you have. One log file for each virtual host. Then when awstats update read those files, everything came up right. Remember to change the awstats config file accordingly. The split-logfile also requires the logs parameters above to work proper.

Good luck :KS!

Regards

---

