---
title: "server name not recognized...HELP"
date: 2008-04-11
forum: Server Platforms
---

### Post by jaredg32 on 2008-04-11
I set up mail server using postfix, dovecot, mysql and squirrelmail.
Much to my surprise everything is working just fine.  EXCEPT...whenever I have to reference my server, I have to use the IP address instead of my server name "server.bankfdic.com".  Nothing works when I use the server name.  

For instance:  When I set up to send/receive emails with Thunderbird, my outgoing and incoming servers had to be set to my server's local IP address to get it to work.  Putting in my server name won't work.

I'm guessing it has something to do with my /etc/hosts file, but I really  have no idea.  I'm a noob!

my hosts file looks like this.....
> 127.0.0.1    localhost.localdomain     localhost     server
192.168.2.10     server.bankfdic.com     server


Can anyone help me?
Please.
Thanks!

---

### Post by Koybe on 2008-04-12
You could check your hostname file : /etc/hostname
I woudl have this :
/etc/hosts :```
127.0.0.1    localhost.localdomain     localhost
192.168.2.10     server.bankfdic.com     server                      
```/etc/hostname : ```
server
```Restart your network conf : ```
sudo /etc/init.d/networking restart
```Then you could check with ```
hostname
hostname -f
```**But this is just local resolution**. If you want a network name resolution you need to install a DNS server such as Bind.

---

### Post by jaredg32 on 2008-04-12
Thanks Koybe.  It seems to be working!  I will install BIND and see if I can get that working.

---

### Post by dbrine on 2008-04-12
I ran the hostname and hostname -f and the results were different. The hostname returned the correct host name but -f didn't? How do I fix this?

---

### Post by andguent on 2008-04-13
What should have happened is that 'hostname' should have given you the short version, and 'hostname -f' should have given you the full version with .bankfdic.com on the end.

On my own server I just did a few grep commands to track files down. I find that the best way to see what settings are where is with a good combination of find, grep, and xargs.

EX:
grep myhostname /etc/*  --- This command searches for 'myhostname' in any text file directly in the /etc directory.

find /etc | xargs grep eth0 -- This command shows any line in any /etc file that contains 'eth0'.

grep -r myhostname /etc -- Same results as above basically, always a different way to do the same thing.

By using commands similar to these, I just now accidentally stumbled onto /etc/mailname and 'man mailname'. Hopefully this may be what you are looking for.

---

