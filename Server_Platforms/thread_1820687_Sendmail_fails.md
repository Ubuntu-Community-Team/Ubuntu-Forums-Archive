---
title: "Sendmail fails"
date: 2011-08-07
forum: Server Platforms
---

### Post by PierreRobiquet on 2011-08-07
I seem to be having an error with sendmail that whenever attempting to send mail with it for example with the command

```
echo "Subject: test" | /usr/lib/sendmail -v blahblah@gmail.com
```I will get the error:

```
Deferred: Connection refused by [127.0.0.1]
```When attempting to telnet to port 25 on my localhost the connection is refused, when attemping to run the command "sudo service sendmail start" I get the error that sendmail doesn't exist however according to apt it does. I have done an apt-get purge sendmail then reinstalled the package however it has not fixed the issue, the one thing I have noticed is that sendmail is absent from /etc/init.d

Is there anything I can do to fix sendmail?

---

### Post by fdrake on 2011-08-07
> **ConcreteDonkey said:**
> I seem to be having an error with sendmail that whenever attempting to send mail with it for example with the command

```
echo "Subject: test" | /usr/lib/sendmail -v blahblah@gmail.com
```I will get the error:

```
Deferred: Connection refused by [127.0.0.1]
```When attempting to telnet to port 25 on my localhost the connection is refused, when attemping to run the command "sudo service sendmail start" I get the error that sendmail doesn't exist however according to apt it does. I have done an apt-get purge sendmail then reinstalled the package however it has not fixed the issue, the one thing I have noticed is that sendmail is absent from /etc/init.d

Is there anything I can do to fix sendmail?
you have to specify the headers. the server will not accept an email without telling who  is that from.
```

tomail="To: toemail@domain.com"
frommail="From: fromemail@domain.com"
message="Subject: hello this is an email"

sendmail($tomail, $frommail, $message)


```

---

### Post by PierreRobiquet on 2011-08-07
But wouldn't I still be able to connect through telnet to the sendmail service? I surely should also be able to start it? I tried doing it through Mutt rather than using the command line and although it reports it succeeded after a long wait (I assume a time out) the logs show the same connection refused error.

---

### Post by SeijiSensei on 2011-08-07
It sounds to me like sendmail isn't running.  Usually telnetting to the server's port 25 is my first test for an operational SMTP server.  You might check by trying 

```
ps aux | grep sendmail | grep -v grep
```

and see if it reports an entry for the sendmail daemon.

If it does appear to be running, but you can't connect to localhost:25, I'd take a look at /etc/mail/sendmail.mc.  It should permit connections on 127.0.0.1 by default.  Also try "grep -i smtp /etc/mail/sendmail.cf" to make sure there's an entry to start the server on localhost:25.

---

### Post by PierreRobiquet on 2011-08-08
It appears that the sendmail daemon isn't running at all, I can't seem to start it through /etc/init.d/sendmail as it doesn't exist and service sendmail start seems to fail. Is there a way I can manually get the file to get created in /etc/init.d? It seems using apt doesn't fix it.

---

### Post by SeijiSensei on 2011-08-08
Try starting it with "sudo service sendmail start" and look at the results in /var/log/syslog and /var/log/mail.log.  Maybe that will give you some hints.

One of my major gripes about Ubuntu Server is that implementation of Upstart has been very inconsistent across server daemons.  What version are you running?  If you're not using 10.04LTS, I'd upgrade to that first before spending more time pulling your hair out.

---

### Post by PierreRobiquet on 2011-08-08
I can't find anything of significant interest unfortunately in the logs and it appears that the /var/log/mail.log file only contains the same error I've been getting:

