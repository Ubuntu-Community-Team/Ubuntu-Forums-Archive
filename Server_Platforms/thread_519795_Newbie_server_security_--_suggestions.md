---
title: "Newbie server security -- suggestions?"
date: 2007-08-07
forum: Server Platforms
---

### Post by KevinM1 on 2007-08-07
I'm still setting up the server, with an eye towards security.  I've already followed some of the advice I've found in the sticky threads and turned off some of the default options.  Now, I'm looking to harden the kernel itself and protect my server from rootkits.

Since I'm a newbie, I doubt that grsecurity would be a good choice for me.  It looks a bit too untamed for my skill level.  Is AppArmor a good substitute?  I tried viewing their site, but it didn't load, so I hope they're still available.  If not, are there any other decent options out there?  Preferably with a GUI?

The same can be asked for proctection against rootkits.  I know there are a few different options out there, but is there anything newbie friendly?

Are there any other tools you can suggest to me?

Thanks! :)

---

### Post by kidders on 2007-08-08
Hi there,

> **KevinM1 said:**
> The same can be asked for proctection against rootkits.  I know there are a few different options out there, but is there anything newbie friendly?Dealing effectively with rootkits isn't something that lends itself to being newbie-friendly, I'm afraid. Is there some reason why your server is likely to wind up with one?

---

### Post by KevinM1 on 2007-08-09
> **kidders said:**
> Hi there,

Dealing effectively with rootkits isn't something that lends itself to being newbie-friendly, I'm afraid. Is there some reason why your server is likely to wind up with one?

Just trying to cover all sides of potential security breaches.

---

### Post by kidders on 2007-08-09
Hmmm...

Rootkit detection is certainly worth playing around with, but it should be exceptionally difficult to get one onto a well-configured Ubuntu box, so unless you're running something that puts you at particular risk, you needn't be too concerned.

Similarly, kernel hardening isn't often an appropriate road to go down, unless there's a clear need for it. Since you used the word "newbie", you may find it far more productive to concentrate on more ... well ... basic security issues. You see, without at least *some* information about what you're up to, it's hard to offer good advice.

As a basic "for instance", it would almost never be appropriate to talk about kernel hardening on a Ubuntu system that has any software from the universe repository on it, or any S?ID binaries. Similarly, rootkit detection is unlikely to be productive unless you already have a comprehensive logging & auditing regime in place that involves at least one other computer.

I suppose what I'm trying to say is that, given some indication of how high-risk your server is, and what kinds of security precautions you've taken to date, it would be much easier to offer coherent suggestions that would make a real difference.

Sorry if there's nothing in this post that you didn't know already.

---

### Post by KevinM1 on 2007-08-09
> **kidders said:**
> Hmmm...

Rootkit detection is certainly worth playing around with, but it should be exceptionally difficult to get one onto a well-configured Ubuntu box, so unless you're running something that puts you at particular risk, you needn't be too concerned.

Similarly, kernel hardening isn't often an appropriate road to go down, unless there's a clear need for it. Since you used the word "newbie", you may find it far more productive to concentrate on more ... well ... basic security issues. You see, without at least *some* information about what you're up to, it's hard to offer good advice.

As a basic "for instance", it would almost never be appropriate to talk about kernel hardening on a Ubuntu system that has any software from the universe repository on it, or any S?ID binaries. Similarly, rootkit detection is unlikely to be productive unless you already have a comprehensive logging & auditing regime in place that involves at least one other computer.

I suppose what I'm trying to say is that, given some indication of how high-risk your server is, and what kinds of security precautions you've taken to date, it would be much easier to offer coherent suggestions that would make a real difference.

Sorry if there's nothing in this post that you didn't know already.

Actually, your post was pretty informative.  I believe I have been using the universe repository (these are the packages obtained through apt-get, correct?).

I'm currently setting up hosting for a pretty simple PHP e-commerce site.  The site will allow people in my state to buy, sell, and trade their goods.  I estimate that the number of users will be in the 10,000 - 20,000 range (this is based on the first attempt by the site owner, in which he had nearly 10,000 users before his business partner bailed on him).  Payments, from what I understand, will either be handled by PayPal or by the individuals selling/buying the item(s) themselves.  So, no monetary information will be held on the server, just people's contact information, which I realize is still an important thing to protect.  To address that, I'm currently in the process of securing the database.

In terms of other security steps I've taken, I've only turned off the defaults mentioned in a link from one of the stickied threads.  If memory serves, this means FTP and SSH.  After the database is secured, I'm going to turn off the sendmail daemon.

---

### Post by kidders on 2007-08-09
Ahhh... now I'm with you.

Sounds like you're chief point of contact with the outside world will be a web server, so. In that case, it's well worth spending some time tightening up your PHP.

> **KevinM1 said:**
> I believe I have been using the universe repository (these are the packages obtained through apt-get, correct?).Not exactly. There are lots and lots of Ubuntu-compatible software repositories around, all of which tend to work well with apt-get. However, in the case of a security-sensitive commercial server, it is not normally appropriate to install any more than a small subset of the available software ... even if it's from an officially supported repository. For instance...[LIST]
[*]Under absolutely no circumstances should Xorg (and therefore anything that requires it) be installed on such a server.
[*]Nothing should ever be installed *without* using apt-get, unless you know exactly what you're doing.
[*]Of the stuff that *is* available from Ubuntu's official repos, you should make a deliberate effort to avoid anything in the universe & multiverse, because they may not have been subjected to the same degree of testing & patching as the core software.
[/LIST]
The "safe" core set of apps are much more likely to be regularly vetted for vulnerabilities, and be properly patched to work well together.

> **KevinM1 said:**
> I'm currently in the process of securing the database.Since your database won't need to be externally accessible, there's not a whole lot you need to do with it, aside from some good replication & backups. The biggest concern might be ensuring that queries sent to it from your web server are always properly escaped.

> **KevinM1 said:**
> If memory serves, this means FTP and SSH.  After the database is secured, I'm going to turn off the sendmail daemon.SSH can be extremely handy ... quite often it's the only viable means of interaction with a server, short of sitting down in front of the thing. On my boxes, I tend to...
[LIST]
[*]Use my firewall to restrict access to SSH servers to known subnets.
[*]Disable authentication by password.
[*]Completely disable root logins.
[/LIST]
For example, by far the safest way to run remote admin utilities (eg phpmyadmin, etc.) is to access them over SSH tunnels.

Anyhow, once all the basics are tightened up, if you want to take a more aggressive approach to things like intrusion detection, it's time to involve a second PC. Obviously, there's less than no point in installing something like a rootkit detector on the machine you're trying to protect. One of the most effective & reassuring things you can do is to take periodic snapshots of critical system components (eg the contents of /bin), and monitor them for changes. There are plenty of apps around that can do this sort of thing, allowing you to detect many common malicious attacks.

Another basic issue worth mentioning is that, strictly speaking, your server really shouldn't need a firewall to protect itself from the outside world. You should pay special attention to configuring your box as though it didn't have one, and then create a nice, robust set of iptables rules anyway, just to be safe.

The best general advice, I suppose, is not to deviate from the standard approaches to particular issues. For example, you should never loosen file access restrictions unnecessarily, execute things as root when you don't think you should need to, install obscure applications to do the job of a well-known one, and so on. Over extended periods, you see, very minor security issues can combine to create significant problems that are very difficult to detect.

Anyhow, those are just a few random thoughts ... I hope there's something useful in them! I'm not sure if this is quite what you were looking for.

---

### Post by KevinM1 on 2007-08-09
Question regarding root login and executing things as root:

Does this include sudo/gksu?  I know that Ubuntu protects root by forcing users to use those commands, but I've never been sure if that means I'm actually using the root, or just acting as a sort of pseudo-root, in those cases.

