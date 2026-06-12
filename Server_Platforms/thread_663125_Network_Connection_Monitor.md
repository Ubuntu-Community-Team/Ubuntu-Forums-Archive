---
title: "Network Connection Monitor"
date: 2008-01-09
forum: Server Platforms
---

### Post by MasterXandrex on 2008-01-09
I am looking for either a developed opensource software or a little help in writing a script to run as a cron job. 

I have three servers at three separate locations and I need to monitor their network status (I would like in ten minute intervals). I have considered placing a dummy file on the server and performing an sftp transfer or wget pull and on error sending an e-mail, however, I don't know how to script this.

Any help would be appreciated.

Thanks,

Xan

---

### Post by k_grdn on 2008-01-10
Hi,

Have you considered nessus:

[http://nessus.org/]("http://nessus.org/")

Regards,

k_grdn

---

### Post by MasterXandrex on 2008-01-10
Excuse me if I've misread this, however, Nessus appears to be a software/netowork vulnerability scanner, not a network and or software monitor. The network and software monitor that this company offer is called PVS and is $10K and thus won't work for me.

Am I reading the descriptions right?

Any other options out there all?

Thanks,

Xan

---

### Post by k_grdn on 2008-01-10
Hi,

> network status (I would like in ten minute intervals)

Nessus can do this by issuing pings also dns checks, service status and lots more, maybe I got the wrong idea.

Check out cacti, ntop or possibly IPAudit, the webs your oyster, googles your perl!

k_grdn

---

### Post by koenn on 2008-01-10
you could just ping, and use (command line) mail to report back. 
You'd need to install and configure the 'mailx' package first. 
Then, maybe something like

```

ping -c 4 server
case $? in
  0) # connection OK
      ;;
  1) # packet loss
      echo "packet loss while pinging server" | mail you@hotmail.com 
      ;;
  2) # no replies
      echo "connection to server is down" | mail you@hotmail.com
      ;;
esac


```

or, using your download idea : 
```

cd tmp
wget http://server/file
[[ -e /tmp/file ]]  ||  echo "failed to download file from server" | mail ...
rm /tmp/file
cd -

```

when you run this via a cron job (for +/- continouos checking), you may not need the mail command, as cron will attempt to mail the output to the system administrator. You can set this up with a real email address but it requires a mail server (MTA) on the computer where the cron jobs run. 

These are just some ideas, they probably need some work

---

