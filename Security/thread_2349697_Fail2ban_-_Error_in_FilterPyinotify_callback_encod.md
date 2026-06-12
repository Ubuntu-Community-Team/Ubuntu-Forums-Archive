---
title: "Fail2ban - Error in FilterPyinotify callback: encoding with 'idna' codec failed"
date: 2017-01-17
forum: Security
---

### Post by maulvi on 2017-01-17
Hello everyone

I've installed fail2ban and I only configured one jail.  At first I used the action "iptables-allports", later I tried the traditional single port action..  Both reesulted in the same error..

Strangely enough, while the service starts, as per service status message, it did not result in banning any brute-forcing illegals..

The logs keep giving the error message "ERROR   Error in FilterPyinotify callback: encoding with 'idna' codec failed (UnicodeError: label empty or too long)", something which I tried googling but only results on stuffs pertaining to python programming, none on fail2ban.

That last error keeps on persisting after startup..

Below is an excerpt from mu /var/log/fail2nan.log
```

2017-01-17 23:51:46,989 fail2ban.server         [15325]: INFO    Stopping all jails
2017-01-17 23:51:47,396 fail2ban.jail           [15325]: INFO    Jail 'sshd' stopped
2017-01-17 23:51:47,455 fail2ban.server         [15325]: INFO    Exiting Fail2ban
2017-01-17 23:51:47,866 fail2ban.server         [17535]: INFO    Changed logging target to /var/log/fail2ban.log for Fail2ban v0.9.3
2017-01-17 23:51:47,868 fail2ban.database       [17535]: INFO    Connected to fail2ban persistent database '/var/lib/fail2ban/fail2ban.sqlite3'
2017-01-17 23:51:47,937 fail2ban.jail           [17535]: INFO    Creating new jail 'sshd'
2017-01-17 23:51:47,981 fail2ban.jail           [17535]: INFO    Jail 'sshd' uses pyinotify
2017-01-17 23:51:47,997 fail2ban.filter         [17535]: INFO    Set jail log file encoding to UTF-8
2017-01-17 23:51:48,013 fail2ban.jail           [17535]: INFO    Initiated 'pyinotify' backend
2017-01-17 23:51:48,095 fail2ban.filter         [17535]: INFO    Added logfile = /var/log/auth.log
2017-01-17 23:51:48,146 fail2ban.filter         [17535]: INFO    Set findtime = 31536000
2017-01-17 23:51:50,181 fail2ban.filter         [17535]: INFO    Set maxRetry = 5
2017-01-17 23:51:50,182 fail2ban.filter         [17535]: INFO    Set jail log file encoding to UTF-8
2017-01-17 23:51:50,183 fail2ban.actions        [17535]: INFO    Set banTime = 31536000
2017-01-17 23:51:50,184 fail2ban.filter         [17535]: INFO    Set maxlines = 10
2017-01-17 23:51:50,258 fail2ban.server         [17535]: INFO    Jail sshd is not a JournalFilter instance
2017-01-17 23:51:50,304 fail2ban.transmitter    [17535]: WARNING Command ['start', 'sshd'] has failed. Received UnicodeError("encoding with 'idna' codec failed (UnicodeError: label empty or too long)",)
2017-01-17 23:52:01,959 fail2ban.filterpyinotify[17535]: ERROR   Error in FilterPyinotify callback: encoding with 'idna' codec failed (UnicodeError: label empty or too long)
2017-01-17 23:52:02,073 fail2ban.filterpyinotify[17535]: ERROR   Error in FilterPyinotify callback: encoding with 'idna' codec failed (UnicodeError: label empty or too long)
2017-01-17 23:52:02,241 fail2ban.filterpyinotify[17535]: ERROR   Error in FilterPyinotify callback: encoding with 'idna' codec failed (UnicodeError: label empty or too long)
2017-01-17 23:52:02,384 fail2ban.filterpyinotify[17535]: ERROR   Error in FilterPyinotify callback: encoding with 'idna' codec failed (UnicodeError: label empty or too long)
2017-01-17 23:52:03,595 fail2ban.filterpyinotify[17535]: ERROR   Error in FilterPyinotify callback: encoding with 'idna' codec failed (UnicodeError: label empty or too long)
2017-01-17 23:52:05,701 fail2ban.filterpyinotify[17535]: ERROR   Error in FilterPyinotify callback: encoding with 'idna' codec failed (UnicodeError: label empty or too long)
2017-01-17 23:52:11,042 fail2ban.filterpyinotify[17535]: ERROR   Error in FilterPyinotify callback: encoding with 'idna' codec failed (UnicodeError: label empty or too long)
2017-01-17 23:52:11,126 fail2ban.filterpyinotify[17535]: ERROR   Error in FilterPyinotify callback: encoding with 'idna' codec failed (UnicodeError: label empty or too long)

```
My current status - 
```
root@redacted:~# fail2ban-client status sshd
Status for the jail: sshd
|- Filter
|  |- Currently failed: 0
|  |- Total failed:     0
|  `- File list:        /var/log/auth.log
`- Actions
   |- Currently banned: 0
   |- Total banned:     0
   `- Banned IP list:
root@redacted:~# systemctl status fail2ban -l
&#9679; fail2ban.service - Fail2Ban Service
   Loaded: loaded (/lib/systemd/system/fail2ban.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2017-01-17 23:51:50 MYT; 49min ago
     Docs: man:fail2ban(1)
  Process: 17523 ExecStop=/usr/bin/fail2ban-client stop (code=exited, status=0/SUCCESS)
  Process: 17531 ExecStart=/usr/bin/fail2ban-client -x start (code=exited, status=0/SUCCESS)
 Main PID: 17535 (fail2ban-server)
    Tasks: 3
   Memory: 12.0M
      CPU: 1min 32.419s
   CGroup: /system.slice/fail2ban.service
           &#9492;&#9472;17535 /usr/bin/python3 /usr/bin/fail2ban-server -s /var/run/fail2ban/fail2ban.sock -p /var/run/fail2ban/fail2ban.pid -x -b


Jan 17 23:51:47 redacted systemd[1]: Stopped Fail2Ban Service.
Jan 17 23:51:47 redacted systemd[1]: Starting Fail2Ban Service...
Jan 17 23:51:47 redacted fail2ban-client[17531]: 2017-01-17 23:51:47,786 fail2ban.server         [17533]: INFO    Starting Fail2ban v0.9.3
Jan 17 23:51:47 redacted fail2ban-client[17531]: 2017-01-17 23:51:47,788 fail2ban.server         [17533]: INFO    Starting in daemon mode
Jan 17 23:51:50 redacted fail2ban-client[17531]: ERROR  NOK: ("encoding with 'idna' codec failed (UnicodeError: label empty or too long)",)
Jan 17 23:51:50 redacted systemd[1]: Started Fail2Ban Service.

```




Below is my jail.local settings -


```
[sshd]
enabled         = true
port            = ssh
filter          = sshd
logpath         = /var/log/auth.log
#banaction      = iptables-allports
action          = iptables[name=sshd, port=ssh, protocol=tcp]
bantime         = 31536000              ; ip address is banned for 1 year (forever)
findtime        = 31536000              ; Search log history up to 1 year back
maxretry        = 5                     ; allow the ip address retry a max of 5 times
ignoreip        = <a bunch of IPs>

```
Anyone knows whats causing this issue, kindly please help, thank you.

---

### Post by Habitual on 2017-01-17
> **maulvi said:**
> 
Below is my jail.local settings -
```
[sshd]
bantime         = 31536000              ; ip address is banned for 1 year (forever)
findtime        = 31536000              ; Search log history up to 1 year back

```
Anyone knows whats causing this issue, kindly please help, thank you.
I suggest defaults values. 
findtime is 600 #default
bantime = -1 #forever, **For now**...

Also suggest manual test using 
```
sudo fail2ban-regex /var/log/auth.log /etc/fail2ban/filter.d/sshd.conf 
```

The /etc/fail2ban/jail.conf is littered with examples and references.
See also [https://help.ubuntu.com/community/Fail2ban](https://help.ubuntu.com/community/Fail2ban)
and [http://www.fail2ban.org/wiki/index.php/Main_Page](http://www.fail2ban.org/wiki/index.php/Main_Page)

---

### Post by maulvi on 2017-01-18
> **Habitual said:**
> I suggest defaults values. 
findtime is 600 #default
bantime = -1 #forever, **For now**...

Also suggest manual test using 
```
sudo fail2ban-regex /var/log/auth.log /etc/fail2ban/filter.d/sshd.conf 
```

The /etc/fail2ban/jail.conf is littered with examples and references.
See also [https://help.ubuntu.com/community/Fail2ban](https://help.ubuntu.com/community/Fail2ban)
and [http://www.fail2ban.org/wiki/index.php/Main_Page](http://www.fail2ban.org/wiki/index.php/Main_Page)


Hello

Thank you for your kind reply..  The "-1" tip was far out..  I missed that somehow  ;-)

I foundout why my fail2ban broke :o

It seems that the line in jail.local "ignoreip" is the culprit.  No matter if it is a long line excluding whole geographic regions by IP Addresses or just less than half a dozen IPs, it will cause the error I encountered.

I had to hardcode the ignoreip directive in jail.conf for it to load up properly for fail2ban to work

---

### Post by Habitual on 2017-01-18
> **maulvi said:**
> Hello

Thank you for your kind reply..  The "-1" tip was far out..  I missed that somehow  ;-)

I foundout why my fail2ban broke :o

It seems that the line in jail.local "ignoreip" is the culprit.  No matter if it is a long line excluding whole geographic regions by IP Addresses or just less than half a dozen IPs, it will cause the error I encountered.

I had to hardcode the ignoreip directive in jail.conf for it to load up properly for fail2ban to work
Since it is python-based and python is tab and space aware, I believe it was likely a formatting issue 
possibly involving both spaces and tabs, which I don't recommend.
I usually line everything up on the right-side of the "=" sign, keeps me safe.

Glad it worked out.
+1 and props for using jail.local. Tells me a lot.

wrt:
> **maulvi said:**
> 
findtime        = 31536000              ; Search log history up to 1 year back
You have /var/log/auth.logs that go back a whole year? :)

---

