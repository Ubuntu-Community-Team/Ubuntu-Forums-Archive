---
title: "Which distro for a web server? (php, apache, mysql)"
date: 2006-05-02
forum: The Cafe
---

### Post by snoopgst on 2006-05-02
Can you guys recommend a good distro to run as a webserver?  I need it to be able to handle php, apache, and mysql.

---

### Post by mjm115 on 2006-05-02
Check out [http://www.howtoforge.com/taxonomy_menu/1](http://www.howtoforge.com/taxonomy_menu/1)

Look to the left and you will see links that show you how to set up the services that you need.  Most linux distros, when configured properly, will be able to provide you with what you need.

---

### Post by tribaal on 2006-05-02
Well any distro would do, really.

Now if I were to pick one or two, I'd say [Debian]("http://www.debian.org") for it's stability and apt-get (thats what I use), installing only a minimal command-line only system, so that ressources aren't used by the graphics and whatnot.

[Gentoo]("http://www.gentoo.org") is a good alternative to Debian IMO, as you build everything from source, making your sytem as optimised as possible. The installation process is a bit steeper though I heard (never installed one myself though).

But again, any distro will do fine, especially if you're not going to setup a really load demanding website.

- trib'

**Edit:** Aaaah I must really be one of the slowest posters around, someone always answers before me :)

---

### Post by Kvark on 2006-05-02
[QUOTE=mjm115]Check out [http://www.howtoforge.com/taxonomy_menu/1](http://www.howtoforge.com/taxonomy_menu/1)

Look to the left and you will see links that show you how to set up the services that you need.  Most linux distros, when configured properly, will be able to provide you with what you need.[/QUOTE]
If you need a howto to set up a server then you're doing it the hard way. And you should not do it the hard way unless you know exactly why the easy way does not suit you. In Ubuntu and probably every Debian based distro (but maybe with other package names in other distros) the easy way which is the right way unless you have a special reason to complicate things is:
```
sudo apt-get install apache2 libapache2-mod-php5 php5-common php5-mysql mysql-server
```
After that the servers are online with the default settings. You will want to change a few of the settings to suit you. For example you should add a root password and non-root users to mysql.

To the original question:
Many say that Debian is king when it comes to servers so thats what I'd try first if I needed a server.

---

### Post by mips on 2006-05-02
For any type for server I would look at something that is Stable & Secure. Those are critical things. Debian would be a good start.

Considered OpenBSD or FreeBSD ?

---

### Post by Specialsauce on 2006-05-02
Go with Gentoo

---

### Post by Virogenesis on 2006-05-02
Don't go with gentoo its unneeded, consider CentOS or WhiteBox, CentOS I've heard gets more updates.
both of these distros are based on red hat enterprise.
Arch gets alot of the update apache and what have you.
Whats the servers job?
Is it just a testing platform or are you looking to host stuff yourself?

---

### Post by beercz on 2006-05-02
I use debian for my web server (apache) with mysql and php - never let me down :-)

---

### Post by helpme on 2006-05-02
Maybe I missed something, but Ubuntu is of course also a good option. Especially dapper, as it will get 5 years of support for a server install.

---

### Post by Virogenesis on 2006-05-02
[QUOTE=helpme]Maybe I missed something, but Ubuntu is of course also a good option. Especially dapper, as it will get 5 years of support for a server install.[/QUOTE]
Actually apache is out of date, so is php and mysql 5 isn't in the repos til dapper so its not that good

---

### Post by DigitalDuality on 2006-05-02
Open and FreeBSD would be my  choice.   But Debian/Ubuntu works as well.

---

### Post by Virogenesis on 2006-05-02
Don't forget about solaris (mentioned it as everyone mentioned BSD's) :)

---

### Post by WildTangent on 2006-05-02
I just use Ubuntu Breezy, though I do have a test server setup with Dapper running all the latest stuff.

-Wild

---

### Post by TrailerTrash on 2006-05-02
Solaris, Fedora, CentOS, and FreeBSD are the ones i like. Xandros has one out now but its not free.

---

### Post by TheCaptain on 2006-05-02
Not Open or FreeBSD if you don't feel like getting into a whole new world of syntax, it is quite different from Linux and not all tools are available in Open and in Free you will have to compile every inch and bit of extra if you want it up to date.

CentOS is the logical choice, for a firewall or a database server i would have chosen OpenBSD, FreeBSD is for desktops, i don't care what anybody says, it's focused on speed and usability, that is a desktop thingy, reliability comes first on servers so CentOS or MAYBE OpenBSD is you are paranoid or just like BSD.

---

### Post by TheCaptain on 2006-05-02
[QUOTE=Virogenesis]Don't forget about solaris (mentioned it as everyone mentioned BSD's) :)[/QUOTE]

Forget about solaris, it's not worth the hassle and you'll be extremely restricted unless you have some G's to waste.

---

### Post by briancurtin on 2006-05-02
im going to go ahead and echo captain on the CentOS choice. its pretty solid in my experience (although it was only a few weeks).

---

