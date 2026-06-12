---
title: "Importing PKCS#12 (.p12) files into Firefox From the Command Line"
date: 2011-02-18
forum: Security
---

### Post by fieldyweb on 2011-02-18
I have a need to perform the following action:

Firefox 3.6.x: 

> open Edit -> Preferences -> Advanced -> Encryption ->  View Certificates -> Your Certificates -> Import

However i need the same functionality from the bash command line.

So far I've established that the following command is supposed to be used:

> certutil -A -t "u,u,u" -d /home/df001/.mozilla/firefox/qe5y5lht.tc.default/ -n "mycert" -i client.p12

This executes with no isses, however, doesn't show up in any Firefox Certificate store.

However, I have noted that prior to running this command, i have a cert8.db key3.db and secmod.db file in the above folder. After running the command the certutil seems to have created a cert9.db, key4.db and pkcs12.txt file

Listing the contents using the command:

> certutil -L -d sql:/home/df001/.mozilla/firefox/qe5y5lht.tc.default/

does seem to confirm my attempts of importing files into a certificate folder of some kind have worked. because i get

> Certificate Nickname                                         Trust Attributes
                                                             SSL,S/MIME,JAR/XPI

Thawte SSL CA                                                ,,   
Go Daddy Secure Certification Authority                      ,,   
Thawte SGC CA                                                ,,   
Entrust Certification Authority - L1C                        ,,   
[B]My Nero                                                      CT,C,c
mynero                                                       P,,  
davidfield - Internet Widgits Pty Ltd                        u,u,u[/B]


So, having tried this, and heading back over to the www, i cam across this command:


>  pk12util -d /home/df001/.mozilla/firefox/qe5y5lht.tc.default/ -i client.p12 -n "David Field" -P "cert8.db"

this again, appears to be importing something somewhere, however, again, Viewing certs from the Firefox interface doesn't show the imported Cert.

I'm surmising here on reading that the certutil and pk12util are creating a new NSS database, which firefox isn't reading. 

So my question is, how can i get the p12 cert from the command line so it displays in the firefox Certificate manager interface?

Why have i posted this here? Why not post on the firefox forum? Well i will copy and post the same question there as well, however the ability to use the command line to do this is important, as I have potentially 2000 machines which will need a user cert imported into firefox via a p12 file. I need to do this in the form of a script, i thought the hard part was going to be making the p12 file from the microsoft 2003 CA, turns out thats easy. 

I can't just import via the GUI and copy over cert8.db x 2000, i can't ask users to use the CA webinterface as its for VPN access, the users are off site, and they need the VPN to get to the cert server..

Is there any person out there who can help?

---

### Post by fieldyweb on 2011-02-19
BUMP!

I could really do with some help..:)

---

### Post by fieldyweb on 2011-02-21
Seems to be that i fix more of my own problems than the forum does..

OK, i have found that having the last update to openSSL applied to my PC has solved this issue, and the libnss-tools 3_11_x installed sorted this out

pk12util -d /home/df001/.mozilla/firefox/qe5y5lht.tc.default/ -i client.p12 -n "David Field"

injects an OpenSSL/Microsoft Cert Server certificate into the firefox User certificates list. It shows up after a restart of Firefox.

Running an old versionof OpenSSL seems to cause this a problem.. because where it was creating cert9.db files, its not now..

Hope this helps someone, DM if you need more.

---

### Post by mkulon on 2012-01-06
Thanks!! pk12util helped me, just had to change the directory & file names to match my system

---

