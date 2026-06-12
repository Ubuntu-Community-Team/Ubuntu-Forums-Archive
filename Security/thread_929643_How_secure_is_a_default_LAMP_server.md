---
title: "How secure is a default LAMP server"
date: 2008-09-25
forum: Security
---

### Post by /////// on 2008-09-25
After playing around a bit with a LAMP server which I recently set up, I decided to host it onto the internet. How secure is the default LAMP server setup and is it possible for other people to use the server to get to my computer and others on the network? Is there anything I can do to make ther server more secure?

---

### Post by cdenley on 2008-09-25
> **/////// said:**
> After playing around a bit with a LAMP server which I recently set up, I decided to host it onto the internet. How secure is the default LAMP server setup and is it possible for other people to use the server to get to my computer and others on the network? Is there anything I can do to make ther server more secure?

Ubuntu's default LAMP configuration allows anonymous web users to gain root terminal access. Just joking, but why wouldn't it be secure? The safest computer is one with no server, but a default LAMP configuration is secure as far as LAMP servers go. What's more important is how you use/configure the LAMP server.

---

### Post by AgainstTheDarkArts on 2008-09-25
> Ubuntu's default LAMP configuration allows anonymous web users to gain root terminal access. Just joking,:lolflag:


I was wondering the same thing. Are the default settings secure enough to be used by someone who is still learning Linux?  I don't have anything on that system that I can't lose (it's a practice server), but am I exposing others through my ignorance?

I'd hate to find out that someone has installed a spam server on my system before I learned how to get it locked down correctly.

(I know enough to use strong passwords, and never log in as root)

---

### Post by stmurray on 2008-09-25
Just be careful about what content you are hosting.  Once you start adding sites and putting dynamic pages (for example, php scripts) and accepting user input, etc, it can be easy to create a vulnerability that can be exploited.

---

### Post by BlackAura on 2008-09-25
It's pretty much OK. There are a few options that could do with being turned off, but otherwise the defaults are pretty sensible.

You're much more likely to have security problems with a PHP app installed in the webserver than the server itself.

I would suggest a firewall at least - block anything other than the HTTP port (port 80). If you have something like SSH running, and that's open to the internet, chances are a bot will find it and try to break in by guessing your user's password. Potentially the same problem with file sharing, or any other service running on that machine. If you don't want it open to the internet, block it.

---

### Post by redgsturbo on 2008-09-25
> **stmurray said:**
> Just be careful about what content you are hosting.  Once you start adding sites and putting dynamic pages (for example, php scripts) and accepting user input, etc, it can be easy to create a vulnerability that can be exploited.

key phrase "accepting user input"

---

### Post by redgsturbo on 2008-09-25
> **BlackAura said:**
> It's pretty much OK. There are a few options that could do with being turned off, but otherwise the defaults are pretty sensible.

You're much more likely to have security problems with a PHP app installed in the webserver than the server itself.

I would suggest a firewall at least - block anything other than the HTTP port (port 80). If you have something like SSH running, and that's open to the internet, chances are a bot will find it and try to break in by guessing your user's password. Potentially the same problem with file sharing, or any other service running on that machine. If you don't want it open to the internet, block it.

I take it a step further, blocking what I know I don't want, and snorting-inline any traffic I *think* I do and dropping if its nasty

---

### Post by beniji on 2008-09-27
Last time I checked the default installation doesn't have a firewall which is a no-no for a server if it has a public interface.

IMHO the default install should be tightened up - it should not have mod_cgi enabled for example and should set Apache servertokens to prod and serversignature off etc, plus I've been hacked before because of the dumb *default* user setup having www-data with a valid shell in /etc/passwd. People will tell you that the user shell setting does not matter as the shadow wildcard entry should be honoured but they are sadly wrong - there is still buggy code out there (e.g. feisty proftpd) that under some circumstances will allow www-data to login.

I'd like to see the default apache homepage being tidied up, indexes off etc and maybe by default setup with basic auth. Who really wants to setup a new webserver and have it all live and public immediately?

The default php.ini could be a bit tighter too...

---

### Post by cdenley on 2008-09-27
> **beniji said:**
> Last time I checked the default installation doesn't have a firewall which is a no-no for a server if it has a public interface.

IMHO the default install should be tightened up - it should not have mod_cgi enabled for example and should set Apache servertokens to prod and serversignature off etc, plus I've been hacked before because of the dumb *default* user setup having www-data with a valid shell in /etc/passwd. People will tell you that the user shell setting does not matter as the shadow wildcard entry should be honoured but they are sadly wrong - there is still buggy code out there (e.g. feisty proftpd) that under some circumstances will allow www-data to login.

I'd like to see the default apache homepage being tidied up, indexes off etc and maybe by default setup with basic auth. Who really wants to setup a new webserver and have it all live and public immediately?

The default php.ini could be a bit tighter too...

What would a firewall accomplish? Apache is supposed to listen on the public interface. Mysql does not listen on the public interface by default.

Why would you have the server live if it isn't set up? I guess some people might not use a LAN, and have the server connected directly to the internet. That's what a development server is for, though. Most users would want to verify their server is working before they begin configuring it.

Apparently, taking away www-data's shell would break some maintainer scripts.
[https://bugs.launchpad.net/ubuntu/+source/base-passwd/+bug/216813](https://bugs.launchpad.net/ubuntu/+source/base-passwd/+bug/216813)
It sounds like you got hacked because of an FTP misconfiguration, not because of the default LAMP server.

How could the default homepage be tidied up? It consists of one file.
```

<html><body><h1>It works!</h1></body></html>

```
I can't see how that can be a security risk.

I guess disabling options and modules you don't need couldn't hurt, but probably wouldn't really give you any security advantages on a default configuration. I don't think the original poster needs to be concerned if remote users can identify the version of apache he's running.

---

### Post by beniji on 2008-10-05
@cdenley

I dont think I really need to argue the benefits of a firewall for a LAMP server. There are plenty of server packages which listen on all interfaces by default in Debian/Ubuntu not to mention making the kernel's TCP stack open to invalid packet fingerprinting etc.

"I guess some people might not use a LAN, and have the server connected directly to the internet." 

That is the case I am talking about which is presumably why the original poster asked the question. If he was setting up a dev server behind a NAT router he wouldn't care much. It's relevant for ISPs and also e.g. customers setting up new colo boxes which are being powered up for the first time with their public interface on so they can pick up repo security updates etc.

"taking away www-data's shell would break some maintainer scripts."
Can you point me to any such scripts? The link does not mention any. IMHO it's an unnecessary risk having the main system user repository having live login shells active. To compare the default FreeBSD install has this /etc/passwd:

root:*:0:0:Ben:/root:/usr/local/bin/bash
toor:*:0:0:Bourne-again Superuser:/root:
daemon:*:1:1:Owner of many system processes:/root:/usr/sbin/nologin
operator:*:2:5:System &:/:/usr/sbin/nologin
bin:*:3:7:Binaries Commands and Source:/:/usr/sbin/nologin
tty:*:4:65533:Tty Sandbox:/:/usr/sbin/nologin
kmem:*:5:65533:KMem Sandbox:/:/usr/sbin/nologin
games:*:7:13:Games pseudo-user:/usr/games:/usr/sbin/nologin
news:*:8:8:News Subsystem:/:/usr/sbin/nologin
man:*:9:9:Mister Man Pages:/usr/share/man:/usr/sbin/nologin
sshd:*:22:22:Secure Shell Daemon:/var/empty:/usr/sbin/nologin
smmsp:*:25:25:Sendmail Submission User:/var/spool/clientmqueue:/usr/sbin/nologin
mailnull:*:26:26:Sendmail Default User:/var/spool/mqueue:/usr/sbin/nologin
bind:*:53:53:Bind Sandbox:/:/usr/sbin/nologin
proxy:*:62:62:Packet Filter pseudo-user:/nonexistent:/usr/sbin/nologin
_pflogd:*:64:64:pflogd privsep user:/var/empty:/usr/sbin/nologin
_dhcp:*:65:65:dhcp programs:/var/empty:/usr/sbin/nologin
uucp:*:66:66:UUCP pseudo-user:/var/spool/uucppublic:/usr/local/libexec/uucp/uucico
pop:*:68:6:Post Office Owner:/nonexistent:/usr/sbin/nologin
www:*:80:80:World Wide Web Owner:/nonexistent:/usr/sbin/nologin
nobody:*:65534:65534:Unprivileged user:/nonexistent:/usr/sbin/nologin


"sounds like you got hacked because of an FTP misconfiguration"
Nope. My configuration was fine. Got hacked due to an old bug in proftpd which was fixed in Debian but not in Ubuntu (and still isn't).


"disabling options and modules you don't need couldn't hurt, but probably wouldn't really give you any security advantages on a default configuration"

Any basic security text book would tell you otherwise. Never run what you dont need, especially on a server. 

"remote users can identify the version of apache he's running"

When a vulnerability occurs in httpd x.y.z the script kiddies often only bother to look at their scans for that version rather than try and deduce the version from further probes (which may or may not be possible).

---

### Post by cdenley on 2008-10-05
> **beniji said:**
> @cdenley

I dont think I really need to argue the benefits of a firewall for a LAMP server. There are plenty of server packages which listen on all interfaces by default in Debian/Ubuntu not to mention making the kernel's TCP stack open to invalid packet fingerprinting etc.

"I guess some people might not use a LAN, and have the server connected directly to the internet." 

That is the case I am talking about which is presumably why the original poster asked the question. If he was setting up a dev server behind a NAT router he wouldn't care much. It's relevant for ISPs and also e.g. customers setting up new colo boxes which are being powered up for the first time with their public interface on so they can pick up repo security updates etc.

"taking away www-data's shell would break some maintainer scripts."
Can you point me to any such scripts? The link does not mention any. IMHO it's an unnecessary risk having the main system user repository having live login shells active. To compare the default FreeBSD install has this /etc/passwd:

root:*:0:0:Ben:/root:/usr/local/bin/bash
toor:*:0:0:Bourne-again Superuser:/root:
daemon:*:1:1:Owner of many system processes:/root:/usr/sbin/nologin
operator:*:2:5:System &:/:/usr/sbin/nologin
bin:*:3:7:Binaries Commands and Source:/:/usr/sbin/nologin
tty:*:4:65533:Tty Sandbox:/:/usr/sbin/nologin
kmem:*:5:65533:KMem Sandbox:/:/usr/sbin/nologin
games:*:7:13:Games pseudo-user:/usr/games:/usr/sbin/nologin
news:*:8:8:News Subsystem:/:/usr/sbin/nologin
man:*:9:9:Mister Man Pages:/usr/share/man:/usr/sbin/nologin
sshd:*:22:22:Secure Shell Daemon:/var/empty:/usr/sbin/nologin
smmsp:*:25:25:Sendmail Submission User:/var/spool/clientmqueue:/usr/sbin/nologin
mailnull:*:26:26:Sendmail Default User:/var/spool/mqueue:/usr/sbin/nologin
bind:*:53:53:Bind Sandbox:/:/usr/sbin/nologin
proxy:*:62:62:Packet Filter pseudo-user:/nonexistent:/usr/sbin/nologin
_pflogd:*:64:64:pflogd privsep user:/var/empty:/usr/sbin/nologin
_dhcp:*:65:65:dhcp programs:/var/empty:/usr/sbin/nologin
uucp:*:66:66:UUCP pseudo-user:/var/spool/uucppublic:/usr/local/libexec/uucp/uucico
pop:*:68:6:Post Office Owner:/nonexistent:/usr/sbin/nologin
www:*:80:80:World Wide Web Owner:/nonexistent:/usr/sbin/nologin
nobody:*:65534:65534:Unprivileged user:/nonexistent:/usr/sbin/nologin


"sounds like you got hacked because of an FTP misconfiguration"
Nope. My configuration was fine. Got hacked due to an old bug in proftpd which was fixed in Debian but not in Ubuntu (and still isn't).


"disabling options and modules you don't need couldn't hurt, but probably wouldn't really give you any security advantages on a default configuration"

Any basic security text book would tell you otherwise. Never run what you dont need, especially on a server. 

"remote users can identify the version of apache he's running"

When a vulnerability occurs in httpd x.y.z the script kiddies often only bother to look at their scans for that version rather than try and deduce the version from further probes (which may or may not be possible).

A LAMP server is supposed to be accessible from the internet. In what typical scenario would a firewall provide any advantage? For a default LAMP configuration, apache should listen to all interfaces. Mysql does not listen to all interfaces. How would a firewall benefit the original poster? If someone had some specialized requirements like blocking certain addresses, then a firewall may be useful. For a typical setup, it would just be an unnecessary complication.

I guess if, hypothetically, there was a vulnerability in the version of apache included on the installation disc, then it would make sense to have apache disabled by default, or filtered. However, at that point, why bother installing any servers during the system install? You can always install LAMP after you install your updates. The original poster already has the LAMP server running, though. I don't think there are too many exploits for apache which can be exploited using the default configuration with only the "it works" page.

About the www-data shell, I can't point you to any such scripts, but maybe you should ask in the bug report since Colin Watson seems to know more about it than me. Can you post a link to the bug report for the bug you are referring to? Does it affect a default configuration? The original poster didn't mention anything about FTP, but if he runs an FTP server and there is actually a bug in proftpd in hardy, then you make a good point.

I definitely agree that the most secure way you could go is to disable anything unnecessary, but I don't think that is where the original poster should focus his efforts. I would be 100 times more concerned with what scripts he serves with his LAMP server than whether attackers can identify which version of apache he is running. Suggesting tasks such as that to new users would only serve as a distraction from the big picture.

Have you ever run OpenBSD? That sounds more like your type of OS. The original poster should stick with ubuntu, though.

---

