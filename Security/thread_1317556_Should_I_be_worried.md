---
title: "Should I be worried?"
date: 2009-11-06
forum: Security
---

### Post by fela on 2009-11-06
I have port 80 forwarded to the WWW using my router, so that anyone can access the website stored on my home server. Are there any security risks that I should be aware of and take action to prevent, eg MITM attacks, MITB attacks etc? I know quite alot about computers but security is my achilles heel in terms of computer knowledge - I've never administrated a server connected to the WWW before.

Also, would it be a tremendous security risk forwarding the SSH (port 22) port, so that I can access and administrate the server remotely too? I'm just totally not sure what to be careful of really. And what about port 5900 for my desktop (VNC port)? I've heard that doing this sort of thing introduces a whole lot of new stuff that people can exploit.

Thanks a bunch
Fela

---

### Post by wojox on 2009-11-06
I've run Apache for years under Windows and months under Ubuntu and never had problems with anything port forwarding wise. VNC never used, but ssh I changed the default port to something a lot higher, not to be so obvious on those script kiddie scans.

---

### Post by Jive Turkey on 2009-11-06
Worried? No, but there is some work left for you to do if you want to be sure the box is reasonably secure.

Based on the information you posted I would reccomend reading up on how to better secure openssh-server, in addition to whatever www-server (i.e. Apache, lighthttpd).  I would not forward that VNC port, making it accessible outside you LAN unless you *know* you will be using it that day.  Changing your port numbers for SSH & VNC will not stop a determined intruder but will thwart many automated attacks.

Pretty much any listening service can introduce new vulnerabilities.

---

### Post by fela on 2009-11-06
Thanks for the replies, both of you.

I think I might look up on how to change the apache port (which is the web server I choose to use), as well as SSH if I want to get that going. I think I'll leave the VNC for now as that would only be if a friend wanted to access my desktop, and I could probably do it more securely over a VPN now I think of it.

So you reckon changing the port numbers would increase security? I see your point as scripts probably scan for vulnerabilities on standardized ports don't they.

Thanks again.

---

### Post by cariboo on 2009-11-07
I would suggest disabling vnc completely and use x forwarding via ssh. If you search through this sub forum, you will find many users have had there systems cracked via vnc. If your "friend" is doing server/system administration remotely, why not use something like [webmin]("http://www.webmin.com/").

---

### Post by Soul-Sing on 2009-11-07
Why recommend webmin when this software is removed from the off. ubuntu repositories some years ago because of security issue's?
: [https://answers.edge.launchpad.net/ubuntu/+question/2873](https://answers.edge.launchpad.net/ubuntu/+question/2873)
with a linkage to ebox: [https://wiki.ubuntu.com/EboxSpec](https://wiki.ubuntu.com/EboxSpec)

---

### Post by cariboo on 2009-11-07
Just because there is no Debian maintainer for the application, doesn't mean that development has stopped, A new version was released September 17/09.

I find ebox is still lacking some functions, plus they have moved to a complete distribution of their own, meaning you would have to do a complete new installation to use it.

---

### Post by bodhi.zazen on 2009-11-07
VNC is probably the most commonly cracked server on these forums, followed by ssh.

Be sure to use strong passwords, and check the strength of your password with a password (strength) checker.

IMO all you need is ssh, and simply use keys and disable password logins.

See :

[SSH/OpenSSH/Configuring - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring") 

[SSH/OpenSSH/Keys - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") 

Web tools can be an alternate , and there are several to choose from, but if you are managing a single server with only apache (and I presume php + mysql) I doubt you need anything more then ssh.

---

### Post by fela on 2009-11-07
OK, my current setup is SSH over port 2222 and Apache on port 80. I might look into VNC over SSH. Although, VNC would only be a 'cool' thing, ie it would be cool for someone to control my desktop remotely. I don't need it for anything in particular.

---

### Post by Jekshadow on 2009-11-08
VNC over SSH does not really add that many more risks then SSH itself, because if someone can access VNC, then they already have SSH access to your system, and if they have SSH access they can do whatever the cracked user account could do.

---

