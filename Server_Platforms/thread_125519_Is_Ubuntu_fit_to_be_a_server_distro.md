---
title: "Is Ubuntu fit to be a server distro?"
date: 2006-02-04
forum: Server Platforms
---

### Post by hachre on 2006-02-04
Hi there,

I wanna start thinking about replacing certain other distros with Ubuntu on my servers...

Is Ubuntu up for the challenge?


**_What I need:_**
[LIST]
[*] Current packages of big server software (apache2, php4 or maybe 5, courier mail server, bind, vsftpd, mysql, and some i may have forgotten)

[*] Security patches that I can easily install without having nightmares of adapting 300 config files or getting to work each and every server again afterwards (ie security patches against my versions and not an enitre upgrade to a newer versions that includes the fixes; that means I want security fixes for php4 rather than being forced to upgrade to php5)

[*] The optional choice to install a new feature update of a certain program like for example php4 -> php5 if I want to. 
[/LIST]

Is Ubuntu going to be the distro I'm looking for?

Thanks for your replies
Harry

---

### Post by venzen on 2006-02-05
Hi Harry,

You can do everything you listed with Ubuntu. Security and package upgrades are all achieved with 2 button clicks from the package installer GUI, or by issuing the following at the command line:

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

That's it. Some stalwarts argue in favour of Debian as a 'better' server distro, but since Ubuntu is based on Debian anyway and now includes a server-specific install CD/ISO I do not see any major advantages of one over the other.

In my own case, I work for an organisation which has migrated ALL of its workstations and servers over to Ubuntu over the past 18 months. This makes administration a breeze and allows, for example, for one server to download and cache package upgrades and all other hosts in the network to get their security and package updates from this central location rather than individually over the net.

Our Ubuntu server runs all of the packages you mention plus some other services... without problems and up-to-date.

Regards

---

### Post by hachre on 2006-02-05
Very nice, thanks for the info!

---

### Post by imagine on 2006-02-05
[QUOTE=hachre]Current packages of big server software (apache2, php4 or maybe 5, courier mail server, bind, vsftpd, mysql, and some i may have forgotten)[/QUOTE]
Just be aware that the Ubuntu stable releases are basically snapshots which get updated every six months. An exception are security updates which become available via apt-get soon after they are relased.
So if you want to live on the edge and have the newest releases running all the time (for unknown reasons), Ubuntu isn't a good choice.

---

### Post by alamba on 2006-02-05
venzen can you point me to a link that would describe how you can set up a central server to download updates and then have the rest of the machines on the network pull updates from there?

Thanks!

Akshay

---

### Post by Zed on 2006-02-05
Make sure the universe repositories are in your /etc/apt/sources.list, and:

```
sudo apt-get install debmirror
```

It makes it easy to choose just one architecture and release (you might also prefer to exclude multiverse.)  For instance, here's how you could use debmirror to build a Breezy i386 repository from utah.edu by rsync:

```

debmirror -p -v --nosource -h ubuntu.cs.utah.edu -e rsync -r :ubuntu -a i386 --section=restricted --nocleanup -d breezy --skippackages --ignore-missing-release --ignore-release-gpg --ignore-small-errors   ubuntu

```

Here are some other ways:

