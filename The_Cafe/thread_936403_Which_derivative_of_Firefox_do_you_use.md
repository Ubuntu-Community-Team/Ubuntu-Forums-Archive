---
title: "Which derivative of Firefox do you use?"
date: 2008-10-02
forum: The Cafe
---

### Post by medic2000 on 2008-10-02
And why? Just wondering. Also this thread may cause us to switch our browser?:popcorn:

Don't rush to choose your browser. First read through the thread. I sense we will reveal so many thinks about Firefox and custom foxes.

---

### Post by Kingsley on 2008-10-02
I use Swiftfox because it loads up slightly faster on my laptop. I've also noticed fewer incidents of freezing on sites like Digg.

---

### Post by oldsoundguy on 2008-10-02
3.0.3 along with Flash RC 10 on 4 Linux machines and two XP machines.

Stable and it works.  PLUS the ability customize and to put "add ons" is a huge plus. The new "Foxmarks" add on made it even nicer as every machine now has the same bookmarks file!

---

### Post by oldsoundguy on 2008-10-02
And "browser speed" is subjective.  There are many things that can have an effect on the speed, from the browser itself and it's ram and processor usage to the speed of your connection to the amount of linked crud that the particular website has loaded onto their index page or further on in, to the TRAFFIC on that particular site to the actual HOST of the web site and their ability do actually "host".

---

### Post by medic2000 on 2008-10-02
Nowadays i use firefox. But this can change after this topic and voting.(swiftweasel and epiphany in mind)

---

### Post by bruce89 on 2008-10-02
Epiphany is not a derivative of Firefox. Trunk doesn't even use Gecko any more.

Anyway, it is very nice (bookmarks are a dream).

---

### Post by BobLand on 2008-10-02
With FireFox, I can't change account settings in Amazon or my ISP.  No problem with Swiftweasel.  

If I'm viewing an assortment of videos, FireFox vanishes.  Not so with SW.

Firefox lost most of my bookmarks when I upgraded to 3.0.  Once I get around to moving my bookmarks to SW I'll probably abandon FF.  Too much trouble.

bobland

---

### Post by medic2000 on 2008-10-02
> **bruce89 said:**
> Epiphany is not a derivative of Firefox. Trunk doesn't even use Gecko any more.

Anyway, it is very nice (bookmarks are a dream).

Yes i made a comment about that matter and why i added it too...

---

### Post by bruce89 on 2008-10-02
> **medic2000 said:**
> Yes i made a comment about that matter and why i added it too...

I noticed that a bit later.

---

### Post by utUtu on 2008-10-02
Flock is excellent!  Why is it not there?  Also, kazahakase should be there too.

---

### Post by medic2000 on 2008-10-02
> **bruce89 said:**
> I noticed that a bit later.

Not a problem;)

---

### Post by medic2000 on 2008-10-02
> **utUtu said:**
> Flock is excellent!  Why is it not there?  Also, kazahakase should be there too.

First I made this topic for the Firefox derivatives first and added Epiphany just for my curiosity(little selfishness here :D )

I have just heard about "flock" though i know and like kazehakase.

---

### Post by Frak on 2008-10-02
Firefox and Swiftweasel are good, but Swiftfox is... incredibly restrictive. "You may not distribute Swiftfox without permission". It's just a special compile script as well.

> 1. Swiftfox binaries are not distributed under the MPL 
   license and are not freely distributable.  Swiftfox 
   is licensed only to the user that downloads the 
   binary from getswiftfox.com and no distribution 
   to other parties is allowable under this license.  
   Download of any binary from getswiftfox.com 
   constitutes acceptance of these terms.


Here's the "oh so advanced" patch he made.

