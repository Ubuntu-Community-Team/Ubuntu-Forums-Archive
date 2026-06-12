---
title: "awk: warning: escape sequence `\/' treated as plain `/'"
date: 2007-06-15
forum: Ubuntuzilla
---

### Post by jb5 on 2007-06-15
Hi Guys - I hope this isn't a simple "learner" mistake on my part, but I get the above error when running the script.

I downloaded the latest script from :- [[COLOR="RoyalBlue"]script[/COLOR]](http://sourceforge.net/project/showfiles.php?group_id=147501&package_id=231543)

I downloaded version 4.0.2 but when running the script it displays the version as 4.0.1?
After confirming that 2.0.0.4 is the latest Thunderbird version I get the awk error. 
After this the localization selection doesn't display a list of localizations and only offers an integer input in the range 0 to -1 ? 
I've tried entering 0 and -1 with no successful result! :)
At this point I  <cntl> c to end the script. Below is the output to the terminal. 

I also tried 

python ~/Desktop/ubuntuzilla.py -a install -p firefox -d

substituting thunderbird for firefox. Just in case!

#########################################################

jb@eric:~$ python ~/Desktop/ubuntuzilla.py -a install -p thunderbird

Welcome to the Ubuntuzilla Thunderbird script version 4.0.1

This script installs the latest release of the official Mozilla build of Thunderbird on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla) 


Retrieving the version of the latest release of Thunderbird from the Mozilla website...
The most recent release of Thunderbird is detected to be 2.0.0.4. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.com/](http://www.mozilla.com/)) Is it correct [y/n]? 
Please enter 'y' or 'n': y
awk: warning: escape sequence `\/' treated as plain `/'
Please choose the localization (language) for Thunderbird. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla) for steps you can take to resolve this problem.]

Enter your choice of localization (integer, from 0 to -1): Traceback (most recent call last):
  File "/home/jb/Desktop/ubuntuzilla.py", line 668, in <module>
    bs.start()
  File "/home/jb/Desktop/ubuntuzilla.py", line 64, in start
    ti.start()
  File "/home/jb/Desktop/ubuntuzilla.py", line 84, in start
    self.install()
  File "/home/jb/Desktop/ubuntuzilla.py", line 320, in install
    while not self.getLocalizationChoice():
  File "/home/jb/Desktop/ubuntuzilla.py", line 142, in getLocalizationChoice
    self.locChoice = raw_input("Enter your choice of localization (integer, from 0 to " + str(len(self.locList) - 1) + "): ")
KeyboardInterrupt
jb@eric:~$

---

### Post by nanotube on 2007-06-15
> **jb5 said:**
> Hi Guys - I hope this isn't a simple "learner" mistake on my part, but I get the above error when running the script.

I downloaded the latest script from :- [[COLOR="RoyalBlue"]script[/COLOR]](http://sourceforge.net/project/showfiles.php?group_id=147501&package_id=231543)

I downloaded version 4.0.2 but when running the script it displays the version as 4.0.1?
After confirming that 2.0.0.4 is the latest Thunderbird version I get the awk error. 
After this the localization selection doesn't display a list of localizations and only offers an integer input in the range 0 to -1 ? 
I've tried entering 0 and -1 with no successful result! :)
At this point I  <cntl> c to end the script. Below is the output to the terminal. 

I also tried 

python ~/Desktop/ubuntuzilla.py -a install -p firefox -d

substituting thunderbird for firefox. Just in case!

#########################################################

jb@eric:~$ python ~/Desktop/ubuntuzilla.py -a install -p thunderbird

Welcome to the Ubuntuzilla Thunderbird script version 4.0.1

This script installs the latest release of the official Mozilla build of Thunderbird on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla) 


Retrieving the version of the latest release of Thunderbird from the Mozilla website...
The most recent release of Thunderbird is detected to be 2.0.0.4. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.com/](http://www.mozilla.com/)) Is it correct [y/n]? 
Please enter 'y' or 'n': y
awk: warning: escape sequence `\/' treated as plain `/'
Please choose the localization (language) for Thunderbird. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla) for steps you can take to resolve this problem.]

Enter your choice of localization (integer, from 0 to -1): Traceback (most recent call last):
  File "/home/jb/Desktop/ubuntuzilla.py", line 668, in <module>
    bs.start()
  File "/home/jb/Desktop/ubuntuzilla.py", line 64, in start
    ti.start()
  File "/home/jb/Desktop/ubuntuzilla.py", line 84, in start
    self.install()
  File "/home/jb/Desktop/ubuntuzilla.py", line 320, in install
    while not self.getLocalizationChoice():
  File "/home/jb/Desktop/ubuntuzilla.py", line 142, in getLocalizationChoice
    self.locChoice = raw_input("Enter your choice of localization (integer, from 0 to " + str(len(self.locList) - 1) + "): ")
KeyboardInterrupt
jb@eric:~$

hmm, well first, thanks for pointing out that i forgot to update the version string to 4.0.2 :)
second, your awk error... i am guessing that maybe you are using gawk instead of the default mawk (which gives me no problems). please post output of this command:
```
awk -W version
```
if it is indeed gawk (or something else besides mawk) that you have, you can run
```
sudo update-alternatives --config awk
```
and choose 'mawk' as your default 'awk', then run the script again, and everything "should" be fine. :)

please post back here with how it all goes!

---

### Post by jb5 on 2007-06-15
Hi Nanotube. Thanks for getting back. 

OP of awk -W version

####################################################
jb@eric:~$ awk -W version
GNU Awk 3.1.5
Copyright (C) 1989, 1991-2005 Free Software Foundation.

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 2 of the Licence, or

(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.
jb@eric:~$ 
########################################################


so changed default awk from gawk to mawk as per:-

sudo update-alternatives --config awk

As you suggest the awk problem is now fixed. :D

However, still get the localization list to integer between 0 and -1? OP below.

#######################################################
jb@eric:~$ python ~/Desktop/ubuntuzilla.py -a install -p thunderbird -d
Your commandline options:
{'package': 'thunderbird', 'skipgpg': False, 'action': 'install', 'test': False, 'mirror': 'releases.mozilla.org', 'debug': True, 'unattended': False, 'keyservers': ['subkeys.pgp.net', 'pgpkeys.mit.edu', 'pgp.mit.edu'], 'targetdir': '/opt'}
Debug mode ON.

Welcome to the Ubuntuzilla Thunderbird script version 4.0.1

This script installs the latest release of the official Mozilla build of Thunderbird on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla) 


Retrieving the version of the latest release of Thunderbird from the Mozilla website...
The most recent release of Thunderbird is detected to be 2.0.0.4. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.com/](http://www.mozilla.com/)) Is it correct [y/n]? 
Please enter 'y' or 'n': y
[]
Please choose the localization (language) for Thunderbird. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla) for steps you can take to resolve this problem.]

Enter your choice of localization (integer, from 0 to -1): 0
Enter your choice of localization (integer, from 0 to -1): -1
Enter your choice of localization (integer, from 0 to -1): 1
Enter your choice of localization (integer, from 0 to -1): Traceback (most recent call last):
  File "/home/jb/Desktop/ubuntuzilla.py", line 668, in <module>
    bs.start()
  File "/home/jb/Desktop/ubuntuzilla.py", line 64, in start
    ti.start()
  File "/home/jb/Desktop/ubuntuzilla.py", line 84, in start
    self.install()
  File "/home/jb/Desktop/ubuntuzilla.py", line 320, in install
    while not self.getLocalizationChoice():
  File "/home/jb/Desktop/ubuntuzilla.py", line 142, in getLocalizationChoice
    self.locChoice = raw_input("Enter your choice of localization (integer, from 0 to " + str(len(self.locList) - 1) + "): ")
KeyboardInterrupt
jb@eric:~$ 
#########################################################

---

### Post by nanotube on 2007-06-15
> **jb5 said:**
> Hi Nanotube. Thanks for getting back. 

<snip>
jb@eric:~$ 
#########################################################

hmm, ok, so it wasn't awk, then... that's a mighty strange error, since i just ran the same version of the script, and it worked for me... could you please post the output of the following commands;
```
w3m -dump_source ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/
```
and

```
w3m -dump_source ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/ |grep -i 'a href=' |grep -v '\"\.\.' |grep -v 'xpi' |awk -F'\"' '{print $2}' |awk -F'\/' '{print $1}'
```

and see what comes out? these are the actual commands that retrieve the localization list...

the -d switch should show the raw output of the first one, (and it does when i run it), but for some reason yours doesn't, just empty brackets 
```
Please enter 'y' or 'n': y
[]
```

so try those two commands i posted, and post the complete output of those two. thanks for working with me on this! :)

