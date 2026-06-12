---
title: "[SOLVED] ssh store password attempts in auth.log"
date: 2008-06-25
forum: Server Platforms
---

### Post by mrpeenut24 on 2008-06-25
I'm wondering if it's possible for sshd to store passwords in auth.log.  Before people get on a privacy rant, I'm on a personal server used only by myself with a banner that notifies people that all information is recorded.  Yet I do have a domain name, and I'm getting over 10k hits/day.  I'm not necessarily interested in storing correct passwords, but rather wrong passwords.  I've tried upping the logging information to Fascist, and up through Debug3, but no luck.

Does anyone know it there's an option somewhere that I'm missing, or if there's a patch that will do this?  If not, does anyone know where in the source the info is written to the log?

---

### Post by mrpeenut24 on 2008-06-28
bump

Anybody?

---

### Post by coyled on 2008-06-29
> **mrpeenut24 said:**
> I'm not necessarily interested in storing correct passwords, but rather wrong passwords.

But you'd end up writing valid passwords to a log file, too, and you really don't want to do that.  What are you ultimately trying to achieve by logging passwords used in failed login attempts?  There might be a better, more secure way to find what you're looking for.

-Coyle

---

### Post by windependence on 2008-06-29
You're nuts! Do you have any idea how many attempts to get in occur on a normal day? If I watch them in real time on the console they just continually scroll by. Just the amount of data would be huge and like coyled said for what? If you just want a passowrd file there are many out there free for tools like John the Ripper and other password cracking tools.

To measure web traffic, what really counts is page views and unique visitors. Hits is not really indicative of total traffic. When you have 10,000 page views per day then you are just turning the corner. :)

-Tim

---

### Post by mrpeenut24 on 2008-06-29
coyled: not necessarily.  If done right, the password can be written to the file when the authentication fails.  See this:

> Jun 29 07:13:33 www sshd[6170]: Invalid user federal from 123.140.245.23
Jun 29 07:13:33 www sshd[6170]: pam_unix(sshd:auth): check pass; user unknown
Jun 29 07:13:33 www sshd[6170]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=123.140.245.23 
Jun 29 07:13:36 www sshd[6170]: Failed password for invalid user federal from 123.140.245.23 port 36942 ssh2
compared to:

> Jun 29 07:09:31 www sshd[5995]: Accepted password for mrpeenut24 from 192.168.1.101 port 45748 ssh2
Jun 29 07:09:31 www sshd[5999]: pam_unix(sshd:session): session opened for user mrpeenut24 by (uid=0)
These are obviously two different outputs being printed to the log.  It shouldn't be difficult to modify it to write the incorrect password along with the login attempt.


I would like to be able to graph the use of passwords with users to see if there's any correlation.  I'm making a honeypot for a school netsec independent study project and would like some extra information.  I'm already able to see which names are used most often (and how often), which IPs send the most login attempts, and I think passwords would be a useful addition to the information I collect.  Even so, I'm the only one with login access to this computer, so logging correct passwords wouldn't be so bad.  If it gets compromised I can easily wipe it and start over.


windependece, I'm not talking about HTTP traffic, I'm talking about ssh login attempts.  The data is already logged.  Check /var/log/auth.log.  In fact, I believe it never deletes those logs, gzipping them instead, so the information collection isn't a problem.  Using grep & awk I can easily pull out the data I need, so I don't have to sort through it all.  It's also not a matter of collecting passwords just so I can use them to brute force, it's a matter of collecting real-world data to use in a presentation.


If you guys don't know of a patch or option variable, I can edit the code myself and reinstall ssh.  The only problem then would be updating.

-mrpeenut



EDIT:
> 
mrpeenut24@www:/var/log$ wc auth.log.0
  10145  131198 1046675 auth.log.0
10145 / 5 = 2029 login attempts last week, give or take

---

### Post by MJN on 2008-06-29
MrPeenut,

That sounds like an interesting little project. If you've not already seen it you might like to take a look at the patch from [this blog](http://unixcluster.dk/index.php?/archives/23-Logging-ssh-passwords,-part-2.html) for either a ready-baked solution or some idea of how you can modify your SSH server to do likewise.

Do post back with any successes/failure as I'm sure it'd be of interest to others.

Mathew

---

### Post by mrpeenut24 on 2008-06-29
So far, looking in OpenBSD's openssh-5.0p1 in auth.c I can see this:

```


if (authctxt->postponed)
        authmsg = "Postponed";
    else
        authmsg = authenticated ? "Accepted" : "Failed";

   authlog("%s %s for %s%.100s from %.200s port %d%s",
        authmsg,
        method,
        authctxt->valid ? "" : "invalid user ",
        authctxt->user,
        get_remote_ipaddr(),
        get_remote_port(),
        info);
```It looks like both success and fail are logged in a single command.  That wouldn't be a problem though.  I'll keep looking and check out that link.  Thanks MJN.

-mrpeenut

---

### Post by mrpeenut24 on 2008-06-29
MJN, that works great!  Thanks.  That'll also make sifting through the logs easier too, and keep the auth.log intact.

:-D


EDIT:  [That patch]("http://www.monkey-house.org/2007/10/openssh-brute-password-capture-patch.html") (linked on that page) was for 4.7p1, but it worked on [5.0p1]("ftp://ftp3.usa.openbsd.org/pub/OpenBSD/OpenSSH/portable/openssh-5.0p1.tar.gz") in case anyone was wondering.  :-)

---

### Post by MJN on 2008-06-29
Wow that was quick - nice work!

Mathew

---