```
Index: browser/app/profile/firefox.js
===================================================================
RCS file: /cvsroot/mozilla/browser/app/profile/firefox.js,v
retrieving revision 1.239
diff -u -p -8 -r1.239 firefox.js
--- browser/app/profile/firefox.js	5 Dec 2007 08:30:07 -0000	1.239
+++ browser/app/profile/firefox.js	8 Dec 2007 19:38:13 -0000
@@ -283,17 +283,17 @@ pref("browser.tabs.tabMinWidth", 100);
 pref("browser.tabs.tabMaxWidth", 250);
 pref("browser.tabs.tabClipWidth", 140);
 
 // Where to show tab close buttons:
 // 0  on active tab only
 // 1  on all tabs until tabClipWidth is reached, then active tab only
 // 2  no close buttons at all
 // 3  at the end of the tabstrip
-pref("browser.tabs.closeButtons", 1);
+pref("browser.tabs.closeButtons", 0);
 
 // When tabs opened by links in other tabs via a combination of 
 // browser.link.open_newwindow being set to 3 and target="_blank" etc are
 // closed:
 // true   return to the tab that opened this tab (its owner)
 // false  return to the adjacent tab (old default)
 pref("browser.tabs.selectOwnerOnClose", true);
 
Index: modules/libpref/src/init/all.js
===================================================================
RCS file: /cvsroot/mozilla/modules/libpref/src/init/all.js,v
retrieving revision 3.712
diff -u -p -8 -r3.712 all.js
--- modules/libpref/src/init/all.js	5 Dec 2007 21:16:33 -0000	3.712
+++ modules/libpref/src/init/all.js	8 Dec 2007 19:38:15 -0000
@@ -159,17 +159,17 @@ pref("accessibility.typeaheadfind.casese
 pref("accessibility.typeaheadfind.linksonly", true);
 pref("accessibility.typeaheadfind.startlinksonly", false);
 pref("accessibility.typeaheadfind.timeout", 4000);
 pref("accessibility.typeaheadfind.enabletimeout", true);
 pref("accessibility.typeaheadfind.soundURL", "beep");
 pref("accessibility.typeaheadfind.enablesound", true);
 pref("accessibility.typeaheadfind.prefillwithselection", true);
 
-pref("browser.history_expire_days", 9);
+pref("browser.history_expire_days", 7);
 
 // loading and rendering of framesets and iframes
 pref("browser.frames.enabled", true);
 
 // form submission
 pref("browser.forms.submit.backwards_compatible", true);
 
 // xxxbsmedberg more toolkit prefs?
@@ -559,32 +559,32 @@ pref("network.http.use-cache", true);
 // HTTP traffic.  an empty value indicates the normal TCP/IP socket type.
 pref("network.http.default-socket-type", "");
 
 pref("network.http.keep-alive", true); // set it to false in case of problems
 pref("network.http.proxy.keep-alive", true);
 pref("network.http.keep-alive.timeout", 300);
 
 // limit the absolute number of http connections.
-pref("network.http.max-connections", 24);
+pref("network.http.max-connections", 32);
 
 // limit the absolute number of http connections that can be established per
 // host.  if a http proxy server is enabled, then the "server" is the proxy
 // server.  Otherwise, "server" is the http origin server.
 pref("network.http.max-connections-per-server", 8);
 
 // if network.http.keep-alive is true, and if NOT connecting via a proxy, then
 // a new connection will only be attempted if the number of active persistent
 // connections to the server is less then max-persistent-connections-per-server.
-pref("network.http.max-persistent-connections-per-server", 2);
+pref("network.http.max-persistent-connections-per-server", 4);
 
 // if network.http.keep-alive is true, and if connecting via a proxy, then a
 // new connection will only be attempted if the number of active persistent
 // connections to the proxy is less then max-persistent-connections-per-proxy.
-pref("network.http.max-persistent-connections-per-proxy", 4);
+pref("network.http.max-persistent-connections-per-proxy", 8);
 
 // amount of time (in seconds) to suspend pending requests, before spawning a
 // new connection, once the limit on the number of persistent connections per
 // host has been reached.  however, a new connection will not be created if
 // max-connections or max-connections-per-server has also been reached.
 pref("network.http.request.max-start-delay", 10);
 
 // Headers
@@ -597,21 +597,21 @@ pref("network.http.sendSecureXSiteReferr
 
 // Maximum number of consecutive redirects before aborting.
 pref("network.http.redirection-limit", 20);
 
 // Enable http compression: comment this out in case of problems with 1.1
 // NOTE: support for "compress" has been disabled per bug 196406.
 pref("network.http.accept-encoding" ,"gzip,deflate");
 
-pref("network.http.pipelining"      , false);
+pref("network.http.pipelining"      , true);
 pref("network.http.pipelining.ssl"  , true); // enable pipelining over SSL
-pref("network.http.proxy.pipelining", false);
+pref("network.http.proxy.pipelining", true);
 
 // Max number of requests in the pipeline
-pref("network.http.pipelining.maxrequests" , 4);
+pref("network.http.pipelining.maxrequests" , 8);
 
 // </http>
 
 // If false, remote JAR files that are served with a content type other than
 // application/java-archive or application/x-jar will not be opened
 // by the jar channel.
 pref("network.jar.open-unsafe-types", false);
 
@@ -686,17 +686,17 @@ pref("network.IDN.whitelist.xn--zckzah",
 pref("network.IDN.blacklist_chars", "\u0020\u00A0\u00BC\u00BD\u01C3\u0337\u0338\u05C3\u05F4\u06D4\u0702\u115F\u1160\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200A\u200B\u2024\u2027\u2028\u2029\u202F\u2039\u203A\u2044\u205F\u2154\u2155\u2156\u2159\u215A\u215B\u215F\u2215\u23AE\u29F6\u29F8\u2AFB\u2AFD\u2FF0\u2FF1\u2FF2\u2FF3\u2FF4\u2FF5\u2FF6\u2FF7\u2FF8\u2FF9\u2FFA\u2FFB\u3000\u3002\u3014\u3015\u3033\u3164\u321D\u321E\u33AE\u33AF\u33C6\u33DF\uFE14\uFE15\uFE3F\uFE5D\uFE5E\uFEFF\uFF0E\uFF0F\uFF61\uFFA0\uFFF9\uFFFA\uFFFB\uFFFC\uFFFD");
 
 // This preference specifies a list of domains for which DNS lookups will be
 // IPv4 only. Works around broken DNS servers which can't handle IPv6 lookups
 // and/or allows the user to disable IPv6 on a per-domain basis. See bug 68796.
 pref("network.dns.ipv4OnlyDomains", "");
 
 // This preference can be used to turn off IPv6 name lookups. See bug 68796.
-pref("network.dns.disableIPv6", false);
+pref("network.dns.disableIPv6", true);
 
 // This preference controls whether or not URLs with UTF-8 characters are
 // escaped.  Set this preference to TRUE for strict RFC2396 conformance.
 pref("network.standard-url.escape-utf8", true);
 
 // This preference controls whether or not URLs are always encoded and sent as
 // UTF-8.
 pref("network.standard-url.encode-utf8", true);
@@ -2094,17 +2094,17 @@ pref("network.hosts.smtp_server", "local
 pref("network.hosts.pop_server", "pop");
 pref("network.protocol-handler.warn-external.file", false);
 pref("layout.css.dpi", -1); // max(96dpi, System setting)
 pref("browser.drag_out_of_frame_style", 1);
 pref("editor.singleLine.pasteNewlines", 0);
 
 // Middle-mouse handling
 pref("middlemouse.paste", true);
-pref("middlemouse.contentLoadURL", true);
+pref("middlemouse.contentLoadURL", false);
 pref("middlemouse.openNewWindow", true);
 pref("middlemouse.scrollbarPosition", true);
 
 // Clipboard behavior
 pref("clipboard.autocopy", true);
 
 pref("browser.urlbar.clickSelectsAll", false);
 

```