edit: btw, a note about features of the forum: when you post output, wrap it in code tags (click the # button above the edit box), then it will be formatted in a nice little box all by itself, like the commands above, e.g. :)

---

### Post by jb5 on 2007-06-15
> **nanotube said:**
> 

so try those two commands i posted, and post the complete output of those two. thanks for working with me on this! :)

Hey no problem, I only wish I could be of more use, but I've only just started played about with BASH, python is a whole new ball game! :D

OP of two commands
```

jb@eric:~$ w3m -dump_source ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/
jb@eric:~$ 
jb@eric:~$ w3m -dump_source ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/ |grep -i 'a href=' |grep -v '\"\.\.' |grep -v 'xpi' |awk -F'\"' '{print $2}' |awk -F'\/' '{print $1}'
jb@eric:~$ 
jb@eric:~$ 
jb@eric:~$ 

```

I'm guessing something should be happening here?

---

### Post by nanotube on 2007-06-15
> **jb5 said:**
> Hey no problem, I only wish I could be of more use, but I've only just started played about with BASH, python is a whole new ball game! :D

OP of two commands
```

jb@eric:~$ w3m -dump_source ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/
jb@eric:~$ 
jb@eric:~$ w3m -dump_source ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/ |grep -i 'a href=' |grep -v '\"\.\.' |grep -v 'xpi' |awk -F'\"' '{print $2}' |awk -F'\/' '{print $1}'
jb@eric:~$ 
jb@eric:~$ 
jb@eric:~$ 

```

I'm guessing something should be happening here?

you bet! something definitely should be happening. w3m should be retrieving the directory listing from that directory on releases.mozilla.org... here's what i get from the first command, eg:
```
nanotube@groovy4:~$ w3m -dump_source ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/
<html>
<head>
<base href="ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/">
<title>ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/</title>
</head>
<body>
<h1>Index of ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/</h1>
<pre>
<a href="..">[Upper Directory]</a>
<a href="be/">be/</a>. . . . . . . . . Jun 13 23:50       
<a href="bg/">bg/</a>. . . . . . . . . Jun 13 23:50       
<a href="ca/">ca/</a>. . . . . . . . . Jun 13 23:50       
<a href="cs/">cs/</a>. . . . . . . . . Jun 13 23:50       
<a href="da/">da/</a>. . . . . . . . . Jun 13 23:50       
<a href="de/">de/</a>. . . . . . . . . Jun 13 23:50       
<a href="el/">el/</a>. . . . . . . . . Jun 13 23:50       
<a href="en-GB/">en-GB/</a> . . . . . . . Jun 13 23:50       
<a href="en-US/">en-US/</a> . . . . . . . Jun 13 23:50       
<a href="es-AR/">es-AR/</a> . . . . . . . Jun 13 23:50       
<a href="es-ES/">es-ES/</a> . . . . . . . Jun 13 23:50       
<a href="eu/">eu/</a>. . . . . . . . . Jun 13 23:50       
<a href="fi/">fi/</a>. . . . . . . . . Jun 13 23:50       
<a href="fr/">fr/</a>. . . . . . . . . Jun 13 23:50       
<a href="ga-IE/">ga-IE/</a> . . . . . . . Jun 13 23:50       
<a href="hu/">hu/</a>. . . . . . . . . Jun 13 23:50       
<a href="it/">it/</a>. . . . . . . . . Jun 13 23:50       
<a href="ja/">ja/</a>. . . . . . . . . Jun 13 23:50       
<a href="ko/">ko/</a>. . . . . . . . . Jun 13 23:50       
<a href="lt/">lt/</a>. . . . . . . . . Jun 13 23:50       
<a href="mk/">mk/</a>. . . . . . . . . Jun 13 23:50       
<a href="nb-NO/">nb-NO/</a> . . . . . . . Jun 13 23:50       
<a href="nl/">nl/</a>. . . . . . . . . Jun 13 23:50       
<a href="nn-NO/">nn-NO/</a> . . . . . . . Jun 13 23:50       
<a href="pa-IN/">pa-IN/</a> . . . . . . . Jun 13 23:50       
<a href="pl/">pl/</a>. . . . . . . . . Jun 13 23:50       
<a href="pt-BR/">pt-BR/</a> . . . . . . . Jun 13 23:50       
<a href="pt-PT/">pt-PT/</a> . . . . . . . Jun 13 23:50       
<a href="ru/">ru/</a>. . . . . . . . . Jun 13 23:50       
<a href="sk/">sk/</a>. . . . . . . . . Jun 13 23:50       
<a href="sl/">sl/</a>. . . . . . . . . Jun 13 23:50       
<a href="sv-SE/">sv-SE/</a> . . . . . . . Jun 13 23:50       
<a href="tr/">tr/</a>. . . . . . . . . Jun 13 23:50       
<a href="xpi/">xpi/</a> . . . . . . . . Jun 13 13:23       
<a href="zh-CN/">zh-CN/</a> . . . . . . . Jun 13 23:50       
<a href="zh-TW/">zh-TW/</a> . . . . . . . Jun 13 23:50       
</pre>
</body>
</html>

```

i do not know what's wrong with your w3m or whatever... so let's take some stabs at it... see if any of the following commands produce any results:
```
w3m -dump_source http://google.com
w3m -dump_source ftp://releases.mozilla.org/
w3m -dump_source http://releases.mozilla.org/
```

also, please post output of
```
w3m -version
```

also, see what happens if you point firefox to [ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/](ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/) do you get a directory listing there?

and, what version of ubuntu are you running, btw? :)

---

### Post by jb5 on 2007-06-15
```
jb@eric:~$ w3m -dump_source http://google.com
Received cookie: PREF=ID=4690df5209e6b630:TM=1181923844:LM=1181923844:S=wg_KvHxOGWRW1nd1
This cookie was rejected to prevent security violation. [RFC 2109 4.3.2 rule 3]
Received cookie: PREF=ID=f00da52f72e3aa2f:TM=1181923844:LM=1181923844:S=K1xD7EYVzgBGnX9I
Received cookie: PREF=ID=666e3e771bc04940:TM=1181923844:LM=1181923844:S=z0MJ_suZ8LIHEGF6
jb@eric:~$ 
```

```
jb@eric:~$ w3m -dump_source ftp://releases.mozilla.org/
jb@eric:~$ 
jb@eric:~$ w3m -dump_source http://releases.mozilla.org/
jb@eric:~$ 
```

```
jb@eric:~$ w3m -version
w3m version w3m/0.5.1+cvs-1.968, options lang=en,m17n,image,color,ansi-color,mouse,gpm,menu,cookie,ssl,ssl-verify,external-uri-loader,w3mmailer,nntp,gopher,ipv6,alarm,mark,migemo
jb@eric:~$ 
jb@eric:~$ 

```

OP of firefox - 

```

Index of ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/
Up to higher level directory
Directory: be 		13/06/07 	23:50:00
Directory: bg 		13/06/07 	23:50:00
Directory: ca 		13/06/07 	23:50:00
Directory: cs 		13/06/07 	23:50:00
Directory: da 		13/06/07 	23:50:00
Directory: de 		13/06/07 	23:50:00
Directory: el 		13/06/07 	23:50:00
Directory: en-GB 		13/06/07 	23:50:00
Directory: en-US 		13/06/07 	23:50:00
Directory: es-AR 		13/06/07 	23:50:00
Directory: es-ES 		13/06/07 	23:50:00
Directory: eu 		13/06/07 	23:50:00
Directory: fi 		13/06/07 	23:50:00
Directory: fr 		13/06/07 	23:50:00
Directory: ga-IE 		13/06/07 	23:50:00
Directory: hu 		13/06/07 	23:50:00
Directory: it 		13/06/07 	23:50:00
Directory: ja 		13/06/07 	23:50:00
Directory: ko 		13/06/07 	23:50:00
Directory: lt 		13/06/07 	23:50:00
Directory: mk 		13/06/07 	23:50:00
Directory: nb-NO 		13/06/07 	23:50:00
Directory: nl 		13/06/07 	23:50:00
Directory: nn-NO 		13/06/07 	23:50:00
Directory: pa-IN 		13/06/07 	23:50:00
Directory: pl 		13/06/07 	23:50:00
Directory: pt-BR 		13/06/07 	23:50:00
Directory: pt-PT 		13/06/07 	23:50:00
Directory: ru 		13/06/07 	23:50:00
Directory: sk 		13/06/07 	23:50:00
Directory: sl 		13/06/07 	23:50:00
Directory: sv-SE 		13/06/07 	23:50:00
Directory: tr 		13/06/07 	23:50:00
Directory: xpi 		13/06/07 	13:23:00
Directory: zh-CN 		13/06/07 	23:50:00
Directory: zh-TW 		13/06/07 	23:50:00

```

I'm running Feisty 7.04
Could it be something to do with my iptables' settings?

---