Also, can you give me more info regarding iptables?  Is this just a simple white/blacklist database of IP addresses?

Thanks for your responses...I've definitely learned a lot in the past few days between my threads here and e-mails to other people.

EDIT: one more thing -- do you happen to know where sendmail's config file is located?  I can't seem to find it.

---

### Post by kidders on 2007-08-09
> **KevinM1 said:**
> Question regarding root login and executing things as root:

Does this include sudo/gksu?They're essentially the same thing, except that utilities like sudo can impose restrictions on who can use them, how they go about it, and what they can do with them.

When people talk about "root logins", they're not usually talking about sudo/su/etc. The phrase "execute as root" describes any of a variety of ways of allowing a process to acquire root privileges, including...
[LIST]
[*]Logging in as root (which, as you mentioned, is disabled by default in Ubuntu) and executing something.
[*]Using sudo, su, etc.
[*]Running a binary which is set SUID root.
[*]Exercising control over a privileged process with an unprivileged one, much as gizmos like hal let you do on desktop PCs.
[/LIST]

> **KevinM1 said:**
> Also, can you give me more info regarding iptables?  Is this just a simple white/blacklist database of IP addresses?You can treat it that way if you'd like to, although strictly speaking, it's a software router. You can use it to do things like...
[LIST]
[*]Manage NAT, especially in situations where the box it's running on has several network interfaces.
[*]Restrict incoming & outgoing traffic based on almost any criteria available at the IP layer.
[*]Redirect, audit & modify (often called mangling) traffic.
[*]It's involved in other common things like QoS control & is the application that underlies most Linux firewalls.
[/LIST]
You can, as you mentioned, whitelist/blacklist IP addresses (or address ranges) with it ... something many people like to have performed automatically, based on system logs, for example. For the sake of argument, as a web server administrator, you might configure your box to disregard traffic from hosts that attempt to exploit old vulnerabilities in IIS, Apache, or other common web servers.

> **KevinM1 said:**
> Thanks for your responses.No problem. :-) Do post back if there's anything more I can do for you.

> **KevinM1 said:**
> EDIT: one more thingOff the top of my head I couldn't tell you, and unfortunately, my sendmail configurations are probably not the same as yours. :-( See if sendmail's man page gives you any clues. Man pages often have a section called "Files" near the end, where they describe things in your filesystem that an application might be interested in.

Have you installed an SMTP server? (Your previous mention of sendmail puzzled me a little.)

---

### Post by KevinM1 on 2007-08-10
> **kidders said:**
> 
Have you installed an SMTP server? (Your previous mention of sendmail puzzled me a little.)

Sorry for the delay in my response.

Nope, I haven't installed a SMTP server.  I wasn't sure if one came with 7.04, or if I'd have to install one.

EDIT: I forgot -- it doesn't look like I have sendmail as there's no manual (i.e. "man sendmail") for it.  If that's the case, I'm thinking of installing Postfix.  I've heard that's better than sendmail.  It's just a matter of getting PHP5 to work with it.

EDIT2: Another question -- my security book mentions Secure Shell server daemon, but I can't find a sshd_config file.  Instead, it looks like SSH isn't installed as a daemon.  Is the ssh_config file, for all intents and purposes, the same as a sshd_config file?

---

### Post by kidders on 2007-08-10
> **KevinM1 said:**
> Sorry for the delay in my response.Hehe... no worries... it's your thread!

> **KevinM1 said:**
> I haven't installed a SMTP server .... it doesn't look like I have sendmail as there's no manual (i.e. "man sendmail") for it.You're right ... quite often, no man page means no application, but there are a few better ways to check...[LIST]
[*]locate -b sendmail
[*]whereis sendmail
[*]which sendmail
[*]apropos sendmail
[*]dpkg --get-selections | grep sendmail[/LIST]Postfix, which doesn't come pre-installed, includes a sendmail binary ... but you shouldn't install Postfix unless you want a full-blown SMTP server.

In security terms, SMTP servers deserve careful, methodical scrutiny. So much as a misplaced comma or a missing line in your mail server configuration can leave you open to all sorts of attacks, including the nightmare scenario, where your box is exploited as a means of damaging other peoples' computers. Having said that, Postfix is a very well-respected, industrially scalable application, so it's a good choice.

> **KevinM1 said:**
> Another question --Often, you'll find that the addition of a 'd' (for daemon) implies "server" ... for example "smtp" vs "smtpd" or "telnet" vs "telnetd". You may have an SSH client installed, but no SSH *server*. Try **apt-get install openssh-server**, if you'd like one.

If you do install one, it is absolutely critical that you enforce strict username and password guidelines on your box, and only enable logins for accounts that represent actual people (as distinct from accounts like "root", "avahi", "www-data", etc.).

I imagine your security books probably mention SSH servers in the context of tunnelling ... something which is tremendously useful in security-sensitive environments.

---

### Post by KevinM1 on 2007-08-10
> **kidders said:**
> Postfix, which doesn't come pre-installed, includes a sendmail binary ... but you shouldn't install Postfix unless you want a full-blown SMTP server.

In security terms, SMTP servers deserve careful, methodical scrutiny. So much as a misplaced comma or a missing line in your mail server configuration can leave you open to all sorts of attacks, including the nightmare scenario, where your box is exploited as a means of damaging other peoples' computers. Having said that, Postfix is a very well-respected, industrially scalable application, so it's a good choice.

Good to know.  That'll probably be the last part of this I deal with.

> Often, you'll find that the addition of a 'd' (for daemon) implies "server" ... for example "smtp" vs "smtpd" or "telnet" vs "telnetd". You may have an SSH client installed, but no SSH *server*. Try **apt-get install openssh-server**, if you'd like one.

If you do install one, it is absolutely critical that you enforce strict username and password guidelines on your box, and only enable logins for accounts that represent actual people (as distinct from accounts like "root", "avahi", "www-data", etc.).

That's where **AllowGroups** comes in, correct?  Is there a terminal command that will give me a list of user accounts?  I believe there's only one account on here, but I'd like to double-check.

Also, my book states to set **PermitRootLogin** to no.  Would this setting change not allow me to remote into the server?

> I imagine your security books probably mention SSH servers in the context of tunnelling ... something which is tremendously useful in security-sensitive environments.

Yup, it recommends tunneling to the MySQL server.

---

### Post by kidders on 2007-08-10
> **KevinM1 said:**
> Also, my book states to set **PermitRootLogin** to no.  Would this setting change not allow me to remote into the server?It's worth setting that option, despite the fact that root shouldn't be able to log in anyway, due to the default account restrictions on your box ... just to be doubly sure. Once you're organised, you should also disable authentication by password, imo.

> **KevinM1 said:**
> Yup, it recommends tunneling to the MySQL server.That is vital under either of the following circumstances...[LIST]
[*]The applications accessing your database server are not on the same *machine* as your database server, and you can't trust your local network.
[*]The applications accessing your database server are not on the same *network* as your database server.[/LIST]If neither is the case, then SSH tunnelling is often unnecessary ... or even unwise! If you're unsure about anything, I'd be glad to try to help.

Returning to Postfix for a moment, please don't put off securing it for too long hehe. You should not leave it exposed to the outside world for any more than about 30-60 mins in total, unless you're sure it's safe.


Oops... almost forgot...

> **KevinM1 said:**
> That's where **AllowGroups** comes in, correct? Is there a terminal command that will give me a list of user accounts? I believe there's only one account on here, but I'd like to double-check."AllowGroups" isn't used that often in my experience, but feel free to set it. If you wanted, you could create an "sshusers" group of some sort, and use "AllowGroups" or "DenyGroups" to limit access to its members. By and large, people find it unnecessary to do so though.