It's just setting some defaults in about:config. Some of those affect usability, and some "theoretically" affect downloading speeds. While some such as "Allow Pipelining over SSL", which is set to false in regular firefox, true in swiftfox , affect security. You're more likely to get information stolen with pipelining on SSL then if you had pipelining disabled.

It's just too much to deal with. It's easier just to patch it yourself, change some settings back, and compile it yourself.


Oh, I do have to mention, he uses some special compiler flags:
```
-O3 -march=native (or pentium4 core2duo, athlonxp, etc) -D_FORTIFY_SOURCE=2
```
-O3 uses the highest level of optimization, though, if your processor doesn't have many registers, you will have a heavy hit in terms of performance. (Firefox uses -Os, which is no optimization, but less chance of unstable-ness)

-march=native uses the instruction sets for your processor type. For example, I have a pentium 4, so pentium4 would be used, which includes SSE1, SSE2, MMX. Though, since mine is a prescott, it would use prescott and also use the SSE3 instruction set.

-D_FORTIFY_SOURCE=2 protects against buffer overflow attacks. Gentoo users, if you are really afraid of buffer overflow attacks, you should add this to your use flags I guess.

All this is, is trivial changes. No actual changes to the source code, as is the case with Swiftweasel.

/informative rant

If you want to know why I posted this, the guy that makes the oh-so-simple patch for swiftfox keeps deleting my threads on why he proprietizes his builds.

---

### Post by SomeGuyDude on 2008-10-02
I just switched to Swiftweasel based on that post!

---

### Post by Frak on 2008-10-02
> **SomeGuyDude said:**
> I just switched to Swiftweasel based on that post!
Then I have done my job (the right way) :)

---