### Post by nanotube on 2007-06-15
that's weird... i have the exact same w3m -version output, i'm also running feisty, but when i do a w3m on google, e.g., i get 
```
nanotube@groovy4:~$ w3m -dump_source http://google.com
Received cookie: PREF=ID=2161066f54a2ffd8:TM=1181928429:LM=1181928429:S=nAxVY2isrND9KGHD
This cookie was rejected to prevent security violation. [RFC 2109 4.3.2 rule 3]
<html><head><meta http-equiv="content-type" content="text/html; charset=ISO-8859-1"><title>Google</title><style><!--
body,td,a,p,.h{font-family:arial,sans-serif}
.h{font-size:20px}
.h{color:#3366cc}
.q{color:#00c}
#gbar{float:left;font-weight:bold;height:22px;padding-left:2px}#gbh{border-top:1px solid #c9d7f1;font-size:0;height:0;position:absolute;right:0;top:24px;width:200%}#gbi{background:#fff;border:1px solid;border-color:#c9d7f1 #36c #36c #a2bae7;font-size:13px;top:24px;z-index:1000}#guser{padding-bottom:7px !important}#gbar,#guser{font-size:13px;padding-top:1px !important}.gb1,.gb3{display:inline;height:22px;margin-right:1em;vertical-align:top}#gbi,.gb2{display:none;position:absolute;width:7em}.gb2{z-index:1001}#gbar a,#gbar a:active,#gbar a:visited{color:#00c;font-weight:normal}.gb2 a,.gb3 a{text-decoration:none}.gb2 a{display:block;padding:.2em .5em}#gbar .gb2 a:hover{background:#36c;color:#fff}--></style>
<script>
<!--
function sf(){document.f.q.focus();}
window.gbar={};(function(){function z(a,d,b){var c="on"+d;if(a.addEventListener){a.addEventListener(d,b,false)}else if(a.attachEvent){a.attachEvent(c,b)}else{var e=a[c];a[c]=function(){var f=e.apply(this,arguments),n=b.apply(this,arguments);return f==undefined?n:(n==undefined?f:n&&f)}}};var o=window,s=o.location,x=s.search,w=s.protocol,m=document,i="",q,u="",h,g,j=o.gbar,r="wivnlmzbjpcoegz0tqfys",l;function p(a){return escape(unescape(a.replace(/\+/g," "))).replace(/\+/g,"%2B")}function t(a){return g[a].firstChild.tagName=="A"}function k(a){return x.match("[?&]("+a+"=)([^&#]*)")}j.init=function(){var a=0,d,b="affdom,channel,client,hl,hs,ie,lr,ned,oe,og,rls,rlz".split(","),c=k("as_q"),e=k("q");q=k("near");g=m.getElementById("gbar").getElementsByTagName("div");e&&(i=e[2])&&c&&(i+="+");c&&(i+=c[2]);while(t(a++)){}l=r.charAt(a-1);for(a=0;b[a];a++){d=k(b[a]);d&&(u+="&"+d[1]+p(d[2]))}for(a=0;g[a];a++){t(a)&&y(a)}h=m.getElementById("gbi");z(m,"click",j.close)};function y(a){var d=g[a].firstChild,b=d.href+(d.href.match("[?]")?"&":"?"),c=r.charAt(a);if(c!="z"){b+="tab="+l+c;if("com".indexOf(c)>=0){b=b.replace("http:",w)}else{b+=u;if(i){b+="&q="+p(i);q&&l=="l"&&(b+="+near%3A+"+p(q[2]))}}}d.href=b}function v(a,d,b){a.display=a.display=="block"?"none":"block";a.left=d+"px";a.top=b+"px"}j.tg=function(a){var d=0,b,c,e,f=0;a=a?a:o.event;a.cancelBubble=true;for(;h&&g[f];f++){c=g[f];e=c.className;if(e=="gb3"){b=c.offsetLeft;while(c=c.offsetParent){b+=c.offsetLeft}v(h.style,b,24)}else if(e=="gb2"){c.id=="gbar"+l&&(c.style.padding=".2em .5em");v(c.style,b+1,25+d);d+=20}}h.style.height=d+"px"};j.close=function(a){h&&h.style.display=="block"&&j.tg(a)};})();// -->
</script>
</head><body bgcolor=#ffffff text=#000000 link=#0000cc vlink=#551a8b alink=#ff0000 onload="sf();if(document.images){new Image().src='/images/nav_logo3.png'}" topmargin=3 marginheight=3><div id=gbar><nobr><div class=gb1>Web</a></div><div class=gb1><a href=http://images.google.com/imghp>Images</a></div><div class=gb1><a href=http://video.google.com/>Video</a></div><div class=gb1><a href=http://news.google.com/nwshp>News</a></div><div class=gb1><a href=http://maps.google.com/maps>Maps</a></div><div class=gb1><a href=http://mail.google.com/mail>Gmail</a></div><div class=gb3><a href=http://www.google.com/intl/en/options/ onclick="this.blur();gbar.tg(event);return false"><u>more</u> <span style=font-size:11px>&#9660;</span></a></div><div class=gb2><a href=http://blogsearch.google.com/>Blog Search</a></div><div class=gb2><a href=http://www.blogger.com/>Blogger</a></div><div class=gb2><a href=http://books.google.com/bkshp>Books</a></div><div class=gb2><a href=http://www.google.com/calendar>Calendar</a></div><div class=gb2><a href=http://docs.google.com/>Documents</a></div><div class=gb2><a href=http://finance.google.com/finance>Finance</a></div><div class=gb2><a href=http://groups.google.com/grphp>Groups</a></div><div class=gb2><a href=http://labs.google.com/>Labs</a></div><div class=gb2><a href=http://www.orkut.com/>Orkut</a></div><div class=gb2><a href=http://www.google.com/ptshp>Patents</a></div><div class=gb2><a href=http://picasaweb.google.com/home>Photos</a></div><div class=gb2><a href=http://www.google.com/prdhp>Products</a></div><div class=gb2><a href=http://www.google.com/reader>Reader</a></div><div class=gb2><a href=http://scholar.google.com/schhp>Scholar</a></div></nobr></div><iframe frameborder=0 id=gbi scrolling=no></iframe><div id=gbh></div><script>window.gbar&&gbar.init()</script><div align=right id=guser style="font-size:84%;padding-bottom:4px" width=100%><nobr><a href="/url?sa=p&pref=ig&pval=3&q=http://www.google.com/ig%3Fhl%3Den&usg=AFQjCNGGKPSkVizi4Snb0FhJZehI-qV8sg">iGoogle</a>&nbsp;|&nbsp;<a href="https://www.google.com/accounts/Login?continue=http://www.google.com/&hl=en">Sign in</a></nobr></div><center><br id=lgpd><img alt="Google" height=110 src="/intl/en_ALL/images/logo.gif" width=276><br><br><form action="/search" name=f><table cellpadding=0 cellspacing=0><tr valign=top><td width=25%>&nbsp;</td><td align=center nowrap><input name=hl type=hidden value=en><input type=hidden name=ie value="ISO-8859-1"><input maxlength=2048 name=q size=55 title="Google Search" value=""><br><input name=btnG type=submit value="Google Search"><input name=btnI type=submit value="I'm Feeling Lucky"></td><td nowrap width=25%><font size=-2>&nbsp;&nbsp;<a href=/advanced_search?hl=en>Advanced Search</a><br>&nbsp;&nbsp;<a href=/preferences?hl=en>Preferences</a><br>&nbsp;&nbsp;<a href=/language_tools?hl=en>Language Tools</a></font></td></tr></table></form><br><br><font size=-1><a href="/intl/en/ads/">Advertising&nbsp;Programs</a> - <a href="/services/">Business Solutions</a> - <a href="/intl/en/about.html">About Google</a></font><p><font size=-2>&copy;2007 Google</font></p></center></body></html>
```

there must be some kind of a setting somewhere maybe you set? or maybe indeed if you have some weird iptables config, though since it does get connected to the site, i kind of doubt it... but try flushing your iptables ruleset, and see if you get any different results from a w3m.

also, try 
```
w3m -dump ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/
w3m -dump http://google.com

```
(just dump, instead of dump_source), and see if you get anything different...

also, try just 
```
w3m ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/
w3m http://google.com

```
and see if the page shows up.

---

### Post by jb5 on 2007-06-15
> **jb5 said:**
> Hi Guys - I hope this isn't a simple "learner" mistake on my part, but I get the above error when running the script.

I ran the program again, this time as root (DOH):-

