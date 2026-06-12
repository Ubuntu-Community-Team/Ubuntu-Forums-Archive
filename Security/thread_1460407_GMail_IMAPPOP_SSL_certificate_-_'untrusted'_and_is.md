---
title: "GMail IMAP/POP SSL certificate - 'untrusted' and issued by Fortinet"
date: 2010-04-22
forum: Security
---

### Post by Helkaluin on 2010-04-22
I might just be paranoid here, I hope I'm not:

Following a recent success in setting up DavMail for my school Exchange 2007 mail, I wished to bundle my GMail account to Thunderbird (3.0.4) as well so that I don't need to bother with web-interfaces anymore.

What alarmed me was that, whilst trying to connect to GMail using IMAP, a notice for untrusted certificate pops up.

Naturally the connection is SSL encrypted. What worries me is that the certificate is issued with CN='Fortigate CA' and O='Fortinet'. May I also enclose that my school's regular web access is filtered using FortiGuard, and it is clear that they use a kind of Fortinet-issued UTM for the school network.

My concern is that are the school intermittent servers trying to substitute my SSL certificates? Using GMail via HTTPS reveals a certificate issued by Thawte SGC, and Firefox believes that is universally verified and trusted.

So may I just ask two things: One, that could anyone report a Fortinet-issued certificate for IMAP GMail is actually normal (I doubt it); and Two, that do I run the potential risk of having my GMail login details and thus access given to my school if I accept the connection via this certificate?

Thank you for your attention.

---

### Post by cdenley on 2010-04-23
That certainly is not the correct SSL certificate.
```

cdenley@ubuntu:~$ echo|openssl s_client -connect imap.gmail.com:993
CONNECTED(00000003)
depth=1 /C=US/O=Google Inc/CN=Google Internet Authority
verify error:num=20:unable to get local issuer certificate
verify return:0
---
Certificate chain
 0 s:/C=US/ST=California/L=Mountain View/O=Google Inc/CN=imap.gmail.com
   i:/C=US/O=Google Inc/CN=Google Internet Authority
 1 s:/C=US/O=Google Inc/CN=Google Internet Authority
   i:/C=US/O=Equifax/OU=Equifax Secure Certificate Authority
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIDWzCCAsSgAwIBAgIKYgnCCAADAAAJ5DANBgkqhkiG9w0BAQUFADBGMQswCQYD
VQQGEwJVUzETMBEGA1UEChMKR29vZ2xlIEluYzEiMCAGA1UEAxMZR29vZ2xlIElu
dGVybmV0IEF1dGhvcml0eTAeFw0wOTA3MTcxNzEzNDFaFw0xMDA3MTcxNzIzNDFa
MGgxCzAJBgNVBAYTAlVTMRMwEQYDVQQIEwpDYWxpZm9ybmlhMRYwFAYDVQQHEw1N
b3VudGFpbiBWaWV3MRMwEQYDVQQKEwpHb29nbGUgSW5jMRcwFQYDVQQDEw5pbWFw
LmdtYWlsLmNvbTCBnzANBgkqhkiG9w0BAQEFAAOBjQAwgYkCgYEA+O0vc2pslfjk
pbxnBF4iznJMrP9Qi3fHjKqA3P2RynTcbnZfGEGMKcPeXHT4IOH6XUnf+4Jw+z7I
KiMtjX8IVGo7DeXec/ZREasEZnpMGisxN7+qk7Ho6HyaglQTAFIQJP99UFJkHO9x
dGDy5d2j9senPad1BqtyaIRGkJpHizUCAwEAAaOCASwwggEoMB0GA1UdDgQWBBT0
WHOeLKf4+VNADzHzGh+AEV+6fjAfBgNVHSMEGDAWgBS/wDDr9UMRPme6npH7/Gra
42sSJDBbBgNVHR8EVDBSMFCgTqBMhkpodHRwOi8vd3d3LmdzdGF0aWMuY29tL0dv
b2dsZUludGVybmV0QXV0aG9yaXR5L0dvb2dsZUludGVybmV0QXV0aG9yaXR5LmNy
bDBmBggrBgEFBQcBAQRaMFgwVgYIKwYBBQUHMAKGSmh0dHA6Ly93d3cuZ3N0YXRp
Yy5jb20vR29vZ2xlSW50ZXJuZXRBdXRob3JpdHkvR29vZ2xlSW50ZXJuZXRBdXRo
b3JpdHkuY3J0MCEGCSsGAQQBgjcUAgQUHhIAVwBlAGIAUwBlAHIAdgBlAHIwDQYJ
KoZIhvcNAQEFBQADgYEAXLvdKJJ6ivWAi29p4pPo4cirMEYnRlpNOmPVAW4QYcSq
lEZhm4cQdyitFo9cxiwNgbBjJk8O+oiOhnueT44RXotEE7j3KnNyPRRZg0OCagGC
4G71fFA11P1L0fSd/7k52/DbZQBea3tJgkseoGL50UVvnJm+LZOovIGxoQzipJk=
-----END CERTIFICATE-----
subject=/C=US/ST=California/L=Mountain View/O=Google Inc/CN=imap.gmail.com
issuer=/C=US/O=Google Inc/CN=Google Internet Authority
---
No client certificate CA names sent
---
SSL handshake has read 1704 bytes and written 300 bytes
---
New, TLSv1/SSLv3, Cipher is RC4-MD5
Server public key is 1024 bit
Compression: NONE
Expansion: NONE
SSL-Session:
    Protocol  : TLSv1
    Cipher    : RC4-MD5
    Session-ID: B94E1A78EF7DC874DAC15C14841C880FAD657E1E0E6A363A0DEF6B0FCFE2B467
    Session-ID-ctx: 
    Master-Key: EC5D7430A8D8BE26B0469089E52EC66EBC868EF5968F5FB817DA584398F1D57279ABC43AACD82AA9F7F9C20CBFC87639
    Key-Arg   : None
    Start Time: 1272029475
    Timeout   : 300 (sec)
    Verify return code: 20 (unable to get local issuer certificate)
---
DONE

```

