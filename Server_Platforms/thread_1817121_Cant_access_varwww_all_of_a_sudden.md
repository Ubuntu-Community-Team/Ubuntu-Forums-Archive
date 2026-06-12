---
title: "Cant access /var/www all of a sudden"
date: 2011-08-02
forum: Server Platforms
---

### Post by SquALeD on 2011-08-02
Hi people, 

I've had my Ubuntu 10.04 server running fine for ages now on my home network. It was serving a Joomla website from /var/www for a while with no problems. I had added a user relo and changed permissions of /var/www by using this method which worked: 

[I]sudo adduser relo www-data
sudo chown root.www-data /var/www
sudo chmod g+ws /var/www[/I]

All was fine for ages, could access /var/www no problems using Filezilla on the relo user account and add/delete stuff.

Then today I tried to access /var/www but all I got back from Filezilla was "connection refused"

The server is working fine, no updates for ages apart from security ones. My FTP server using vsftpd works fine and I can SSH into /var/www and add/delete stuff with no probs using the CLI.

I've changed nothing on the server at all! The only thing on my network that has changed is that I've replaced my router and the fixed IP for the server is now 192.168.1.13 instead of the original 192.168.0.81. Got a feeling that this might be involved but no too sure where to look?

 Im sure its something simple but its been so long since I had to do any tinkering with the webserver that I think I might  have missed something obvious!

Any ideas or pointers would be great

Cheers!

---

### Post by Wim Sturkenboom on 2011-08-03
firewall rules? router config not forwarding correctly?

Do yopu have the option to (temporarily) change it back to 192.168.1.13?

PS this is not 'all of a sudden', this is after you changed something

---

### Post by Lars Noodén on 2011-08-03
A note on www-data:

The group www-data is there to provide privilege separation for  the web server.  If you grant write access to either the user or the group www-data, then you are granting write access to the web server and open up great potential for trouble from visitors.  

Best would be to create a new group, say 'webmasters', and use that instead.

This is a common problem, I wish it were addressed in a FAQ or in the documentation.

---

### Post by SquALeD on 2011-08-04
Wim I understand its because I changed something its just that everything else is fine, just the ftp to the server. You understand that this server is on a home lan yes? I'm trying to ftp from within the lan, sorry if I didn't make that clear.

Lars Im having much better results and realise I only need to using terminal/ssh to move files to /var/www on the server. Maybe this is a better/safer way? If so what would the best way to revert the www-data group back to safe permissions?

Like I said before, all this is done from within my home lan - sorry if it wasn't clear in the op

Thanks both for your replies

---

### Post by WhiteHorse on 2011-08-04
try this:
man chown
If that doesn't work, try this:
man apache2
If you still can't get it, try this:
finger self

---

### Post by Lars Noodén on 2011-08-04
> **SquALeD said:**
> Lars Im having much better results and realise I only need to using terminal/ssh to move files to /var/www on the server.  


Awesome.  

> **SquALeD said:**
> Maybe this is a better/safer way? If so what would the best way to revert the www-data group back to safe permissions?


Yes, it is.  

Here is one way to revert back.  The default group for /var/www is **root**.

```

sudo chgrp -R root /var/www

[s]sudo find /var/www -type d -exec chmod g=rx [/s]

[s]sudo find /var/www -type f -exec chmod g=r  [/s]

```

For details, see

chmod(1)
[http://linux.die.net/man/1/chmod](http://linux.die.net/man/1/chmod)

find(1)
[http://linux.die.net/man/1/find](http://linux.die.net/man/1/find)

---

### Post by SquALeD on 2011-08-05
Thanks guys for the replies,

Gonna be using ssh from now on, no more ftp.

---

### Post by SquALeD on 2011-08-06
> **Lars Noodén said:**
> Awesome.  



Yes, it is.  

Here is one way to revert back.  The default group for /var/www is **root**.

```

sudo chgrp -R root /var/www

sudo find /var/www -type d -exec chmod g=rx 

sudo find /var/www -type f -exec chmod g=r  

```For details, see

chmod(1)
[http://linux.die.net/man/1/chmod](http://linux.die.net/man/1/chmod)

find(1)
[http://linux.die.net/man/1/find](http://linux.die.net/man/1/find)

Hi mate, Im trying to use the code you supplied but the last 2 lines are throwing this error:

*find: missing argument to `-exec'*

Anu ideas what could be causing this?

Cheers

---

### Post by Lars Noodén on 2011-08-06
> **SquALeD said:**
> Hi mate, Im trying to use the code you supplied but the last 2 lines are throwing this error:

*find: missing argument to `-exec'*

Anu ideas what could be causing this?

Cheers

My mistake.

```

sudo find /var/www -type d -exec chmod g=rx **{} \;**

sudo find /var/www -type f -exec chmod g=r **{} \;**

```

---

### Post by SquALeD on 2011-08-10
Thanks mate ill give it a go

---