The easiest way to get a user list is to look in /etc/passwd. The file format goes something like this...```
[COLOR=DimGray]username[/COLOR]**:x:**[COLOR=DimGray]UID[/COLOR]**:**[COLOR=DimGray]GID[/COLOR]**:**[COLOR=DimGray]Additional Info Here[/COLOR]**:**[COLOR=DimGray]home[/COLOR]**:**[COLOR=DimGray]shell[/COLOR]
```In order to log in normally, a user needs at least a password (the ":x:" in /etc/passwd lines tells you to look in /etc/shadow for a password) and a reasonable shell.

This thread is getting really random lol ... I hope you don't mind!

---

### Post by KevinM1 on 2007-08-10
> **kidders said:**
> It's worth setting that option, despite the fact that root shouldn't be able to log in anyway, due to the default account restrictions on your box ... just to be doubly sure. Once you're organised, you should also disable authentication by password, imo.

That is vital under either of the following circumstances...[LIST]
[*]The applications accessing your database server are not on the same *machine* as your database server, and you can't trust your local network.
[*]The applications accessing your database server are not on the same *network* as your database server.[/LIST]If neither is the case, then SSH tunnelling is often unnecessary ... or even unwise! If you're unsure about anything, I'd be glad to try to help.

Well, both are on the same box.  We're actually using a desktop for our server.  Not an ideal solution, to be sure, but since I work for a small startup, it's all we could afford.

My book suggests removing one of the root users, specifically [email]root@mydomain.com[/email], but leaving root@localhost intact.  It then suggests creating a seperate user with limited access (basically just SELECT, INSERT, and UPDATE) that should be what the scripts access the database with.  I'm just wondering if there's anything else, other than input validation/escaping script-side, that I should consider with the database.

> Returning to Postfix for a moment, please don't put off securing it for too long hehe. You should not leave it exposed to the outside world for any more than about 30-60 mins in total, unless you're sure it's safe.

Well, I haven't installed a Postfix package yet. ;)  Thanks for the tip, though.  I'll definitely go over the documentation before installing it.

> Oops... almost forgot...

"AllowGroups" isn't used that often in my experience, but feel free to set it. If you wanted, you could create an "sshusers" group of some sort, and use "AllowGroups" or "DenyGroups" to limit access to its members. By and large, people find it unnecessary to do so though.

The easiest way to get a user list is to look in /etc/passwd. The file format goes something like this...```
[COLOR=DimGray]username[/COLOR]**:x:**[COLOR=DimGray]UID[/COLOR]**:**[COLOR=DimGray]GID[/COLOR]**:**[COLOR=DimGray]Additional Info Here[/COLOR]**:**[COLOR=DimGray]home[/COLOR]**:**[COLOR=DimGray]shell[/COLOR]
```In order to log in normally, a user needs at least a password (the ":x:" in /etc/passwd lines tells you to look in /etc/shadow for a password) and a reasonable shell.

This thread is getting really random lol ... I hope you don't mind!

Ah, thanks.  And, I like that the thread is getting a bit randomized.  I've learned more in the past couple of days about both Linux in general and Ubuntu specifically than I did when I was in college using the old Red Hat systems in the computer clusters! :)

Thanks again! :D

---

### Post by kidders on 2007-08-10
> **KevinM1 said:**
> Well, both are on the same box.In that case, I suppose you'll be using unix sockets, rather than TCP connections, for communicating with your database.

> **KevinM1 said:**
> My book suggests removing one of the root usersYep. It's a question of not providing access for something that doesn't really need it. Since you won't have a reason to allow access to anyone whose name doesn't end in "@localhost", it would be prudent to remove everything else.

The idea behind creating additional users is similar. Many database applications will never have a legitimate reason to drop a database, truncate a table, and so on. The only other issue with specific relevance to security that I can think of is DoS, which has to do with the resources a badly-designed PHP script might be able to consume by being repeatedly or maliciously executed. It's not normally a major concern ... especially since most SQL servers can tell you if you're running queries that have the potential to be abused.

---

### Post by KevinM1 on 2007-08-13
Once again, I apologize for the delay in response.  The weekend called! ;)  Please bear with me as I have a few more general questions to ask:

I tried looking in /etc/password for user info.  Unfortunately, there isn't a /etc/password (or /etc/shadow) directory to be found.  Cause for concern?

Also, I'm trying to figure out sshd_config's **ListenAddress** property.     This is used to tell the ssh server what specific addresses it can allow, correct?  Should I even bother using it?

Finally, my boss mapped shift+t to open the terminal.  Naturally, this was a bad decision as it makes typing messages a pain whenever I need a capital 't.'  How can I change it to something more reasonable like ctrl+t or alt+t?

Thanks! :)

EDIT: one more MySQL question: I have an account for username-desktop and 127.0.0.1.  I assume the last one is okay, but should I remove the first one?

---

### Post by kidders on 2007-08-13
Hey again,

Hope you had a good weekend!

> **KevinM1 said:**
> I tried looking in /etc/password for user info.  Unfortunately, there isn't a /etc/password (or /etc/shadow) directory to be found.  Cause for concern?They are files (rather than directories). You may have trouble accessing them (particularly /etc/shadow) as an unprivileged user, if that's any help. The other file is called /etc/passwd (rather than /etc/passw**or**d). Incidentally, it's vital that you make no attempt to modify either of them.

> **KevinM1 said:**
> I'm trying to figure out sshd_config's **ListenAddress** property. This is used to tell the ssh server what specific addresses it can allow, correct?No, not quite. It controls the local addresses your SSH server binds to. Since many computers often have more than one network card, server applications tend to allow you to control which interfaces you want them to listen on.

> **KevinM1 said:**
> Finally, my boss mapped shift+t to open the terminal.Eek! What sort of graphical environment does he have? Has he created a global shortcut of some kind, or something more application-specific? (You're certainly very charitable to be fielding your boss' technical booboos!)

> **KevinM1 said:**
> I have an account for username-desktop and 127.0.0.1.  I assume the last one is okay, but should I remove the first one?I'm not quite with you here. MySQL account names tend to have a username component and a hostname component. This allows you to control where a given user can access your database from, and vary the operational privileges he has, depending on where he is.

I'm not completely sure what you're asking, but would it help if I said that MySQL servers operating on untrusted networks should never allow anyone to connect from any machine other than localhost? This essentially forces users who want remote access to your database to wrap their connection in the SSH protocol.