```

sudo python ~/Desktop/ubuntuzilla.py -a install -p thunderbird -d

```
And the localizations appeared! :redface:
However now get --  thunderbird already newest version, and gpg key error.
```

jb@eric:~/Desktop$ sudo python ~/Desktop/ubuntuzilla.py -a install -p thunderbird -d
Your commandline options:
{'package': 'thunderbird', 'skipgpg': False, 'action': 'install', 'test': False, 'mirror': 'releases.mozilla.org', 'debug': True, 'unattended': False, 'keyservers': ['subkeys.pgp.net', 'pgpkeys.mit.edu', 'pgp.mit.edu'], 'targetdir': '/opt'}
Debug mode ON.

Welcome to the Ubuntuzilla Thunderbird script version 4.0.1

This script installs the latest release of the official Mozilla build of Thunderbird on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla 


Retrieving the version of the latest release of Thunderbird from the Mozilla website...
The most recent release of Thunderbird is detected to be 2.0.0.4. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.com/) Is it correct [y/n]? 
Please enter 'y' or 'n': y
['<html>\n', '<head>\n', '<base href="ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/">\n', '<title>ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/</title>\n', '</head>\n', '<body>\n', '<h1>Index of ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/</h1>\n', '<pre>\n', '<a href="..">[Upper Directory]</a>\n', '<a href="be/">be/</a>. . . . . . . . . Jun 13 23:50       \n', '<a href="bg/">bg/</a>. . . . . . . . . Jun 13 23:50       \n', '<a href="ca/">ca/</a>. . . . . . . . . Jun 13 23:50       \n', '<a href="cs/">cs/</a>. . . . . . . . . Jun 13 23:50       \n', '<a href="da/">da/</a>. . . . . . . . . Jun 13 23:50       \n', '<a href="de/">de/</a>. . . . . . . . . Jun 13 23:50       \n', '<a href="el/">el/</a>. . . . . . . . . Jun 13 23:50       \n', '<a href="en-GB/">en-GB/</a> . . . . . . . Jun 13 23:50       \n', '<a href="en-US/">en-US/</a> . . . . . . . Jun 13 23:50       \n', '<a href="es-AR/">es-AR/</a> . . . . . . . Jun 13 23:50       \n', '<a href="es-ES/">es-ES/</a> . . . . . . . Jun 13 23:50       \n', '<a href="eu/">eu/</a>. . . . . . . . . Jun 13 23:50       \n', '<a href="fi/">fi/</a>. . . . . . . . . Jun 13 23:50       \n', '<a href="fr/">fr/</a>. . . . . . . . . Jun 13 23:50       \n', '<a href="ga-IE/">ga-IE/</a> . . . . . . . Jun 13 23:50       \n', '<a href="hu/">hu/</a>. . . . . . . . . Jun 13 23:50       \n', '<a href="it/">it/</a>. . . . . . . . . Jun 13 23:50       \n', '<a href="ja/">ja/</a>. . . . . . . . . Jun 13 23:50       \n', '<a href="ko/">ko/</a>. . . . . . . . . Jun 13 23:50       \n', '<a href="lt/">lt/</a>. . . . . . . . . Jun 13 23:50       \n', '<a href="mk/">mk/</a>. . . . . . . . . Jun 13 23:50       \n', '<a href="nb-NO/">nb-NO/</a> . . . . . . . Jun 13 23:50       \n', '<a href="nl/">nl/</a>. . . . . . . . . Jun 13 23:50       \n', '<a href="nn-NO/">nn-NO/</a> . . . . . . . Jun 13 23:50       \n', '<a href="pa-IN/">pa-IN/</a> . . . . . . . Jun 13 23:50       \n', '<a href="pl/">pl/</a>. . . . . . . . . Jun 13 23:50       \n', '<a href="pt-BR/">pt-BR/</a> . . . . . . . Jun 13 23:50       \n', '<a href="pt-PT/">pt-PT/</a> . . . . . . . Jun 13 23:50       \n', '<a href="ru/">ru/</a>. . . . . . . . . Jun 13 23:50       \n', '<a href="sk/">sk/</a>. . . . . . . . . Jun 13 23:50       \n', '<a href="sl/">sl/</a>. . . . . . . . . Jun 13 23:50       \n', '<a href="sv-SE/">sv-SE/</a> . . . . . . . Jun 13 23:50       \n', '<a href="tr/">tr/</a>. . . . . . . . . Jun 13 23:50       \n', '<a href="xpi/">xpi/</a> . . . . . . . . Jun 13 13:23       \n', '<a href="zh-CN/">zh-CN/</a> . . . . . . . Jun 13 23:50       \n', '<a href="zh-TW/">zh-TW/</a> . . . . . . . Jun 13 23:50       \n', '</pre>\n', '</body>\n', '</html>\n']
Please choose the localization (language) for Thunderbird. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla for steps you can take to resolve this problem.]
  0. be           1. bg           2. ca           3. cs        
  4. da           5. de           6. el           7. en-GB     
  8. en-US        9. es-AR       10. es-ES       11. eu        
 12. fi          13. fr          14. ga-IE       15. hu        
 16. it          17. ja          18. ko          19. lt        
 20. mk          21. nb-NO       22. nl          23. nn-NO     
 24. pa-IN       25. pl          26. pt-BR       27. pt-PT     
 28. ru          29. sk          30. sl          31. sv-SE     
 32. tr          33. zh-CN       34. zh-TW     
Enter your choice of localization (integer, from 0 to 34): 7
You have chosen localization en-GB. Is that correct [y/n]? 
Please enter 'y' or 'n': y
Get: 1 http://archive.ubuntu.com feisty-backports Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_GB                                                                           
Get: 2 http://archive.canonical.com feisty-commercial Release.gpg [191B]                                                                        
Ign http://archive.canonical.com feisty-commercial/main Translation-en_GB                                                                       
Get: 3 http://gb.archive.ubuntu.com feisty Release.gpg [191B]                                                                                   
Hit http://gb.archive.ubuntu.com feisty/main Translation-en_GB                                                            
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_GB                
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_GB                  
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_GB                
Get: 4 http://archive.ubuntu.com feisty-updates Release.gpg [191B]                         
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_GB                    
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_GB                  
Hit http://archive.canonical.com feisty-commercial Release                                 
Ign http://gb.archive.ubuntu.com feisty/restricted Translation-en_GB                       
Ign http://gb.archive.ubuntu.com feisty/universe Translation-en_GB   
Hit http://gb.archive.ubuntu.com feisty/multiverse Translation-en_GB 
Get: 5 http://gb.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://gb.archive.ubuntu.com feisty-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty-updates/restricted Translation-en_GB
Get: 6 http://archive.ubuntu.com feisty-security Release.gpg [191B]                        
Ign http://archive.ubuntu.com feisty-security/main Translation-en_GB                       
Ign http://archive.ubuntu.com feisty-security/restricted Translation-en_GB                 
Ign http://archive.ubuntu.com feisty-security/universe Translation-en_GB                                         
Get: 7 http://security.ubuntu.com feisty-security Release.gpg [191B]                                             
Ign http://security.ubuntu.com feisty-security/main Translation-en_GB                                            
Ign http://archive.ubuntu.com feisty-security/multiverse Translation-en_GB                                       
Hit http://archive.ubuntu.com feisty-backports Release                                                           
Hit http://gb.archive.ubuntu.com feisty Release                                                                                       
Hit http://archive.canonical.com feisty-commercial/main Packages                                                                      
Hit http://archive.ubuntu.com feisty-updates Release                                                                                  
Hit http://gb.archive.ubuntu.com feisty-updates Release                                                         
Hit http://archive.ubuntu.com feisty-security Release                                                           
Get: 8 http://www.getautomatix.com feisty Release.gpg [189B]                                                    
Ign http://www.getautomatix.com feisty/main Translation-en_GB                                                   
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_GB                                     
Ign http://security.ubuntu.com feisty-security/universe Translation-en_GB                  
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_GB                
Hit http://gb.archive.ubuntu.com feisty/main Packages                                      
Hit http://archive.ubuntu.com feisty-backports/main Packages                               
Hit http://archive.ubuntu.com feisty-backports/restricted Packages                         
Hit http://archive.ubuntu.com feisty-backports/universe Packages                           
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages                         
Hit http://gb.archive.ubuntu.com feisty/restricted Packages                                
Hit http://gb.archive.ubuntu.com feisty/main Sources                                       
Hit http://gb.archive.ubuntu.com feisty/restricted Sources                                 
Hit http://security.ubuntu.com feisty-security Release               
Hit http://archive.ubuntu.com feisty-updates/universe Packages                            
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages                          
Hit http://gb.archive.ubuntu.com feisty/universe Packages                                 
Hit http://gb.archive.ubuntu.com feisty/universe Sources             
Hit http://gb.archive.ubuntu.com feisty/multiverse Packages          
Hit http://gb.archive.ubuntu.com feisty/multiverse Sources           
Hit http://gb.archive.ubuntu.com feisty-updates/main Packages        
Hit http://www.getautomatix.com feisty Release                                             
Hit http://archive.ubuntu.com feisty-security/main Packages                                
Hit http://archive.ubuntu.com feisty-security/restricted Packages                        
Hit http://archive.ubuntu.com feisty-security/universe Packages                          
Hit http://archive.ubuntu.com feisty-security/multiverse Packages                        
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Packages                      
Hit http://gb.archive.ubuntu.com feisty-updates/main Sources         
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Sources   
Hit http://security.ubuntu.com feisty-security/main Packages         
Hit http://www.getautomatix.com feisty/main Packages
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Fetched 8B in 0s (10B/s) 
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mozilla-thunderbird is already the newest version.
libstdc++5 is already the newest version.
libgtk2.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

A Thunderbird profile has been found at ~/.thunderbird. Do you want to make a backup of your Mozilla Thunderbird profile at ~/.thunderbird? Note that if you store your email there, this may take quite a bit of disk space. You may wish to check the size of that directory and the amount of free disk space before you answer this question. Make backup? [y/n]: 
Please enter 'y' or 'n': y

Backing up old thunderbird preferences


Downloading Thunderbird archive from the Mozilla site

--17:45:13--  ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/en-GB/thunderbird-2.0.0.4.tar.gz
           => `thunderbird-2.0.0.4.tar.gz'
