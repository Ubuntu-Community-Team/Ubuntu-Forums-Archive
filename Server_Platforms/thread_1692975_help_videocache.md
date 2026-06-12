---
title: "help videocache"
date: 2011-02-22
forum: Server Platforms
---

### Post by grantang on 2011-02-22
Hi all,,
I setting squid-2.7.STABLE9 + videocache-1.9.2 then i try one link at youtube.com, when buffering done videocache result like :
[IMG]http://i1140.photobucket.com/albums/n568/cupak/itam/videocache.jpg[/IMG]
the size is "0"
when i try open link youtube same at other computer, youtube error [B]"An error occurred, please try again later"
[/B]this quote my squid.conf
```

# --BEGIN-- videocache config for squid
url_rewrite_program /usr/bin/python /usr/share/videocache/videocache.py
url_rewrite_children 7
acl videocache_allow_url url_regex -i \.youtube\.com\/get_video\?
acl videocache_allow_url url_regex -i \.youtube\.com\/videoplayback \.youtube\.com\/videoplay \.youtube\.com\/get_video\?
acl videocache_allow_url url_regex -i \.youtube\.[a-z][a-z]\/videoplayback \.youtube\.[a-z][a-z]\/videoplay \.youtube\.[a-z][a-z]\/get_video\?
acl videocache_allow_url url_regex -i \.googlevideo\.com\/videoplayback \.googlevideo\.com\/videoplay \.googlevideo\.com\/get_video\?
acl videocache_allow_url url_regex -i \.google\.com\/videoplayback \.google\.com\/videoplay \.google\.com\/get_video\?
acl videocache_allow_url url_regex -i \.google\.[a-z][a-z]\/videoplayback \.google\.[a-z][a-z]\/videoplay \.google\.[a-z][a-z]\/get_video\?
acl videocache_allow_url url_regex -i (25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\/videoplayback\?
acl videocache_allow_url url_regex -i (25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\/videoplay\?
acl videocache_allow_url url_regex -i (25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\/get_video\?
acl videocache_allow_url url_regex -i proxy[a-z0-9\-][a-z0-9][a-z0-9][a-z0-9]?\.dailymotion\.com\/
acl videocache_allow_url url_regex -i vid\.akm\.dailymotion\.com\/
acl videocache_allow_url url_regex -i [a-z0-9][0-9a-z][0-9a-z]?[0-9a-z]?[0-9a-z]?\.xtube\.com\/(.*)flv
acl videocache_allow_url url_regex -i bitcast\.vimeo\.com\/vimeo\/videos\/
acl videocache_allow_url url_regex -i va\.wrzuta\.pl\/wa[0-9][0-9][0-9][0-9]?
acl videocache_allow_url url_regex -i \.files\.youporn\.com\/(.*)\/flv\/
acl videocache_allow_url url_regex -i \.msn\.com\.edgesuite\.net\/(.*)\.flv
acl videocache_allow_url url_regex -i media[a-z0-9]?[a-z0-9]?[a-z0-9]?\.tube8\.com\/ mobile[a-z0-9]?[a-z0-9]?[a-z0-9]?\.tube8\.com\/
acl videocache_allow_url url_regex -i \.mais\.uol\.com\.br\/(.*)\.flv
acl videocache_allow_url url_regex -i \.video[a-z0-9]?[a-z0-9]?\.blip\.tv\/(.*)\.(flv|avi|mov|mp3|m4v|mp4|wmv|rm|ram)
acl videocache_allow_url url_regex -i video\.break\.com\/(.*)\.(flv|mp4)
acl videocache_allow_dom dstdomain .mccont.com .metacafe.com .redtube.com .cdn.dailymotion.com
acl videocache_deny_url url_regex -i http:\/\/[a-z][a-z]\.youtube\.com http:\/\/www\.youtube\.com
url_rewrite_access deny videocache_deny_url
url_rewrite_access allow videocache_allow_url
url_rewrite_access allow videocache_allow_dom
redirector_bypass on
# --END-- videocache config for squid

```Did I miss anything?

