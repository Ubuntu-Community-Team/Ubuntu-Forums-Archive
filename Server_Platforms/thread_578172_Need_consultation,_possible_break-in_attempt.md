---
title: "Need consultation, possible break-in attempt"
date: 2007-10-17
forum: Server Platforms
---

### Post by daxumaming on 2007-10-17
Hi guys, I've setup a Gutsy RC server and it's been running really well. However, I'm quite concerned about the possible break-in attempts of unscrupulous individuals, and I'd like to consult the community about this.

1 ) I've configured OpenSSH to only accept logins with an SSH key, so no PAM.. Is there a way someone can circumvent this?

2 ) I only created 2 users, my main one (with sudo privileges) and a regular account - an email account. What command do I need to type to list down users and groups on my server. I need to keep track any newly created accounts/groups.

3 ) I'd like to confirm that the only one capable of creating a root account is the account with sudo priviliges. Is this correct? I'm not comfortable with having a root account, so I want to make sure no one else is capable.

4 ) I checked /var/log/auth.log and got this:

```
Oct 17 06:26:32 server su[26605]: Successful su for www-data by root
Oct 17 06:26:32 server su[26605]: + ??? root:www-data
Oct 17 06:26:32 server su[26605]: pam_unix(su:session): session opened for user www-data by (uid=0)
Oct 17 06:26:32 server su[26605]: pam_unix(su:session): session closed for user www-data
Oct 17 06:26:35 server su[26632]: Successful su for nobody by root
Oct 17 06:26:36 server su[26632]: + ??? root:nobody
Oct 17 06:26:36 server su[26632]: pam_unix(su:session): session opened for user nobody by (uid=0)
Oct 17 06:26:36 server su[26632]: pam_unix(su:session): session closed for user nobody
Oct 17 06:26:36 server su[26636]: Successful su for nobody by root
Oct 17 06:26:36 server su[26636]: + ??? root:nobody
Oct 17 06:26:36 server su[26636]: pam_unix(su:session): session opened for user nobody by (uid=0)
Oct 17 06:26:36 server su[26636]: pam_unix(su:session): session closed for user nobody
Oct 17 06:26:36 server su[26638]: Successful su for nobody by root
Oct 17 06:26:36 server su[26638]: + ??? root:nobody
Oct 17 06:26:36 server su[26638]: pam_unix(su:session): session opened for user nobody by (uid=0)
Oct 17 06:27:10 server su[26638]: pam_unix(su:session): session closed for user nobody
Oct 17 06:31:34 server CRON[26523]: pam_unix(cron:session): session closed for user root
Oct 17 06:39:01 server CRON[31492]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 17 06:39:01 server CRON[31492]: pam_unix(cron:session): session closed for user root
Oct 17 06:40:53 server sshd[31499]: Did not receive identification string from 200.27.236.10

```

Does this mean that I now have a root account?
If so, how is this possible?
If not, do I need to worry about anything?

5 ) I've also been getting this:

```

Oct 15 22:22:13 server sshd[7958]: Invalid user pgsql from 200.74.167.51
Oct 15 22:22:21 server sshd[7962]: Invalid user adm from 200.74.167.51
Oct 15 22:22:25 server sshd[7964]: Invalid user ident from 200.74.167.51
Oct 15 22:22:29 server sshd[7966]: Invalid user webpop from 200.74.167.51
Oct 15 22:22:33 server sshd[7968]: Invalid user susan from 200.74.167.51
Oct 15 22:22:37 server sshd[7970]: Invalid user sunny from 200.74.167.51
Oct 15 22:22:41 server sshd[7972]: Invalid user steven from 200.74.167.51
Oct 15 22:22:45 server sshd[7974]: Invalid user ssh from 200.74.167.51
Oct 15 22:22:49 server sshd[7976]: Invalid user search from 200.74.167.51
Oct 15 22:22:52 server sshd[7978]: Invalid user sara from 200.74.167.51
Oct 15 22:22:57 server sshd[7980]: Invalid user robert from 200.74.167.51
Oct 15 22:23:01 server sshd[7982]: Invalid user richard from 200.74.167.51
Oct 15 22:23:05 server sshd[7984]: Invalid user party from 200.74.167.51
Oct 15 22:23:09 server sshd[7986]: Invalid user amanda from 200.74.167.51
Oct 15 22:23:13 server sshd[7988]: Invalid user rpm from 200.74.167.51
Oct 15 22:23:18 server sshd[7990]: Invalid user operator from 200.74.167.51
Oct 15 22:23:22 server sshd[7992]: Invalid user sgi from 200.74.167.51
Oct 15 22:23:26 server sshd[7994]: User sshd not allowed because account is locked
Oct 15 19:39:01 server CRON[7584]: pam_unix(cron:session): session closed for user root
Oct 15 19:51:02 server sshd[7591]: Did not receive identification string from 208.75.212.160
Oct 15 19:51:35 server sshd[7592]: Address 208.75.212.160 maps to server160.inetservices.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Oct 15 19:51:35 server sshd[7592]: pam_unix(ssh:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=208.75.212.160  user=root
Oct 15 19:51:37 server sshd[7592]: Failed password for root from 208.75.212.160 port 44871 ssh2
Oct 15 19:51:41 server sshd[7594]: Address 208.75.212.160 maps to server160.inetservices.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Oct 15 19:51:41 server sshd[7594]: pam_unix(ssh:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=208.75.212.160  user=root
Oct 15 19:51:43 server sshd[7594]: Failed password for root from 208.75.212.160 port 47610 ssh2
Oct 15 19:51:48 server sshd[7611]: Address 208.75.212.160 maps to server160.inetservices.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Oct 15 19:51:48 server sshd[7611]: Invalid user apple from 208.75.212.160
Oct 15 19:51:48 server sshd[7611]: pam_unix(ssh:auth): check pass; user unknown
Oct 15 19:51:48 server sshd[7611]: pam_unix(ssh:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=208.75.212.160 
Oct 15 19:51:51 server sshd[7611]: Failed password for invalid user apple from 208.75.212.160 port 48360 ssh2
Oct 15 19:51:54 server sshd[7613]: Address 208.75.212.160 maps to server160.inetservices.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Oct 17 01:24:53 server sshd[25765]: Address 211.233.59.172 maps to 211-233-59-172.kidc.net, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Oct 17 01:24:53 server sshd[25765]: User root not allowed because account is locked
Oct 17 06:41:11 server sshd[31500]: Invalid user test from 200.27.236.10
Oct 17 06:41:19 server sshd[31502]: Invalid user test from 200.27.236.10
Oct 17 06:41:28 server sshd[31504]: Invalid user test from 200.27.236.10


```

Is this normal for a server?

6 ) Where can I find the log of all executed commands?

7 ) What other logs do I need to review regularly?

8 ) Do I need to setup a firewall for my server?

Thanks for your help!

---

### Post by codmate on 2007-10-17
Firstly, you should know that all Ubuntu and Debian boxes have a root account.
Try ```
sudo crontab -l -u root
```
...and you'll see that root has a crontab and everything.

The sudo system is just a different way of accessing root.
Don't imagine it makes your box any more secure.
Treat all admin users as if they were root and you'll be OK.

Firstly, it is normal for nobody to su to root and do stuff. This can happen when you're running certain software such as apache or samba. It is a good precaution to check that 'nobody' doesn't have a shell. ```
grep nobody /etc/passwd
``` and check that nobody doesn't have a shell.
You don't want to see 'bin/bash' or '/bin/sh' or anything like that on the line that grep returns.

If nobody does have a shell, then ```
echo "/dev/null" >> /etc/shells
chsh -s /dev/null nobody
```
This is just a precaution...

As for the ```
Did not receive identification string from
``` and ```
Invalid user y from x.x.x.x
```...those do look like scripted attacks to me; although the first can also be caused by some software and older versions of ssh.

I would either change your ssh port or lock it down to specific ip addresses (or an ip range if appropriate).

To lock ssh down to one ip, try this in your iptables configuration:
```
-A INPUT -p tcp -s x.x.x.x -m tcp --dport 22 -m state --state NEW -m limit --limit 3/min --limit-burst 3 -j ACCEPT
-A OUTPUT -p tcp --sport 22 -m state --state ESTABLISHED -j ACCEPT
```
...where x.x.x.x is the ip address you want to lock ssh down to. If you want to use a range - try something like ```
--src-range 192.168.0.5-192.168.0.10
``` instead of ```
-s x.x.x.x
``` on the INPUT line.

Hope this helps.

---

### Post by codmate on 2007-10-17
Oh - and BTW, you can find logs of executed commands in users' .bash_history files if they are using bash.

You should be looking in /var/log/messages, /var/log/auth and /var/log/syslog on a regular basis.
If you're running apache or samba, also be sure tocheck their logs regularly.

