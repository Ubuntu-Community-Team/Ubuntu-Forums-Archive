---
title: "Mailman Postfix Integration Not Working"
date: 2012-03-07
forum: Server Platforms
---

### Post by MidnightJava on 2012-03-07
I’ve installed Mailman 2.1.12 on Ubuntu 11.04 from the ppa using apt-get install mailman. I also installed postfix in the same way. I followed instructions for installation of both, including using the script postfix-to-mailman.py for integrating the two programs.

Both Mailman and Postfix seem to be working, except they’re not aware of each other. I can create lists with the Mailman web interface, but no e-mails get sent, and there is nothing in postfix log. I can successfully send mail from external accounts to local users on my mail server via postfix, and I can telnet into postfix and manually create an SMTP message and send it to an external user. But if I send mail to mailman-subscribe, postfix reports every few hours that it’s trying to deliver it, and eventually it fails, with no reason except “Unable to deliver this message.”

I have an MX record that points <hostname.lists.my.domain> to the server (hostname) on which postfix and mailman are running. I address mail successfully to local users as <user>@<hostname.lists.my.domain>. I try to send mail to mailman as [email]mailman-subscribe@<hostname.lists.my.domain[/email]. In mm_cfg.py, I have the following settings

mydomain = <lists.my.domain>
myorigin = $myhostname.$mydomain
myhostname = <hostname>
mydestination = $myhostname, localhost, localhost.localdomain, localhost.$mydomain, $mydomain $myhostname.$mydomain
mynetworks_style = subnet
relay_domains = $mynetworks <lists.my.domain>


So I’m apparently missing something in the integration configuration.

I have a couple observations that may indicate where I’ve gone wrong.

1.	[LIST=1]
[/LIST]I put a print statement in the main method of postfix-to-mailman.py, and I don’t see its output in any log file, so it seems it’s never executing. I have the entry in master.cf of Postfix as instructed in the python script, namely 

mailman   unix  -       n       n       -       -       pipe  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py ${nexthop} ${user}

The script is in the location indicated by argv. However, according to man page for master, there should be an executable named mailman in the directory pointed to by $queue_directory. This variable is configured in /usr/share/postfix/main.cf.dist to point to var/spool/postfix. I don’t see an executable mailman at that location. 

2.	[LIST=2]
[/LIST]The python script instructs me to add to Postfix’s main.cf the following: relay_recipient_maps = ... hash:/var/lib/mailman/data/virtual-mailman. I understand mailman is supposed to put entries in virtual-mailman to tell postfix which lists exist. However virtual-mailman does not exist. Am I supposed to do something to have mailman create it?

I tried to ask this question on the Mailman forum, but the moderator rejected it with an explanation that since I'm using a packaged version of Mailman I should seek help from the package provider. It makes sense to me, as I did notice some differences in installed contents and instructions between the ppa version and the version downloaded from the Mailman site. (I previously downloaded and manually installed + configured Mailman + Postfix for OSX, and then decided to implement them on my Ubuntu machine. The integration wasn't working for OSX either.)

---

