---
title: "slow PHP mail() function with sendmail"
date: 2008-01-04
forum: Server Platforms
---

### Post by HeyItsMatt on 2008-01-04
Hello everyone.

After a lot of struggling I have gotten PHP to send mail using the mail() function with sendmail installed.  The mail function returns 1 in the PHP code, and I receive the email in mailinator and gmail (my college account doesn't receive it but it doesn't really matter because I only want this set up to be able to use mail() while I am learning PHP).

The problem, however, is that the mail() function takes between 30 seconds and 1 minute to actually send the mail (the mail is just a small test email, no crazy attachments or anything).  Is this normal or is this something that I could fix with some kind of config modification?

Alternatively, is there an alternative email program I can install with a minimum of setup or mail server knowledge in order to use PHP mail() more efficiently for test purposes?  I tried messing with exim4 and it did not seem to work, and postfix (although more briefly) seemed to have issues too.

If I try exim4 or postfix, do I need to leave sendmail installed and install these also, or remove sendmail first?  I had the impression that exim and postfix somehow interacted with sendmail, but when I do "sudo aptitude install" for exim4 it claims there are dependency conflicts and a package sendmail requires must be removed.

So, any suggestions for how to fix sendmail or choose an alternative that does not require becoming a mail server administration expert?

*EDIT* If it's needed, my php.ini sendmail_path is set to "/usr/sbin/sendmail -t" (I also tried -t -i, it goes through but does it slowly for either line).

---

### Post by johncudd on 2008-02-13
I have the EXACT same problem. The mail function works, but it takes a good minute or two to work. I think it's an issue with the way I have it configured. I hope someone figures this one out, it's annoying to have to wait so long while testing a PHP login script. 

I'm doing the same thing, running an appache server locally to learn PHP.

---

### Post by KCPokes on 2008-02-13
I've seen this before as well and it is related to your sendmail configuration rather then any PHP calls.  Typically the biggest offender is the fact that you do not have your machine set up with a fully qualified name, which Sendmail really tends to shy upon.  Look at your system log, from startup, and you'll typically find a message relating to Sendmail and "short name".  Normally you can just work around it by assigning yourself a FQDN in your host file, local to your machine.

---

### Post by wmcdona89 on 2008-03-03
I found that sendmail was slow on my machine because I had my hostname mapped to 127.0.0.1 in my /etc/hosts file. I now just have:
127.0.0.1   localhost

I also found that I needed to specify an additional_parameter to the mail function. The -f sendmail option sets the envelope sender address. Without this, sendmail refused to send my messages.
mail($emailaddress,"Subject: $subject",$message,"From: $email", "-f$email" )

see [http://us3.php.net/manual/en/function.mail.php](http://us3.php.net/manual/en/function.mail.php)

Now the PHP mail function returns almost instantly and my messages are sent successfully.

---

### Post by R.Bucky on 2008-04-27
Could you clarify the file that you are referring to in the "additional_parameter" and "sendmail" function? I just set up my apache server and sendmail. It is really quite slow. What file would these extra arguements append to?

---

### Post by Adam_NZ on 2008-04-28
> **KCPokes said:**
> I've seen this before as well and it is related to your sendmail configuration rather then any PHP calls.  Typically the biggest offender is the fact that you do not have your machine set up with a fully qualified name, which Sendmail really tends to shy upon.  Look at your system log, from startup, and you'll typically find a message relating to Sendmail and "short name".  Normally you can just work around it by assigning yourself a FQDN in your host file, local to your machine.

I have exactly the same [delay] problem. I haven't set up a FQDN. Apart from setting it up in the host file, would I need to amend the Apache config?

---

### Post by R.Bucky on 2008-04-29
The forum posts that I have been reading say that the "hosts", "hostsname", and "apache2.conf" file all need to include the FQDN. I cannot get a straight answer to this post on how to configure the mailserver properly. For now, i disabled the option on my server. It stopped working all together once I put in my FQDN. Time to place my backup files in those directories!

Part of my problem is the FQDN. I understand the format of [ip address] [long name] [short name], but do not understand the nslookup portion to determine the name. My results are mark@"username"-desktop. So, what is my long and short name?I tried variations like [ip] "username"-desktop] ["username"]. No such luck.

Well, I hope that you figure it out. I am not getting anywhere.

---

