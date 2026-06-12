---
title: "Firefox RC2 Install Script"
date: 2006-10-09
forum: The Cafe
---

### Post by avihappy on 2006-10-09
I made a small install script for firefox RC2. It is a modified version of Visvak's script  [here]("http://everythingelse.wordpress.com/2006/07/15/howto-install-firefox-20-bon-echo-in-ubuntu/").
Enjoy. PS i did not know where to put this thread, move if needed:) !
Note: you make need to give it executable ability.

I DONT KNOW HOW UPDATING WILL BE AFFECTED

If you can make an uninstall script, please do so.

UNINSTALL SCRIPT BELOW

DO NOT DOWNLOAD, SECURITY RISK YOU CANNOT UPDATE

---

### Post by GStubbs43 on 2006-10-09
[http://www.ubuntuforums.org/showthread.php?t=248158&highlight=howto+firefox+2](http://www.ubuntuforums.org/showthread.php?t=248158&highlight=howto+firefox+2)
Is that basically the same thing?

---

### Post by avihappy on 2006-10-09
> **GStubbs43 said:**
> [http://www.ubuntuforums.org/showthread.php?t=248158&highlight=howto+firefox+2](http://www.ubuntuforums.org/showthread.php?t=248158&highlight=howto+firefox+2)
Is that basically the same thing?

No this is RC2 not Beta 2

---

### Post by GStubbs43 on 2006-10-09
Oh, woops, I didn't see that... I'll try it out in a second, even though I use Iceweasel instead...

---

### Post by JcZndeR on 2006-10-09
Thanks!
seems to work great on my computer
doesnt fix the fact that i cant run firfox on my main account but thats another problem
;) 
ite perfect on my alternate account
good well done!

---

### Post by GStubbs43 on 2006-10-09
Worked great, all plugins and settings etc. stayed... Great job!

---

### Post by Joey French on 2006-10-09
Works well, just installed on a fresh Edgy install, left everything intact.

---

### Post by fuscia on 2006-10-09
thanks. worked great.

---

### Post by IYY on 2006-10-09
Awesome script, but I don't think I like the new Firefox...

[LIST]
[*]The new UI is much slower and less responsive on my 1.4 GHz machine.
[*]The new UI might look good on a Vista or KDE system, but with a warm theme like Gillouche or Human, it looks horribly out of place. Same goes for the icons. What was wrong with the beautiful Tango-ish icons we had in the old version (in fact, Tango was inspired by them)?
[*] The new 'close tab' icon wastes space and makes it incredibly easy to close tabs by mistake. What was wrong with middle click? Who has a two-button mouse these days? And even if you do, just click both buttons at once!
[/LIST]

Seems like they're copying Opera and IE when it comes to the UI, and I don't like it in the least bit. IceWeasel is where my hopes lie ;)

---

### Post by fungi on 2006-10-10
Boo hoo, seg fault.

I get a few of these, probably because i have a pile of other crap installed :-k 
```

gamera@sakura:~/temp$ firefox
/opt/firefox/run-mozilla.sh: line 131: 21787 Segmentation fault      "$prog" ${1+"$@"}

gamera@sakura:~/temp$ sudo /opt/firefox/run-mozilla.sh

run-mozilla.sh: Cannot execute .

gamera@sakura:~/temp$

```
**Edit:** Seems to run fine under fresh account (Linux user, not Mozilla Pofile)

---

### Post by aysiu on 2006-10-10
I agree with IYY's complaints about the close tab buttons. I know a lot of people consider that a feature, but I consider it an annoyance, and I'm glad we'll always have Firefox extensions to undo the default behaviors we don't like.

For me, it's not a matter of wasted space but a matter of convenience. With the old Firefox, I knew I could always click in one place (the top-right corner) to close the active tab. Of course, most of the time I just use Control-W, and I rarely close inactive tabs.

In any case, what's done is done. If they want to head in the direction of Opera... so be it.

---

### Post by avihappy on 2006-10-10
> **fungi said:**
> Boo hoo, seg fault.

I get a few of these, probably because i have a pile of other crap installed :-k 

gamera@sakura:~/temp$ firefox
/opt/firefox/run-mozilla.sh: line 131: 21787 Segmentation fault      "$prog" ${1+"$@"}

gamera@sakura:~/temp$ sudo /opt/firefox/run-mozilla.sh

run-mozilla.sh: Cannot execute .

gamera@sakura:~/temp$

Hmm,I dont know. Maybe someone can help you. I can't replicate it OR see a script problem, but firefox can't start due to a problem in run-mozilla.sh, try asking in the firefox forums.

Hey aysiu, i like your "The Linux Desktop Myth". And the lack of buttons was a common critisism of FF, so they added it. Guess most people don't try middle clicking ;)

---

### Post by visvak on 2006-10-11
I've updated the script to install RC2 instead of Beta 2, could someone try it and tell if there are any probs ??

---

### Post by bruce89 on 2006-10-11
> **Joey French said:**
> Works well, just installed on a fresh Edgy install, left everything intact.

Edgy now has Fx 2.0rc2 anyway:

> firefox (1.99+2.0rc2+dfsg-0ubuntu1) edgy; urgency=low

  * New upstream version 2.0rc2.
  * Fix/workaround for epiphany GtkSocket lifetype crash:
    apply patch id=241087 from Mozilla Bugzilla #241535 to fix LP #63814.
  * Change application name to `Firefox', as requested by mdz.
    Files changed:
      - browser/locales/en-US/chrome/branding/brand.dtd
      - browser/locales/en-US/chrome/branding/brand.properties;
    New values:
      - brandShortName and brandFullName: `Bon Echo' => `Firefox'
      - vendorShortName: `Mozilla' => `Ubuntu'
  * Make preferences dialogue fit again (bah!).

 -- Ian Jackson <iwj@ubuntu.com>   Tue, 10 Oct 2006 18:49:32 +0100 

---

### Post by aysiu on 2006-10-11
> **avihappy said:**
> 
Hey aysiu, i like your "The Linux Desktop Myth". Thanks. It took me a while to write. > And the lack of buttons was a common critisism of FF, so they added it. Guess most people don't try middle clicking ;) Yes, I know--I'm definitely fighting a losing battle on that. As long as I have extensions to fix it, it's no big deal.

---

### Post by TrendyDark on 2006-10-11
Worked very well, thanks a million! :)

> **aysiu said:**
> I agree with IYY's complaints about the close tab buttons. I know a lot of people consider that a feature, but I consider it an annoyance, and I'm glad we'll always have Firefox extensions to undo the default behaviors we don't like.

For me, it's not a matter of wasted space but a matter of convenience. With the old Firefox, I knew I could always click in one place (the top-right corner) to close the active tab. Of course, most of the time I just use Control-W, and I rarely close inactive tabs.

In any case, what's done is done. If they want to head in the direction of Opera... so be it.

I actually like the placement of the close button in the new Firefox. In other versions of Firefox I would often close the wrong tab on accident, because they all had the same universal close button.

---

### Post by aysiu on 2006-10-11
Apparently, I'm in the minority on the close tab button.

---

