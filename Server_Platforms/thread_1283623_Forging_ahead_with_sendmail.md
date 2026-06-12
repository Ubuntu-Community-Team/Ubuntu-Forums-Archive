---
title: "Forging ahead with sendmail"
date: 2009-10-05
forum: Server Platforms
---

### Post by Vegan on 2009-10-05
I have finally got my domains working the way I want. I changed my /etc/resolv.conf to localhost and my linksys box, works fine when I use DIG ubuntu.com or any other valid domain such as one of my own.

Now I have a GMAIL account, I would like to leverage it if possible but I would accept other ideas such as one of my domains.

I would like to leverage SENDMAIL to send messages such as error reports etc. I also wanted to use it from PHP to send messages from the web site.

Thoughts? :confused:

---

### Post by yknivag on 2009-10-05
```
sudo apt-get install postfix
```

In the set-up chose "Internet domain" and all will work out of the box!

Sendmail is fine but horrendously complicated to configure...

---

### Post by nix4me on 2009-10-05
I also recommend postfix.  Much easier to configure, and better support available.

---

### Post by Vegan on 2009-10-06
I already have that installed, so what is next.

---

### Post by yknivag on 2009-10-06
If it's installed correctly then it should simply work.  Have you tried running a php script which sends an email?  If so, what happened?

---

### Post by Vegan on 2009-10-06
So I wanted to use my gmail address as the source, anything I need to look at?

---

### Post by yknivag on 2009-10-07
Just specify the source address in the email headers. How you do this will depend on what you're using to send the email.

---

### Post by Vegan on 2009-10-08
I using postfix as that is the default choice with tasksel.

I wanted to be able to use it generally from my web sites for forum validations etc.

The problem I see is there is no conspicuous file to edit with the particulars.

---

### Post by yknivag on 2009-10-09
There are settings files (in /etc/postfix/ I think) but I've never yet come across a situation where it hasn't just worked out of the box.

What "particulars" are you trying to edit?

---

### Post by Vegan on 2009-10-09
I looked at that directory, nothing seemed to be what I was seeking. I have several vhosts on my web server that I need to look after.

The email will be sent from phpBB my forum, but also from PHP programs.

---