Resolving releases.mozilla.org... 64.50.236.214, 156.56.247.196, 204.152.184.113, ...
Connecting to releases.mozilla.org|64.50.236.214|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/en-GB ... done.
==> SIZE thunderbird-2.0.0.4.tar.gz ... done.
==> PASV ... done.    ==> REST 11180767 ... done.    
==> RETR thunderbird-2.0.0.4.tar.gz ... done.
Length: 11,180,767 (11M), 0 (0) remaining

100%[+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++] 11,180,767    --.--K/s             

17:45:16 (0.00 B/s) - `thunderbird-2.0.0.4.tar.gz' saved [11180767]


Downloading Thunderbird signature from the Mozilla site

--17:45:16--  ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/en-GB/thunderbird-2.0.0.4.tar.gz.asc
           => `thunderbird-2.0.0.4.tar.gz.asc'
Resolving releases.mozilla.org... 64.50.236.214, 155.98.64.83, 156.56.247.196, ...
Connecting to releases.mozilla.org|64.50.236.214|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/en-GB ... done.
==> SIZE thunderbird-2.0.0.4.tar.gz.asc ... done.
==> PASV ... done.    ==> REST 186 ... done.    
==> RETR thunderbird-2.0.0.4.tar.gz.asc ... done.
Length: 186, 0 remaining

100%[+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++] 186           --.--K/s             

17:45:19 (0.00 B/s) - `thunderbird-2.0.0.4.tar.gz.asc' saved [186]


Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: WARNING: unsafe ownership on configuration file `/home/jb/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
Unable to retrieve Mozilla Software Releases Public key from subkeys.pgp.net . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/jb/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
Unable to retrieve Mozilla Software Releases Public key from pgpkeys.mit.edu . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/jb/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
Unable to retrieve Mozilla Software Releases Public key from pgp.mit.edu . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/jb/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
Unable to retrieve Mozilla Software Releases Public key from subkeys.pgp.net . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/jb/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
Unable to retrieve Mozilla Software Releases Public key from pgpkeys.mit.edu . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/jb/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
Unable to retrieve Mozilla Software Releases Public key from pgp.mit.edu . Trying again...
Failed to retrieve Mozilla Software Releases Public key from any of the listed keyservers. Please check your network connection, and try again later.

jb@eric:~/Desktop$

```

```

-------cut----------
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mozilla-thunderbird is already the newest version.
libstdc++5 is already the newest version.
libgtk2.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
-------cut--------

```
This is actually the OP from the second time I ran the program. 
(My internet connection decided to fail on me halfway through posting my last reply and so this is the only bit of terminal OP I could recover. One of those days I guess!)

Anyway, I decided to run the original installnewthunderbird.sh script and low & behold

```

jb@eric:~/DATA/Scripts$ sudo bash installnewthunderbird.sh -install

Welcome to the Ubuntuzilla Thunderbird script for installation of the official Mozilla build of Thunderbird on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla


The most recent release of thunderbird is detected to be 2.0.0.4. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.com/) Is it correct [y/n]? y
Please choose the localization (language) for Thunderbird. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla for steps you can take to resolve this problem.]
0: be
1: bg
2: ca
3: cs
4: da
5: de
6: el
7: en-GB
8: en-US
9: es-AR
10: es-ES
11: eu
12: fi
13: fr
14: ga-IE
15: hu
16: it
17: ja
18: ko
19: lt
20: mk
21: nb-NO
22: nl
23: nn-NO
24: pa-IN
25: pl
26: pt-BR
27: pt-PT
28: ru
29: sk
30: sl
31: sv-SE
32: tr
33: zh-CN
34: zh-TW
Enter your choice of localization: 7
You have chosen localization "en-GB". Is that correct [y/n]? y

Updating repositories list

Get: 1 http://archive.canonical.com feisty-commercial Release.gpg [191B]
Ign http://archive.canonical.com feisty-commercial/main Translation-en_GB                                                                                
Get: 2 http://archive.ubuntu.com feisty-backports Release.gpg [191B]                                                                                     
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_GB                                                                                   
Get: 3 http://gb.archive.ubuntu.com feisty Release.gpg [191B]                                                             
Hit http://gb.archive.ubuntu.com feisty/main Translation-en_GB                                                            
Hit http://archive.canonical.com feisty-commercial Release                                 
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_GB                                    
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_GB                  
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_GB                
Get: 4 http://archive.ubuntu.com feisty-updates Release.gpg [191B]                         
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_GB                    
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_GB                  
Ign http://gb.archive.ubuntu.com feisty/restricted Translation-en_GB                       
Ign http://gb.archive.ubuntu.com feisty/universe Translation-en_GB                         
Hit http://gb.archive.ubuntu.com feisty/multiverse Translation-en_GB                       
Get: 5 http://gb.archive.ubuntu.com feisty-updates Release.gpg [191B]                      
Ign http://gb.archive.ubuntu.com feisty-updates/main Translation-en_GB                     
Ign http://gb.archive.ubuntu.com feisty-updates/restricted Translation-en_GB               
Hit http://archive.canonical.com feisty-commercial/main Packages                           
Get: 6 http://archive.ubuntu.com feisty-security Release.gpg [191B]                        
Ign http://archive.ubuntu.com feisty-security/main Translation-en_GB 
Ign http://archive.ubuntu.com feisty-security/restricted Translation-en_GB
Ign http://archive.ubuntu.com feisty-security/universe Translation-en_GB                   
Hit http://gb.archive.ubuntu.com feisty Release                                            
Ign http://archive.ubuntu.com feisty-security/multiverse Translation-en_GB                                      
Hit http://archive.ubuntu.com feisty-backports Release                                     
Hit http://archive.ubuntu.com feisty-updates Release                                                            
Hit http://gb.archive.ubuntu.com feisty-updates Release                                                         
Get: 7 http://www.getautomatix.com feisty Release.gpg [189B]                                                    
Ign http://www.getautomatix.com feisty/main Translation-en_GB                              
Hit http://archive.ubuntu.com feisty-security Release                                      
Hit http://gb.archive.ubuntu.com feisty/main Packages                                                           
Hit http://gb.archive.ubuntu.com feisty/restricted Packages                                
Hit http://gb.archive.ubuntu.com feisty/main Sources                                       
Hit http://archive.ubuntu.com feisty-backports/main Packages                               
Hit http://archive.ubuntu.com feisty-backports/restricted Packages                         
Hit http://archive.ubuntu.com feisty-backports/universe Packages                           
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages                         
Hit http://gb.archive.ubuntu.com feisty/restricted Sources                                 
Hit http://gb.archive.ubuntu.com feisty/universe Packages                                  
Hit http://gb.archive.ubuntu.com feisty/universe Sources                                   
Hit http://gb.archive.ubuntu.com feisty/multiverse Packages                                
Hit http://gb.archive.ubuntu.com feisty/multiverse Sources                                 
Hit http://archive.ubuntu.com feisty-updates/universe Packages                             
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages                           
Hit http://gb.archive.ubuntu.com feisty-updates/main Packages                              
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Packages                        
Hit http://gb.archive.ubuntu.com feisty-updates/main Sources                               
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Sources                         
Hit http://www.getautomatix.com feisty Release                                             
Hit http://archive.ubuntu.com feisty-security/main Packages          
Hit http://archive.ubuntu.com feisty-security/restricted Packages    
Hit http://archive.ubuntu.com feisty-security/universe Packages      
Hit http://archive.ubuntu.com feisty-security/multiverse Packages    
Hit http://www.getautomatix.com feisty/main Packages                 
Get: 8 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_GB
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_GB
Ign http://security.ubuntu.com feisty-security/universe Translation-en_GB
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com feisty-security Release
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Fetched 8B in 3s (2B/s)  
Reading package lists... Done