Hopefully this isn't too much information all in one go, but going back to SSH for a moment, one of the most effective ways of controlling what networks can access a server is to use your firewall. Imagine you did the following...```
sudo iptables -I INPUT -p tcp -i eth1 --dport 22 -j DROP
sudo iptables -I INPUT -p tcp -i eth1 --dport 22 -s 12.34.56.78 -j ACCEPT
```Your server would then drop any incoming packets destined for your SSH server that didn't come from 12.34.56.78.

---

### Post by KevinM1 on 2007-08-13
> **kidders said:**
> Hey again,

Hope you had a good weekend!

Thanks!  I hope yours was fun/restful too!

> They are files (rather than directories). You may have trouble accessing them (particularly /etc/shadow) as an unprivileged user, if that's any help. The other file is called /etc/passwd (rather than /etc/passw**or**d). Incidentally, it's vital that you make no attempt to modify either of them.

Ah, okay.  Found it.  Looks like there's only one account.

> No, not quite. It controls the local addresses your SSH server binds to. Since many computers often have more than one network card, server applications tend to allow you to control which interfaces you want them to listen on.

Oh, that makes sense.  Looks like another thing to leave blank as our current set-up is a bit odd.  There's some port forwarding going on, I believe...not a very smart set-up, as I believe this box, which is supposed to just be a small one-site web server is basically our company's gateway to the internet as a whole.  Hence my security concerns.

> Eek! What sort of graphical environment does he have? Has he created a global shortcut of some kind, or something more application-specific? (You're certainly very charitable to be fielding your boss' technical booboos!)

I'm only handling the booboo because I'm the only one capable (and I use the term loosely :P ) to be working on this machine.  He installed the OS, but knows absolutely nothing about Linux.  Less than me, if you can believe it.  I'm not sure where he found the shortcut mapping, but it was done before I could mitigate the damage.  *sigh* The joys of work :lol:

In any event, this machine is using the generic Gnome desktop that comes with 7.04, if that helps.

> I'm not quite with you here. MySQL account names tend to have a username component and a hostname component. This allows you to control where a given user can access your database from, and vary the operational privileges he has, depending on where he is.

I'm not completely sure what you're asking, but would it help if I said that MySQL servers operating on untrusted networks should never allow anyone to connect from any machine other than localhost? This essentially forces users who want remote access to your database to wrap their connection in the SSH protocol.

I don't know if this helps, but everything is being done on this box.  The other accounts (if that's what they are) look to have been created by default when I installed MySQL.     I have the normal root@localhost user, a root@rex-desktop (that's my home directory) user, and a (I assume) utility/maintenance user debian-sys-main@localhost.  I'm thinking I should remove the rex-desktop one.  I hope that made sense.

> Hopefully this isn't too much information all in one go, but going back to SSH for a moment, one of the most effective ways of controlling what networks can access a server is to use your firewall. Imagine you did the following...```
sudo iptables -I INPUT -p tcp -i eth1 --dport 22 -j DROP
sudo iptables -I INPUT -p tcp -i eth1 --dport 22 -s 12.34.56.78 -j ACCEPT
```Your server would then drop any incoming packets destined for your SSH server that didn't come from 12.34.56.78.

Actually, I was going to ask you about iptables.  Is there a GUI I could install to help me manage them?  Actually, more to the point, any resources to read regarding them in general?

Regarding the SSH itself, I'm thinking that I'll only use it to remote in from my Vista machine at home via Putty.  I'm probably wrong, but ISP's don't typically give their customers static IP addresses by default, right?  If that's the case, is there any other way I could lock the SSH server to only accept connections from my computer?

Thanks again, my friend! :D

---

### Post by kidders on 2007-08-13
> **KevinM1 said:**
> I'm only handling the booboo because I'm the only one capableHmm. So if you're typing an email, say, and you hit Shift+T, a terminal window opens up?

> **KevinM1 said:**
> I'm thinking I should remove the rex-desktop one.You might as well, yeah.

> **KevinM1 said:**
> Actually, I was going to ask you about iptables.  Is there a GUI I could install to help me manage them?Yes, there are many ... but imo, under no circumstances should you install any graphical applications on your server. Desktop environments, etc. are a security *nightmare*.

> **KevinM1 said:**
> Regarding the SSH itself, I'm thinking that I'll only use it to remote in from my Vista machine at home via Putty.Despite the lack of a static IP, that can be achieved relatively easily, I imagine. Having said that, it doesn't pay to be overly restrictive ... something I say from experience hehe! Depending on where you live, you might decide to limit access to your subcontinent, your ISP, or something similarly broad. If an emergency arises, the last thing you need is for your own security precautions to lock you out of your own system!

If you'd like me to describe limiting access to a single dynamically assigned IP address anyway, I'd be happy to do so, though.

On a totally different topic, this thread is probably becoming less and less useful to the community at large lol. It occurs to me that you might like to switch to IM, for quicker answers to your questions, if for no other reason hehe.

---

### Post by p_quarles on 2007-08-13
To set keybindings in Gnome, you can use the "Keyboard shortcuts" utility located in System >> Preferences. I believe these settings are bound to individual user accounts, so you might want to set up a separate account for the boss, so that he can have whatever bizarre keybindings he wants :)

> On a totally different topic, this thread is probably becoming less and less useful to the community at large lol.
FWIW, I disagree. I've been following the thread, and have gleaned a few interesting points from it.

---

### Post by KevinM1 on 2007-08-14
Thanks, I'm able to use capital 'T' without relying on caps lock!  Awesome. :)

Since this thread seems to have something of a viewership, I guess I'll keep bugging you this way. ;)

I'm currently trying to get my SSH set up, but it isn't working.  In particular, I've made an RSA passphrase, but every time I try to do what the stickied SSH setup thread recommends (namely, ssh-copy-id), I get asked for a password.  Now, I haven't setup an actual password.  I've tried entering in the passphrase I chose, but it doesn't work.  My current config file is:
```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress
#ListenAddress 
Protocol 2
AllowGroups ssh wheel
AllowUsers rex
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key

Ciphers aes256-cbc
MACs hmac-sha1

#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel VERBOSE

# Authentication:
LoginGraceTime 20
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding no
X11DisplayOffset 10
PrintMotd yes
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM no
```

This is a mix between what this site recommended and what my security book recommended.  I also had some errors when trying to restart the server with the **Ciphers** and **MACs** settings.  I originally had:
```

Ciphers aes256-cbc,3des-cbs,blowfish-cbc
MACs hmac-sha1,hmac-ripemd160,hmac-md5
```

But it kept telling me that everything after the first comma on each line was garbage.  I did check the spacing between each comma and each cipher/mac, but it made no difference.

I think my main problem is deciding what to do with the ssh-copy-id bit, specifically where it requires username@host at the end.  I'm not sure what to put for those values as there's only one user account, and I'm not sure if I should use localhost, my actually site's hostname, or my home directory for the '@host' part.

---

### Post by kidders on 2007-08-14
> **KevinM1 said:**
> I'm currently trying to get my SSH set up, but it isn't working.At least to start with, there's not much to be gained by over-thinking your SSH configuration, if you ask me. SSH is so widely used, that you can (in my view) take it for granted that default configurations are quite acceptable for general use. Beefed up encryption, the use of passphrase-protected keys, and so on are probably overkill.

Anyhow, the "Ciphers" line you posted has a typo in it, which may be causing your problems ... but personally, I don't think I would have bothered specifying one at all. For most people, setting up an SSH server is a 90-second job.

---

### Post by KevinM1 on 2007-08-15
> **kidders said:**
> At least to start with, there's not much to be gained by over-thinking your SSH configuration, if you ask me. SSH is so widely used, that you can (in my view) take it for granted that default configurations are quite acceptable for general use. Beefed up encryption, the use of passphrase-protected keys, and so on are probably overkill.

Anyhow, the "Ciphers" line you posted has a typo in it, which may be causing your problems ... but personally, I don't think I would have bothered specifying one at all. **For most people, setting up an SSH server is a 90-second job.**

True, but I'm dumb. :P

Like I said above, this machine is my company's gateway to the internet, as well as the business partner's hosting.  Everything goes through it -- phone (VoIP), internet, everything.  I'm just trying to be as secure as possible as it's probably our most vulnerable system.

What should I be using for a password?  Like I said before, I set up a RSA passphrase, but neither that nor my username's password work.  Should the RSA stuff be in my home folder?  Or someplace else?  Should I just say "forget it" and go back to default settings?

EDIT: I almost have it working, but now it doesn't accept my passphrase.  I think this may be due to some of the file permission juggling I had to do in order to create a passphrase for my username instead of root.  I know that the authorized_keys file is supposed to have 600 for permissions, but what about the others (id_rsa, id_rsa.pub, known_hosts)?

---

### Post by kidders on 2007-08-16
> **KevinM1 said:**
> EDIT: I almost have it working, but now it doesn't accept my passphrase.  I think this may be due to some of the file permission juggling I had to do in order to create a passphrase for my username instead of root.That sounds suspicious. Are you sure you're not doing something you shouldn't be?

Afaik, "chmod 600" should be fine for all your ssh-related files. Perhaps if you post what you've done & what happens when you try to log in to your server, I might be able to spot the problem.

---

### Post by KevinM1 on 2007-08-16
> **kidders said:**
> That sounds suspicious. Are you sure you're not doing something you shouldn't be?

Afaik, "chmod 600" should be fine for all your ssh-related files. Perhaps if you post what you've done & what happens when you try to log in to your server, I might be able to spot the problem.

Well, here's what happened:

Trying to use the ```
ssh-keygen -t
``` command without **sudo** wasn't working as the file permissions wouldn't let me have write access for the id_rsa files.  I couldn't login as root as I had turned that off in my configuration.  So, I chmod-ed everything to 777, then tried again.  This allowed me to create the proper id_rsa files (and subsequent authorized_keys file).  I then chmod-ed everything to, I believe 600.  I get the "Enter passphrase" prompt when I try to SSH, but every time I enter in the passphrase, the prompt is just repeated back to me.  After three or so attempts, it gives "Permission Denied."  I'm certain I'm typing it correctly.  All of these files are located in my /home/.ssh/ directory.

Unfortunately, I won't have access to the server for another couple of hours, so I can't paste my config file here for you to read until then.

EDIT: I'm finally at work, so here's my sshd_config:
```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress
#ListenAddress 
Protocol 2
AllowGroups ssh wheel
AllowUsers rex
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key

