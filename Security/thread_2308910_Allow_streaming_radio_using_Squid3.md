---
title: "Allow streaming radio using Squid3"
date: 2016-01-06
forum: Security
---

### Post by justonetaste2003 on 2016-01-06
Trying to create a proxy to allow me to listen to music in situations where it might be blocked.  Have setup a Proxy Server using Squid3 on ubuntu.  I could use some help figuring out how to allow this radio station to be "allowed" through the proxy.  Currently, it doesn't start playing.  Below is the access.log entries upon trying to access [www.radioparadise.com](www.radioparadise.com).


```
1452093305.223      0 111.222.333.444 TCP_DENIED/407 3739 CONNECT aus5.mozilla.org:443 - HIER_NONE/- text/html
1452093305.748      0 111.222.333.444 TCP_DENIED/407 3771 CONNECT snippets.cdn.mozilla.net:443 - HIER_NONE/- text/html
1452093310.484      3 111.222.333.444 TCP_MISS/200 906 POST [http://ocsp.digicert.com/](http://ocsp.digicert.com/) admin HIER_DIRECT/72.21.91.29 application/ocsp-response
1452093310.978     81 111.222.333.444 TCP_MISS/302 378 GET [http://radioparadise.com/](http://radioparadise.com/) admin HIER_DIRECT/23.29.117.2 text/html
1452093311.088     83 111.222.333.444 TCP_MISS/302 440 GET [http://www.radioparadise.com//](http://www.radioparadise.com//) admin HIER_DIRECT/23.29.117.2 text/html
1452093311.182     65 111.222.333.444 TCP_MISS/200 3516 GET [http://www.radioparadise.com/rp_2.php?](http://www.radioparadise.com/rp_2.php?) admin HIER_DIRECT/23.29.117.2 text/html
1452093311.234      6 111.222.333.444 TCP_MISS_ABORTED/000 0 GET [http://www.radioparadise.com/rp2-content.php](http://www.radioparadise.com/rp2-content.php) admin HIER_DIRECT/23.29.117.2 -
1452093311.346     80 111.222.333.444 TCP_MISS/200 3356 GET [http://www.radioparadise.com/rp2_player_1.php?](http://www.radioparadise.com/rp2_player_1.php?) admin HIER_DIRECT/23.29.117.2 text/html
1452093311.352     79 111.222.333.444 TCP_MISS/200 4480 GET [http://www.radioparadise.com/rp2_player_2.php?](http://www.radioparadise.com/rp2_player_2.php?) admin HIER_DIRECT/23.29.117.2 text/html
1452093311.409      0 111.222.333.444 TCP_HIT/200 8653 GET [http://www.radioparadise.com/scripts/ui/jquery.ui.core.js](http://www.radioparadise.com/scripts/ui/jquery.ui.core.js) admin HIER_NONE/- application/javascript
1452093311.411    145 111.222.333.444 TCP_MISS/200 20566 GET [http://www.radioparadise.com/rp2-content.php?](http://www.radioparadise.com/rp2-content.php?) admin HIER_DIRECT/23.29.117.2 text/html
1452093311.428     36 111.222.333.444 TCP_HIT/200 33067 GET [http://www.radioparadise.com/scripts/soundmanager2-nodebug-jsmin.js](http://www.radioparadise.com/scripts/soundmanager2-nodebug-jsmin.js) admin HIER_NONE/- application/javascript
1452093311.433      0 111.222.333.444 TCP_HIT/200 7418 GET [http://www.radioparadise.com/scripts/ui/jquery.ui.widget.js](http://www.radioparadise.com/scripts/ui/jquery.ui.widget.js) admin HIER_NONE/- application/javascript
1452093311.441      0 111.222.333.444 TCP_HIT/200 4698 GET [http://www.radioparadise.com/scripts/ui/jquery.ui.mouse.js](http://www.radioparadise.com/scripts/ui/jquery.ui.mouse.js) admin HIER_NONE/- application/javascript
1452093311.441      0 111.222.333.444 TCP_HIT/200 18002 GET [http://www.radioparadise.com/scripts/ui/jquery.ui.slider.js](http://www.radioparadise.com/scripts/ui/jquery.ui.slider.js) admin HIER_NONE/- application/javascript
1452093311.444     39 111.222.333.444 TCP_REFRESH_UNMODIFIED/200 16003 GET [http://www.radioparadise.com/css/rp2-style.1.css?](http://www.radioparadise.com/css/rp2-style.1.css?) admin HIER_DIRECT/23.29.117.2 text/css
1452093311.449     39 111.222.333.444 TCP_REFRESH_UNMODIFIED/200 675 GET [http://www.radioparadise.com/scripts/themes/base/jquery.ui.all.css?](http://www.radioparadise.com/scripts/themes/base/jquery.ui.all.css?) admin HIER_DIRECT/23.29.117.2 text/css
1452093311.451      0 111.222.333.444 TCP_HIT/200 11822 GET [http://www.radioparadise.com/scripts/boxover.js](http://www.radioparadise.com/scripts/boxover.js) admin HIER_NONE/- application/javascript
1452093311.485     40 111.222.333.444 TCP_REFRESH_UNMODIFIED/200 5330 GET [http://www.radioparadise.com/scripts/rp2.js?](http://www.radioparadise.com/scripts/rp2.js?) admin HIER_DIRECT/23.29.117.2 application/javascript
1452093311.489      0 111.222.333.444 TCP_HIT/200 1047 GET [http://www.radioparadise.com/scripts/themes/base/jquery.ui.base.css](http://www.radioparadise.com/scripts/themes/base/jquery.ui.base.css) admin HIER_NONE/- text/css
1452093311.490      0 111.222.333.444 TCP_HIT/200 18511 GET [http://www.radioparadise.com/scripts/themes/base/jquery.ui.theme.css](http://www.radioparadise.com/scripts/themes/base/jquery.ui.theme.css) admin HIER_NONE/- text/css
1452093311.518      0 111.222.333.444 TCP_HIT/200 1455 GET [http://www.radioparadise.com/scripts/themes/base/jquery.ui.accordion.css](http://www.radioparadise.com/scripts/themes/base/jquery.ui.accordion.css) admin HIER_NONE/- text/css
1452093311.518      0 111.222.333.444 TCP_HIT/200 2860 GET [http://www.radioparadise.com/scripts/themes/base/jquery.ui.button.css](http://www.radioparadise.com/scripts/themes/base/jquery.ui.button.css) admin HIER_NONE/- text/css
1452093311.518      0 111.222.333.444 TCP_HIT/200 4450 GET [http://www.radioparadise.com/scripts/themes/base/jquery.ui.datepicker.css](http://www.radioparadise.com/scripts/themes/base/jquery.ui.datepicker.css) admin HIER_NONE/- text/css
1452093311.518      0 111.222.333.444 TCP_HIT/200 1499 GET [http://www.radioparadise.com/scripts/themes/base/jquery.ui.autocomplete.css](http://www.radioparadise.com/scripts/themes/base/jquery.ui.autocomplete.css) admin HIER_NONE/- text/css
1452093311.521      0 111.222.333.444 TCP_HIT/200 1747 GET [http://www.radioparadise.com/scripts/themes/base/jquery.ui.dialog.css](http://www.radioparadise.com/scripts/themes/base/jquery.ui.dialog.css) admin HIER_NONE/- text/css
1452093311.521      0 111.222.333.444 TCP_HIT/200 1561 GET [http://www.radioparadise.com/scripts/themes/base/jquery.ui.resizable.css](http://www.radioparadise.com/scripts/themes/base/jquery.ui.resizable.css) admin HIER_NONE/- text/css
1452093311.524      0 111.222.333.444 TCP_HIT/200 1848 GET [http://www.radioparadise.com/scripts/themes/base/jquery.ui.core.css](http://www.radioparadise.com/scripts/themes/base/jquery.ui.core.css) admin HIER_NONE/- text/css
1452093311.525      0 111.222.333.444 TCP_HIT/200 711 GET [http://www.radioparadise.com/scripts/themes/base/jquery.ui.selectable.css](http://www.radioparadise.com/scripts/themes/base/jquery.ui.selectable.css) admin HIER_NONE/- text/css
1452093311.525      0 111.222.333.444 TCP_HIT/200 1552 GET [http://www.radioparadise.com/scripts/themes/base/jquery.ui.slider.css](http://www.radioparadise.com/scripts/themes/base/jquery.ui.slider.css) admin HIER_NONE/- text/css
1452093311.526      0 111.222.333.444 TCP_HIT/200 1772 GET [http://www.radioparadise.com/scripts/themes/base/jquery.ui.tabs.css](http://www.radioparadise.com/scripts/themes/base/jquery.ui.tabs.css) admin HIER_NONE/- text/css
1452093311.528      0 111.222.333.444 TCP_HIT/200 745 GET [http://www.radioparadise.com/scripts/themes/base/jquery.ui.progressbar.css](http://www.radioparadise.com/scripts/themes/base/jquery.ui.progressbar.css) admin HIER_NONE/- text/css
1452093311.530     79 111.222.333.444 TCP_REFRESH_UNMODIFIED/200 8438 GET [http://www.radioparadise.com/css/rp2-home.css?](http://www.radioparadise.com/css/rp2-home.css?) admin HIER_DIRECT/23.29.117.2 text/css
1452093311.560      0 111.222.333.444 TCP_HIT/200 9614 GET [http://www.radioparadise.com/graphics/icecast.png](http://www.radioparadise.com/graphics/icecast.png) admin HIER_NONE/- image/png
1452093311.566      0 111.222.333.444 TCP_HIT/200 428 GET [http://www.radioparadise.com/clear.gif](http://www.radioparadise.com/clear.gif) admin HIER_NONE/- image/gif
1452093311.576    121 111.222.333.444 TCP_MISS/301 286 GET [http://verify.authorize.net/anetseal/seal.js](http://verify.authorize.net/anetseal/seal.js) admin HIER_DIRECT/23.203.59.175 -
1452093311.576    188 111.222.333.444 TCP_HIT/200 94271 GET [http://www.radioparadise.com/scripts/jquery_1_7_1.js](http://www.radioparadise.com/scripts/jquery_1_7_1.js) admin HIER_NONE/- application/javascript
1452093311.582     23 111.222.333.444 TCP_HIT/200 26379 GET [http://www.radioparadise.com/graphics/covers/m/B002ELM5HY.jpg](http://www.radioparadise.com/graphics/covers/m/B002ELM5HY.jpg) admin HIER_NONE/- image/jpeg
1452093311.639     79 111.222.333.444 TCP_REFRESH_UNMODIFIED/200 18235 GET [http://www.radioparadise.com/graphics/rp_mobile.png?](http://www.radioparadise.com/graphics/rp_mobile.png?) admin HIER_DIRECT/23.29.117.2 image/png
1452093311.653      0 111.222.333.444 TCP_DENIED/407 3767 CONNECT safebrowsing.google.com:443 - HIER_NONE/- text/html
1452093311.735     12 111.222.333.444 TCP_MISS/200 2584 POST [http://ocsp.entrust.net/](http://ocsp.entrust.net/) admin HIER_DIRECT/2600:1406:34:287::1b01 application/ocsp-response
1452093311.904      0 111.222.333.444 TCP_HIT/200 8991 GET [http://www.radioparadise.com/scripts/swf/soundmanager2_flash9.swf](http://www.radioparadise.com/scripts/swf/soundmanager2_flash9.swf) admin HIER_NONE/- application/x-shockwave-flash
1452093311.933      0 111.222.333.444 TCP_DENIED/407 3783 CONNECT shavar.services.mozilla.com:443 - HIER_NONE/- text/html
1452093311.950     27 111.222.333.444 TCP_HIT/200 29519 GET [http://www.radioparadise.com/graphics/welcome_4.jpg](http://www.radioparadise.com/graphics/welcome_4.jpg) admin HIER_NONE/- image/jpeg
1452093311.999     80 111.222.333.444 TCP_REFRESH_UNMODIFIED/200 12736 GET [http://www.radioparadise.com/graphics/logo_2011_360.png?](http://www.radioparadise.com/graphics/logo_2011_360.png?) admin HIER_DIRECT/23.29.117.2 image/png
1452093312.000     80 111.222.333.444 TCP_MISS/200 1358 GET [http://www.radioparadise.com/RP_flash_map.php?](http://www.radioparadise.com/RP_flash_map.php?) admin HIER_DIRECT/23.29.117.2 text/html
1452093312.003     80 111.222.333.444 TCP_HIT/200 52846 GET [http://www.radioparadise.com/graphics/support_speakers_536x144.png](http://www.radioparadise.com/graphics/support_speakers_536x144.png) admin HIER_NONE/- image/png
1452093312.003     80 111.222.333.444 TCP_REFRESH_UNMODIFIED/200 12069 GET [http://www.radioparadise.com/graphics/start_2.png?](http://www.radioparadise.com/graphics/start_2.png?) admin HIER_DIRECT/23.29.117.2 image/png
1452093312.006      0 111.222.333.444 TCP_HIT/200 496 GET [http://www.radioparadise.com/scripts/themes/base/images/ui-bg_glass_75_e6e6e6_1x400.png](http://www.radioparadise.com/scripts/themes/base/images/ui-bg_glass_75_e6e6e6_1x400.png) admin HIER_NONE/- image/png
1452093312.039      0 111.222.333.444 TCP_HIT/200 4768 GET [http://www.radioparadise.com/scripts/objectSwap.js](http://www.radioparadise.com/scripts/objectSwap.js) admin HIER_NONE/- application/javascript
1452093312.364    277 111.222.333.444 TCP_MISS/200 157300 GET [http://www.radioparadise.com/scripts/swf/world.swf?](http://www.radioparadise.com/scripts/swf/world.swf?) admin HIER_DIRECT/23.29.117.2 application/x-shockwave-flash
1452093312.418      0 111.222.333.444 TCP_HIT/200 1809 GET [http://www.radioparadise.com/favicon.ico](http://www.radioparadise.com/favicon.ico) admin HIER_NONE/- image/vnd.microsoft.icon
1452093312.902     40 111.222.333.444 TCP_MISS/200 14406 GET [http://www.radioparadise.com/xml/flash_countries_24.xml?](http://www.radioparadise.com/xml/flash_countries_24.xml?) admin HIER_DIRECT/23.29.117.2 text/xml
1452093313.420     41 111.222.333.444 TCP_MISS/200 379 GET [http://www.radioparadise.com/ajax_replace.php?](http://www.radioparadise.com/ajax_replace.php?) admin HIER_DIRECT/23.29.117.2 text/html
1452093314.759   5359 111.222.333.444 TCP_MISS/200 4043 CONNECT geo.mozilla.org:443 admin HIER_DIRECT/63.245.215.82 -
1452093314.766   6258 111.222.333.444 TCP_MISS/200 3884 CONNECT aus5.mozilla.org:443 admin HIER_DIRECT/63.245.213.48 -
1452093316.428     41 111.222.333.444 TCP_MISS/200 1566 GET [http://www.radioparadise.com/ajax_playlist_display.php?](http://www.radioparadise.com/ajax_playlist_display.php?) admin HIER_DIRECT/23.29.117.2 text/html
```

squid.con is setup standard...here are the only changes that I have made... I

```
squid.conf
##################################
##################################
auth_param basic program /etc/webmin/squid/squid-auth.pl /etc/webmin/squid/users
  acl ncsa_users proxy_auth REQUIRED
  http_access allow ncsa_users
```

---

### Post by Bucky Ball on 2016-01-06
*Thread closed.*

This says it all:

> Trying to create a proxy to allow me to listen to music in situations where it might be blocked.

If it's blocked, it's blocked for a reason. Please read this, from the forum Code of Conduct:

> We do not support circumventing TOS, EULA, etc here. Such threads will be closed and offending users will be penalised with infractions and warnings. 

---

