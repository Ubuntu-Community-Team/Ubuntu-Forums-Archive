---
title: "Which hosting Control Panel is the least invasive?"
date: 2010-04-01
forum: Server Platforms
---

### Post by creatorbri on 2010-04-01
I want to set up a hosting control panel solution on my Ubuntu LAMP server to make it easier to administer virtual hosts, users, databases, and so on. I have used cPanel for years and appreciated its general range of features, but I'm completely disgusted with how drastically the installation seems to alter your system (I highly doubt it even works at all with Debian/Ubuntu).

I'd actually prefer something that was more than JUST a web hosting manager, but that gave me options for managing my server in general. What control panel option would you recommend?

Most importantly, I want something that's going to work well with the Apache config standards that are unique to Debian/Ubuntu and won't require a PhD to setup. :) I really like the default Apache/PHP stack in Ubuntu.

Of course I'm particularly interested in Open Source solutions. The new OpenPanel project sounds really exciting, and I've heard lots of people talking about Webmin. Others I've heard good things about include VHCS, ispCP, and ISPConfig.

Thanks in advance for your advice!

---

### Post by johngreth on 2010-04-01
I use Webmin on my server. It was easy to install and doesn't change anything unless I tell it to.

---

### Post by HermanAB on 2010-04-02
Webmin, Usermin and Virtualmin.

---

### Post by spynappels on 2010-04-02
Webmin does not work well with the Ubuntu/Debian Apache setup, it really screwed with one of my boxes when I was testing it.

I like Webmin for some stuff, like firewall and Samba admin etc, but for Apache it isn't great.

I'm not a great fan of Ebox, but for hosting control, some swear by it.

---

### Post by HermanAB on 2010-04-02
Uhmm, Webmin is configurable.  You need to set it up properly before you clickadabutton, which can be a pain yes, but that doesn't mean that there is anything wrong with Webmin per se.

---

### Post by jfmanamtr on 2010-04-02
+1 for Webmin.

It isn't too hard to configure. I run webmin on an Ubuntu 9.10 box. All I really had to do was add the Webmin repositories, import the key & then install it with apt-get. I went in & cleaned out a few of the modules I wasn't using (like PPP services cause I don't use my server for dial in) & viola. Hope this helps!

~John

---

### Post by Jive Turkey on 2010-04-02
IMHO any all-in-one type of tool is going to have major caveats.  One of the major philosophical paradigms in linux is that applications should do one thing, and do that one thing very well.  

The webmin/virtualmin combination is the best all in one tool I've tested, however I don't reccomend them.  (Actually the very best I've seen is the proprietary control panel used by Dreamhost but you aren't going to be able to duplicate that).  If you go with webmin/virtualmin I reccomend you stay with ssh to do apache, mysql, or postgresql administration on ubuntu.  pgAdmin and mysql admin are both good tools IME.  phpmyadmin not so much.  Administration of any type of ftp server would probably be better done over ssh+nano or vi, as would samba.

On my home server, I currently use the NXserver from nomachine (I have gdm installed on the server) and do pretty much everything via commandline.  Eventually, I'll take gdm off but I do it this way because I have a need for access from windows clients and putty just isn't the same as the linux cli.  Its like having my ubuntu box everywhere I go.

---

### Post by jrssystemsnet on 2010-04-02
> **Jive Turkey said:**
> putty just isn't the same as the linux cli

Ummm... what?

---

### Post by megahost on 2010-04-02
[http://ehcp.net](http://ehcp.net) VERY easy to install and a breeze to use. Also installs the required tools like PHP5, Apache2, and more.

---

### Post by lisati on 2010-04-02
Webmin works well for me, with only the occasional dalliance into SSH or logging directly on to my server.

---

### Post by Jive Turkey on 2010-04-06
> **jrssystemsnet said:**
> Ummm... what?

I was refering to the behavior, particularly the keyboard mapping in putty on windows, versus a terminal on a linux machine.  For me some keys and combinations of keys just dont work how I like on putty.

---

### Post by jrssystemsnet on 2010-04-07
> **Jive Turkey said:**
> I was refering to the behavior, particularly the keyboard mapping in putty on windows, versus a terminal on a linux machine.  For me some keys and combinations of keys just dont work how I like on putty.So change the ANSI terminal type in the PuTTY configs to match the one you're using on the console.

---

### Post by creatorbri on 2010-04-13
I really appreciate all the great input on this. Pretty much everywhere I go I hear great things about Webmin, so it seems like the one to try.

What I'm really most interested in is finding some tool (if such a tool exists) that allows me to manage Apache Virtual Hosts, from a web GUI interface, hopefully without screwing with the way that Ubuntu/Debian currently handle those (i.e., the "sites-available" directory structure). It would also be super nice if it let me configure email accounts, user storage directory limits, and the like as well, but if I can find a separate GUI tool for each of these items, I can handle that just fine. phpMyAdmin will be used for DB config regardless.

Several of you mentioned the importance of customizing your Webmin installation. Any particular advice on that subject? Particularly on how to avoid screwing with Apache too heavily?

Thanks again!

---

