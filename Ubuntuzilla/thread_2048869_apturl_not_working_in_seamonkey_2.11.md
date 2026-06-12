---
title: "apturl:// not working in seamonkey 2.11"
date: 2012-08-27
forum: Ubuntuzilla
---

### Post by dwb814 on 2012-08-27
Hi,
I need a little help here, apturl:// isn't working in seamonkey 2.11. I reinstalled apturl_0.5.1ubuntu3_i386 & apturl-common_0.5.1ubuntu3_i386 and added this to about:config

Enter *about:config* in the URL bar and add : 

[LIST]
[*]**network.protocol-handler.app.apt** in character chain with **/usr/bin/apturl** as value,
[*]**network.protocol-handler.app.apt+http** in character chain with **/usr/bin/apturl** as value,
[*]**network.protocol-handler.warn-external.apt** in boolean value and put **true** as value,
[*]**network.protocol-handler.warn-external.apt+http** in boolean value and put **true** as value.
[/LIST]
from [https://help.ubuntu.com/community/AptURL](https://help.ubuntu.com/community/AptURL)


But it's still not working. Any advise would be appreciated.

BTW, I'm running Ubuntu 12.04.1 LTS and here's the error when I click on an apt: link

[ATTACH]223247[/ATTACH]

---

### Post by nanotube on 2012-08-28
just in case: you know it's supposed to be apt:// not apturl:// right? you made your own apturl:// link and it didn't work, that's why. 

if the apt:// links don't work either, then that's a different story... but wanted to check on this first.

---

### Post by nanotube on 2012-08-28
ok, i just tried it myself. the instructions on the ubuntu wiki AptURL page seem to be outdated, and do not work. The mozilla wiki comes to the rescue:

[http://kb.mozillazine.org/Register_protocol#Firefox_3.5_and_above](http://kb.mozillazine.org/Register_protocol#Firefox_3.5_and_above)

follow these instructions, just replace 'foo' with 'apt', and you will be good to go.

EDIT: i just updated the outdated ubuntu wiki page for apturl.

---

### Post by dwb814 on 2012-08-28
> **nanotube said:**
> ok, i just tried it myself. the instructions on the ubuntu wiki AptURL page seem to be outdated, and do not work. The mozilla wiki comes to the rescue:

[http://kb.mozillazine.org/Register_protocol#Firefox_3.5_and_above](http://kb.mozillazine.org/Register_protocol#Firefox_3.5_and_above)

follow these instructions, just replace 'foo' with 'apt', and you will be good to go.

EDIT: i just updated the outdated ubuntu wiki page for apturl.


[nanotube]("http://ubuntuforums.org/member.php?u=66474"),
Thank you sir, I'm good to go now. I appreciate your kind assistance and expediency. :D

---

### Post by nanotube on 2012-08-28
> **dwb814 said:**
> [nanotube]("http://ubuntuforums.org/member.php?u=66474"),
Thank you sir, I'm good to go now. I appreciate your kind assistance and expediency. :D

You're quite welcome. :)

---

