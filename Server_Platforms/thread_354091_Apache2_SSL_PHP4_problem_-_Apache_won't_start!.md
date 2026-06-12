---
title: "Apache2 SSL PHP4 problem - Apache won't start!"
date: 2007-02-05
forum: Server Platforms
---

### Post by quackking on 2007-02-05
Howdy. I have an Apache2 server running on 6.06 serving several dozen virtual domains; as far as I can tell it has worked fine for months. All of the domains are non-SSL; that is, they are served from port 80. Here is output from server-status:
-----------
Server Version: Apache/2.0.55 (Ubuntu) DAV/2 PHP/4.4.2-1build1 mod_ssl/2.0.55 OpenSSL/0.9.8a
Server Built: Jul 26 2006 18:01:22
-----------

I recently decided to try to enable port 443/SSL for an email application (Horde.) The application has been running fine under port 80.

I generated a pem file and a server key, put them in the correct location, modified 'sites-enabled-default.conf' so it expressly only has NameVirtualServer *.80 entries,  generated a 'sites-available/ssl.conf' file, and symlinked it to sites-enabled, all correctly, added 'Listen 443' to ports.conf, and have 

AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

in apache2.conf

 - in short, I read most of the available posts on the topic and I am pretty sure that I did things correctly - also, I've brought up SSL on Apache 1.3.x several times on other servers, so I think I am up on most of the issues.

My sites-enabled/ssl.conf file begins:

Options +Includes
AddType text/html .shtml
AddOutputFilter INCLUDES .shtml

NameVirtualHost *:443

The problem is that as soon as I include 
the following in that file and restart Apache,:
------------
<VirtualServer *:443>
	ServerName webmail.la-la-la.com
	DocumentRoot /var/www/html/webmail/la-la-la
        SSLEngine on
        SSLCertificateFile /etc/apache2/ssl/la-la-la.pem
        SSLCertificateKeyFile /etc/apache2/ssl/webmailsystem.la-la-la.com.crt
 	ErrorLog /var/log/apache2/horde-error.log
	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn
        CustomLog /var/log/apache2/horde-access.log "%t %h %{SSL_PROTOCOL}x %{SSL_CIPHER}x \"%r\" %b"
	ServerSignature On
</VirtualHost>

-------------
...Apache fails to start with the following message (in Webmin)

Failed to start apache : Apache does not appear to be running :

[Mon Feb 05 15:19:44 2007] [error] an unknown filter was not added: PHP
[Mon Feb 05 15:19:44 2007] [error] an unknown filter was not added: PHP
[Mon Feb 05 15:19:45 2007] [error] an unknown filter was not added: PHP
[Mon Feb 05 15:19:45 2007] [error] an unknown filter was not added: PHP
[Mon Feb 05 15:20:36 2007] [notice] Graceful restart requested, doing restart


