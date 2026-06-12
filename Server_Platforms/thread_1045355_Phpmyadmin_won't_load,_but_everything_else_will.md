---
title: "Phpmyadmin won't load, but everything else will"
date: 2009-01-20
forum: Server Platforms
---

### Post by Blairboy on 2009-01-20
I'm a bit perplexed currently.  When I try to load up phpmyadmin, my browser (I've tried it in about 4) offers a phtml file for me to download, as opposed to actually loading phpmyadmin.  Now, I know for a fact that apache is set up correctly, because wordpress and a number of other php dependent things load up just fine on the server, just not phpmyadmin.  Any ideas?

---

### Post by drubin on 2009-01-20
How did you "install" php myadmin

---

### Post by Chris of Arabia on 2009-01-20
I installed the other day (could have even been yesterday - time flies) following the instructions in the 8.04 LTS documentation - [PHPmyAdmin: Installing from a package]("https://help.ubuntu.com/community/phpMyAdmin")

Two steps and went on nice as you like - very difficult to get wrong from what I saw.

---

### Post by drubin on 2009-01-20
I don't like the idea of using apt-get to install php code that runs in the web root.

I suggest a much simpler way of just going to the phpMyadmin home page downloading the latest version. Unzip it to a folder in your webroot and then just hit that folder in your browser and follow those steps.

There is no compiling or any thing involved.

---

### Post by Blairboy on 2009-01-20
Not sure why apt decided to crap out on me, but I downloaded/extracted it and all's well.  Thanks for the help.

---

### Post by drubin on 2009-01-20
> **Blairboy said:**
> Not sure why apt decided to crap out on me, but I downloaded/extracted it and all's well.  Thanks for the help.

Don't worry I have never heard of a successfull install of phpmyadmin from apt-get.

Glad it is working

---

### Post by MeneM on 2009-01-20
I use to install via aptitude.

I'd always choose aptitude over manual, since it is much more likely to be updated (in case of security issues and what not) by apt then when I have remind myself to check for updated myphpadmin pages.

---

### Post by drubin on 2009-01-20
> **MeneM said:**
> I use to install via aptitude.

I'd always choose aptitude over manual, since it is much more likely to be updated (in case of security issues and what not) by apt then when I have remind myself to check for updated myphpadmin pages.

in general I would agree. Just not with phpmyadmin

---

### Post by MeneM on 2009-01-20
> **drubin said:**
> Just not with phpmyadmin

Really? Because you only use it internally? Or is phpmyadmin not updated in Apt? I'm seriously interested.

---

### Post by drubin on 2009-01-20
> **MeneM said:**
> Really? Because you only use it internally? Or is phpmyadmin not updated in Apt? I'm seriously interested.

[LIST]
[*]I don't think it is that updated. 
[*]It requires you to have root access to install it. (That is not required if you have access only to the webroot files). 
[*]I could never get it to work. (via apt-get)
[*]I have never seen any one on the forums go. Woo apt-get install was much easier then downloading the php files.
[*]I have also found it much similar to download unzip. then fiddle in your appache2.conf file (generally most standard users should never fiddle with the defaults of servers unless they know what they are doing)
[*]It is webscripts and I feel should sit in your webroot.
[/LIST]

Hope this explains my reasoning for it.

btw: Same reason I would never recommend installing phpbb3 via apt-get

---

### Post by MeneM on 2009-01-20
I see your point, makes sense.

Some things are better managed by a good admin.

I like you avatar BTW ;-)

---

### Post by drubin on 2009-01-20
> **MeneM said:**
> I see your point, makes sense.

Some things are better managed by a good admin.

I like you avatar BTW ;-)

hehe Thanks :)

btw I wont install phpmyadmin on production servers. :). the idea of brute force mysql logins... or a security valunlebity even with apt-get. phpmyadmin almost has root mysql access to your db's. with interface to run raw sql...

---

### Post by Chris of Arabia on 2009-01-20
> **drubin said:**
> 
[LIST]
[*]I have never seen any one on the forums go. Woo apt-get install was much easier then downloading the php files.
[/LIST]


Maybe I got lucky, but it's what happened. It does make interesting reading that the method recommended in the official documentation isn't highly thought of though. I'll bear it in mind for the future.

---

### Post by drubin on 2009-01-20
> **Chris of Arabia said:**
> Maybe I got lucky, but it's what happened. It does make interesting reading that the method recommended in the official documentation isn't highly thought of though. I'll bear it in mind for the future.

Remember this is just my ramblings.... As with the interwebs it is almost always a good idea to get a 2nd or 3rd opinion before making final decisions.

---

### Post by Chris of Arabia on 2009-01-20
Generally speaking, if I can get one opinion (other than my own) I'm happy ;). Worth noting that your recommended solution is how I have it installed with IIS7 on my Vista box - seems to work quite happily that way too.

---

### Post by cariboo on 2009-01-20
@drubin:

See screenshot of successful installation of phpmyadmin using Synaptic. :)

Jim

---

### Post by drubin on 2009-01-21
> **cariboo907 said:**
> @drubin:

See screenshot of successful installation of phpmyadmin using Synaptic. :)

Jim

Glad yours worked. **I** still wont recommended it. :). To me unziping a zip file seems simple and less complicated.

---

