---
title: "64-Bit Flash plugin is here!"
date: 2008-12-01
forum: The Cafe
---

### Post by tuxxy on 2008-12-01
Couldnt find a similar thread so decided to make one because an alpha version of 64-bit Adobe Flash Player 10 for Linux operating systems was released on 11/17/2008. Flash Player 10 beta for Solaris was released on 9/26/2008.

The plugin download is [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz") and it runs great!

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by xebian on 2008-12-01
> **tuxxy said:**
> Couldnt find a similar thread so decided to make one because an alpha version of 64-bit Adobe Flash Player 10 for Linux operating systems was released on 11/17/2008. Flash Player 10 beta for Solaris was released on 9/26/2008.

The plugin download is [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz") and it runs great!

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

They keep removing it because they think it's not a support request.

---

### Post by Kilz on 2008-12-01
> **tuxxy said:**
> Couldnt find a similar thread so decided to make one because an alpha version of 64-bit Adobe Flash Player 10 for Linux operating systems was released on 11/17/2008. Flash Player 10 beta for Solaris was released on 9/26/2008.

The plugin download is [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz") and it runs great!

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

The info is in the flash sticky. This post isnt a support issue, the 64bit section is a support area.

---

### Post by DarkDancer on 2008-12-01
Tried it, gave me a grey box. Had to revert.

---

### Post by cariboo on 2008-12-01
I've been using it for a week, I've probably watched more flash videos in the last week then I have in the last year. :)

@DarkDancer

How did you install it the plugin, all I did was untar the file and copy it to /usr/lib/mozilla/plugins. Restart Firefox and go to youtube.


Jim

---

### Post by DarkDancer on 2008-12-01
I put it here in place of the file that was there already...

/usr/lib/flashplugin-nonfree/libflashplayer.so

---

### Post by DarkDancer on 2008-12-01
Thanks cariboo907, that seems to have done it... ;)

---

### Post by tuxxy on 2008-12-01
Yes sorry I probably should have explained, you want to download the plugin and close your browser.

Remove all existing Adobe Flash Player installations from the system.

Unpackage the file, a dir that contains the plugin libflashplayer.so will be created, copy libflashplayer.so to your firefox plugins folder. 

Launch your browser, to verify it in Firefox type 

```
about:plugins
```

---

### Post by Patch1234 on 2008-12-01
I just bought an Acer Aspire M5641 Refurbished Desktop PC - Intel Pentium Dual-Core E2200 2.2GHz. 3GB DDR2, 320 GB SATA HDD, DVDRW DL LabelFlash, Gigabit LAN, Vista Home Premium.

It is a 64bit system.

How hard will it be to convert this to a Ubuntu system?

Thank you for your help.

---

### Post by dfowensby on 2008-12-01
does anyone have a work-around for flash on atom.com? agreed, most/many other sites work just fine, but my faves DON'T.
i support adobe's designation of alpha--YMMV, eh?
some sites tell me i need to upgrade to 9. heh.
still, since i don't do windows, i'll never make it as a glass washer, i guess, and flash in a windows environment, you'll get indecent exposure...
happy chanukah, merry xmas, etc

---

### Post by dfowensby on 2008-12-01
1234:
DL the iso for U8.10 amd64/x86_64 and fire it up!
beware of extreme delite!

edit" more detail to follow

---

### Post by dfowensby on 2008-12-01
patch 1234
download the iso from ubuntu, go to your nautilus cd-burner, scorch a dvd or cd, and reboot: 20 - 30 minutes later you will be wallowing in a 64 bit paradise!
luck -O.

---

### Post by Patch1234 on 2008-12-01
> **dfowensby said:**
> patch 1234
download the iso from ubuntu, go to your nautilus cd-burner, scorch a dvd or cd, and reboot: 20 - 30 minutes later you will be wallowing in a 64 bit paradise!
luck -O.

Thank you for your help. patch 1234

---

### Post by tomdkat on 2008-12-02
Woo-hoo!!!!  I just installed this in /usr/lib/mozilla/plugins and both Firefox 3.0.4 and Opera 9.62 pick it up and it's working great!  :D

Peace...

---

