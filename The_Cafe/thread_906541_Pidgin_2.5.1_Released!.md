---
title: "Pidgin 2.5.1 Released!"
date: 2008-08-31
forum: The Cafe
---

### Post by Kosimo on 2008-08-31
Pidgin folks has just released a new version! 2.5.1  

Here the changelog:

>      * In the Join/Part plugin, add the ability to apply the rules to
       buddies.  By default, joins and parts for buddies are still shown.
     * Support SOCKS proxies specified in GNOME or Windows proxy settings.
     * Fix some possible crashes in MSNP15.
     * Enable a default SSL trust relationship for MSN servers.
     * Avoid disconnecting from XMPP servers on parse errors that are
       non-fatal.
     * Include some perl files that were mistakenly omitted in 2.5.0.
   Pidgin:
     * Prevent use of custom smilies without "shortcuts."
     * Fix a crash that could appear with AIM buddy tooltips.
   Artwork:
     * General refresh of many icons in the interface.
     * Many cleanups to artwork source are now included in the distribution.
     * A new "throbber" animation has been added to indicate when accounts
       are connecting.


As always:

Download the source code, then:

```
./configure
make
sudo make install 
```

If you're lazy to compile and you're using Hardy, getdeb has easy .deb's to install in 32 and 64 bits.  [http://www.getdeb.net](http://www.getdeb.net)

Enjoy!!

---

### Post by Kingsley on 2008-08-31
My system still has Pidgin 2.4.3. Fedora is slippin.

---

### Post by mrgnash on 2008-08-31
A steady stream of improvements, as per the Gnome way :) I really like the artwork refresh, already visible in 2.5, but taken even further here, but without breaking the Pidgin 'look' :)

---

### Post by Polygon on 2008-08-31
yay, more bug fixes =)

---

### Post by Prefix100 on 2008-08-31
Still crashes for me..

Guess its time to submit a bug report.

---

### Post by StOoZ on 2008-08-31
will wait for getdeb to have it. :guitar:

---

### Post by klange on 2008-08-31
Waiting for an official Intrepid build, then I'll just update + upgrade.

---

### Post by slumbergod on 2008-08-31
Ever since 2.50 I have had a lot of trouble connecting to MSN and staying connected. I just use the getdeb packages which have always worked perfectly. My google chat account works perfectly in 2.51 though.

For the time being I have to use aMSN for MSN protocol. It connects in a couple of seconds and stays connected.

---

### Post by Kosimo on 2008-08-31
> **StOoZ said:**
> will wait for getdeb to have it. :guitar:

Is already in getdeb

---

### Post by RiceMonster on 2008-09-01
I'm using 2.5.0 (which is the version in the arch repos) and it works fine, so I won't bother updating until the package maintainer does :).

---

### Post by Ub1476 on 2008-09-01
This looks very nice! :)

Artwork is much improved.

Now we just need webcam support.

---

### Post by highv0ltage on 2008-09-01
I've followed the instructions you've posted and I can't get past he "make" process. I keep receiving configuration errors. The first one I got was "XScreenSaver extension development headers not found". If I disable that one, I get a different one further down the process. Any idea how to fix this? Thanks.

---

### Post by highv0ltage on 2008-09-01
Never mind, I was able to get it fixed.

---

### Post by Dalius on 2008-09-01
Is Pidgin not going to be updated within apt-get Hardy Haron until 8.10 comes out? Not exactly sure how it works... seems some distros have the newest version in their package systems and some don't.

---

### Post by ex.hav0k on 2008-09-01
did they fix the jabber support... cause it sucks having to reconnect every few minutes.

---