Making sure libstdc++5 and the Ubuntu Package of Thunderbird are installed

Reading package lists... Done
Building dependency tree       
Reading state information... Done
mozilla-thunderbird is already the newest version.
libstdc++5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

A Thunderbird profile has been found at ~/.thunderbird. Do you want to make a backup of your Mozilla Thunderbird profile at ~/.thunderbird? Note that if you store your email there, this may take quite a bit of disk space. You may wish to check the size of that directory and the amount of free disk space before you answer this question. Make backup? [y/n]: y

Backing up old thunderbird preferences


Changing to home directory


Downloading Thunderbird archive from the Mozilla site

--17:49:51--  http://ftp.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/en-GB/thunderbird-2.0.0.4.tar.gz
           => `thunderbird-2.0.0.4.tar.gz'
Resolving ftp.mozilla.org... 63.245.208.138
Connecting to ftp.mozilla.org|63.245.208.138|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/en-GB/thunderbird-2.0.0.4.tar.gz [following]
--17:49:51--  http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/en-GB/thunderbird-2.0.0.4.tar.gz
           => `thunderbird-2.0.0.4.tar.gz'
Resolving releases.mozilla.org... 64.50.236.214, 130.239.18.158, 130.239.18.159, ...
Connecting to releases.mozilla.org|64.50.236.214|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 11,180,767 (11M) [application/x-gzip]

100%[==============================================================================================================>] 11,180,767    92.17K/s    ETA 00:00

17:51:16 (129.47 KB/s) - `thunderbird-2.0.0.4.tar.gz' saved [11180767/11180767]

The next step will verify the GPG signature for the Thunderbird archive to assure its integrity. This step is important for your security. However, if you have problems getting this to work right, you may choose 'no' and proceed to installation without signature verification. Do you want to verify the signature [y/n]?n
Proceeding without signature verification...

Extracting the downloaded Thunderbird archive


Removing installation file(s) to free up disk space


Linking launcher to new thunderbird

Leaving `local diversion of /usr/bin/mozilla-thunderbird to /usr/bin/mozilla-thunderbird.ubuntu'

The new thunderbird version 2.0.0.4 has been installed successfully.
jb@eric:~/DATA/Scripts$ 

```

So now I have the latest TBrd on my system. 
Not sure what I need to do to overcome the gpg problem  but if I do not use the option in the sh script I can get it to work!

```
The next step will verify the GPG signature for the Thunderbird archive to assure its integrity. 
This step is important for your security. However, if you have problems getting this to work right, you may choose 'no' and proceed to installation without signature verification. 
Do you want to verify the signature [y/n]?n
```

Really, REALLY, sorry for wasting your time on this.

"I'll get my coat"   :oops:

---

### Post by nanotube on 2007-06-15
heh wow, weird... i don't understand why w3m doesn't work without sudo for you. it really /shouldn't/ be like that, you know. :)
but i guess since your problem is solved, we can stop trying to get to the root of this (haha, check out the pun), unless you want to keep at it just out of curiosity. :)

since it works with sudo, i'm starting to suspect some kind of a permissions issue... but at this point it's just idle speculation. ...

---

### Post by jb5 on 2007-06-15
Just for completeness sake and to satisfy any lingering curiosity.


> **nanotube said:**
> 
also, try 
```
w3m -dump ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/
w3m -dump http://google.com

```
(just dump, instead of dump_source), and see if you get anything different...


```

jb@eric:~$ w3m -dump ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/
Index of ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/
2.0.0.4/linux-i686/

[Upper Directory]
be/. . . . . . . . . Jun 13 23:50
bg/. . . . . . . . . Jun 13 23:50
ca/. . . . . . . . . Jun 13 23:50
cs/. . . . . . . . . Jun 13 23:50
da/. . . . . . . . . Jun 13 23:50
de/. . . . . . . . . Jun 13 23:50
el/. . . . . . . . . Jun 13 23:50
en-GB/ . . . . . . . Jun 13 23:50
en-US/ . . . . . . . Jun 13 23:50
es-AR/ . . . . . . . Jun 13 23:50
es-ES/ . . . . . . . Jun 13 23:50
eu/. . . . . . . . . Jun 13 23:50
fi/. . . . . . . . . Jun 13 23:50
fr/. . . . . . . . . Jun 13 23:50
ga-IE/ . . . . . . . Jun 13 23:50
hu/. . . . . . . . . Jun 13 23:50
it/. . . . . . . . . Jun 13 23:50
ja/. . . . . . . . . Jun 13 23:50
ko/. . . . . . . . . Jun 13 23:50
lt/. . . . . . . . . Jun 13 23:50
mk/. . . . . . . . . Jun 13 23:50
nb-NO/ . . . . . . . Jun 13 23:50
nl/. . . . . . . . . Jun 13 23:50
nn-NO/ . . . . . . . Jun 13 23:50
pa-IN/ . . . . . . . Jun 13 23:50
pl/. . . . . . . . . Jun 13 23:50
pt-BR/ . . . . . . . Jun 13 23:50
pt-PT/ . . . . . . . Jun 13 23:50
ru/. . . . . . . . . Jun 13 23:50
sk/. . . . . . . . . Jun 13 23:50
sl/. . . . . . . . . Jun 13 23:50
sv-SE/ . . . . . . . Jun 13 23:50
tr/. . . . . . . . . Jun 13 23:50
xpi/ . . . . . . . . Jun 13 13:23
zh-CN/ . . . . . . . Jun 13 23:50
zh-TW/ . . . . . . . Jun 13 23:50

jb@eric:~$ 

