---
title: "About Server"
date: 2007-05-05
forum: Server Platforms
---

### Post by palestal on 2007-05-05
i want to set up a server. i will download ubuntu server edition. i want to ask some questions.

1-) After installation of server edition, will i need a static IP or domain?
2-)If i will canalize a domain to my server, will i need a dns adress??
3-) Is 1024 adsl(128kbyte/sec) internet speed enough for an average forum?

With My respects...

---

### Post by bobsta63 on 2007-05-06
> **palestal said:**
> i want to set up a server. i will download ubuntu server edition. i want to ask some questions.

1-) After installation of server edition, will i need a static IP or domain?
2-)If i will canalize a domain to my server, will i need a dns adress??
3-) Is 1024 adsl(128kbyte/sec) internet speed enough for an average forum?

With My respects...

Hi palestal,

With regards to your questons:-

1. After installing Ubuntu Server Editon you wouldn't really need a static IP address, You could use a Dynamic DNS Service like [DynDNS]("http://www.dyndns.com") or [No-IP]("http://www.no-ip.com"). I personally would get a static IP address for stability and so that you can easily point a TLD (Top level domain) to your server.

2. No really sure what your talking about for queston #2. However, I have the same sort of setup as yourself, I use UKReg to register my domain name then use the control panel to point the domain to my static IP address (provided by my ISP) and then have port fowarded the required ports to my server on my lan... So basically, I only have one server and I do not have a DNS server as such.

3. I have 2MB ADSL, Check out my site [www.urbanparty.net]("http://www.urbanparty.net") and see for yourself how fast it responds. I would say that I could easily host a forum on my connection, however its when you start getting say 10+ concurrent users online at a time is when you may start to notice lag.

Hope this helps mate, If you have any more questons please feel free to ask away :)

Regards,

Bobby

---

### Post by MJN on 2007-05-06
> **palestal said:**
> i want to set up a server. i will download ubuntu server edition. i want to ask some questions.

1-) After installation of server edition, will i need a static IP or domain?

You don't *need* a static IP - there are many 'workarounds' available to cope with you having a dynamic address. You'll need a domain name anyway if you want people to access your site by name - which you'd certainly want to be the case if you're on a dynamic IP given the potential for it to change. As an example, my download rate is 10mbps but my upload rate is a relatively poor 384kbps. Good enough for my needs (simple pages and not that many visitors at any one time).

Do some reading on 'dynamic DNS' - this is what you'll need for your static name to be kept pointing at your dynamic address.

Regarding choice of domain name there are many outfits that will provide one for free - but it'll be underneath their hierarchy e.g. <yourname>.no-ip.org, alternatively you can buy your own (not a top-level domain though as Bobby says! ;)) *under* one of the ccTLD's or gTLD's e.g. <yourname>.com, <yourname>.co.uk etc for next to nothing these days. Choose your registrar wisely though as you'll want them to either support dyamic DNS themselves (for free ideally) or let you delegate control of your domain to a dedicated dynamic DNS provider (e.g. [www.zoneedit.com)]("http://www.zoneedit.com%29"), again ideally for free so shop around!

> 2-)If i will canalize a domain to my server, will i need a dns adress??Can you rephrase what you mean? The bottom line is, yes, you will want a domain name - hosting a site by IP address alone is really not what you want to be doing. (Sure, it's doable - for example you can visit my site at [http://82.46.99.50/](http://82.46.99.50/) but when my address changes you won't be able to find me. I'd have to tell you what my new address is. Far better instead to reach me at [http://www.newtonnet.co.uk/](http://www.newtonnet.co.uk/) - that domain will always point to my latest IP address.)

> 3-) Is 1024 adsl(128kbyte/sec) internet speed enough for an average forum?Given that your website will mainly be *uploading* date to users (there can of course be exceptions but even without knowing your intent it's more likely you'll be serving content rather than accepting it) then the key factor is your *upload* speed. This is usually (but not always) much less than your download rate.

Do you know your upload speed? Or was 1024mbps it? Sounds rather high for a 'standard' connection hence I'd suspect that's your download.

As Bobby correctly alludes how sufficient your connection speed is akin to asking how long a piece of string is. It depends - how many concurrent visitors are you wanting to support, what sort of content (simple webpages, streaming video, etc?) are you serving, etc etc.

Have a search through the archives - there's a million and one of us all doing what you're thinking of so there's plenty of info about.

Mathew

---

### Post by palestal on 2007-05-06
well, my upload speed is 256 kbit/sec(32 kbyte/sec)

---

### Post by MJN on 2007-05-07
As mentioned, it all depends on what usage you're expecting/wanting out of it. My connection used to be 256kbps upload and it was 'okay'. The thing is, whatever it is you'll always want more!

Mathew

---

### Post by palestal on 2007-05-07
thx for help, i can just say that:D

---

