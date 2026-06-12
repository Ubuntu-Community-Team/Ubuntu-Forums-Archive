---
title: "Shell Scripting"
date: 2010-05-21
forum: Server Platforms
---

### Post by danielgroves on 2010-05-21
Hi all,

I am trying to write a shell script in order to automate the process of uploading a file onto an FTP server using the built in FTP commands in ubuntu server (lucid).  

In order to connect I can use the following:
```

ftp wsbeorchids.org.uk
Name (wsbeorchids.org.uk:danielgroves): USERNAME
Password: PASSWORD

```

In need to pass my username and password in when prompted the prompts.  How should I go about doing this?

I have tried echoing the values without success.  Please not that I am something of an amateur with scripting.  

Thanks in advance,
Dan.

---

### Post by cdenley on 2010-05-21
I would just use a php script.
[PHP]#!/usr/bin/php
<?php
if(count($argv)<6) die("usage: ./upload.php server user password localfile remotefile\n");
$host=$argv[1];
$user=$argv[2];
$pass=$argv[3];
$local=$argv[4];
$remote=$argv[5];
$ftp=ftp_connect($host) or die("Failed to connect\n");
if(ftp_login($ftp,$user,$pass)) {
        if(ftp_put($ftp,$remote,$local,FTP_BINARY))
                echo "Upload succeeded\n";
        else
                echo "Upload failed\n";
}
else
        echo "Failed to login\n";
ftp_close($ftp);
?>[/PHP]

Make sure you have the "php5-cli" package installed.

---

### Post by iponeverything on 2010-05-21
expect will do the job.

you can install it via the package manger.

[http://expect.nist.gov/](http://expect.nist.gov/)

---

### Post by danielgroves on 2010-05-21
> **cdenley said:**
> I would just use a php script.
[PHP]#!/usr/bin/php
<?php
if(count($argv)<6) die("usage: ./upload.php server user password localfile remotefile\n");
$host=$argv[1];
$user=$argv[2];
$pass=$argv[3];
$local=$argv[4];
$remote=$argv[5];
$ftp=ftp_connect($host) or die("Failed to connect\n");
if(ftp_login($ftp,$user,$pass)) {
        if(ftp_put($ftp,$remote,$local,FTP_BINARY))
                echo "Upload succeeded\n";
        else
                echo "Upload failed\n";
}
else
        echo "Failed to login\n";
ftp_close($ftp);
?>[/PHP]

Make sure you have the "php5-cli" package installed.

Do I just add this to the shell script?  How do I know if I have the php5-cli package?   If it does not exist how do I install it?



> **iponeverything said:**
> expect will do the job.

you can install it via the package manger.

[http://expect.nist.gov/](http://expect.nist.gov/)

Installing things is a bit on an issue.  The server is sat behind a proxy server that is refusing us access to the apt-get servers... technicians are working on that one though.

---

### Post by cdenley on 2010-05-21
> **danielgroves said:**
> Do I just add this to the shell script?

That is a shell script, sort of. You create that file, for example at /usr/local/bin/upload.php. Then make it executable
```

sudo chmod a+rx /usr/local/bin/upload.php

```
Now, to upload a file:
```

upload.php server user password /path/to/localfile /path/to/remotefile

```

> **danielgroves said:**
> 
How do I know if I have the php5-cli package?   If it does not exist how do I install it?
```

sudo apt-get install php5-cli

```

---

### Post by danielgroves on 2010-05-21
Awesome, will have to give that a go on monday.  Can't do it till then as the server is currently mounted in a greenhouse at school, annoyingly IT won't foreword the correct port for me to SSH it from home.  

Thank You cdenley.

---

### Post by just_another_user on 2010-05-22
Or you can use ncftpput command from ncftp package [http://packages.ubuntu.com/dapper/ncftp]("http://packages.ubuntu.com/dapper/ncftp")

---

