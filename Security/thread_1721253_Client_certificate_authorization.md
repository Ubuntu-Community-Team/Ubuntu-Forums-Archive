---
title: "Client certificate authorization"
date: 2011-04-04
forum: Security
---

### Post by Jontebullen on 2011-04-04
I am trying to perform client certificate authorization. I'm using Ubuntu 10.10, Apache2 and OpenSSL.
I've managed to get regular https browsing to my server to work, but (for now) I want only people with a certificate from me to be able to access /auth. It is not working.
I have signed a certificate and installed it in my browser (Chrome and FF) and a pop-up asks me if I want to use this certificate to validate myself when browsing to /auth, I choose OK, but Chrome delivers the following result:

```
SSL connection error
Unable to make a secure connection to the server. This may be a problem with the server, or it may be requiring a client authentication certificate that you don't have.
Error 107 (net::ERR_SSL_PROTOCOL_ERROR): SSL protocol error.
```

Apache error log:

```
[Mon Apr 04 14:54:27 2011] [error] [client x.x.x.x] Re-negotiation handshake failed: Not accepted by client!?
[Mon Apr 04 14:54:28 2011] [error] [client x.x.x.x] Certificate Verification: Error (26): unsupported certificate purpose
[Mon Apr 04 14:54:28 2011] [error] [client x.x.x.x] Re-negotiation handshake failed: Not accepted by client!?

```

httpd.conf:


```
# ServerName is to be specified to avoid warning during reload
ServerName xxx.no-ip.org

# require a client certificate which has to be directly
# signed by our CA certificate in ca.crt

SSLVerifyClient none
SSLCACertificateFile /home/xxx/myCA/cacert.crt

<Location /auth>
SSLVerifyClient require
SSLVerifyDepth 1
</Location>
```

Relevant section of site-available/default:

```
<VirtualHost *:443>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        SSLEngine on
        SSLOptions +StrictRequire

        SSLCertificateFile /home/xxx/myCA/server_crt.pem
        SSLCertificateKeyFile /home/xxx/myCA/server_key.pem

```


I've been stuck for like two weeks now and decided I need some help. What can I try? I guess I'm not the most skilled ubuntu/unix dude out there..

---

### Post by BkkBonanza on 2011-04-04
The error msg seems to indicate an incorrect certificate purpose. 

Make sure the cert installed in your browser is a **client** certificate (not server or CA). Make sure the one provided to the server for SSLCACertificateFile is actually a **Certificate Authority** cert. And then if you want to use SSL then make sure the one for SSLCertificateFile is a **server** cert. These are all different usage restrictions in the actual cert file. 

If you open a cert in any viewer (browser too) it should show the intended purpose. So you have 3 different purposes here: CA for verifying the other two, server for providing ssl connection, client for identity of user attempting to use /auth.

---

### Post by Jontebullen on 2011-04-04
Well, looking at the user_crt.pem that I used for my p12 and imported into my browser I find:

```
Netscape Cert Type:
                SSL Server
```

I have been following this guide: [https://help.ubuntu.com/community/OpenSSL#SSL Certificates](https://help.ubuntu.com/community/OpenSSL#SSL Certificates) most of the time, and I assume this:

```
nsCertType              = server
```
has something to do with my cert type being server? But I mean that is in the caconfig.cnf in the section "x509 extensions to use when generating server certificates." so.. does it have any effect when I sign client certificates?
How should I make a client certificate?

---

### Post by BkkBonanza on 2011-04-04
I'm pretty sure that you can't use a server cert for client purposes. But I haven't tried that myself. I browsed thru the help page link you posted and it seems to be mostly aimed at server certs, except for one part further down where they mention converting to a client cert. I found that part a bit confusing as it seems mixed up with a CA cert.

I haven't used openssl at the cmd line for a couple years now since I found a much easier way to do it. I would suggest you may find it easier the way I do it all now, which is... use Synaptics to install TinyCA, a gui interface for openssl.

Once TinyCA is there you can import your CA cert into it or just start fresh (probably better). In TinyCA you can create your Certificate Authority, create a server cert for your server, and easily create a client cert for authenticating as a client. I find it very easy to manage my own little CA and the certs I've issued with this tool.

I import my CA cert into Firefox (as an Authority, not as client) so that any of my self-signed certs are valid without a popup warning. Then I import my client cert into Firefox (as a client cert). And then I put my server cert and key onto the server for Apache (Nginx in my case actually).

Note that in Firefox it has 3 tabs (People, Servers, Authorities) and I think it's the people one that is for client certs. Each tab has an import for that type of cert. Client certificates are usually identified by email address.

[StartSSL.com]("http://www.startssl.com/") also issues free client/server certs that are actually recognized by browsers as well. It may help to get one there as a reference case to see how it works since their site requires a client cert to login (and associates the cert with an OpenID for use on many sites).

Edit:
I think you're probably doing most of this right except for the client part. I had a quick look around and found this page which seems to lay out the steps more clearly (though obviously you don't have to use Windows as a client here).

