---
title: "Citrix CA automatic download"
date: 2008-04-01
forum: Server Platforms
---

### Post by dj3mb3 on 2008-04-01
Hi
My problem is with the ICAClient 10.6

I have installed the client into Gutsy end It works fine!

But when I try to log into a web browser application It fail to retrive automatically the CA.   I don't know if it is the client or the browser, but I can't work

The windows version of the client works fine and don't need to receive manually the CA file (I have searched for .crt in my pc with 0 result).
I think the active directory service of the citrix web server provide it automatically.

Someone can tell me how to retrieve that file directly from the "internet" or from the windows version

:confused:

thanks a lot

---

### Post by bmathis on 2008-04-02
What certificate is it asking for? You should be able to download the.cer file by searching google and then move it to a .crt file inside your citrix config folders. 

You can also follow my blog entry below which has the information to get this going when it requires an Equifax certificate

[http://www.brianmathis.net/2008/01/01/howto-citrix-client-106-in-ubuntu-gutsy/#more-17]("http://www.brianmathis.net/2008/01/01/howto-citrix-client-106-in-ubuntu-gutsy/#more-17")

---

### Post by dj3mb3 on 2008-04-02
Hi

I have tried your blog instuction, but I have always the same error message

"The archives required to make an SSL connection are not avaible. Please contact your MetaFrame Administrator"

:confused:

What I have to done???

thanks a lot

---

### Post by bmathis on 2008-04-02
im not sure on that one. you might want to try the citrix knowledge base and forums.

Please post back here if you find a solution so that others may find the answer.

thanks

---

### Post by Charles-2007 on 2008-04-16
I just want to clarify this as I've been struggling with the same issue.  It appears that Citrix running on Ubuntu Linux with a Citrix call generated through the Firefox browser does not automatically download and install the security certificates needed to make this work (sorry for the run-on sentence).

So one must separately install these certificates which must be retrieved from the appropriate authority.  For Globalsign, in a different forum it was suggested to do this in a terminal window:

wget [http://secure.globalsign.net/cacert/Root.crt](http://secure.globalsign.net/cacert/Root.crt)

then move it:

cp Root.crt /usr/lib/ICAClient/keystore/cacerts/entrust_ssl_ca .crt

Brian shows theBase-64 encoded Equifax (which is GeoTrust) one is at: 

[https://www.geotrust.com/resources/root_certificates/certificates/Equifax_Secure_Certificate_Authority.cer](https://www.geotrust.com/resources/root_certificates/certificates/Equifax_Secure_Certificate_Authority.cer)

But the wget command I assume won't fly as the file must be renamed from cer to crt and then:

sudo mv Equifax_Secure_Certificate_Authority.cer /usr/lib/ICAClient/keystore/cacerts/Equifax_Secure_Certificate_Authority.crt

to put it in the right place.

I would further assume that this would work for other certificates.  the Thawte ones are here (but you must register):

[http://www.thawte.com/roots/index.html](http://www.thawte.com/roots/index.html)

Best wishes.

---