Whoever is providing that certificate (not google) is going to be decrypting whatever data you send. Whether they will then establish a real connection to gmail's IMAP server and proxy your connection so they can monitor your IMAP use is another question. If it were on port 443, I would assume they are just sending you to a captive portal.

Can you run this and post the output?
```

echo . LOGOUT|openssl s_client -ign_eof -connect imap.gmail.com:993

```

---

### Post by Helkaluin on 2010-04-23
> **cdenley said:**
> That certainly is not the correct SSL certificate.
. . .
Can you run this and post the output?
```

echo . LOGOUT|openssl s_client -ign_eof -connect imap.gmail.com:993

```

Output as below. Notice the issuer lines:
```
helkaluin@EveNotMallory:~$ echo . LOGOUT|openssl s_client -ign_eof -connect imap.gmail.com:993
CONNECTED(00000003)
depth=0 /C=US/ST=California/L=Mountain View/O=Google Inc/CN=imap.gmail.com
verify error:num=20:unable to get local issuer certificate
verify return:1
depth=0 /C=US/ST=California/L=Mountain View/O=Google Inc/CN=imap.gmail.com
verify error:num=27:certificate not trusted
verify return:1
depth=0 /C=US/ST=California/L=Mountain View/O=Google Inc/CN=imap.gmail.com
verify error:num=21:unable to verify the first certificate
verify return:1
---
Certificate chain
 0 s:/C=US/ST=California/L=Mountain View/O=Google Inc/CN=imap.gmail.com
   i:/C=US/ST=California/L=Sunnyvale/O=Fortinet/OU=Certificate Authority/CN=FortiGate CA/emailAddress=support@fortinet.com
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIDCjCCAfKgAwIBAgIIS82tdAAAAAIwDQYJKoZIhvcNAQEFBQAwgaUxCzAJBgNV
BAYTAlVTMRMwEQYDVQQIEwpDYWxpZm9ybmlhMRIwEAYDVQQHEwlTdW5ueXZhbGUx
ETAPBgNVBAoTCEZvcnRpbmV0MR4wHAYDVQQLExVDZXJ0aWZpY2F0ZSBBdXRob3Jp
dHkxFTATBgNVBAMTDEZvcnRpR2F0ZSBDQTEjMCEGCSqGSIb3DQEJARYUc3VwcG9y
dEBmb3J0aW5ldC5jb20wHhcNMDkwNzE3MTcxMzQxWhcNMTAwNzE3MTcyMzQxWjBo
MQswCQYDVQQGEwJVUzETMBEGA1UECBMKQ2FsaWZvcm5pYTEWMBQGA1UEBxMNTW91
bnRhaW4gVmlldzETMBEGA1UEChMKR29vZ2xlIEluYzEXMBUGA1UEAxMOaW1hcC5n
bWFpbC5jb20wgZ8wDQYJKoZIhvcNAQEBBQADgY0AMIGJAoGBAMSYEsSZ5iVRHiuO
SjhR5bOZ9M3JnMD8Ze4yTAXRVI9OVPJrzHNsi0pEJdFwDbv/7LgcpLsKPN8E9g9F
+iiY9TTdfOuEWTOJr5geIQfeu1eue67xTZU0gYj4F4yYdVY67zjZC5lm+Mw8WJko
7jihfogtg5USAUEnoa7+gmqVB0z1AgMBAAEwDQYJKoZIhvcNAQEFBQADggEBAD1G
C8G00jQ57EWPrkz8GqgrsTD2mFrzKd86HYjbq9hldvC26HyLcbf/3VAzVsFy/KTk
UXoMAYo2V8RMfDMgKJ62r++DsZxYNgdg7wr0VSA5oZvUgx/+hvXUJ0YKFDiAQlvI
M/ZINwClsMBUG7gV+2AgV2omKlg8IC6/4b7+CP7MOg7WJRzcvc6wV/iptKdX+Fzz
cTaVB1s6ixn3wziODGS5EtbjuRctyHo7LcMf7mWVXkb1v70D6v4gzM20fl0XIzc/
sOPjqp9V19ID00IYIRYl5rI88ZjtmuqXJ0DjtNmgkY7tbXGhd9psqMfm5bwhyRVp
dSCwFzFawIc8a21luvg=
-----END CERTIFICATE-----
subject=/C=US/ST=California/L=Mountain View/O=Google Inc/CN=imap.gmail.com
issuer=/C=US/ST=California/L=Sunnyvale/O=Fortinet/OU=Certificate Authority/CN=FortiGate CA/emailAddress=support@fortinet.com
---
No client certificate CA names sent
---
SSL handshake has read 1331 bytes and written 316 bytes
---
New, TLSv1/SSLv3, Cipher is DHE-RSA-AES256-SHA
Server public key is 1024 bit
Compression: NONE
Expansion: NONE
SSL-Session:
    Protocol  : TLSv1
    Cipher    : DHE-RSA-AES256-SHA
    Session-ID: FA49F61461AA4D88C45C2CC5B9147C04AFF1EE703DE8198869E5EE03948332AD
    Session-ID-ctx: 
    Master-Key: B7D33F50CAC14BD326755704287F5509AF221F2B48F723F1A3956EAE97E1DE2744A8B926C79B245466354C7CD1873435
    Key-Arg   : None
    Start Time: 1272040737
    Timeout   : 300 (sec)
    Verify return code: 21 (unable to verify the first certificate)
---
* OK Gimap ready for requests from 194.80.21.10 j27if2275018wbw.40
* BYE Logout Requested j27if2275018wbw.40
. OK Quoth the raven, nevermore... j27if2275018wbw.40
closed
```Should I just resort back to the WebUI (which does present a correct certificate), or should I contact the school IT department? I understand that their network usage policy does include the line: > Use of the network and internet is monitored. But inserting their own SSL cert? I mean... *Really?*

