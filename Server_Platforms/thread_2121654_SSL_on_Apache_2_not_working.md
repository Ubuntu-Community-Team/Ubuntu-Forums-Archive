---
title: "SSL on Apache 2 not working"
date: 2013-03-02
forum: Server Platforms
---

### Post by cryptodan on 2013-03-02
I am using apache2 on Ubuntu 12.04.2 LTS Server, and I am trying to get SSL to work, however, I am unable to do so.  i have both self signed certs and certs from cacerts.org generated and both fail.  

Here is what I am getting in Chrome:

```

SSL connection error
Unable to make a secure connection to the server. This may be a problem with the server or it may be requiring a client authentication certificate that you don't have.
Error 107 (net::ERR_SSL_PROTOCOL_ERROR): SSL protocol error

```

Here is what I am getting in Firefox:

```

Secure Connection Failed
      
An error occurred during a connection to 192.168.1.2.

SSL received a record that exceeded the maximum permissible length.

(Error code: ssl_error_rx_record_too_long)

The page you are trying to view cannot be shown because the authenticity of the received data could not be verified.

Please contact the web site owners to inform them of this problem. Alternatively, use the command found in the help menu to report this broken site.

```

Here is my default-ssl file: [http://www.cryptodan.net/txt/apache2_ssl.txt](http://www.cryptodan.net/txt/apache2_ssl.txt)

Here is my ports.conf file: [http://www.cryptodan.net/txt/ports.txt](http://www.cryptodan.net/txt/ports.txt)

Here is the output of openssl s_client -connect [www.cryptodan.net:443](www.cryptodan.net:443)

```

root@orion:/etc/apache2# openssl s_client -connect www.cryptodan.net:443
CONNECTED(00000003)
3077875912:error:1408E098:SSL routines:SSL3_GET_MESSAGE:excessive message size:s3_both.c:504:
---
no peer certificate available
---
No client certificate CA names sent
---
SSL handshake has read 16452 bytes and written 7 bytes
---
New, (NONE), Cipher is (NONE)
Secure Renegotiation IS supported
Compression: NONE
Expansion: NONE
SSL-Session:
    Protocol  : TLSv1.1
    Cipher    : 0000
    Session-ID: 
    Session-ID-ctx: 
    Master-Key: 
    Key-Arg   : None
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    Start Time: 1362253742
    Timeout   : 300 (sec)
    Verify return code: 0 (ok)

```

Here is the output of apachectl -S

```

root@orion:/etc/apache2# apachectl -S
VirtualHost configuration:
wildcard NameVirtualHosts and _default_ servers:
*:443                  www.cryptodan.net (/etc/apache2/sites-enabled/default-ssl:2)
*:80                   is a NameVirtualHost
         default server www.cryptodan.net (/etc/apache2/sites-enabled/000-default:1)
         port 80 namevhost www.cryptodan.net (/etc/apache2/sites-enabled/000-default:1)
         port 80 namevhost www.pandorah.net (/etc/apache2/sites-enabled/pandorah.net:1)
Syntax OK

```

I can usually fix things like this, but I need another set of eyes maybe I am missing something.

https is listening and is opened up on my firewall as well.

```

root@orion:/etc/apache2# nmap -p 443 localhost

Starting Nmap 5.21 ( http://nmap.org ) at 2013-03-02 19:58 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00010s latency).
Hostname localhost resolves to 2 IPs. Only scanned 127.0.0.1
PORT    STATE SERVICE
443/tcp open  https

Nmap done: 1 IP address (1 host up) scanned in 0.13 seconds
root@orion:/etc/apache2# 

```

---

### Post by gordintoronto on 2013-03-02
Have you gone through this:
[https://help.ubuntu.com/community/OpenSSL](https://help.ubuntu.com/community/OpenSSL)

---

### Post by cryptodan on 2013-03-02
I have not, been threw that, and that is far more then I think is required to get the ssl working on my website, as I have my dovecot setup working just fine with my self created certs.

---

### Post by cryptodan on 2013-03-02
I am now getting the following:

```

Secure Connection Failed
      
      
      
      
      
        
        
          An error occurred during a connection to www.cryptodan.net.

SSL peer was unable to negotiate an acceptable set of security parameters.

(Error code: ssl_error_handshake_failure_alert)

        

        
        

  The page you are trying to view cannot be shown because the authenticity of the received data could not be verified.
  Please contact the web site owners to inform them of this problem. Alternatively, use the command found in the help menu to report this broken site.

```

---

### Post by cryptodan on 2013-03-04
Well, I found the issue and my OpenSSL is corrupted on my server.  So I will reinstall OpenSSL and see if it I can get it to work.  WIll post back my findings.

---

### Post by cryptodan on 2013-03-04
I have solved my SSL Issue, the resolution was a corrupted file system impacting creating of https connections.

so if you follow countless howtos and still cant get it to work, then its time to look at hardware issues.

---