Always four error lines. As soon as I comment out the lines above the server works fine again (although, for the first time, I noticed that the apache error log does contain many lines like this

[Sat Feb 03 09:13:25 2007] [error] an unknown filter was not added: PHP

and apparently has all along!

Here is output from the mod-ssl stuff from [http://la-la-la.com/server-info](http://la-la-la.com/server-info) 
--------
Module Name: mod_ssl.c
Content handlers: none
Configuration Phase Participation: Create Directory Config, Merge Directory Configs, Create Server Config, Merge Server Configs
Request Phase Participation: Post-Read Request, Translate Path, Check Access, Verify User ID, Verify User Access, Fixups
Module Directives:
    SSLMutex - Valid SSLMutex mechanisms are: `none', `default', `flock:/path/to/file', `fcntl:/path/to/file', `sysvsem', `pthread', `file:/path/to/file', `sem' 
    SSLPassPhraseDialog - SSL dialog mechanism for the pass phrase query (`builtin', `|/path/to/pipe_program`, or `exec:/path/to/cgi_program')
    SSLSessionCache - SSL Session Cache storage (`none', `dbm:/path/to/file')
    SSLRandomSeed - SSL Pseudo Random Number Generator (PRNG) seeding source (`startup|connect builtin|file:/path|exec:/path [bytes]')
    SSLEngine - SSL switch for the protocol engine (`on', `off')
    SSLCipherSuite - Colon-delimited list of permitted SSL Ciphers (`XXX:...:XXX' - see manual)
    SSLCertificateFile - SSL Server Certificate file (`/path/to/file' - PEM or DER encoded)
    SSLCertificateKeyFile - SSL Server Private Key file (`/path/to/file' - PEM or DER encoded)
    SSLCertificateChainFile - SSL Server CA Certificate Chain file (`/path/to/file' - PEM encoded)
    SSLCACertificatePath - SSL CA Certificate path (`/path/to/dir' - contains PEM encoded files)
    SSLCACertificateFile - SSL CA Certificate file (`/path/to/file' - PEM encoded)
    SSLCARevocationPath - SSL CA Certificate Revocation List (CRL) path (`/path/to/dir' - contains PEM encoded files)
    SSLCARevocationFile - SSL CA Certificate Revocation List (CRL) file (`/path/to/file' - PEM encoded)
    SSLVerifyClient - SSL Client verify type (`none', `optional', `require', `optional_no_ca')
    SSLVerifyDepth - SSL Client verify depth (`N' - number of intermediate certificates)
    SSLSessionCacheTimeout - SSL Session Cache object lifetime (`N' - number of seconds)
    SSLProtocol - Enable or disable various SSL protocols(`[+-][SSLv2|SSLv3|TLSv1] ...' - see manual)
    SSLUserName - Set user name to SSL variable value
    SSLProxyEngine - SSL switch for the proxy protocol engine (`on', `off')
    SSLProxyProtocol - SSL Proxy: enable or disable SSL protocol flavors (`[+-][SSLv2|SSLv3|TLSv1] ...' - see manual)
    SSLProxyCipherSuite - SSL Proxy: colon-delimited list of permitted SSL ciphers (`XXX:...:XXX' - see manual)
    SSLProxyVerify - SSL Proxy: whether to verify the remote certificate (`on' or `off')
    SSLProxyVerifyDepth - SSL Proxy: maximum certificate verification depth (`N' - number of intermediate certificates)
    SSLProxyCACertificateFile - SSL Proxy: file containing server certificates (`/path/to/file' - PEM encoded certificates)
    SSLProxyCACertificatePath - SSL Proxy: directory containing server certificates (`/path/to/dir' - contains PEM encoded certificates)
    SSLProxyCARevocationPath - SSL Proxy: CA Certificate Revocation List (CRL) path (`/path/to/dir' - contains PEM encoded files)
    SSLProxyCARevocationFile - SSL Proxy: CA Certificate Revocation List (CRL) file (`/path/to/file' - PEM encoded)
    SSLProxyMachineCertificateFile - SSL Proxy: file containing client certificates (`/path/to/file' - PEM encoded certificates)
    SSLProxyMachineCertificatePath - SSL Proxy: directory containing client certificates (`/path/to/dir' - contains PEM encoded certificates)
    SSLOptions - Set one or more options to configure the SSL engine(`[+-]option[=value] ...' - see manual)
    SSLRequireSSL - Require the SSL protocol for the per-directory context (no arguments)
    SSLRequire - Require a boolean expression to evaluate to true for granting access(arbitrary complex boolean expression - see manual)
    SSLLog - SSLLog directive is no longer supported - use ErrorLog.
    SSLLogLevel - SSLLogLevel directive is no longer supported - use LogLevel.
Current Configuration:
    SSLRandomSeed startup builtin
    SSLRandomSeed connect builtin
    SSLPassPhraseDialog builtin
    SSLSessionCache dbm:/var/run/apache2/ssl_scache
    SSLSessionCacheTimeout 300
    SSLMutex file:/var/run/apache2/ssl_mutex
    SSLCipherSuite ALL:!ADH:!EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP:+eNULL 
----------
and the mod-php4.c from server-info:
---------
Module Name: mod_php4.c
Content handlers: yes
Configuration Phase Participation: Create Directory Config, Merge Directory Configs
Request Phase Participation: none
Module Directives:
    php_value - PHP Value Modifier
    php_flag - PHP Flag Modifier
    php_admin_value - PHP Value Modifier (Admin)
    php_admin_flag - PHP Flag Modifier (Admin)
    PHPINIDir - Directory containing the php.ini file
Current Configuration:
---------

Any suggestions? I don't know what the significance of content-handlers:none is in the mod-ssl.c area above. HELP HELP HELP!!

---

### Post by jtc on 2007-02-05
A longshot I guess...

Where is <Directory /var/www/html/webmail/la-la-la> (or similar) defined?

---

### Post by jtc on 2007-02-05
This sounds like something in the direction of your problem?

[http://www.howtoforge.com/forums/showthread.php?t=3386](http://www.howtoforge.com/forums/showthread.php?t=3386)
(scroll down a bit)

Is it possible that there is something not entirely right with your certificate?

---

### Post by quackking on 2007-02-05
JTC, you are absolutely correct!

I recreated the pem file (the self-signed certificate) using the command I found at the bottom of your reference

#openssl req $@ -new -x509 -days 365 -nodes -out /etc/apache2/apache.pem -keyout /etc/apache2/apache.pem (I put the file in the right place later)

and got rid of the line in sites-enabled-ssl.conf that referred to the certificate key file (all I have is the single pem file now)

and now everything works!

It is too bad that there is not any message in the apache errorlog to indicate the bad certificate.

Also, I still wonder how to get rid of the unable to load filter messages. Work for tomorrow, I guess.

Thank you!

---