You are already running the iptables firewall...```
sudo iptables -L
```
I really suggest reading up on how to configure it.
Here is the basic Ubuntu community 'how-to':
[https://help.ubuntu.com/community/IptablesHowTo?highlight=%28iptables%29](https://help.ubuntu.com/community/IptablesHowTo?highlight=%28iptables%29)

---

### Post by daxumaming on 2007-10-17
Thank you codmate. You've been very helpful. Now I can sleep peacefully at night.

---

### Post by joewilliams on 2007-10-17
All those IPs look like compromised accounts/servers.  The last one has a wide open directory with ready to download Warez...like Office, Photoshop , etc..and what must be a script kiddie favorite: Spysharp.exe which is a password recovery tool for windows.  

It looks like Iptables is doing it's job on your machine.

---

### Post by Endolith on 2007-11-28
> **codmate said:**
> Firstly, it is normal for nobody to su to root and do stuff. This can happen when you're running certain software such as apache or samba.

Is that what all this is?  Because I see this too:
> 
Oct 17 06:31:34 server CRON[26523]: pam_unix(cron:session): session closed for user root
Oct 17 06:39:01 server CRON[31492]: pam_unix(cron:session): session opened for user root by (uid=0)

> It is a good precaution to check that 'nobody' doesn't have a shell. ```
grep nobody /etc/passwd
``` and check that nobody doesn't have a shell.

You don't want to see 'bin/bash' or '/bin/sh' or anything like that on the line that grep returns.


I get this:

> nobody:x:65534:65534:nobody:/nonexistent:/bin/sh


Why is this bad?  What does this mean?  Is Ubuntu configured like this by default or does this mean someone has accessed by computer?  Is there any reason why they would have one?

---

### Post by crouton on 2007-11-29
It appears that this is the Ubuntu default, as my system also has /bin/sh.

---

### Post by HermanAB on 2007-11-29
Well, that is dumb.  User nobody should have /biin/false or /bin/nologin as its 'shell'.

Note that you can easily stop brute force SSH attacks in a number of ways:
a. Change the port to a non standard port, eg 2222 or whatever, in /etc/ssh/sshd_config
b. Install a rate limiting iptables rule.
c. Install a black listing utility.

Each method has advantages and disadvantages.  I do both a and b.

There are existing threads on all of the above on the forum already.

Cheers,

Herman

---

### Post by crouton on 2007-11-29
I haven't researched this a lot (yet), but I thought there was a way to change the number of attempts per 'session' and also to change the timeperiod between attempt 'sessions'.  Increasing the # of attempts/session but also increasing the timeperiod between sessions should make your system still usable but more secure, as the brute force method is forced to wait that increased period before more logins can be attempted.

I could be absolutely wrong about this, please correct me if this is the case.

---

### Post by johnl on 2007-11-29
These brute force ssh attempts are perfectly normal.  If you don't want to change the port that ssh is listening on, there are a couple programs out there that will identify these kind of attacks and stop them:

fail2ban is a common one that can be found in the ubuntu repositories;  it gives each IP address a certain number of failed login attempts, then blocks that IP address from attempting to login again for a configurable amount of time.  This will stop attacks that are all coming from the same location, or at least slow them down enough that they are no longer feasible.

sshdfilter is a similar program that is more aggressive;  if an IP address attempts to login with an invalid username, that IP address is  permanently blocked. If an IP address gives an incorrect password for an existing username N times in a row, that IP address is blocked.  I don't know if sshdfilter is available in the repos.


Generally I would recommend fail2ban because it's a little easier to set up, but they both work fine.

---

### Post by johnl on 2007-11-29
Also, it should be noted that you can disable any attempt to login as root remotely.

In /etc/ssh/sshd_config, make sure that the line:
```
PermitRootLogin no
``` is present and uncommented (doesn't start with a # symbol).

If it says "PermitRootLogin yes," change it to no.  You can then restart the ssh service with 'sudo /etc/init.d/ssh restart'

I'm not sure if remote root logins are enabled or disabled by default on Ubuntu, so it's worth checking.

---

### Post by p_quarles on 2007-11-29
> **johnl said:**
> Also, it should be noted that you can disable any attempt to login as root remotely.

In /etc/ssh/sshd_config, make sure that the line:
```
PermitRootLogin no
``` is present and uncommented (doesn't start with a # symbol).

If it says "PermitRootLogin yes," change it to no.  You can then restart the ssh service with 'sudo /etc/init.d/ssh restart'

I'm not sure if remote root logins are enabled or disabled by default on Ubuntu, so it's worth checking.
They are enabled by default. That's definitely the first thing to change when you install openssh-server. 

My strategy (aside from using a non-standard port) is to use this setting:
```
PasswordAuthentication no
```
That way you don't even get asked for a password, and unless you happen to be carrying around a copy of my private rsa key, you're not getting in. Passwordless authentication is much more difficult to brute force (i.e., not even do-able by an ordinary computer) than a good password.

---

