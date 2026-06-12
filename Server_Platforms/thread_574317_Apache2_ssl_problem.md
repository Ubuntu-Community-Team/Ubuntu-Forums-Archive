---
title: "Apache2 ssl problem"
date: 2007-10-12
forum: Server Platforms
---

### Post by osx on 2007-10-12
Having a problem with Apache that seems somehow related to hardware. Sounds strange, but here is the scenario:

My existing configuration works perfect on a VM and a regular desktop, but whenever I put the same configuration onto either of two identical Dell PowerEdge 2850 servers, both fail with the same error messages returned in the apache2 logs.

Here's the other strange part. For testing purposes, I made a simple text file to access to eliminate other factors (e.g., PHP). I can access the test/text file over ssl through a browser, any browser, just fine. But, when I try to access the test/text file via an app written in RealBasic, it fails on the Dell servers, but works on the VM and regular desktops.

I've tried this now on Ubunut 7.04 and the beta 7.10 with the same results. Everything works great in each environment, except for on the identical Dell servers.

Here's what appears in the access.log file of the Dell servers when I use the app written in RealBasic:

::1 - - [12/Oct/2007:13:50:14 -0600] "GET /" 400 600 "-" "-"

Here's what appears in the error.log file of the Dell servers when I use the app written in RealBasic (it's truncated to show only the relevant errors):

[debug] ssl_engine_kernel.c(1789): OpenSSL: Exit: error in SSLv2/v3 read client hello A
[info] [client ::1] SSL handshake failed: HTTP spoken on HTTPS port; trying to send HTML error page
[info] SSL Library Error: 336027804 error:1407609C:SSL routines:SSL23_GET_CLIENT_HELLO:http request speaking HTTP to HTTPS port!?

I know the problem would appear to be obvious given the errors in the error.log file, but keep in mind, absolutely everything else works perfectly over ssl (verified by sniffing) when the identical configuration is run on anything but the Dell servers.

I even enabled mod_rewrite with no change in behavior.

If it helps, all systems used in final testing are running 2.6.22-14-server (no desktop installed on any of them), with Apache/2.2.4 (Ubuntu). The install on them was done using the beta of Ubuntu 7.10 that was downloaded on 10/11/07. LAMP and OpenSSH were selected during install. All systems were updated this morning (10/12/07) with no change in behavior.

---

### Post by MJN on 2007-10-12
Have you a packet trace on the transaction between the app and the Dell server? Does it show that https is being used, or https?

Indeed, compare the traces between the working app configuration and not - they should behave identically (obviously) so any discrepancy should show up.

As you say, the error seems obvious - attempting to speak http to an ssl-wrapped server - but quite how this should vary between hosts is not at all clear.

To me it sounds like a problem in your app - regardless of the apparent differences seen when changing hardware (the browsers checks show the SSL handshaking is working) so you need to do some packet sniffing to see exactly what connection the app is initiating.

As an independent test try connecting to the Dell with **openssl s_client <serveraddress>:443** (substitute your server name and port if non-standard) and when connected issue the command **get**. Post the output (handshaking and data).

Mathew

---

### Post by osx on 2007-10-12
> Have you a packet trace on the transaction between the app and the Dell server? Does it show that https is being used, or https?

Yes and it shows https is being used.

> As an independent test try connecting to the Dell with openssl s_client <serveraddress>:443 (substitute your server name and port if non-standard) and when connected issue the command get. Post the output (handshaking and data).

I did this on both the Dell systems and the working systems. The results are the same for both Dell and non-Dell systems (see below - some information changed to provide some confidentiality).

CONNECTED(00000003)
depth=0 /C=US/ST=AZ/L=Phoenix/CN=my.example.com/emailAddress=support@example.com
verify error:num=18:self signed certificate
verify return:1
depth=0 /C=US/ST=AZ/L=Phoenix/CN=my.example.com/emailAddress=support@example.com
verify return:1
---
Certificate chain
 0 s:/C=US/ST=AZ/L=Phoenix/CN=my.example.com/emailAddress=support@example.com
   i:/C=US/ST=AZ/L=Phoenix/CN=my.example.com/emailAddress=support@example.com
