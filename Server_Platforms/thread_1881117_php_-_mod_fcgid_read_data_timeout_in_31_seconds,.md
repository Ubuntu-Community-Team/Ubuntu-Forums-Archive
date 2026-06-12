---
title: "php - mod_fcgid: read data timeout in 31 seconds,"
date: 2011-11-14
forum: Server Platforms
---

### Post by clubbing80s on 2011-11-14
Hi.
I'm have installed phpwiki on my server. I'm running LAMP Virtualmin stack. Each virtualhost runs under suexec as a separate user, and thus php-cgi is used. 

When trying to restore a backup (3.2MB) into phpwiki I get 500 Internal server error and the following errors in the logs :

[Tue Nov 15 17:19:55 2011] [warn] [client 192.168.69.237] mod_fcgid: read data timeout in 31 seconds, referer: [http://test-phpwiki.example.com/index.php/PhpWikiAdministration]("http://test-phpwiki.et.endace.com/index.php/PhpWikiAdministration")
[Tue Nov 15 17:19:55 2011] [warn] [client 192.168.69.237] (110)Connection timed out: mod_fcgid: ap_pass_brigade failed in handle_request function, referer: [http://test-phpwiki.example.com/index.php/PhpWikiAdministration]("http://test-phpwiki.et.endace.com/index.php/PhpWikiAdministration")

I have changed all the timeout values I can find, and no change.

From Apache config: 
<IfModule mod_fcgid.c>
  AddHandler    fcgid-script .fcgi
  FcgidConnectTimeout 300
IdleTimeout 3600
ProcessLifeTime 7200
MaxProcessCount 1000
DefaultMinClassProcessCount 3
DefaultMaxClassProcessCount 100
IPCConnectTimeout 8
IPCCommTimeout 600
BusyTimeout 300
</IfModule>

php.ini
post_max_size = 32M
max_input_time = 600
max_execution_time = 600
upload_max_filesize = 32M

Most of the values are insane ..

Where else can I look ?

Thanks
G

---

### Post by clubbing80s on 2011-11-16
I found the issue. 
The was a duplicate entry for IPCCommTimeout in the virtualhost config that was over riding the global settings where I was making all my changes.

Ooops.

---

