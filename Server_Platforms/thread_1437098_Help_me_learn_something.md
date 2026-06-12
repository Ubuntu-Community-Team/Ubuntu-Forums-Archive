---
title: "Help me learn something"
date: 2010-03-23
forum: Server Platforms
---

### Post by wrose51106 on 2010-03-23
I am coming from a MS world and the last few months I have been enjoying Linux at home, in fact I sold my Win7 copy;) 

I absolutley love what you can do without MS! I have no problems installing 9.10 desktop and installing what I need.

Here is my problem, I have grown bored, it was frustrating at first with Ubuntu but now I want to learn more. I built a small server and got myself a static IP at home. I have my ADSL modem coming into my netgear router/firewall. I want to do something but I do not know what!

Perhaps a small web server or ssh, I just do not know where to start or what to really do. I want to have some sort of knowledge. Hopefully this makes some sense...

-Bill

---

### Post by jrssystemsnet on 2010-03-23
Figure out something you'd actually like to do, and do it.

Set up a samba server for sharing your files on the LAN.

Set up a backup server for *backing up* files on the LAN.

Set up a webserver; host a blog.  Or a wiki.  Or a photo gallery.

If you're REALLY a glutton for punishment, set up a mailserver... then come back here in a couple of months and call me horrible, horrible names because I suggested you do that, and you discovered how awful running a mailserver is. :)

---

### Post by wrose51106 on 2010-03-23
I suppose I could setup a web server, I have nothing to host but it should be interesting. Any begineer links you can point me to.

-Bill

---

### Post by jsprev on 2010-03-23
If I was at home and doing this for fun I would look in to something like a media server.

