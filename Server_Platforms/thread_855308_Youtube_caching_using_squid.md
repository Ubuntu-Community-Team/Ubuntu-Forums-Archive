---
title: "Youtube caching using squid"
date: 2008-07-10
forum: Server Platforms
---

### Post by ikt on 2008-07-10
Hey guys,

is anyone able to convert the following into an ubuntu version/equivalent?

[http://fedora.co.in/content/youtube-cache-version-02-available-now](http://fedora.co.in/content/youtube-cache-version-02-available-now)

---

### Post by fujikofujio on 2008-11-11
I tried it and got it to install, here's how:

Download the source code from [http://cachevideos.com/download](http://cachevideos.com/download)

I used this one.
[http://cachevideos.com/sites/default/files/pub/youtube_cache/youtube_cache-1.2.tar.gz](http://cachevideos.com/sites/default/files/pub/youtube_cache/youtube_cache-1.2.tar.gz)

Make sure you got all the requirements.

   1. Squid >= 2.6
   2. Python >= 2.4
   3. Python-urlgrabber (urlgrabber module of python)
   4. Python-iniparse (iniparse module of python)
   5. Apache (httpd) Web Server

Not sure if it would have worked with lighttpd so I went ahead and used apache2, for the iniparse there is nothing on the repositories you can download it here: [http://code.google.com/p/iniparse/](http://code.google.com/p/iniparse/)

After downloading extract it, on the terminal type:

sudo python setup.py install

Extract the youtube_cache-1.2.tar.gz archive if you haven't done so already.

Open the setup.py file from youtube cache and make this changes to the following entries

squid_user = 'proxy'
squid_group = 'proxy'
apache_conf_dir = '/etc/apache2/conf.d/'

save it and type:

 sudo python setup.py install

edit your squid conf file

sudo gedit /etc/squid/squid.conf

Paste the following at the end of the file:

url_rewrite_program /usr/bin/python /etc/squid/youtube_cache/youtube_cache.py
url_rewrite_children 10
acl youtube_query url_regex -i \.youtube\.com\/get_video
acl youtube_query url_regex -i \.cache[a-z0-9]?[a-z0-9]?[a-z0-9]?\.googlevideo\.com\/videoplayback
acl youtube_query url_regex -i \.cache[a-z0-9]?[a-z0-9]?[a-z0-9]?\.googlevideo\.com\/get_video
acl youtube_deny url_regex -i http:\/\/[a-z][a-z]\.youtube\.com
acl metacafe_query dstdomain v.mccont.com
acl dailymotion_query url_regex -i proxy\-[0-9][0-9]\.dailymotion\.com\/
acl google_query dstdomain vp.video.google.com
acl redtube_query dstdomain dl.redtube.com
acl xtube_query url_regex -i [a-z0-9][0-9a-z][0-9a-z]?[0-9a-z]?[0-9a-z]?\.xtube\.com\/(.*)flv
acl vimeo_query url_regex -i bitcast\.vimeo\.com\/vimeo\/videos\/
acl wrzuta_query url_regex -i va\.wrzuta\.pl\/wa[0-9][0-9][0-9][0-9]?
url_rewrite_access deny youtube_deny
url_rewrite_access allow youtube_query
url_rewrite_access allow metacafe_query
url_rewrite_access allow dailymotion_query
url_rewrite_access allow google_query
url_rewrite_access allow redtube_query
url_rewrite_access allow xtube_query
url_rewrite_access allow vimeo_query
url_rewrite_access allow wrzuta_query
redirector_bypass on


restart your squid and apache

sudo /etc/init.d/squid restart

sudo /etc/init.d/apache2 restart

Configure the browsers to use your proxy and you can check if its working by typing

sudo tail -f /var/log/squid/youtube_cache.log


Hope you get it to work too, those damn kids and their videos bahhh!!!



It works with lighttpd also, make sure you can access [http://localhost/video_cache](http://localhost/video_cache) otherwise the flv files that are in the cache won't get served.

[http://sitegeisha.blogspot.com/2008/11/youtube-cache-with-squid.html](http://sitegeisha.blogspot.com/2008/11/youtube-cache-with-squid.html)

---

### Post by maroon on 2009-02-16
guys,

any update for this how-to on debian/ubuntu that supports the new version of videcocache 1.9 ? 

your help is highly appreciated

regards,

---

### Post by elico on 2011-01-15
i just got into it and the reason that no one is doing anything about it i saw something intresting..
my ISP i using a bunch of squid servers and... nginx webserver as a LOCAL cache storage.
from what i have seen it's mainly for ms updates but im looking for a  way to buid something free \opensource based that will work and maybe with api and stuff...

---

### Post by wallander_kurt on 2011-04-27
Hi, 

Is videocache a free product?

No I think. 

is there any other tweaking possible with squid ?

with Ubuntu 9.10 squid available version via apt repos is 3 , which is not capable of caching youtube as i read. 

Googling directs me to caching with squid 2.7STABLE9, with some changes. 

But none worked so far

Regards,

---

