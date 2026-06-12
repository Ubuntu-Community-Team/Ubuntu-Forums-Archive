---
title: "Regex for fail2ban &amp; proftpd"
date: 2007-06-28
forum: Server Platforms
---

### Post by Rich99 on 2007-06-28
I'm using fail2ban under 6.06 LTS, and wanted to check whether I'm doing this right.  Here's the relevent section of fail2ban.conf:

[proftpd]
enabled = true
#port = ftp,ftp-data,ftps,ftps-data
port = ftp
logfile = /var/log/proftpd/proftpd.log
timeregex = \S{3}\s{1,2}\d{1,2} \d{2}:\d{2}:\d{2}
timepattern = %%b %%d %%H:%%M:%%S
failregex = USER \S+: no such user found from \S* ?\[<HOST>\] to \S+\s*$

My lines in /var/log/proftpd/proftpd.log look like this for a failed login:
Jun 28 18:17:51 rich-server proftpd[643] rich-server (rich.xxx.xxx.com[::ffff:193.6.x.x]): USER dave: no such user found from rich.xxx.xxx.com [::ffff:193.6.x.x] to ::ffff:193.6.x.x:21

Now I got the above regex from the fail2ban site, and the 'time' patterns & regexes from the ssh example in the config file.  However my failed log lines are slightly different to the ones given in fail2bans example.  Thus I suspect the regex won't match.  However I don't really understand regex's!! I  know there is a fail2ban regex testing tool but I don't seem to have it installed, and can't find it in the 6.06 repositories.  I assume it's only in the newer fail2bans as in feisty.  Can anyone help me sort out the regex's based on the above line?

---

### Post by Fireal on 2008-05-07
The testing tool is fail2ban-regex.  Try
```
sudo fail2ban-regex /var/log/proftpd/proftpd.log /etc/fail2ban/filter.d/proftpd.conf
```

the expression is ```
fail2ban-regex name_of_logfile file_with_regex_in_it
```

the post located [here]("http://ubuntuforums.org/showthread.php?t=475595&highlight=fail2ban-regex") elborates
Summary:
> yup, failregex is the test line - there's a "rexex testing utility" included with fail2ban:
Code:

fail2ban-regex "line" "failregex"

will test a single regular expression "failregex" (such as given in sshd.conf) with a single "line" of your logfile. Don't forget the double quotes around your line and failregex definitions.

fail2ban-regex accepts files too. Thus, it is easier to test and debug your own regular expressions:
Code:

 
# fail2ban-regex /var/log/auth.log /etc/fail2ban/filter.d/sshd.conf

Or you can use a combination of both:
Code:

# fail2ban-regex /var/log/auth.log "Failed [-/\w]+ for .* from <HOST>"



also make sure the /etc/fail2ban/filter.d/proftpd.conf file has the following in it. ```
failregex = \(\S+\[<HOST>\]\)[: -]+ USER \S+: no such user found from \S+ \[[0-9.]+\] to \S+:\S+$
            \(\S+\[<HOST>\]\)[: -]+ USER \S+ \(Login failed\): Incorrect password\.$
            \(\S+\[<HOST>\]\)[: -]+ SECURITY VIOLATION: \S+ login attempted\.$
            \(\S+\[<HOST>\]\)[: -]+ Maximum login attempts \(\d+\) exceeded$
            USER \S+: no such user found from \S* ?\[<HOST>\] to \S+\s*$

```

The fifth line I inserted because ever since going to 8.04-Hardy the first is not being recognized as a failure.

---