### Post by medic2000 on 2008-10-02
> **Frak said:**
> Firefox and Swiftweasel are good, but Swiftfox is... incredibly restrictive. "You may not distribute Swiftfox without permission". It's just a special compile script as well.



Here's the "oh so advanced" patch he made.

```
Index: browser/app/profile/firefox.js
===================================================================
RCS file: /cvsroot/mozilla/browser/app/profile/firefox.js,v
retrieving revision 1.239
diff -u -p -8 -r1.239 firefox.js
--- browser/app/profile/firefox.js	5 Dec 2007 08:30:07 -0000	1.239
+++ browser/app/profile/firefox.js	8 Dec 2007 19:38:13 -0000
@@ -283,17 +283,17 @@ pref("browser.tabs.tabMinWidth", 100);
 pref("browser.tabs.tabMaxWidth", 250);
 pref("browser.tabs.tabClipWidth", 140);
 
 // Where to show tab close buttons:
 // 0  on active tab only
 // 1  on all tabs until tabClipWidth is reached, then active tab only
 // 2  no close buttons at all
 // 3  at the end of the tabstrip
-pref("browser.tabs.closeButtons", 1);
+pref("browser.tabs.closeButtons", 0);
 
 // When tabs opened by links in other tabs via a combination of 
 // browser.link.open_newwindow being set to 3 and target="_blank" etc are
 // closed:
 // true   return to the tab that opened this tab (its owner)
 // false  return to the adjacent tab (old default)
 pref("browser.tabs.selectOwnerOnClose", true);
 
Index: modules/libpref/src/init/all.js
===================================================================
RCS file: /cvsroot/mozilla/modules/libpref/src/init/all.js,v
retrieving revision 3.712
diff -u -p -8 -r3.712 all.js
--- modules/libpref/src/init/all.js	5 Dec 2007 21:16:33 -0000	3.712
+++ modules/libpref/src/init/all.js	8 Dec 2007 19:38:15 -0000
@@ -159,17 +159,17 @@ pref("accessibility.typeaheadfind.casese
 pref("accessibility.typeaheadfind.linksonly", true);
 pref("accessibility.typeaheadfind.startlinksonly", false);
 pref("accessibility.typeaheadfind.timeout", 4000);
 pref("accessibility.typeaheadfind.enabletimeout", true);
 pref("accessibility.typeaheadfind.soundURL", "beep");
 pref("accessibility.typeaheadfind.enablesound", true);
 pref("accessibility.typeaheadfind.prefillwithselection", true);
 
-pref("browser.history_expire_days", 9);
+pref("browser.history_expire_days", 7);
 
 // loading and rendering of framesets and iframes
 pref("browser.frames.enabled", true);
 
 // form submission
 pref("browser.forms.submit.backwards_compatible", true);
 
 // xxxbsmedberg more toolkit prefs?
@@ -559,32 +559,32 @@ pref("network.http.use-cache", true);
 // HTTP traffic.  an empty value indicates the normal TCP/IP socket type.
 pref("network.http.default-socket-type", "");
 
 pref("network.http.keep-alive", true); // set it to false in case of problems
 pref("network.http.proxy.keep-alive", true);
 pref("network.http.keep-alive.timeout", 300);
 
 // limit the absolute number of http connections.
-pref("network.http.max-connections", 24);
+pref("network.http.max-connections", 32);
 
 // limit the absolute number of http connections that can be established per
 // host.  if a http proxy server is enabled, then the "server" is the proxy
 // server.  Otherwise, "server" is the http origin server.
 pref("network.http.max-connections-per-server", 8);
 
 // if network.http.keep-alive is true, and if NOT connecting via a proxy, then
 // a new connection will only be attempted if the number of active persistent
 // connections to the server is less then max-persistent-connections-per-server.
-pref("network.http.max-persistent-connections-per-server", 2);
+pref("network.http.max-persistent-connections-per-server", 4);
 
 // if network.http.keep-alive is true, and if connecting via a proxy, then a
 // new connection will only be attempted if the number of active persistent
 // connections to the proxy is less then max-persistent-connections-per-proxy.
-pref("network.http.max-persistent-connections-per-proxy", 4);
+pref("network.http.max-persistent-connections-per-proxy", 8);
 
 // amount of time (in seconds) to suspend pending requests, before spawning a
 // new connection, once the limit on the number of persistent connections per
 // host has been reached.  however, a new connection will not be created if
 // max-connections or max-connections-per-server has also been reached.
 pref("network.http.request.max-start-delay", 10);
 
 // Headers
@@ -597,21 +597,21 @@ pref("network.http.sendSecureXSiteReferr
 
 // Maximum number of consecutive redirects before aborting.
 pref("network.http.redirection-limit", 20);
 
 // Enable http compression: comment this out in case of problems with 1.1
 // NOTE: support for "compress" has been disabled per bug 196406.
 pref("network.http.accept-encoding" ,"gzip,deflate");
 
-pref("network.http.pipelining"      , false);
+pref("network.http.pipelining"      , true);
 pref("network.http.pipelining.ssl"  , true); // enable pipelining over SSL
-pref("network.http.proxy.pipelining", false);
+pref("network.http.proxy.pipelining", true);
 
 // Max number of requests in the pipeline
-pref("network.http.pipelining.maxrequests" , 4);
+pref("network.http.pipelining.maxrequests" , 8);
 
 // </http>
 
 // If false, remote JAR files that are served with a content type other than
 // application/java-archive or application/x-jar will not be opened
 // by the jar channel.
 pref("network.jar.open-unsafe-types", false);
 
@@ -686,17 +686,17 @@ pref("network.IDN.whitelist.xn--zckzah",
 pref("network.IDN.blacklist_chars", "\u0020\u00A0\u00BC\u00BD\u01C3\u0337\u0338\u05C3\u05F4\u06D4\u0702\u115F\u1160\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200A\u200B\u2024\u2027\u2028\u2029\u202F\u2039\u203A\u2044\u205F\u2154\u2155\u2156\u2159\u215A\u215B\u215F\u2215\u23AE\u29F6\u29F8\u2AFB\u2AFD\u2FF0\u2FF1\u2FF2\u2FF3\u2FF4\u2FF5\u2FF6\u2FF7\u2FF8\u2FF9\u2FFA\u2FFB\u3000\u3002\u3014\u3015\u3033\u3164\u321D\u321E\u33AE\u33AF\u33C6\u33DF\uFE14\uFE15\uFE3F\uFE5D\uFE5E\uFEFF\uFF0E\uFF0F\uFF61\uFFA0\uFFF9\uFFFA\uFFFB\uFFFC\uFFFD");
 
 // This preference specifies a list of domains for which DNS lookups will be
 // IPv4 only. Works around broken DNS servers which can't handle IPv6 lookups
 // and/or allows the user to disable IPv6 on a per-domain basis. See bug 68796.
 pref("network.dns.ipv4OnlyDomains", "");
 
 // This preference can be used to turn off IPv6 name lookups. See bug 68796.
-pref("network.dns.disableIPv6", false);
+pref("network.dns.disableIPv6", true);
 
 // This preference controls whether or not URLs with UTF-8 characters are
 // escaped.  Set this preference to TRUE for strict RFC2396 conformance.
 pref("network.standard-url.escape-utf8", true);
 
 // This preference controls whether or not URLs are always encoded and sent as
 // UTF-8.
 pref("network.standard-url.encode-utf8", true);
@@ -2094,17 +2094,17 @@ pref("network.hosts.smtp_server", "local
 pref("network.hosts.pop_server", "pop");
 pref("network.protocol-handler.warn-external.file", false);
 pref("layout.css.dpi", -1); // max(96dpi, System setting)
 pref("browser.drag_out_of_frame_style", 1);
 pref("editor.singleLine.pasteNewlines", 0);
 
 // Middle-mouse handling
 pref("middlemouse.paste", true);
-pref("middlemouse.contentLoadURL", true);
+pref("middlemouse.contentLoadURL", false);
 pref("middlemouse.openNewWindow", true);
 pref("middlemouse.scrollbarPosition", true);
 
 // Clipboard behavior
 pref("clipboard.autocopy", true);
 
 pref("browser.urlbar.clickSelectsAll", false);
 

```

