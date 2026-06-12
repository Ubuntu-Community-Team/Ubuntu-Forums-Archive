---
title: "Nessus cannot login"
date: 2006-07-16
forum: Server Platforms
---

### Post by culmore on 2006-07-16
Hmmm I must be missing something simple but I just cannot see it. I have install nessus as per these instructions (from the 6.06 release notes)

=================================================================

sudo apt-get install nessus
sudo apt-get install nessusd
sudo nessus-adduser
sudo ln -fs /etc/init.d/nessusd /etc/rc2.d/S20nessusd
sudo /etc/init.d/nessusd start
sudo gedit /usr/share/applications/Nessus.desktop

    * Insert the following lines into the new file 

[Desktop Entry]
Name=Nessus
Comment=Nessus
Exec=nessus
Icon=/usr/share/pixmaps/nessus.xpm
Terminal=false
Type=Application
Categories=Application;System;

===========================================================

simple enough. In fact I have done this on two machines and have gotten the same problem on both. But when I run the nessus client and try and connect I get the terse message "SSL error". Here is the error message that comes to the console when I run the nessus cleint from the console:

 SSL_connect: error:00000000:lib(0):func(0):reason(0)

this corresponds with the "SSL error" message.

Okay so I read various forums etc and come to the conclusion I should disable SSL so I set

ssl_version=none

in the two files

/home/paul/.nessusrc
/etc/nessus/nessusd.conf

But then I get the error message "remote host is not using the good version of the Nessus communication protocol(1.2) or is tcpwrapped". 


so now what can I try? Here are some parts of the config files

.nessusrc

trusted_ca = /var/lib/nessus/CA/cacert.pem
cert_file = /home/paul/.nessus/cert_paul.pem
key_file = /home/paul/.nessus/key_paul.pem

nessusd_host = localhost
nessusd_user = paul
paranoia_level = 2
ssl_version=none
# use_ssl = no
user_client_cert = yes
hide_msglog =  no




# ssl_version = 3

ssl_version=none

# Full path and filename of a trusted certificate authority
# see /usr/share/doc/nessus/README_SSL.gz
# trusted_ca =

# SSL Ciphers to use
# The following removes all SSLv3 ciphers except RC4.
# This has been implemented to workaround an OpenSSL 0.9.8
# bug, for more information please read
# [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=338006](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=338006)
# and
# [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=343487](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=343487)
 ssl_cipher_list = SSLv2:-LOW:-EXPORT:RC4+RSA

# NASL scripts cryptographic checks of some plugins (trusted
# scripts). Nessus will refuse to load and execute trusted
# scripts that are not signed. Use extreme caution when
# setting this to 'yes'

#nasl_no_signature_check = no

# Uncomment the following for IO thread debugging
#track_iothreads = yes

# Set this to 'yes' if you want each child to be nice(2)d
# be_nice = yes

# End of /etc/nessus/nessusd.conf file.
#
# Added by nessus-mkcert
#
cert_file=/var/lib/nessus/CA/servercert.pem
key_file=/var/lib/nessus/private/CA/serverkey.pem
ca_file=/var/lib/nessus/CA/cacert.pem
# If you decide to protect your private key with a password,
# uncomment and change next line
# pem_password=password
# If you want to force the use of a client certificate, uncomment next line
force_pubkey_auth = yes


PS I have tried also turning off the client certificates ie commenting out 

# force_pubkey_auth = yes

and 

user_client_cert=no

but I get the same problems. I am sure it is something simple but I cannot see it. I am also running the service ssh (have even tried turn that off)

---

### Post by culmore on 2006-07-18
maybe my question is not well put basically my problem is that I cannot get the nessus client to connect to the server. I get the message

"SSL error"

if I turn off SSL in both the client and the server I get


"remote host is not using the good version of the Nessus communication protocol(1.2) or is tcpwrapped".

so what do i try next?](*,)

---

### Post by fdamstra on 2006-07-18
Did you run 'nessus-mkcert'?

---

### Post by culmore on 2006-07-18
yes I  did run nessus-mkcert!

---

### Post by charly4711 on 2008-01-03
This is late in coming, but since I've just come across the same problem and it took me some time to research, here's the answer that helped me for the records:

nessus when compiled with libwrap support (as is the case for the version in the repos) adheres to /etc/hosts.allow and /etc/hosts.deny. If you've hardened your system, that may cause the error.

You will also be seeing this in /var/log/nessus/nessusd.messages:
Connection from 127.0.0.1 rejected by libwrap

nessus seems to be rather picky about what you put in /etc/hosts.allow, though.

This, did not work for me:
nessusd: 127.0.0.1/24,192.168.1.5: ALLOW

This did:
nessusd: 127.0.0.1

---

