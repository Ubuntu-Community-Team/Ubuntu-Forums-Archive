---
title: "firewall Iptables - what is a best way to secure a server?"
date: 2011-07-27
forum: Security
---

### Post by 007casper on 2011-07-27
what is the best option to securing server via firewall and iptables?

ufw status
```

To        Action    From
80/tcp    Allow     Anywhere
Anywhere  Allow     <specific IP>
2222      Allow     <specific IP>

```

is that ok?  or are there better alternatives?

---

### Post by HermanAB on 2011-07-27
Howdy,

You don't need a firewall on a server - assuming that the server is properly managed and is only serving what you intend it to serve.

My servers have only one iptables rule to protect against DOS and brute forcing:
```
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT
```

---

### Post by The Cog on 2011-07-27
Moved to Security Discussions

---

### Post by wacky_sung on 2011-07-27
> **HermanAB said:**
> Howdy,

You don't need a firewall on a server - assuming that the server is properly managed and is only serving what you intend it to serve.

My servers have only one iptables rule to protect against DOS and brute forcing:
```
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT
```

I think you put yourself at a potential risk of a hack. Probably you can post a hyperlink of the website that your server host. Your iptables script can never combat botnets because till this present day there is no 100% solution to resolve DDOS.As long as you run a server, you open doors to attacks.

Just highlight to you that a simple smurf attack can bring down what your script can offer.:guitar:

---

### Post by bodhi.zazen on 2011-07-27
> **007casper said:**
> what is the best option to securing server via firewall and iptables?

ufw status
```

To        Action    From
80/tcp    Allow     Anywhere
Anywhere  Allow     <specific IP>
2222      Allow     <specific IP>

```

is that ok?  or are there better alternatives?

iptables can help, but you sort of need to know how.

If you are running a public server, such as apache, you are going to allow traffic, so a firewall does not help much.

You can put limits as suggested by HermanAB , but those limits again vary by server (IMO). So apache can dish out thousands of requests per second, so limiting an ip to a few hundred connections may be reasonable, but really will not help you against a ddos.

a ssh server is another matter. ssh is likely semi-public and you are better off learning to use AllowUsers in the sshd_config file and using keys rather then iptables.

If you use keys, and disable passwords, IMO it is then secure enough. So again a firewall does not add much.

You can black list IP addresses if you wish, but, ip addresses are easy to obtain so again you are more likely to block legitimate traffic then would be crackers.

Learn to secure your server (apache, php, mysql, ssh, etc) and a firewall is much less important.

The reason firewalls are touted in Windows is that Windows has a number of open, poorly secured ports, so you need to firewall them. This is not the case with Linux.

---

### Post by 007casper on 2011-07-28
I am surprised that firewall is pretty much useless on a server that is open to public.  I guess I am thinking windows.

sorry if this is really a silly question but what about blocking outbound attempts to port 25 in regards to spam, and blocking outbound attempts to port 22.  I changed the ssh port, but does that lock down 22.

I would like to serve the website from port 80 and allow specific IP on any port on the server, and close the rest of the ports to anyone.

---

### Post by The Cog on 2011-07-28
If your server is only listening on ports 22 and 80, then by definition, all other ports are closed. If you move the SSH server from 22 to (say) 22222 then port 22222 opens and 22 closes. A windows server has lots of other open ports that you can't easily do anything about except firewall them, but Ubuntu doesn't behave like that.

Your web server needs to accept connections from everywhere, so a firewall doesn't have anything to do there. Your SSH server only wants to accept connections from one IP address. This could be done by firewall configuration, but could also be done by configuring the SSH server AllowedUsers which can also restrict which users can log in from that address.

Firewalling can limit connection rate and thus control DDOS attacks, but you need to get the limits right to avoid rejecting real users, and since a self-respecting DDOS will simply flood your internet connection I'm not convinced a firewall would help there much either.

As for blocking outgoing connections, firewall configuration can do that, but I'm not convinced of the merit of that. You've already been compromised if your machine is trying to make unwanted outgoing connections.

---

### Post by wacky_sung on 2011-07-28
> **The Cog said:**
> If your server is only listening on ports 22 and 80, then by definition, all other ports are closed. If you move the SSH server from 22 to (say) 22222 then port 22222 opens and 22 closes. A windows server has lots of other open ports that you can't easily do anything about except firewall them, but Ubuntu doesn't behave like that.

