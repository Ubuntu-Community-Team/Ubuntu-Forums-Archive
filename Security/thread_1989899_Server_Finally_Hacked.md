---
title: "Server Finally Hacked"
date: 2012-05-29
forum: Security
---

### Post by starz677 on 2012-05-29
Ubuntu 10.04
Standard install with GUI
Setup as LAMP server

Hello,

I do believe my server finally got hacked, or at least I finally found evidence.

The evidence came from the Fail2ban Jail.conf file

An unknown IP address had apparently been added to the Ignore list on each of the jail configurations.

I have one other IP address there and that was a local IP address.

My passwords were complex and I blocked all countries other than the US and even all the proxy server I could find.

Updates were up to date.

What was the likely vector they used to gain access?

SSH is disabled and there is no remote access configured.

Thx

---

### Post by prshah on 2012-05-29
> **starz677 said:**
> An unknown IP address had apparently been added to the Ignore list on each of the jail configurations.

As a start, why don't you check which area the IP address belongs to? You can check it using (for example) [www.ip2location.com](www.ip2location.com)

Of course, that's assuming it's a public ip address and not an internal one (Eg 10.0.0.1, etc)

---

### Post by Ms. Daisy on 2012-05-29
Agree with prshah.  **POST** the evidence and we may be able to actually help.

---

### Post by starz677 on 2012-05-30
Hi,

I have the physical address where the IP address was assigned or used, the ISP, the date and time and other information..   However, that won't rule out proxy use, hijacked PC's or other vectors that would render that info useless.
Someone wanted to stop fail2ban from blocking their hacking so they edited the file manually.

It's not a guess.

The server was hacked.  I should not have said "I believe".

**Fact:** No OS is hack proof.  Admin experience makes the job harder for hackers.  But never impossible.


Thanks for the offer of help, but as I investigate this more, that would be an exercise in futility.   The time would be better spent starting over and trying to sharpen my skills to make the new build less vulnerable.  I wish I was savvy enough to install a vanilla Ubuntu server but I lack the skills to do everything from the command line and I need GUI's.

---

### Post by starz677 on 2012-05-30
Here is one of the IP addresses that appears to be involved....

90.199.29.86

5ac71d56.bb.sky.com
.
.
.
.

---

### Post by cariboo on 2012-05-30
The IP address you provided proves nothing. How do you know someone edited the fail2ban configuration file? Was there a none route-able private ip address inserted into the file?

What other indication do you have that your server has been cracked?

---

### Post by Ms. Daisy on 2012-05-30
OK, so you're looking to harden the new installation now, correct?  We need information to help with that.

What security measures did you have in place in the last installation?  What services are you running on it? What services are facing the internet?

BTW, no time like the present to learn how to use the command line.

---

### Post by prshah on 2012-05-31
Of course finding an IP address and ISP does not rule out proxy, etc, but it's a starting point. Given that the IP address was "unblocked" in the fail2ban conf file indicates confidence that this ip address may be used again, probably indicating a static ip.

Most static ip's can then be [s]traced to[/s] used to trace their parent source, and an email to webmaster or administrative contact can alert them to misuse if any.

Can you also check the "/var/log/auth.log" (or auth.log.1, .2.gz, .3.gz...) at about the time you believe the server was hacked? It may indicate the entry point that you are looking for. 

I don't think there is any entry point that bypasses auth.log; if you can't find something suitable in auth.log, maybe you need to look at your local system for some rouge programs or "user error" / social engineering.

Suggestions only. I'm by no means a security or server expert.

---

### Post by starz677 on 2012-06-01
> **cariboo907 said:**
> The IP address you provided proves nothing. How do you know someone edited the fail2ban configuration file? Was there a none route-able private ip address inserted into the file?

What other indication do you have that your server has been cracked?

 I want to make sure I understand you crystal clear. You say that the clear and indisputable alteration of a fail2ban configuration file and the addition of an IP address into that file which I never added is not evidence of hacking?  Explain that please.  I think it makes absolutely no difference what External IP address was added (but for the record, it was a static IP address in a nearby state).  I was able to identify the domain location and even a physical address.  However, it is also possible that that IP address at the time was being used as a proxy and was not the ORIGIN of the attack.

---

### Post by starz677 on 2012-06-01
> **Ms. Daisy said:**
> OK, so you're looking to harden the new installation now, correct?  We need information to help with that.

