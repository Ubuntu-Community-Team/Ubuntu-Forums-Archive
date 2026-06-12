---
title: "Drupal 6 Ubuntu 10.10 Site email account can't be verified"
date: 2011-04-06
forum: Server Platforms
---

### Post by Horatio on 2011-04-06
Hello,

I've successfully set-up Drupal on my machine on a local network and have no problem accessing it with the virtual host names defined in /etc/hosts, but I don't have bind or any other DNS set-up.

I've installed Postfix and can sent email with the mail command to unix account, and I can also read them with the mail command( from the command line).

Now, my problem is with not being able to use the local Unix email accounts in drupal. Particularly, I would like to have one of the unix account receive email for the development site. I tried to put webuser@localhost in the sites email form during drupal set-up, but the forum give me an error message in return. It tell me that the email is not valid?

I might like to also have various user on the drupal installation, and then test sending notifications to them.

here is my /etc/postfix/main.cf
[INDENT]# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem                                                                                                                              
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key                                                                                                                             
smtpd_use_tls=yes                                                                                                                                                                     
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache                                                                                                               
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache                                                                                                                 
                                                                                                                                                                                      
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for                                                                                                             
# information on enabling SSL in the smtp client.                                                                                                                                     
                                                                                                                                                                                      
myhostname = localhost                                                                                                                                                               
alias_maps = hash:/etc/aliases                                                                                                                                                        
alias_database = hash:/etc/aliases                                                                                                                                                    
mydestination = localhost.localdomain, localhost                                                                                                                          
relayhost =                                                                                                                                                                           
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128                                                                                                                             
mailbox_size_limit = 0                                                                                                                                                                
recipient_delimiter =                                                                                                                                                                 
inet_interfaces = loopback-only                                                                                                                                                       
default_transport = error                                                                                                                                                             
relay_transport = error                                                                                                                                                               
inet_protocols = ipv4
virtual_alias_maps = regexp:$config_directory/virtual-regexp
local_recipient_maps = proxy:unix:passwd.byname $alias_maps[/INDENT]

I'll be very happy to find the problem. Thanx in advance for the outstanding help!

---

### Post by falko on 2011-04-06
Does Drupal accept webuser@localhost.localdomain?

---

### Post by Horatio on 2011-04-06
Thanks a lot falko:D The night before, I had read through many of the man pages and READMEs which came with postfix. I found the magic words

[INDENT]local_recipient_maps = proxy:unix:passwd.byname $alias_maps[/INDENT]

but needed to get some rest. I decided to give the magic a try the next morning, before going to my day job, and I only try the machines name, ie webuser@machienname - machinename was in my /etc/hosts file too. Sorry, it slipped my mind that I didn't even try Webuser@localhost. Anyway, it didn't work because postfix was not accepting requests from my networks ip:o 

Now they all work with some extra magic:
[INDENT]mynetworks = 192.168.0.0/24 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128[/INDENT]
 
webuser@localhost
[email]webuser@localhost.locald[/email]omain
and
webuser@machinename

Thanks again. 

Wenn wir uns jemals in Deutschland begegnen dann soll ich dir ein Bier oder einen Kaffee spendieren. Hoffentlich könnte Sie mein Deutsch verbitten.

---

