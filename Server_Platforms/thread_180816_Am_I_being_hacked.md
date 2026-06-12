---
title: "Am I being hacked?"
date: 2006-05-23
forum: Server Platforms
---

### Post by iridgedati on 2006-05-23
Sorry all of this is something I should know already... I am at beginning of the Linux journey.
So, I have port 8080 open on my router/firewall. No other ports are open. I've been keeping an eye on my apache2 access.log file. The following entries started to show up in it a couple of days ago:

124.8.2.142 - - [23/May/2006:00:46:33 -0400] "CONNECT 67.28.113.73:25 HTTP/1.0" 403 361 "-" "-"
124.8.2.142 - - [23/May/2006:01:02:50 -0400] "CONNECT 4.79.181.136:25 HTTP/1.0" 403 361 "-" "-"
124.8.2.142 - - [23/May/2006:01:02:59 -0400] "CONNECT 4.79.181.15:25 HTTP/1.0" 403 360 "-" "-"
124.8.2.142 - - [23/May/2006:01:04:31 -0400] "CONNECT 66.218.86.254:25 HTTP/1.0" 403 362 "-" "-"

Here is what i found  in apache2's error.log:

[Tue May 23 00:46:33 2006] [error] [client 124.8.2.142] client denied by server configuration: /var/www/
[Tue May 23 01:02:50 2006] [error] [client 124.8.2.142] client denied by server configuration: /var/www/
[Tue May 23 01:02:59 2006] [error] [client 124.8.2.142] client denied by server configuration: /var/www/
[Tue May 23 01:04:31 2006] [error] [client 124.8.2.142] client denied by server configuration: /var/www/

And this is in the server's auth.log.

May 23 00:39:01 localhost CRON[17668]: (pam_unix) session opened for user root by (uid=0)
May 23 00:39:01 localhost CRON[17670]: (pam_unix) session opened for user root by (uid=0)
May 23 00:39:01 localhost CRON[17670]: (pam_unix) session closed for user root
May 23 00:39:01 localhost CRON[17668]: (pam_unix) session closed for user root

Am I being hacked? I sense HTTP Tunneling here. What should I do? 
Thanks for your help in advance...

---

### Post by Glut on 2006-05-23
First part: CONNECT is a used for proxying or tunnelling, but unless you have it setup the attempts should fail. I wouldn't worry about it if you are sure of your configuration
Second: an attempt to load the directory, blocked by your configuration. 
These first two hint at an attempt to break in. I'd be more surprised if you didn't get your logs filled with this type of stuff. 
I don't think that you're being hacked, But there are no guarentees.

Third:
The CRON entries are fine, CRON runs as root so it can perform its tasks. Your logs should be full of this also.

---

### Post by iridgedati on 2006-05-23
That's cool. I set up apache2 to allow only GET and POST. 
This is a snippet from my sites-enabled/default file:

<Directory /var/www/>
	Options Indexes FollowSymLinks MultiViews
	AllowOverride None
	Order deny,allow
	Deny from all
	# This directive allows us to have apache2's default start page
        # in /apache2-default/, but still have / go to the right place
        # Commented out for Ubuntu		
	RedirectMatch ^/$ /apache2-default/
	<Limit POST GET>
	</Limit>		
</Directory>

I blocked the HTTP CONNECT with the Limit tag. Is that enough to block HTTP Tunneling?

How can I check for suspicious activity on the machine? What log files should I look at? Can you guys post me links that I could read?
I found this one last night and seemed to be pretty good:
[http://www.debian.org/doc/user-manuals#securing](http://www.debian.org/doc/user-manuals#securing)

---

### Post by Ride Jib on 2006-05-28
..

---