It's just setting some defaults in about:config. Some of those affect usability, and some "theoretically" affect downloading speeds. While some such as "Allow Pipelining over SSL", which is set to false in regular firefox, true in swiftfox , affect security. You're more likely to get information stolen with pipelining on SSL then if you had pipelining disabled.

It's just too much to deal with. It's easier just to patch it yourself, change some settings back, and compile it yourself.


Oh, I do have to mention, he uses some special compiler flags:
```
-O3 -march=native (or pentium4 core2duo, athlonxp, etc) -D_FORTIFY_SOURCE=2
```
-O3 uses the highest level of optimization, though, if your processor doesn't have many registers, you will have a heavy hit in terms of performance. (Firefox uses -Os, which is no optimization, but less chance of unstable-ness)

-march=native uses the instruction sets for your processor type. For example, I have a pentium 4, so pentium4 would be used, which includes SSE1, SSE2, MMX. Though, since mine is a prescott, it would use prescott and also use the SSE3 instruction set.

-D_FORTIFY_SOURCE=2 protects against buffer overflow attacks. Gentoo users, if you are really afraid of buffer overflow attacks, you should add this to your use flags I guess.

All this is, is trivial changes. No actual changes to the source code, as is the case with Swiftweasel.

/informative rant

If you want to know why I posted this, the guy that makes the oh-so-simple patch for swiftfox keeps deleting my threads on why he proprietizes his builds.

