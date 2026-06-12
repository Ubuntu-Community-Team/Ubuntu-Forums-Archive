---
title: "hybridfox &amp; UEC"
date: 2010-01-13
forum: Server Platforms
---

### Post by christoph_b on 2010-01-13
Hi,

I'm trying to get UEC running, looks good so far. I tried to get Eucalyptus running with elasticfox 1.7 which does not work for some elasticfox internal reasons. So I tried hybridfox instead but with no real success. I registered the correct credentials in hybridfox and entered my local region. This leads to the following error:

Please check your EC2 URL 'http://<ip_of_my_cloud_cluster>:8773/services/Eucalyptus/' for correctness, or delete the value in ec2ui.endpoints using about:config and retry.

This maybe a hybridfox problem, but when I try to get the URL 'by foot' (
http://<ip_of_my_cloud_cluster>:8773/services/Eucalyptus) in my browser I get a 500 http error. Does this mean there is a problem witrh my UEC/Euca configuration or is it simply a certficate problem. 

Is there anyone out there running the 9.10 UEC release with hybridfox 1.000006 (latest version) successfully ???

Any hints are much appreciated, everything looks really cool apart from this little problem ;)

cheers
christoph

---

### Post by shahin on 2011-02-17
you may be running into the same issue I did. I could not connect due to time mismatch between my server and client.  Firefox has an addon called Firebug. It gives you visibility into your browser request and replies that come from the server.  It may help.  But first just check the time on your server and client.  If they are not the same, fix it possibly by configuring an NTP server for your server. If that does not work install firebug and activate the "net" option.  That may tell you why you are having this problem.  Good luck.

---

