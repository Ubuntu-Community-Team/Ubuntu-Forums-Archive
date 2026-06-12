---
title: "stuck with google wave CA-issued certs..."
date: 2009-12-04
forum: Server Platforms
---

### Post by al.adab on 2009-12-04
To use Google Wave I've been following the directions given at 
[http://code.google.com/p/wave-protocol/wiki/Installation](http://code.google.com/p/wave-protocol/wiki/Installation)

When it comes to the section "Wave Extension Installation" (and from the line *To run the extension you will need some of the parameters...*) I feel I'm not making much sense....

here's what I've done in the meantime:  

- registered at [http://startssl.com](http://startssl.com)
- didn't (as far as I'm aware) create an *XMPP Certificate*
- got to a page where it says 

[I]Submit Certificate Request (CSR)
    * Copy and paste the content from the certificate request into the textbox below.
    * Make sure, that you do not alter the content and you did not add any spaces!
    * Always include the headers and footers of the CSR.
    * The CSR must have a SHA1 hash or better, MD5 hashes are not allowed.
    * The RSA key size must be 2048 bit or higher.[/I]

and don't know how to proceed from here. Can you please help? 

Also I don't quite understand what I'm supposed to do in relation to 

a) *Copy the run-config.sh.example to run-config.sh, then edit run-config.sh to configure it to your setup. The arguments passed to the server are* (at [http://code.google.com/p/wave-protocol/wiki/Installation](http://code.google.com/p/wave-protocol/wiki/Installation) - section "Wave Extension Installation") 

b) *Self-Signed Certificates - Here's a script: * ([http://code.google.com/p/wave-protocol/wiki/Certificates](http://code.google.com/p/wave-protocol/wiki/Certificates)) 

I don't know if this matters but I've been invited to Google Wave and have previously installed LAMP (to install Moodle) according to ([http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)) if it's related to what I'm doing now at all :) I'm completely new to this and feel like a child, completely out of my element, so please be patient. 

Thanks.

---

### Post by al.adab on 2009-12-05
In other words, if I sudo gedit *run-config.sh* and copy + edit

[I]i. WAVE_SERVER_DOMAIN_NAME: wave-test.nl
ii. WAVE_SERVER_HOST_NAME: localhost
iii. XMPP_SERVER_SECRET: The default shared secret that you entered
iv. PRIVATE_KEY_FILE_NAME: the .key file you generated
v. CERTIFICATE_FILENAME_LIST: the .cert file you generated
vi. XMPP_SERVER_IP: localhost[/I]

when it comes to editing iv. & v. I don't know what to do. If I run (as an attempt) *openssl x509 -text -in test.crt* in Terminal, I get the following

[I]openssl x509 -text -in test.crt 
Error opening Certificate test.crt
16747:error:02001002:system library:fopen:No such file or directory:bss_file.c:352:fopen('test.crt','r')
16747:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:354:
unable to load certificate
daniele@adab:~$ sudo openssl x509 -text -in test.crt 
Error opening Certificate test.crt
16756:error:02001002:system library:fopen:No such file or directory:bss_file.c:352:fopen('test.crt','r')
16756:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:354:
unable to load certificate
[/I]

...as I followed (seemingly successfully) everything up at [http://code.google.com/p/wave-protocol/wiki/Installation](http://code.google.com/p/wave-protocol/wiki/Installation) up to the line 

*To run the extension you will need some of the parameters you used to set up the Openfire server. They are the extension port, the extension shared secret, the server name, and finally the component name which is "wave". *

I don't really know what cert.file and key.file I'm supposed to be dealing with. Maybe the certificate (XMPP???) I after all created at [http://startssl.com?](http://startssl.com?)

I'm going through a third ref ([http://googlewavecommunity.com/forum/viewtopic.php?f=11&t=43](http://googlewavecommunity.com/forum/viewtopic.php?f=11&t=43)) to try to make sense....any idea?

---