[http://ubuntuforums.org/showthread.php?t=1435381](http://ubuntuforums.org/showthread.php?t=1435381)

---

### Post by kwacka on 2010-03-23
Try setting up a LAMP server (Linux Apache MySQl & PHP). Apache is widely used and probably the best documented webserver but there are others (Hiawatha, Cheyenne, etc).

For tips see [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

For content maybe one of the CMS (content management systems) such as Drupal, Joomla!, Wordpress, etc.

Again see [https://help.ubuntu.com/community/Drupal]("https://help.ubuntu.com/community/Drupal")

Also see [Host your own website for $1.19]("http://docs.google.com/Doc?id=dc7fw57_79hmgqmn3j") (there's a shorter version on this forum somewhere).

Finally, if you want to start building your own site take a look at Kompozer (its in the repositories).

Have fun.   :lolflag:

---

### Post by KB1JWQ on 2010-03-23
Learn Postfix, Dovecot, and get a new job running mailservers.  It's a niche, but a lucrative one.

---

### Post by kgatan on 2010-03-23
Im a noob myself on linux but try to mess around with all functions i can find.
 
As someone said a fileserver with schedueld backup.
VPN so you can access the files from anywhere.
LAMP and FTP, its easy to make it work but there is a ton of configs to learn. Also setup SSL
 
Look into SSH.
Learn scripting with bash and python.
Integration with Windows, shares etc. 
 
 
Have fun! ;)

---

### Post by Iowan on 2010-03-23
[Here]("https://help.ubuntu.com/9.10/serverguide/C/index.html") is the Server Guide - with a listing of some of the different servers available.

---

### Post by Ghost|BTFH on 2010-03-23
The first thing I'd do is learn cli.  The command line offers you a lot of raw power.  If you're comfortable with it already, I'd move on to a personal interest:

Photo editing - Gimp
SVG logo designs - Inkscape
Music Mixing - LMMS, Hydrogen, Jokosher
Programming - Take your pick...

If you're just looking for an insane challenge...take a look at [Linux for Smart Homes]("http://home.comcast.net/~ncherry/") and just go nuts with it.

Become a lesser god of your domain.

Now that's a challenge.

Cheers,
Ghost|BTFH

---

### Post by wrose51106 on 2010-03-23
WOW, thanks guys! Lots of looking ahead of me :)

-Bill

---

### Post by dudumomo on 2010-03-23
There are some many things you can do !
What do you need ?

Webmail ? Blog ? FTP ? Jabber server (IM)? Mediacenter ? (Love that ! with XBMC)

You will learn a lot by installing a mail server I will say.. But not so easy.

I think the best will be to start a LAMP server to host blog, website, or any others things.
Have a look here: [http://www.freelydifferent.com/tutorial-selfhosting/](http://www.freelydifferent.com/tutorial-selfhosting/)
I've done my own tutorial to help people to self-host themselves, Have a try.

Oh, and what about trying to host a webradio or even a seeks node ([http://www.seeks-project.info/wiki/index.php/Main_Page](http://www.seeks-project.info/wiki/index.php/Main_Page))

Have fun !

---

### Post by KB1JWQ on 2010-03-23
Worst case, you learn something.  Dive in, and take good FREQUENT backups!

---

### Post by Maheriano on 2010-03-23
You can do what I do:
- go to [www.x10.com](www.x10.com) and order a bunch of home automation hardware
- forward port 22 on your router to your desktop running SSH
- install Heyu on your desktop
- Control all lighting/appliances in your home from your phone via SSH

- get a Google Android phone
- install Gmote
- use your phone as a remote control to control all media in your home via SSH

- set up your desktop so you can access all your files from your laptop

- set up a webserver, install Wordpress, install Wordpress onto your phone and blog on the go.

That's about all I do with my Ubuntu box.

---

### Post by wrose51106 on 2010-03-23
I have a Droid already, but I just asked the wife and she says its a waste of money to do the home automation :/

But the LAMP project sounds interesting:)

-Bill

> **Maheriano said:**
> You can do what I do:
- go to [www.x10.com](www.x10.com) and order a bunch of home automation hardware
- forward port 22 on your router to your desktop running SSH
- install Heyu on your desktop
- Control all lighting/appliances in your home from your phone via SSH

- get a Google Android phone
- install Gmote
- use your phone as a remote control to control all media in your home via SSH

- set up your desktop so you can access all your files from your laptop

- set up a webserver, install Wordpress, install Wordpress onto your phone and blog on the go.

That's about all I do with my Ubuntu box.

---

### Post by Maheriano on 2010-03-24
> **wrose51106 said:**
> I have a Droid already, but I just asked the wife and she says its a waste of money to do the home automation :/

But the LAMP project sounds interesting:)

-Bill

It should make you money. You can set the heat to turn down an hour after bedtime and turn back up an hour before you wake up. Lights can go on/off with photo relay sensors so if you leave your porch light on all night it can turn off when the sun comes up. You can also purchase a X10 doorbell which will email you when someone rings the doorbell. As well you can have a single button you push when you leave the house which will disconnect all appliances when not in use. I was watching the news today and they found various phone chargers, media centers and computers in a test home which drew over 160 watts total when not even turned on. A Playstation 3 which is turned off will draw 4 watts on its own...and that's turned off! So by unplugging these (or using X10 to disconnect them) you can save about 2 cents per hour or $175 per year. So basically X10 is free if it's set up right.

---

### Post by terazen on 2010-03-24
The very first project I did like this was in 2002.  I setup a firewall, squid proxy, and dns server on a cheapo box I bought on ebay.  I can't remember if I did dhcp or not.  I also bought the o'reilly learning perl book and after reading the regular expression chapter, I setup a script to parse my squid proxy logs to make them easily readable.

The squid and local bind server made my internet a lot faster.  Nowadays with opendns and faster broadband you might not gain as much benefit.  If you have a spare box you could try installing something like pfsense (I think ubuntu equivalent is smoothwall?).

---

### Post by wrose51106 on 2010-03-25
So last night I used SSH and got into my other machine, it worked so thats the first step!

Thanks to dudumomo I used your guide!

-Bill

---

### Post by dudumomo on 2010-03-25
Glad to know ! :D
Thanks for the feedback.

---

