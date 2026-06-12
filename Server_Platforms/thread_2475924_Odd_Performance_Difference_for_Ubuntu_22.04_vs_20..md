---
title: "Odd Performance Difference for Ubuntu 22.04 vs 20.04 for SSL-enabled MySQL Connection"
date: 2022-06-11
forum: Server Platforms
---

### Post by orware on 2022-06-11
I haven't ever really encountered something that is this specific so I wanted to share it here in the forums and see if any others might have thoughts.

I've been working on a fairly small/simply PHP script in recent weeks that gathers MySQL connection time metrics, and the database I'm connecting to is publicly accessible and the connections have to be made over SSL.

I was running some tests today in AWS and spun up a few new VMs, and figured I'd try things out with an Ubuntu 22.04 VM because it is the latest/greatest.

After creating the 22.04 VM, I added my script to the server and started up the test process (the script loops forever, and connects/disconnects from the MySQL databases on each run and tracks the time to connect in milliseconds each time).


Under ideal conditions, the connection times I'm expecting should be in the 10-20 millisecond range due to the extra SSL handshake steps when creating the connection (and this is when the VM and the database are in the same general AWS region).

However, with an Ubuntu 22.04 VM, the connection times I get were much higher than that and were initially in the 130ms range, but now seem to be hovering in the 70ms range, but still very high in comparison to an equivalent Ubuntu 20.04 VM that was spun up afterward in AWS.

To add some additional confirmation, I went over to Vultr and spun up an Ubuntu 22.04 and Ubuntu 20.04 VM and did the same set of the tests (in this case Vultr didn't have an exact equivalent region so the timing isn't as fast, but there's still a significant difference between the two). For this test, the Ubuntu 22.04 VM is connecting in about 100ms on average vs. the Ubuntu 20.04 VM is connecting in 45ms.

The main difference that I'm directly aware of is PHP 7.4 is installed for the CLI in Ubuntu 20.04 vs. PHP 8.1 in Ubuntu 22.04. After this I'm enabling the mysqli extension, but it just seems weird to have this sort of large performance delta between the two Ubuntu versions and I was hoping there might be an explanation that someone could offer for it.

```
PHP installation commands ran on the Ubuntu 22.04 VMs:
sudo apt install php8.1-cli
sudo apt-get install php8.1-mysqli


PHP installation commands ran on the Ubuntu 20.04 VMs:
sudo apt install php7.4-cli
sudo apt-get install php7.4-mysqli
```

---

### Post by orware on 2022-06-11
A few other notes:

I don't believe this issue is related to the PHP versions as far as I can tell for several reasons. In other tests I have had running for the last few weeks, those were on Ubuntu 20.04 servers using PHP 8.1 and those ran with timing information that matches my 20.04 data I shared above.

I also ran a quick test on the Ubuntu 20.04 Vultr VM I was still connected to and updated it to PHP 8.1 and re-ran the connection tests and they were still in that 45ms range.

So at the moment it feels like something specifically related to Ubuntu 22.04, but I'm just not certain what exactly has changed that would explain such a difference in responsiveness.

---

### Post by orware on 2022-09-27
Ubuntu 22.04's latest OpenSSL version appears to be v3.0.2, but a recent ProxySQL Pull Request here seems to indicate that perhaps the performance differences I shared above may be due to OpenSSL performance differences:
[https://github.com/sysown/proxysql/pull/3937](https://github.com/sysown/proxysql/pull/3937)

I attempted to manually compile OpenSSL v3.0.5 on an Ubuntu 22.04 server but PHP kept on thinking/using the 3.0.2 version that comes installed by default so I may have been doing something wrong, but hopefully once v3.0.5 is available as standard on Ubuntu 22.04 the performance differences I noted above may go away on their own or be reduced significantly.

---

