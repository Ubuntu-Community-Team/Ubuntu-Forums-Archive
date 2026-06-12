---
title: "SSL WildCard setup Apache"
date: 2015-11-24
forum: Server Platforms
---

### Post by edwin.caveney on 2015-11-24
Just installing owncloud on Ubuntu server 14.04 and I am looking to secure the web site using an SSL certificate.  I already have a wildcard cert from Godaddy with a .crt and the intermediates.p7b files but I have no idea how to set these up on the Ubuntu server.  Any advice or pointers to any guides would be very help full.

Thanks

---

### Post by edwin.caveney on 2015-11-25
I found the guide on the Ubuntu documentation here [https://help.ubuntu.com/lts/serverguide/httpd.html#https-configuration](https://help.ubuntu.com/lts/serverguide/httpd.html#https-configuration)

However it makes no mention there about editing [COLOR=#333333][FONT=monospace]/etc/apache2/sites-enabled/ as i have found on other guides like this one [/FONT][/COLOR]https://www.digicert.com/ssl-certificate-installation-ubuntu-server-with-apache2.htm 

Does anyone know the best way to do this.

Thanks

---

### Post by darkod on 2015-11-25
sites-enabled is only a symlink to the same site in sites-available if I'm not mistaken. If the ssl default site is enabled (if it exists in sites-enabled), I believe it is enough to edit only the default-ssl.conf (or what ever it was called) in sites-available. Restart apache and that should be it.

For the certificate you can choose whether to chain all CA root certificates into one, so that it supports more devices. Most devices in the world would already have the root certificate for well known CAs, but by chaining it all up you make sure of 100% compatibility.

---

### Post by edwin.caveney on 2015-11-25
Thanks for the reply.

I have followed the instructions and at the minute its using the self-signed default certificates called ssl-cert-snakeoil held in /etc/ssl/certs/ and /etc/ssl/private/

To get my Godaddy Wildcard to work do I copy the certificate as described into these locations and then update /etc/apache2/sites-avaiable/default-ssl.conf with the name of the Godaddy cert?

Also from Godaddy I have a .crt and then three intermediate certs which have a .cer which files go where?  I don't have a .key file

---

### Post by darkod on 2015-11-25
1. The key file you should have on your server as part of preparing the CSR (certificate signing request), the file you used to order the GoDaddy cert. The procedure creates the .csr and .key. It will not work without the key (I think). It is needed on the server side.

2. The three GD certs are all intermediary/root certs. They need to be chained into one .cer in a specific order. When I get home I can send you a link. There are tutorials to be found on the net, maybe even on GD support pages.

3. Once you have that, you will update the .conf with the correct path and filename for all three parameters: your cert .crt, the single file .cer CA cert, and the key.

---

### Post by edwin.caveney on 2015-11-25
Thanks,

I don't have a key file as the request didn't come from this server.  It was created on a Windows IIS server then exported to allow me to use the Wildcard on other servers.

---

### Post by Habitual on 2015-11-25
Edwin:
I stuck my GD cert stuff in  /etc/apache2//sites-available/default-ssl.conf
like so:
```

        SSLCertificateFile /etc/apache2/ssl/domain_com_ba2bd_6695f_1513282441_a2bd116028000513064326faa078a96c.crt
        SSLCertificateKeyFile /etc/apache2/ssl/keys/ba2bd_6695f_80d595386f72c24375f338ff17a059dd.key
        SSLCACertificateFile /etc/apache2/ssl/GoDaddy_com_Inc__90490a5c829d2aca24f22b5820864c6e_1935558000.cabundle
```
The cert process assumes you have the key that made the .csr
without it, apache2 won't start, I believe.

GoDaddy can re-issue a cert within a certain time-frame, this will allow you to generate  a new .csr from a key on a Linux-based system.

Don't forget to ```

a2ensite default-ssl
``` when that edit is complete.
YMMV.

You can put the keys where ever on the host (new or existing directory), say in /etc/ssl/mydirectory
I purposely don't use /etc/ssl/certs/ as it's heavily populated by other CA certs.

Hope that helps.

TIP: Make certain the "**Common Name**" is [COLOR=#ff0000]***.domain.tld **[/COLOR]
to match the wildcard cert.

---

### Post by edwin.caveney on 2015-11-25
Thanks for the help, unfortunately the wildcard cert is been used on a few other in production servers so I can't get it re-issued.  Does anyone know a way to get the .key file from a Windows IIS server?

---

### Post by darkod on 2015-11-25
As far as I know, the key has to be created on the same machine (web server) and can be used on that machine only. SSL is serious communication and needs to be 100% secure. That's why it doesn't allow re-using keys from other servers.

---

### Post by edwin.caveney on 2015-11-25
Yes but this is a Wildcard certificate and therefore can be used on different servers as long as they have the same domain name.  Is Ubuntu/Apache not able to use Wildcard certs?

---

### Post by darkod on 2015-11-25
I understand WC cert as a cert that you can use on single machine for unlimited subdomains in format *.domain.com. Not sure it applies cross-machines... But I might be wrong...

---

### Post by edwin.caveney on 2015-11-25
Ok, this is my first look at Apache on Ubuntu server to be honest.  Usually use Windows IIS servers for what little web servers we actually have.  Anyway with Windows IIS once you have requested the certificate from Godaddy and imported the certificate back in you can then export it.  Then on a different server you just import the certificate, as long as both servers have the same DNS domain name you can use the Wildcard cert on as many servers as you like.  I take it this is not the case with Ubuntu/Apache? and we will need a new certificate that has been requested from that server?

---

### Post by darkod on 2015-11-25
You still might be correct.

@Habitual???

But especially since we are talking about different platforms (windows/linux), I doubt you will be able to use the same WC cert on your ubuntu server.

---

### Post by edwin.caveney on 2015-11-25
It's looking that way.  Thanks for the help.

---

### Post by CharlesA on 2015-11-25
I doubt this helps any, but I've always done my key creation and CSR from a local machine and then transfer that key and the cert itself to whatever server I need to use it on, but that has been with Nginx, not IIS.

IIS looks to handle it differently from Apache/Nginx, so what darkod is saying seems to be true from a quick search.

Have you reached out to the company that issued the cert to see if they can help?

Found this, maybe it will help?
[https://www.sslshopper.com/move-or-copy-an-ssl-certificate-from-a-windows-server-to-an-apache-server.html](https://www.sslshopper.com/move-or-copy-an-ssl-certificate-from-a-windows-server-to-an-apache-server.html)

---

### Post by edwin.caveney on 2015-11-25
Godaddy are my next stop.  Thanks for the help.

---

### Post by edwin.caveney on 2015-11-25
Godaddy says it is possible but they don't give out instructions on how to do it and don't guarantee that it will work or that it won't break any of the servers.  They recommended that I buy a new certificate!!!  Thats very helpful of them.

---

### Post by CharlesA on 2015-11-25
Very helpful response from GoDaddy. Er, not.

Did you have any luck with the link from the sslshopper?

---

### Post by edwin.caveney on 2015-11-25
Which sslshopper link?

---

### Post by CharlesA on 2015-11-25
> **edwin.caveney said:**
> Which sslshopper link?

[https://www.sslshopper.com/move-or-copy-an-ssl-certificate-from-a-windows-server-to-an-apache-server.html](https://www.sslshopper.com/move-or-copy-an-ssl-certificate-from-a-windows-server-to-an-apache-server.html)

---

### Post by edwin.caveney on 2015-11-25
It might do the trick.  I will have a go tomorrow and let you know.

Thanks

---

### Post by edwin.caveney on 2015-11-26
I have followed those instructions and now have a .key a .crt and two intermediate and two root .crt how do I create a linked bundle for the intermediate and root certs?

---

### Post by darkod on 2015-11-26
Those are basically text files and linking them in one file is very simple. What is important is the correct order, because the full linked bundle is expected to be in certain order. I don't have any links at hand right now, you can search on the net about the order. Also, usually there are tutorials if the files arrived from your CA. In this case you created them with your own procedure and the file names might not help you much in deciding the order. But give it a shot and ask google...

Otherwise, to link you simply do:
```
cat cert1.cer cert2.cer cert3.cer > full.cer
```

That's it. But the order of the files in cat is the important thing.

---

### Post by edwin.caveney on 2015-11-26
Great thanks

---

### Post by edwin.caveney on 2015-11-26
Well I have it working.  Thanks for all the help guys its very much appreciated.

---

### Post by darkod on 2015-11-26
Perfect. Glad you got it working.

---

### Post by Habitual on 2015-11-26
> **edwin.caveney said:**
> Well I have it working.  Thanks for all the help guys its very much appreciated.

Can you post the steps you took to resolve this issue for future "generations"?

Thanks.

---

### Post by edwin.caveney on 2015-11-27
·         To use a Godaddy Wildcard cert from IIS do the following:
o   Go to a server with the wildcard installed
o   Open an MMC with Certifcates ADD-on for Local computer account
o   Go to the Personal folder and right click and export the wildcard cert
o   Select “Yes, export the private key”
o   Select “Include all certificates in the certification path if possible”
o   Enter a Password and save as wildcard.pfx
o   Using WINSCP and with SSH enabled on ubuntu server copy the .pfx file to /home/username/
o   On ubuntu server run the following command to convert .pfx to a .txt:
§  Sudo openssl pkcs12 –in wildcard.pfx –out wildcard.txt –nodes
o   Copy the wildcard.txt file back to a Windows PC using WINSCP
o   Open wildcard.txt with notepad++
o   Using the header names copy out the contents between and including BEGIN CERTIFICATE and END CERTIFICATE
o   Copy them to new files for each wildcard.key wildcard.crt and cabundle.crt which contains all the intermediate and root certs in the order from the wildcard.txt
o   Copy the three files back to /home/username/ using WINSCP
o   Now on ubuntu server copy the three files using the commands:
§  Sudo cp /home/username/wildcard.crt /etc/ssl/certs/
§  Sudo cp /home/username/wildcard.key /etc/ssl/private/
§  Sudo cp /home/username/cabundle.crt /etc/ssl/certs/
·         Enable SSL with the command sudo a2enmod ssl
·         Configure Apache2 to use HTTPS sudo a2ensite default-ssl
·         Restart Apache2  with sudo service apache2 reload
·         To make it use the wildcard edit default-ssl.conf with the command:
·         Sudo nano default-ssl.conf
·         Edit the following lines:
o   Above SSLEngine on add:
o   ServerName .domainname.com (or whatever the actual name will be)
o   SSLCertificateFile /etc/ssl/certs/wildcard.crt
o   SSLCertificateKeyFile /etc/ssl/private/wildcard.key
o   SSLCACertificateFile /etc/ssl/certs/cabundle.crt
·         Restart Apache2  with sudo service apache2 reload
you might also need to edit the config.php file for the website to add ther servername as a trusted domain this file will most likely be in /var/www/websitename/config/config.php


Thanks

---

### Post by Habitual on 2015-11-27
Awesome! Thanks Edwin

---