#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel VERBOSE

# Authentication:
LoginGraceTime 20
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
PasswordAuthentication no

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding no
X11DisplayOffset 10
PrintMotd yes
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM no
```

---

### Post by kidders on 2007-08-16
Hmm...

There could be any number of reasons for your difficulties, I'm afraid. Are you really sure the various little files in ~/.ssh are in the right place, on the right computers & have the correct permissions? You could try turning up ssh's verbosity, to see if its debug messages give you any clues. It may also be worth checking whether authentication by password even works.

---

### Post by KevinM1 on 2007-08-17
> **kidders said:**
> Hmm...

There could be any number of reasons for your difficulties, I'm afraid. Are you really sure the various little files in ~/.ssh are in the right place, on the right computers & have the correct permissions? You could try turning up ssh's verbosity, to see if its debug messages give you any clues. It may also be worth checking whether authentication by password even works.

I believe all of the files are in the right place.  id_rsa, id_rsa.pub, authorized_keys, and one more (I believe it has something to do with zones) are all in /home/myusername/.ssh.

All have chmod 600 permissions.

I'm not sure how to turn up the verbosity, and I don't believe that password (not RSA passphrase) authentication works.  I don't really know how to test for that as I was never prompted to create a generic password.  Is there a particular config setting or command to use for that?

---

### Post by kidders on 2007-08-18
Hey again,

> **KevinM1 said:**
> I'm not sure how to turn up the verbosityCheck out ssh's man page ... debug messages might not turn up anything interesting, but it's at least worth a try, I suppose.

Generally, in order for key-based authentication to work, authentication by password must work. Although in practice you may want to disable it, you can't use a key to log in to a server that wouldn't at least theoretically be able to accept your password ... if you know what I mean.

Setting up an SSH server in Ubuntu is exceptionally straightforward, so I'm having difficulty wrapping my head around where your problems could be coming from. All you should need to do is...[LIST]
[*]Install the server.
[*]Check that it is running.[/LIST]Now, authentication by password works. Then, you might want to...[LIST]
[*]Tweak your server config file *slightly* to tighten up your security.
[*]Set up key-based logins.
[*]Disable password-based logins, if desired.[/LIST]This may sound silly, but perhaps if you walk me through exactly what you've done in pedantic detail, your mistake might jump out at us. All five steps really shouldn't take you any more than five minutes, from beginning to end, you see :-( so I'm not quite sure what to suggest you try next.

---

### Post by KevinM1 on 2007-08-20
> **kidders said:**
> Hey again,

Check out ssh's man page ... debug messages might not turn up anything interesting, but it's at least worth a try, I suppose.

Generally, in order for key-based authentication to work, authentication by password must work. Although in practice you may want to disable it, you can't use a key to log in to a server that wouldn't at least theoretically be able to accept your password ... if you know what I mean.

Setting up an SSH server in Ubuntu is exceptionally straightforward, so I'm having difficulty wrapping my head around where your problems could be coming from. All you should need to do is...[LIST]
[*]Install the server.
[*]Check that it is running.[/LIST]Now, authentication by password works. Then, you might want to...[LIST]
[*]Tweak your server config file *slightly* to tighten up your security.
[*]Set up key-based logins.
[*]Disable password-based logins, if desired.[/LIST]This may sound silly, but perhaps if you walk me through exactly what you've done in pedantic detail, your mistake might jump out at us. All five steps really shouldn't take you any more than five minutes, from beginning to end, you see :-( so I'm not quite sure what to suggest you try next.

What I did was install the server using **apt-get** and then started tweaking the config file (the latest iteration is the one above) and created the RSA keys.  I don't remember specifying a password upon installation, which is where my frustration is coming from.  I was surprised when it asked me to supply one.

Here's a question -- do I need to change the ssh_config file as well?  Right now, both the PasswordAuthentication and RSAAuthentication properties are commented out.

I also just noticed that there's no /home/username/.ssh/config file.  Could this be a problem?

Here's the output I get when using the debugging option:
```

rex@rex-desktop:~/.ssh$ ssh -v rex@rex-desktop
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to rex-desktop [127.0.1.1] port 22.
debug1: Connection established.
debug1: identity file /home/rex/.ssh/identity type -1
debug1: identity file /home/rex/.ssh/id_rsa type -1
debug1: identity file /home/rex/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug1: An invalid name was supplied
Unknown code krb5 224

debug1: An invalid name was supplied
A parameter was malformed
Unknown code ggss 3

debug1: An invalid name was supplied
Unknown code krb5 224

debug1: An invalid name was supplied
A parameter was malformed
Unknown code ggss 3

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'rex-desktop' is known and matches the RSA host key.
debug1: Found key in /home/rex/.ssh/known_hosts:2
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
Ubuntu 7.04
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/rex/.ssh/identity
debug1: Trying private key: /home/rex/.ssh/id_rsa
Enter passphrase for key '/home/rex/.ssh/id_rsa': 
Enter passphrase for key '/home/rex/.ssh/id_rsa': 
Enter passphrase for key '/home/rex/.ssh/id_rsa': 
debug1: Trying private key: /home/rex/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey).
rex@rex-desktop:~/.ssh$ 
```

It looks like it's not recognizing my user name.  I did enter the passphrase on each attempt, too.

I still have the original sshd_config file...I'm thinking of using that and starting over.

---

### Post by p_quarles on 2007-08-20
> What I did was install the server using **apt-get** and then started tweaking the config file (the latest iteration is the one above) and created the RSA keys. I don't remember specifying a password upon installation, which is where my frustration is coming from. I was surprised when it asked me to supply one.
SSH doesn't create a new user, it just allows you to access your regular accounts remotely. When it asks for a password, you simply provide the password for your user account on that machine.

Also, the RSA keys have to be created on the *remote* machine (the one you're logging in from), and then the public key should be transferred to the server.

---

### Post by KevinM1 on 2007-08-20
> **p_quarles said:**
> SSH doesn't create a new user, it just allows you to access your regular accounts remotely. When it asks for a password, you simply provide the password for your user account on that machine.

**Also, the RSA keys have to be created on the *remote* machine (the one you're logging in from), and then the public key should be transferred to the server.**

Well, that explains my problem, then.  I didn't see that part of the documentation until you mentioned it.  Since the machine I want to use in order to log into the server is a Vista machine, how/where would I save the public keys I generated?

Also, I've been testing out my Postfix setup.  In particular, I've been trying to execute the telnet commands the documentation suggests, but the system tells me I can't telnet into localhost, regardless of me using **sudo** or not.  Specifically, I get a connection refused message.  Any ideas on what that's about?

Also, let me thank both of you again.  I know it must be frustrating to deal with my seemingly never ending stream of questions.  Thanks for having the patience to deal with me. :)

---

### Post by p_quarles on 2007-08-20
Are you using PuTTY for Windows, then? I'm not real sure how that program deals with RSA keys, but I know the author's site has pretty good documentation.

Just FYI, too, RSA keys are not necessary for full ssh functionality. They're an extra layer of security, and they can be used to allow safe passwordless authentication. But if it ends up being too much trouble to set that up in Windows, it's perfectly reasonable to use a strong user password and to change the remote connection port.

---

### Post by KevinM1 on 2007-08-29
Sorry for bringing this up again....

I've been trying to use PuTTY for Windows to connect to this Ubuntu box.  Every time I try it, I get a connection timeout before I can even reach the system.  I've switched the sshd_config files -- in detail, I've renamed the one I was trying to get RSA encryption working on to sshd_config.new and renamed the generic config (sshd_config.original) to sshd_config.  I still get timeouts.

I'm wondering if it has something to do with the iptables rules I set up.  I followed the tutorial in the wiki to the letter.  Here's my current iptables setup:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            limit: avg 5/min burst 5 LOG level debug prefix `iptables denied: ' 
DROP       0    --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