Your web server needs to accept connections from everywhere, so a firewall doesn't have anything to do there. Your SSH server only wants to accept connections from one IP address. This could be done by firewall configuration, but could also be done by configuring the SSH server AllowedUsers which can also restrict which users can log in from that address.

Firewalling can limit connection rate and thus control DDOS attacks, but you need to get the limits right to avoid rejecting real users, and since a self-respecting DDOS will simply flood your internet connection I'm not convinced a firewall would help there much either.

As for blocking outgoing connections, firewall configuration can do that, but I'm not convinced of the merit of that. You've already been compromised if your machine is trying to make unwanted outgoing connections.

Why don't you do a experimental with firewall server and non firewall server running the same web applications and configuration open to public and invite crackers to crack it.I can assure you that the non firewall server are more prone to get rooted than a firewall server when vulnerability are found within the web application / configuration. Firewall help to limit and control. When an intrusion has occurred, that's where IDS step in.SElinux, Apparmor, etc help to prevent a buffer overflow for the affected application but it is not a 100% bullet proof solution. That's why web security is a continuous process to counter all those uncover vulnerability.Believe it or not is your choice.

---

### Post by 007casper on 2011-07-28
IDS - from wikipedia
> 
    Noise can severely limit an Intrusion detection system's effectiveness. Bad packets generated from software bugs, corrupt DNS data, and local packets that escaped can create a significantly high false-alarm rate.
    It is not uncommon for the number of real attacks to be far below the false-alarm rate. Real attacks are often so far below the false-alarm rate that they are often missed and ignored.
    Many attacks are geared for specific versions of software that are usually outdated. A constantly changing library of signatures is needed to mitigate threats. Outdated signature databases can leave the IDS vulnerable to new strategies.

good times over there

Then, SElinux, Apparmor. Snort.

I guess I figured maybe there is a global solution through iptables, and firewall.

I really appreciate everyones help.

I knew about apparmor, and snort.  I wasnt aware of the other two.

@wacky_sung - Besides, SElinux, apparmor,and IDS; how would you go about securing your server?  how would you come over the security challenge? I do realize that everybody has a unique set up. There isnt a single solution, or a magic bullet.  I want to have the right tools and gears to minimize the risk of intrusion. So, far nobody passed your acid test ;)

---

### Post by bodhi.zazen on 2011-07-28
> **007casper said:**
> IDS - from wikipedia


good times over there

Then, SElinux, Apparmor. Snort.

I guess I figured maybe there is a global solution through iptables, and firewall.

I really appreciate everyones help.

I knew about apparmor, and snort.  I wasnt aware of the other two.

@wacky_sung - Besides, SElinux, apparmor,and IDS; how would you go about securing your server?  how would you come over the security challenge? I do realize that everybody has a unique set up. There isnt a single solution, or a magic bullet.  I want to have the right tools and gears to minimize the risk of intrusion. So, far nobody passed your acid test ;)

Well, yes this is a problem with any NIDS, false positives.

You as the administrator need to remain diligent. If you are going to ignore snort alerts, or are not willing to follow up (investigate), then do not bother installing snort in the first place.

Yes, HIDS and NIDS use a rule set to detect intrusions, and so are imperfect and can not protect against zero day exploits.

For this we have apparmor and selinux.

None of this is perfect, but that is the best you can do.

In terms of securing your server , what server ? securing apache is not the same as ssh. If it is apache, does that include the rest of the lamp stack ? php ? mysql ?

You need to Google search hardening your various servers.

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

