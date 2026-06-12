---
title: "Gnome3 at login Abiword always starts"
date: 2015-03-10
forum: Ubuntu Development Version
---

### Post by 65 mustang on 2015-03-10
When I login to a Gnome3 session Abiword always starts even though i have checked and it is not listed in "gnome-session-properties".  I cant tell if this is a bug in 15.04 or just a misconfiguration on my machine.

---

### Post by ajgreeny on 2015-03-10
Have a look in ~/.cache/sessions and if there are lots of session files delete them and try again.

I do not know gnome 3 but check that when you shutdown it is not configured to remember the session and use it next time.

---

### Post by 65 mustang on 2015-03-11
> **ajgreeny said:**
> Have a look in ~/.cache/sessions and if there are lots of session files delete them and try again.

I do not know gnome 3 but check that when you shutdown it is not configured to remember the session and use it next time.

This did not stop it from autolaunching.

---

### Post by wgarcia on 2015-03-12
Same thing happened to me, and using Unity and not Gnome. Since I was not using abiword I just unistalled and it was gone, but I couldn't figure out what was causing it, it was not in the list of applications autostart.

---

### Post by kansasnoob on 2015-03-27
Just noticed this myself and found an existing bug report:

[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1432271](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1432271)

---

### Post by orj-gmail on 2015-03-30
didn't get fixed till now

---

### Post by ventrical on 2015-04-01
This has got to be the best gnome3-shell yet. :) haven't had , nor do I have that problem. I have nurtured this install from very begining  and there have not been hardly any problmes with exception of nVidia proprietary  but nouveau suffices excellently.

Regards..

---

### Post by kansasnoob on 2015-04-01
> **ventrical said:**
> This has got to be the best gnome3-shell yet. :) haven't had , nor do I have that problem. I have nurtured this install from very begining  and there have not been hardly any problmes with exception of nVidia proprietary  but nouveau suffices excellently.

Regards..

Do you have Abiword installed? It's not by default, but I started using Abiword clear back around the Win ME and Lindows era ............... imagine going back to dial-up :eek:

Anyway none of the other word processors are able to read or convert all those years of Abiword docs so I need it. I need to cross-check with Lubuntu since it's one of their default apps, but I haven't been able to install Lubuntu lately.

---

### Post by kansasnoob on 2015-04-01
It doesn't auto-launch in Ubuntu Mate, but it displays an ugly black border which I don't get in either Ubuntu or Ubuntu GNOME.

---

### Post by ventrical on 2015-04-01
> **kansasnoob said:**
> Do you have Abiword installed? It's not by default, but I started using Abiword clear back around the Win ME and Lindows era ............... imagine going back to dial-up :eek:

Anyway none of the other word processors are able to read or convert all those years of Abiword docs so I need it. I need to cross-check with Lubuntu since it's one of their default apps, but I haven't been able to install Lubuntu lately.

No , not on ubuntu unity but I think it is by default on lubuntu and xubuntu and I do not have those problems there either.

'dial-up'

Those were the days ! :) I had two lines, 2 BBSes and everything was free, (FIDO NET and WWIV and any other network with a modem).

 ahhh .. sigh ... but onwards and upwards.. :)


edit... libre' usually reads most anything from old win95 .

Regards..

---

### Post by kansasnoob on 2015-04-01
> edit... libre' usually reads most anything from old win95 .

Just tried and you're right! That's good to know :guitar:

---

### Post by ventrical on 2015-04-02
But abiword is more .. ummm .. as one might say..  more compact and faster loading .. so I can see why people would prefer it over OO.

---

### Post by kansasnoob on 2015-04-02
> **ventrical said:**
> But abiword is more .. ummm .. as one might say..  more compact and faster loading .. so I can see why people would prefer it over OO.

And there's always the familiarity factor. When you've used something for about 15 years it's hard to change.

---

### Post by ventrical on 2015-04-09
I downloaded the xubuntu-desktop on top of ubuntu-desktop so as to run in virtual terminals concurrently. Of course xubuntu brings in abiword and so now , when logging in to unity desktop, abiword auto starts.

Just fyi.

Regards..

---

### Post by zika on 2015-04-10
> **ventrical said:**
> I downloaded the xubuntu-desktop on top of ubuntu-desktop so as to run in virtual terminals concurrently. Of course xubuntu brings in abiword and so now , when logging in to unity desktop, abiword auto starts.
Just fyi.
Regards..Which makes it even simpler (if possible) to find a reason/file that makes this behaviour occuring.

---

