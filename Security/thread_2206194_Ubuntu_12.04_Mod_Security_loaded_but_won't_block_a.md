---
title: "Ubuntu 12.04 Mod Security loaded but won't block attacks"
date: 2014-02-17
forum: Security
---

### Post by kisonay on 2014-02-17
I'm very new to self managing a server and security. I have a 12.04 installation that I am fooling around with, with a goal of setting up a LAMP server.

I was doing great and got PHP 5.3, Apache 2.2, MySQL 5.5 all up an running but i'm at a total loss with getting mod_security working.


I installed mod_security with the following command.


```
apt-get install libapache2-modsecurity

```

and have confirmed it is loaded with the following (returns security2_module (shared))


```
apachectl -M | grep --color security

```

Also when I run the following it does list mod_security



```
/usr/share/modsecurity-crs$ sudo apachectl -t -D DUMP_MODULES

```

I copied the recommended config file to 


```
/etc/modsecurity/modsecurity.conf


```

Apache reloads without a problem and the audit log is present.


```
ls -l /var/log/apache2/modsec_audit.log
-rw-r----- 1 root root 0 Oct 19 08:08 /var/log/apache2/modsec_audit.log

```

I have modified the config file with the following


```
nano /etc/modsecurity/modsecurity.conf

```

```
SecRuleEngine On

```

And left everything else standard for now.


I then edited the apache mods enabled file


```
nano /etc/apache2/mods-enabled/mod-security.conf

```

```
Include "/usr/share/modsecurity-crs/*.conf"
Include "/usr/share/modsecurity-crs/activated_rules/*.conf"
Include "/usr/share/modsecurity-crs/base_rules/*.conf"

```

The first time I tried to restart apache I got an error due the the fact that /usr/share/modsecurity-crs/activated_rules/ didn't exist. I created it and restarted apache without a problem.


This confirms that mod_security is loading in my mind.


A list of the base rules are being loaded.


```
ls /usr/share/modsecurity-crs/base_rules/
modsecurity_35_bad_robots.data               modsecurity_crs_40_generic_attacks.conf
modsecurity_35_scanners.data                 modsecurity_crs_41_sql_injection_attacks.conf
modsecurity_40_generic_attacks.data          modsecurity_crs_41_xss_attacks.conf
modsecurity_41_sql_injection_attacks.data    modsecurity_crs_42_tight_security.conf
modsecurity_50_outbound.data                 modsecurity_crs_45_trojans.conf
modsecurity_50_outbound_malware.data         modsecurity_crs_47_common_exceptions.conf
modsecurity_crs_20_protocol_violations.conf  modsecurity_crs_48_local_exceptions.conf.example
modsecurity_crs_21_protocol_anomalies.conf   modsecurity_crs_49_inbound_blocking.conf
modsecurity_crs_23_request_limits.conf       modsecurity_crs_50_outbound.conf
modsecurity_crs_30_http_policy.conf          modsecurity_crs_59_outbound_blocking.conf
modsecurity_crs_35_bad_robots.conf           modsecurity_crs_60_correlation.conf

```

Now here is were I am totally stumped. No mater what I do I cannot get mod_sec to block attacks.


I setup a simple php file that queries a table for a username and password. When it gets a match it displays authorized otherwise it displays invalid. 


If I try posting the username as the following I get the authorized message when it should be blocked by the xss rules. (php script shown below.)


```
' or true --

```

I took a look at /var/log/apache2/modsec_audit.log and nothing gets added to the log file. It is like it isn't even installed.


Any guidance would be greatly appreciated.


```
<html>
<body>
<?php
    if(isset($_POST['login']))
    {
        $username = $_POST['username'];
        $password = $_POST['password'];
        $con = mysqli_connect('localhost','root','password','sample');
        $result = mysqli_query($con, "SELECT * FROM `users` WHERE username='$username' AND password='$password'");
        if(mysqli_num_rows($result) == 0)
            echo 'Invalid username or password';
        else
            echo '<h1>Logged in</h1><p>A Secret for you....</p>';
    }
    else
    {
?>
        <form action="" method="post">
            Username: <input type="text" name="username"/><br />
            Password: <input type="password" name="password"/><br />
            <input type="submit" name="login" value="Login"/>
        </form>
<?php
    }
?>
</body>
</html>
```

---

### Post by wale2 on 2014-05-20
I am exactly in the same fix. Have you found a solution to this pls?

---

### Post by kisonay on 2014-05-21
It turned out that the method I was using to test this was invalid. I tried a different exploit and it blocked it correctly.

---