```

```
jb@eric:~$ w3m -dump http://google.com
Received cookie: PREF=ID=8502109fa5852940:TM=1181928794:LM=1181928794:S=COPeljF8iJK0wVSV
This cookie was rejected to prevent security violation. [RFC 2109 4.3.2 rule 3]
Received cookie: PREF=ID=dc42d0ec888c3b5d:TM=1181928794:LM=1181928794:S=d9wODlmWzk6a2CnY
Received cookie: PREF=ID=ad667e2ffc35a820:TM=1181928794:LM=1181928794:S=ubha6RAOe0BXNFlA
                                                              iGoogle | Sign in

                                    Google


 Web    Images    News    MapsNew!    Products    Groups    Scholar    more »

             [                                                       ]   Advanced
                        [Google Search][I'm Feeling Lucky]             Search
                                                                         Preferences
                                                                         Language
                                                                       Tools
                     Search: (*) the web ( ) pages from the UK


 Advertising Programmes - Business Solutions - About Google - Go to Google.com

                                 ©2007 Google

jb@eric:~$ 
```

Also both pages showed up with following code.

> **nanotube said:**
> also, try just
Code:

w3m [ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/](ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/)
w3m [http://google.com](http://google.com)

and see if the page shows up.


Weird huh?

Not sure if I've _deliberately_ altered anything from default, but as I'm new at this I've used quite a few scripts and other peoples' templates to personalise my user environment, so who knows what I've done! LOL

I was surprised that awk was set at gawk and not mawk as this would seem to be the default, no? So who knows!
Once again thank you very much for your help & feedback.

I'm more than happy to explore this problem further if you think it might help in any way, however I don't want to waste your time unecessarily. 
I'll check back in tomorrow. 
TTFN

---

### Post by nanotube on 2007-06-15
wow, that /is/ weird. so, -dump works fine, but -dump_source doesn't do it eh... what a conundrum, i must say!

well, at least this gives me some ideas for what to do in the future. for one, i think i will use -dump instead of -dump_source, because its output is easier to handle, anyway. i don't know why i didn't use it in the first place!

please let me know if you figure out why w3m -dump works and w3m -dump_source does not... i'd be mighty interested. :) but i myself am quite stumped for now. 

thanks for putting up with all this prodding and testing! :)

---

### Post by jb5 on 2007-06-16
Hi Nanotube -
I thought I'd have another look at some of the issues I was having with w3m.
Typing :-
```

w3m -dump_source ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/

```
yeilded zip, as seen yesterday.
So then I tried
```

jb@eric:~$ sudo w3m -dump_source ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/
<html>
<head>
<base href="ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/">
<title>ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/</title>
</head>
<body>
<h1>Index of ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/</h1>
<pre>
<a href="..">[Upper Directory]</a>
<a href="be/">be/</a>. . . . . . . . . Jun 13 23:50       
<a href="bg/">bg/</a>. . . . . . . . . Jun 13 23:50       
<a href="ca/">ca/</a>. . . . . . . . . Jun 13 23:50       
<a href="cs/">cs/</a>. . . . . . . . . Jun 13 23:50       
<a href="da/">da/</a>. . . . . . . . . Jun 13 23:50       
<a href="de/">de/</a>. . . . . . . . . Jun 13 23:50       
<a href="el/">el/</a>. . . . . . . . . Jun 13 23:50       
<a href="en-GB/">en-GB/</a> . . . . . . . Jun 13 23:50       
<a href="en-US/">en-US/</a> . . . . . . . Jun 13 23:50       
<a href="es-AR/">es-AR/</a> . . . . . . . Jun 13 23:50       
<a href="es-ES/">es-ES/</a> . . . . . . . Jun 13 23:50       
<a href="eu/">eu/</a>. . . . . . . . . Jun 13 23:50       
<a href="fi/">fi/</a>. . . . . . . . . Jun 13 23:50       
<a href="fr/">fr/</a>. . . . . . . . . Jun 13 23:50       
<a href="ga-IE/">ga-IE/</a> . . . . . . . Jun 13 23:50       
<a href="hu/">hu/</a>. . . . . . . . . Jun 13 23:50       
<a href="it/">it/</a>. . . . . . . . . Jun 13 23:50       
<a href="ja/">ja/</a>. . . . . . . . . Jun 13 23:50       
<a href="ko/">ko/</a>. . . . . . . . . Jun 13 23:50       
<a href="lt/">lt/</a>. . . . . . . . . Jun 13 23:50       
<a href="mk/">mk/</a>. . . . . . . . . Jun 13 23:50       
<a href="nb-NO/">nb-NO/</a> . . . . . . . Jun 13 23:50       
<a href="nl/">nl/</a>. . . . . . . . . Jun 13 23:50       
<a href="nn-NO/">nn-NO/</a> . . . . . . . Jun 13 23:50       
<a href="pa-IN/">pa-IN/</a> . . . . . . . Jun 13 23:50       
<a href="pl/">pl/</a>. . . . . . . . . Jun 13 23:50       
<a href="pt-BR/">pt-BR/</a> . . . . . . . Jun 13 23:50       
<a href="pt-PT/">pt-PT/</a> . . . . . . . Jun 13 23:50       
<a href="ru/">ru/</a>. . . . . . . . . Jun 13 23:50       
<a href="sk/">sk/</a>. . . . . . . . . Jun 13 23:50       
<a href="sl/">sl/</a>. . . . . . . . . Jun 13 23:50       
<a href="sv-SE/">sv-SE/</a> . . . . . . . Jun 13 23:50       
<a href="tr/">tr/</a>. . . . . . . . . Jun 13 23:50       
<a href="xpi/">xpi/</a> . . . . . . . . Jun 13 13:23       
<a href="zh-CN/">zh-CN/</a> . . . . . . . Jun 13 23:50       
<a href="zh-TW/">zh-TW/</a> . . . . . . . Jun 13 23:50       
</pre>
</body>
</html>
jb@eric:~$ 

```
so far so usual, (for me anyway!) ;)

Looking  in my home directory, I noticed :-
```

jb@eric:~$ ls -Al
total 11432

---------cut---------------
drwx------  2 root root     4096 2007-06-16 11:44 .w3m
---------cut---------------

jb@eric:~$ 

```

Hmmmm..... So I removed .w3m

```

sudo rm -r .w3m

```

Now when I run :-
```

jb@eric:~$ w3m -dump_source ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/
<html>
<head>
<base href="ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/">
<title>ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/</title>
</head>
<body>
<h1>Index of ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/</h1>
<pre>
<a href="..">[Upper Directory]</a>
<a href="be/">be/</a>. . . . . . . . . Jun 13 23:50       
<a href="bg/">bg/</a>. . . . . . . . . Jun 13 23:50       
<a href="ca/">ca/</a>. . . . . . . . . Jun 13 23:50       
<a href="cs/">cs/</a>. . . . . . . . . Jun 13 23:50       
<a href="da/">da/</a>. . . . . . . . . Jun 13 23:50       
<a href="de/">de/</a>. . . . . . . . . Jun 13 23:50       
<a href="el/">el/</a>. . . . . . . . . Jun 13 23:50       
<a href="en-GB/">en-GB/</a> . . . . . . . Jun 13 23:50       
<a href="en-US/">en-US/</a> . . . . . . . Jun 13 23:50       
<a href="es-AR/">es-AR/</a> . . . . . . . Jun 13 23:50       
<a href="es-ES/">es-ES/</a> . . . . . . . Jun 13 23:50       
<a href="eu/">eu/</a>. . . . . . . . . Jun 13 23:50       
<a href="fi/">fi/</a>. . . . . . . . . Jun 13 23:50       
<a href="fr/">fr/</a>. . . . . . . . . Jun 13 23:50       
<a href="ga-IE/">ga-IE/</a> . . . . . . . Jun 13 23:50       
<a href="hu/">hu/</a>. . . . . . . . . Jun 13 23:50       
<a href="it/">it/</a>. . . . . . . . . Jun 13 23:50       
<a href="ja/">ja/</a>. . . . . . . . . Jun 13 23:50       
<a href="ko/">ko/</a>. . . . . . . . . Jun 13 23:50       
<a href="lt/">lt/</a>. . . . . . . . . Jun 13 23:50       
<a href="mk/">mk/</a>. . . . . . . . . Jun 13 23:50       
<a href="nb-NO/">nb-NO/</a> . . . . . . . Jun 13 23:50       
<a href="nl/">nl/</a>. . . . . . . . . Jun 13 23:50       
<a href="nn-NO/">nn-NO/</a> . . . . . . . Jun 13 23:50       
<a href="pa-IN/">pa-IN/</a> . . . . . . . Jun 13 23:50       
<a href="pl/">pl/</a>. . . . . . . . . Jun 13 23:50       
<a href="pt-BR/">pt-BR/</a> . . . . . . . Jun 13 23:50       
<a href="pt-PT/">pt-PT/</a> . . . . . . . Jun 13 23:50       
<a href="ru/">ru/</a>. . . . . . . . . Jun 13 23:50       
<a href="sk/">sk/</a>. . . . . . . . . Jun 13 23:50       
<a href="sl/">sl/</a>. . . . . . . . . Jun 13 23:50       
<a href="sv-SE/">sv-SE/</a> . . . . . . . Jun 13 23:50       
<a href="tr/">tr/</a>. . . . . . . . . Jun 13 23:50       
<a href="xpi/">xpi/</a> . . . . . . . . Jun 13 13:23       
<a href="zh-CN/">zh-CN/</a> . . . . . . . Jun 13 23:50       
<a href="zh-TW/">zh-TW/</a> . . . . . . . Jun 13 23:50       
</pre>
</body>
</html>
jb@eric:~$ 

```

and 

```

jb@eric:~$ ls -Al
total 516
--------------------------------cut----------------------------------
drwx------  2 jb   jb     4096 2007-06-16 13:29 .w3m
--------------------------------cut----------------------------------

jb@eric:~$ 

```

Okay! The desired OP and ownership of .w3m! 

I'm guessing that w3m was given root ownership when I first ran :- 
```

sudo bash ~/DATA/Scripts/installnewthunderbird.sh -install

```

I'm not quite sure why I ran it as root? Maybe I'd needed to run another script as root previously? (& then - monkey see, monkey do! LOL). 
Maybe the first install failed with the gpg key error, so I tried running as root and then the next time I installed UBUNTU I had gotten into the habit of running as root by then? Who Knows?

-----------------------------------------------------------
BTW, the gpg key problem was solved by following the code you suggested at the end of this [[COLOR="Blue"]thread[/COLOR]](http://ubuntuforums.org/showthread.php?p=2816092) i.e.
```

sudo chown yourusername:yourusername ~/.gnupg
chmod 700 ~/.gnupg
chmod 600 ~/.gnupg/*

```
-----------------------------------------------------------

Anyhow, that is why w3m -dump-source only worked as root for me.
(It still doesn't answer WHY 
```

w3m -dump ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/


```
works as user and 
```

w3m -dump-source ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/

```
doesn't, when the .w3m directory is owned by root, but it may get someone closer to an answer?)

I'm not even sure what the purpose of the .w3m directory serves as it appears to be empty?!
```

jb@eric:~$ cd .w3m
jb@eric:~/.w3m$ ls -Al
total 0
jb@eric:~/.w3m$ 

```

Anyway to try and bring this post to a point!!!!!!!!

The python script now works for me as user, though I guess I still need to get to the bottom of why the awk default was set as gawk for me!, but :-
```

jb@eric:~$ python ~/Desktop/ubuntuzilla.py -a install -p thunderbird

Welcome to the Ubuntuzilla Thunderbird script version 4.0.1

This script installs the latest release of the official Mozilla build of Thunderbird on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla 


Retrieving the version of the latest release of Thunderbird from the Mozilla website...
The most recent release of Thunderbird is detected to be 2.0.0.4. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.com/) Is it correct [y/n]? 
Please enter 'y' or 'n': y
Please choose the localization (language) for Thunderbird. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla for steps you can take to resolve this problem.]
  0. be           1. bg           2. ca           3. cs        
  4. da           5. de           6. el           7. en-GB     
  8. en-US        9. es-AR       10. es-ES       11. eu        
 12. fi          13. fr          14. ga-IE       15. hu        
 16. it          17. ja          18. ko          19. lt        
 20. mk          21. nb-NO       22. nl          23. nn-NO     
 24. pa-IN       25. pl          26. pt-BR       27. pt-PT     
 28. ru          29. sk          30. sl          31. sv-SE     
 32. tr          33. zh-CN       34. zh-TW     
Enter your choice of localization (integer, from 0 to 34): 7
You have chosen localization en-GB. Is that correct [y/n]? 
Please enter 'y' or 'n': y
Get: 1 http://archive.ubuntu.com feisty-backports Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_GB
Get: 2 http://security.ubuntu.com feisty-security Release.gpg [191B]                                                                            
Ign http://security.ubuntu.com feisty-security/main Translation-en_GB                                                                           
Get: 3 http://gb.archive.ubuntu.com feisty Release.gpg [191B]                              
Hit http://gb.archive.ubuntu.com feisty/main Translation-en_GB                                                          
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_GB                
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_GB                  
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_GB                
Get: 4 http://archive.ubuntu.com feisty-updates Release.gpg [191B]                         
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_GB                    
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_GB                  
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_GB                
Ign http://security.ubuntu.com feisty-security/universe Translation-en_GB                  
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_GB
Get: 5 http://archive.canonical.com feisty-commercial Release.gpg [191B]
Ign http://archive.canonical.com feisty-commercial/main Translation-en_GB                  
Ign http://gb.archive.ubuntu.com feisty/restricted Translation-en_GB                       
Ign http://gb.archive.ubuntu.com feisty/universe Translation-en_GB   
Hit http://gb.archive.ubuntu.com feisty/multiverse Translation-en_GB 
Get: 6 http://gb.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://gb.archive.ubuntu.com feisty-updates/main Translation-en_GB                            
Ign http://gb.archive.ubuntu.com feisty-updates/restricted Translation-en_GB
Get: 7 http://archive.ubuntu.com feisty-security Release.gpg [191B]  
Ign http://archive.ubuntu.com feisty-security/main Translation-en_GB 
Ign http://archive.ubuntu.com feisty-security/restricted Translation-en_GB
Ign http://archive.ubuntu.com feisty-security/universe Translation-en_GB                                         
Hit http://security.ubuntu.com feisty-security Release                                                           
Hit http://gb.archive.ubuntu.com feisty Release                                                                  
Ign http://archive.ubuntu.com feisty-security/multiverse Translation-en_GB                 
Hit http://archive.ubuntu.com feisty-backports Release                                                           
Hit http://archive.ubuntu.com feisty-updates Release                                                             
Hit http://archive.canonical.com feisty-commercial Release                                                       
Get: 8 http://www.getautomatix.com feisty Release.gpg [189B]                                                     
Ign http://www.getautomatix.com feisty/main Translation-en_GB                                                   
Hit http://gb.archive.ubuntu.com feisty-updates Release                                                         
Hit http://security.ubuntu.com feisty-security/main Packages                                                    
Hit http://archive.ubuntu.com feisty-security Release                                                           
Hit http://gb.archive.ubuntu.com feisty/main Packages                                                                                 
Hit http://gb.archive.ubuntu.com feisty/restricted Packages                                                      
Hit http://gb.archive.ubuntu.com feisty/main Sources                                                             
Hit http://security.ubuntu.com feisty-security/restricted Packages                                               
Hit http://security.ubuntu.com feisty-security/main Sources                                                      
Hit http://security.ubuntu.com feisty-security/restricted Sources                                                
Hit http://www.getautomatix.com feisty Release                                                                   
Hit http://archive.ubuntu.com feisty-backports/main Packages                                                     
Hit http://archive.ubuntu.com feisty-backports/restricted Packages                                               
Hit http://archive.ubuntu.com feisty-backports/universe Packages                                                 
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages                                               
Hit http://gb.archive.ubuntu.com feisty/restricted Sources                                                       
Hit http://gb.archive.ubuntu.com feisty/universe Packages                                                        
Hit http://gb.archive.ubuntu.com feisty/universe Sources                                                         
Hit http://gb.archive.ubuntu.com feisty/multiverse Packages                                                      
Hit http://gb.archive.ubuntu.com feisty/multiverse Sources                                                       
Hit http://security.ubuntu.com feisty-security/universe Packages                                                 
Hit http://security.ubuntu.com feisty-security/universe Sources                                                  
Hit http://security.ubuntu.com feisty-security/multiverse Packages                                               
Hit http://security.ubuntu.com feisty-security/multiverse Sources                                                
Hit http://archive.canonical.com feisty-commercial/main Packages                                                 
Hit http://gb.archive.ubuntu.com feisty-updates/main Packages                              
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Packages  
Hit http://gb.archive.ubuntu.com feisty-updates/main Sources         
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Sources   
Hit http://www.getautomatix.com feisty/main Packages                 
Hit http://archive.ubuntu.com feisty-updates/universe Packages
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://archive.ubuntu.com feisty-security/main Packages
Hit http://archive.ubuntu.com feisty-security/restricted Packages
Hit http://archive.ubuntu.com feisty-security/universe Packages
Hit http://archive.ubuntu.com feisty-security/multiverse Packages
Fetched 8B in 0s (12B/s) 
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mozilla-thunderbird is already the newest version.
libstdc++5 is already the newest version.
libgtk2.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

A Thunderbird profile has been found at ~/.thunderbird. Do you want to make a backup of your Mozilla Thunderbird profile at ~/.thunderbird? Note that if you store your email there, this may take quite a bit of disk space. You may wish to check the size of that directory and the amount of free disk space before you answer this question. Make backup? [y/n]: 
Please enter 'y' or 'n': n

OK, proceeding without backup.

Downloading Thunderbird archive from the Mozilla site

--13:00:35--  ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/en-GB/thunderbird-2.0.0.4.tar.gz
           => `thunderbird-2.0.0.4.tar.gz'
Resolving releases.mozilla.org... 64.50.236.214, 204.152.184.113, 130.239.18.158, ...
Connecting to releases.mozilla.org|64.50.236.214|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/en-GB ... done.
==> PASV ... done.    ==> RETR thunderbird-2.0.0.4.tar.gz ... done.
Length: 11,180,767 (11M) (unauthoritative)

100%[==============================================================================================================>] 11,180,767   336.01K/s    ETA 00:00

13:01:11 (322.22 KB/s) - `thunderbird-2.0.0.4.tar.gz' saved [11180767]


Downloading Thunderbird signature from the Mozilla site

--13:01:11--  ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/en-GB/thunderbird-2.0.0.4.tar.gz.asc
           => `thunderbird-2.0.0.4.tar.gz.asc'
Resolving releases.mozilla.org... 64.50.236.214, 156.56.247.196, 204.152.184.113, ...
Connecting to releases.mozilla.org|64.50.236.214|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/en-GB ... done.
==> PASV ... done.    ==> RETR thunderbird-2.0.0.4.tar.gz.asc ... done.
Length: 186 (unauthoritative)

100%[==============================================================================================================>] 186           --.--K/s             

13:01:13 (265.01 KB/s) - `thunderbird-2.0.0.4.tar.gz.asc' saved [186]


Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: requesting key 0E3606D9 from hkp server subkeys.pgp.net
gpg: key 0E3606D9: "Mozilla Software Releases <releases@mozilla.org>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
Successfully retrieved Mozilla Software Releases Public key from subkeys.pgp.net .


Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Thu 14 Jun 2007 00:50:37 BST using DSA key ID 0E3606D9
gpg: Good signature from "Mozilla Software Releases <releases@mozilla.org>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: F57F 372A 8C6D 4F55 72DE  C9B9 696E 3431 0E36 06D9

Linking launcher to new thunderbird

Leaving `local diversion of /usr/bin/mozilla-thunderbird to /usr/bin/mozilla-thunderbird.ubuntu'

The new Thunderbird version 2.0.0.4 has been installed successfully. Thank you for using Ubuntuzilla scripts.
jb@eric:~$ 

```
\\:D/\\:D/\\:D/

Phew! Well I've certainly learned a lot, and that is NEVER a bad thing. 
It appears that 
```

w3m -dump ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/

```
yeilds more easily manipulated data for your program as well, so hopefully not a COMPLETE waste of time for you either. :biggrin:

Thank you again.

:)

---

### Post by nanotube on 2007-06-16
wow, thanks for tracking that down! that was a good piece of work there! really good! :) :popcorn:

---