---

### Post by marlow_bg on 2011-02-23
Hello there,

I am using videocache from [http://cachevideos.com](http://cachevideos.com) since 4-5 months and up to now I was pretty happy with it - working fine of course with some little bugs.

From 4-5 days youtube changed something in their flash player (it buffers the clip on portions not the entire at once) and now youtube cache is not working properly. It says in the log CACHE_HIT and rewrites the url but actually it is downloading from internet not from cache.

I was trying to contact Kulbir Saini (creator of videocache) regarding this issue but he is not responding on e-mail neither in his forum. 

Now on your question: I don't know any reason why your files are with 0 size. 

You can post here your videocache.conf so I can take a look and tell you if I find something wrong.

---

### Post by grantang on 2011-02-24
@marlow_bg, 
thanks to replay, this my videocache.conf
```

enable_video_cache = 1
cache_host = 192.168.9.2
proxy = http://192.168.9.2:3128/
proxy_username = proxy
hit_threshold = 1
base_dir = /videocache/
disk_avail_threshold = 100
temp_dir = tmp
max_parallel_downloads = 30
enable_videocache_cleaner = 1
video_lifetime = 60
logdir = /var/log/videocache/
max_logfile_size = 10
max_logfile_backups = 10
rpc_host = 127.0.0.1
rpc_port = 9100
enable_youtube_cache = 1
youtube_cache_dir = youtube
max_youtube_video_size = 0
min_youtube_video_size = 0
# Metacafe.com Options
enable_metacafe_cache = 1
metacafe_cache_dir = metacafe
max_metacafe_video_size = 0
min_metacafe_video_size = 0

# Dailymotion.com Options
enable_dailymotion_cache = 1
dailymotion_cache_dir = dailymotion
max_dailymotion_video_size = 0
min_dailymotion_video_size = 0

# Google.com Options
enable_google_cache = 1
google_cache_dir = google
max_google_video_size = 0
min_google_video_size = 0

# Redute.com Options
enable_redtube_cache = 1
redtube_cache_dir = redtube
max_redtube_video_size = 0
min_redtube_video_size = 0

# Xtube.com Options
enable_xtube_cache = 1
xtube_cache_dir = xtube
max_xtube_video_size = 0
min_xtube_video_size = 0

# Vimeo.com Options
enable_vimeo_cache = 1
vimeo_cache_dir = vimeo
max_vimeo_video_size = 0
min_vimeo_video_size = 0

# Wrzuta.pl Options
enable_wrzuta_cache = 1
wrzuta_cache_dir = wrzuta
max_wrzuta_video_size = 0
min_wrzuta_video_size = 0

# Youporn.com Options
enable_youporn_cache = 1
youporn_cache_dir = youporn
max_youporn_video_size = 0
min_youporn_video_size = 0

# Soapbox.msn.com Options
enable_soapbox_cache = 1
soapbox_cache_dir = soapbox
max_soapbox_video_size = 0
min_soapbox_video_size = 0

# Tube8.com Options
enable_tube8_cache = 1
tube8_cache_dir = tube8
max_tube8_video_size = 0
min_tube8_video_size = 0

# Tvuol.uol.com.br Options
enable_tvuol_cache = 1
tvuol_cache_dir = tvuol
max_tvuol_video_size = 0
min_tvuol_video_size = 0

# Blip.tv Options
enable_bliptv_cache = 1
bliptv_cache_dir = bliptv
max_bliptv_video_size = 0
min_bliptv_video_size = 0

# Break.com Options
enable_break_cache = 1
break_cache_dir = break
max_break_video_size = 0
min_break_video_size = 0


```

---

### Post by marlow_bg on 2011-02-24
Hello 

What I see from your videocache.conf is that you are using proxy for the videocache, can you just try without it:

leave this field empty:


proxy =

proxy_username =

proxy_password =


Also can you show a part of your videocache.log file, to see what is happening there.

---

### Post by grantang on 2011-02-24
ok, i'll try

thanks

---

