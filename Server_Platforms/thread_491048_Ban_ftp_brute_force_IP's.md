---
title: "Ban ftp brute force IP's"
date: 2007-07-03
forum: Server Platforms
---

### Post by jnusa on 2007-07-03
Hello

I'm having a problem with foreign IP's trying to bruteforce my FTP server (at least FTP, not really checked other services). I'm using ProFTPd and it seems that it does not offer a ban option when e.g. 5 or 10 login failures have occured.
Is there a ftp server which natively offers this option or is there any 3rd. part module which could be installed

Any information is greatly appreciated.

Regards jnusa

---

### Post by MJN on 2007-07-03
The popular Fail2Ban package will be of interest...
 
[http://www.fail2ban.org/](http://www.fail2ban.org/)
 
Mathew

---

### Post by jnusa on 2007-07-03
Hi MJN

I've tried the fail2ban utility (well it was installed anyway should work with ssh in theory) and played with it for about an hour now. It seems that it doesn't reg. the correct entries in auth.log. I've tried setting up proftpd as described in this tutorial [http://www.howtoforge.com/fail2ban_debian_etch](http://www.howtoforge.com/fail2ban_debian_etch).
I've tried to use the default regex's in filter.d and the one he overrides in the toturial, but they do not work. I've been monitoring auth.log and fail2ban.log while trying to hammer the ftp server with a known user and an unknown user. One of the problems that I've encountered is that auth.log groups log messages together e.g.

```

Jul  3 13:52:45 vito proftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=notforyoureyes.com  user=admin
Jul  3 13:53:32 vito last message repeated 3 times
Jul  3 13:54:29 vito last message repeated 2 times
Jul  3 13:55:31 vito last message repeated 4 times
Jul  3 13:56:29 vito last message repeated 3 times

```

Another problem is that different types messages occur in the auth.log depending on the type of attack. If the brute force utility finds a user that exists (probably wont happen since I don't use regular usernames) and tries to guess the password. Most common attack is to bruteforce 'admin', 'adm', 'admam' etc which doesn't exist (really badly written brute force utility!!). Each of these scenarios add a different log message in auth.log 



Every time i alter the conf files, I restart the fail2ban server. I'm using Ubuntu 7.04 with most updates. Proftpd is installed via apt-get and should be pretty much stock. Any advice?

---

### Post by MJN on 2007-07-03
I don't run an FTP server myself so can't comment on the correct expressions to be matching for - perhaps a search of the archives, and someone else, can assist there.
 
Regarding the varying message types (invalid username, wrong password etc) that shouldn't be a problem as they should all be covered by the multiple regex's. I have in the past also worried about the 'last message repeated n times' issue however in practice have not found it to be a problem. Given this I never investigated further the consequences and/or how it might be being handled.
 
Mathew
 
[Edit: Looks like the syslog compresson is an issue afterall - see [http://wiki.nerdylorrin.net/wiki/Wiki.jsp?page=Fail2Ban](http://wiki.nerdylorrin.net/wiki/Wiki.jsp?page=Fail2Ban). Perhaps the reason I've not noticed a problem is because the 'attacker' isn't sticking with the same attack i.e. a single username and variety of passwords - them changing username would change the log entry, disallow repeated compression, and hence get 'caught'. Either way, it's proving extremely effective]

---