And the contents of my current sshd_config file:
```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes
```

Any ideas?

---

### Post by kidders on 2007-08-29
Hey again,

With reference to your o/p, it's worth nothing that the iptables configuration you posted is inherently insecure, since its default action is to accept incoming data. It might be worth revising it.

It's possible that timeouts could be caused by your firewall ... although it's hard to judge, because of the low detail level in the output you posted. I would suggest testing your firewall with a more basic protocol ... ping maybe.

---

### Post by KevinM1 on 2007-08-29
> **kidders said:**
> Hey again,

With reference to your o/p, it's worth nothing that the iptables configuration you posted is inherently insecure, since its default action is to accept incoming data. It might be worth revising it.

It's possible that timeouts could be caused by your firewall ... although it's hard to judge, because of the low detail level in the output you posted. I would suggest testing your firewall with a more basic protocol ... ping maybe.

Right now, unfortunately, my firewall/iptables are having...issues.  Firestarter has never worked right for me with how my boss set up our internet connection, and now that I've tried playing around with Firestarter even more, all of my old iptables rules, as insecure as they were, have been erased.  Not a good afternoon to say the least.

---

### Post by kidders on 2007-08-30
In that case, you can probably rule iptables out of the equation ... assuming it's now accepting all packets, your problem is most likely elsewhere.

---

### Post by KevinM1 on 2007-08-30
> **kidders said:**
> In that case, you can probably rule iptables out of the equation ... assuming it's now accepting all packets, your problem is most likely elsewhere.

If I reinstall the daemon, it should accept connections right 'out of the box,' correct?

---

### Post by kidders on 2007-08-30
If you mean SSH, then yes. Out of the box, it accepts incoming connections from anywhere (provided nothing else is blocking them, of course), and can handle key-based or password-based authentication.

---

### Post by KevinM1 on 2007-08-31
This is going to sound really dumb, but please bear with me: is there a terminal command I can use to remove the ssh server along the lines of **apt-get install**?  Or will removing it via Synaptic suffice?  I just don't want to remove the wrong component.

Also, should I delete some of the things in /home/.ssh?

Thanks! :)

---

### Post by p_quarles on 2007-08-31
```
sudo apt-get remove --auto-remove openssh-server
```
will do the trick. 

That will not, however, remove sshd_config, so if that's the only thing that's broken, I'm sure that someone here could be persuaded to supply you with a workable version of that file. (or you can manually delete it, then reinstall the whole thing).

---

