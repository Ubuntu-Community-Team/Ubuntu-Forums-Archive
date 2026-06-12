---
title: "Would like to setup Opera browser for use with prioxy / TOR in hardy"
date: 2008-05-21
forum: Security
---

### Post by kraymore on 2008-05-21
I was wondering if anyone had any instructions on setting up the Opera browser for use with both privoxy and TOR in ubuntu hardy.  I am a long time firefox user, and while I do have TOR running ok with Torbutton, I would rather have Opera be my 'stealth' browser and firefox for my less secure activities.  I found the place in Opera to enter proxy information, though there was no such place to enter information regarding a Socks host with port 9050.  I do not know if that means that its being hidden well enough.  I would also like to use privoxy with Opera so that dns lookups will be done by prioxy and not be reflected at the ISP level, even if the rest of Opera was stealth, the dns at ISP level would give it away without privoxy.  I can also select 'no cookies' in Opera and choose to not send 'referrer information' which I like.  

Thanks

---

### Post by Dr Small on 2008-05-21
I found this information from the Gentoo Wiki:
> Browsing anonymously

Configure your web browser's http proxy to point to: host: 127.0.0.1 port: 8118. 

Under Opera, go to the Tools menu -> Preferences -> Advanced -> Network -> Proxy Servers

But since you are wanting to use privoxy, the port number should be 9050 instead.

---

### Post by kraymore on 2008-05-21
let me clarify.  i did not want to jump to any conclusions.  I want to use both Tor and prioxy in Opera.  if i simply change to port 9050 in Opera i will do that instead of 8118.  does going to 8118 just go to Tor with dns lookups on the ISP side ?  

thanks

---