What security measures did you have in place in the last installation?  What services are you running on it? What services are facing the internet?

BTW, no time like the present to learn how to use the command line.

 How I would love to.  I can use the command line (to some degree) and what I dont know I can find, but an even bigger issue to me is how to monitor a headless server for malicious activity.  On my desktop server I can watch ipblock as it blocks domains and I can see the domain name.  with one click I can see any IP addresses tagged by fail2ban.  I can use etherape to see a graphical real time representation of the bandwitdth being used by a connection....  How would I do all that on a headless server?  thx

---

### Post by starz677 on 2012-06-01
> **prshah said:**
> Of course finding an IP address and ISP does not rule out proxy, etc, but it's a starting point. Given that the IP address was &quot;unblocked&quot; in the fail2ban conf file indicates confidence that this ip address may be used again, probably indicating a static ip.

Most static ip's can then be [s]traced to[/s] used to trace their parent source, and an email to webmaster or administrative contact can alert them to misuse if any.

Can you also check the &quot;/var/log/auth.log&quot; (or auth.log.1, .2.gz, .3.gz...) at about the time you believe the server was hacked? It may indicate the entry point that you are looking for. 

I don't think there is any entry point that bypasses auth.log; if you can't find something suitable in auth.log, maybe you need to look at your local system for some rouge programs or &quot;user error&quot; / social engineering.

Suggestions only. I'm by no means a security or server expert.

 Excellent.  thx Could the hacker be able to delete sections of logs in order to cover his or her tracks?  I would swear that blocks of logs have been deleted over the last few months but it never made sense to me....until  a few days ago.

---

### Post by lisati on 2012-06-01
> **starz677 said:**
> I want to make sure I understand you crystal clear. You say that the clear and indisputable alteration of a fail2ban configuration file and the addition of an IP address into that file which I never added is not evidence of hacking?  Explain that please.  I think it makes absolutely no difference what External IP address was added (but for the record, it was a static IP address in a nearby state).  I was able to identify the domain location and even a physical address.  However, it is also possible that that IP address at the time was being used as a proxy and was not the ORIGIN of the attack.

Being able to correctly identify the real address associated with an IP address without a subpoena is highly unusual but not completely impossible. 

I think that what the others who have posted in this thread would like to see is whatever relevant information you are comfortable sharing from your system logs and other files that might support your case, taking care to obfuscate details that could be misused by rogues who might see this thread.

---

### Post by Soul-Sing on 2012-06-01
I have seen nothing but an ip address. But you don't show the context. (log files) hammering ip's, netfilter activity. Please get yourself involved into monitoring your server, thats the most important task that lays in front of you, using a server. For now, I have seen no evidence that your server is compromised.....

---

### Post by CharlesA on 2012-06-01
Just wanted to +1 that.

Read the links in Ms. Daisy's sig and go from there.

I don't see any evidence the machine is compromised.

---

### Post by starz677 on 2012-06-01
Noone has answered the most basic question here or addressed the most obvious evidence.

**Can at least one person offer a reasonable explanation as to how then a fail2ban configuration file got edited without my knowledge and an IP address got added that was identified as valid and was never entered by anyone authorized to do so?**

It seems that indisputable evidence is simply being ignored here.

If someone could just answer that one question I might feel better about this.
Trust me, I would rest better tonight if I had doubts that my server was hacked.
But Really.  I have yet to get a reasonable explanation on this.  Perhaps there is yet another Ubuntu / Linux fact I need to become aware of?  I have never seen a fail2ban configuration file edit itself to exempt IP addresses of remote hosts.
I cannot see how 1 + 1 will ever not equal 2 yet that seems to be the going assertion here.  :confused:

thx for everyone's patience in helping an obviously unskilled admin :p

---

### Post by starz677 on 2012-06-01
> **leoquant said:**
> I have seen nothing but an ip address. But you don't show the context. (log files) hammering ip's, netfilter activity. Please get yourself involved into monitoring your server, thats the most important task that lies in front of you, using a server. For now, I have seen no evidence that your server is compromised.....

No problem.  Thank you for your time.
Perhaps someone else will.

Good day.

---

### Post by starz677 on 2012-06-01
> **CharlesA said:**
> Just wanted to +1 that.

Read the links in Ms. Daisy's sig and go from there.

I don't see any evidence the machine is compromised.

