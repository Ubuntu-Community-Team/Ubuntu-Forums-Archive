---
title: "Apache SSL certificate"
date: 2015-04-16
forum: Server Platforms
---

### Post by aaron27 on 2015-04-16
I am having some issues getting a certificate working in Apache on ubuntu 14.04 LST. 
I have been in contact on a different forum as we are using the server for Owncloud. [https://forum.owncloud.org/viewtopic.php?f=31&t=27514&start=50](https://forum.owncloud.org/viewtopic.php?f=31&t=27514&start=50)

---

### Post by Gunjan_Tripathi on 2015-04-16
I think you have a problem with installation, and referred link regarding installation will work for you. [https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)

---

### Post by aaron27 on 2015-04-16
I have already gone through that process and have the owncloud site working with a self signed certificate. I am now trying to do the same but with a CA signed certificate, i have followed instructions on [https://www.digitalocean.com/community/tutorials/how-to-install-an-ssl-certificate-from-a-commercial-certificate-authority](https://www.digitalocean.com/community/tutorials/how-to-install-an-ssl-certificate-from-a-commercial-certificate-authority) but i am getting errors still.


I have adjusted the default apache2 config and apache ssl config files.  however when i try to start the apache2 service i get the following:

```

* Starting web server apache2
*
*The apache2 configtest failed.
Output of config test was:
AH00526: Syntax error on line 10 of /etc/apache2/sites-enabled/000-default-config: ServerAlias only used in <VirtualHost>
Action 'configtest' failed.
The apache erorr log may have more information.


```

I  have googled this and it states that ServerAlias needs to be within the  <VirtualHost_default_:443> section which upon checking, there is  no <VirtualHost_default_:443> in the default config, this only  appears in the ssl config file. both default and ssl config files have  ServerName and ServerAlias set in them.

---

### Post by SeijiSensei on 2015-04-16
Did you look specifically at line 10 of /etc/apache2/sites-enabled/000-default-config which is where the error is flagged?

One issue might be that, on 14.04 with Apache 2.4, all the virtual host definition files must end in .conf unless you changed the default configuration.  I don't know why Apache is even reading 000-default-config.

---

### Post by aaron27 on 2015-04-16
I have to admit i dont know why it is either as I was expecting it to read the ssl config file. 
I have looked at line 10 and it is ServerAlias *.ourdomain.co.uk

---

### Post by darkod on 2015-04-16
If it worked with local cert but not with CA cert, make sure you have the cert, key, CA root cert and any intermediary cert configured correctly. In many cases you can specify only one root cert so you have to concatenate the CA and intermediary in correct order. You can also add the main cert too so you have the whole chain in single file. In such case in apache you need parameters for only the one chained file and the key. I don't have links at hand now. I can post later if you are still stuck.
Which files did your CA send you? How many and their names (the name doesn't have any classified info I think, so you can post it here).

---

### Post by aaron27 on 2015-04-16
The CA sent two files to us. Both .crt files. their names are
961dbcd5edd5d616.crt and gd_bundle-g2-g1.crt
It is a wildcard certificate and when following the instructions on the link i posted earlier i am told to create the .key and .csr files in ubuntu itself which i have done and are named *.ourdomain.co.uk 
The first crt file is the renamed *.hpcplc.co.uk.crt and the 2nd is renamed intermediate.crt 

I am assuming the link is correct in telling me to do this?

---

### Post by darkod on 2015-04-16
I wouldn't use a * in filenames since it's a wildcard but it shouldn't be an issue. Can you post the part of the ssl config files where you set the cert parameters?

---

### Post by aaron27 on 2015-04-16
I certainly can let me find them, just a side note i have tried without the * and i had the exact same issue. however i will post the parameters in a moment

---

### Post by aaron27 on 2015-04-16
Ok just to clarify from an earlier post on here, all the files are named .config so that is correct.

In the first file 000-default.conf (/etc/apache2/sites-enabled)
I have set ```
ServerName ourdomain.co.uk
               ServerAlias owncloud.ourdomain.co.uk

               DocumentRoot /var/www/owncloud
```

There is more in here but it is quoted out so no reason to include.

The following is the SSL config file.
```

<IfModule mod_ssl.c>
    <VirtualHost _default_:443>
        ServerAdmin webmaster@localhost
        ServerName ourdomain.co.uk
        ServerAlias owncloud.ourdomain.co.uk

        DocumentRoot /var/www/owncloud

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf

        #   SSL Engine Switch:
        #   Enable/Disable SSL for this virtual host.
        SSLEngine on

        #   A self-signed (snakeoil) certificate can be created by installing
        #   the ssl-cert package. See
        #   /usr/share/doc/apache2/README.Debian.gz for more info.
        #   If both key and certificate are stored in the same file, only the
        #   SSLCertificateFile directive is needed.
        SSLCertificateFile    /etc/ssl/certs/keys/*.ourdomain.co.uk.crt
        SSLCertificateKeyFile /etc/ssl/certs/keys/*.ourdomain.co.uk.key

        #   Server Certificate Chain:
        #   Point SSLCertificateChainFile at a file containing the
        #   concatenation of PEM encoded CA certificates which form the
        #   certificate chain for the server certificate. Alternatively
        #   the referenced file can be the same as SSLCertificateFile
        #   when the CA certificates are directly appended to the server
        #   certificate for convinience.
        SSLCertificateChainFile /etc/ssl/certs/keys/*.ourdomain.co.uk.crt

        #   Certificate Authority (CA):
        #   Set the CA certificate verification path where to find CA
        #   certificates for client authentication or alternatively one
        #   huge file containing all of them (file must be PEM encoded)
        #   Note: Inside SSLCACertificatePath you need hash symlinks
        #         to point to the certificate files. Use the provided
        #         Makefile to update the hash symlinks after changes.
        SSLCACertificatePath /etc/ssl/certs/keys
        SSLCACertificateFile /etc/ssl/certs/keys/intermediate.crt

        #   Certificate Revocation Lists (CRL):
        #   Set the CA revocation path where to find CA CRLs for client
        #   authentication or alternatively one huge file containing all
        #   of them (file must be PEM encoded)
        #   Note: Inside SSLCARevocationPath you need hash symlinks
        #         to point to the certificate files. Use the provided
        #         Makefile to update the hash symlinks after changes.
        #SSLCARevocationPath /etc/apache2/ssl.crl/
        #SSLCARevocationFile /etc/apache2/ssl.crl/ca-bundle.crl

        #   Client Authentication (Type):
        #   Client certificate verification type and depth.  Types are
        #   none, optional, require and optional_no_ca.  Depth is a
        #   number which specifies how deeply to verify the certificate
        #   issuer chain before deciding the certificate is not valid.
        #SSLVerifyClient require
        #SSLVerifyDepth  10

        #   SSL Engine Options:
        #   Set various options for the SSL engine.
        #   o FakeBasicAuth:
        #     Translate the client X.509 into a Basic Authorisation.  This means that
        #     the standard Auth/DBMAuth methods can be used for access control.  The
        #     user name is the `one line' version of the client's X.509 certificate.
        #     Note that no password is obtained from the user. Every entry in the user
        #     file needs this password: `xxj31ZMTZzkVA'.
        #   o ExportCertData:
        #     This exports two additional environment variables: SSL_CLIENT_CERT and
        #     SSL_SERVER_CERT. These contain the PEM-encoded certificates of the
        #     server (always existing) and the client (only existing when client
        #     authentication is used). This can be used to import the certificates
        #     into CGI scripts.
        #   o StdEnvVars:
        #     This exports the standard SSL/TLS related `SSL_*' environment variables.
        #     Per default this exportation is switched off for performance reasons,
        #     because the extraction step is an expensive operation and is usually
        #     useless for serving static content. So one usually enables the
        #     exportation for CGI and SSI requests only.
        #   o OptRenegotiate:
        #     This enables optimized SSL connection renegotiation handling when SSL
        #     directives are used in per-directory context.
        #SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
        <FilesMatch "\.(cgi|shtml|phtml|php)$">
                SSLOptions +StdEnvVars
        </FilesMatch>
        <Directory /usr/lib/cgi-bin>
                SSLOptions +StdEnvVars
        </Directory>

        #   SSL Protocol Adjustments:
        #   The safe and default but still SSL/TLS standard compliant shutdown
        #   approach is that mod_ssl sends the close notify alert but doesn't wait for
        #   the close notify alert from client. When you need a different shutdown
        #   approach you can use one of the following variables:
        #   o ssl-unclean-shutdown:
        #     This forces an unclean shutdown when the connection is closed, i.e. no
        #     SSL close notify alert is send or allowed to received.  This violates
        #     the SSL/TLS standard but is needed for some brain-dead browsers. Use
        #     this when you receive I/O errors because of the standard approach where
        #     mod_ssl sends the close notify alert.
        #   o ssl-accurate-shutdown:
        #     This forces an accurate shutdown when the connection is closed, i.e. a
        #     SSL close notify alert is send and mod_ssl waits for the close notify
        #     alert of the client. This is 100% SSL/TLS standard compliant, but in
        #     practice often causes hanging connections with brain-dead browsers. Use
        #     this only for browsers where you know that their SSL implementation
        #     works correctly.
        #   Notice: Most problems of broken clients are also related to the HTTP
        #   keep-alive facility, so you usually additionally want to disable
        #   keep-alive for those clients, too. Use variable "nokeepalive" for this.
        #   Similarly, one has to force some clients to use HTTP/1.0 to workaround
        #   their broken HTTP/1.1 implementation. Use variables "downgrade-1.0" and
        #   "force-response-1.0" for this.
        BrowserMatch "MSIE [2-6]" \
                nokeepalive ssl-unclean-shutdown \
                downgrade-1.0 force-response-1.0
        # MSIE 7 and newer should be able to use keepalive
        BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown

    </VirtualHost>
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

---

### Post by darkod on 2015-04-16
OK, first of all about that error upon staring apache. Unfortunately I'm not apache expert... Is that message only a warning, and the service starts, or it stops the service from starting?

If it stops the service from starting, how do you even know that your SSL cert is not working good? You can't test without apache running.

As for the ssl config you posted. There are small errors in it.

1. Since your CA sent you two files only, there is no intermediate cert (it's probably already included in gd_bundle...). So, you have the server cert and the CA cert. That's why in the ssl config comment out the SSLCertificateChainFile parameter. It doesn't look like you have a file to chain.

2. According to post #7 you renamed the server cert to *.hpcplc.co.uk.crt but in your SSLCertificateFile you use *.ourdomain.co.uk.crt. Unless you translated 'hpcplc' to 'ourdomain' when pasting the config content, that is a mistake in the config file. The key parameter is correct since when creating the key and CSR you said you used *.ourdomain.co.uk.key but once you got the server cert the SSLCertificateFile should point to it. That parameter should be identical to your server cert file.

The rest looks good, the SSLCACertificateFile points to intermediate.crt which is what you received from the CA and you renamed. Of course, make sure all files are in that folder.

---

### Post by SeijiSensei on 2015-04-16
The 000-default.conf file sets up unencrypted connections on port 80.  If you put a ServerAlias entry in that file, it needs to be inside of a <VirtualHost> container which is what the original error reported.

If you don't want to accept unencrypted connections, I'd disable the default configuration.

---

### Post by aaron27 on 2015-04-17
Haha yes ourdomain is hpcplc - so they are all named the same, in my rush to get this posted to fix asap i have mistakenly posted the name without realising. so much for keeping that anonymous.

---

### Post by darkod on 2015-04-17
Ok. But did you disable SSLCertificateChainFile parameter? It says to use it for the chain files but in your case all of the are in intermediate.crt. So that parameter should not point to your server .crt also. At least I have it working like that.

Also disable the SSLCACertificatePath parameter. The path is included in the File parameter. If you specify the path additionally I'm not sure if it can confuse it.

---

### Post by aaron27 on 2015-04-17
I have disabled both of those and the default config, however apache service still wont start and i cannot access the site either

---

### Post by darkod on 2015-04-17
Apache not starting is not related to cert config. Even if the cert is not set up correctly it should open the page but there will be a warning about security.
Did you try what Sensei suggested about ServerAlias? If the error message from apache is still the same look real good in that line to try figure out the issue. It might even be something really stupid like punctuation etc.

---

### Post by aaron27 on 2015-04-17
I have done his recommendation of turning that off as we dont want unencrypted connections, so that file wont be read anymore.

I now just get a message saying the service couldnt be started and didnt start within 20 seconds.

---

### Post by darkod on 2015-04-17
Try looking into logs for clues. Sorry I don't know where the apache log is on the top of my head. Google should help you find the path.
Also check /var/log/dmesg and /var/log/messages for anything related to apache not starting.
One option is to use the original sample config file and see if it works. Do small chages bit by bit and you can see what stopped it working if it happens again. Do minimum changes, only what you need (like domain name and cert).

---

### Post by SeijiSensei on 2015-04-17
The error log is stored in /var/log/apache2/error.log.  It should be the first place you look when things go wrong.  Open a terminal, then run the command
```
sudo tail -f /var/log/apache2/error.log
```
Now open another terminal and try to start Apache.  You'll see the errors in the first window.

You might also need to disable the "Listen 80" directive in /etc/apache2/ports.conf to get Apache to listen only on the HTTPS port.  Apache might be complaining that it doesn't have a configuration to handle port 80 requests, but without the log entries we're shooting in the dark here.

Modified ports.conf:
```

#Listen 80

<IfModule ssl_module>
        Listen 443
</IfModule>

<IfModule mod_gnutls.c>
        Listen 443
</IfModule>

```

On Debian/Ubuntu, system messages are stored in /var/log/syslog, not /var/log/messages.  That's the filename that RedHat and its derivatives use.

---

### Post by aaron27 on 2015-04-29
Good morning,

I am getting a key error message in the apache logs now, however i can only confirm what i set as details for the .key and .csr files how can i check the contents of the .crt files.

To make sure i havent missed anything i have now started from scratch on this. I have re-created all the files i need and set them up as before. 

The error log in /var/log/apache2/error.log shows the following:

```
 
[Wed Apr 29 11:59:00.664290 2015] [ssl:emerg] [pid 3537] AH02238:
Unable to configure RSA server private key
[Wed Apr 29 11:59:00.664353 2015] [ssl:emerg] [pid 3537] SSL Library
Error: error:0B080074:x509 certificate
routines:x509_check_private_key:key value mismatch
[Wed Apr 29 11:59:00.664359 2015] [ssl:emerg] [pid 3537] AH02311:
Fatal error initialising mod_ssl, exiting. See /var/log/apache2/
error.log for more information

```

I  have rebooted the machine to make sure nothing is awaiting a reboot.

I also tried running the following:

```
 openssl rsa -noout -modulus -in server.key | openssl md5
openssl x509 -noout -modulus -in server.crt | openssl md5 
```

But if i do this i get an errror (for both) saying there is no such file or directory - do you need to specify the location when typing '-in server.key'? or should it just find the files?

This is becoming a real pain now, i have triple checked that i have all the correct information and files. Unless the instructions on the link below are wrong in some way?

[https://www.digitalocean.com/community/tutorials/how-to-install-an-ssl-certificate-from-a-commercial-certificate-authority](https://www.digitalocean.com/community/tutorials/how-to-install-an-ssl-certificate-from-a-commercial-certificate-authority)

Kind regards
Aaron

---

### Post by Kenneth_Benson on 2015-04-29
Is the 00-default.conf file in sites-enabled as well as site-available? If it is please use the a2dissite(spelling :P) program to remove it. Otherwise, what you have 'looks' correct to me.

---

### Post by aaron27 on 2015-04-30
Hi Kenneth, 

Thanks for the advice I have run the a2dissite command and it confirmed that 000-default.conf has been disabled however apache service still won't start with the same key mismatch error as posted yesterday.

---

### Post by darkod on 2015-04-30
It might sound like a stupid question but did you doublecheck that you are using the correct files for the certificate? And looking at the correct config files?
From the error log apache is obviously bothered by the key pair (file) used. And computers don't make mistakes, we do. Even if we think we got it right. Just make sure you are using the correct files after recreating the setup. That would include getting a new cert from your provider if you are using external cert.

---

### Post by aaron27 on 2015-04-30
Thank you for your reply, I thought the same as you and have now re-done the Key Pair file twice from fresh and I am still getting this error. I want to check the crt file and key file but I dont know how to check the contents, as stated previously the openssl commands i found to compare the contents do not work as they state they cannot find the file. 

I know the PC is right in saying something isnt matching just want to be able to find where so i can change it to be correct.

---

### Post by darkod on 2015-04-30
Unfortunately I'm at work now and it's not easy to check that digitalocean link on my mobile. I will take a better look when at home. Apache is complex and has many config options but this part for the certs is rather straightforward. We should be able to figure it out...

---

### Post by aaron27 on 2015-04-30
Ok thank you for your help, i await your reply :)

---

### Post by darkod on 2015-04-30
OK. Looking at the digitalocean tutorial... I suppose you followed the steps to create the .key and .csr file, and used that .csr to order again your certificate. Note that you probably need to order a new certificate after the last attempt recreating the .key and .csr files. The earlier certificate is probably invalid.

After you got the certificate from the provider, and the intermediate CA bundle, you modified the 000-default.conf as per that tutorial? And when starting apache it gives you the errors posted above?

Can you please post the SSL section of the 000-default.conf and the content of the folder where SSLCertificateFile, etc point to?

---

### Post by aaron27 on 2015-05-01
So running the command to get the CSR + Key file has made the CRT's invalid?
I already had the two CRT files, so I followed the steps to create the CSR + Key files and then copied everything over.

I went in to modify 000-default.conf but there was no ssl section so i modified the default-ssl.conf file. as per the last couple of posts i followed those instructions to remove the 000-default.conf so that it doesnt try using that.

So the content is:

```


<IfModule mod_ssl.c>
<VirtualHost_Default_:443>
ServerAdmin webmaster@localhost
ServerName ourdomain.co.uk
ServerAlias *.ourdomain.co.uk

DocumentRoot /var/www/owncloud

ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined

# SSL Engine Switch
# Enable/Disable SSL for this virtual host.
SSLEngine on

SSLCertificateFile /etc/ssl/certs/keys/*.ourdomain.co.uk.crt
SSLCertificateKeyFile /etc/ssl/certs/keys/*.ourdomain.co.uk.key

SSLCertificateChainFile /etc/ssl/certs/keys/intermediate.crt

SSLCACertificationFile /etc/ssl/certs/keys/intermediate.crt

</VirtualHost>
</IfModule>


```

There is also the usual information about each section which is #'d out and didnt think you would need to see this?

The folder location /etc/ssl/certs/keys contains:
*.ourdomain.co.uk.crt
*.ourdomain.co.uk.csr
*.ourdomain.co.uk.key
intermediate.crt

Thanks for your ongoing advice and help

Aaron

---

### Post by darkod on 2015-05-01
Hmmm, few things... The 000-default.conf is the default page. The DO instructions said to modify the port, not to completely disable the file. I'm not sure apache can run without any sites enabled (I'm not apache expert as already said). I suggest you enable 000-default.conf again. You can do the SSL stuff in default-ssl.conf, no problem. Just make sure it's included in 000-default.conf. If I'm not mistaken, there should be a line like:
```
include /path/default-ssl.conf
```

Apache can combine a bunch of conf files with include command. That way you can also organize parts of the config in separate files. Also, if you are not aware, just the .conf file is not enough for a site to start working. It needs to be "enabled". That's why the folders sites-available and sites-enabled exist. The apache commands were something like a2ensite and a2dissite.

As for the CRT, I'm not 100% sure because I have never tried it, but I would say you better recreate new CRTs after you changed the CSR and key. That might explain the key mismatch error. Don't forget, SSL was created for high security and in my logic it will detect and dislike any changes done after the CRT was issued. Which is what you did. So it simply stops because it knows something is wrong.

Otherwise the secure SSL traffic might be attempted to be intercepted which is what it tries to avoid.

---

### Post by Kenneth_Benson on 2015-05-01
Ok, I noticed one thing. The _CertificateChain_ file is for older versions of apache, you should comment that out. If you recreated the key then you have to resend the csr and get an updated certificate. I would talk to the support for DO about that process. Make sure that wherever you put key and crt, that Apache has access to them (permissions-wise), otherwise the conf is correct. What DO was having you do with their instructions was convert your 000-default.conf into a default-ssl.conf without changing the name. If you do these, it _should_ start working. YMMV.

---

### Post by aaron27 on 2015-05-05
All I did was run the a2dissite on the 000-default.conf as suggested earlier in this thread, was I wrong to do so? 
When i now run the a2ensite the command errors and says the file is real and wont run the command.

I have commented out he certificatechainfile in the config file. And from what i can make out running a command allows the combination of both 000-default.conf and default-ssl.conf? 

I will start from scratch and get the key and csr created first then get our crt and test again

---

### Post by aaron27 on 2015-05-06
I just found another website which informed me to put the crt file into /usr/local/share/ca-certificates and then run update ca-certificates which has created a .pem file.... is this more correct?

---

### Post by darkod on 2015-05-06
I think it's the same. The crt files you receive are already PEM encoded. The file extension has no real meaning.
I recently had to secure one apache website with a Namecheap certificate and I used the crts they sent. I never intended to make them into pem files.

---

### Post by aaron27 on 2015-05-06
Aaaah ok was just wondering if it would make any difference. Having spoke to my manager about the crt files, once they are created they are set how they are so we cant get them re-sent. He was under the impression that it should work similar to IIS in Windows where you make a request and then the request looks at the crt files themselves, which at the moment I havent had to do because Ive copied the crt files over and then made the key and csr files once they were copied over.

---

### Post by darkod on 2015-05-06
Now I am starting to get lost... Are you saying that you are using "older" crt files with a new key/csr pair you created???

If that is the case, IMHO, you can forget about making it work. And if by "request looks at the crt files" you mean the csr and key creation, you are both wrong again. And IIS doesn't worj like that either.

A CSR file is Certificate Signing Request. That is the FIRST step in getting a certificate from the issuer (the Certificate Authority, CA). The csr includes specific info about your machine/server which the CA uses when creating the crt files. That's why you have to give them (or online paste into their ordering form) the csr file when you are ordering the certificate. They will use the csr to create your crt.

After that, you can ONLY use that crt with the key that was created in the csr/key creation process. You CAN NOT take an older crt, even if it was issued for the same machine, and use it with a newly created key. It won't match. Which is basically what the apache error log is telling you too. Wrong key blah blah...

As for the crt not being able to be re-sent, I don't know where you are buying your certificate but most CAs since years ago offer you the possibility to "recreate" the crt. You have paid a subscription period for the certificate and you have the right to ask them to recreate it. Imagine your server dies and you buy a new one. They won't allow you to ask them to create certificate for it? If that is really so, change that provider immediately.

If I have not misunderstood anything, and if all of the above is true, your ONLY option now is to guard the latest version of the key/csr file pair (the ones most recently created), and contact your certificate issuer and ask them to recreate the certificate using this new csr file. After that your apache config will work in 5mins... without that, it will never work... IMHO.

As we said, SSL security is serious business. That's why payment processing and other communication uses it. There is no bending the rules. You can't "choose" which crt you will use with which key. It has to be the specific crt created using the csr pair of that key.

On the other hand, if I have misunderstood the above, then you have another type of problem... Not the key/crt mismatch.

---

### Post by Habitual on 2015-05-06
> **aaron27 said:**
> 
The folder location /etc/ssl/certs/keys contains:
*.ourdomain.co.uk.crt
*.ourdomain.co.uk.csr
*.ourdomain.co.uk.key
Aaron: These file names will not work!

You can name them anything you wish that does NOT include an asterisk.
I suggest 
```
ourdomain.co.uk.crt
ourdomain.co.uk.csr
ourdomain.co.uk.key
```

Has the ourdomain.co.uk.key file had the password removed?

Here's how I used a GoDaddy signed CSR for one of our Owncloud hosts. These are the short notes on how that was done.
 edit /etc/apache2/sites-enabled/000-default.conf and edit/update:

```

SSLCertificateFile /etc/apache2/ssl/certs/owncloud.domain.com.crt
SSLCertificateKeyFile /etc/apache2/ssl/private/owncloud.domain.com_nopass.key
SSLCertificateChainFile /etc/apache2/ssl/gd_bundle.crt
```

Yours should be something like:
```
SSLCertificateFile /etc/ssl/certs/keys/ourdomain.co.uk.crt
SSLCertificateKeyFile /etc/ssl/certs/keys/ourdomain.co.uk.key
SSLCertificateChainFile /etc/ssl/certs/keys/intermediate.crt
```
After renaming those files in /etc/ssl/certs/keys

Then try to start apache.

Hope this helps you out.

---

### Post by aaron27 on 2015-05-07
Right everything is making sense now, sorry for my vague/newbie responses. 
We have done it the wrong way round then we got the crt files and then did the csr/key creation so I will make a new pair and then ask for the crt files to be updated and then we will have everything working.

Habitual - thank you for pointing that out, I only used the asterix as we have a wildcard certificate (from godaddy aswell and the instructions on the link earlier said i could use an asterix when using a wildcard certificate) I will get those file names changed over.

---

### Post by Habitual on 2015-05-07
Aaron:
My hints are from a GD wildcard domain cert as well.
Here is one of the sites I used to install mine: [http://jonwilliams.org/wordpress/2010/12/30/installing-a-godaddy-ssl-certificate-into-apache-ubuntu-linux/](http://jonwilliams.org/wordpress/2010/12/30/installing-a-godaddy-ssl-certificate-into-apache-ubuntu-linux/)

You have a key, so no need to regenerate another one.
Use the original key to generate a new .csr ;)

Good Luck. It sounds like you are almost there.

---

### Post by aaron27 on 2015-05-13
Great news we are now up and running, godaddy sent us a pfx file which we imported and changed to a pem file, this then gave us our crt/key files and now apache service starts and we can access owncloud.

thank you to everyone who advised me on this it has been a big learning curve for me.

---

### Post by Habitual on 2015-05-13
Glad it all worked out!

---

### Post by aaron27 on 2015-05-14
Habitual - [http://ubuntuforums.org/showthread.php?t=2278176&p=13285072#post13285072](http://ubuntuforums.org/showthread.php?t=2278176&p=13285072#post13285072) are you able to help me with this aswell?

---

### Post by Habitual on 2015-05-14
[http://ubuntuforums.org/showthread.php?t=2278176&p=13285123#post13285123](http://ubuntuforums.org/showthread.php?t=2278176&p=13285123#post13285123) looks like you resolved that too?

---

