---
title: "Possible to have local smarthost send mail to ISP smarthost"
date: 2009-12-21
forum: Server Platforms
---

### Post by secondstage on 2009-12-21
I have one server running dovecot and exim4 (which can send email perfectly fine) along with 3 other servers that I'd like to send mail with, mostly from PHP calls to the function mail(). 

How can I setup PHP, or exim4 or whatever on the other 3 servers to send the emails to the one server running dovecot and exim4 to then be sent to my ISP's smarthost?

---

### Post by secondstage on 2009-12-21
Somewhere in trying to figure this myself, I have lost the ability to send mail from the first server. I have pretty much purged all mail related packages, and am starting from the ground up.

A more appropriate question to ask now, I guess, is What packages should be installed to allow for the server to receive email via SMTP and then send them out to the mail.bellsouth.net smarthost?

And what packages should be installed on the servers that will send the emails to this SMTP server?

Please note that the "client" servers will be using PHP to send the emails to the SMTP server. 

Thanks in advance if anyone gracefully enlightens me on this subject.

---

### Post by secondstage on 2009-12-21
Me again! Got it fixed. 

I'll post my solution in hopes that it will someday be useful for someone. 

[SIZE=4][COLOR=Black]Setup the Relay Host[/COLOR][/SIZE]
Firstly, follow [this]("https://help.ubuntu.com/community/Postfix") tutorial for installed and configuring postfix. This is the for the server which will be the relay host for the other servers in the local network. If you are using a smarthost, as in mail.bellsouth.net then don't forget to put brackets around the address (ie [mail.bellsouth.net]). If you fail to have the brackets around the domain name, then the connection will time out always, leading to unneeded frustration. For the configuration part, specifically the Local networks: add **192.168.0.0/24** to the end of it. This will allow for anyone computer within your local area network to use the server as a relay host. If you don't want everyone in your local network, then specify the IP addresses for which you do want to use. (Separate each by a space). Finish off the tutorial.


[SIZE=4]Setup the Clients[/SIZE]
Now for each "client" server that will be using the relay host install exim4.
```
sudo aptitude install exim4
```Note: I use exim4 here, because it is often simpler to install and configure than postfix.
Now configure exim4.
```
sudo dpkg-reconfigure exim4-config
```For this configuration, use the following settings:

[LIST]
[*]mail sent by smarthost; no local mail
[*][whatever your Fully Qualified Domain Name is. If you don't have one and don't want to pay for one, then us dyndns.org to get a nice subdomain, which will work fine with this.]
[*]127.0.0.1
[*][hit enter for this one]
[*][again, whatever your Fully Qualified Domain Name is. If you don't have one and don't want to pay for one, then us dyndns.org to get a nice subdomain, which will work fine with this.]
[*][This should be the IP address of the relay host you made in the start. If you don't know the IP address of the relay host, then use the command **ifconfig** on the relay host machine and it should be in there somewhere.]
[*][use the appropriate setting for your system]
[*][again, use the appropriate setting for your system]
[/LIST]

You should be good to go now. 

[SIZE=4]Testing[/SIZE]
To do some testing either telnet into the relay host while on one of the clients, or use a php script and execute the mail() function.

**Telnet Testing:**
[http://www.wikihow.com/Send-Email-Using-Telnet](http://www.wikihow.com/Send-Email-Using-Telnet)

**PHP Testing:**
Install command line php:
```
sudo aptitude install php5-cli
```Navigate your home directory, make a script file, and open it
```
cd
touch mailtest.php
nano mailtest.php
```Copy the script below into it.
```
<?php
$recipient      = 'somewhere@somedomain.com';
$subject = 'HELLOOO!!!!!';
$message = 'Umm. It works.';

$result = mail($recipient, $subject, $message);

if ($result) {print 'Good! :)';} else {print 'Bad! :(';}
print "\n";
?>
```Hit Ctrl-x then y then enter
You should be back at the prompt now, use the command below.
```
php mailtest.php
```If you get Good then it was successful according to the client server. If Bad then the client server configuration is messed up. If you get Good and the $recipient gets the email, then the client is good,  and the relay host is good. If you don't get the email, then go through the log files on the relay host (/var/log/mail.err /var/log/mail.log /var/log/mail.warn /var/log/mail.info) and the log on the client (/var/log/exim4/mainlog) and google your problem or post it here for help.


Good Luck to all in this sometimes-confusing endeavour.

---

