---
title: "is this Bookeeping applacation safe to install?"
date: 2009-11-23
forum: Security
---

### Post by toolmanpaul on 2009-11-23
looking to install bookeeping software named ah3 (autohouse 3) [http://www.linuxlots.com/~ah2]("http://www.linuxlots.com/%7Eah2") This seems to have to have internet access to operate. does that seem right to you. Also this needs support programs installed.....are these also safe to install? ..  Ah2 depends on the following be installed on your system:

     Postgres             Available with most distributions or from [www.postgres.org]("http://www.postgres.org/").  On Fedora Core 3, install postgresql*server*7.4.6*1 and postgresql*7.4.6*1

     Qt3 development      Available in most distributions that offer KDE.  Known as qt2*devel*3.3.3*8 under Fedora Core 3.

     Qt3 Postgres support Qt2 support for Postgres databases.  Known as qt*PostgreSQL*3.3.3*8on Fedora Core 3.

     Perl 5.8             Perl is used for generating the reportsDate::Manip module  

[COLOR=DarkRed]Does anyone know if this is a "safe" program to use? ... if it is , this is exactly what i need to track my business... Thanks[/COLOR]

---

### Post by OpSecShellshock on 2009-11-23
There are a couple of things that have me concerned here. First, there are spelling and grammar errors on the site. I'm not saying this to be a snob or anything, but it makes me wonder about attention to detail in general with regard to the application. Second, there's not really much information available on the home page. You'd think that with these dependencies that there would be a section of the site devoted to explaining what it needs them for.

That said, the dependencies you listed are not harmful. The application simply appears to need a database in order to work (makes sense). If I had to guess from context, I'd say the Internet access requirement has something to do with searching an external supplier database for auto parts, and then automatically placing orders for them. But I can't say for sure because the home page is a bit light on information.

---

### Post by arubislander on 2009-11-23
It seems to be an in-house developed application that the makers decided to share with the world. Their main business being car sales, and English not necessarily being their first language the lapses in grammar could be harmless.

If you are concerned about the security of your system as a whole, maybe you could install the program in a virtual machine? If you are concerned about where the data you enter is going... then you can check the source-code, to be sure and compile from source.

---
After trying to download the source-code, i found that there are no links on that page.. So I headed over to the home-page, and found they were based in Texas...

---

