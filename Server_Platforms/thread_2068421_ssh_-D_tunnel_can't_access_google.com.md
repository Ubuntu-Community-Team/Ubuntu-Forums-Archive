---
title: "ssh -D tunnel can't access google.com"
date: 2012-10-09
forum: Server Platforms
---

### Post by ame177674 on 2012-10-09
Hi,I don't know where to post this question so I post here,if I make a mistake I will apologize.

I have a server:Burst.net Xen #1 vps,with ubuntu 11.10 kernel 3.0.0-12-generic-pae.

my two clients is : Asus notebook windows7 64-bit,Asus eeepc Xubuntu 12.04.1

On Xubuntu I simply use ssh -D,On windows I use Bitvise ssh cilent,both with firefox 15.0+autoproxy,I also test it on chrome+proxy switchysharp,but I can access to all of the sites except google.com,and youtube,and all websites which belongs to google. this weird :<

But,if I found thier IPs,I can access them through IP. I used socks v5 proxy.It resolve dns on the server! So I log in the server,/etc/resolv.conf is already set to 8.8.8.8. I excute  "host google.com"/"dig google.com"/"ping google.com".All of them return the correct reports.(from 8.8.8.8,right IPs).

But if I curl google.com,got nothing.If I curl google's IP,got its homepage.then I check /etc/hosts /etc/hosts.deny,nothing,they are alright. I have a ufw firewall default in policy to "deny",but I think it no effect.

Anybody help me? this is really wired.I even want to give up and buy a new one.but I don't have that money. :<

---

### Post by Lars Noodén on 2012-10-09
If you are using Firefox, you can set [font=Courier New]network.proxy.socks_remote_dns[/font] = true

That will make sure that DNS requests get passed via the SOCKS proxy instead of being resolved locally.

/etc/hosts.allow and hosts.deny are for incoming connections only, not outgoing.

---

### Post by ame177674 on 2012-10-09
> **Lars Noodén said:**
> If you are using Firefox, you can set [font=Courier New]network.proxy.socks_remote_dns[/font] = true

That will make sure that DNS requests get passed via the SOCKS proxy instead of being resolved locally.

/etc/hosts.allow and hosts.deny are for incoming connections only, not outgoing.

the problem is not firefox,I can use other ssh account to access them, so I make sure dns is resolved remotely (socks v5)

the things which really puzzled me is "host/dig/ping" working but curl/links don't work,even I'm not use the ssh tunnel

---

### Post by markbl on 2012-10-09
> **ame177674 said:**
> 
the things which really puzzled me is "host/dig/ping" working but curl/links don't work,even I'm not use the ssh tunnel
So the title of this thread is completely wrong is it not? You are saying the problem is completely on your server and ssh (and the dynamic proxy) has nothing to do with it?

---

### Post by ame177674 on 2012-10-09
> **markbl said:**
> So the title of this thread is completely wrong is it not? You are saying the problem is completely on your server and ssh (and the dynamic proxy) has nothing to do with it?

