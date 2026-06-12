---
title: "apache ssl cert not recognized??? i think???"
date: 2007-01-23
forum: Server Platforms
---

### Post by dantrevino on 2007-01-23
I followed the wiki, installed and enabled my ssl site, but I get "unable to connect" errors when trying to access secure parts of my site.  Non-secure parts run fine.  

Below is some tests i've run, and results:

>> openssl verify apache.pem
error 18 at 0 depth lookup:self signed certificate
OK

>>openssl s_client -connect localhost:443 -state -debug
CONNECTED(00000003)
SSL_connect:before/connect initialization
write to 0x80bffc8 [0x80c0f40] (142 bytes => 142 (0x8E))
0000 - 80 8c 01 03 01 00 63 00-00 00 20 00 00 39 00 00   ......c... ..9..
0010 - 38 00 00 35 00 00 16 00-00 13 00 00 0a 07 00 c0   8..5............
0020 - 00 00 33 00 00 32 00 00-2f 03 00 80 00 00 66 00   ..3..2../.....f.
0030 - 00 05 00 00 04 01 00 80-08 00 80 00 00 63 00 00   .............c..
0040 - 62 00 00 61 00 00 15 00-00 12 00 00 09 06 00 40   b..a...........@
0050 - 00 00 65 00 00 64 00 00-60 00 00 14 00 00 11 00   ..e..d..`.......
0060 - 00 08 00 00 06 04 00 80-00 00 03 02 00 80 eb b9   ................
0070 - 89 c7 79 ba b0 8b b8 b4-fe 98 98 8c 0b d2 ab 83   ..y.............
0080 - ce 37 3d 3a 9d 06 1c c9-98 a6 98 0f 92 c7         .7=:..........
SSL_connect:SSLv2/v3 write client hello A
read from 0x80bffc8 [0x80c64a0] (7 bytes => 7 (0x7))
0000 - 3c 3f 78 6d 6c 20 76                              <?xml v
SSL_connect:error in SSLv2/v3 read server hello A
28927:error:140770FC:SSL routines:SSL23_GET_SERVER_HELLO:unknown protocol:s23_clnt.c:567:

Finally
>> sudo openssl s_server -cert apache.pem -WWW
Using default temp DH parameters
Using default temp ECDH parameters
ACCEPT
ACCEPT
ACCEPT
ACCEPT

Error accessing '' <---- firefox at [https://localhost:4433/](https://localhost:4433/), certifcate shows, all looks fine

Can someone tell me how to debug this further?  I'm not getting anything useful (to me) and dont know where to go next.

tia,
dan

Edit: The following is my apache configuration as well...possibly misconfigured:
>>ls sites-enabled/
main
ssl
>>cat ports.conf 
Listen 80
Listen 443
>>head sites-available/main  <---not really using "fqdn" or "dn", but you get the picture
NameVirtualHost *

<VirtualHost *>
        ServerName fqdn
        ServerAdmin webmaster@dn

        DocumentRoot /var/www/dn
        <Directory />

>>head sites-available/ssl
<VirtualHost fqdn:443>
        ServerName fqdn
        ServerAdmin webmaster@dn

        DocumentRoot /var/www/dn
>>tail sites-available/ssl

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access-dn.log combined
        ServerSignature Off
        SSLEngine On
        SSLCertificateFile /etc/apache2/ssl/apache.pem
</VirtualHost>

---

### Post by dantrevino on 2007-01-23
Solved.  Bad IP address in /etc/hosts.  Once I got the correct IP address in there, everything worked.

---

