---
title: "SSH very slow to respond"
date: 2009-01-21
forum: Server Platforms
---

### Post by irishdunn on 2009-01-21
I have noticed that when I jump into my server through SSH there is like a 30 second wait time from the time I type the command to the password prompt.

Once inside the machine works great, no speed issues.

I had chalked this issue up to something screwy in the 'tubes' of the interweb but recently I was checking ports from a verlihub install and noticed when I do:

netstat -tlup

here is an example:
[PHP]
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:21                    *:*                     LISTEN      4457/sshd       
tcp        0      0 *:mysql                 *:*                     LISTEN      4548/mysqld     
tcp        0      0 *:webmin                *:*                     LISTEN      4822/perl       
tcp        0      0 *:www                   *:*                     LISTEN      4769/apache2    
tcp        0      0 localhost:6010          *:*                     LISTEN      4929/0          
tcp        0      0 *:411                   *:*                     LISTEN      4664/verlihub

* 45 SECOND WAIT *
   
tcp6       0      0 [::]:21               [::]:*                  LISTEN      22/sshd       
tcp6       0      0 [::]:8009               [::]:*                  LISTEN      4789/jsvc       
tcp6       0      0 [::]:http-alt           [::]:*                  LISTEN      4789/jsvc       
tcp6       0      0 localhost:6010          [::]:*                  LISTEN      4929/0          
udp        0      0 *:10000                 *:*                                 4822/perl   
[/PHP]

Not sure why this is happening... any ides?

---

### Post by Dr Small on 2009-01-21
I'm guessing that since your SSHd config file probably does not specify a ListenAddress, it is listening on all interfaces, including IPv6. I would try setting the ListenAddress to your server's LAN IP just for tests (so long as this box is not remote), restart SSH and then see how the connectivity is.

Because they way I am figuring, Box A (running SSHd) is listening on IPv4 and IPv6 addresses. Box B (the client) is trying to resolve the address to IPv6 first and then to IPv4, thus, the slow response time.

Maybe this has something to do with the client end, I really don't know.

---

### Post by tubezninja on 2009-01-21
Just curious: what is the latency (ping time) between your client and the server?  I've found the initial ssh connection really bogs down if you have a high latency.

---

### Post by Cracauer on 2009-01-22
Either xauth. Does it go faster when you do `ssh -x`?

Or reverse lookup. But that should be 20 seconds. Can you reverse lookup your IP address with nslookup?

---

### Post by irishdunn on 2009-01-22
The issue was in my /etc/hosts and /etc/resolv.conf files... I needed to specify my domain.

Problem Fixed.

---

### Post by kaspar_silas on 2009-12-10
Hi, 

What exactly did you add/alter in /etc/hosts or /etc/resol.conf

As you might have guessed I now have the same issue.

---

### Post by irishdunn on 2009-12-11
I am connecting to it via some domain (domain.domain.topleveldomain)

I placed that in my hosts file.

---

### Post by kaspar_silas on 2009-12-15
Cheers that sorted out me as well

---

### Post by car1 on 2009-12-15
You can add "UseDNS no" to /etc/ssh/sshd_config to turn off reverse DNS lookup attempts, this has caused slowness on initial connections for me in the past.

---

### Post by kaspar_silas on 2009-12-18
"UseDNS" is not mentioned in my sshd_config. Did you just add this line in?

---

### Post by doodah on 2010-03-25
In case anyone else is looking for this in future, UseDNS defaults to Yes, so it doesn't matter if it's in sshd_config or not.

<add_to_file value="sshd_config">
UseDNS No
</add_to_file>

---

### Post by spynappels on 2010-03-25
If for some reason you need the Reverse DNS feature, you can also open port 53 in your firewall and specify your DNS server(s) as originating host. Also fixes the slow to log in issue.

---

### Post by terazen on 2010-03-25
> **doodah said:**
> In case anyone else is looking for this in future, UseDNS defaults to Yes, so it doesn't matter if it's in sshd_config or not.

<add_to_file value="sshd_config">
UseDNS No
</add_to_file>

Strangely I had to set to "UseDNS no" instead of "UseDNS No".  The error was "Bad yes/no argument".

---

### Post by germallon on 2010-08-13
> **irishdunn said:**
> I am connecting to it via some domain (domain.domain.topleveldomain)

I placed that in my hosts file.
Forgive my ignorance.  But how exactly do you do that?
Here's what my hosts file looks like:

[I]127.0.0.1    localhost
127.0.1.1    g

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/I]


And here's how my resolv.conf file looks like:

[I]# Generated by NetworkManager
nameserver 192.168.10.1

[/I]Thank you in advance.

---

### Post by kaspar_silas on 2010-08-31
I think the information you want is here:
[ http://ubuntuforums.org/showthread.php?t=3407"]http://ubuntuforums.org/showthread.php?t=3407"] http://ubuntuforums.org/showthread.php?t=3407]("http://ubuntuforums.org/showthread.php?t=3407")

---

