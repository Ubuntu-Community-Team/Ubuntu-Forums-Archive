---
title: "OpenSSH 5.0 - How Do I Setup Chroot?"
date: 2008-04-09
forum: Security Discussions
---

### Post by umechanism on 2008-04-09
I have downloaded OpenSSH 5.0 and installed it on my Kubuntu computer.  I can connect to it remotely from anywhere which is great!  However, I would like to allow a few family members to connect as well but restrict them to just one folder.  The folder's name is "Family".  I understand that Chroot is the way to do this and that OpenSSH version 5.0 has made this much easier to do than previous releases of the OpenSSH software.  

Apparently, it is not easy enough for this Noob (that's me) so could someone please explain how I can restrict access to other users to just the "Family" folder?

Thanks!
Mike

---

### Post by umechanism on 2008-04-09
...and here is the article where I read about the new OpenSSH Chroot functionality.
[http://it.slashdot.org/article.pl?sid=08/02/20/1637259&from=rss]("http://it.slashdot.org/article.pl?sid=08/02/20/1637259&from=rss")

---

### Post by hyper_ch on 2008-04-09
I use MySecureShell to do that...

---

### Post by umechanism on 2008-04-09
I'll take a look at this but I'd prefer to use OpenSSH for this because my computer is quite old and it doesn't really need another program running in the background.  

Can someone else give me some direction here?

Thanks!

Mike

---

### Post by hyper_ch on 2008-04-09
MySecureShell is a just another shell like bash that can be applied to the user... you should not notice any impact. On Windows you'd use then WinSCP... on Linux also some SCP capable program (I use Konqueror)...

you connect then through SSH to the computer and then you are locked into your user folder.

---

### Post by umechanism on 2008-04-09
Ah...I see that now.  Okay, I'll look at this more seriously now.  However, the purist side of me still wants to do this with OpenSSH 5.0 because I'm hard headed and can't let the details go. :)

Also, I'm getting confused on what to configure.  I'm running OpenSSH, DenyHosts, and (soon to be) MySecureShell all of which have their own config files for user access.  I'm sure that there is a way to have conflicting configs setup which would mess things up.  A little direction here would help.

It's tough being a noob. :confused:

---

### Post by hyper_ch on 2008-04-10
MySecureSheel has its own config files... I use it for the following:

On my webserver I want to give secure access to a website to others. The software I'm running for managing normal websites is confixx.

However confixx allows differend kind of logins (shell, ftp, ....) but out of convenience chrooted ssh or rather chrooted scp the kind of access I want to give.

So, there's the normal user - in that case it's "web21". All files are owned by hime and the group belongs to apache. What I did now is create a new user. Changed his shell to MSS and also his home folder to /var/www/web21. Then I "aliased" his username to "web21" by altering his UID in /etc/passwd to the one of web21. So that if he logs in he will also be owner of those files.

In the MSS config I then also made an special entry for that user to user /var/www/web21 as chrooted home which he may not leave.

Well, that's how I did it this far. It might be that OpenSSH 5 will make things easier, however I do not want the user to have a real shell access... only secure file transfer.

---

### Post by kevdog on 2008-04-10
MySecureShell -- Im going to have to check that out.  Ive always used the module known as jailkit.

[http://olivier.sessink.nl/jailkit/](http://olivier.sessink.nl/jailkit/)

The support forum for this is really good, and the author oliver responds rapidly (within an hour or so).  It takes about 1-2 hours to initially setup -- the reason for that is that I had to go through the examples in my mind a few times to actually understand what was going on.  The documentation however if fairly complete along with the user forums.

---

### Post by hyper_ch on 2008-04-10
I like MSS quite a bit... only problem (with their page is), that the translation is done by google ;) but then you still can understand it ;)

---

### Post by dperfors on 2008-04-11
This is a quite from [this](http://undeadly.org/cgi?action=article&sid=20080409110634) website:
[quote="undeadly"]Here's a quick list of steps I used to make ChrootDirectory work:

    * mkdir -p /var/www/sites/user1/home/user1/www
    * Add user1 to wwwusers in /etc/group
    * Add to /etc/ssh/sshd_config:

              Match Group wwwusers
              X11Forwarding no
              AllowTcpForwarding no
              ForceCommand internal-sftp
              ChrootDirectory /var/www/sites/%u

    * If using public-key authentication, copy authorized_keys file to /var/www/sites/user1/home/user1/.ssh and create a symlink to /var/www/sites/user1/home/user1 in /home.
    * Configure web server to point to /var/www/sites/user1/home/user1/www for user1's website.

Using /var/www/sites/%u ensures that user1 can only see user1's home directory. The lines in sshd_config also prevent ssh tunneling and X11 forwarding. To add more users, add them to wwwusers and create, for example, /var/www/sites/user2/home/user2/www[/quote] Perhaps it helps :)

---

