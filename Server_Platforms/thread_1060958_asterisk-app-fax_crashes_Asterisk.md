---
title: "asterisk-app-fax crashes Asterisk"
date: 2009-02-05
forum: Server Platforms
---

### Post by beniwtv on 2009-02-05
Hi all,

I have installed asterisk-app-fax from the repos, but every time I try to RxFax, Asterisk crashes after a few seconds (Segmentation fault).

Here's my config:
exten => _[a-zA-Z0-9].,1,Answer()
exten => _[a-zA-Z0-9].,2,RxFax(/tmp/file.tif)

Asterisk logs do not say anything either. So I'm a bit lost. Anyone had that problem before? If not, could anyone tell me steps to diagnose what's causing this?

(NOTE: This is on Hardy LTS, fully up-to-date).

EDIT: Found a Debian bug: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=479612](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=479612). Might that apply to Ubuntu as well?

Cheers,

---

### Post by beniwtv on 2009-02-06
Anyone? :'(

---

### Post by amenszer on 2009-05-12
I had a similar problem, and noticed that I had the asterisk-oh323 package installed on my server. I purged it from the machine, and that fixed the segfault problem. Not sure about that Debian bug though.

I am however experiencing another issue.
I have the following installed:
-Asterisk 1.4.17
-asterisk-app-fax-0.0.20070624
-libtiff4

When I receive a fax, I see the following on the console:
```

-- Starting simple switch on 'Zap/1-1'
-- Executing [s@incoming:1] Set("Zap/1-1", "FAXFILE=/var/spool/asterisk/fax/asterisk-20942-1242136284.32.tif") in new stack
-- Executing [s@incoming:2] RxFAX("Zap/1-1", "/var/spool/asterisk/fax/asterisk-20942-1242136284.32.tif") in new stack
[May 12 08:51:59] WARNING[30209]: channel.c:3059 set_format: Unable to find a codec translation path from unknown to unknown
[May 12 08:51:59] WARNING[30209]: app_rxfax.c:340 rxfax_exec: Unable to restore read format on 'Zap/1-1'
-- Hungup 'Zap/1-1'

```

It creates the fax .tif file in /var/spool/asterisk/fax/, but all but 2 of them are corrupt (they are only 8-bytes and not viewable).
Do you have any ideas about this?

---

### Post by beniwtv on 2009-05-12
Heh...

Thanks, for the info. I ended up installing NVfax manually from source, which also works fine.

About your problem, I think it's a problem with codecs. I have never used zap channels, but that message means it doesn't know what codec it should use.

Can you do voice calls on this channel?

---

### Post by amenszer on 2009-05-12
Yeah, I can do everything else just fine. 
I've tried a couple of different approaches to this...compiling from source with agx-ast-addons (rxfax and txfax), and also using synaptic's packages for asterisk. 
Compiling from source ended up being a nightmare...which is why I'm doing the synaptic approach right now. 

Would you mind posting your fax relevant config files so that I can compare?

---

### Post by beniwtv on 2009-05-13
Sure. What configuration files do you need?

---

### Post by amenszer on 2009-05-19
I guess your zaptel.conf and zapata.conf....those are the only other things that I guess would matter.

Thanks.

---

### Post by beniwtv on 2009-05-19
Like I said before, I don't use zap channels, so no zaptel.conf or zapata.conf.

I used SIP with an incoming provider just for a test, and it seemed to go well.

But I guess you might be able to find some information on #asterisk for that error.

---

### Post by amenszer on 2009-05-19
My mistake.
Thanks anyway.

---

### Post by netpro25 on 2009-09-02
So I found a way to fix the issue I was experiencing which was asterisk would receive the tiff file then exit abruptly after. I was able to fix this in the following manner:

Get the most recent app_rxfax and app_txfax
```

svn co svn://svn.debian.org/pkg-voip/asterisk-spandsp-plugins/trunk@6561 asterisk-spandsp-plugins 

```

Then run the following
```

cd asterisk-spandsp-plugins 
svn-buildpackage

```

Lastly
```

cd ../build-area
dpkg -i install asterisk-app-fax*.deb

```

And cross your fingers and everything should work as expected.

Adapted from [http://www.voip-info.org/wiki/view/app_rxfax+and+app_txfax](http://www.voip-info.org/wiki/view/app_rxfax+and+app_txfax)

---

### Post by beniwtv on 2009-09-02
Yes, that's basically what I did. Just recompile it (but I didn't do it from Debian)

---

