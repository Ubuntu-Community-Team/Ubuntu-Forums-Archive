---
title: "Can I sign client SSL certs with a commercial cert?"
date: 2010-01-11
forum: Security
---

### Post by waynemr on 2010-01-11
I have an SSL certificate for my website, which is signed by Verisign. I would like to generate client SSL certs that are signed by my website cert. Does anyone know if this is possible?

I have found some references about generating signed client SSL certificates, which are created after you configure a Certificate Authority (CA) on your server. In those examples, though, they always use self-signed certificates as the basis for their CA.

In my case, I guess I need to establish a CA, using my cert that has been signed by the Verisign CA. Anyway, I was just curious if it was as simple as that - just configuring my CA with my commercial cert - or if there was more to it.

Thanks!

Reference links about client SSL signing
[http://www.securityfocus.com/infocus/1823](http://www.securityfocus.com/infocus/1823)
[http://www.garex.net/apache/#CCusign](http://www.garex.net/apache/#CCusign)

---

### Post by bodhi.zazen on 2010-01-12
> **waynemr said:**
> In my case, I guess I need to establish a CA, using my cert that has been signed by the Verisign CA. Anyway, I was just curious if it was as simple as that - just configuring my CA with my commercial cert - or if there was more to it.

This ^^

simply use the commercial cert to sign

---

### Post by waynemr on 2010-01-12
> **bodhi.zazen said:**
> This ^^

simply use the commercial cert to sign


So, something like...

openssl x509 -req -days 365 -in myclient.csr -signkey mycommercial.key -out myclient.crt

(myclient.csr = the signing request generated from the new client cert I made
mycommercial.key is the web server's key that has been signed by Verisign)


...without any need to setup a CA?

Then convert myclient.crt + myclient.key into pkcs12.

I guess I can give it a shot, but I thought there were some parameters, like policy=policy_anything and extensions=ssl_client that had to get loaded into the signed crt file that gets generated.

---

### Post by bodhi.zazen on 2010-01-12
I am not understanding what you are wanting to do exactly.

Does this link help ?

[http://www.howtoforge.com/secure_websites_using_openssl_and_apache](http://www.howtoforge.com/secure_websites_using_openssl_and_apache)

---

### Post by BkkBonanza on 2010-01-12
I think you can sign your client certs with your commercial one but that doesn't make those certs trusted. I'm pretty sure the trust of verisign isn't relayed onto your signings. Can you imagine if that were the case?

It's easy to form your own CA but that CA will have no trust in the public at large so every time a cert signed by it is used a warning will be shown - or should be anyway.

If you need client certificates that are trusted I would recommend startssl.com. They are trusted by almost all browsers and email clients and offer client signings for free, verified by an email address. Commodo also does this but I think almost all the others have dried up now.

---

### Post by waynemr on 2010-01-12
First, thank you bodhi.zazen and BkkBonaza.

To explain more clearly what I am trying to accomplish, let me fill out some details:

[LIST]I created a SSL key (myexample.key) for my website (let's call it myexample.site)[/LIST]
[LIST]I generated a CSR from myexample.key - so I now have myexample.key and myexample.csr[/LIST]
[LIST]I submitted myexample.csr to my commercial Certificate Authority (CA)[/LIST]
[LIST]The commercial CA uses myexample.csr to create myexample.crt, which is signed and trusted[/LIST]
[LIST]The CA sends me myexample.crt and they send me their PEM file - CAname.pem[/LIST]
[LIST]At this point, I have myexample.key (the private key),  myexample.crt (the trusted and signed public certificate), and CAname.pem (public info on the source that trusts myexample.crt)[/LIST]
[LIST]I modify my Apache configuration to use mod_ssl and I reference myexample.crt, myexample.key, and CAname.pem[/LIST]
[LIST]I restart Apache and now access to https: // myexample.site is secured and does not generate any warning messages[/LIST]
[LIST]Now, I decide that I want to restrict access to myexample.site/securefolder so that only a user presenting a client SSL certificate can get access - to do this, I want to generate client SSL certs and sign them with myexample.crt[/LIST]

Everywhere I searched, to sign the client SSL cert, the instructions talk about creating my own CA and then signing the client certs. However, all of those examples use a self-signed cert for setting up the local CA.

BkkBonaza brings up a good point that I cannot expect to convey the trust from my commercial CA provider to any client certs I sign with my server cert - but actually, I think that is OK, because it would be my server that would need to trust the client's cert. In theory, if the client cert has been signed by server cert, then my server should trust it.

In other words:
[LIST]The user goes to myexample.site/securefolder[/LIST]
[LIST]Their browser does the HTTPS handshake with my server and they get a copy of my server cert, which is trusted because my commercial CA is already in their list of trusted certs in the browser[/LIST]
[LIST]the site requests that they send a client cert before getting access to the content, though, and their browser submits the client cert that has been already signed by the server cert[/LIST]
[LIST]The server accepts the client cert as trusted and the user gets the content[/LIST]

My concern here, though, is that the functionality of the server getting and inspecting the client SSL cert - that logic - is bound with configuring a local CA. So, if no local CA exists, perhaps Apache cannot inspect a client SSL cert.

I'll give it a shot and see what I can come up with. Then, I'll take a crack at doing a quick write-up to contribute to the community.

---

### Post by BkkBonanza on 2010-01-12
If this is only for clients login to your server then you should be good. You need to create your own CA and add the CAcert to your servers CA bundle. See openssl for how to add a CA to your server "bundle". It usually means adding to a certain directory or appending to the cert file already present.

Once you've done that then you can sign and distribute certs for your clients only and they should be able to use them without warnings on your site only. However, this IS using a self signed cert as your CA cert but that should work fine. It's only an issue when someone tries to use their cert on another site which doesn't trust your CA.

Your users can create their own cert for your site by using the built in browser functions to generate a csr that your site will sign for them. This is the same as if you go to Verisign/Commodo/StartSSL to get a client cert except that theirs are trusted everywhere but yours is trusted only by yourself.

I have googled before and come across example JS code for handling the csr signing in the browser and how to do it on your site but I didn't bookmark it. I'm sure you can find it.

Edit: Note that the client csr signing is handled through the browser which generates your users private key, and csr. It adds the private key to the browsers cert store and gives you the csr to sign. You sign the public key (cert) and give it back as their client cert. It works this way so that you never get the private key. They should backup the certificate from the browser store for safety.

There is a nifty tinyCA gui CA manager app in Synaptics you may want to try out. It does all the stuff with openssl but makes a nice interface for testing and managing your own CA. I'm pretty sure there's some way to tie it's cert store to the one used by Apache.

---

### Post by waynemr on 2010-01-12
> **BkkBonaza said:**
> ...See openssl for how to add a CA to your server "bundle". It usually means adding to a certain directory or appending to the cert file already present...

Ah yes, the PEM file. OK, I think it is starting to gel in my mind a little. I'll try to put it together after lunch and see what happens :)

---

### Post by BkkBonanza on 2010-01-12
Ya, I'm just going by memory but somewhere there is a directory that contains all the trusted CA certs that openssl will accept. You add yours there and it will trust you too. I had to do this a couple years back as I use my own cert for communicating between my own servers. Curl (which depends on openssl like apache) wouldn't accept my SSL connections until I added my own cert there.

---

### Post by bodhi.zazen on 2010-01-12
> **waynemr said:**
> Ah yes, the PEM file. OK, I think it is starting to gel in my mind a little. I'll try to put it together after lunch and see what happens :)

Awesome, and post back if you have a problem.

Thank you to [BkkBonaza]("http://ubuntuforums.org/member.php?u=550406")

---

### Post by waynemr on 2010-01-12
no joy so far...

Just for grins, I took a copy of my signed CRT file for my server and the KEY file and used it to setup a local CA. Then, I generated a new client KEY and client request PEM. I used the client PEM in my CA to create a signed client PEM. Then I exported the signed client PEM to a P12 file. Then, I tried to import the P12 file into both IE 7 and FF 3.5.7. Finally, I configured my secure folder to require a client SSL certificate. Since the entire site is using the server CRT and KEY I used for my local CA, I was hoping everything would work out.

It appears like the import was successful to the browsers, but when I actually go to the directory where a client SSL cert is required, no certs are available in either IE or FF. Actually, FF gives me the following error message:

SSL peer was unable to negotiate an acceptable set of security parameters.

So, I think somehow the client P12 file I created was invalid - which is why it does not show up as an available cert to select when browsing to the restricted folder - either that or perhaps I need to explicitly trust the server CRT on my desktop.

Anyway, I am going to go back and generate a self-signed server cert, use that in my local CA, sign the client cert and then see if I can use the self-signed server cert on the restricted folder, while using the commercially signed server cert for the rest of the site. I figure the people I have in mind, who need to get to the secure folder are savvy enough to trust the self-signed cert if directed to do so.

Or... as suggested by a co-worker, I could just use encrypted cookies for application-level, 2-part authentication.

---

### Post by waynemr on 2010-01-12
OK, it is not possible to issue the SSLCertificateFile directive in a <Directory></Directory> area of the Apache config... so, it is not possible to use one set of server certs in one area of a website and a different set of certs in another. I guessed as much, but I wanted to try it out, just to make sure.

At this point, I think my options are:

install a self-signed certificate on my website and use it as the basis for a local certificate authority - and then issue signed client certificates from that local CA.

or, use some form of encrypted cookies at the application layer

---

### Post by BkkBonanza on 2010-01-12
I'm not sure how you configure a client cert for user authentication but I do know it's not handled the same as the SSL server certificate. I would look into the details for using OpenID since it uses (or can use) a client cert in this way. It may shed some light on it.

---

