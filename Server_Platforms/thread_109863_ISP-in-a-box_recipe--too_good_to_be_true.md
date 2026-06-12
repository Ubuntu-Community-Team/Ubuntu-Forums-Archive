---
title: "ISP-in-a-box recipe--too good to be true?"
date: 2005-12-29
forum: Server Platforms
---

### Post by nordmann on 2005-12-29
I came across a neat-looking recipe for how to quickly set up an all-in-one "ISP" box using Breezy Badger.  The article shows how to quickly set up a box with most of the services that most small-time ISP wannabes want to have, such as email, FTP, and Apache.  I would love if a server admin guru could look it over and vet it for any potential problems, particularly in the area of security.

The article is located here:

[http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10)

I'm not sure what ISPConfig is, which is installed as the final step.  But I probably won't do that step, anyway.  Until I really know what I'm doing, I would prefer to administer my server at the bash prompt over SSH.

I have only a small amount of unix server administration knowledge and experience, but from what little I know this recipe looks pretty decent.  Yes, ideally we run our different servers on seperate physical boxes.  But I only have one IP address to use along with some hand-me-down server hardware--no Cisco PIX boxes for me.  And this recipe at least has me running named in a chroot jail, for example.

However, I know that in the field of server administration, what you don't know *will* hurt you, so if anyone sees anything too egregious, I'd love it if you could raise a red flag and maybe explain what alternative way you might do things.

And if this article really is good to go as is, then I figure other "junior" server administrators might like to read it, too!

---

### Post by xequence on 2005-12-29
Is this like a... Thing where you can be your own ISP?

---

### Post by nordmann on 2005-12-29
Well, sort of.  You would need to have a static IP address, which rules out most home installations.  (Dynamic DNS doesn't work too well for SMTP.)

Go have a look and you'll see right away what it's about.

---

### Post by bjweeks on 2005-12-29
[QUOTE=nordmann]Well, sort of.  You would need to have a static IP address, which rules out most home installations.  (Dynamic DNS doesn't work too well for SMTP.)

Go have a look and you'll see right away what it's about.[/QUOTE]
You want to start a WISP?

---

### Post by nordmann on 2005-12-30
[QUOTE=bjweeks]You want to start a WISP?[/QUOTE]

A wireless ISP?  Nah.  I'm not really looking to become an ISP myself--I just need to have the equivalent of a small NOC for small-time use by some of my web development clients.

Basically, my story is that I'm a Web/J2EE developer, and now that I'm starting to do moonlighting work, some of my clients are asking me to take over their hosting.  Now, it turns out that a good friend and longtime business partner of mine owns and runs an ISP, so the natural arrangement for me is to hook up with him.

But I'm starting small, and I can't afford high-end equipment or support yet.  I'm not going to ask my buddy to give me something for nothing.  So I have a rack off in a corner of his office outside of his climate-controlled, air-filtered, diesel-backup electric, etc. NOC room.  It's hooked into the NOC room with a wire and one IP address.  I'm giving him a small consideration for this courtesy, and maybe if things take off, I'll be able to move into his NOC room and add machines.  But for the time being, an ISP-in-a-box is just about what I can afford and what will suit my needs.

And I've talked to many other IT/Web people who could use an arrangement much like mine and who don't have lots of time and money to spend, so I thought I'd bring this article to people's attention.

---

### Post by steve_250 on 2005-12-30
Hello all, obviously my first post.
Just want to say thank you to everyone.  I have samba and apache running a home server for my personal use thanks to everything I have read here.
(questions will follow) :D 

In answer to Nordmann, I also, have a dynamic address assigned at home.  I use dyndns.com to assign a static on the net.  It updates my dynamic and points to it through a name you get to choose.  Works great for us little guys.
Oh, and it's free!

---

### Post by Bailx on 2005-12-30
I am also looking at this setup... with a few modifications from these howto's

[http://www.howtoforge.com/proftpd_mysql_virtual_hosting](http://www.howtoforge.com/proftpd_mysql_virtual_hosting)
[http://www.howtoforge.com/virtual_postfix_mysql_quota_courier](http://www.howtoforge.com/virtual_postfix_mysql_quota_courier)

as i'd like to keep users in a database, rather than as system users.

so.. i'd also be interested to see what others think...

---

