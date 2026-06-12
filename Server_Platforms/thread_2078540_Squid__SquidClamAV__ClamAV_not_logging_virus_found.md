---
title: "Squid / SquidClamAV / ClamAV not logging virus found messages"
date: 2012-10-31
forum: Server Platforms
---

### Post by iefke on 2012-10-31
Hello,

I'm currently working on a Squid setup and using squidclamav / clamav for virus scanning. Everything works as expected, except for the logging of a found virus. I get redirectly correctly to the URL specified in my squidclamav config every time I try to download the EICAR test virus, although not every attempt is logged by either squidclamav (using the c-icap log) or ClamAV.

Did I not configure the setup correctly or could there be something else going on?

Used packages:
squid3 3.1.19-1ubuntu3.12.04.1
c-icap 1:0.1.6-1ubuntu1
libc-icap-mod-squidclamav 6.4-1

And the configs:

C-Icap related squid config:
```
icap_enable on
icap_send_client_ip on
icap_send_client_username on
icap_client_username_encode off
icap_client_username_header X-Authenticated-User
icap_preview_enable on
icap_preview_size 1024
icap_service service_req reqmod_precache bypass=1 icap://127.0.0.1:1344/squidclamav
adaptation_access service_req allow all
icap_service service_resp respmod_precache bypass=1 icap://127.0.0.1:1344/squidclamav
adaptation_access service_resp allow all
```

C-Icap config:
```
PidFile /var/run/c-icap/c-icap.pid
CommandsSocket /var/run/c-icap/c-icap.ctl
Timeout 300
MaxKeepAliveRequests 100
KeepAliveTimeout 600
StartServers 3
MaxServers 10
MinSpareThreads     10
MaxSpareThreads     20
ThreadsPerChild     10
MaxRequestsPerChild  0
Port 1344
User proxy
Group proxy
ServerAdmin monitoring@mydomain.com
ServerName myserver
TmpDir /tmp
MaxMemObject 131072
DebugLevel 1
ModulesDir /usr/lib/c_icap
ServicesDir /usr/lib/c_icap
TemplateDir /usr/share/c_icap/templates/
TemplateDefaultLanguage en
LoadMagicFile /etc/c-icap/c-icap.magic
RemoteProxyUsers off
RemoteProxyUserHeader X-Authenticated-User
RemoteProxyUserHeaderEncoded on
ServerLog /var/log/c-icap/server.log
AccessLog /var/log/c-icap/access.log
Service squidclamav squidclamav.so
Service echo srv_echo.so
```

And the srv_squidclamav.conf:
```
maxsize 5000000
redirect http://www.mydomain.com/proxyerror.ivo
clamd_local /var/run/clamav/clamd.ctl
timeout 1
logredir 1
dnslookup 0
abortcontent ^video\/x-flv$
abortcontent ^video\/mp4$
abort ^.*\.swf$
abortcontent ^application\/x-shockwave-flash$
abortcontent ^.*application\/x-mms-framed.*$
whitelist .*\.clamav.net
```

One other thing I noticed, which may or may not have anything to do with the problem:

```
root@myserver:/etc/c-icap# c-icap -N -d 1 -D
DEBUG squidclamav_init_service: Going to initialize squidclamav
Warning, alias is the same as service_name, not adding
Warning, alias is the same as service_name, not adding
```


Console output when trying to open the EICAR test virus:

```

DEBUG squidclamav_init_request_data: initializing request data handler.
DEBUG squidclamav_check_preview_handler: processing preview header.
DEBUG squidclamav_check_preview_handler: No body data, allow 204
DEBUG squidclamav_release_request_data: Releasing request data.
DEBUG squidclamav_init_request_data: initializing request data handler.
DEBUG squidclamav_check_preview_handler: processing preview header.
DEBUG squidclamav_check_preview_handler: preview data size is 1024
dconnect: entering.
DEBUG squidclamav_end_of_data_handler: Sending STREAM command to clamd.
DEBUG squidclamav_end_of_data_handler: Received port 1736 from clamd.
DEBUG squidclamav_end_of_data_handler: Trying to connect to clamd [port: 1736].
DEBUG squidclamav_end_of_data_handler: Ok connected to clamd on port: 1736.
DEBUG: squidclamav_end_of_data_handler: Scanning data now
DEBUG squidclamav_end_of_data_handler: End Clamd connection, attempting to read result.
DEBUG squidclamav_end_of_data_handler: received from Clamd: stream: OK
DEBUG squidclamav_end_of_data_handler: Closing Clamd connection.
DEBUG squidclamav_release_request_data: Releasing request data.
```

Although I do get redirected to my defined redirect page, nothing is logged about the found virus.

Thanks in advance!

---

### Post by SeijiSensei on 2012-11-02
I'm using CentOS 6 as the platform rather than Ubuntu, but the two should be equivalent.  I get entries in /var/log/c-icap/server.log that look like this:

```
server.log-20121007:Thu Oct  4 08:41:30 2012, general, DEBUG squidclamav_end_of_data_handler: Virus redirection: ....
```

Rather than scan through logs, I use a PHP script as the redirection handler so I can mail a warning notice to the admin when an attempted virus download takes place.

```

<?php

$url=$_REQUEST['url'];
$virus=$_REQUEST['virus'];
$fromip=$_REQUEST['source'];
$fromhost=gethostbyaddr($fromip);

# send a notice to the admin
$to='admin@localhost';
$from='Security Alerts <security@example.com>';
$subj="ALERT: Attempt to Download Malware by $fromhost";
$msg="$fromhost ($fromip)
attempted to download malware from:
$url

Found malware: $virus      
";

mail($to,$subj,$msg,"From: $from");
?>

    <h1>Virus Found!</h1>

    <h3>The file you attempted to access contains a virus or other malware.</h3>

    <p>If you believe this message is in error, 
       <a href="mailto:security@example.com">please 
       contact the IT department</a>.</p>

    <h4>Details</h4>

    <p>URL of infected file: <?php echo $url?>

    <p>Virus scanner message: <?php echo $virus ?>
```

---

### Post by iefke on 2012-12-03
Thank you for your suggestion SeijiSensei, but PHP is not an option for me. 

Does anyone else have a suggestion as to how to fix my problem regarding logging?

---

### Post by SeijiSensei on 2012-12-03
Do you not have entries in the c-icap server log like I showed above?

---

