---
title: "Cannot get &quot;from&quot; key limits working for SSH authorized_keys"
date: 2017-05-24
forum: Security
---

### Post by devan1002 on 2017-05-24
I noticed that multiple various IP addresses were trying to log into my SSH port.  In order to harden my connections I want to limit the keys to only certain domains.  I have used the "from=" notion in my authorized keys file and it only works if I use the actual IP address of the remote computer.  Those addresses are dynamic and are updated to the appropriate DNS.

If I substitute the IP address for the domain or domain wildcard, the public key is denied.

Here is a snippet of my authorized key file:

from="*.example.com" ssh-rsa AAAA

Here is the output from auth.log

May 24 11:43:28 server1 sshd[2131]: Authentication tried for *** with correct key but not from a permitted host (host=XXX.XX.XXX.XXX, ip=XXX.XX.XXX.XXX).

The host and the ip numbers are the same, just obscured.

I tried adding the domain and ip address to /etc/hosts but that also didn't work.

Thanks for any insight,

Devan

---

### Post by TheFu on 2017-05-24
Multiple layers of protection are needed.
[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

---

### Post by Habitual on 2017-05-24
I beat on getting that implemented for a good 2 hours without success.
man page and documented examples did not work.

I had the short and dirty answer using [tcpwrappers]("https://ubuntuforums.org/showthread.php?t=2318000&p=13459876#post13459876") and [fail2ban]("https://www.google.com/url?q=https://help.ubuntu.com/community/Fail2ban&sa=U&ved=0ahUKEwj4nLGhsInUAhUHC8AKHRzjAOoQFggFMAA&client=internal-uds-cse&usg=AFQjCNHdY-rY1W939eqGwU5_e_rfItc2MA"), but I paused.

Kept the link handy. :)

---

### Post by TheFu on 2017-05-24
It is always best to block all remote systems from access unless you **know** they need access. Staying open to the world when it isn't necessary is a bad idea.

And I wouldn't trust DNS for something like this. Stick with subnets - IP ranges.

tcp-wrappers is very powerful and built-into sshd already.
I'm also a fail2ban user.

But by far the easiest way to end almost all ssh hack attempts is to NOT use the default 22/tcp port. Move to a different port - something high. 60K+.  Sure, it is security by obscurity, but 99% of the attempts will end, immediately.  That will clean up the logs so you can bother with only real attacks.

---

### Post by devan1002 on 2017-05-25
Thank you everyone.

I'm using port 2222 but now I'll switch to something else.

I'm not familiar with tcpwrappers or fail2ban.  I was thinking about setting up some sort of firewall knock that would open the port on demand but I think it's unlikely given my level of expertise.

I do like the firewall firehol src modifier to just let one IP range get in.  Can that be spoofed as well?

-Devan

---

### Post by TheFu on 2017-05-25
Is this still an issue?

```

     The following pattern would match any host in the 192.168.0.[0-9] network
     range:

           Host 192.168.0.?

     A pattern-list is a comma-separated list of patterns.  Patterns within
     pattern-lists may be negated by preceding them with an exclamation mark
     (‘!’).  For example, to allow a key to be used from anywhere within an
     organization except from the “dialup” pool, the following entry (in
     authorized_keys) could be used:

           from="!*.dialup.example.com,*.example.com"
```

from the PATTERNS section of the sshd_config manpage.
Does your DNS handle example.com name resolution?

---

### Post by devan1002 on 2017-05-25
Like the other user on this thread, I have been unable to get any host information in my authorized keys file to work.  I don't know if this is a bug but I tried using the canonical name, verified by using "host servername" but whenever I tried using any name, the key was denied.  The only wildcard that worked was from="*". 

I would hope to find someone using 16.04 LTS with a successful from="host" so I know it is possible.

Thanks,

Devan

---

### Post by TheFu on 2017-05-25
Does using ssh -vvvv show anything?  Anything in the server sshd logs?
Is the ~/.ssh/config file 600 and the directory 700?  ssh can be very picky about file permissions.

Looks to me like things should be working. Just guessing at this point.

---

### Post by devan1002 on 2017-05-27
[FONT=arial]sshd_config at loglevel debug3 gave me no more info other than user root attempted with correct key but not allowable host.[/FONT][FONT=arial]
[/FONT]
[FONT=arial]Maybe my ubuntu install doesn't translate the name correctly?  Command line requests for name translation works.  I am not sure how ssh does it.  The weird thing is that in the logs, both host and IP address match but ssh still refuses.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Has anybody out there have success with 16.04?[/FONT]

---

### Post by TheFu on 2017-05-27
Both systems know each other by IP and name as the exact same answers for both the name AND the IP?

---

### Post by devan1002 on 2017-05-28
yep.  

from auth.log
May 28 09:51:12 server1 sshd[2124]: Authentication tried for root with correct key but not from a permitted host (host=123.67.89.123, ip=123.67.89.123).

Mind boggling.

---

### Post by cariboo on 2017-05-28
This may be a dumb question, but have you got:

```
PermitRootLogin without-password
```

enabled in /etc/ssh/sshd_config?

---

### Post by devan1002 on 2017-05-28
That's in the config.  I can ssh to the server if I remove the From portion from authorized_keys.  I can also ssh if I use from="123.44.555.666".  It just doesn't work with hostname or hostname wildcards.

---

### Post by TheFu on 2017-05-29
123.44.555.666?  That's really impressive.  ;)

Sounds like a DNS issue somewhere. Is it DNS, /etc/hosts, NIS, NIS+, LDAP?  How are hostnames resolved? Do they get the FQDN exactly the same way and is it correct?  Forward AND reverse lookups?

---

### Post by lespocky on 2017-07-27
Got a similar problem on Debian after upgrading to stretch. My problem was a changed setting on the server side in /etc/ssh/sshd_config … I got a hint on that after filing a bug:

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=869903](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=869903)

After setting 'UseDNS yes' in /etc/ssh/sshd_config the 'from' option in authorized_keys worked again. :-)

This is somehow documented, but hard to find, see `man 5 sshd_config`:

>      UseDNS  Specifies whether sshd(8) should look up the remote host name, and to check that the resolved host name for the remote IP address maps back to
             the very same IP address.

             If this option is set to no (the default) then only addresses and not host names may be used in ~/.ssh/authorized_keys from and sshd_config
             Match Host directives.



HTH

---

