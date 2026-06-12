---
title: "Mail Server Software"
date: 2006-03-10
forum: Server Platforms
---

### Post by OPaul on 2006-03-10
I'm looking to set up a Ubuntu mail server. Right now my mail is being served with Alt-N's MDaemon on a Windows machine. The linux alternative needs to be able to support IMAP and Web Mail, as well as be able to connect to an open relay database to filter out SPAM mail, and detect viruses (either with a built in scanner or by using another).

---

### Post by gruepig on 2006-03-11
Without knowing what your needs or preferences are, it's hard to say what you should use.  But you've got lots of options to choose from.  Here are some things I've used:

SMTP server: postfix, exim, qmail, sendmail.  All of these support using DNSBLs (e.g., reject_rbl_client in postfix) as well as lots of other spam filtering techniques (e.g., [http://ww.postfix.org/uce.html)](http://ww.postfix.org/uce.html)).

Spam/virus detection: spamassassin, clamav, ravantivirus.

IMAP server: cyrus, courier.

webmail: imp, squirrelmail.

For example, one setup I had was postfix, spamassassin, clamav, cyrus, squirrelmail (as well as saslauthd for smtp auth and mailman for mailing lists).

I encourage you to look at the docs for various SMTP and IMAP servers and see what you will be most comfortable with.

Ask if you have more questions.

---

### Post by OPaul on 2006-03-11
So there is no all in one solution with Linux?

---

### Post by btdown on 2006-03-11
yea im in the same boat.... is there an all in one?

---

### Post by robert_pectol on 2006-03-12
Someone mentioned Hula to me a while back, but I haven't looked into it too much yet.  It looks nice though.  Perhaps it will do what you need.
[http://www.hula-project.org/Hula_Project](http://www.hula-project.org/Hula_Project)

Anyway, good luck with your project.

---

### Post by gruepig on 2006-03-12
There are probably several all-in-one solutions (which is to say, bundles of several packages, which do various things depending on your requirements); I've never looked for one, since I generally prefer to build things for myself, so I don't know.  I think if you research the available software a bit, you'll get a much better understanding of mail services.

In Linux, it's easy to install as many software packages as you need.  I think postfix even comes in the default install of Ubuntu (though I could be wrong).  For something approximating an all-in-one, try 'sudo apt-get update && sudo apt-get install postfix postfix-doc courier-imap-ssl clamav imp4'.

One thing I forgot to mention earlier ... Will you have local user accounts, or are you authenticating against LDAP/directory service?  For the latter, also install postfix-ldap and courier-ldap (or equivalent).

---

### Post by btdown on 2006-03-12
Hula looks great but its not ready for prime time. I was able to get it working in Dapper, but the documentation currently is not sufficient to accomplish anything. ;( i couldnt even figure out if existing unix shell users had an account, or if they needed to added from the admin page. If you go to the admin page, there's no (no way I can see) to add users.

I wish there was an open source distro (preferably Debian/Ubuntu variant) specifically  configured for small businesses needs (email/firewall/vpn/avirus/spamfilter/etc)----Like Clark Connect! Its perfect, but the startup I'm working for can't afford it. Yes, all those things are in your standard Ubuntu distro, but how many mere mortals would be able to set it up?

---

### Post by drakkan on 2006-03-12
for an all in one solution try this:

[http://www.vhcs.net/](http://www.vhcs.net/)

---

### Post by Tortanick on 2006-03-12
I'm also after a dedicated mail server, I was going to install the [Red Hat E-mail server]("http://sourceforge.net/projects/rhems/"),  It said supports All POSIX Operating systems but I can't get setup.sh to work.

If anyone here is caperble of figureing out and writing a guide for geting it working on ubuntu please do. Its a very impressive all in one server.

---

### Post by Soleil-Raid on 2006-03-12
If you are dead set on having a one-stop solution, then I'd advise looking at the courier suite. This will handle SMTP, POP3, and IMAP.

Most webmail setups under Linux are PHP/Perl/Python setups that talk to an IMAP server. This is actually a good thing, because it lets you change the back or front end without upsetting the other.

---

### Post by OPaul on 2006-03-13
Because I'm migrating my mail server from Windows to Linux, is there anyway to synchronize all the mail from the old mail server with the new mail server?

---

