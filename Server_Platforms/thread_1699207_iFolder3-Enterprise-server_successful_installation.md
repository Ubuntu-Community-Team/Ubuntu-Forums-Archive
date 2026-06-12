---
title: "iFolder3-Enterprise-server successful installation on Ubuntu Server 10.04 Lucid Lynx"
date: 2011-03-03
forum: Server Platforms
---

### Post by gube on 2011-03-03
I tried to find complete guides for the iFolder3-Enterprise-server installation on a fresh Ubuntu server 10.04 OS. But every one of them I found were incomplete or assumed that some dependent packages already were installed on the machine. So this is the steps i went through from scratch.

The following is terminal [COLOR=Navy]*commands*[/COLOR] except when preceded with a #

#First of all update your installation and the install HTTPD - Apache2 Web Server

[COLOR=Navy][I]apt-get update
apt-get upgrade
apt-get install apache2[/I][/COLOR]

#Then you should get your SSL certificates in place. A nice guide is
#[https://help.ubuntu.com/10.04/serverguide/C/certificates-and-security.html](https://help.ubuntu.com/10.04/serverguide/C/certificates-and-security.html)
#If you followed the certificate-guide above a edit in the file '/etc/apache2/sites-available/default-ssl' is nessesary.
#Find the two lines 'SSLCertificateFile' and 'SSLCertificateKeyFile' and make sure they look like this or as you configure the certificates in the step before
#SSLCertificateFile /etc/ssl/certs/example.com.crt
#SSLCertificateKeyFile /etc/ssl/private/server.key
#
#Now lets install iFolder3 server.

[COLOR=Navy][I]apt-get install python-software-properties
add-apt-repository ppa:marceloshima/ifolder
apt-get update
/etc/init.d/apache2 stop[/I][/COLOR]

#Remember to answer 'y' on the following question during install of ifolder3-enterprise
#mod_mono.conf (Y/I/N/O/D/Z) [default=N] ? y

[COLOR=Navy]*apt-get install ifolder3-enterprise*[/COLOR]
[COLOR=Navy][I]ln -sf /etc/ifolder-server/apache/ifolder_apache.conf /etc/apache2/conf.d/
apt-get install liblog4net1.2-cil
a2ensite default-ssl
/etc/init.d/apache2 restart[/I][/COLOR]

#Now you can log in via 'http://your_server/admin' or 'https://your_server/admin'
#default user/password is admin/admin
#To be able to connect to the server make sure you edit the Public URL after you have logged in to the iFolder Administrator area
#Click on 'Servers' -> 'Server Details' and update the Public URL. Example: [http://your_server/simias10]("https://your_server/simias10")
#Most of the configuration can be made in the iFolder Administrator area but if, for some reason, you need to manually configure it the simias config file is located here: '/var/lib/simias/Simias.config' 
#To change a users password use the following command and change word marked [COLOR=DarkGreen]green [/COLOR]with your own settings:
#simias-user modify --url [http://localhost](http://localhost) --admin-name admin --admin-password admin --user [COLOR=DarkGreen]USER_NAME[/COLOR] --password [COLOR=DarkGreen]USER_PASSWORD[/COLOR]

Hope this guide can save you all some time.

/G

---

### Post by Dragonbite on 2011-03-03
This is great to know!

Is there a Wiki page for this that can be updated?

---

### Post by liaogz on 2011-06-28
hi.

Good guide. is there a guide for me to link it up to openldap? i always have this problem...


System.ArgumentNullException: Argument cannot be null.
Parameter name: Either baseUri or relativeUri are required.
  at System.Xml.XmlResolver.ResolveUri (System.Uri baseUri, System.String relativeUri) [0x00000] in <filename unknown>:0 
  at System.Xml.XmlUrlResolver.ResolveUri (System.Uri baseUri, System.String relativeUri) [0x00000] in <filename unknown>:0 
  at Mono.Xml2.XmlTextReader.GetStreamFromUrl (System.String url, System.String& absoluteUriString) [0x00000] in <filename unknown>:0 
  at Mono.Xml2.XmlTextReader..ctor (System.String url, System.Xml.XmlNameTable nt) [0x00000] in <filename unknown>:0 
  at System.Xml.XmlTextReader..ctor (System.String url, System.Xml.XmlNameTable nt) [0x00000] in <filename unknown>:0 
  at System.Xml.XmlDocument.Load (System.String filename) [0x00000] in <filename unknown>:0 
  at Novell.iFolder.SimiasServerSetup.SetupSimias () [0x00000] in <filename unknown>:0 
  at Novell.iFolder.SimiasServerSetup.Configure () [0x00000] in <filename unknown>:0 
  at Novell.iFolder.SimiasServerSetup.Main (System.String[] args) [0x00000] in <filename unknown>:0 
  at System.Xml.XmlResolver.ResolveUri (System.Uri baseUri, System.String relativeUri) [0x00000] in <filename unknown>:0 
  at System.Xml.XmlUrlResolver.ResolveUri (System.Uri baseUri, System.String relativeUri) [0x00000] in <filename unknown>:0 
  at Mono.Xml2.XmlTextReader.GetStreamFromUrl (System.String url, System.String& absoluteUriString) [0x00000] in <filename unknown>:0 
  at Mono.Xml2.XmlTextReader..ctor (System.String url, System.Xml.XmlNameTable nt) [0x00000] in <filename unknown>:0 
  at System.Xml.XmlTextReader..ctor (System.String url, System.Xml.XmlNameTable nt) [0x00000] in <filename unknown>:0 
  at System.Xml.XmlDocument.Load (System.String filename) [0x00000] in <filename unknown>:0 
  at Novell.iFolder.SimiasServerSetup.SetupSimias () [0x00000] in <filename unknown>:0 
  at Novell.iFolder.SimiasServerSetup.Configure () [0x00000] in <filename unknown>:0 
  at Novell.iFolder.SimiasServerSetup.Main (System.String[] args) [0x00000] in <filename unknown>:0 

FAILED

---

