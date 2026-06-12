---
title: "no CUPS webadmin access?"
date: 2010-02-17
forum: System76 Support
---

### Post by ethanay on 2010-02-17
Hello,

On my recommendation, my dad made the transition to Ubuntu from an old WinXP computer via a System76 Meerkat Nettop.  He loves it so far -- it does everything he needs it to do and it is MUCH lower maintenance.

One thing has been bothering me (as admin):  No access to [http://localhost:631](http://localhost:631) on his computer.  I can't for the life of me figure out why it is.  What can I do to enable CUPS web admin interface access??

Thank you System76!!  Wonderful counterpoint to that SmellsLikeDell.  As a side note:  If you had a small/light laptop with solid firewire (a la Dell XPS m1330; for audio streaming), I'd buy my next upgrade through you!  I hate those 17" clunkers.

---

### Post by thomasaaron on 2010-02-18
The webadmin interface works for me on a fresh install of 9.10.

What error does firefox give? Server not found?

---

### Post by jdb on 2010-02-18
> **ethanay said:**
> Hello,

On my recommendation, my dad made the transition to Ubuntu from an old WinXP computer via a System76 Meerkat Nettop.  He loves it so far -- it does everything he needs it to do and it is MUCH lower maintenance.

One thing has been bothering me (as admin):  No access to [http://localhost:631](http://localhost:631) on his computer.  I can't for the life of me figure out why it is.  What can I do to enable CUPS web admin interface access??

Thank you System76!!  Wonderful counterpoint to that SmellsLikeDell.  As a side note:  If you had a small/light laptop with solid firewire (a la Dell XPS m1330; for audio streaming), I'd buy my next upgrade through you!  I hate those 17" clunkers.

I ran into that once but I can't for the life of me remember what it was.
I think it was a permissions issue of some sort

You might try sudo firefox just to see what happens.

jdb

---

### Post by ethanay on 2010-02-20
i'm away from his computer, but here's what i remember:

1. i type in [http://localhost:631](http://localhost:631) (or click on the link)
2. instead of going to the CUPS web admin interface, Firefox looks up [www.localhost.com](www.localhost.com), and
3. eventually returns a "server not found" error

ethan

---

### Post by thomasaaron on 2010-02-22
Stupid question: Do other websites work? i.e is File > Work Offline selected?

Did JDB's solution work?

Try running...
sudo apt-get --reinstall install cups
...from a terminal.

---

### Post by apmcd47 on 2010-02-22
> **ethanay said:**
> i'm away from his computer, but here's what i remember:

1. i type in [http://localhost:631](http://localhost:631) (or click on the link)
2. instead of going to the CUPS web admin interface, Firefox looks up [www.localhost.com](www.localhost.com), and
3. eventually returns a "server not found" error

ethan

What are the proxy settings for this machine/firefox? It sounds to me as though firefox is sending the request through a proxy server.

Can you install the telnet client and see what you get when you type ```
telnet localhost 631
``` at the command prompt? If you get an http response then CUPS is probably okay. Also check /etc/hosts has the correct entry for localhost (compare with a working machine).

Andrew

---

### Post by ethanay on 2010-02-23
Thomas -- yes, other websites work fine :) (and no, not a stupid question, just part of the diagnostic process)

I will try the suggestions everyone has mentioned when I have access to the computer again, and report back.

thanks!

ethan

---

### Post by ethanay on 2010-02-26
alright, here's the update:

1. ```
sudo firefox
```
same behavior

2. ```
sudo apt-get --reinstall install cups
```
same behavior

3. ```
$ telnet localhost 631
telnet: could not resolve localhost/631: Name or service not known

```

any other suggestions?

---

### Post by Flyers2391 on 2010-02-26
> **ethanay said:**
> 
3. ```
$ telnet localhost 631
telnet: could not resolve localhost/631: Name or service not known

```

any other suggestions?

Have you tried to hit it by IP address?

---

### Post by ethanay on 2010-02-27
How do you access the CUPS web interface via IP address?

---

### Post by riseringseeker on 2010-02-28
> **ethanay said:**
> How do you access the CUPS web interface via IP address?

Use the IP address localhost.  Type "ifconfig" in a terminal and find out what it is, it will be listed as 

inet addr:192.168.1.1 
(for example) 

then try:

```
192.168.1.1:631
```

or whatever IP address ifconfig returns.

---

### Post by ethanay on 2010-02-28
ifconfig returned 

```
inet addr:127.0.0.1
```

tried from a computer with working CUPS webadmin:
```
telnet 127.0.0.1 631
```
connects me.  typing "quit" terminated the connection.

tried it on the problem computer:

1. initially connected through telnet, but "quit" would NOT terminate connection.
2. tried via firefox:  same error message as before
3. tried again via telnet:
```
$ telnet 127.0.0.1 631
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
```

so it seems like something is either crashing or hanging on this computer, making that resource unavailable.  on a hunch, tried restarting CUPS:

```
$ sudo /etc/init.d/cups restart
sudo: unable to resolve host john-desktop
[sudo] password for john: 
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
```

and tried telnet again:
```
$ telnet 127.0.0.1 631
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
quit
Connection closed by foreign host.
```

now I can connect via Firefox to the CUPS web admin:
```
http://127.0.0.1:631
```
but STILL not via localhost:
```
http://localhost:631
Connecting to www.localhost.com...
```

So there are two problems on this computer:
1. CUPS appears to be unstable, and freezes or crashes
2. connection to CUPS webadmin interface, even when CUPS is working, is only available via IP address, NOT localhost

thanks for the help folks!

---

### Post by ethanay on 2010-02-28
PS Here's some debug info from a time a bit back when CUPS was crashing on me constantly on the problem computer, in case it is helpful:

```
$ system-config-printer --debug
Connected as user john
refresh
<monitor.Monitor instance at 0xa3c280c>: CUPS IPP error (1282, 'server-error-service-unavailable')
Created subscription -1
<monitor.Monitor instance at 0xa3c280c>: CUPS IPP error (1282, 'server-error-service-unavailable')
Authentication pass: 1
Authentication: password callback set
get_notifications
refresh
Created subscription 18
<monitor.Monitor instance at 0xa3c280c>: printers and jobs lists provided
update_jobs
get_notifications
update_jobs
retrying operation...
Authentication pass: 1
Authentication: password callback set
Authentication pass: 1
Authentication: password callback set
Canceled subscription 18
<monitor.Monitor instance at 0xa3c280c> exited
```

---

### Post by ethanay on 2010-03-11
no one has any ideas as to why [http://localhost:631](http://localhost:631) is converted to [www.localhost.com](www.localhost.com) on the Meerkat?

---

### Post by riseringseeker on 2010-03-12
> **ethanay said:**
> no one has any ideas as to why [http://localhost:631](http://localhost:631) is converted to [www.localhost.com](www.localhost.com) on the Meerkat?

Might not be a factor, but what does ```
hostname
``` in a terminal return?

---

### Post by ethanay on 2010-03-13
Thanks for the suggestion...

```
$ hostname
john-desktop
```

the command prints a similar response on both the working computers.

Proxy settings appear identical as well...!!

---

### Post by riseringseeker on 2010-03-14
> **ethanay said:**
> Thanks for the suggestion...

```
$ hostname
john-desktop
```

the command prints a similar response on both the working computers.

Proxy settings appear identical as well...!!

If my thinking cap is on straight this morning,

```
cat /etc/hosts
```

should return something like this:

```
127.0.0.1	localhost
127.0.1.1	john-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

If it's not, maybe we've got something to work with.

I just help get a friend setup with his brand new Meerkat yesterday, and have sent him an e-mail to see if he has the same error, I would have done it when there had I thought of it.

[update] The new Meerkat does NOT show the same behavior.  localhost:631 works as it should

---

### Post by ethanay on 2010-03-26
Ok, looks like we are getting somewhere!  Maybe the hosts file is corrupted:

```
$ cat /etc/hosts
# Do not remove the following line, or various programs# that require network functionality will fail.127.0.0.1	localhost.localdomain	localhostjohn@john-desktop:~$
```

I will edit and update...

UPDATE:  SUCCESS!  It was a corrupted hosts file...how/why it was corrupted, Lord knows.  Nothing we did should have caused that (normal software installs, updates, etc).

So maybe some Meerkats shipped with corrupted hosts files for some reason?

---

### Post by thomasaaron on 2010-03-29
I'm not sure what fouled up the hosts file on a freshly imaged Meerkat, and I had no problems going to cups admin.

---

### Post by ethanay on 2010-05-03
> **thomasaaron said:**
> I'm not sure what fouled up the hosts file on a freshly imaged Meerkat, and I had no problems going to cups admin.

It is quite obviously a case of Gremlins :)

It was a good experience for me...I am slowly getting used to the (usual presence of) logic in Unix-based systems.  

"Problem with localhost?  Try looking at the hosts file..."

---