sorry,maybe wrong.But I do not know how to describe it."host/dig/ping work but curl not work"? Then nobody knows what I'm saying.My English is not good,I'm not native speaker,sorry :( (I ask this question in our language form but no one can answer it)

---

### Post by Lars Noodén on 2012-10-09
Can you try rephrasing your question again?  Which machine are you running curl on that it does not work and what is the target of curl then?

---

### Post by ame177674 on 2012-10-10
> **Lars Noodén said:**
> Can you try rephrasing your question again?  Which machine are you running curl on that it does not work and what is the target of curl then?

Yeah:p my Server is Ubuntu 11.10 with 3.0.0-12-generic-pae kernel,Burst.net Xen #1 VPS.

host -v google.com

```
Trying "google.com"
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 51599
;; flags: qr rd ra; QUERY: 1, ANSWER: 11, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.                    IN      A

;; ANSWER SECTION:
google.com.             173     IN      A       74.125.225.166
google.com.             173     IN      A       74.125.225.168
google.com.             173     IN      A       74.125.225.161
google.com.             173     IN      A       74.125.225.160
google.com.             173     IN      A       74.125.225.163
google.com.             173     IN      A       74.125.225.174
google.com.             173     IN      A       74.125.225.162
google.com.             173     IN      A       74.125.225.165
google.com.             173     IN      A       74.125.225.167
google.com.             173     IN      A       74.125.225.169
google.com.             173     IN      A       74.125.225.164

Received 204 bytes from 8.8.8.8#53 in 55 ms
Trying "google.com"
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 10784
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.                    IN      AAAA

;; ANSWER SECTION:
google.com.             173     IN      AAAA    2607:f8b0:400f:800::1000

Received 56 bytes from 8.8.8.8#53 in 28 ms
Trying "google.com"
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 62474
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.                    IN      MX

;; ANSWER SECTION:
google.com.             600     IN      MX      30 alt2.aspmx.l.google.com.
google.com.             600     IN      MX      50 alt4.aspmx.l.google.com.
google.com.             600     IN      MX      40 alt3.aspmx.l.google.com.
google.com.             600     IN      MX      20 alt1.aspmx.l.google.com.
google.com.             600     IN      MX      10 aspmx.l.google.com.

Received 136 bytes from 8.8.8.8#53 in 38 ms

```

ping google.com

```
PING google.com (74.125.225.166) 56(84) bytes of data.
64 bytes from den03s05-in-f6.1e100.net (74.125.225.166): icmp_req=1 ttl=56 time=26.0 ms
64 bytes from den03s05-in-f6.1e100.net (74.125.225.166): icmp_req=2 ttl=56 time=26.1 ms
64 bytes from den03s05-in-f6.1e100.net (74.125.225.166): icmp_req=3 ttl=56 time=26.1 ms
64 bytes from den03s05-in-f6.1e100.net (74.125.225.166): icmp_req=4 ttl=56 time=27.5 ms
64 bytes from den03s05-in-f6.1e100.net (74.125.225.166): icmp_req=5 ttl=56 time=27.6 ms
64 bytes from den03s05-in-f6.1e100.net (74.125.225.166): icmp_req=6 ttl=56 time=26.1 ms
64 bytes from den03s05-in-f6.1e100.net (74.125.225.166): icmp_req=7 ttl=56 time=26.1 ms
^C
--- google.com ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6008ms
rtt min/avg/max/mdev = 26.069/26.547/27.637/0.673 ms
```

curl google.com/curl [www.google.com](www.google.com)

```
nothing output...
```

But curl 74.125.225.166

```
<!doctype html><html itemscope="itemscope" itemtype="http://schema.org/WebPage"><head><meta itemprop="image" content="/images/google_favicon_128.png"><title>Google</title><script>window.google={kEI:"-fp0UMTqHI7nqAGezIHQBg",getEI:function(a){var b;while(a&&!(a.getAttribute&&(b=a.getAttribute("eid"))))a=a.parentNode;return b||google.kEI},https:function(){return window.location.protocol=="https:"},kEXPI:"25657,39523,39976,4000018,4000116,4000354,4000472,4000553,4000624,4000648,4000742,4000833,4000879,4000955,4001132,4001145,4001188,4001192,4001267,4001282,4001290,4001449",kCSI:{e:"25657,39523,39976,4000018,4000116,4000354,4000472,4000553,4000624,4000648,4000742,4000833,4000879,4000955,4001132,4001145,4001188,4001192,4001267,4001282,4001290,4001449",ei:"-fp0UMTqHI7nqAGezIHQBg"},authuser:0,
ml:function(){},kHL:"en",time:function(){return(new Date).getTime()},log:function(a,b,c,e){var d=new Image,h=google,i=h.lc,f=h.li,j="";d.onerror=(d.onload=(d.onabort=function(){delete i[f]}));i[f]=d;if(!c&&b.search("&ei=")==-1)j="&ei="+google.getEI(e);var g=c||"/gen_204?atyp=i&ct="+a+"&cad="+b+j+"&zx="+google.time();
var k=/^http:/i;if(k.test(g)&&google.https()){google.ml(new Error("GLMM"),false,{src:g});delete i[f];return}d.src=g;h.li=f+1},lc:[],li:0,Toolbelt:{},y:{},x:function(a,b){google.y[a.id]=[a,b];return false}};

window.google.sn="webhp";window.google.timers={};window.google.startTick=function(a,b){window.google.timers[a]={t:{start:(new Date).getTime()},bfr:!(!b)}};window.google.tick=function(a,b,c){if(!window.google.timers[a])google.startTick(a);window.google.timers[a].t[b]=c||(new Date).getTime()};google.startTick("load",true);try{}catch(u){}
var _gjwl=location;function _gjuc(){var e=_gjwl.href.indexOf("#");if(e>=0){var a=_gjwl.href.substring(e);if(a.indexOf("&q=")>0||a.indexOf("#q=")>=0){a=a.substring(1);if(a.indexOf("#")==-1){for(var c=0;c<a.length;){var d=c;if(a.charAt(d)=="&")++d;var b=a.indexOf("&",d);if(b==-1)b=a.length;var f=a.substring(d,b);if(f.indexOf("fp=")==0){a=a.substring(0,c)+a.substring(b,a.length);b=c}else if(f=="cad=h")return 0;c=b}_gjwl.href="/search?"+a+"&cad=h";return 1}}}return 0}function _gjp(){!(window._gjwl.hash&&
window._gjuc())&&setTimeout(_gjp,500)};
window._gjp&&_gjp();</script><style>#gbar,#guser{font-size:13px;padding-top:1px !important;}#gbar{height:22px}#guser{padding-bottom:7px !important;text-align:right}.gbh,.gbd{border-top:1px solid #c9d7f1;font-size:1px}.gbh{height:0;position:absolute;top:24px;width:100%}@media all{.gb1{height:22;margin-right:.5em;vertical-align:top}#gbar{float:left}}a.gb1,a.gb4{text-decoration:underline !important}a.gb1,a.gb4{color:#00c !important}</style><style id="gstyle">body{margin:0;overflow-y:scroll}#gog{padding:3px 8px 0}td{line-height:.8em}.gac_m td{line-height:17px}form{margin-bottom:20px}body,td,a,p,.h{font-family:arial,sans-serif}.h{color:#36c;font-size:20px}.q{color:#00c}.ts td{padding:0}.ts{border-collapse:collapse}em{font-weight:bold;font-style:normal}.lst{height:25px;width:496px}.gsfi,.lst{font:18px arial,sans-serif}.gsfs{font:17px arial,sans-serif}.ds{display:-moz-inline-box;display:inline-block;margin:3px 0 4px;margin-left:4px}input{font-family:inherit}a.gb1,a.gb2,a.gb3,a.gb4{color:#11c !important}body{background:#fff;color:black}a{color:#11c;text-decoration:none}a:hover,a:active{text-decoration:underline}.fl a{color:#36c}a:visited{color:#551a8b}a.gb1,a.gb4{text-decoration:underline}a.gb3:hover{text-decoration:none}#ghead a.gb2:hover{color:#fff!important}.sblc{padding-top:5px}.sblc a{display:block;margin:2px 0;margin-left:13px;font-size:11px;}.lsbb{background:#eee;border:solid 1px;border-color:#ccc #999 #999 #ccc;height:30px;display:block}.ftl,#fll a{display:inline-block;margin:0 12px}.lsb{background:url(/images/srpr/nav_logo80.png) 0 -258px repeat-x;border:none;color:#000;cursor:pointer;height:30px;margin:0;outline:0;font:15px arial,sans-serif;vertical-align:top}.lsb:active{background:#ccc}.lst:focus{outline:none}#addlang a{padding:0 3px}.gac_v div{display:none}.gac_v .gac_v2,.gac_bt{display:block!important}table.gssb_c{z-index:986  }.nbcl{background:url(/images/srpr/nav_logo80.png) no-repeat ;height:px;width:px}</style><script></script> </head><body dir="ltr" bgcolor="#fff"><script>(function(){var src='/images/srpr/nav_logo80.png';var iesg=false;document.body.onload = function(){window.n && window.n();if (document.images){new Image().src=src;}
if (!iesg){document.f&&document.f.q.focus();document.gbqf&&document.gbqf.q.focus();}
}
})();</script><textarea id="csi" style="display:none"></textarea><div id="mngb"><div id=gbar><nobr><b class=gb1>Search</b> <a class=gb1 href="http://www.google.com/imghp?hl=en&tab=wi">Images</a> <a class=gb1 href="http://video.google.com/?hl=en&tab=wv">Videos</a> <a class=gb1 href="http://maps.google.com/maps?hl=en&tab=wl">Maps</a> <a class=gb1 href="http://news.google.com/nwshp?hl=en&tab=wn">News</a> <a class=gb1 href="http://www.google.com/shopping?hl=en&tab=wf">Shopping</a> <a class=gb1 href="https://mail.google.com/mail/?tab=wm">Gmail</a> <a class=gb1 style="text-decoration:none" href="http://www.google.com/intl/en/options/"><u>More</u> &raquo;</a></nobr></div><div id=guser width=100%><nobr><span id=gbn class=gbi></span><span id=gbf class=gbf></span><span id=gbe></span><a href="http://www.google.com/history/optout?hl=en" class=gb4>Web History</a> | <a  href="/preferences?hl=en" class=gb4>Settings</a> | <a target=_top id=gb_70 href="https://accounts.google.com/ServiceLogin?hl=en&continue=http://74.125.225.166/" class=gb4>Sign in</a></nobr></div><div class=gbh style=left:0></div><div class=gbh style=right:0></div></div><center><br clear="all" id="lgpd"><div id="lga"><div style="padding:28px 0 3px"><div dir="ltr" title="Google" align="left" id="hplogo" onload="window.lol&&lol()" style="height:110px;width:276px;background:url(/images/srpr/logo1w.png) no-repeat"><div nowrap="nowrap" style="color:#777;font-size:16px;font-weight:bold;position:relative;left:214px;top:70px"></div></div></div><br></div><form action="//www.google.com/search" name="f"><table cellpadding="0" cellspacing="0"><tr valign="top"><td width="25%">&nbsp;</td><td align="center" nowrap="nowrap"><input name="ie" value="ISO-8859-1" type="hidden"><input value="en" name="hl" type="hidden"><input name="source" type="hidden" value="hp"><div class="ds" style="height:32px;margin:4px 0"><input autocomplete="off" class="lst" value="" title="Google Search" maxlength="2048" name="q" size="57" style="color:#000;margin:0;padding:5px 8px 0 6px;vertical-align:top"></div><br style="line-height:0"><span class="ds"><span class="lsbb"><input class="lsb" value="Google Search" name="btnG" type="submit"></span></span><span class="ds"><span class="lsbb"><input class="lsb" value="I'm Feeling Lucky" name="btnI" type="submit" onclick="if(this.form.q.value)this.checked=1; else top.location='/doodles/'"></span></span></td><td class="fl sblc" align="left" nowrap="nowrap" width="25%"><a href="/advanced_search?hl=en&amp;authuser=0">Advanced search</a><a href="/language_tools?hl=en&amp;authuser=0">Language tools</a></td></tr></table><input type="hidden" id="gbv" name="gbv" value="1"></form><div id="gac_scont"></div><div style="font-size:83%;min-height:3.5em"><br></div><span id="footer"><div style="font-size:10pt"><div id="fll" style="margin:19px auto;text-align:center"><a href="/intl/en/ads/">Advertising&nbsp;Programs</a><a href="/services/">Business Solutions</a><a href="/intl/en/about.html">About Google</a><a id="fehl" href="http://74.125.225.166/setprefdomain?prefdom=US&amp;sig=0_CXgZAXYsWyAv-TqptB6G3NMgdQQ%3D">Google.com</a></div></div><p style="color:#767676;font-size:8pt">&copy; 2012 - <a href="/intl/en/policies/">Privacy & Terms</a></p></span></center><div id=xjsd></div><div id=xjsi><script>if(google.y)google.y.first=[];(function(){
var c,d,e=false;function f(a){var b={_sn:a?"FAILURE":"FALLBACK",_pu:c,_fu:d},h=google.ml(new Error("pml"),false,b,true);google.log(0,"",h)}function g(){if(!google.pml)f(true)}function i(a){window.setTimeout(function(){var b=document.createElement("script");b.src=a;document.getElementById("xjsd").appendChild(b)},0)}function j(){if(!e&&!google.pml){e=
true;f();i(d,g)}}google.dljp=function(a,b){c=a;d=b;if(!google.xjsi){google.xjsu=a;i(c,j)}};google.dlj=i;
})();
if(!google.xjs){google.dstr=[];google.rein=[];window._=window._||{};window._._DumpException=function(e){throw e};if(google.timers&&google.timers.load.t){google.timers.load.t.xjsls=new Date().getTime();}google.dljp('/xjs/_/js/hp/hp,sb_he,pcc/rt\x3dj/ver\x3dXz87VpaxUb0.en_US./d\x3d1/sv\x3d1/rs\x3dAItRSTMrME976LEeoNEElhPGPyV0iB2UJg','/xjs/_/js/hp/hp,sb_he,pcc/rt\x3dj/ver\x3dXz87VpaxUb0.en_US./d\x3d1/sv\x3d1/rs\x3dAItRSTMrME976LEeoNEElhPGPyV0iB2UJg');google.xjs=1;}google.pmc={14:{},10:{"agen":false,"cgen":true,"client":"heirloom-hp","dh":true,"ds":"","eqch":true,"fl":true,"host":"google.com","jsonp":true,"msgs":{"lcky":"I\u0026#39;m Feeling Lucky","lml":"Learn more","oskt":"Input tools","psrc":"This search was removed from your \u003Ca href=\"/history\"\u003EWeb History\u003C/a\u003E","psrl":"Remove","sbit":"Search by image","srch":"Google Search"},"ovr":{"ms":1},"pq":"","qcpw":false,"scd":10,"sce":5,"stok":"PRuGIP3NZcT8gNaD9Y6zLxcclN8"},24:{}};google.y.first.push(function(){if(google.med){google.med('init');google.initHistory();google.med('history');}google.History&&google.History.initialize('/');google.hs&&google.hs.init&&google.hs.init()});if(google.j&&google.j.en&&google.j.xi){window.setTimeout(google.j.xi,0);}</script></div><script>(function(){
var b,d,e,f;function g(a,c){if(a.removeEventListener){a.removeEventListener("load",c,false);a.removeEventListener("error",c,false)}else{a.detachEvent("onload",c);a.detachEvent("onerror",c)}}function h(a){f=(new Date).getTime();++d;a=a||window.event;var c=a.target||a.srcElement;g(c,h)}var i=document.getElementsByTagName("img");b=i.length;d=0;for(var j=0,k;j<b;++j){k=i[j];if(k.complete||typeof k.src!="string"||!k.src)++d;else if(k.addEventListener){k.addEventListener("load",h,false);k.addEventListener("error",
h,false)}else{k.attachEvent("onload",h);k.attachEvent("onerror",h)}}e=b-d;function l(){if(!google.timers.load.t)return;google.timers.load.t.ol=(new Date).getTime();google.timers.load.t.iml=f;google.kCSI.imc=d;google.kCSI.imn=b;google.kCSI.imp=e;if(google.stt!==undefined)google.kCSI.stt=google.stt;google.csiReport&&google.csiReport()}if(window.addEventListener)window.addEventListener("load",
l,false);else if(window.attachEvent)window.attachEvent("onload",l);google.timers.load.t.prt=(f=(new Date).getTime());
})();
```

this is really werid,I think that burst.net company is doing sth

/etc/resolv.conf:

```
nameserver 8.8.8.8
nameserver 8.8.4.4

```

/etc/hosts

```
127.0.0.1               localhost.localdomain localhost
***.***.***.***(my ip)                    my domain name

```

---

### Post by ame177674 on 2012-10-10
> **Lars Noodén said:**
> Can you try rephrasing your question again?  Which machine are you running curl on that it does not work and what is the target of curl then?

burs.net vps is a Virtual private server (VPS)

Virtual private server (VPS) is a term used by Internet hosting services to refer to a virtual machine. The term is used for emphasizing that the virtual machine, although running in software on the same physical computer as other customers' virtual machines, is in many respects functionally equivalent to a separate physical computer, is dedicated to the individual customer's needs, has the privacy of a separate physical computer, and can be configured to run server software.

                                                              --by wikipedia
burst.net is a company which is hosting it.

firewall:

```
ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
13578                      LIMIT IN    Anywhere
4080                       ALLOW IN    Anywhere
20369/tcp                  ALLOW IN    Anywhere
20373/udp                  ALLOW IN    Anywhere
2771                       ALLOW IN    Anywhere
6882/tcp                   ALLOW IN    Anywhere
13643/udp                  ALLOW IN    Anywhere
6881                       ALLOW IN    Anywhere
80                         ALLOW IN    Anywhere
13578                      ALLOW IN    Anywhere (v6)
4080                       ALLOW IN    Anywhere (v6)
20369/tcp                  ALLOW IN    Anywhere (v6)
20373/udp                  ALLOW IN    Anywhere (v6)
2771                       ALLOW IN    Anywhere (v6)
6882/tcp                   ALLOW IN    Anywhere (v6)
13643/udp                  ALLOW IN    Anywhere (v6)
6881                       ALLOW IN    Anywhere (v6)
80                         ALLOW IN    Anywhere (v6)

```

---