Thanks for this useful information! I have used swiftfox for a while and i didnt notice a quite speed improvement.And now i see this guy restricts even that simple code i disliked his build.

---

### Post by medic2000 on 2008-10-02
And what about the Swiftweasel? Is it worth to use an unofficial built? 
Hey Swiftweasel guys tell us about your testimonials.

---

### Post by perlluver on 2008-10-02
I use Firefox 3.0.3, but if Delicious bookmarks worked in Opera I would probably use it.

---

### Post by ArtF10 on 2008-10-02
Firefox.....nice and light.  Don't use ANY extensions/addons.  Why?  Cause it came as default with Ubuntu.

---

### Post by Frak on 2008-10-02
> **medic2000 said:**
> And what about the Swiftweasel? Is it worth to use an unofficial built? 
Hey Swiftweasel guys tell us about your testimonials.
I personally like Swiftweasel, and for the speed necessarily. I like the default theme + the useful added extensions (such as XForms).

I think it's worth it, plus, they use -O2 instead of -O3, so for people like me who have processors without a high number of registers, it doesn't have a negative impact.

---

### Post by danbuter on 2008-10-02
I use Firefox.

---

### Post by crimesaucer on 2008-10-02
I like this optimized build of Firefox from the Arch AUR: [http://aur.archlinux.org/packages.php?ID=18090](http://aur.archlinux.org/packages.php?ID=18090)


I build it from source using pacbuilder so it uses my custom CFLAGS, CXXFLAS, and MAKEFLAGS from my /etc/makepkg.conf.


It feels more stable than Swiftweasel (Athlon64 and K8 ), plus it uses the real Firefox theme and branding.


These are my CFLAGS/CXXFLAGS/MAKEFLAGS for my AMD Turion64x2 TL-60:

```

CFLAGS="-march=athlon64 -msse3 -O2 -pipe"
CXXFLAGS="-march=athlon64 -msse3 -O2 -pipe"
#-- Make Flags: change this for DistCC/SMP systems
MAKEFLAGS="-j3"

```

---

### Post by Frak on 2008-10-02
> **crimesaucer said:**
> I like this optimized build of Firefox from the Arch AUR: [http://aur.archlinux.org/packages.php?ID=18090](http://aur.archlinux.org/packages.php?ID=18090)


I build it from source using pacbuilder so it uses my custom CFLAGS, CXXFLAS, and MAKEFLAGS from my /etc/makepkg.conf.


It feels more stable than Swiftweasel (Athlon64 and K8 ), plus it uses the real Firefox theme and branding.
I have to agree, I <3 pacbuilder. I spammed the guy who made it with thanks. This is coming from a guy who used gentoo since way back, but switched to arch.

---

### Post by crimesaucer on 2008-10-02
> **Frak said:**
> I have to agree, I <3 pacbuilder. I spammed the guy who made it with thanks. This is coming from a guy who used gentoo since way back, but switched to arch.

I just recently found pacbuilder. 


I wanted to install Gentoo so I could build my whole system from source, I followed every step of a stage3 install from the AMD64 handbook, I think I did everything correctly, and when I finished the day long install process, the grub menu didn't boot into any of my partitions (vista included), and I had to do another fresh install of Arch just to fix the problem.


So, upset that I didn't get a chance to use Gentoo and build my entire system from source using custom flags, I was lucky to find the pacbuilder thread in the Arch forums.


Now I have a complete Archlinux system built almost entirely from source using all of my custom flags..... and if I run into an app or a dependency that I need that won't compile correctly, I can just use regular pacman to install the x86_64 binary and continue the build from source.


(I also use a custom AMD64 kernel with the zen2 patch and all the same flags from above.)

---

### Post by Frak on 2008-10-02
> **crimesaucer said:**
> I just recently found pacbuilder. 


I wanted to install Gentoo so I could build my whole system from source, I followed every step of a stage3 install from the AMD64 handbook, I think I did everything correctly, and when I finished the day long install process, the grub menu didn't boot into any of my partitions (vista included), and I had to do another fresh install of Arch just to fix the problem.


So, upset that I didn't get a chance to use Gentoo and build my entire system from source using custom flags, I was lucky to find the pacbuilder thread in the Arch forums.


Now I have a complete Archlinux system built almost entirely from source using all of my custom flags..... and if I run into an app or a dependency that I need that won't compile correctly, I can just use regular pacman to install the x86_64 binary and continue the build from source.
Arch is now Gentoo + binsource in a handy little package now I guess :)

---

### Post by crimesaucer on 2008-10-02
> **Frak said:**
> Arch is now Gentoo + binsource in a handy little package now I guess :)

