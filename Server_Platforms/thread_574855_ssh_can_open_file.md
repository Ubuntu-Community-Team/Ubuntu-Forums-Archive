---
title: "ssh can open file?"
date: 2007-10-13
forum: Server Platforms
---

### Post by Wuu on 2007-10-13
It's more php questions then Ubuntu but still i don't know where i can ask this :( So :)

ssh
[PHP]$connection = ssh2_connect('shell.example.com', 22);
ssh2_auth_password($connection, 'username', 'password');

$sftp = ssh2_sftp($connection);

$stream = fopen("ssh2.sftp://$sftp/path/to/file", 'r');[/PHP]

and my old function with simple file open but i need some more security i don't want leave account file in free access place like apache folder...
[PHP]    $f = fopen($acc_temp, "a+");

    flock($f, LOCK_EX);

    $ok = fputs($f, "[".$acc_name."]\r\nPRIV=0\r\nPASSWORD=".$acc_pass."\r\n"."TAG.EMAIL=".$_POST['rmail']."\r\n"."TAG.PIN=".$acc_pin."\r\n"."TAG.PASSWORD=".$acc_pass."\r\n\r\n");

    flock($f, LOCK_UN);

    fclose($f);   [/PHP]

can i combine them so i can open file with ssh, edit it save and exit ?

---

### Post by GigaVolt on 2007-10-14
Hint 1: scp - secure copy (remote file copy program)
Hint 2: php5-cgi - server-side, HTML-embedded scripting language (CGI binary)

---