### Post by HermanAB on 2007-08-31
BTW, you could have a look at Bastille for hardening your server:
[http://www.bastille-linux.org/](http://www.bastille-linux.org/)

First configure it the way you want it, then run Bastille.  It can be hard to change stuff after Bastille was run, since that is the whole purpose of Bastille...

Cheers,

H.

---

### Post by KevinM1 on 2007-09-04
> **HermanAB said:**
> BTW, you could have a look at Bastille for hardening your server:
[http://www.bastille-linux.org/](http://www.bastille-linux.org/)

First configure it the way you want it, then run Bastille.  It can be hard to change stuff after Bastille was run, since that is the whole purpose of Bastille...

Cheers,

H.

I've been going over the site, and it looks like there hasn't been any updates since August 2006.  Have I missed more recent updates?  Or is this product not supported any longer?  I'd like to harden the kernal with something that is still supported against new exploits/attacks.

---

### Post by kidders on 2007-09-04
> **KevinM1 said:**
> I'd like to harden the kernal with something that is still supported against new exploits/attacks.Several distros produce hardened versions of their software. Careful though ... hardened kernels are not a walk in the park. You'd need to be *really* sure it's a road you want to go down, imo.

---

### Post by KevinM1 on 2007-09-04
> **kidders said:**
> Several distros produce hardened versions of their software. Careful though ... hardened kernels are not a walk in the park. You'd need to be *really* sure it's a road you want to go down, imo.

Yeah, I've heard that from other sources, too.  I'll hold off on hardening until I get a lot more comfortable with the OS.  With any luck, my copy of the Ubuntu Bible will be delivered today or tomorrow.

EDIT: another SSH question -- I've reinstalled the server, and so far, it appears to be working fine out of the box.  However, it keeps asking me for my RSA authentication passphrase.  Now, I tried getting RSA authentication to work during my original SSH server setup, but could never get it to work properly.  I haven't changed the config file, yet, to try again.  And, I can log into the system by providing nothing for the passphrase, which causes it to merely ask for my user password.

To avoid getting asked for a passphrase, should I delete some of the files in /home/.ssh (authorized_keys, id_rsa.pub)?  Or perhaps some of the key files (ssh_host_rsa_key, ssh_host_dsa_key, etc) in /etc/ssh?

---

### Post by kidders on 2007-09-04
Hmm...

Perhaps trying a login in verbose mode might give you some insight into *why* your key is being rejected. Sometimes the debug output tends to omit useful details like that, but it's worth a shot.

---

### Post by KevinM1 on 2007-09-05
> **kidders said:**
> Hmm...

Perhaps trying a login in verbose mode might give you some insight into *why* your key is being rejected. Sometimes the debug output tends to omit useful details like that, but it's worth a shot.

Good idea.  I'll try it when I get to work today.

Unfortunately, PuTTY still isn't connecting to the server from home.  I can SSH to localhost from the server itself, which is further than I got with my first install, but I keep getting a connection timeout when I try PuTTY.  As far as I know, nothing should be blocking the connection.  My sshd_config is the default version, and I have the port open in Firestarter.

For the host that I'm trying to connect to, would it be the webhost or the machine's actual hostname?  Trying rextrader.com, which is the webhost, gives me the timeout, as does trying the static IP address.  Trying mail.rextrader.com, which is the machine's actual hostname, gives me a "host does not exist" error.

---

### Post by KevinM1 on 2007-09-05
Well, switching to verbose didn't reveal anything.  It's still asking for a rsa key passphrase, but it doesn't need one for me to log on.:

```

rex@mail:/etc/ssh$ ssh localhost
Enter passphrase for key '/home/rex/.ssh/id_rsa': (<-- nothing was entered)
rex@localhost's password: 
Linux mail 2.6.20-16-generic #2 SMP Thu Aug 30 23:16:15 UTC 2007 x86_64

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have new mail.
Last login: Wed Sep  5 12:01:05 2007 from localhost
rex@mail:~$ exit
logout
Connection to localhost closed.

```

I still haven't figured out the PuTTY issue, either.

---

### Post by kidders on 2007-09-05
Could you post the verbose output?

From what you *have* posted, it seems as though the key you're trying to use is not valid. You might want to read some of OpenSSH's documentation, or look over a few howtos on using SSH.

---

### Post by KevinM1 on 2007-09-05
> **kidders said:**
> Could you post the verbose output?

From what you *have* posted, it seems as though the key you're trying to use is not valid. You might want to read some of OpenSSH's documentation, or look over a few howtos on using SSH.

Right now I don't even want to try key authentication.  Any keys that are on my system aren't valid as they were from my previous install.  Like I asked above, should I erase anything regarding key authentication from /home/.ssh or /etc/ssh?

In any event, here's my verbose attempt:
```

rex@mail:~$ ssh -v localhost
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/rex/.ssh/identity type -1
debug1: identity file /home/rex/.ssh/id_rsa type -1
debug1: identity file /home/rex/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug1: An invalid name was supplied
Unknown code krb5 224

debug1: An invalid name was supplied
A parameter was malformed
Unknown code ggss 3

debug1: An invalid name was supplied
Unknown code krb5 224

debug1: An invalid name was supplied
A parameter was malformed
Unknown code ggss 3

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /home/rex/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/rex/.ssh/identity
debug1: Trying private key: /home/rex/.ssh/id_rsa
Enter passphrase for key '/home/rex/.ssh/id_rsa': 
debug1: Trying private key: /home/rex/.ssh/id_dsa
debug1: Next authentication method: password
rex@localhost's password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
Linux mail 2.6.20-16-generic #2 SMP Thu Aug 30 23:16:15 UTC 2007 x86_64

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have new mail.
Last login: Wed Sep  5 12:01:39 2007 from localhost
rex@mail:~$ exit
logout
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: channel 0: free: client-session, nchannels 1
Connection to localhost closed.
debug1: Transferred: stdin 0, stdout 0, stderr 33 bytes in 2.8 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 11.9
debug1: Exit status 0

```

And my sshd_config file as it stands now:
```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel VERBOSE

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

#RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes
```

I do have a new OpenSSH book, but I haven't had the time to go through all of it yet.  I just got it a couple days ago.

---

### Post by kidders on 2007-09-05
If you don't want to use key-based authentication, then you might as well remove any SSH keys in your home directory. Otherwise, keep them. By default, SSH will naturally try any it can find, unless specifically instructed not to.

Incidentally, what SSH server you had installed at the time you created a given client key (or whether you even had on installed at all) is irrelevant. By and large, any SSH-compatible public/private keypair created anywhere will work with any client/server combination. If you think about it, key-based authentication would be completely useless otherwise.

Anyhow, thanks for the additional output. I just wanted to be 100% sure I was right, and that nothing odd was going on. As I suspected, the debug messages indicate that your SSH client tries to authenticate using your SSH keys (which it needs your keyphrase to do), fails, falls back on password-based authentication, which succeeds.

---

### Post by KevinM1 on 2007-09-05
> **kidders said:**
> If you don't want to use key-based authentication, then you might as well remove any SSH keys in your home directory. Otherwise, keep them. By default, SSH will naturally try any it can find, unless specifically instructed not to.

Incidentally, what SSH server you had installed at the time you created a given client key (or whether you even had on installed at all) is irrelevant. By and large, any SSH-compatible public/private keypair created anywhere will work with any client/server combination. If you think about it, key-based authentication would be completely useless otherwise.

Anyhow, thanks for the additional output. I just wanted to be 100% sure I was right, and that nothing odd was going on. As I suspected, the debug messages indicate that your SSH client tries to authenticate using your SSH keys (which it needs your keyphrase to do), fails, falls back on password-based authentication, which succeeds.

Ah, okay.  Thanks.

Any ideas re: my timeout issues?  I don't see anything in my config file that should be causing it.

---

### Post by kidders on 2007-09-05
Can you ping the server in question? (It's unlikely to be an SSH-related issue, imo.)

---

### Post by KevinM1 on 2007-09-06
> **kidders said:**
> Can you ping the server in question? (It's unlikely to be an SSH-related issue, imo.)

This is strange.  Ping gives me a timeout as well, but I can still view the temporary "Coming Soon" web page I made.

---

### Post by kidders on 2007-09-06
Hmm... unfortunately, trouble contacting your server could be caused by any number of things. For instance, any firewall or router between you and the server could be to blame.

---

### Post by KevinM1 on 2007-09-06
> **kidders said:**
> Hmm... unfortunately, trouble contacting your server could be caused by any number of things. For instance, any firewall or router between you and the server could be to blame.

I'm thinking it's the router at work, as I know for certain I'm allowing SSH through the firewall.

---

### Post by KevinM1 on 2007-09-06
Could port forwarding be an issue?  As I'm still getting the timeout even though my boss claims to have opened port 22 on the router.

---

### Post by kidders on 2007-09-06
Yes it could, I suppose. It's hard to make any kind of intelligent suggestion without a reasonably detailed understanding of how the networks on both sides of the connection are organised, I'm afraid.

If you want, PM me the IP address of the server you're trying to access. I may be able to narrow the list of possible problems a little.

---

### Post by kidders on 2007-09-06
First of all, apologies for replying to myself!

Thanks for the PM, KevinM1 ... I didn't see the need to tell the *entire* world your address hehe. Anyhow, I note that your IP has externally accessible services listening on ports 22 and 80, although they're a little on the sluggish side (at around 22:30 GMT anyway).

The SSH service seems fine from my end...```
$ nmap [COLOR=Plum][deleted][/COLOR]

Starting Nmap 4.20 ( http://insecure.org ) at 2007-09-06 22:23 IST
Interesting ports on static-[COLOR=Plum][deleted][/COLOR].metrocast.net ([COLOR=Plum][deleted][/COLOR]):
Not shown: 1695 filtered ports
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http

Nmap finished: 1 IP address (1 host up) scanned in 148.221 seconds
$ ssh !$
ssh [COLOR=Plum][deleted][/COLOR]
The authenticity of host '[COLOR=Plum][deleted][/COLOR] ([COLOR=Plum][deleted][/COLOR])' can't be established.
RSA key fingerprint is 8f:24:0a:c0:2d:5e:be:55:0b:f2:33:e9:3c:23:b2:3f.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '[COLOR=Plum][deleted][/COLOR]' (RSA) to the list of known hosts.
kidders@[COLOR=Plum][deleted][/COLOR]'s password:
```

That seems to suggest either:[LIST]
[*]a server-side router or firewall has a problem specifically with your IP (unlikely), or
[*]there is a configuration problem on your local network (more likely).[/LIST]I hope that's of some help.

---

### Post by KevinM1 on 2007-09-07
I finally got it to work!  The problem appeared to be my wireless router.  Once I opened port 22 on it, PuTTY connected to the server.  I still can't ping to it - ping must use a different port - but SSH is now working.  Now to start setting up RSA authentication....

---

### Post by KevinM1 on 2007-09-20
Apologies for bumping this thread, but I'm still having difficulty getting RSA authentication to work.

I'm using PuTTY at home in order to connect to the server at work.  Password-only authentication works fine, but the RSA mechanism is just ignored (I SSH-ed to localhost within the current SSH connection in order to get the verbose output when trying to login):
```

rex@mail:/etc/ssh$ ssh -v localhost
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/rex/.ssh/identity type -1
debug1: identity file /home/rex/.ssh/id_rsa type -1
debug1: identity file /home/rex/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debia                                                                                                 n-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug1: An invalid name was supplied
Unknown code krb5 224

debug1: An invalid name was supplied
A parameter was malformed
Unknown code ggss 3

debug1: An invalid name was supplied
Unknown code krb5 224

debug1: An invalid name was supplied
A parameter was malformed
Unknown code ggss 3

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /home/rex/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/rex/.ssh/identity
debug1: Trying private key: /home/rex/.ssh/id_rsa
Enter passphrase for key '/home/rex/.ssh/id_rsa':  **<--- Tried entering my passphrase, but it just repeated the prompt**
Enter passphrase for key '/home/rex/.ssh/id_rsa': **<--- Pressed <enter> without entering a value for the passphrase**
debug1: Trying private key: /home/rex/.ssh/id_dsa
debug1: Next authentication method: password
rex@localhost's password:
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
Linux mail 2.6.20-16-generic #2 SMP Thu Aug 30 23:16:15 UTC 2007 x86_64

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have new mail.
Last login: Thu Sep 20 15:10:59 2007 from d-65-175-211-84.metrocast.net
rex@mail:~$
```

I followed PuTTYgen's instructions regarding the keys - my private key is on my local machine, and I pasted the public key info in ~/.ssh/authorized_keys.  My sshd_config is:
```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel VERBOSE

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile     %h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes
```

Are there any steps I'm missing?

---

### Post by kidders on 2007-09-20
> **KevinM1 said:**
> I SSH-ed to localhost within the current SSH connection in order to get the verbose output when trying to loginDoesn't that make it useless? The way I see it, trying to use debug information from a connection between host A and host B (technically host A and host A, I suppose!) to diagnose a problem with host C would send you on a wild goose chase. :-(

---

### Post by KevinM1 on 2007-09-21
> **kidders said:**
> Doesn't that make it useless? The way I see it, trying to use debug information from a connection between host A and host B (technically host A and host A, I suppose!) to diagnose a problem with host C would send you on a wild goose chase. :-(

Damn you and your logic! :-P

Unfortunately, from what I see, there's nothing in PuTTY that jumps out to me as an equivalent to the **-v** flag.

I've done everything* I could that was suggested in the wiki page ([https://help.ubuntu.com/community/AdvancedOpenSSH#head-f06532af79917a251e68c7ccf567cb5c399e0aba](https://help.ubuntu.com/community/AdvancedOpenSSH#head-f06532af79917a251e68c7ccf567cb5c399e0aba)), but PuTTY keeps telling me that the server isn't accepting my private key.  I can still get in with my password, though.

*Steps I've taken:
1. Created public and private keys using PuTTYgen key generator.
2. Saved my private key on my local machine, pasted the public key into ~/.ssh/authorized_keys.
3. I also put the public key into ~/.ssh/id_rsa.pub.
4. I uncommented the RSA authentication lines in /etc/ssh/sshd_config
5. I restarted the SSH server.
6. Tried connecting via PuTTY.  I can connect, but it refuses my private key, so I can only gain access by using my password.

One thing of note: I do have a private key saved in ~/.ssh/id_rsa.  This is from my first attempt at getting RSA authentication to work a couple weeks ago.  It's owned by root, as I entered **sudo ssh_keygen -t rsa** (I thought that everything had to be done with sudo back then).  Is it possible that OpenSSH is trying to use that key instead?  Should I just erase it?

---

### Post by KevinM1 on 2007-09-21
Test #2:

I'm trying to see if I can use RSA authentication while on the server itself.  In other words, trying to see if **ssh localhost** will use the RSA authentication.  Like my other attempts, whenever I enter my passphrase, I just get another prompt asking me to enter it again:
```

rex@mail:~/.ssh$ ssh -v rex@localhost
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/rex/.ssh/identity type -1
debug1: identity file /home/rex/.ssh/id_rsa type 1
debug1: identity file /home/rex/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug1: An invalid name was supplied
Unknown code krb5 224

debug1: An invalid name was supplied
A parameter was malformed
Unknown code ggss 3

debug1: An invalid name was supplied
Unknown code krb5 224

debug1: An invalid name was supplied
A parameter was malformed
Unknown code ggss 3

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /home/rex/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/rex/.ssh/identity
debug1: Offering public key: /home/rex/.ssh/id_rsa
debug1: Server accepts key: pkalg ssh-rsa blen 277
Enter passphrase for key '/home/rex/.ssh/id_rsa': **<--- I entered my passphrase here**
Enter passphrase for key '/home/rex/.ssh/id_rsa': <-- Just pressed <enter> without inputing my passphrase[/b]
debug1: Trying private key: /home/rex/.ssh/id_dsa
debug1: Next authentication method: password
rex@localhost's password: 
Connection closed by UNKNOWN **<--- I accidentally mistyped my password, so it booted me**

```

It looks like it accepted my private key, but the passphrase issue is still popping up.  If I enter nothing, I get prompted for my password.  If I enter something, I just get another prompt asking for my passphrase again.

Looking over the debugging output again, is id_rsa truly the public key?  I always thought that id_rsa.pub was the public key.  If the former is the case, could my problem be it being owned by root rather than my user account?

EDIT: looks like changing the owner of id_rsa did the trick, as it's accepting my passphrase now.  Yay! :)

EDIT2: Should I be concerned about the line I bolded below?

```

rex@mail:~/.ssh$ ssh -v rex@localhost
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/rex/.ssh/identity type -1
debug1: identity file /home/rex/.ssh/id_rsa type 1
debug1: identity file /home/rex/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug1: An invalid name was supplied
Unknown code krb5 224

debug1: An invalid name was supplied
A parameter was malformed
Unknown code ggss 3

debug1: An invalid name was supplied
Unknown code krb5 224

debug1: An invalid name was supplied
A parameter was malformed
Unknown code ggss 3

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /home/rex/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/rex/.ssh/identity
debug1: Offering public key: /home/rex/.ssh/id_rsa
debug1: Server accepts key: pkalg ssh-rsa blen 277
**debug1: PEM_read_PrivateKey failed**
debug1: read PEM private key done: type <unknown>
Enter passphrase for key '/home/rex/.ssh/id_rsa': 
debug1: read PEM private key done: type RSA
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
Linux mail 2.6.20-16-generic #2 SMP Thu Aug 30 23:16:15 UTC 2007 x86_64

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have new mail.
Last login: Fri Sep 21 10:54:42 2007 from localhost
rex@mail:~$ exit
logout
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: channel 0: free: client-session, nchannels 1
Connection to localhost closed.
debug1: Transferred: stdin 0, stdout 0, stderr 33 bytes in 15.9 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 2.1
debug1: Exit status 0

```

---

### Post by kidders on 2007-09-21
This is all a bit confusing again, I'm afraid. Sorry if this post doesn't tell you any more than you already know! :-(

> **KevinM1 said:**
> whenever I enter my passphrase, I just get another prompt asking me to enter it againThis normally means your passphrase is wrong.

> **KevinM1 said:**
> ```
Enter passphrase for key '/home/rex/.ssh/id_rsa': **<--- I entered my passphrase here**
Enter passphrase for key '/home/rex/.ssh/id_rsa': <-- Just pressed <enter> without inputing my passphrase[/b]
debug1: Trying private key: /home/rex/.ssh/id_dsa
```These debug lines show that the key you are using is inaccessible, or you're not using the right passphrase.

> **KevinM1 said:**
> could my problem be it being owned by root rather than my user account?Possibly. Nothing in anyone's home directory should be owned by root (except of course, things in *root*'s home directory hehe).

> **KevinM1 said:**
> Should I be concerned about the line I bolded below?I don't *think* so.

---

