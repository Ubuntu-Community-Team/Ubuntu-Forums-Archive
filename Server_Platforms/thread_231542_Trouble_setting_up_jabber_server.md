---
title: "Trouble setting up jabber server"
date: 2006-08-07
forum: Server Platforms
---

### Post by arjun.shankar on 2006-08-07
I wanted to run a local jabber server on my friend's Dapper machine.

Well, I did the following:

**gagan@Tulip:~$ sudo apt-get install jabber**

The server starts up on install

so I gave:

**gagan@Tulip:~$ sudo /etc/init.d/jabber stop**

then

**gagan@Tulip:~$ ps aux | grep jabber gives me this:**

[B]jabber    5780  0.0  0.3   4480  1804 ?        Ss   23:04   0:00 /usr/sbin/jabberd -h 172.16.16.2 -s /var/lib/jabber
jabber    5781  0.0  0.1   4340   868 ?        S    23:04   0:00 /usr/sbin/jabberd -h 172.16.16.2 -s /var/lib/jabber
[/B]

Is this normal? It shouldn't be like this. Right? Anyways I didn't want to kill these processes, so I decided to reboot.

Before rebooting, I edited /etc/jabber/jabber.cfg so and set the hostname to 172.16.16.200 (The local IP address, we don't use DNS here.)

I also gave:

**gagan@Tulip:~$ sudo apt-get install sysv-rc-conf**

and made sure jabber doesn't start on rebooting (I had trouble when playing with the jabber server package on my notebook also, so I wanted to start fresh with the actual machine).

I rebooted. Now jabber isn't running (obviously, I had disabled it). So this I gave:

**gagan@Tulip:~$ sudo /etc/init.d/jabber start**

Again I see two instances of jabberd from ps.

Also:

**gagan@Tulip:~$ nmap -n localhost**

Shows port 5222 to be closed.

Then:

**gagan@Tulip:~$ sudo /etc/init.d/jabber stop**

The ps entries dont go away after this. Weird!

I kill both, and then:

**gagan@Tulip:~$ jabberd -h 172.16.16.200**

And I get this:

[B]Invalid Configuration in instance 'elogger':
<file>/var/log/jabber/error.log</file>
[/B]

What just happened?

---

