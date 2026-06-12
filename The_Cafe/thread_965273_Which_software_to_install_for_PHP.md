---
title: "Which software to install for PHP"
date: 2008-10-31
forum: The Cafe
---

### Post by Silvernail on 2008-10-31
I have upgraded to ubuntu n8.04 with all the updates offered.

On a previous unnamed Linux system I had some bash script files that ran on PHP-4.

On my new installation, when I run the following code:
```

#!/bin/bash
## jasp Linspire users support group.

main()
{
cat pdlist12 | ( \
     while read admin; \
     do check_link $admin; done \
     )

}

PHP_EXEC='php -r'

check_link()
{
    member_email=$1

##line 19    
    php -f mailsender.php "$member_email" "two"  
}

```

I use to get this error:
> 
./send.sh: line 19: php: command not found

Investigation found I did not have any 'php' installed so I installed Apache2 as that was the only comments I could find in the forums concerning 'php'.

Now I get this error:

> 
./send.sh: line 19: php: command not found
dave@gadabout:~/tffrobot$ ICE default IO error handler doing an exit(), pid = 8586, errno = 11


So I tried this;
> 
dave@gadabout:~/tffrobot$ sudo apt-get install php
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package php is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package php has no installation candidate

dave@gadabout:~/tffrobot$ sudo apt-get install php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
php5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dave@gadabout:~/tffrobot$ 


If I change the 'php' in both instances to 'php5' I still get the command not found error.

Is there a HOWTO for me to read? Do I need to rewrite my code?
Can anyone help?

TIA
Dave

---

### Post by Silvernail on 2008-10-31
Consider this solver.

I did this:
```

dave@gadabout:~$ php5 --version
The program 'php5' is currently not installed.  You can install it by typing:
sudo apt-get install php5-cli
bash: php5: command not found
dave@gadabout:~$ 

```

So I did it and can now do this:
```

dave@gadabout:~$ php5 --version
PHP 5.2.4-2ubuntu5.3 with Suhosin-Patch 0.9.6.2 (cli) (built: Jul 23 2008 06:44:49) 
Copyright (c) 1997-2007 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2007 Zend Technologies


dave@gadabout:~$ php --version
PHP 5.2.4-2ubuntu5.3 with Suhosin-Patch 0.9.6.2 (cli) (built: Jul 23 2008 06:44:49) 
Copyright (c) 1997-2007 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2007 Zend Technologies
dave@gadabout:~$ 

```

Everything works as it should.

Dave

---

