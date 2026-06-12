---
title: "Spam Relay'ers SMTP"
date: 2011-04-14
forum: Server Platforms
---

### Post by Frizianz on 2011-04-14
Hey guys, 

Basically wanting to create a script that will run and parse my postfix/dovecot logs on the go and find people that are trying to relay though my server and do a whois lookup to find the network administrator for the ip. Then send off preformatted email with the details of the relay attempt. 

Basically this sorta line -> 

> Apr 14 14:06:46 frizianz postfix/smtpd[1782]: NOQUEUE: reject: RCPT from 114-36-4-229.dynamic.hinet.net[114.36.4.229]: 554 5.7.1 <alan0935191105@yahoo.com.tw>: Relay access denied; from=<z2007tw@yahoo.com.tw> to=<alan0935191105@yahoo.com.tw> proto=SMTP helo=<*removed my ip*>

Currently i have the postfix logs all going into syslog, not sure if this is a problem but for me it would prob be easier if they were all seperate, but not sure on how to fix this.

Cheers

---

### Post by Iker Etxebarria on 2011-04-14
You can start with this:

<?php
system("grep 'Relay access denied' mail.log> relay");
$f=fopen('relay','r');
while (!feof($f)){
$result = fgets($f,4096);
if ($result!=''){
$dividido=explode('[',$result);
$cadenas = explode(']', $dividido[2]);
echo $cadenas[0] . "\n";}}
fclose($f);
?>

This is a script file that located in the /var/log directory with super user permissions shows the ips. You can modify it to once you have ips, do the whois and send the mail....

To launch it you have to install php-cli and launch it with
php nameofile.php

---

### Post by Iker Etxebarria on 2011-04-14
Maybe this can be helpfull

<?php
system("grep 'Relay access denied' mail.log> relay");
$f=fopen('relay','r');
while (!feof($f)){
$result = fgets($f,4096);
if ($result!=''){
$dividido=explode('[',$result);
$cadenas = explode(']', $dividido[2]);
echo $cadenas[0] . "\n";
system("whois " . $cadenas[0] . "|grep e-mail > email.txt");
$resulta =  file_get_contents("email.txt");
if ($resulta!=''){
$email = explode(':',$resulta);
mail($email[1],"Email relay access denied. Trying to abuse from our server.",$result);
}}}
fclose($f);
?>

---

### Post by SeijiSensei on 2011-04-14
How about just configuring the server so it's not an open relay?

Notifying network administrators is like spitting in the wind.  Most of them will ignore your report, and many others won't have a clue what to do.  Remember, too, that most spam is sent from compromised Windows machines.  They don't have network administrators.  They're usually sitting in the corner of someone's house or office.

Just the other day there was a news report about botnets that were [available for rent]("http://krebsonsecurity.com/2011/04/is-your-computer-listed-for-rent/").  One of the computers that was listed as available was in a hospital outside Boston.  I actually sent a notice to them about this.  I've never heard a word from them in response.

---

### Post by Frizianz on 2011-04-14
The server is not setup as an open relay, i know half of the time i wont get a reply, but my brother actually suggested the idea as he works at an isp here in NZ but i shall try those ideas, but any others are appreciated.

Is there a way to post the whole log line that the ip address was pulled from? That would make my life easier

---

