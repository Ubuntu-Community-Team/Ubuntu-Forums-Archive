---
title: "Postfix, Dovecot, Squirrelmail, NFS symlink and connection drop."
date: 2011-10-30
forum: Server Platforms
---

### Post by systemrooterrr on 2011-10-30
Hi everyone! I'm a little new to Ubuntu so hopefully you can help me out. I've been working with Ubuntu Server 10.10 over the last week or so setting up an email server for our office. I followed a couple different [perfect server setups] but a lot of them are out dated or too technical for me at this point.

What I wound up with is fairly simple. Postfix, Dovecot, and finally Squirrelmail splotched on top of an apache2 server.

Now that was fine, though it still doesn't receive emails. I'm going to look at that later though.

What I have is two seperate servers. We already have an Unbuntu 10.10 server set up to host our website. They arent very powerful, so what I wanted was for this server to only handle our email, and perhaps extend it at some later point to multiple domains.

I thought this would be the simplest way to do it. our webserver hosts littletechboy.com So I mapped /var/www/mail (the symlinked location on the mail server) accross to /var/www/webmail on the webserver. Now is the weird part I want help with. If I'm on the local subnet, connecting to the mailserver directly at it's ip /mail shows and logs into squirrlmail fine and works. Connecting however to littletechboy.com/webmail displays squirrelmail, but when I attempt to log on it just says 

"Error connecting to IMAP server: localhost.
111 : Connection refused". 

Where do I start looking for problems? Squirrelmail doesn't provide documentation for a setup like this...

My suspicion is that it's looking for an IMAP server on the webserver as it's pointed to localhost. Do I only have to change it to the other server's static ip?


Sorry for the long post, just trying to be thorough. Thanks for any help you can provide.

<edit> Sorry if this is the wrong place, let me know if it needs to be moved. </edit>

---

### Post by kustomjs on 2011-10-30
Are you using mysql by any chance? Because I have a email server running IMAP,Dovecot,Postfix/Mysql but I am also using iredmail also.

for my webmail I am using roundcube and squirrelmail.

Also when I went to littletechboy.com/webmail I am getting 404 not found.

Because with my squirrelmail I have it set as localhost:143.

If you have a firewall make sure you open ports 143,110,25,587

for squirrelmail check this out: [https://help.ubuntu.com/community/Squirrelmail](https://help.ubuntu.com/community/Squirrelmail)

---

### Post by SeijiSensei on 2011-10-30
You can put SquirrelMail on a different machine and have it act as an IMAP client, but you have to set up SM differently.

Don't bother with a symlink.  Just run the conf.pl script and set the IMAP (and probably the SMTP) server to point to the actual mail server.  

NFS mounts of mail spools are generally a bad idea because of file-locking issues. Using SM as an IMAP client avoids these problems since the file locks will be managed by dovecot on the mail server.

---

### Post by systemrooterrr on 2011-10-30
> **kustomjs said:**
> Are you using mysql by any chance? Because I have a email server running IMAP,Dovecot,Postfix/Mysql but I am also using iredmail also.

for my webmail I am using roundcube and squirrelmail.

Also when I went to littletechboy.com/webmail I am getting 404 not found.

Because with my squirrelmail I have it set as localhost:143.

If you have a firewall make sure you open ports 143,110,25,587

for squirrelmail check this out: [https://help.ubuntu.com/community/Squirrelmail](https://help.ubuntu.com/community/Squirrelmail)

Sorry, I must have been thinking of the last setup I had going. It is littletechboy.com/wmail The firewall is setup to allow 110, 25, 143 to the mail server's internal ip. It then allows port 80 to the internal ip of the webserver. I believe port 587 is closed though.

MySQL is installed, but the mailserver is not configured with virtual hosts from mysql databases (to my knowlege) that was in one of the guides I followed, but after going through, I believe there was some issue with postfix and the security certs. It was listening on port 25 but I could not telnet into postfix. So I did a stock install of Ubuntu server, and just used postfix's defaults and Dovecot's defaults.

Thanks for the link, I used it the first time I tried to get this all set up, I'll read through it again now that I know some more it might make more sense!

<Edit> I'll open port 587 on Monday when I'm in the office again, that seems to be a fairly important one! </edit>

---

### Post by systemrooterrr on 2011-10-30
> **SeijiSensei said:**
> You can put SquirrelMail on a different machine and have it act as an IMAP client, but you have to set up SM differently.

Don't bother with a symlink.  Just run the conf.pl script and set the IMAP (and probably the SMTP) server to point to the actual mail server.  

NFS mounts of mail spools are generally a bad idea because of file-locking issues. Using SM as an IMAP client avoids these problems since the file locks will be managed by dovecot on the mail server.

I had to read that 5 times to understand it (yes, I feel dumb). That makes way more sense! I'll set that up on Monday as well! Thanks!

---

### Post by systemrooterrr on 2011-10-31
Ok, so I've opened the ports as recommended. I've installed squirrelmail on top of the webserver as you suggested and removed the mounted version. [http://littletechboy.com/webmail/squirrelmail](http://littletechboy.com/webmail/squirrelmail) I can log in fine and everything seems to be working. Now I want to get a bit more indepth with TLS and authentication as I want it more secure and for postfix not to deny me relay access as I'm not on the same network. 

Does anyone have a guide or link to one that covers this? Something that's beginner friendly would be great! I'll keep poking around and thanks for the help guys!

---