Charles, I'm not doubting your expertise and I appreciate your responses but the process of learning sometimes requires questioning the teacher  :)
I did look through the links in Ms. Daisy's sig,

One of the main oversights a few here seems to have when asking for "evidence" is that you have not considered that a really good hacker could (if they gained sufficient access and rights) delete all or portions of the logs to hide their activity.

In fact, wouldn't a thorough hack be incomplete without doing just that?   What good hacker is going to leave evidence of their handy work to be easily discovered?   And the first thing a hacker would do (imho) would be to manipulate the logs to remove evidence.

That is one of the symptoms I mentioned.  Over the last few months, I had suspected parts of my logs were missing.  My logs seemed to get spontaneously rotated at times not scheduled.  Then I would look through the logs and often times, the time period when I though hacking might have occurred would not be there, which was VERY frustrating.

Sometimes my server would spontaneously shut down and I would come back into the server room and to my surprise it would be off.
I suspected these might be after kernel manipulation which required re-booting to write them to memory.  Just a guess if we accept the idea that the server was indeed compromised.

**It is often not as easy as some here suggest to locate hacking evidence.**

That is why there are forensic tools such as Snort.

Is this not correct?

Thx again

---

### Post by CharlesA on 2012-06-01
Check the logs and see if there are any missing time/dates. auth.log in particular.

[https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned)

---

### Post by prshah on 2012-06-02
> **starz677 said:**
> Could the hacker be able to delete sections of logs in order to cover his or her tracks?

Yes, of course. The log files are editable with sudo access, just like any other.

As to your question about how a "hacker" managed to add an ip address to your fail2ban conf file, we need more information about your setup.

For example (no specifics), do you access the server via ssh?  FTP? Telnet (shudder!)? HTTP (Control panel / config panel)? SSH uses password-less (key file) authentication or passworded authentication?

Another point you should check is your ~/.ssh/ directory. If you have passwordless authentication, it is childs play for a hacker to add authentication credentials to your "authorized_keys" file. Alternately, he could have created another user and kept the auth cred in THAT user's home dir.

Please use the AllowUsers config directive in your /etc/sshd_config file to prevent unknown users from gaining access to your server via SSH. (man sshd_config will give information on syntax and more options).

Keep in mind that this is possible only IF the hacker has actually gained access to your computer.

As an amatuer admin, I can't really say how an ip has been added to your fail2ban conf, but some background info may help someone point out a vulnerability in your server.

---

### Post by Ms. Daisy on 2012-06-02
> **starz677 said:**
> [B]Can at least one person offer a reasonable explanation as to how then a fail2ban configuration file got edited without my knowledge and an IP address got added that was identified as valid and was never entered by anyone authorized to do so?

[/B]**...It is often not as easy as some here suggest to locate hacking evidence.**
We're going in circles here. Everyone is asking you for more information about your server and you keep giving us conversations about what you think might have happened.  Maybe an expert could look at what you've given us and know what happened, but I can't.

I guess I'll ask one more time, can you please copy & paste some of the evidence that you're seeing?  Look at the [Did I Just Get Owned Wiki]("https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned")  for the types of things that we want to see.  If there are chunks of  logs missing, then explain how you're viewing the logs and what time  chunks are missing.

Alternatively, if you have decided that the server got hacked then you should reinstall and restore your data from your backups.  Then make sure you 're doing everything you can to secure the new server by at least reading the security sticky.

---

### Post by Hungry Man on 2012-06-02
Assume you've been hacked, don't assume to know how. Wipe and reset everything and just lock down the entire system this time.

---

### Post by nothingspecial on 2012-06-02
[IMG]http://img402.imageshack.us/img402/6242/220pxouroborossimplesvg.png[/IMG]

---

### Post by The Cog on 2012-06-02
I agree with Hungry Man. An unexpexted entry in a white list, and chunks missing from log files both point towards unauthorised meddling. Even if you did post the evidence (and you seem not to want to), probably the best we could do is to agree that it looks like you've been got at. I doubt we could work out how it was done if the logs have been edited. Your best bet is to wipe and reinstall, and re-double your efforts to secure the server next time. 

I have heard of a program called tripwire that might help detect unauthorised access, but haven't looked at it myself. It's also possible to set up logging to a separate server, and a server that only accepts syslog messages should be quite easy to secure even more, such that your log information can't be deleted next time.

---

