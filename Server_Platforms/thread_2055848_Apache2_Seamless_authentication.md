---
title: "Apache2 Seamless authentication"
date: 2012-09-10
forum: Server Platforms
---

### Post by scarrez on 2012-09-10
Hi,

I have setup in a testing environment an IIS7 machine which collects the domain/user when connecting to a website using PHP from the: 

$_SERVER['AUTH_USER'];

resulting in

DOMAIN\username

now I want to do this with Apache 2 on Ubuntu which is needed for my live system, I do not need any LDAP authentication, I just need to acquire the domain/user which I can can use in an IF statement.

Any help is much appreciated

Thanks,
Scarrez

---

### Post by scarrez on 2012-09-10
**Update**

I have managed to get 90% of it working with a small bug.
I am using this, [http://gnomeskull.com/?p=162]("http://gnomeskull.com/?p=162")
Auth NTLM, which works and I believe is setup correctly but I am getting this error in the Apache log...

Bad/Missing NTLM/Basic Authorization Header for /index.php

it pops up asking for username/password in IE but upon entering the details I get another error...

Wrong password/user (rc=3/1/327681): DOMAIN_censor\\USERNAME_censor for /index.php

---

### Post by SeijiSensei on 2012-09-10
Read this: [http://httpd.apache.org/docs/2.2/howto/auth.html](http://httpd.apache.org/docs/2.2/howto/auth.html)

You want to use "Basic Authentication" like this:

```

<VirtualHost *:80>
   ServerName  www.example.com
   DocumentRoot /path/to/website/root

   <Directory "/path/to/website/root">
       AuthUserFile /path/to/some/file
       AuthGroupFile /dev/null
       AuthName "Please enter your username and password"
       AuthType Basic

       <Limit GET>
          require valid-user
       </Limit>
   </Directory>

   [other stuff]

</VirtualHost>

```

The password file ("AuthUserFile") can be anywhere as long as the "www-data" user that apache runs as can read it.  You manage the file with the htpasswd utility that comes with the Apache server.  

The user will be prompted to enter the username by the browser and it will be available as $_SERVER['AUTH_USER'].

The Apache Organization's servers won't respond for me at the moment.  I presume this is a transient problem.

It's possible to [achieve the same result using PHP itself]("http://php.net/manual/en/features.http-auth.php"), but I find the approach above much easier to implement.

---

### Post by scarrez on 2012-09-11
Hi,

Sorry to be a pain but to clarify what I wanted was for the username/domain to be passed through IE (Intranet) automatically without the end user having to type anything in, Unless I misunderstood your post the end user would have too enter there details again which is not the aim here unfortunately.

Thanks for your post though!

Scarrez

---

### Post by SeijiSensei on 2012-09-11
I would imagine that only happens if IE somehow passes the users Windows credential in the background. 

I suggest you create a file called info.php in the /var/www directory.  (You'll need to be root for this with sudo.)  In that file put just the line:

```
<?php phpinfo() ?>
```

Then access the file as [http://localhost/info.php](http://localhost/info.php).  PHP will then display everything it knows about.  If you search the page for your Windows username, does it appear anywhere there at all?  If not, I'm guessing this invisible credential-passing behavior is proprietary to IE+IIS.  How, for instance, would this work if people used Firefox instead of IE on Windows networks?

If you end up having to request the person's username and credentials there are a couple of alternatives you can use to authenticate them.  One is to use the LDAP functions to query Active Directory.  Another approach is to authenticate them by using their credentials to log into Exchange.  I use this approach on a site where we once had a Unix mail server and wanted to use it as the authentication host.  I wrote a script that uses the PHP IMAP functions to see if a valid mail account existed with that username and password.  When the client switched to Exchange, I modified the script to use that instead.

---

### Post by scarrez on 2012-09-12
Hi,

Thanks for your reply.

This is a IIS+IE specific thing but I have done some research and many people have got this working with linux/apache2 with certain module addons which is what I am trying to do.
It only works with IE, FireFox/Chrome would need you to enter the credentials but IE would be automatic which is fine, the location I'm in only uses IE so not an issue.

I am certain this can be done as many people have reported it so but all methods I try seem to fail which is why I have resulted in posting here in the hope someone might be able to answer it.

**EDIT**

Yes I have entered the <?php phpinfo(); ?> and no username/domain appears, the SERVER variables which should be filled with the data don't even appear.
I don't need to authenticate any of the users, I only need the username/domain which I plan to output to the website using an "echo".

Thanks
Scarrez

---