[http://docs.fedoraproject.org/en-US/Fedora/13/html/Security_Guide/](http://docs.fedoraproject.org/en-US/Fedora/13/html/Security_Guide/)

[http://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html](http://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html)

etc

---

### Post by wacky_sung on 2011-07-29
@007casper 
Most servers got hack due to vulnerability being found or wrongly configure server. Every server setup can be difference but the security mindset of how you lay down your network, isolation of each server to prevent total compromise of your whole network if a hack has been intruded. There is no perfect solution but what you can do is damage control.

The newly introduction of cloud system is still ongoing process but it can provide much better security and benefit to the users. There is a potential and it can be fatal if the whole cloud system get compromise.Thus security is a continuous process and we learn from one another.

---

### Post by 007casper on 2011-07-30
>what server? If it is apache, does that include the rest of the lamp stack? php? mysql?
Yes, it does include LAMP.  Installed apps LAMP, nginx, perl, phyton, java, fail2ban and all the dependent apps on ubuntu server set up.

I already covered a good portion of ssh lock down; I should complete it all the way.
[http://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html](http://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html)

I wanted to use snort, but it doesnt seem plug and play.  Then, I figured if I allow apache to be accessible, and allow only one specific IP to access the server, it would be a good start. I guess it doesnt work that way.

I am trying to make a priority list of securing the server.  In the mean time, I will look over the debian 'how to' since it isnt a light read.
> 
- ssh lock down
[http://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html](http://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html)

got fail2ban

- limit DDOS attack (since, the below brute force protection can be brought down, what is the best option?)
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

do I need all, or one would do? Sorry, if it is a stupid question
- Apparmor, SElinux

- IDS

- Snort

any suggestions on priority list.

---

### Post by bodhi.zazen on 2011-07-30
IMO the best way of securing a ssh server is :

1. Use key, disable password authentication.

2. Use the AllowUsers directive in /etc/ssh/sshd_config

You can add a few "simple" rules in iptables if you wish, but #1 is sufficient.

No need to install denyhosts or fail2ban, why add extra services ? Each extra service adds a vulnerability, and, if you secure your ssh server with #1 and perhaps #2 you will be good to go.

---

### Post by 007casper on 2011-08-31
I am using a key for ssh, and disabled password authentication.

I do have AllowUsers directive in etc/ssh/sshd_config

removed fail2ban.

I gathered list of rule sets for iptables.  
[http://ubuntuforums.org/showthread.php?t=1829763](http://ubuntuforums.org/showthread.php?t=1829763)

is there anything should I add to that list?

I figured it is a good practice to use those rule sets.  

Should I turn off my ufw and only use those iptables rules?

The reason why I thought about getting rid of ufw is that... I figure it could cause issues with iptables.  Then, I found out that ufw is a front interface for iptables.  So, figured I can leave it.  Then, found out you can ping ufw.  Can you ping iptables?

Is it a sound plan just to use iptables and get rid of ufw all the way?

---

### Post by bodhi.zazen on 2011-08-31
ufw is nothing more then a tool to configure iptables.

It makes no sense to manually configure iptables and use ufw, use one method or the other.

---

### Post by jramshu on 2011-08-31
Read up on SQL injection and how to secure the db. Read up on XSS and how to prevent it. Those vulnerabilities are very common and tend to be the most exploited.

---

### Post by JKyleOKC on 2011-09-01
> **007casper said:**
> I gathered list of rule sets for iptables.  
[http://ubuntuforums.org/showthread.php?t=1829763](http://ubuntuforums.org/showthread.php?t=1829763)

is there anything should I add to that list?The list as you posted it will do nothing at all but confuse you, since you have commented out each command line and failed to comment the comment lines! If you try to execute it as posted, you'll get the error message "bash: no such command" and it may be repeated once for each line in the script.

The "#" character that you have placed in front of each command line tells the shell that the line is a comment to be skipped over. Unfortunately, that same character is the last character of a root user's prompt, and is often used in how-to postings to indicate that root permission is required for a command. I suspect that's what happened in the sources that you used to compile the list. Just move it from each command line to the comment line(s) that precede it and the script should at least execute without error messages.

As bodhi.zazen has told you, ufw (and gufw) are simply tools to help you configure iptables and it makes no sense to manually configure the rule set and then use one of these tools to replace your set with another one. My own opinion is that these tools are excellent aids for newcomers, because they hide most of the option details built into the filters, but that for that same reason they are NOT suitable for administering a server to be used by the public. It will take some time to learn to write a rule set without such help, but will be well worth it when you've learned since you will be able to tweak the rules as needed to deal with any emergencies that might arise.

---

### Post by bodhi.zazen on 2011-09-01
> **JKyleOKC said:**
> My own opinion is that these tools are excellent aids for newcomers, because they hide most of the option details built into the filters, but that for that same reason they are NOT suitable for administering a server to be used by the public. It will take some time to learn to write a rule set without such help, but will be well worth it when you've learned since you will be able to tweak the rules as needed to deal with any emergencies that might arise.

I would agree with this advice.

The one redeeming quality of ufw is the syntax is very close to the syntax of iptables.

If it is of any assistance, see 

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

I also wrote an overview on LibreOffice I made available [here](bodhizazen.net/IPTables.odt)

If you download that second document it has a number of useful links and I would appreciate feedback, good or bad, as I am probably going to revise the first link adding / revising with info from the second.

Feel free to send a PM on the forms, good or bad.

TYIA

---