[http://www.impetus.us/~rjmooney/projects/misc/clientcertauth.html](http://www.impetus.us/~rjmooney/projects/misc/clientcertauth.html)

Edit again:
Here is another good tutorial. It has the advantage that he tells you how to require more than just a client cert but also only one with certain details like organization and organization unit allowing for more limitation and control.

[http://www.garex.net/apache/](http://www.garex.net/apache/)

---

### Post by Jontebullen on 2011-04-06
ok, I've installed tinyCA and created a new CA, I exported the server cert to my webserver and got https up and running with the new certificate, but I couldn't figure out how to export my CA key, which leads to me not being able to start apach again...

The part of my /site-available/default that handles SSL now looks like this:

```
        SSLEngine on
        SSLOptions +StrictRequire

        SSLCertificateFile /home/xxx/xxx_server_.pem

```and httpd.conf:

```
        SSLEngine on
        SSLOptions +StrictRequire

        SSLCertificateFile /home/xxx/xxx_server.pem

```If I add this row:

```
[FONT=Arial][COLOR=#000000]SSLCertificateKeyFile /etc/ssl/private/server.key[/COLOR][/FONT]
```and point it to my old key I can start the webserver but the client-authorization (obviously?) fails..

apache error.log when using no key:
```
[Wed Apr 06 09:16:54 2011] [error] Init: Private key not found
[Wed Apr 06 09:16:54 2011] [error] SSL Library Error: 218710120 error:0D094068:asn1 encoding routines:d2i_ASN1_SET:bad tag
[Wed Apr 06 09:16:54 2011] [error] SSL Library Error: 218529960 error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag
[Wed Apr 06 09:16:54 2011] [error] SSL Library Error: 218595386 error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error
[Wed Apr 06 09:16:54 2011] [error] SSL Library Error: 218734605 error:0D09A00D:asn1 encoding routines:d2i_PrivateKey:ASN1 lib

```so.. how do I export my new key from tinyCA? Or should I create my CA outside of tinyCA and import it? (can you import a key but not export?).
tinyCA looks good and seems easier than openssl cli though! :D


edit:
looking at the first link you posted it seems the difference between making a server certificate and a client certificate is quite minimal:

```
openssl genrsa -out server.key 1024
openssl req -new -key server.key -out server.csr
openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt

openssl genrsa -out client.key 1024
openssl req -new -key client.key -out client.csr -config openssl.cnf
openssl x509 -req -days 365 -CA ca.crt -CAkey ca.key -CAcreateserial -in client.csr -out client.crt
```

if I look in my openssl.cnf all lines containing nsCertType are commented:

```
# Here are some examples of the usage of nsCertType. If it is omitted
# the certificate can be used for anything *except* object signing.

# This is OK for an SSL server.
# nsCertType                    = server

# For an object signing certificate this would be used.
# nsCertType = objsign

# For normal client use this is typical
# nsCertType = client, email

# and for everything including object signing:
# nsCertType = client, email, objsign

```

when making for example a cliet certificate, should I uncomment the line where the nsCertType is 'client, email' before making a request?

---

### Post by BkkBonanza on 2011-04-06
When I use TinyCA there is a menu button on the CA tab for "Export". Just click that and select format PEM or DER (probably PEM I think). 

When on the Certificates tab click "New" and it has a small menu for server or client choices. I choose "client" when creating a client certificate.

I don't recall anything about the cnf file - it's really been years since I messed with that. I would expect the difference between server and client is just one flag in the file indicating intended usage restriction, not anything more than that. When I open the certificates in the browser it has a usage of either "server" or "email" indicated.

---

### Post by Jontebullen on 2011-04-06
> **BkkBonanza said:**
> When I use TinyCA there is a menu button on the CA tab for "Export". Just click that and select format PEM or DER (probably PEM I think).

Yeah I managed to do that, and export my ca certificate, but I can't seem to export my ca key, which is needed for everything to work, isn't it?

Btw I greatly appreciate your help :)

---

### Post by BkkBonanza on 2011-04-06
I think you need the CA cert for the server not the key. The key you need is the server key. The CA key is extremely confidential - anyone having that could create and issue certs as your CA, which would be bad. 

Apache needs:
CA cert (signed by CA key)
Server key (generated by server admin)
Server cert (signed by CA key when given csr)

User needs:
Client key (generated by user)
Client cert (signed by CA key when given csr)

If you want no message to popup in the browser then you also import the CA cert as an authority in the browser.

The CA key is the precious gold that no one ever gets to play with. Usually the root CA key is truly protected and intermediate CA keys are generated for day to day use as these can be easily revoked without wiping out the validity of every signature ever done. TinyCA allows for this second level as well - on the CA screen you can create a SubCA and work with that as CA (but that's another issue now).

Note - the server key is needed for encryption but the CA cert is just used to verify authenticity of the client.

---

### Post by Jontebullen on 2011-04-08
yeah ok that seems right, I had mixed up server key with ca key..

my setup now:

httpd.conf:

```
SSLVerifyClient none
SSLCACertificateFile /home/xxx/ca1-cacert.pem

<Location /auth>

SSLVerifyClient require
SSLVerifyDepth 1
</Location>

```

sites-available/default:

```
        DocumentRoot /var/www
        SSLEngine on
        SSLOptions +StrictRequire

        SSLCertificateFile /home/xxx/server_cert.pem
        SSLCertificateKeyFile /home/xxx/server_key.pem

```

error.log:
```

[Fri Apr 08 14:58:33 2011] [error] [client x.x.x.x] Re-negotiation handshake failed: Not accepted by client!?
[Fri Apr 08 14:58:35 2011] [error] [client x.x.x.x] Re-negotiation handshake failed: Not accepted by client!?

```


AND WOW now as I was writing this post I realized I had been testing in the wrong browser for the last 10 mins, and IT IS WORKING!!

WOOOOOOOOOOOOOOOOOOOHO!

I exported the client certificate from tinyca, from the client-certificate section. If I inspect the certificate installed in my browser it says the Netscape Certificate Type is 

```
Not Critical
SSL Client Certificate
Email
Object Signer
```

Not client, but at least email (and definitely not server). It seems tinyca removes the readable parts of certificates because when I just look at it with 'cat' or something as I did with my own certificates I could read the nsCertType-field there, but now there's no human-readable text.

Thanks so much for the help BkkBonanza! :D IT WORKS!

---

### Post by BkkBonanza on 2011-04-08
Good to hear it worked out. :)

---