---
Server certificate
-----BEGIN CERTIFICATE-----
MIICWzCCAcQCCQCT+SmsPE123456789qhkiG9w0BAQUFADByMQswCQYDVQQGEwJV
UzELMAkGA1U123456789ETAPBgNVBAcTCENoZXllbm5lMRswGQYDVQQDExJwcC53
eW9taW5naWNhYy5jb20xJjAkBgkqhkiG9w0BCQEWF3N1cHBvcnRA1234567892lj
YWMuY29tMB4X12345678923456789loXDTA4MTAwNzIyMDEyNlowcjELMAkGA1UE
BhM123456789BgNVBAgTAldZMREwDwYDVQQHEwhDaGV5ZW5uZTEbMBkGA1UEAxMS
cHAud3lvbWluZ2ljYWMuY29tMSYwJAYJKoZIhvcN123456789XBwb3J0QHd5b21p
bmdpY2FjLmNv123456789gkqhkiG9w0BAQEFAAOBjQAwgYkCgYEAtKtu2QF1eVE6
bBVkQn1X+kVYXC9CU7Y/XljqDlLorBL+ReA123456789/sUgojZTOLXoDhIsM5Yr
WiMGeSM+L123456789z+cbSUKSEOrUDdBDjlCG8LV8L8HZ36zsKCN2h0XGHtPegG
ulbW270QM2KPLk3FS5AsjjRgc9e/omEC123456789gkqhkiG9w0BAQUFAAOBgQAR
sl/Yr3L317c39o1234567890QcPAyTARxUrmKuO4/0fb8DHerWMtbqCdyIC3+bZm
w4kaaw0/G5xCbPuR596LklnZ6RKulKi3s1234567892Cji/eAVrBQn9N8aw1Y3t7
ehTrmIfen123456789YXVzCMrgqkctbW66x31dHZ9w==
-----END CERTIFICATE-----
subject=/C=US/ST=AZ/L=Phoenix/CN=my.example.com/emailAddress=support@example.com
issuer=/C=US/ST=AZ/L=Phoenix/CN=my.example.com/emailAddress=support@example.com
---
No client certificate CA names sent
---
SSL handshake has read 1171 bytes and written 316 bytes
---
New, TLSv1/SSLv3, Cipher is DHE-RSA-AES256-SHA
Server public key is 1024 bit
Compression: NONE
Expansion: NONE
SSL-Session:
    Protocol  : TLSv1
    Cipher    : DHE-RSA-AES256-SHA
    Session-ID: 8E912BFACC0F372A118C218E62B45CB59DF918F32372A881F3469ADA72A6F521
    Session-ID-ctx: 
    Master-Key: FA96465F011F443084550D6D9B9DF0095C47F4DD27AFFF5E31E360B71BCB36187F5C55885E313CA64FD202AEEB0C5EBE
    Key-Arg   : None
    Start Time: 1192231355
    Timeout   : 300 (sec)
    Verify return code: 18 (self signed certificate)
---
get
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>501 Method Not Implemented</title>
</head><body>
<h1>Method Not Implemented</h1>
<p>get to / not supported.<br />
</p>
<hr>
<address>Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6 mod_ssl/2.2.4 OpenSSL/0.9.8e Server at my.example.com Port 443</address>
</body></html>
closed

---

### Post by MJN on 2007-10-13
Then I'd say it's your app at fault - not the servers. You've seen two independent applications working in the same, and correct, fashion - a browser and a low(er)-level ssl tool.

The fact that the different servers result in different results when using your app is merely highlighting that the app fault only occurs in certain conditions... but either way it's still a fault.

Mathew

---