---

### Post by DodgeV83 on 2010-04-23
On the UTM I manage, this will happen whenever I check "Scan https".  It will give you this huge red warning whenever a certificate is presented.  My UTM provides a custom certificate you can upload to Firefox to bypass such warnings, but this probably wouldn't work with Thunderbird.

You aren't being hacked and no malicious site is attempting to access your e-mail (unless you consider your University to be malicious ;)).

If your goal is to not be scanned, I'm not sure that using gmail.com would solve that.  The "Scan https" on my UTM scans all SSL traffic and would catch both gmail.com and Thunderbird.  Are you sure you didn't already trust the "Fortigate CA" in your browser a while ago and forgot about it?

This setting can even disable VPN connections, so I'm not sure what your solution would be.

---

### Post by cdenley on 2010-04-23
They are indeed proxying your IMAP connection, since that is a response from gmail's IMAP with another SSL certificate substituted, and have access to your unencrypted IMAP traffic. I would assume that when establishing their connection to the real gmail IMAP they are using another SSL tunnel. Your traffic should be safe travelling across the net if their MITM device verifies the authenticity of gmail's SSL certificate correctly.

By the way, he said in his first post that gmail was using a Thawte SSL certificate with his web browser, so they must not be proxying SSL connections on port 443.

---

### Post by Helkaluin on 2010-04-23
> **DodgeV83 said:**
> 
If your goal is to not be scanned, I'm not sure that using gmail.com would solve that.  The "Scan https" on my UTM scans all SSL traffic and would catch both gmail.com and Thunderbird.  Are you sure you didn't already trust the "Fortigate CA" in your browser a while ago and forgot about it?
I'm viewing the Certificate Manager in Firefox now. No user-set exceptions are set. I generally steer away from unverified certificates.