Yes, I even have the zen2 kernel patched and using all AMD64 settings, zen tunables, nice settings, and all of my custom flags.


Everything feels very fast.



Oh yeah, I guess my vote is other.... or regular Firefox?

---

### Post by Naiki Muliaina on 2008-10-02
I use Flock (the social browser). Pretty sure its a firefox derivative but no option on your list :)

---

### Post by kk0sse54 on 2008-10-02
> **Naiki Muliaina said:**
> I use Flock (the social browser). Pretty sure its a firefox derivative but no option on your list :)

Yup it's a derivative alright and I used it for a while but it seems slower than the original. I was using FF 3 although as of the last few days I've been using Opera.

---

### Post by schauerlich on 2008-10-02
I use the velocity.

---

### Post by tgrisier on 2008-10-02
I'm using Flock here as well.  And when I'm not using Flock I use Firefox 3.0.3.

---

### Post by OutOfReach on 2008-10-02
I used to use Swiftweasel, but now I use Opera.

---

### Post by Sky Pixie on 2008-10-02
[Infomercial]

I tried the Ubuntu-packaged Firefox and straight-from-Mozilla Firefox when I first installed Kubuntu.  Both behaved slowly.  I tried Swiftweasel and was instantly hooked.  Swiftweasel loaded pages faster than Firefox!  Now I suggest Swiftweasel to all my Linux friends.

[/Infomercial]

---

### Post by crimesaucer on 2008-10-02
My experience of the list above:

