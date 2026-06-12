---
title: "Ubuntu soars!"
date: 2005-02-02
forum: The Cafe
---

### Post by HiddenWolf on 2005-02-02
Distrowatch.cz:
6 month average:   860 h/p/d
3 month average: 1143 h/p/d
1 month average: 1584 h/p/d

For those who follow it, our one month average hits per day on the distrowatch 'ubuntu-page' is now the highest of any distro. Topping mandrakesoft, suse, mepis and fedora.

It's getting big. Fast.

---

### Post by Randabis on 2005-02-02
[QUOTE=HiddenWolf]Distrowatch.cz:
6 month average:   860 h/p/d
3 month average: 1143 h/p/d
1 month average: 1584 h/p/d

For those who follow it, our one month average hits per day on the distrowatch 'ubuntu-page' is now the highest of any distro. Topping mandrakesoft, suse, mepis and fedora.

It's getting big. Fast.[/QUOTE]
 With good reason too. :) Just wait until Hoary is released. It's gonna get a HUGE boost. :P

---

### Post by HiddenWolf on 2005-02-02
[QUOTE=Randabis]With good reason too. :) Just wait until Hoary is released. It's gonna get a HUGE boost. :P[/QUOTE]

Considering how 'rough' warty is compared to hoary, hell yeah!
For safety reasons I'm on warty right now, but I want to go back all the time.

---

### Post by ctt1wbw on 2005-02-02
Question about Hoary...  is that going to be available as an apt-get or a whole new reinstall from cd?

---

### Post by axcairns on 2005-02-02
[QUOTE=ctt1wbw]Question about Hoary...  is that going to be available as an apt-get or a whole new reinstall from cd?[/QUOTE]
 IIRC you should be able to upgrade via apt.

Allan

---

### Post by Randabis on 2005-02-02
[QUOTE=ctt1wbw]Question about Hoary...  is that going to be available as an apt-get or a whole new reinstall from cd?[/QUOTE]
both

---

### Post by jerome bettis on 2005-02-02
i think all you have to do is go into your sources.list and replace all occurences of warty with hoary  and then do apt-get update ; apt-get upgrade ; apt-get dist-upgrade.

right?

does hoary have a new kernel?  if so how can i upgrade but keep this custom kernel i have now?  it's totally optimized, i don't want to lose it.

---

### Post by jerome bettis on 2005-02-02
screw it i'm gonna do it right now and see what happens

---

### Post by Lynx on 2005-02-02
I think it's funny how may people pass judgement so quickly on Ubuntu, when the first release surpasses many well known distros. Releasing a new one every six months, we will surpass the others quickly.

---

### Post by jerome bettis on 2005-02-02
[QUOTE=jerome bettis]screw it i'm gonna do it right now and see what happens[/QUOTE]


yep it worked!  the new kernel didn't boot (kernel panic unable to mount root fs)  not sure why, but the kernel i have was saved and i booted into that just fine.

hoary is pretty sweet so far.

---

### Post by poofyhairguy on 2005-02-02
[QUOTE=ctt1wbw]Question about Hoary...  is that going to be available as an apt-get or a whole new reinstall from cd?[/QUOTE]


You can apt-get it REAL easily if you have an untainted install. I personally am planning a clean install, if only because I used jdong's backports.

If you used those backports, upgrading is a little harder via apt.

---

### Post by HiddenWolf on 2005-02-02
[QUOTE=poofyhairguy]You can apt-get it REAL easily if you have an untainted install. I personally am planning a clean install, if only because I used jdong's backports.

If you used those backports, upgrading is a little harder via apt.[/QUOTE]
Yeah, it is.

---

### Post by rapala61 on 2005-02-03
[QUOTE=poofyhairguy]You can apt-get it REAL easily if you have an untainted install. I personally am planning a clean install, if only because I used jdong's backports.

If you used those backports, upgrading is a little harder via apt.[/QUOTE]


untainted would be like a installation with the default packages and default conf??.. because , im having problems every time i try to upgrade to hoary... and the first thing i do when i install warty is tweak it  a bit.. but install quite a few more packages from marillat , universe , multiverse.. so dont know if this has some connection with the  unstable upgrades im experiencing....

---

### Post by poofyhairguy on 2005-02-03
[QUOTE=rapala61]untainted would be like a installation with the default packages and default conf??.. [/QUOTE]

yep

[QUOTE=rapala61]because , im having problems every time i try to upgrade to hoary... and the first thing i do when i install warty is tweak it  a bit.. but install quite a few more packages from marillat , universe , multiverse.. so dont know if this has some connection with the  unstable upgrades im experiencing....[/QUOTE]

I didn't see backports in your list- thats the big one.


But who knows, that stuff is unsupported, it is probably the trouble.

---