### Post by coyled on 2008-06-29
> **mrpeenut24 said:**
> I'm making a honeypot for a school netsec independent study project and would like some extra information.

Ah, ok.  You could do this via PAM, and you wouldn't have to worry about re-patching sshd any time you want to upgrade it.  Check out pam_storepw [ [http://silicon-verl.de/home/flo/software/pamcifs.html](http://silicon-verl.de/home/flo/software/pamcifs.html) ] for a starting point.

-Coyle

---

### Post by mrpeenut24 on 2008-06-29
:-/ there's almost no documentation on that, and it looks like all it does is "store" the password in an /etc/shadow-type file so you don't have to type it in twice to mount a samba drive, or something like that.  I'd like to get pam to work, since the ssh I installed disabled it...but I don't believe it's necessary.

---

### Post by coyled on 2008-06-29
> **mrpeenut24 said:**
> :-/ there's almost no documentation on that, and it looks like all it does is "store" the password in an /etc/shadow-type file so you don't have to type it in twice to mount a samba drive, or something like that.  I'd like to get pam to work, since the ssh I installed disabled it...but I don't believe it's necessary.

There's not much documentation on it because there's not much to it.  :)  It just writes usernames and passwords out to a file.  All I'm saying is you might have an easier go of it if you inserted a little logging module into the PAM stack vs. patching sshd.  You'd get what you want (logging of user/pass attempts) without having to patch sshd every time you want to roll out a new version.  But either way works.

-Coyle

---

### Post by mrpeenut24 on 2008-06-29
I couldn't find where it stored the passwords.  I checked /var/run/pw and the file didn't exist.  Have you used this before?


By the way, I found how to get pam working in ssh, it was a config option --with-pam :-p .

---

### Post by coyled on 2008-06-29
> **mrpeenut24 said:**
> I couldn't find where it stored the passwords.  I checked /var/run/pw and the file didn't exist.

Set
```

LogLevel DEBUG

```
in sshd_config to see if pam_storepw is complaining about anything.


> Have you used this before?

I installed in on a Hardy box just to see if it worked, but that's it.  In /etc/pam.d/sshd I added
```

auth    optional        pam_unix.so nullok_secure
auth    optional        pam_storepw.so

```
just above
```

@include common-auth

```
The first line is just a lazy way to make PAM_AUTHTOK (the password as it's passed to PAM) available to pam_storepw as-written.  Not the most efficient way to go about it, but it's quick and dirty.  Later, in common-auth, pam_unix is listed as a requisite module, so it's still doing the password checks as before.  Only now it'll write both successful and failed passwords to the file in /var/run/pw , but only the latest one used for each user.  You'll want to patch pam_storepw to write the usernames/passwords to a log instead of these per-user files, I presume.  But once you do that you're done, and you can upgrade/downgrade sshd as you wish without modification.

Oh, and you'll want to verify that listing a requisite module (pam_unix) as both optional and then later requisite in one stack does the same thing as just listing it once as requisite.  It should, if memory serves, but you should check the pam.conf man page just to double-check me.

Hope that helps.

-Coyle

---

### Post by windependence on 2008-06-30
Here is an article you might find useful.

[http://www.securityfocus.com/infocus/1876](http://www.securityfocus.com/infocus/1876)

Good luck!

-Tim

---

### Post by mrpeenut24 on 2008-06-30
Thanks Tim!  That looks great!

---

### Post by thefifthsetpin on 2008-09-29
If you feel that storing people's correct passwords is a security concern, please feel the same way about incorrect passwords.  If you cracked the ubuntu forums and found that I kept mistyping my password with something like 'drowwssaP' or 'drowssap', you might reasonably guess my password was 'drowssaP'.  Similarly if you found that I frequently typed 'passy_the_word', then you could try cracking things like [email]thefifthsetpin@hotmail.com[/email] with 'passy_the_word' as it's common for people to reuse their handle and just change their passwords.  

Furthermore, if one of my passwords was 'passy_the_word' and you logged it, it wouldn't be that unheard of for me to change my password at a later date on your site to 'passy_the_word'.

---

### Post by doobiest on 2012-04-27
I also run a personal server and came to this thread because of the same thought. After thinking it over might I suggest to forget about the passwords, don't worry about them. And here's why.

If you check our logs I bet you'll see that your personal username probably doesn't show up from their brute force list, thus they have no valid account to log into.

I edited my ssh conf to only allow ssh logins from my main account. So any other attempted users obviously will fail.

Then I installed fail2ban and configured it so to ban an IP after 6 ssh failed attempts. 6 attempts to guess the actual username AND my actual password is highly unlikely. 

These attacks come from bots not people doing manual work. They will see the host is down now after a number of attempts and move on.

I don't think it matters what random brute force strings they send as usernames/password, I care more about the 10K requests a day from them you get. Kind of annoying knowing that your server is doing work (processing attempts) that you don't want it to do.

Lastly, rather than parsing logs to see password patterns, parse logs to see username patterns. This is my log data since January. You can see based on the number of occurrences these are account names that you'd probably want to avoid using.


root@LinuxBox:/var/log# zgrep ssh auth*|grep "Invalid user"|cut -d ' ' -f 8|sort|uniq -c|sort -n|tail -n 17
      1 zenoss
      2 cron
      2 linux
      2 samba
      2 staff
      2 tomcat
      2 webmaster
      3 fluffy
      3 info
      3 sales
      3 sjobeck
      3 support
      4 oracle
      4 postgres
      5 guest
     12 admin
     29 user

---

### Post by nothingspecial on 2012-04-27
Thanks for the information, but please don't bump very old threads to the top.

Closed.

---