Epiphany ----- I think it's the fastest. As for looks, even though it uses the native gtk and icons, it still seems to look worse than Firefox..... I don't like the way they have the bookmarks (maybe I'm not used to it), I don't mind using greasemonkey userscripts but a couple of extra plug-ins like google thumb images would be nice. The few add-ons like ad-block are good.... I HATE HOW IT OPENS NEW WINDOWS FROM LINKS..... and I also had spell checker issues and an about:config that would break and crash when I tried to fix the spell-checker....


Firefox-Optimized ----- Feels just as fast as the Swiftweasel/Swiftfox builds, has the Firefox branding/icon, so far it has felt more stable than the Swiftweasel/Swiftfox/Minefield nightly builds.... exactly as stable as the Arch Minefield and regular Firefox.


Swiftfox ----- was very fast on my Celeron M chip, but wouldn't install on my AMD Turion64x2 TL-60.......


Swiftweasel Athlon64 ----- fast, but sort of funny feeling, sort of a pain on updates, and I had to hack the /chrome/classic.jar to use my native Linux gtk/icon theme and not that ugly Kempleton theme.


Swiftweasel k8 ------ same as above.


Minefield nightly builds from the Firefox nightly page ----- can be very good, can be very buggy..... fast, and always the new stuff.


Minefield from Arch repo's ----- solid, fast, and stable like regular Firefox..... boring icon..... basically the same as below.


Firefox (regular) ----- good old regular Firefox, usually feels the most stable, while only being a bit slower than the 2 Swift builds, and noticeably slower than Epiphany.



#######################################


When I tried Opera last year it was very fast, but I didn't like the issues with some pages not showing correctly..... other things made me not like it compared to Firefox..... I can't remember but I think it was java and a media player plug-in..... things I solved, but felt was more of a hassle than firefox..... and the update failed..... so I never tried it again. Plus, I don't like the themes/icons/browser lay-out.



..... but one of the most important browsers I've used is "Links" because it can connect you to the Internet if you break something and can only use the tty console.

---

### Post by zmjjmz on 2008-10-02
Firefox, because NoScript and Ubiquity are awesomeful.
I _have_ (but don't use much) Flock, Kazehakase, and I unsuccessfully tried to compile Skipstone.

---

### Post by crimesaucer on 2008-10-04
Just my luck to brag about the Firefox-optimized package from the Arch AUR right before it breaks becasue of a xulrunner upgrade.....


This sucks. I did a pacbuilder -Su (same as pacman -Su) last night and I saw one of the packages was xulrunner--1.9.0.3-1...... and it replaced or messed with the xulrunner-devel-1.9.0.1 that had been used by the Firefox-optimized package.


I guess I can wait for a few days until they update and fix it to use the new xulrunner......


So while waiting, I have tried the web browser Midori and it is far from complete..... it might be nice one of these days.


...... and I am curently giving Opera another try with the 9.60-dev build from the Arch AUR..... so far it is VERY FAST, maybe as fast or faster than Epiphany, but I still don't like the layout as much, and I still need to figure out how to get OpenJDK "icedtea" Java64bit plugin to work..... 64bit Flash seemed to work out the box using my 64bit nspluginwrapper for flash form my mozilla folder..... maybe I can symlink the java somehow.

---

### Post by homemadejam on 2008-10-04
I use Opera a fair bit, I quite like that. Its a shame that Opera didn't come with all the extra plugins that Firefox does, otherwise I'd never use Firefox..

Jam

---

### Post by crimesaucer on 2008-10-04
Now I remember why I gave up on opera last year....


To find the actual instructions for certain things like userscripts and plugins is not easy..... once you find them, they are ancient and i386 specific.....


I followed the java instructions but used amd instead of i386, and opera was linked it to my GCJ Web Browser Plugin (using IcedTea) 1.3 from my firefox folder.... I also made sure that my mozplugger was linked, as well as my nspluginwrapper for 64bit flash....


Flash works (pretty good even), but java openjdk and my totem-xine don't work at all..... neither does the userscript for google thumbnail images.... so that right there just ruins the Internet. No google thumbs for searching? no streaming movies from my favorite sites (Surfline.com), no java streaming.....


Maybe I'm being lazy about this, but I think they would have made all of this easier for a linux user.... it's the exact same way as it was almost 2 years ago.

---

### Post by doorknob60 on 2008-10-04
I put Minefield, even though I belive that was FF2's codename, FF3's is Gran Paradiso. It's simply Firefox without the branding, I wouldn't really call it a derivative. I use Arch, and the firefox package doesn't have the trademarked branding. I don't use it much though, because I use Konqueror for most things, and the things that don't work, I end up using the mozilla i686 binary Firefox (Better Flash support and Java plugin), but yeah.

---

### Post by Corfy on 2008-10-05
I use Firefox. It seems to have the best support and the most extensions.

I'm surprised your poll doesn't mention SeaMonkey. Granted, I'm not sure it is technically considered a derivative of Firefox, but both Firefox and SeaMonkey are derivatives of the Mozilla Suite.

I do use SeaMonkey occasionally. One website I regularly visit has a real problem with Flashblock, which I have installed in Firefox. Even telling Flashblock to allow all flash on that one site doesn't fix the problem, so I use SeaMonkey for that site.

---

### Post by cardinals_fan on 2008-10-05
> **crimesaucer said:**
> Now I remember why I gave up on opera last year....


To find the actual instructions for certain things like userscripts and plugins is not easy..... once you find them, they are ancient and i386 specific.....


I followed the java instructions but used amd instead of i386, and opera was linked it to my GCJ Web Browser Plugin (using IcedTea) 1.3 from my firefox folder.... I also made sure that my mozplugger was linked, as well as my nspluginwrapper for 64bit flash....


Flash works (pretty good even), but java openjdk and my totem-xine don't work at all..... neither does the userscript for google thumbnail images.... so that right there just ruins the Internet. No google thumbs for searching? no streaming movies from my favorite sites (Surfline.com), no java streaming.....


Maybe I'm being lazy about this, but I think they would have made all of this easier for a linux user.... it's the exact same way as it was almost 2 years ago.
Opera detected all my Firefox plugins (including Java) out of the box.  Go figure.

---

### Post by crimesaucer on 2008-10-05
> **cardinals_fan said:**
> Opera detected all my Firefox plugins (including Java) out of the box.  Go figure.

On the plugin page, it lists all of my plugins.... mozplugger, icedtea.... but neither of them actually work.


I am using the 9.60 beta, so maybe that has something to do with it.

---

### Post by Scruffynerf on 2008-10-06
Originally a standard Firefox, have a lot of extensions though.

---