And no, I don't *really* trust my school's IT department. This is an IT department that sets up laptops bought via the school-discount-scheme to have their XP administrator passwords set as the same for the ones in the computer labs. What's worrying is that the instructions printed in their issued guide to connect to the school network require the exact steps in allowing remote administration via the set of SAMBA net equivalent tools on Windows machines.

[QUOTE=cdenley]Your traffic should be safe travelling across the net if their MITM  device verifies the authenticity of gmail's SSL certificate correctly.[/QUOTE]
So is it possible for them to know my password? I will read more on SSL tunnelling shortly.

---

### Post by cdenley on 2010-04-23
> **Helkaluin said:**
> 
So is it possible for them to know my password? I will read more on SSL tunnelling shortly.

Yes. Every time you connect, it will be sent in plaintext within the SSL tunnel.

---

### Post by Jive Turkey on 2010-04-25
There are some hardware vendors out there who have recently begun selling appliances specifically for MITM snooping of SSL encrypted traffic.  [http://www.wired.com/threatlevel/2010/03/packet-forensics/](http://www.wired.com/threatlevel/2010/03/packet-forensics/)

To be sure, you SHOULD contact the IT department to find out if they are using such techniques, if it isn't them spoofing that cert, they should probably know who is.

---

### Post by movieman on 2010-04-25
> **Jive Turkey said:**
> To be sure, you SHOULD contact the IT department to find out if they are using such techniques, if it isn't them spoofing that cert, they should probably know who is.

Personally I'd also ask why they're spying on private emails.

---

### Post by CharlesA on 2010-04-25
> **movieman said:**
> Personally I'd also ask why they're spying on private emails.

It is their network, their rules.

---

### Post by rookcifer on 2010-04-25
Let this be a lesson that we all need to periodically check our certs, or at least, make sure the little lock icon is engaged when on an SSL site.

However, even checking certs may not be enough as there are hundreds of CA's out there and there's no way all of them are trustworthy.  Indeed, some of them are very likely ran by intelligence agencies while others are just incompetent and issue certs to bad people (Comodo).  Even some of the trustworthy ones may still be giving out certs to NSA for domestic spy purposes.  Others might be forging trusted certs and selling them to known criminals just to make a quick profit.  We just can't know, which is why I hate the CA model.

---

### Post by movieman on 2010-04-26
> **CharlesA said:**
> It is their network, their rules.

An argument that's unlikely to stand up in court in most Western nations.

And irrelevant to the question of why they're doing so, if they are.

---

### Post by CharlesA on 2010-04-26
> **movieman said:**
> An argument that's unlikely to stand up in court in most Western nations.

Perhaps, but for every job I've had, I've had to sign a "network/computer use agreement." Most had some verbage in there about monitoring computer/network usage.

If it is not your network, expect no privacy.

> And irrelevant to the question of why they're doing so, if they are.

Again, perhaps not relevant, but only the IT admin of the school can answer if they are doing that sort of thing or not.

---

### Post by Helkaluin on 2010-04-26
> **CharlesA said:**
> Perhaps, but for every job I've had, I've had to sign a "network/computer use agreement." Most had some verbage in there about monitoring computer/network usage.

If it is not your network, expect no privacy.
I believe the stock phrase 'network traffic will be monitored' is just a legal catch-all phrase for logging.


I have contacted with my school IT authorities. Apparently it isn't intentional, and no one else had raised the issue before. They are now finding a solution in the man pages.

Some individual research on the almighty Google found this is actually Bug #87297 in version 4.0.0: [http://helpdesk.netcentral.co.uk/index.php?_m=downloads&_a=downloadfile&downloaditemid=96](http://helpdesk.netcentral.co.uk/index.php?_m=downloads&_a=downloadfile&downloaditemid=96)

But I don't know what version my school is running. So heck.

[QUOTE=movieman]Personally I'd also ask why they're spying on private emails.[/QUOTE]
That's what I suspected as one of the possibilities when I first encountered the rogue certificate. But let us not draw conclusions on assumptions.

---

### Post by klly on 2012-11-26
you would get such message when you pass through any UTM Firewall.

why coz the Application Monitoring feature is enabled on the UTM which means that your SSL traffic flow will be inspected for any viruses, worms,,etc. how it works?

Client ----SSL Tunnel ---->UTM FW (Issues a self generated certificate for the SSL Tunnel)----UTM Establishes a new SSL tunnel with desired Mail server on behab of the client ----->pop.gmail (eg).

such inspection would be places in most of the organizations, University, schools ..etc to be able to monitor of the traffic coming out of their network and detect the missus.


but if no written agreement was issued for you, then i guess you can sue them..
hope info was helpful.

---

