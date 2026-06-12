---
title: "Where is the exim4.conf handled"
date: 2012-08-08
forum: Server Platforms
---

### Post by saphil on 2012-08-08
I have an error that Drupal is not waiting for a response from the Exim4 server before sending data to smtp
I want to torn off sync on the exim3 server instead of attempting to fix all sorts of drupal instances on my network.
I understand that the solution is to set the following directive to 'false'  ```
smtp_enforce_sync  
```I cannot find it anywhere

```
root@LTS-MAILBOX-01:/etc/exim4# ls -R
.:
conf.d    exim4.conf.template  passwd.client  update-exim4.conf.conf

./conf.d:
acl  auth  main  retry    rewrite  router  transport

./conf.d/acl:
00_exim4-config_header               30_exim4-config_check_mail  40_exim4-config_check_data
20_exim4-config_local_deny_exceptions  30_exim4-config_check_rcpt

./conf.d/auth:
00_exim4-config_header    30_exim4-config_examples

./conf.d/main:
01_exim4-config_listmacrosdefs    03_exim4-config_tlsoptions
02_exim4-config_options        90_exim4-config_log_selector

./conf.d/retry:
00_exim4-config_header    30_exim4-config

./conf.d/rewrite:
00_exim4-config_header    31_exim4-config_rewriting

./conf.d/router:
00_exim4-config_header         400_exim4-config_system_aliases  850_exim4-config_lowuid
100_exim4-config_domain_literal  500_exim4-config_hubuser      900_exim4-config_local_user
150_exim4-config_hubbed_hosts     600_exim4-config_userforward      mmm_mail4root
200_exim4-config_primary     700_exim4-config_procmail
300_exim4-config_real_local     800_exim4-config_maildrop

./conf.d/transport:
00_exim4-config_header          30_exim4-config_maildrop_pipe
10_exim4-config_transport-macros  30_exim4-config_mail_spool
30_exim4-config_address_file      30_exim4-config_procmail_pipe
30_exim4-config_address_pipe      30_exim4-config_remote_smtp
30_exim4-config_address_reply      30_exim4-config_remote_smtp_smarthost
30_exim4-config_maildir_home      35_exim4-config_address_directory

```This command prints all the files above to less and I do not see it.
 ```
root@LTS-MAILBOX-01:/etc/exim4# cat ./* "smtp_enforce_sync"|less
```

---