[http://apt-proxy.sourceforge.net/](http://apt-proxy.sourceforge.net/)

Always choose a [mirror](https://wiki.ubuntu.com/Archive) near you. (And, everyone considering this, please be polite: do this if it'll mean less overall use of the mirrors' bandwidth, not more.)

---

### Post by LordHunter317 on 2006-02-05
> **hachre]Is Ubuntu up for the challenge?[/quote]It depends.

> [*] Security patches that I can easily install without having nightmares of adapting 300 config files or getting to work each and every server again afterwards (ie security patches against my versions and not an enitre upgrade to a newer versions that includes the fixes said:**
> Uhh, I don't know any vendor who tells you to fix things by moving to a new *major* release unless the software is ancient.

And here's where the pickle comes out: Ubuntu only provides backported security patches for main and main only.  They don't assure you of regular updates for universe, and you will need to use univervse.  For me in production, this is a no-go.  For home systems, it's not as bad.

[quote][*] The optional choice to install a new feature update of a certain program like for example php4 -> php5 if I want to. You can run them side-by-side, if you really want to.

[quote=venzen]
That's it. Some stalwarts argue in favour of Debian as a 'better' server distro, but since Ubuntu is based on Debian anyway and now includes a server-specific install CD/ISO I do not see any major advantages of one over the other.Their security policy isn't dumb, when they have a security team *sigh*.

---

### Post by hachre on 2006-02-05
[QUOTE=LordHunter317]Uhh, I don't know any vendor who tells you to fix things by moving to a new *major* release unless the software is ancient.[/QUOTE]

I was referring to Gentoo...

Thanks for all the replies so far :)
Harry

---

### Post by majikstreet on 2006-02-05
I didn't read much of the thread, but here's my experience:

I used to run an apache, php5, mysql, and ftp server with ubuntu.. well it's still up, but I switched my sites to professional hosting.... I think it was easy enough.. I had no issues doing it.. I was unsuccessful with postfix, but I probably screwed it up by trying to install it so many times..

majikstreet

---

### Post by tonkatruck on 2006-02-18
no

---

### Post by UbuWu on 2006-02-18
Probably best to wait 2 months, as dapper will be supported for 5 years on servers.

---

### Post by bjweeks on 2006-02-18
Debian is better for a production server if your loseing money if its down, because they have better testing

---

### Post by Revolution on 2006-02-18
There is a very good reason why professional web hosts run distros like Redhat 9 or even Fedora. They are based on a mature build and are regularly updated. (we currently have 4 shared servers running FC1)

You only have to look through places like [http://www.ev1servers.net](http://www.ev1servers.net) to see what distros they offer.
It'll be a while before you see Ubuntu among them.
Of course Redhat do provide "incentives" to datacenters.

Now for home or "behind the firewall" Lan servers Ubuntu will do quite nicely.
Although according to admins I've spoken to, Windows Server 2003 is the preferred "company network" package. But thats for a whole 'nuther thread.

---

### Post by LordHunter317 on 2006-02-18
[QUOTE=Revolution]There is a very good reason why professional web hosts run distros like Redhat 9 or even Fedora. They are based on a mature build and are regularly updated. (we currently have 4 shared servers running FC1)[/quote]No competent professional site runs an unsupported distro.  Nevermind the fact that RH9 has more security holes than swiss cheese.

---

### Post by Revolution on 2006-02-18
I guess you didnt know you could patch RH9

---

### Post by az on 2006-02-18
[QUOTE=LordHunter317]Ubuntu only provides backported security patches for main and main only.  They don't assure you of regular updates for universe, and you will need to use univervse.  For me in production, this is a no-go.  For home systems, it's not as bad.
[/QUOTE]

How will this change with Dapper?  Won't Dapper have more server-candy in main?

---

### Post by LordHunter317 on 2006-02-18
[QUOTE=Revolution]I guess you didnt know you could patch RH9[/QUOTE]And it still has security vulnerabilites with all official patches applied.

Running Fedora or RH9 on a server screams incompetence, when you can just run CentOS.  Almost all of RHEL (minus support and RHN) without any issues.  You can even build the RH patches and apply them for like 99% of the distro.

It's just inexecuable.  There's no valid reason beyond, "legacy".  And a public web hosting provider shouldn't be using that as an excuse, they don't have one they need to maintain w.r.t. OS.  They're not running anything that should care that much about specific OS version.
 
[quote=azz]How will this change with Dapper? Won't Dapper have more server-candy in main?[/quote]That's the idea, but I haven't followed it enough to say whether it will truly make a difference though.  For the LAMP folks, maybe.  That's not me though.

---

### Post by UbuWu on 2006-02-19
[QUOTE=azz]How will this change with Dapper?  Won't Dapper have more server-candy in main?[/QUOTE]

Yes. This is the list of programs that will be supported for the full five years:

[http://people.ubuntu.com/~cjwatson/seeds/ubuntu-server-dapper/server](http://people.ubuntu.com/~cjwatson/seeds/ubuntu-server-dapper/server)

All other stuff from main will be supported for three years.

---

### Post by UbuWu on 2006-02-19
See also [https://wiki.ubuntu.com/ServerFaq](https://wiki.ubuntu.com/ServerFaq)

---

### Post by hachre on 2006-03-02
Thanks for all the replies :)

---

