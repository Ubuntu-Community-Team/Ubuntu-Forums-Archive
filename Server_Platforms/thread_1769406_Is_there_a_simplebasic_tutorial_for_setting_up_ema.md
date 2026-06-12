---
title: "Is there a simple/basic tutorial for setting up email?"
date: 2011-05-27
forum: Server Platforms
---

### Post by tristram60 on 2011-05-27
I want to put email on my server but after reading through the documentation I am totally lost.  I don't know much about using the CLI but I did set up apache and openssh.  Any links or help would be appreciated.

I have ubuntu server 10.04

Not sure what other details you need...

Thanks for your time.

---

### Post by munzerelli on 2011-05-27
Check this out: [https://help.ubuntu.com/10.04/serverguide/C/postfix.html](https://help.ubuntu.com/10.04/serverguide/C/postfix.html)

---

### Post by tristram60 on 2011-05-27
My understanding is that that is only a small part of the entire process...
I was also hoping for something that it is from a 3rd party, not in the ubuntu documentation.  I found that stuff to be too complicated and not geared toward beginners.

---

### Post by munzerelli on 2011-05-28
Not sure where to find a simple tutorial that would not involve some cli but here are a few more that may be helpful:

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
[http://www.scribd.com/doc/31128654/Install-Guide-Ubuntu-10-04-LTS-Lucid-Lynx-Server-v1-7](http://www.scribd.com/doc/31128654/Install-Guide-Ubuntu-10-04-LTS-Lucid-Lynx-Server-v1-7)

there is also a good pdf that may be helpful 
[https://help.**ubuntu**.com/**10.04**/**server**guide/C/**server**guide.pdf]("https://help.ubuntu.com/10.04/serverguide/C/serverguide.pdf")
hope this helps :)

---

### Post by Ghosthaven on 2011-05-28
Are you trying to setup a mail server, or only trying to send
email from the command line, or only trying to check it?

---

### Post by tristram60 on 2011-05-28
I am trying to set up an email server that allows me to send/receive mail from [email]admin@mydomain.com[/email].  I plan to use outlook or some other mail client to send/receive the mail

---

### Post by HermanAB on 2011-05-29
Just go to the Citadel.org web site and run the Easy Install script.

There is nothing easier.

---

### Post by Tylerjd on 2011-05-29
If you would rather not use Citadel, and still go with setting it up yourself, I would encourage you to take a look at [Webmin]("http://www.webmin.com/") ([http://www.webmin.com/](http://www.webmin.com/)), it is an online GUI for setting up, configuring, and using Linux and UNIX servers. It isn't in the Ubuntu Repos, and requires you to apt-get some dependancies, but I have it installed on every single one of my Servers.

---

### Post by brettg on 2011-06-01
If all you want to do is configure your server so that it can send emails then you will need either a proper, publicly resolvable domain name (with mx record) to send from or an email server in a proper domain that is willing (and configured) to act as a smarthost for you and forward on your emails on your behalf.

You can't just configure postfix/sendmail to send out from 'myfakedomain.com' because the receiving servers will simply reject the mail because they can't resolve that domain and verify the MX record.

It's an anti spam thing.

If you don't have a valid domain or an upstream smarthost to send your mails through then you can use a gmail account for that purpose. 

[This guide is pretty simple to follow]("http://tuxnetworks.blogspot.com/2009/03/mutt-to-remote-smtp-server.html"). All you require is a gmail account to send through.

If you do own a valid domain and have root privileges to your email and dns servers then I would advise you to step away from the keyboard if you aren't fully aware of what you are doing.

---

### Post by tristram60 on 2011-06-02
I do have full access to my own domain and all that stuff but if you think that its a little to complicated I think I will stick with the gmail thing.  All I need is to make my emails look more professional.

---

### Post by HermanAB on 2011-06-03
Howdy,

If you are running your own domain, then you can use Citadel.  As I said, there is nothing easier.  I've been using it for more than ten years on many systems.

---

### Post by andrew.46 on 2011-06-07
If you own your own domain you can use gmail to host your mail needs, I have done this for a while with andrews-corner.org and have had no problems. It eliminates a lot of the painful setting up and gives you the address [email]username@domain_name.org[/email].

---

