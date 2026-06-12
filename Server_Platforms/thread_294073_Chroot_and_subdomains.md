---
title: "Chroot and subdomains"
date: 2006-11-06
forum: Server Platforms
---

### Post by markokaa on 2006-11-06
I need help with my server.
I need to create this enviroment:
Users home folder is in /home/user
Users can't go anywhere but in there home folder with SSH.
domain.com/~user should be user.domain.com

So how I can do this?

---

### Post by kidders on 2006-11-06
Hi there,

> **markokaa said:**
> Users can't go anywhere but in there home folder with SSH.

Ordinarily, doing this is unnecessary. In any case, locking users out of *everything* except their homes would deny them access to the /bin and /usr/bin directories, system documentation, etc., making their accounts unworkable.

> **markokaa said:**
> domain.com/~user should be user.domain.com

This is a job for your web server. Setting up subdomains involves adding virtual hosts and restarting the service. What web server are you using?

---

### Post by markokaa on 2006-11-06
I use Apache.

And I mean that they couldn't go to /home or / or anywhere else like this what I've done to Proftpd -> [link]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_FTP_user_to_be_.22jailed.22_.28chrooted.29_into_their_home_directory")

---

### Post by kidders on 2006-11-06
Afaik it would be completely impractical to use chroot jails for your SSH users, although (if you *reallllly* wanted to) you could, I suppose. In terms of how they work, FTP and SSH have almost nothing in common, you see.

The way I see it, you'd have to compile a list of all the stuff a typical SSH user will need access to ... basic commands/utilities, their assocated system libraries and documentation, etc., etc. Then you'd have to create symbolic links to them inside every user's home directory. If you didn't, not even "cd" would work for them!

Can I ask why you're providing SSH access at all, if you want to try to keep them out of your system files?

I'm not completely sure about Apache, but on Apache2, you add virtual hosts to /etc/apache2/sites-available and symlink the ones you want to activate in /etc/apache2/sites-enabled. Once you restart the service, they should come alive :-)

---

### Post by pppetter on 2006-11-07
It might just be me, but wouldn't it be possible to just add /home as a virtual host, then every users adress would become [www.mysite.com/user](www.mysite.com/user).
Of course, then your main sites home adress would be /home, but hey, a Symlink would fix that.

You could of course do it the other way around, creating symlinks in your present document root...

---

### Post by kidders on 2006-11-07
A similar setup is already available in apache, using the /~username/ convention. The usual approach is to use "/home/*/www_dir" to expose URLs, rather than sharing /home itself.

Like the o/p, lots of people prefer username.host.tld over [www.host.tld/username](www.host.tld/username) ... among other things, it makes server-side scripting a little more straightforward. If it were me, I'd just create all the virtual hosts in one go, with a bash script.

---

