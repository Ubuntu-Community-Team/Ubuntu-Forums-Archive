---
title: "Thin client using Linux"
date: 2012-04-11
forum: Server Platforms
---

### Post by gshreya3 on 2012-04-11
Hello All

We are using Ncomputing L230 thin clients. Is there any thin client package directly available for linux?
Will any other solution become helpful to improve system performance?

[COLOR=#1F497D][FONT=&quot]I’m told that Linux has provided for remote access unlike window.[/FONT][/COLOR]
[COLOR=#1F497D][FONT=&quot]If that is the case, can we use it without ncomputing box?

[/FONT][/COLOR]Please reply at your earliest.

Thanks in advance...

---

### Post by gshreya3 on 2012-04-11
please visit the link [http://www2.userful.com/products/userful-multiseat-linux](http://www2.userful.com/products/userful-multiseat-linux)

---

### Post by Lars Noodén on 2012-04-11
You'll want to read up on LTSP (Linux Terminal Server Project)

[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)
[http://www.ltsp.org/](http://www.ltsp.org/)

Using LTSP, you'll be able to run the workstations as thin clients.  There is also a lot of material, though somewhat hard to find, out on the net for LTSP and related projects like K12-LTSP.

gshreya3's link above to the Userful page is interesting in that it is [multiseat](http://www.linuxtoys.org/multiseat/multiseat.html) which is quite useful in reducing noise, power consumption and hardware.  It can be combined with LTSP.  It is done by modifying Xorg's configuration.

---

