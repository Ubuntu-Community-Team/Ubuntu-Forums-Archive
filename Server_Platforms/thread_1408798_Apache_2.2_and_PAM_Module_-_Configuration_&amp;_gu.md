---
title: "Apache 2.2 and PAM Module - Configuration &amp; guidance needed.."
date: 2010-02-16
forum: Server Platforms
---

### Post by tomehb on 2010-02-16
Hi Guys,

Just setup an Apache2 server, and I would like to setup a login. I also wanted to use the same method that is setup for vsftpd....

For vsftpd  I've created a mysql database.... structured as:

```


mysql> use vsftpd
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> describe accounts;
+----------+-------------+------+-----+---------+----------------+
| Field    | Type        | Null | Key | Default | Extra          |
+----------+-------------+------+-----+---------+----------------+
| id       | int(11)     | NO   | PRI | NULL    | auto_increment |
| username | varchar(30) | NO   | UNI | NULL    |                |
| pass     | varchar(50) | NO   |     | NULL    |                |
+----------+-------------+------+-----+---------+----------------+
3 rows in set (0.00 sec)


```

So not really sure what I was doing I proceeded to attempt to get this to work with Apache 2.2.......



My apache config is the following:
```

        # Website Dir
        <Directory /var/wwws/>

                #Server Auth
                AuthType Digest
                AuthName "Authentication Required"
                AuthPAM_Enabled on
                AuthPAM_FallThrough Off
                AuthBasicAuthoritative off
                Require valid-user

                Options -ExecCGI -FollowSymLinks -Indexes
                AllowOverride None
                Order allow,deny
                Allow from all
        </Directory>

```



my /etc/pam.d/apache2 configuration:
```

auth required pam_mysql.so user=vsftpd passwd=**** host=localhost db=vsftpd table=accounts usercolumn=username passwdcolumn=pass crypt=2

account required pam_mysql.so user=vsftpd passwd=**** host=localhost db=vsftpd table=accounts usercolumn=username passwdcolumn=pass crypt=2
```


However I get the following error found in /var/log/error.log:

```
[Wed Feb 17 01:54:02 2010] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.10 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g configured -- resuming normal operations
[Wed Feb 17 01:54:08 2010] [crit] [client 81.23.57.*] configuration error:  couldn't check user.  No user file?: /
[Wed Feb 17 01:54:09 2010] [crit] [client 81.23.57.*] configuration error:  couldn't check user.  No user file?: /favicon.ico
```

and when you navigate to the site: [www.tomehb.co.uk](www.tomehb.co.uk) (click secure & ignore SSL Cert to bypass error or download the certs lol!) you get....

Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.




[B]Q1) Is it possible?
Q2) Any Guidance on what I need to read?
Q3) Is This Just a Stupid Me[/B]thod?

---

