---
title: "Apache won't start after upgrade to 11.10 (Redmine dependancy issue?)"
date: 2011-10-17
forum: Server Platforms
---

### Post by Jarige on 2011-10-17
I discovered that after upgrading to 11.10 Apache won't start. Whenever I start it this happens:

```

user@computer:~$ sudo service apache2 start
 * Starting web server apache2                                                                    Syntax error on line 2 of /etc/apache2/httpd.conf:
Can't locate Digest/SHA1.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl . /etc/apache2) at /usr/lib/perl5/Apache/Redmine.pm line 102.\nBEGIN failed--compilation aborted at /usr/lib/perl5/Apache/Redmine.pm line 102.\nCompilation failed in require at (eval 2) line 2.\n
Action 'start' failed.
The Apache error log may have more information.

```

This Apache error log (if located at /var/log/apache2/error.log) is empty.

This is my httpd.conf:

```

# /svn location for users
   PerlLoadModule Apache::Redmine
   <Location /svn>
     DAV svn
     SVNParentPath "/var/svn" 
     Order deny,allow
     Deny from all
     Satisfy any

     PerlAccessHandler Apache::Authn::Redmine::access_handler
     PerlAuthenHandler Apache::Authn::Redmine::authen_handler
     AuthType Basic
     AuthName "Redmine SVN Repository" 

     #read-only access    
     <Limit GET PROPFIND OPTIONS REPORT>
        Require valid-user
        Allow from 127.0.0.1
        # Allow from another-ip
         Satisfy any
     </Limit>
     # write access
     <LimitExcept GET PROPFIND OPTIONS REPORT>
       Require valid-user
     </LimitExcept>

     ## for mysql
     RedmineDSN "DBI:mysql:database=redmine_default;host=127.0.0.1" 
     ## for postgres
     # RedmineDSN "DBI:Pg:dbname=databasename;host=my.db.server" 
     ## for SQLite3
     # RedmineDSN "DBI:SQLite:dbname=database.db" 

     RedmineDbUser "redmine" 
     RedmineDbPass "pass" 
  </Location>

```

I'm using these versions of Redmine, Ruby, Rails and Perl:
Redmine 1.1.3-4 (which I manually tried upgrading to 1.2.1)
Ruby 4.8
Rails 2.3.14.1
Perl 5.12.4-4

What can I do to fix this? I've got svn repo's running on this machine which are currently not accessible due to Apache failing to start. Yes, I know I should be careful when updating Ubuntu and I will next time.

Is there anyone that can help me?

---

### Post by Jarige on 2011-10-17
Solved! :D Some guy on the Redmine IRC helped me :D
```
sudo perl -MCPAN -e'install Digest::SHA1'
```

---

### Post by JamesAng on 2011-10-20
Hi,

I'm also running Redmine 1.2.1 on Apache2+Passenger+SVN/HTTP authentication on Ubuntu 11.04 x64

May I know if the upgrade to 11.10 is smooth and did it broke any of Redmine operation?

Thanks.

James.

---

### Post by Jarige on 2011-10-21
Well it didn't work immediately after upgrading since Apache wouldn't even start, but after exedcuting the code in my second post it worked. I only use SVN as extra 'feature' of Redmine, so I don't know whether more things will go wrong after upgrading.
I can not guarantee you that the upgrade will succeed without problems. I can only tell you my upgrade failed but was fixed easily.

---

