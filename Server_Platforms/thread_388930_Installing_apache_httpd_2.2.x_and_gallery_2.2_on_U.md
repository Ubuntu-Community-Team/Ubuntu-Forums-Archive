---
title: "Installing apache httpd 2.2.x and gallery 2.2 on Ubuntu 6.10 Server?"
date: 2007-03-20
forum: Server Platforms
---

### Post by AndR on 2007-03-20
Hi,

I have Ubuntu 6.10 up and running nicely. I did *not* choose LAMP installation, so httpd/mysql/python are not installed. I installed sshd and samba afterwards though. I am almost a newbie when it comes to Linux, but am not afraid of the console either.

I would like to get apache http server v2.2.x installed, along with gallery2 version 2.2. However, they are not listed in the repositories (apache 2.0.55 and gallery 2.1.something are the latest I could find in packages.ubuntu.com).

In the future, I would also like to be able *update* apache and gallery2 via apt-get update.

Question:

Is it possible to install apache 2.2 and/or gallery 2.2 so that the apt-get update method works nicely for them in the future? If so, how? I must stress that the ability to update via apt-get is invaluable to me, although I don't mind if the first-time installation is a bit more complicated.

Please point me in the right direction -- I do not want to end up in the situation where I have apache 2.2.4 (and gallery2 v2.2 for that matter) running but cannot easily update it/them.

Although I know how to use apt-get and how to administer the server (at least to some extent), a very short lesson (or pointer to one) on ubuntu/debian package (in)compatibility and especially updatability would not hurt either ;-) -- although I have been Googling a lot I decided to ask here before I plunge.

Thanks for any help,
AndR

---

### Post by AndR on 2007-03-20
Ahh,

Finally I found something enlightening on the matter...

Apparently I need to have Feisty (7.04) installed in order to get the latest apache2 and/or gallery2 packages - the newest versions are simply not built for 6.10 anymore.

So, once the official Edgy -> Feisty upgrade comes out (in [April 2007]("https://help.ubuntu.com/community/FeistyUpgrades")) I'll upgrade to Feisty (7.04) and then I'll be able to install apache2 v2.2.x and gallery2 2.2.x...

Someone wiser please confirm that I'm on the right track here :-k

Cheers,
AndR

---

### Post by Bubbel on 2007-03-27
Not so, i fear.

I have updated to 7.04 beta and Apache is at 2.2.3, but gallery stics at 2.1.2 :( 

I'm also trying to find a solution. . .but no luck yet.

---

### Post by Brazen on 2007-03-27
> **Bubbel said:**
> Not so, i fear.

I have updated to 7.04 beta and Apache is at 2.2.3, but gallery stics at 2.1.2 :( 

I'm also trying to find a solution. . .but no luck yet.

You have to realize, you will not be able to stick with always having the absolute latest packages when using Ubuntu or Debian.

When a Debian Stable or Ubuntu version is released, whatever version those packages are at, that is the version they will be at through apt for infinity and beyond.   This is done for stability and reliability reasons.

One option around this is to use "backports" repositories, but they have a pretty small number of packages (you might find Apache in it, but most doubtful that you will find Gallery).

Your best bet, if you always want to stay at close-to-the-latest version of packages is to use Debian with the "Testing" repository.  Or if you want the absolute-latest version, use Debian with the "Unstable" repository which despite its name is actually the latest stable versions of software which are just knew to the repos.

However, if you are wanting to use this for a production server, you would be better off sticking with either Debian Stable (which will be Etch next week, hopefully) or Ubuntu Dapper.

---