```
Aug  8 06:35:05 Samsung-NC10 sendmail[5940]: My unqualified host name (Samsung-NC10) unknown; sleeping for retry
Aug  8 06:36:05 Samsung-NC10 sendmail[5940]: unable to qualify my own domain name (Samsung-NC10) -- using short name
Aug  8 06:36:05 Samsung-NC10 sendmail[5940]: p785a5Fr005940: from=root, size=695, class=0, nrcpts=1, msgid=<201108080536.p785a5Fr005940@Samsung-NC10>, relay=root@localhost
Aug  8 06:36:05 Samsung-NC10 sendmail[5940]: p785a5Fr005940: to=root, ctladdr=root (0/0), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30695, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: Connection refused by [127.0.0.1]
```

I am running Ubuntu Server 11.04 at the moment, I was late and didn't realise that 10.04 was the LTS version and for some reason assumed it was still 8.04. The only thing I've done since is a dist-upgrade from 10.10 to 11.04 since this isn't a production server, more of a hobby thing (and a Minecraft/Mumble server for friends :D ).

Although there is one thing I've done, I installed a new Ubuntu Server 11.04 install into a virtual machine on my computer and noticed that sendmail is present in /etc/init.d . I assume this means that for whatever reason it is missing on my system? Would it be safe just to SCP it over or do I need a specific version?

---

### Post by PierreRobiquet on 2011-08-08
Great news, I've managed to fix it. It seems that I did need the sendmail file in /etc/init.d and for whatever reason it was never added when I used apt-get install sendmail. Due to the fact I couldn't SSH into the VM without weird networking errors, I had to ftp it to another server then download the file and finally cp it into the /etc/init.d folder.

Then once I had started the service I received a ton of emails which were queued up from my testing. Although I have two problems with sendmail

[LIST=1]
[*]It takes a while to startup after I issue the command or power on the server, I assume this is because something is timing out but I'm not sure what. I can't seem to find logs that will tell me what it is doing either.
[*]I currently use DynDNS and have a domain through that, is it possible for me to setup sendmail to use that subdomain when sending so it actually comes from a valid address rather than my computers hostname? I don't really want to change the hostname just set up an alias.
[/LIST]
EDIT: I've fixed problem one as per described here [http://www.zyxware.com/articles/641/fixed-ubuntu-startup-slows-down-at-starting-mail-transport-agent-mta-sendmail](http://www.zyxware.com/articles/641/fixed-ubuntu-startup-slows-down-at-starting-mail-transport-agent-mta-sendmail)

---

### Post by PierreRobiquet on 2011-08-08
Does anyone have a solution to my second problem? At the current time it remains rather functional, however I have logs sent to my email address which are sometimes caught by Gmails spam filter. I assume this is because of the incorrect domain name and by using my DynDNS subdomain when a reverse lookup is performed my IP address will be seen and therefore allowed through the spam filter.

---

### Post by fdrake on 2011-08-08
> **ConcreteDonkey said:**
> Does anyone have a solution to my second problem? At the current time it remains rather functional, however I have logs sent to my email address which are sometimes caught by Gmails spam filter. I assume this is because of the incorrect domain name and by using my DynDNS subdomain when a reverse lookup is performed my IP address will be seen and therefore allowed through the spam filter.

this howto uses redhat but the commands works on ubuntu, since they are very similar for may setup that i used to relay sendmail to my gmail.

[http://test1.linux.org.hk/org/event/200111-cafe/mailsys/linuxcafe1.htm](http://test1.linux.org.hk/org/event/200111-cafe/mailsys/linuxcafe1.htm)

---

### Post by PierreRobiquet on 2011-08-08
For some strange reason when I issue the M4 command I get permission denied, even though the service is stopped and I'm using sudo

```
sudo m4 /etc/mail/sendmail.mc > /etc/sendmail.cf
bash: /etc/sendmail.cf: Permission denied

```

Any ideas what could be causing it?

EDIT: It seems that m4 isn't compatible with sudo and I had to run it under root.

It seems even after editing the local-host-names file it still prefers my ubuntu.localhost that I set in /etc/hosts to stop sendmail from timing out during boot. Does this mean that I can now remove the ubuntu.localhost from my /etc/hosts file?

---