### Post by Adam_NZ on 2008-04-29
> **R.Bucky said:**
> The forum posts that I have been reading say that the "hosts", "hostsname", and "apache2.conf" file all need to include the FQDN. I cannot get a straight answer to this post on how to configure the mailserver properly. For now, i disabled the option on my server. It stopped working all together once I put in my FQDN. Time to place my backup files in those directories!

Part of my problem is the FQDN. I understand the format of [ip address] [long name] [short name], but do not understand the nslookup portion to determine the name. My results are mark@"username"-desktop. So, what is my long and short name?I tried variations like [ip] "username"-desktop] ["username"]. No such luck.

Well, I hope that you figure it out. I am not getting anywhere.

I'm no expert, but I think the FQDN format is like this:

hostname.mydomain.com hostname

If you know your IP address, then I *think* you can use:

192.168.1.159 hostname

The "hostname" in this case is an alias - and can be anything you want, but it's usually your server's network name.

---

### Post by Adam_NZ on 2008-04-29
Well ... it looks like I may have solved it! After Googling around all over the place and getting utterly confused by the geekiness of it, I did this:

Edit your hosts file:
/etc/hosts

Here's what I added:
192.168.1.160 ub6 ub6.localdomain loghost

... where ub6 is my hostname. If you haven't got a domain attached to that server, any old name will do ("localdomain", in my case) I've no idea what "loghost" does ... I just copied what I saw on some web page.

I changed *nothing else* ... anywhere ... and my PHP mailscript fires and sends immediately now. What's more, it actually sends out the email as well!

---

### Post by R.Bucky on 2008-04-30
Hey, I added the info on your last post to the hosts file. I changed the ip address that you had in there, which was the router ip, to my hard ip (24.18.97.15). I can send mail like a madman now, but it does not show up in my inbox. 

I believe that in my fooling around, I may have changed my /etc/hostname file. Mine reads "127.0.0.1 localhost." Shouldn't it also have something like username-desktop?

---

### Post by wmcdona89 on 2008-05-03
I'm running sendmail on Slackware 10.2 but I think the following all applies to Ubuntu as well.

My /etc/HOSTNAME file contains:
xunil

My /etc/hosts file now contains:
127.0.0.1 localhost localhost.localdomain xunil

In my previous post, I stated that the sendmail delays were due to the server's hostname being mapped to 127.0.0.1. I was mapping both localhost and xunil to 127.0.0.1 and sendmail was trying to use xunil but it was unqualified.
From /var/log/maillog
May  3 18:20:11 localhost sendmail[6973]: My unqualified host name (xunil) unknown; sleeping for retry
May  3 18:21:11 localhost sendmail[6973]: unable to qualify my own domain name (xunil) -- using short name

Sendmail worked when only localhost was mapped to 127.0.0.1 but then I found that my apache server wouldn't start because it couldn't resolve my hostname (xunil). I ran some more tests and found that if both localhost.localdomain and the server's hostname are mapped to 127.0.0.1 that sendmail will use localhost.localdomain as the domain name and consider it to be qualified.

To summarize my findings:
-/etc/hosts file
127.0.0.1 localhost localhost.localdomain xunil
-things break if I don't map localhost to 127.0.0.1
-apache will fail to start if I don't map my system's hostname (xunil) to 127.0.0.1
-sendmail requires a qualified domain name and localhost.localdomain is sufficient in cases where your computer doesn't have a real FQDN

The /etc/mail/local-host-names file can be used to ensure that mail sent to the local server from the local server (cron reports for example) is accepted locally and not forwarded to the external mail server. Put 1 host/domain per line. I think this is necessary when using an FQDN other than localhost.localdomain.

Check the /var/log/maillog file to help debug sendmail problems.

Finally, if using the php mail function, include the -f parameter to ensure that mail gets delivered.
mail($emailaddress,"Subject: $subject",$message,"From: $email", "-f$email" )

---

### Post by nomaam on 2008-06-12
I am having a very hard time getting sendmail to send messages within a decent time frame. 

Right now sendmail works but it takes well over a minute or two to send a message with a simple line of text. 

My hosts file looks like this:

127.0.0.1 localhost localhost.localdomain first.com second.com

My hostname file contains just the name of the computer. I'm not sure if I have to enter each .com address in the hostname file as well?

Any suggestions would be appreciated.

---

### Post by Dr_Snapid on 2008-07-02
> **wmcdona89 said:**
> 
mail($emailaddress,"Subject: $subject",$message,"From: $email", "-f$email" )


This is what fixed it for me.

---

