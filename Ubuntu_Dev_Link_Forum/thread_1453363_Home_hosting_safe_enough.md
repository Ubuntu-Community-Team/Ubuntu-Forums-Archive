---
title: "Home hosting safe enough?"
date: 2010-04-13
forum: Ubuntu Dev Link Forum
---

### Post by worldsayshi on 2010-04-13
I'm a bit into C and C++ programming, done some python, Virtually no web programming and I've only scratched the surface when it comes to server and network administration. Although I have successfully set up a home ssh and svn server. But I'm somewhat worried about security. Not that it holds much that I can't afford to be peeked at, it's more of a spiritual comfort thing, and Im not that sure on the extent of these "threats" anyway. I've taken the most obvious precautions but I'm sure that anyone with some further experience would do more.
Anyway, I'm thinking of testing out some web programming, maybe set up an home page, but I'm unsure if it's better to set it up on a hosting service or on my own server. Setting it up on my home server might expose and announce it further. Setting up on a server would deprive me of control, money and well, it wouldn't be "mine". What would you recommend?

---

### Post by new_tolinux on 2010-04-13
I prefer a hosting service.

Ubuntu (Linux in general) is quite secure, and setting up a webserver is simple. But that doesn't mean it can not be hacked/compromised.
I'm guessing you'll use that webserver for other things beside running a webserver, which means that you'll have "more" to loose when your security is compromised.

A hosting-service (especially if it's _paid_) has more experience (at least they should have ;))
When their servers are compromised, go down, or whatever else, it's _their_ problem.

Then there's another point, upload speed. A hosting-service has probably a better upload speed than you have. That means your page will be served to any user in less time.

---

### Post by BbUiDgZ on 2010-04-13
If you want to run it from your house you should setup a firewall with a list of ip's from which you want to allow access. i do this at home i run torrentflux (apache,php,python,mysql) on a debian box but use ipcop as a stand alone firewall and allow only http access from my office.

i in no way work for this company or get any sort of payment at all in any form or shape, but you might want to look [here](http://www.slicehost.com) for a cheap dedicated host :lolflag:

---

### Post by cdaringe on 2010-05-03
Just in case you haven't already checked, make sure that your ISPs ToS doesn't have any limitations on what you may be looking to do...

---

### Post by WitchCraft on 2010-06-12
It's no problem, me too I host my websites at my home.

All you need is a server with a static IP, a domain name, and a dns server entry.

You add a dns entry to a free DNS service, everydns.net/zoneedit for example, and then you point your domain name enty to this dns server/s.

Just make sure that your ssh server uses a key for authentication, and not a password. Also make sure you configure the ssh server for EVERY user. You can use the GoogleCheckout sandbox or the PayPal sandbox to add credit card support to your site. You might also want x11vnc and ssvnc. And I'd use git, not svn, if I were you.

Use LightHttp, not apache, and use a secure chroot environment to run the servers. You best use Python, not PHP, that way you can avoid installing PHP and all it's security holes. You could also use mono/.net. Then install a good database server, like PostGre/FireBird/MySQL.

Then you need a mail server and a CMS/Forum. That's all.
If you want, I'd give you some room on my server [under the condition that I get the sourcecode for all executables that I shall put there...]

---

### Post by SoFl W on 2010-06-12
Five or so years ago I ran a website from my house.  I had a separate computer (server), a static IP and R.H. version 7.  The site was simple it had some pictures I wanted to share (hot link) on websites and the gallery software for the family.
My boss wanted to see if I could do it.  First time with linux, he provided the (old) computer.  The thing I learned the most was how often a server gets attacked.

---

### Post by WitchCraft on 2010-06-13
> **SoFl W said:**
> Five or so years ago I ran a website from my house.  I had a separate computer (server), a static IP and R.H. version 7.  The site was simple it had some pictures I wanted to share (hot link) on websites and the gallery software for the family.
My boss wanted to see if I could do it.  First time with linux, he provided the (old) computer.  The thing I learned the most was how often a server gets attacked.

About 4000 attempts on my ssh per month. But no success so far.

---

### Post by worldsayshi on 2010-08-26
/var/log/auth.log
does show some attack attempts, but it seems also that denyhosts is doing a good job. The attacks are comming in short bursts ending with denyhosts adding them to the list.
It also shows tons of messages of the kind:
```

<Date and computer name> CRON[18539]: pam_unix(cron:session): session opened for user root by (uid=0)

```
Not sure what this means. Is it me doing sudo operations through ssh or is it some root proccess going on and off? Or - terrible thought - is it someone who has figured out my password? :o

---

### Post by worldsayshi on 2010-08-26
WitchCraft: Thanks! Valuable tips. As for python, I will think it over. Although I have worked with python and barely looked at php python in web development seems a bit unwieldy and poorly documented in comparison. I suspect it would be more powerful once you can master it though. Powerful, but moving attention away from the web design. *Seems* a bit to procedural for web development...

---

### Post by Maarek Stele on 2010-11-04
A Static IP is not necessary.  You can find a hosting company that will update your IP when it changes such as DynDNS or NO-IP.  You can also use their hosting services as well.  Price range is $30~$40 per year.

All you have to do is setup your Router for Port redirecting of ports 80(web) & 22(ssh, sftp, etc) to the IP of your server.  That's it, any other ports would be due to software requests or any other type of hosting you are offering.  Make sure all other securities are enabled on your router as well, such as leaving your PCs OFF the DMZ, enabling WPA encryption for your wireless, and turning off internet access for your router administration.

once you have LAMP installed, and run your local host check you'll see the default web page.  Or you can try the domain name once it's finally populated or just your external IP address.

If you plan on developing directly on this server make sure it's not the main website where people can see changes, but rather a location within your directory.  Once the changes work, then move them to the correct location. You can also create an alias for your web pages, just google the question or look here in the forums for your answer.  A good idea is to make sure the alias configuration is for local use only just in case someone stumbles across some important scripts that you haven't moved.

---

