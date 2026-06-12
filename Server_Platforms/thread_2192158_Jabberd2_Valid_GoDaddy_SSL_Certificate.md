---
title: "Jabberd2 Valid GoDaddy SSL Certificate?"
date: 2013-12-06
forum: Server Platforms
---

### Post by Kirk Schnable on 2013-12-06
I am running an XMPP chat network using the Jabberd2 server platform.  I currently am using a self-signed PEM certificate which I generated with OpenSSL, however every time clients connect, they are obviously prompted that the certificate is invalid because it is self-signed.

I pay for a valid SSL certificate for the website of this chat network, and I had hoped to eventually use it for XMPP.  However, GoDaddy does not provide a way for me to download the certificate as a PEM file.  I've attempted, in the past, to use the provided certificates to create my own PEM file, but the result in the past was a still-invalid SSL message containing all my GoDaddy certificate information.  (I'm assuming I messed up with the CA?)

I contacted GoDaddy support, and frankly I was not satisfied with their response.

[quote="GoDaddy Support"]Thank you for your response. The SSLs we provide are the common ones used for most installations. If they are not in the format that you need then you must convert them. We do not offer a conversion offer. If the website we last gave you does not work for your situation then you will need to find a website that allows you to convert the SSL into the type of file you need. You may want to do a search on your favorite search engine or consult with a community forum online as other users may have encountered similar problems in the past and may offer helpful solutions.[/quote]

When I download the certificate bundle from GoDaddy, they offer it in several "formats", but all of these "formats" look like they contain two .crt files, which is not what Jabberd2 needs.

[IMG]http://binaryimpulse.com/wp-content/uploads/2013/12/GoDaddy-1.png[/IMG]

When I downloaded the "Apache" format, I got a certificate bundle like this:

[IMG]http://binaryimpulse.com/wp-content/uploads/2013/12/Screenshot-ssl.zip.png[/IMG]

So, can someone suggest how I might go about creating a PEM file to use with Jabberd2?

Thanks!
Kirk

---

### Post by newbie-user on 2013-12-06
Here you go. Hope this helps:

[http://stackoverflow.com/questions/4691699/how-to-convert-crt-to-pem](http://stackoverflow.com/questions/4691699/how-to-convert-crt-to-pem)

---

### Post by Kirk Schnable on 2013-12-07
> **newbie-user said:**
> Here you go. Hope this helps:

[http://stackoverflow.com/questions/4691699/how-to-convert-crt-to-pem](http://stackoverflow.com/questions/4691699/how-to-convert-crt-to-pem)
I think this is similar to what I've tried in the past which still results in invalid certificate errors.  I am not clear what to do with the sf_bundle.crt in this type of conversion process, and I think that is where my problem lies...

---

### Post by CharlesA on 2013-12-07
That looks to be a certificate bundle for used for cPanel and the like.

> Starfield Certificate Bundles (for cPanel, Plesk, Apache 1.x and 2.x installation only)

    sf_bundle.crt
    Certificate File Hash (sha1): 9F 4B 50 01 1B DE AB DA 27 6C 9D D0 8F 32 F5 45 21 8E A1 B7


[https://certs.godaddy.com/anonymous/repository.pki](https://certs.godaddy.com/anonymous/repository.pki)

---

### Post by Kirk Schnable on 2013-12-08
> **CharlesA said:**
> That looks to be a certificate bundle for used for cPanel and the like.
I see, I wasn't aware of that, thanks.
[URL="https://certs.godaddy.com/anonymous/repository.pki"]
> **CharlesA said:**
> https://certs.godaddy.com/anonymous/repository.pki[/URL]
That is a FANTASTIC link, thank you!

I'm going to give this a shot.  

Right now, for Apache, I have the following files:
**mydomain.key**
```
-----BEGIN RSA PRIVATE KEY-----
lots of text and stuff
-----END RSA PRIVATE KEY-----
```

**mydomain.crt**
```
-----BEGIN CERTIFICATE-----
lots of other text and stuff
-----END CERTIFICATE-----
```


From jabberd2's router.xml file:
> **"router.xml"]    <!-- File containing an SSL certificate and private key for client
         connections. From SSL_CTX_use_certificate_chain_file(3):
         "The certificates must be in PEM format and must be sorted
         starting with the subject's certificate (actual client or
         server certificate), followed by intermediate CA certificates
         if applicable, and ending at the highest level (root) CA"
         (the latter one being optional).
         If this is commented out, connecting components will not be able
         to request an SSL-encrypted channel. -->[/QUOTE]

It sounds like what I need to do is create a PEM file containing (in this order): **mydomain.crt, mydomain.key, intermediate CA certs, and the root CA cert**.  Is this accurate?  The description in router.xml doesn't actually say anything about the private key but I assume it's needed.



Any idea which intermediately certificates I should use?  GoDaddy appears to have several:
[QUOTE="GoDaddy"]
[LIST]
[*]Go Daddy Secure Server Certificate (Intermediate Certificate)
[LIST]
[*][URL="https://certs.godaddy.com/anonymous/repository.pki said:**
> gd_intermediate.crt[/URL]
[*]Certificate File Hash (sha1): B4 7F 9E C2 C1 60 9F 36 EF 11 7E D6 71 81 32 91 65 57 B6 15
[*]Certificate Thumbprint (sha1): 7C 46 56 C3 06 1F 7F 4C 0D 67 B3 19 A8 55 F6 0E BC 11 FC 44
[/LIST]
[/LIST]

[LIST]
[*]Go Daddy Secure Server Certificate (Intermediate Certificate) (DER Format)
[LIST]
[*][gd_intermediate.crt.der]("https://certs.godaddy.com/anonymous/repository.pki;jsessionid=p4-YqJ+O5o1vnL8wZ99JlA__.p3p02jb?streamfilename=gd_intermediate.crt.der&actionMethod=anonymous%2Frepository.xhtml%3Arepository.streamFile%28%27%27%29&cid=136493")
[*]Certificate File Hash (sha1): 7C 46 56 C3 06 1F 7F 4C 0D 67 B3 19 A8 55 F6 0E BC 11 FC 44
[*]Certificate Thumbprint (sha1): 7C 46 56 C3 06 1F 7F 4C 0D 67 B3 19 A8 55 F6 0E BC 11 FC 44
[*]Certificate File Hash (sha256): 09 ED 6E 99 1F C3 27 3D 8F EA 31 7D 33 9C 02 04 18 61 97 35 49 CF A6 E1 55 8F 41 1F 11 21 1A A3
[/LIST]
[/LIST]

[LIST]
[*]Go Daddy Secure Server Certificate (Cross Intermediate Certificate)
[LIST]
[*][gd_cross_intermediate.crt]("https://certs.godaddy.com/anonymous/repository.pki;jsessionid=p4-YqJ+O5o1vnL8wZ99JlA__.p3p02jb?streamfilename=gd_cross_intermediate.crt&actionMethod=anonymous%2Frepository.xhtml%3Arepository.streamFile%28%27%27%29&cid=136493")
[*]Certificate File Hash (sha1): 7D B7 4B 33 10 93 18 46 A4 BF CD E8 C6 EA 22 32 25 66 A9 0B
[*]Certificate Thumbprint (sha1): DE 70 F4 E2 11 6F 7F DC E7 5F 9D 13 01 2B 7E 68 7A 3B 2C 62
[/LIST]
[/LIST]

[LIST]
[*]Go Daddy Secure Server Certificate (Cross Intermediate Certificate) (DER Format)
[LIST]
[*][gd_cross_intermediate.crt.der]("https://certs.godaddy.com/anonymous/repository.pki;jsessionid=p4-YqJ+O5o1vnL8wZ99JlA__.p3p02jb?streamfilename=gd_cross_intermediate.crt.der&actionMethod=anonymous%2Frepository.xhtml%3Arepository.streamFile%28%27%27%29&cid=136493")
[*]Certificate File Hash (sha1): DE 70 F4 E2 11 6F 7F DC E7 5F 9D 13 01 2B 7E 68 7A 3B 2C 62
[*]Certificate Thumbprint (sha1): DE 70 F4 E2 11 6F 7F DC E7 5F 9D 13 01 2B 7E 68 7A 3B 2C 62
[*]Certificate File Hash (sha256): 18 F8 A7 A1 51 B4 EC 28 08 98 09 3D F5 BD 53 7C A0 99 CC 27 74 05 D0 28 1D E0 DA DF D1 44 20 DA
[/LIST]
[/LIST]
[FONT=inherit]
[LIST]
[*]Go Daddy Secure Server Certificate (Intermediate Certificate) - G2
[LIST]
[*][gdig2.crt]("https://certs.godaddy.com/anonymous/repository.pki;jsessionid=p4-YqJ+O5o1vnL8wZ99JlA__.p3p02jb?streamfilename=gdig2.crt&actionMethod=anonymous%2Frepository.xhtml%3Arepository.streamFile%28%27%27%29&cid=136493")
[*]Certificate File Hash (sha1): C6 2F E9 0D 24 2C A6 4F 1F FD 82 BF CA AC 1A EF 41 BD D2 1D
[*]Certificate Thumbprint (sha1): 27 AC 93 69 FA F2 52 07 BB 26 27 CE FA CC BE 4E F9 C3 19 B8
[*]Certificate File Hash (sha256): 70 8C 14 77 F5 E2 B2 AE 40 2B A1 02 0A 69 6C DD 00 51 D4 48 59 A7 E1 42 3C 90 08 26 D0 90 53 F4
[*]Certificate Thumbprint (sha256): 97 3A 41 27 6F FD 01 E0 27 A2 AA D4 9E 34 C3 78 46 D3 E9 76 FF 6A 62 0B 67 12 E3 38 32 04 1A A6
[/LIST]
[/LIST]

[LIST]
[*]Go Daddy Secure Server Certificate (Intermediate Certificate) (DER Format) - G2
[LIST]
[*][gdig2.crt.der]("https://certs.godaddy.com/anonymous/repository.pki;jsessionid=p4-YqJ+O5o1vnL8wZ99JlA__.p3p02jb?streamfilename=gdig2.crt.der&actionMethod=anonymous%2Frepository.xhtml%3Arepository.streamFile%28%27%27%29&cid=136493")
[*]Certificate File Hash (sha1): 27 AC 93 69 FA F2 52 07 BB 26 27 CE FA CC BE 4E F9 C3 19 B8
[*]Certificate Thumbprint (sha1): 27 AC 93 69 FA F2 52 07 BB 26 27 CE FA CC BE 4E F9 C3 19 B8
[*]Certificate File Hash (sha256): 97 3A 41 27 6F FD 01 E0 27 A2 AA D4 9E 34 C3 78 46 D3 E9 76 FF 6A 62 0B 67 12 E3 38 32 04 1A A6
[/LIST]
[/LIST]
[/FONT]

[LIST]
[*]Starfield Secure Server Certificate (Intermediate Certificate)
[LIST]
[*][sf_intermediate.crt]("https://certs.godaddy.com/anonymous/repository.pki;jsessionid=p4-YqJ+O5o1vnL8wZ99JlA__.p3p02jb?streamfilename=sf_intermediate.crt&actionMethod=anonymous%2Frepository.xhtml%3Arepository.streamFile%28%27%27%29&cid=136493")
[*]Certificate File Hash (sha1): 36 B9 51 53 B8 EA 7A 9A 63 A8 1B 28 E8 21 49 90 CC 62 47 FB
[*]Certificate Thumbprint (sha1): 7E 18 74 A9 8F AA 5D 6D 2F 50 6A 89 20 FF 22 FB D1 66 52 D9
[/LIST]
[/LIST]

[LIST]
[*]Starfield Secure Server Certificate (Intermediate Certificate) (DER Format)
[LIST]
[*][sf_intermediate.crt.der]("https://certs.godaddy.com/anonymous/repository.pki;jsessionid=p4-YqJ+O5o1vnL8wZ99JlA__.p3p02jb?streamfilename=sf_intermediate.crt.der&actionMethod=anonymous%2Frepository.xhtml%3Arepository.streamFile%28%27%27%29&cid=136493")
[*]Certificate File Hash (sha1): 7E 18 74 A9 8F AA 5D 6D 2F 50 6A 89 20 FF 22 FB D1 66 52 D9
[*]Certificate Thumbprint (sha1): 7E 18 74 A9 8F AA 5D 6D 2F 50 6A 89 20 FF 22 FB D1 66 52 D9
[*]Certificate File Hash (sha256): 05 A6 DB 38 93 91 DF 92 E0 BE 93 FD FA 4D B1 E3 CF 53 90 39 18 B8 D9 D8 5A 9C 39 6C B5 5D F0 30
[/LIST]
[/LIST]

[LIST]
[*]Starfield Secure Server Certificate (Cross Intermediate Certificate)
[LIST]
[*][sf_cross_intermediate.crt]("https://certs.godaddy.com/anonymous/repository.pki;jsessionid=p4-YqJ+O5o1vnL8wZ99JlA__.p3p02jb?streamfilename=sf_cross_intermediate.crt&actionMethod=anonymous%2Frepository.xhtml%3Arepository.streamFile%28%27%27%29&cid=136493")
[*]Certificate File Hash (sha1): CC 96 2B 82 D0 51 E7 B5 85 FB 4B CB 49 B7 30 3F F3 0C CC 42
[*]Certificate Thumbprint (sha1): 36 3E 47 34 F7 57 BD EB 89 86 8E FE 94 90 77 74 A3 27 69 5E
[/LIST]
[/LIST]

[LIST]
[*]Starfield Secure Server Certificate (Cross Intermediate Certificate) (DER Format)
[LIST]
[*][sf_cross_intermediate.crt.der]("https://certs.godaddy.com/anonymous/repository.pki;jsessionid=p4-YqJ+O5o1vnL8wZ99JlA__.p3p02jb?streamfilename=sf_cross_intermediate.crt.der&actionMethod=anonymous%2Frepository.xhtml%3Arepository.streamFile%28%27%27%29&cid=136493")
[*]Certificate File Hash (sha1): 36 3E 47 34 F7 57 BD EB 89 86 8E FE 94 90 77 74 A3 27 69 5E
[*]Certificate Thumbprint (sha1): 36 3E 47 34 F7 57 BD EB 89 86 8E FE 94 90 77 74 A3 27 69 5E
[*]Certificate File Hash (sha256): D7 34 94 E3 44 6B 02 16 75 73 B3 CD E3 AE 1C 85 84 AC 26 E1 5E 45 AC 3E C0 32 67 08 42 5D 90 FB
[/LIST]
[/LIST]
[FONT=inherit]
[LIST]
[*]Starfield Secure Server Certificate (Intermediate Certificate) - G2
[LIST]
[*][sfig2.crt]("https://certs.godaddy.com/anonymous/repository.pki;jsessionid=p4-YqJ+O5o1vnL8wZ99JlA__.p3p02jb?streamfilename=sfig2.crt&actionMethod=anonymous%2Frepository.xhtml%3Arepository.streamFile%28%27%27%29&cid=136493")
[*]Certificate File Hash (sha1): 2E A0 42 B7 DD 5F E6 4C 72 4D E7 87 45 35 D0 2B 6D EC 7B D8
[*]Certificate Thumbprint (sha1): 7E DC 37 6D CF D4 5E 6D DF 08 2C 16 0D F6 AC 21 83 5B 95 D4
[*]Certificate File Hash (sha256): 6E 57 69 28 89 30 4D 1C AA 8F C6 AC 76 C2 58 D0 F6 E4 33 7E 30 F8 0F 9B 4F 04 9C B2 F7 38 59 23
[*]Certificate Thumbprint (sha256): 93 A0 78 98 D8 9B 2C CA 16 6B A6 F1 F8 A1 41 38 CE 43 82 8E 49 1B 83 19 26 BC 82 47 D3 91 CC 72
[/LIST]
[/LIST]

[LIST]
[*]Starfield Secure Server Certificate (Intermediate Certificate) (DER Format) - G2
[LIST]
[*][sfig2.crt.der]("https://certs.godaddy.com/anonymous/repository.pki;jsessionid=p4-YqJ+O5o1vnL8wZ99JlA__.p3p02jb?streamfilename=sfig2.crt.der&actionMethod=anonymous%2Frepository.xhtml%3Arepository.streamFile%28%27%27%29&cid=136493")
[*]Certificate File Hash (sha1): 7E DC 37 6D CF D4 5E 6D DF 08 2C 16 0D F6 AC 21 83 5B 95 D4
[*]Certificate Thumbprint (sha1): 7E DC 37 6D CF D4 5E 6D DF 08 2C 16 0D F6 AC 21 83 5B 95 D4
[*]Certificate File Hash (sha256): 93 A0 78 98 D8 9B 2C CA 16 6B A6 F1 F8 A1 41 38 CE 43 82 8E 49 1B 83 19 26 BC 82 47 D3 91 CC 72
[/LIST]
[/LIST]
[/FONT]


There's also this:
> **"GoDaddy"][COLOR=#000000][FONT=Arial]**All Intermediate CA Certificates**[/FONT][/COLOR]
[LIST]
[*]PKCS#7 Bundle
[LIST]
[*][URL="https://certs.godaddy.com/anonymous/repository.pki said:**
> all_intermediate_ca_certificates.p7b[/URL]
[*]Certificate File Hash (sha1): D5 76 A1 58 B1 8F 2A 18 7C 60 17 2F 19 E5 3E 8F 57 8A 67 7E
[*]Certificate File Hash (sha256): DF 65 59 CA BB E5 FA DF 25 CD 16 89 A3 7D 94 01 B5 A4 CF 2D 8F CF 87 CD A3 1E 89 9D 75 79 5D 66
[/LIST]
[/LIST]
[FONT=inherit]

Should I try to use the **all_intermediate_ca_certificates.p7b** file?  How might I go about converting this to be used with my PEM?

I believe my SSL certificate is a Starfield one, so maybe I only need the Starfield intermediate certificates.

Any guidance here would be appreciated. :)[/FONT]

---

### Post by CharlesA on 2013-12-08
Worth a shot, I guess.

Check this out:
[https://forum.startcom.org/viewtopic.php?t=699](https://forum.startcom.org/viewtopic.php?t=699)

---

### Post by Kirk Schnable on 2014-01-09
I've been experimenting this morning, and I created a pem file consisting of:
My Cert,
My Key,
sf_intermediate.crt,
sf_cross_intermediate.crt,
sf-class2-root.crt

So far it looks like this might not be generating the certificate errors on the clients.  I will keep everyone apprised. :)

---

### Post by Habitual on 2014-01-09
Please do, Kirk, as I may have to update my client's jabberd host soon enough.

---

### Post by Kirk Schnable on 2014-01-09
> **Habitual said:**
> Please do, Kirk, as I may have to update my client's jabberd host soon enough.

I believe my method worked.  So far, I have not seen any indications that the SSL certificate is invalid.  I have tested with Pidgin, Empathy, and Jitsi on several different computers and accounts.

I will update the thread if I find out I ran into any further difficulties.  If you need any help with your upgrade, just reply to this thread and I will do my best to assist you.

Essentially, to generalize this process for someone on a registrar other than GoDaddy...

**1. Locate your public certificate and private key.**  Your private key is what you generated before you issued your certificate sign request (CSR) to your SSL registry.  It is probably called "yourdomain.key".  Your certificate can be downloaded from your SSL provider.  It's probably called "yourdomain.crt".

**2. Locate any intermediate certificates.**  These can probably be downloaded from your SSL registry, as above for GoDaddy.  You need to figure out which registry you are with if you're a GoDaddy customer.  My particular certificate was Starfield Technologies, and it had no mention of G2.  I used the G1 intermediate certificates and they seemed to work.  The G2 ones caused the SSL certificate to fail and appear to be self-signed.  Using the right intermediate certificates is important!

**3. Locate the root CA certificate.**  This can also be found from your SSL registry's website.  

For steps 2 and 3, the files will be .crt files.  Save them with common sense names like "intermediate1.crt, intermediate2.crt, and rootca.crt".

**4. Combine all these files into your .PEM file.**
You can do so in a text editor like nano, vi, gedit... or you can just use cat.  Assuming you've used the filenames like I have above, your process will look something like this:

cat yourdomain.crt > yourdomain.pem
cat yourdomain.key >> yourdomain.pem 
cat intermediate1.crt >> yourdomain.pem
cat intermediate2.crt >> yourdomain.pem
cat rootca.crt >> yourdomain.pem

When you're done, the PEM file will look something like this.
```
-----BEGIN CERTIFICATE-----
contents of yourdomain.crt
-----END CERTIFICATE-----
-----BEGIN RSA PRIVATE KEY-----
contents of yourdomain.key
-----END RSA PRIVATE KEY-----
-----BEGIN CERTIFICATE-----
intermediate cert contents
-----END CERTIFICATE-----
-----BEGIN CERTIFICATE-----
2nd intermediate cert contents if applicable
-----END CERTIFICATE-----
-----BEGIN CERTIFICATE-----
root ca cert contents
-----END CERTIFICATE-----
```

Now yourdomain.pem is finished, and should be usable in your jabberd2 configuration files.

---

### Post by Habitual on 2014-01-09
Thanks Kirk!

---

### Post by Kirk Schnable on 2014-01-09
> **Habitual said:**
> Thanks Kirk!
No problem!

If you run into any issues feel free to hit me up.  I'm not an expert by any means but I've been running jabberd2 for a good few months in production now and I'm pretty familiar with the configuration process.

---

### Post by Habitual on 2014-01-10
Well, I'll keep that in mind, Thank you again and 
Have a Great Day!

---

