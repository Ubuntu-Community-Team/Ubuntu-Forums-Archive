---
title: "SSH Security"
date: 2006-11-24
forum: Server Platforms
---

### Post by szim90 on 2006-11-24
I apologize if this has an obvious answer; I am new to running a server. I 

I have been running my powermac running Ubuntu as a server for a few months. I use it primarily as a dav and sftp server so I can access my files when I am away. The only ports that are not blocked by my router's firewall are 8000 (my isp blocks port 80), 22, and 4900-5000 (for irc).

I recently looked through the auth.log and was stunned that multiple people had tried to gain access to my machine through ssh.

These are parts of the auth.log entry
```

Nov 23 05:49:56 localhost sshd[9728]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ppp-82-85-8-68.cust-adsl.tiscali.it  user=root
Nov 23 05:49:58 localhost sshd[9728]: Failed password for root from 82.85.8.68 port 52536 ssh2
Nov 23 05:49:59 localhost sshd[9730]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ppp-82-85-8-68.cust-adsl.tiscali.it  user=root

```

```

Nov 23 06:04:21 localhost sshd[10609]: Invalid user sells from 82.85.8.68
Nov 23 06:04:21 localhost sshd[10609]: (pam_unix) check pass; user unknown
Nov 23 06:04:21 localhost sshd[10609]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ppp-82-85-8-68.cust-adsl.tiscali.it 

```

It appears the attacker tried different usernames and when he found one that was valid, tried to access my computer using it.

I don't see anywhere in the log that any attempt to gain access was successful, but I am not sure what it would look like if one of these attacks succeed. How would I get the log to filter out all the failed attacks?

Also, is it possible to make ssh block an ip address after a certain number of failed attempts? 

Again, I am sorry if this is obvious, but I am worried about my computer's and my network's security. Are servers attacked like this often? What is the best way to handle this?

Thank you for any help,
Sean

---

### Post by MJN on 2006-11-24
Welcome to the world of SSH - that's what happens round these parts!

There's little to worry about as long as your passwords are secure - at the very least these so-called 'brute force' attempts will be running dictionary attacks so dictionary words as your password is obviously a no-no. There are numerous comments/discussion on the web about password strengths so I won't go into it here.

If you still want to keep them out (it can certainly help you sleep at night - you don't want people knocking on your door even if it is locked) then there are numerous packages available. I use Denyhosts[1] ([http://denyhosts.sourceforge.net/](http://denyhosts.sourceforge.net/)) as it goes one step further than other similar tools in that not only does it block IPs that repeatedly fail to login but it can also be set to download (and upload for that matter) IPs that other Denyhosts users have been attacked by - there is a page at [http://stats.denyhosts.net/stats.html](http://stats.denyhosts.net/stats.html) showing this in 'real time'.

Fail2ban ([http://fail2ban.sourceforge.net/](http://fail2ban.sourceforge.net/)) is another popular tool for this too.

Mathew

[1] I'm not sure if Denyhosts is available in the Ubuntu repositories however there is a guide to installation/configuration at [www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts](www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts)

---

### Post by szim90 on 2006-11-24
Thank you MJN. I'll certainly try denyhosts.

I am confident that the user passwords are secure.

However, are the password for the mysql, www, and other system accounts the same as the root password - I want to make sure they are secure as well.

---

### Post by MJN on 2006-11-24
They won't have passwords (by default) hence wouldn't be able to login (check out /etc/shadow - the second column is the hashed password - * or ! meaning none).

You can restrict who can login anyway with the **AllowUsers **directive in /etc/ssh/ssd_config (restart SSH with /etc/init.d/ssh restart to take effect) and indeed you might even want to set **PermitRootLogin no**.

Mathew

---

### Post by szim90 on 2006-11-24
Thank you again for you help.


Sean

---

### Post by tturrisi on 2006-11-24
I config my /etc/ssh/sshd.conf to listen on port 3022 and forward 3022 via via the router.  Script kiddies & would be crackers, like most criminal mided folk, are usually lazy and only scan common ports.  3022 won't get looked for in most scans, even if use nMap.  You'd have to specifically target an uncommon port like 3022, thus your log will show little to no break in attempts.

---

### Post by MJN on 2006-11-25
No need for that approach - to continue my door analogy (always dangerous!) that's like putting the front door round the side... It can cause inconvenience to both myself and my users so it's an unacceptable step to take.

Furthermore, there's no need - if you've got strong passwords then it's simply not an issue. Period.

The main reason I installed Denyhosts was curiosity and desire to learn more about the topic - it's not a necessity given my passwords are strong.

The bottom line is don't rely on security through obscurity as one day you'll come a cropper, or at the very least you won't have that option that you're so used to choosing.

Mathew

---

### Post by tturrisi on 2006-11-25
Yes, I understand that.  On a real production server I would not change default ports, but for a home server it's a good idea, if only to obscure the detection of an existing network to would be burglers.  It's just another layer of security.

Granted, no network is really "stealthed" per those hyped up online security scanners like ShieldsUp at grc,com.  But the majority of folks who do net scans will scan for common ports and don't even know how to use nMap, so they will not realize a comp exists at the "stealthed' ip.

Strong passwords are a MUST on any comp, home or production.  My point is this, on a home server, if use default ports then you invite onlookers, and then the only safeguard is a password of 10 characters minimum that uses lower case, upper case, numbers & special characters, else in a short while a weak password can be cracked.  This is not really an issue w/ ssh due to the encryption and the fact that ssh passwords are not transmitted in plain text like ftp or pop.

All I'm saying is if you don't want to see port probes in your logs, change to an uncommon port.

---

