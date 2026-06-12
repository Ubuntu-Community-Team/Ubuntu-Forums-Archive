---
title: "PHP Soap Extension Problems"
date: 2010-12-26
forum: Server Platforms
---

### Post by Zenguy on 2010-12-26
I'm in the process of upgrading a server from Hardy (8.04) to Lucid (10.04). There's an open source package that we are running that runs fine in Hardy, but does not install properly in Lucid.

It uses the php-soap extension, which I've installed via apt-get.

During the software installation on Lucid, the preflight complains that the Soap extension is not installed. Hardy passes this same preflight test just fine.

Has something changed in the way the php soap extension is installed or activated from Hardy to Lucid?

I've pretty much scoured the web for info on this issue, and cannot find a solution.

Thanks.

---

### Post by furlabs on 2010-12-26
Can you check whether the software is expecting a certain version of soap? Sometimes a preflight will say a package is "not installed" when in fact it is just not the version it was expecting.

---

### Post by Zenguy on 2010-12-27
Thanks for the reply. I don't think that it is checking for a specific version. I don't know anything about SOAP, but here is the preflight code that fails:

[PHP]        if (!self::DEBUG_FAIL && extension_loaded('soap') && class_exists('SoapClient') &&
            (is_callable(array('SoapClient', '__soapCall'), false) ||
            is_callable(array('SoapClient', '__call'), false)))[/PHP]

The first test (DEBUG_FAIL) is a debugging flag that will force a failure if enabled. It is disabled.

The first three tests all return 1, so they pass.

It looks like the SoapClient call with the "__call" parameter has been depreciated, but they "OR" that result with (what I believe to be) a valid Soap call '__soapCall'.

I guess it's possible that the calling mechanism for SoapClient has changed and this code is no longer valid.

Any insight?

---

