---
title: "FTP Bruteforce Attempts"
date: 2013-02-19
forum: Security
---

### Post by shibby4555 on 2013-02-19
So I check out my log files occassionally and those damn Chinese keep trying to bruteforce VSFTPD on my server. Any idea how to stop this? Its almost every day, and it just bothers me. The cryptographic strength of my password is very good, but still. Or is it just a reality that I have to deal with?

---

### Post by TheFu on 2013-02-19
Plain FTP is a terrible way to protect any files. Plain FTP should only be used when you want the entire world to see everything on the system. 
[http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) explains more. There are other places saying the same thing around the internet.

Switch to using** sftp** and key-based authentication for any clients outside your LAN. Heck, key-based authentication from inside your LAN is more convenient too. Fantastic clients exist for every platform.

With ssh/scp/sftp, the fail2ban tool will block them after you tell your router to listen on a non-standard port (anything but 22).  Failures should automatically block future access for some period of time - 5 minutes, a day, a year. You decide.

Here is an article [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) about steps to secure ssh - which applies to **sftp **as well.

---

### Post by hakermania on 2013-02-19
I'd just change the default port that FTP uses :)

This worked pretty well for me as for SSH brute forcing attempts!

---

### Post by Ms. Daisy on 2013-02-19
> **shibby4555]So I check out my log files occassionally and those damn Chinese keep trying to bruteforce VSFTPD on my server.[/QUOTE] Reminds me of my CYA motto: when in doubt, spoof a Chinese IP  said:**
> I'd just change the default port that FTP uses :)

This worked pretty well for me as for SSH brute forcing attempts!
As long as you understand that changing ports alone won't actually make you any more secure.  It will probably stop the automated bots because they're looking for default ports for the most part.  But it doesn't make it any harder to find the FTP server.

Change the port, use SFTP and key-based auth like TheFu recommended if you'd like to increase the security on your server as well as decrease log noise.

---

### Post by aerokid240 on 2013-03-07
A couple things that can be done.

1. Ensure that are indeed using ssl with vsftpd, i.e, FTPS . If not, then do so immediately or like others suggested, use SFTP.
2. Switching from the default FTP port helps hide from the automated bots that only check for certain common ports.
3. Consider installing fail2ban. This will block the offending IP addresses that are attempting to brute force your ftp service. It works by monitoring log files, like the one at /var/log/auth.log, for failed log in attempts. If it detects multiple failed logged in attempts from a remote host, it creates an iptables rule to block that host.

---

### Post by HermanAB on 2013-03-09
Simple really.  Iptables has a rate limit rule that you can use to limit new connections from the same IP address:

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

This problem has been solved a decade ago, yet few people are aware of it, since no-one on these forums ever reads man pages.

---

