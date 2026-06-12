---
title: "Apache2 FastCGI which modules are not needed?"
date: 2010-05-10
forum: Server Platforms
---

### Post by ravingmad on 2010-05-10
Hi all, I've been having performance problems with Apache2 spiking my CPU at 100% which is located in a different thread. The reason for this separate post it to ask specifically about Apache's modules and I don't want to necessarily link this to the other topic right now, hope that's ok? I will however update both topics and mark as solved once I am 100% sure I have resolved them.

Anyhow. In my endeavours to solve my poor Apache performance problems I came across so many articles dealing with tweaking performance. Some suggested turning on cache, diskcache and memcache modules which I did but I still had the CPU spiking. 

Then I found an [interesting article]("http://www.joomlaperformance.com/articles/webcasts/why_mod_php_is_bad_for_performance_52_13.html") regarding switching Apache to use fastcgi (mod_fcgid) instead of mod_php. I also implemented this change and activated the fcgid module and so far (hold thumbs) things seem much better and pages are being served super fast and I've not seen the CPU spike to 100% in nearly an hour since making the change whereas before it was spiking every 30-60 seconds. What I need to know is how do I now tell that apache is actually now using FCGID and not mod_php as I called up a list of modules from Joomla SysInfo and the mod_php5 module is still loaded. When I disabled it and restarted Apache clicking on pages from sites like Joomla and Wordpress wanted to download the php file and not execute it server side so I re-enabled mod_php5 and then those sites all work again.

I also disabled su_php which was previously loaded and all works with that disabled. Below are the modules currently loaded on the Apache server. Is there any which do not need to be there? Any I can disable to ensure that Apache is onyl using FCGID and nothing else. 

I would really appreciate any help with this.

core 
mod_log_config 
mod_logio 
prefork 
http_core 
mod_so 
mod_alias 
mod_auth_basic 
mod_authn_file 
mod_authz_default 
mod_authz_groupfile 
mod_authz_host 
mod_authz_user 
mod_autoindex 
mod_cache 
mod_cgi 
mod_deflate 
mod_dir 
mod_disk_cache 
mod_env 
mod_expires 
mod_fcgid 
mod_headers 
mod_include 
mod_mem_cache 
mod_mime 
mod_evasive20 
mod_negotiation 
mod_php5 
mod_rewrite 
mod_setenvif 
mod_ssl mod_status

---

