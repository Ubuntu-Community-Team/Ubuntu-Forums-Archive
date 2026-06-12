---
title: "Squid Cache(TCP_MISS)"
date: 2011-03-31
forum: Server Platforms
---

### Post by mkhurram92 on 2011-03-31
hi all there,

i installed Squid Server using webmin 3 days before and redirect all the traffic to this server... After i monitor access.log for cache testing...

it is giving me alot TCP_MISS msgs


1301567341.317  23434 192.168.100.165 TCP_MISS/200 957 POST [http://by2msg3010710.by2.gateway.edge.messenger.live.com/gateway/gateway.dll?](http://by2msg3010710.by2.gateway.edge.messenger.live.com/gateway/gateway.dll?) - DIRECT/64.4.34.80 text/html
1301567341.896    531 192.168.100.165 TCP_MISS/200 1056 POST [http://by2msg3010710.by2.gateway.edge.messenger.live.com/gateway/gateway.dll?](http://by2msg3010710.by2.gateway.edge.messenger.live.com/gateway/gateway.dll?) - DIRECT/64.4.34.80 text/html
1301567344.042    770 192.168.100.155 TCP_MISS/200 1117 POST [http://www.facebook.com/ajax/chat/buddy_list.php?](http://www.facebook.com/ajax/chat/buddy_list.php?) - DIRECT/69.63.190.18 application/x-javascript
1301567347.991    414 192.168.100.161 TCP_MISS/200 316 POST [http://oss-content.securestudies.com/cidpost](http://oss-content.securestudies.com/cidpost) - DIRECT/165.193.73.40 text/plain
1301567351.115    494 192.168.100.161 TCP_MISS/200 316 POST [http://oss-content.securestudies.com/cidpost](http://oss-content.securestudies.com/cidpost) - DIRECT/165.193.73.40 text/plain
1301567352.986    412 192.168.100.161 TCP_MISS/200 316 POST [http://oss-content.securestudies.com/cidpost](http://oss-content.securestudies.com/cidpost) - DIRECT/165.193.73.40 text/plain
1301567354.288    555 192.168.100.150 TCP_MISS/200 6079 GET [http://www.google.com.sa/](http://www.google.com.sa/) - DIRECT/209.85.147.104 text/html
1301567354.516     37 192.168.100.150 TCP_MISS/302 683 GET [http://www.google.com.sa/gen_204?](http://www.google.com.sa/gen_204?) - DIRECT/209.85.147.104 text/html
1301567354.773    254 192.168.100.150 TCP_MISS/204 367 GET [http://www.google.com.sa/gen_204?](http://www.google.com.sa/gen_204?) - DIRECT/209.85.147.104 text/html
1301567354.842    161 192.168.100.150 TCP_MISS/302 856 GET [http://www.google.com.sa/csi?](http://www.google.com.sa/csi?) - DIRECT/209.85.147.106 text/html
1301567355.165    320 192.168.100.150 TCP_MISS/204 413 GET [http://www.google.com.sa/csi?](http://www.google.com.sa/csi?) - DIRECT/209.85.147.106 text/html
1301567355.234    456 192.168.100.150 TCP_MISS/204 322 GET [http://clients1.google.com.sa/generate_204](http://clients1.google.com.sa/generate_204) - DIRECT/74.125.230.163 text/html
1301567355.485    383 192.168.100.161 TCP_MISS/200 316 POST [http://oss-content.securestudies.com/cidpost](http://oss-content.securestudies.com/cidpost) - DIRECT/165.193.73.40 text/plain
1301567356.656    143 192.168.100.150 TCP_MISS/302 724 GET [http://clients1.google.com.sa/complete/search?](http://clients1.google.com.sa/complete/search?) - DIRECT/74.125.230.163 text/html
1301567356.933    274 192.168.100.150 TCP_MISS/200 638 GET [http://clients1.google.com.sa/complete/search?](http://clients1.google.com.sa/complete/search?) - DIRECT/74.125.230.163 text/javascript
1301567357.071    247 192.168.100.150 TCP_MISS/302 742 GET [http://clients1.google.com.sa/complete/search?](http://clients1.google.com.sa/complete/search?) - DIRECT/74.125.230.165 text/html
1301567357.400    326 192.168.100.150 TCP_MISS/200 527 GET [http://clients1.google.com.sa/complete/search?](http://clients1.google.com.sa/complete/search?) - DIRECT/74.125.230.165 text/javascript
1301567357.458    412 192.168.100.161 TCP_MISS/200 316 POST [http://oss-content.securestudies.com/cidpost](http://oss-content.securestudies.com/cidpost) - DIRECT/165.193.73.40 text/plain
1301567357.811     48 192.168.100.150 TCP_MISS/302 736 GET [http://clients1.google.com.sa/complete/search?](http://clients1.google.com.sa/complete/search?) - DIRECT/74.125.230.165 text/html
1301567358.010     91 192.168.100.150 TCP_MISS/302 730 GET [http://clients1.google.com.sa/complete/search?](http://clients1.google.com.sa/complete/search?) - DIRECT/74.125.230.163 text/html
1301567358.173    360 192.168.100.150 TCP_MISS/200 627 GET [http://clients1.google.com.sa/complete/search?](http://clients1.google.com.sa/complete/search?) - DIRECT/74.125.230.165 text/javascript
1301567358.287    274 192.168.100.150 TCP_MISS/200 587 GET [http://clients1.google.com.sa/complete/search?](http://clients1.google.com.sa/complete/search?) - DIRECT/74.125.230.163 text/javascript
1301567359.109     96 192.168.100.150 TCP_MISS/302 719 GET [http://clients1.google.com.sa/complete/search?](http://clients1.google.com.sa/complete/search?) - DIRECT/74.125.230.163 text/html
1301567359.355     29 192.168.100.150 TCP_MISS/302 721 GET [http://clients1.google.com.sa/complete/search?](http://clients1.google.com.sa/complete/search?) - DIRECT/74.125.230.165 text/html
1301567359.400    288 192.168.100.150 TCP_MISS/200 638 GET [http://clients1.google.com.sa/complete/search?](http://clients1.google.com.sa/complete/search?) - DIRECT/74.125.230.163 text/javascript
1301567359.630    269 192.168.100.150 TCP_MISS/200 610 GET [http://clients1.google.com.sa/complete/search?](http://clients1.google.com.sa/complete/search?) - DIRECT/74.125.230.165 text/javascript
1301567359.863     38 192.168.100.150 TCP_MISS/302 722 GET [http://clients1.google.com.sa/complete/search?](http://clients1.google.com.sa/complete/search?) - DIRECT/74.125.230.165 text/html
1301567360.225    359 192.168.100.150 TCP_MISS/200 616 GET [http://clients1.google.com.sa/complete/search?](http://clients1.google.com.sa/complete/search?) - DIRECT/74.125.230.165 text/javascript
1301567362.463    144 192.168.100.150 TCP_MISS/302 747 GET [http://www.google.com.sa/search?](http://www.google.com.sa/search?) - DIRECT/209.85.147.106 text/html
1301567363.059    591 192.168.100.150 TCP_MISS/200 15621 GET [http://www.google.com.sa/search?](http://www.google.com.sa/search?) - DIRECT/209.85.147.106 text/html
1301567363.337      0 192.168.100.150 TCP_NEGATIVE_HIT/204 330 GET [http://clients1.google.com.sa/generate_204](http://clients1.google.com.sa/generate_204) - NONE/- text/html


Pls guide me

---

### Post by SeijiSensei on 2011-03-31
In places where I've installed Squid it caches perhaps a quarter of the objects requested.  There are many things it can't cache.  Some of the entries in your logs are POSTs, where your computer is uploading information to a site.  There's nothing to cache there. You also have a lot of pages in that list with "?" in the URL.  Depending on what was in the query string after the "?", it's pretty likely that each of those requests were at least slightly different so they could not be retrieved from the cache.

Where Squid matters most, I think, is with graphics.  Many sites have lots of static graphic objects -- banners, buttons, etc.  These are all eminently cacheable.

The major reason why I and my clients use Squid is to enforce controls over web browsing using ACL's.  Caching is of secondary importance.

---

### Post by mkhurram92 on 2011-03-31
> 
The major reason why I and my clients use Squid is to enforce controls over web browsing using ACL's.  Caching is of secondary importance.


Proxy is already configured in my enviornment. Now i want to configure it as Cache Server... 

What is have to do now to configure it as Cache server ???

---

### Post by SeijiSensei on 2011-03-31
> **mkhurram92 said:**
> What is have to do now to configure it as Cache server ???

It does caching by default.  Take a look at the log entries for visits to ubuntuforums.org.  What kind of results do you see for things like JPG and GIF files?  Do you see an entry for my avatar, for instance, with URL [http://ubuntuforums.org/customavatars/avatar698195_1.gif?](http://ubuntuforums.org/customavatars/avatar698195_1.gif?)

---

### Post by mkhurram92 on 2011-03-31
> It does caching by default.  Take a look at the log entries for visits to ubuntuforums.org.  What kind of results do you see for things like JPG and GIF files?  Do you see an entry for my avatar, for instance, with URL [http://ubuntuforums.org/customavatars/avatar698195_1.gif?](http://ubuntuforums.org/customavatars/avatar698195_1.gif?)

Here i get some image result that are hitting Cache Like Under


1301548038.355      7 192.168.100.151 TCP_HIT/200 2502 GET [http://l.yimg.com/hb/i/fp/mastheads/fp_spirit_aa_purple_flat.png](http://l.yimg.com/hb/i/fp/mastheads/fp_spirit_aa_purple_flat.png) - NONE/- image/png
1301548038.364      8 192.168.100.151 TCP_HIT/200 1709 GET [http://l.yimg.com/hb/i/sea/fp/img/t1/srch1.png](http://l.yimg.com/hb/i/sea/fp/img/t1/srch1.png) - NONE/- image/png
1301548038.364      8 192.168.100.151 TCP_HIT/200 1581 GET [http://l.yimg.com/hb/i/sea/fp/img/t1/grad.png](http://l.yimg.com/hb/i/sea/fp/img/t1/grad.png) - NONE/- image/png
1301548038.364      8 192.168.100.151 TCP_HIT/200 2367 GET [http://l.yimg.com/hb/i/sea/fp/img/srch-sprite.png](http://l.yimg.com/hb/i/sea/fp/img/srch-sprite.png) - NONE/- image/png
1301548038.364      0 192.168.100.151 TCP_HIT/200 7288 GET [http://l.yimg.com/hb/i/sea/fp/img/combo10asia.png](http://l.yimg.com/hb/i/sea/fp/img/combo10asia.png) - NONE/- image/png
1301548038.367   1060 192.168.100.151 TCP_MISS/200 18222 GET [http://asia.yahoo.com/](http://asia.yahoo.com/) - DIRECT/124.108.120.244 text/html
1301548038.389      6 192.168.100.151 TCP_HIT/200 6757 GET [http://l.yimg.com/hb/i/sea/fp/img/combo10.png](http://l.yimg.com/hb/i/sea/fp/img/combo10.png) - NONE/- image/png
1301548038.389      0 192.168.100.151 TCP_HIT/200 2230 GET [http://l.yimg.com/hb/i/sea/fp/img/trough_asia3.png](http://l.yimg.com/hb/i/sea/fp/img/trough_asia3.png) - NONE/- image/png
1301548038.436      8 192.168.100.151 TCP_HIT/200 1117 GET [http://ads.yimg.com/hb/a/sg/javascript/yad_flash8_20090528.js](http://ads.yimg.com/hb/a/sg/javascript/yad_flash8_20090528.js) - NONE/- application/x-javascript
1301548038.626     16 192.168.100.151 TCP_HIT/200 34011 GET [http://ads.yimg.com/hb/i/sg/adv/houseads/wam_shb_messengerpc_sg_28aug10.swf](http://ads.yimg.com/hb/i/sg/adv/houseads/wam_shb_messengerpc_sg_28aug10.swf) - NONE/- application/x-shockwave-flash
1301548038.654     34 192.168.100.151 TCP_HIT/200 20397 GET [http://l.yimg.com/hb/combo?](http://l.yimg.com/hb/combo?) - NONE/- application/x-javascript
1301548038.752      0 192.168.100.151 TCP_HIT/200 878 GET [http://l.yimg.com/i/i/sg/se/j/osdl.xml](http://l.yimg.com/i/i/sg/se/j/osdl.xml) - NONE/- application/xml


But y not all other huge contents are in cache They are still TCP_MISS ???

i have some doubt in Refresh Rules. Can anyone check that, attached is image from webmin of refresh rules

---

### Post by mkhurram92 on 2011-04-03
Is there any update on my matter ???

---

### Post by diedo on 2011-08-12
Bump i'm experiencing the same problem

---

### Post by diedo on 2011-08-12
anyone please

---

### Post by robgr85 on 2011-08-12
I think it might be a filesystem issue. Got similar squid missing hits almost everytime, when trying to put squid cache on NTFS disk partition.

What about error logs? Are there any entries from squid?

Cheers,
Robert

---

### Post by diedo on 2011-08-14
> **robgr85 said:**
> I think it might be a filesystem issue. Got similar squid missing hits almost everytime, when trying to put squid cache on NTFS disk partition.

What about error logs? Are there any entries from squid?

Cheers,
Robert

 the file system is right it's on ext4 

here is some logs 

1. access.log
```
1313304007.597   1220 192.168.32.1 TCP_MISS/200 21460 GET http://ubuntuforums.org/showthread.php? - DIRECT/91.189.94.12 text/html
1313304007.598    320 192.168.32.1 TCP_SWAPFAIL_MISS/304 307 GET http://ubuntuforums.org/clientscript/vbulletin_important.css? - DIRECT/91.189.94.12 -
1313304007.637    322 192.168.32.1 TCP_SWAPFAIL_MISS/304 308 GET http://ubuntuforums.org/clientscript/vbulletin_menu.js? - DIRECT/91.189.94.12 -
1313304007.658    326 192.168.32.1 TCP_MISS/200 1419 GET http://ubuntuforums.org/clientscript/vbulletin_post_loader.js? - DIRECT/91.189.94.12 application/x-javascript
1313304007.750    151 192.168.32.1 TCP_MISS/200 2623 GET http://ubuntuforums.org/clientscript/vbulletin_ajax_tagsugg.js? - DIRECT/91.189.94.12 application/x-javascript
1313304007.767    130 192.168.32.1 TCP_SWAPFAIL_MISS/304 308 GET http://ubuntuforums.org/clientscript/vbulletin_lightbox.js? - DIRECT/91.189.94.12 -
1313304007.809    283 192.168.32.1 TCP_SWAPFAIL_MISS/304 308 GET http://ubuntuforums.org/clientscript/vbulletin_ajax_taglist.js? - DIRECT/91.189.94.12 -
1313304007.810    150 192.168.32.1 TCP_MISS/200 1403 GET http://ubuntuforums.org/clientscript/vbulletin_multi_quote.js? - DIRECT/91.189.94.12 application/x-javascript
1313304007.887    132 192.168.32.1 TCP_SWAPFAIL_MISS/304 308 GET http://ubuntuforums.org/clientscript/vbulletin_textedit.js? - DIRECT/91.189.94.12 -
1313304007.917    148 192.168.32.1 TCP_SWAPFAIL_MISS/304 308 GET http://ubuntuforums.org/clientscript/vbulletin_quick_edit.js? - DIRECT/91.189.94.12 -
1313304007.942    627 192.168.32.1 TCP_MISS/200 8952 GET http://ubuntuforums.org/clientscript/vbulletin_global.js? - DIRECT/91.189.94.12 application/x-javascript
1313304007.968    157 192.168.32.1 TCP_MISS/200 2615 GET http://ubuntuforums.org/clientscript/vbulletin_quick_reply.js? - DIRECT/91.189.94.12 application/x-javascript
1313304008.378    398 192.168.32.1 TCP_MISS/200 1617 GET http://ubuntuforums.org/clientscript/vbulletin_editor.css? - DIRECT/91.189.94.12 text/css
1313304008.446    925 192.168.32.1 TCP_SWAPFAIL_MISS/200 721 GET http://mystatus.skype.com/smallicon/robert.85. - DIRECT/204.9.163.163 image/png
1313304009.350    769 192.168.32.1 TCP_MISS/200 466 GET http://www.google-analytics.com/__utm.gif? - DIRECT/209.85.148.101 image/gif
1313304009.829  43325 192.168.32.1 TCP_MISS/200 1881 GET http://2.251.channel.facebook.com/x/3586540857/3951225087/false/p_1138545365=17 - DIRECT/66.220.145.46 application/json
1313304009.829  43062 192.168.32.1 TCP_MISS/200 1036 GET http://3.251.channel.facebook.com/x/3928622071/2642638453/false/p_1138545365=17 - DIRECT/66.220.145.46 application/json
1313304031.209   1436 192.168.32.1 TCP_MISS/200 897 POST http://www.facebook.com/ajax/chat/buddy_list.php? - DIRECT/69.63.189.39 application/x-javascript
1313304033.118    548 192.168.32.1 TCP_MISS/503 3890 GET http://pastebin/ - DIRECT/pastebin text/html
1313304033.331      0 192.168.32.1 TCP_MISS/503 3891 GET http://pastebin/favicon.ico - DIRECT/pastebin text/html
1313304033.341      0 192.168.32.1 TCP_MISS/503 3923 GET http://pastebin/favicon.ico - DIRECT/pastebin text/html
1313304033.345      1 192.168.32.1 TCP_MISS/503 3923 GET http://pastebin/favicon.ico - DIRECT/pastebin text/html
1313304037.594    127 192.168.32.1 TCP_MISS/000 0 GET http://suggestqueries.google.com/complete/search? - DIRECT/suggestqueries.google.com -
1313304037.908     59 192.168.32.1 TCP_MISS/000 0 GET http://suggestqueries.google.com/complete/search? - DIRECT/suggestqueries.google.com -
1313304038.939    383 192.168.32.1 TCP_MISS/200 542 GET http://suggestqueries.google.com/complete/search? - DIRECT/209.85.148.102 text/javascript
1313304040.609    768 192.168.32.1 TCP_MISS/302 793 GET http://www.google.com/search? - DIRECT/209.85.148.106 text/html
1313304042.181   1566 192.168.32.1 TCP_MISS/200 27329 GET http://www.google.co.uk/search? - DIRECT/209.85.148.105 text/html
1313304042.701    620 192.168.32.1 TCP_MISS/200 2202 GET http://news.google.co.uk/news/tbn/ujiYC34amgwJ - DIRECT/209.85.148.102 image/jpeg
1313304043.148    749 192.168.32.1 TCP_MISS/204 261 GET http://clients1.google.co.uk/generate_204 - DIRECT/209.85.148.113 text/html
1313304043.559    403 192.168.32.1 TCP_MISS/204 351 GET http://www.google.co.uk/csi? - DIRECT/209.85.148.105 image/gif
1313304044.368   1212 192.168.32.1 TCP_MISS/200 3821 GET http://pastebin.com/ - DIRECT/184.154.125.14 text/html
1313304044.664     75 192.168.32.1 TCP_MISS/000 0 GET http://www.google.co.uk/url? - DIRECT/www.google.co.uk -
1313304045.301    635 192.168.32.1 TCP_MISS/200 7320 GET http://pastebin.com/ - DIRECT/184.154.125.14 text/html
1313304045.833    560 192.168.32.1 TCP_MISS/304 269 GET http://pastebin.com/i/style.css? - DIRECT/184.154.125.14 -
1313304045.851    561 192.168.32.1 TCP_MISS/304 269 GET http://pastebin.com/i/fixed.css? - DIRECT/184.154.125.14 -
1313304045.851    551 192.168.32.1 TCP_MISS/200 765 GET http://pastebin.com/i/highlight.png - DIRECT/184.154.125.14 image/png
1313304046.169    880 192.168.32.1 TCP_MISS/304 479 GET http://platform.twitter.com/widgets.js - DIRECT/2.16.88.124 application/javascript
1313304046.378   1066 192.168.32.1 TCP_MISS/200 400 GET http://lolbin.net/stats.php - DIRECT/184.154.125.12 text/html
1313304046.621    375 192.168.32.1 TCP_MISS/200 1681 GET http://pastebin.com/etc/social/index.html - DIRECT/184.154.125.14 text/html
1313304046.630    328 192.168.32.1 TCP_MISS/200 466 GET http://www.google-analytics.com/__utm.gif? - DIRECT/209.85.148.101 image/gif
1313304046.719    397 192.168.32.1 TCP_MISS/200 809 GET http://pastebin.com/i/bg-button.gif - DIRECT/184.154.125.14 image/gif
1313304046.729    407 192.168.32.1 TCP_MISS/200 1308 GET http://pastebin.com/i/settings.png - DIRECT/184.154.125.14 image/png
1313304046.890    588 192.168.32.1 TCP_MISS/204 332 GET http://pixel.quantserve.com/pixel;r=1050271986;fpan=0;fpa=P0-1024441005-1313126124283;ns=0;url=http%3A%2F%2Fpastebin.com%2F;ref=http%3A%2F%2Fwww.google.co.uk%2Fsearch%3Fq%3Dpaste%2Bbin%26ie%3Dutf-8%26oe%3Dutf-8%26aq%3Dt%26rls%3Dorg.mozilla%3Aen-US%3Aofficial%26client%3Dfirefox-a;ce=1;je=0;sr=1600x900x24;enc=n;ogl=description.Pastebin%252Ecom%20is%20the%20number%20one%20paste%20tool%20since%202002%252E%20Pastebin%20is%20a%20website%20wher%2Ctitle.Pastebin%252Ecom%20-%20%231%20paste%20tool%20since%202002!%2Curl.http%3A%2F%2Fpastebin%252Ecom%2F%2Cimage.http%3A%2F%2Fpastebin%252Ecom%2Fi%2Ffb%252Ejpg%2Csite_name.Pastebin;dst=1;et=1313304051824;tzo=-180;a=p-306sOjcgY0NWo - DIRECT/95.172.94.52 -
1313304046.919    536 192.168.32.1 TCP_MISS/200 906 GET http://pastebin.com/i/error.png - DIRECT/184.154.125.14 image/png
1313304047.158    533 192.168.32.1 TCP_MISS/200 12949 GET http://platform.twitter.com/widgets/follow_button.html - DIRECT/2.16.88.124 text/html
1313304047.449    804 192.168.32.1 TCP_MISS/304 383 GET http://connect.facebook.net/en_US/all.js - DIRECT/92.123.111.139 application/x-javascript
1313304047.449    269 192.168.32.1 TCP_MISS/200 572 GET http://platform.twitter.com/widgets/images/f.gif? - DIRECT/2.16.88.124 image/gif
1313304047.922    742 192.168.32.1 TCP_MISS/200 1505 GET http://cdn.api.twitter.com/1/users/show.json? - DIRECT/2.16.62.124 application/json
1313304048.810    693 192.168.32.1 TCP_MISS/304 268 GET http://www.facebook.com/extern/login_status.php? - DIRECT/69.63.189.39 text/plain
1313304049.198   1078 192.168.32.1 TCP_MISS/200 7111 GET http://www.facebook.com/plugins/like.php? - DIRECT/69.63.189.39 text/html
1313304050.840    575 192.168.32.1 TCP_MISS/200 2527 GET http://static.ak.fbcdn.net/connect/xd_proxy.php? - DIRECT/77.109.169.184 text/html
1313304064.004  54153 192.168.32.1 TCP_MISS/200 2948 GET http://2.251.channel.facebook.com/x/4272451959/3951225087/false/p_1138545365=18 - DIRECT/66.220.145.46 application/json
1313304064.129  54251 192.168.32.1 TCP_MISS/200 1399 GET http://3.251.channel.facebook.com/x/3154587218/2642638453/false/p_1138545365=18 - DIRECT/66.220.145.46 application/json
1313304065.025    883 192.168.32.1 TCP_MISS/200 3259 GET http://profile.ak.fbcdn.net/hprofile-ak-snc4/275872_100001820875422_5717925_q.jpg - DIRECT/77.109.169.136 image/jpeg
1313304119.474  55351 192.168.32.1 TCP_MISS/200 375 GET http://2.251.channel.facebook.com/x/3180142026/3951225087/false/p_1138545365=19 - DIRECT/66.220.145.46 application/json
1313304119.618  55471 192.168.32.1 TCP_MISS/200 400 GET http://3.251.channel.facebook.com/x/2405486441/2642638453/false/p_1138545365=19 - DIRECT/66.220.145.46 application/json
1313304132.233    959 192.168.32.1 TCP_MISS/200 899 POST http://www.facebook.com/ajax/chat/buddy_list.php? - DIRECT/69.63.189.39 application/x-javascript
1313304154.936    616 192.168.32.1 TCP_MISS/200 757 POST http://www.facebook.com/ajax/chat/buddy_list.php? - DIRECT/69.63.189.39 application/x-javascript
1313304162.720 116073 192.168.32.1 TCP_MISS/200 5532 CONNECT apis.google.com:443 - DIRECT/209.85.148.102 -
1313304164.720 116599 192.168.32.1 TCP_MISS/200 1607 CONNECT plusone.google.com:443 - DIRECT/209.85.148.138 -
1313304174.917  55409 192.168.32.1 TCP_MISS/200 375 GET http://2.251.channel.facebook.com/x/1874439510/3951225087/false/p_1138545365=19 - DIRECT/66.220.145.46 application/json
1313304175.128  55456 192.168.32.1 TCP_MISS/200 400 GET http://3.251.channel.facebook.com/x/602191332/2642638453/false/p_1138545365=19 - DIRECT/66.220.145.46 application/json
1313304230.286  55360 192.168.32.1 TCP_MISS/200 375 GET http://2.251.channel.facebook.com/x/2221149867/3951225087/false/p_1138545365=19 - DIRECT/66.220.145.46 application/json
1313304230.611  55466 192.168.32.1 TCP_MISS/200 400 GET http://3.251.channel.facebook.com/x/2312898410/2642638453/false/p_1138545365=19 - DIRECT/66.220.145.46 application/json
1313304233.150    904 192.168.32.1 TCP_MISS/200 757 POST http://www.facebook.com/ajax/chat/buddy_list.php? - DIRECT/69.63.190.10 application/x-javascript
1313304285.664  55373 192.168.32.1 TCP_MISS/200 375 GET http://2.251.channel.facebook.com/x/3920668387/3951225087/false/p_1138545365=19 - DIRECT/66.220.145.46 application/json
1313304286.114  55491 192.168.32.1 TCP_MISS/200 400 GET http://3.251.channel.facebook.com/x/69861472/2642638453/false/p_1138545365=19 - DIRECT/66.220.145.46 application/json

```

squid.conf

```

acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl localhost src ::1/128
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32
acl to_localhost dst ::1/128
# should be allowed
acl localnet src 10.0.0.0/8	# RFC1918 possible internal network
acl localnet src 172.16.0.0/12	# RFC1918 possible internal network
acl localnet src 192.168.0.0/16	# RFC1918 possible internal network
acl localnet src fc00::/7   # RFC 4193 local private network range
acl localnet src fe80::/10  # RFC 4291 link-local (directly plugged) machines
acl SSL_ports port 443
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localnet
http_access allow localhost
http_access deny all
http_port 3128 
visible_hostname localhost
hierarchy_stoplist cgi-bin ?
cache_mem 0
cache_dir ufs /var/spool/squid 640 32 512 max-size=1048576
minimum_object_size 20 KB
maximum_object_size 500 MB
cache_swap_low 96
cache_swap_high 97
memory_replacement_policy lru
coredump_dir /var/spool/squid

# Add any of your own refresh_pattern entries above these.
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern -i (/cgi-bin/|\?) 0	0%	0
refresh_pattern .		0	20%	4320
```

Please someone reply me ASAP i should give  this server by today and i still can't find a fix for it it's all TCP_MISS/200 nothing is cached at all

---

