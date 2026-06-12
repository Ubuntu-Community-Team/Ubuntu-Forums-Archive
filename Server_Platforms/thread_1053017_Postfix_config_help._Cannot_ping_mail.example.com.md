---
title: "Postfix config help. Cannot ping mail.example.com"
date: 2009-01-28
forum: Server Platforms
---

### Post by trileru on 2009-01-28
Hello. I just installed Ubuntu 8.10 Server Edition on my Dell R300. I did that from the Perfect Server description. Everything except the mail server works great. Thing is...i cannot ping mail.example.com (example.com beeing my domain)

the output of the files is 

cat /etc/hosts
127.0.0.1 localhost
89.xxx.xxx.xxx server1

cat /etc/hostname
server1

cat /etc/bind/named.conf
options {
pid-file "/var/run/bind/run/named.pid";
directory "/etc/bind";
auth-nxdomain no;
/*
* If there is a firewall between you and nameservers you want
* to talk to, you might need to uncomment the query-source
* directive below. Previous versions of BIND always asked
* questions using port 53, but BIND 8.1 uses an unprivileged
* port by default.
*/
// query-source address * port 53;
};

//
// a caching only nameserver config
//
zone "." {
type hint;
file "db.root";
};

zone "0.0.127.in-addr.arpa" {
type master;
file "db.local";
};


zone "example.com" {
type master;
file "pri.example.com";
};
zone "otherexample.com" {
type master;
file "pri.otherexample.com";
};



//// MAKE MANUAL ENTRIES BELOW THIS LINE! ////




cat /etc/bind/pri.example.com
$TTL 86400
@ IN SOA ns1.example.com. xxx.gmail.com. (
2009012801 ; serial, todays date + todays serial #
28800 ; refresh, seconds
7200 ; retry, seconds
604800 ; expire, seconds
86400 ) ; minimum, seconds
;
NS ns1.example.com. ; Inet Address of name server 1
NS ns2.example.com. ; Inet Address of name server 2
;

mail MX 10 example.com.

example.com. A 89.xxx.xxx.xxx
www A 89.xxx.xxx.xxx

ftp CNAME example.com.

example.com.example.com. TXT "v=spf1 a ptr ~all"


;;;; MAKE MANUAL ENTRIES BELOW THIS LINE! ;;;;



cat /etc/bind/pri.otherexample.com
$TTL 86400
@ IN SOA ns1.otherexample.com. xxx.gmail.com. (
2009012205 ; serial, todays date + todays serial #
28800 ; refresh, seconds
7200 ; retry, seconds
604800 ; expire, seconds
86400 ) ; minimum, seconds
;
NS ns1.otherexample.com. ; Inet Address of name server 1
NS ns2.otherexample.com. ; Inet Address of name server 2
;

mail MX 10 otherexample.com.

otherexample.com. A 89.xxx.xxx.xxx
www A 89.xxx.xxx.xxx

ftp CNAME otherexample.com.

;;;; MAKE MANUAL ENTRIES BELOW THIS LINE! ;;;;




cat /etc/aliases
# See man 5 aliases for format
postmaster: root






cat /etc/postfix/main.cf
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific: Specifying a file name will cause the first
# line of that file to be used as the name. The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

mydomain = example.com
myhostname = mail.example.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = /etc/postfix/local-host-names
relayhost =
mynetworks = 89.xxx.xxx.0/30, 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject _unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
message_size_limit=102400000
virtual_maps = hash:/etc/postfix/virtusertable

mydestination = /etc/postfix/local-host-names





cat /etc/postfix/local-host-names
###################################
#
# ISPConfig local-host-names Configuration File
# Version 1.0
#
###################################
localhost
server1.example.com
localhost.server1.example.com
localhost.example.com
localhost.localdomain
[www.example.com](www.example.com)
[www.otherexample.com](www.otherexample.com)
webmail.example.com
otherexample.com
example.com
#### MAKE MANUAL ENTRIES BELOW THIS LINE! ####
mail.example.com


cat /etc/mailname
mail.example.com




Now...there are a lot of files with alot of hostnames and such... I have an external IP and i access on port 81 ispconfig. I want to host 4 domains, each with 1 subdomain for webmail. I need mail.example.com accessable. If i ping it i get this:

ping mail.example.com
ping: unknown host mail.example.com 

(once again, example.com is my example domain, it's not the real one :P )

What did i do wrong?

Furthermore...i want to host 4 domains in the future...let's say
example.com
otherexample.com
example3.com and
example4.com

Now...i wanna have a dns entry for each one of mail.example.com, mail.otherexample.com etc...how can i host mail server for 4 domains? let's say when i config the mail manager, i put at server mail.example.com, on another account mail.example3.com etc..
Basically i wanna host 4 mail servers for each of the 4 domains... Is it possible?

---

