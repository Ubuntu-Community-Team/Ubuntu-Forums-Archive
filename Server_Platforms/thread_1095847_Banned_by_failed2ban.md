---
title: "Banned by failed2ban"
date: 2009-03-14
forum: Server Platforms
---

### Post by mistypotato on 2009-03-14
Good morning!

What do hackers see after they've been banned by fail2ban if they try to connect again?

Do they get a message saying they've been banned or do they simply get a blank screen?

thx

---

### Post by rebugger on 2009-03-14
Why dont you try it?

In short: it won't let you connect ;) thats it. No message, no "black screen" - simply no response.

---

### Post by mistypotato on 2009-03-15
I have it installed on both my servers and was curious as to what the hacker on the other side saw after being banned.

I see several bans per day.

I might try it if I knew how to "unban" myself afterward.

---

### Post by darksideforge on 2009-03-15
From what I understand from reading fail2ban's website, it looks like there's a predetermined jail time unless you've set it to permanent lockout. I may have been reading it wrong though. Here's what I'm seeing:

> **Filters**

*The directory filter.d contains mainly regular expressions which are used to detect break-in attempts, password failures, etc. Here is an example for filter.d/sshd.conf with 3 possible regular expressions to match the lines of the logfile:* 

```
failregex = Authentication failure for .* from <HOST>
            Failed [-/\w]+ for .* from <HOST>
            ROOT LOGIN REFUSED .* FROM <HOST>
            [iI](?:llegal|nvalid) user .* from <HOST>

```

> In the above example the default regex has been changed to allow the absence of user in a line such as: 

```
Jan 10 07:02:37 homebrou sshd[18419]: Failed password for root from 222.76.213.151 port 55236 ssh2
```

> *If you're creating your own failregex expressions, here are some things you should know:*

    * A failregex can have multiple lines, any one of which may match a line of the log file. 

    * In every line of failregex, the part that matches the host name or IP address must be wrapped in a (?P<host> ... ) sandwich. This is a Python-specific regex extension that assigns the contents of the match to the name <host>. The <host> tag is how you tell fail2ban which host was connecting, so it has to be present in every line of failregex. If it's not, fail2ban will issue an error message about "No 'host' group". 

    * As a convenience, you can use the predefined entity <HOST> in your regexes. <HOST> is an alias for (?:::f{4,6}:)?(?P<host>\S+), which matches either a hostname or an IPv4 address (possibly embedded in an IPv6 address). 

    * In the action scripts, the tag <ip> will be replaced by the IP address of the host that was matched in the <host> tag. 

    * In order for a log line to match your failregex, it actually has to match in two parts: the beginning of the line has to match a timestamp pattern or regex, and the remainder of the line has to match your failregex. If the failregex is anchored with a leading ^, then the anchor refers to the start of the remainder of the line, after the timestamp and intervening whitespace. 

    * The pattern or regex to match the time stamp is currently not documented, and not available for users to read or set. See Debian bug #491253. This is a problem if your log has a timestamp format that fail2ban doesn't expect, since it will then fail to match any lines. Because of this, you should test any new failregex against a sample log line, as in the examples below, to be sure that it will match. If fail2ban doesn't recognize your log timestamp, then you have two options: either reconfigure your daemon to log with a timestamp in a more common format, such as in the example log line above; or file a bug report asking to have your timestamp format included. 

I found this information here:
[http://www.fail2ban.org/wiki/index.php/MANUAL_0_8#Jail_Options]("http://www.fail2ban.org/wiki/index.php/MANUAL_0_8#Jail_Options")

---

### Post by mistypotato on 2009-03-16
darkside...that's WAY over my head :P

I was really just curious as to what the person who got banned saw is all :KS

I think rebugger's reply was what I was after.

But you never know, your reply may be JUST what the next person searcing this topic may need :KS:KS

Thanks !

---