### Post by saphil on 2012-08-09
[http://blog.edseek.com/archives/2005/02/02/hacked-initd-script-for-3dmd/](http://blog.edseek.com/archives/2005/02/02/hacked-initd-script-for-3dmd/) has a line in it 
> One solution is to disable Exim4&#8242;s synch check for SMTP commands.  On Debian GNU/Linux, you’d edit /etc/exim4/exim4.conf.template  if you’re using the automatically generated configuration and add the  following somewhere in the configuration section for ‘main’ near the  top.
 smtp_enforce_sync = false  Restart Exim4 and you can receive mail from 3dm2.
I added that line and my error is:
```
SMTP -> get_lines(): $data was "" 
SMTP -> get_lines(): $str is "220 mailserver.org ESMTP Exim 4.72 Thu, 09 Aug 2012 07:39:14 -0400 " 
SMTP -> get_lines(): $data is "220 mailserver.org ESMTP Exim 4.72 Thu, 09 Aug 2012 07:39:14 -0400 " 
SMTP -> FROM SERVER: 220 mailserver.org ESMTP Exim 4.72 Thu, 09 Aug 2012 07:39:14 -0400  
SMTP -> ERROR: EHLO not accepted from server: 220 mailserver.org ESMTP Exim 4.72 Thu, 09 Aug 2012 07:39:14 -0400  
SMTP -> get_lines(): $data was "" 
SMTP -> get_lines(): $str is "250-mailserver.org Hello www.drupal7.net [192.168.10.17] " 
SMTP -> get_lines(): $data is "250-mailserver.org Hello www.drupal7.net [192.168.10.17] " 
SMTP -> get_lines(): $data was "250-mailserver.org Hello www.drupal7.net [192.168.10.17] " 
SMTP -> get_lines(): $str is "250-SIZE 52428800 " 
SMTP -> get_lines(): $data is "250-lyrasistechnology.org Hello www.drupal7.net [192.168.10.17] 250-SIZE 52428800 " 
SMTP -> get_lines(): $data was "250-mailserver.org Hello www.drupal7.net [192.168.10.17] 250-SIZE 52428800 " 
SMTP -> get_lines(): $str is "250-PIPELINING " 
SMTP -> get_lines(): $data is "250-mailserver.org Hello www.drupal7.net [192.168.10.17] 250-SIZE 52428800 250-PIPELINING " 
SMTP -> get_lines(): $data was "250-mailserver.org Hello www.drupal7.net [192.168.10.17] 250-SIZE 52428800 250-PIPELINING " 
SMTP -> get_lines(): $str is "250 HELP " 
SMTP -> get_lines(): $data is "250-mailserver.org Hello www.drupal7.net [192.168.10.17] 250-SIZE 52428800 250-PIPELINING 250 HELP " 
SMTP -> FROM SERVER: 250-mailserver.org Hello www.drupal7.net [192.168.10.17] 250-SIZE 52428800 250-PIPELINING 250 HELP  
SMTP -> get_lines(): $data was "" 
SMTP -> get_lines(): $str is "250 mailserver.org Hello www.drupal7.net [192.168.10.17] " 
SMTP -> get_lines(): $data is "250 mailserver.org Hello www.drupal7.net [192.168.10.17] " 
SMTP -> FROM SERVER:250 mailserver.org Hello www.drupal7.net [192.168.10.17]  
SMTP -> get_lines(): $data was "" 
SMTP -> get_lines(): $str is "250 OK " 
SMTP -> get_lines(): $data is "250 OK " 
SMTP -> FROM SERVER:250 OK  
SMTP -> get_lines(): $data was "" 
SMTP -> get_lines(): $str is "250 Accepted " 
SMTP -> get_lines(): $data is "250 Accepted " 
SMTP -> FROM SERVER:250 Accepted  
SMTP -> ERROR: DATA command not accepted from server: 250 Accepted  
SMTP Error: Data not accepted.
```Mailserver.org:/var/log/exim4/mainlog said that the machines IP did not resolve to a name, though in the next line they were shown with their LAN machine name, so I added the machines to the mailserver's /etc/hosts file

The last error still shows when I try to send a test email from the drupal sites, and the 
mainlog on the mail server says
```
2012-08-09 08:04:28 End queue run: pid=9987
2012-08-09 08:07:30 SMTP connection from www.drupal7.net [192.168.10.17] lost while reading message data (header)

```
At least it is no longer saying that the IP doesn't resolve.

Other mail issues are starting to come up from machines that were not having issues before, so I am going to comment out the "smtp_enforce_sync" line.

---

### Post by saphil on 2012-08-09
wolf@Drupal-7-01:~$ telnet mailserver.org 25
Trying 192.168.10.25...
Connected to mailserver.org.
Escape character is '^]'.
220 mailserver.org ESMTP Exim 4.72 Thu, 09 Aug 2012 08:22:21 -0400

wolf@Drupal-7-02:~$ telnet mailserver.org 25
Trying 192.168.10.25...
Connected to mailserver.org.
Escape character is '^]'.
220 mailserver.org ESMTP Exim 4.72 Thu, 09 Aug 2012 08:24:46 -0400

---

### Post by saphil on 2012-08-09
… The solution seems to be running a mail-server from the drupal machine and making the support user support@localhost. 
Then the user's mail gets properly dumped to the local server that sends it to the main mailserver.

---

