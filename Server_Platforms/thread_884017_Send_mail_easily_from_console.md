---
title: "Send mail easily from console ?"
date: 2008-08-08
forum: Server Platforms
---

### Post by BSK on 2008-08-08
Hi,

I have some bash script that would need mailing capability, I tried to send mail with mutt or sendmail directly but I can't get it to work.

I'm on a corporate network and I just want to forward my mail to our smtp server or my isp's smtp server.

A simple console command with a switch to specify smtp server would be awesome.

Anyone has any idea ?

Thanks

---

### Post by HermanAB on 2008-08-08
You need an MTA.  Postfix is overkill and hard to configure.  Try nullmailer:
[http://untroubled.org/nullmailer/](http://untroubled.org/nullmailer/)

The only thing nullmailer does is forward mail, which is exactly what you want.

Cheers,

Herman

---

### Post by BSK on 2008-08-09
thanks, it works great and it's easy to configure.

I just wonder if it's possible to send file attachment with it...

---

### Post by PerJensen on 2008-08-09
I use mutt in my bash scripts, something like this:


mutt -s "Here is the attached mail"  -a the.attached.file [email]someone@some.doma[/email]in << EOF

Hi there, 

Here is the file

Regards
Per

EOF

---

### Post by zorrek on 2009-05-01
What you are after is sendEmail

[http://packages.ubuntu.com/dapper/sendemail](http://packages.ubuntu.com/dapper/sendemail)
"SendEmail is a lightweight, completly command line based, SMTP email agent.

It was designed to be used in bash scripts, Perl programs, and web sites, but it is also quite useful in many other contexts.

SendEmail is written in Perl and is unique in that it requires no special modules. It has a straight forward interface, making it very easy to use. "

cli example
sendEmail -t [email]address@WhoYouWantToSendItTo.com.au[/email] -a FileNameOfAnAttachmentIfYouWant -f [email]your@email.addres[/email]s
This will then allow you to type an e-mail if you stop here it will timeout after40 seconds and send the e-mail with no message just the attachment.

sendEmail-1.55 by Brandon Zehm <caspian@dotconf.net>

Synopsis:  sendEmail -f ADDRESS [options]
  
  Required:
    -f ADDRESS                from (sender) email address
    * At least one recipient required via -t, -cc, or -bcc
    * Message body required via -m, STDIN, or -o message-file=FILE
    
  Common:
    -t ADDRESS [ADDR ...]     to email address(es)
    -u SUBJECT                message subject
    -m MESSAGE                message body
    -s SERVER[:PORT]          smtp mail relay, default is localhost:25
    
  Optional:
    -a   FILE [FILE ...]      file attachment(s)
    -cc  ADDRESS [ADDR ...]   cc  email address(es)
    -bcc ADDRESS [ADDR ...]   bcc email address(es)
    -xu  USERNAME             username for SMTP authentication
    -xp  PASSWORD             password for SMTP authentication
    
  Paranormal:
    -b BINDADDR[:PORT]        local host bind address
    -l LOGFILE                log to the specified file
    -v                        verbosity, use multiple times for greater effect
    -q                        be quiet (i.e. no STDOUT output)
    -o NAME=VALUE             advanced options, for details try: --help misc
        -o message-file=FILE         -o message-format=raw
        -o message-header=HEADER     -o message-charset=CHARSET
        -o reply-to=ADDRESS          -o timeout=SECONDS
        -o username=USERNAME         -o password=PASSWORD
        -o tls=<auto|yes|no>         -o fqdn=FQDN
  
  Help:
    --help                    the helpful overview you're reading now
    --help addressing         explain addressing and related options
    --help message            explain message body input and related options
    --help networking         explain -s, -b, etc
    --help output             explain logging and other output options
    --help misc               explain -o options, TLS, SMTP auth, and more


> **BSK said:**
> Hi,

I have some bash script that would need mailing capability, I tried to send mail with mutt or sendmail directly but I can't get it to work.

I'm on a corporate network and I just want to forward my mail to our smtp server or my isp's smtp server.

A simple console command with a switch to specify smtp server would be awesome.

Anyone has any idea ?

Thanks

---

### Post by drumfire420 on 2009-05-17
thanks that works like a charm for me ^_^

---

