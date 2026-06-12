---
title: "Zimbra impressions"
date: 2007-12-04
forum: Server Platforms
---

### Post by seepage87 on 2007-12-04
I'm setting up my server and want a good mail server for mostly personal use.  Zimbra seems highly developed, but I get the feeling that not many people use it/recommend it.

What are your impressions of Zimbra?

Is there another solution I should look into with a relatively broad feature set (webmail a must, conversation grouping a plus) that I can get up and running quickly?

Thanks

---

### Post by sethvath on 2007-12-04
Personally I use roundcube but zimbra is certainly more polished. 1 man team and multi million dollar company compared.

---

### Post by seepage87 on 2007-12-04
My only concern with Roundcube is that, while it's definitely on the right track, it's still in pretty early development.  I look at the planned features on its website and they're all things I'm interested in, but they haven't been implemented yet.  If you feel this isn't the case, I'd love to hear otherwise.

I've read some reports of Zimbra being very easy to install, but other reports of it conflicting if you try to install LAMP over it.  I'm really looking for some input into its ease and the general experience using it.

I'm not trying to make an enterprise machine with regards to number of accounts or even security, just something to handle my email and play around with for experience that is feature rich and a pleasure on the end-user side.

---

### Post by sethvath on 2007-12-04
I have little experience with zimbra, the time I spent on their demo is certainly not enough. As for roundcube, anything beats squirrelmail which I had for years. 

As I said, its a 1 man team and I'm certain roundcube is not high on his priority list right now. Its not been updated for a while but it works for me and thats all that counts. I'm certainly not interested in tinkering with a mission critical aspect like mail.

---

### Post by HermanAB on 2007-12-04
Basically Zimbra is heading towards where Citadel is already: [http://www.citadel.org](http://www.citadel.org)

---

### Post by seepage87 on 2007-12-04
I've heard citadel is good, but I'm not that much in need of the groupware features and the web front end seems not as developed (e.g. no threading and kinda ugly, though I know it's CSS themeable).  Given my travel schedule, the web interface is pretty important.  Is there a compelling reason to use Citadel I may not know of?

Another concern is import of contacts and email from my google apps mail.  Does Citadel (or Zimbra) provide a useful method for this?

---

### Post by HermanAB on 2007-12-04
The Blue Citadel theme looks better.

The main thing I like about Citadel is that it is rock solid stable and zero maintenance.  It also scales very well and can handle very large numbers of users.  MS Exchange is Micky Mouse compared to Citadel.

---

### Post by sethvath on 2007-12-04
> **seepage87 said:**
> I've heard citadel is good, but I'm not that much in need of the groupware features and the web front end seems not as developed (e.g. no threading and kinda ugly, though I know it's CSS themeable).  Given my travel schedule, the web interface is pretty important.  Is there a compelling reason to use Citadel I may not know of?

Another concern is import of contacts and email from my google apps mail.  Does Citadel (or Zimbra) provide a useful method for this?
If gmail compatabilty is an issue, why not go for the google apps hosted mail? Its free for the standard account and 50/usr/yr for the premium and thats not too much to pay either.

---

### Post by seepage87 on 2007-12-05
> **sethvath said:**
> If gmail compatabilty is an issue, why not go for the google apps hosted mail? Its free for the standard account and 50/usr/yr for the premium and thats not too much to pay either.

I am using google apps hosted mail right now.  There's a couple reasons why I want to switch, but the most important one is for fun and experience.

---

### Post by primski on 2007-12-05
> **seepage87 said:**
> 
Another concern is import of contacts and email from my google apps mail.  Does Citadel (or Zimbra) provide a useful method for this?

Zimbra has also external POP accounts support and upcoming version 5.0 even external IMAP support, so you can easily import you mail from elsewhere. Not sure about contacts though, there must be a way, i know there is one for importing calendar from google, contacts can probably be done too.

Other than that, zimbra is very easy to install and maintain. Maybe its a little resource hungry, and web ajax client is a little heavy, but very well featured, nice and easy to use, i definitely recommend it, i've been using it for a good year now, and am very pleased.

---

### Post by seepage87 on 2007-12-05
How is your system set up?  Does your Zimbra box also do your web hosting etc, because  people keep saying Zimbra conflicts with a standard LAMP install.  Did you run into any issues?  If so, which ones and were they easy to solve?

---

### Post by primski on 2007-12-06
> **seepage87 said:**
> How is your system set up?  Does your Zimbra box also do your web hosting etc, because  people keep saying Zimbra conflicts with a standard LAMP install.  Did you run into any issues?  If so, which ones and were they easy to solve?

Yes, i have some web hosting too, only a few pages tho, for friends etc...

Zimbra comes shipped with its own web server, so yes, it does conflict with apache, if you run it on default port, 80. Thats why I had to change default zimbra's web port to 8080, you can do that during installation so no problems there.

Zimbra's MySQL runs on its own port, so it wont conflict with your already installed version.

Other than that, there are no major issues with it, installer is very easy and straightforward. You just have to make sure you have all the prerequisites installed. (check howto's below)

Keep in mind, that only Ubuntu 6.06 LTS x86 is supported, so if you have any other release than that, you might have issues Im not aware off at the moment.

Check out these two howtos I always keep handy when installing zimbra:

[Howto 1](http://www.tickus.com/?q=node/15)
[Howto 2](http://www.bluishcoder.co.nz/2007/01/installing-zimbra-on-ubuntu-610.html)

Good luck mate and report how is it going :)

---

### Post by garba on 2007-12-06
just another piece of bloatware trying to mimick ms exchange, take a look at horde if you are serious about groupware stuff on a linux platform

---

### Post by primski on 2007-12-06
ye, if you got a timemachine back in your garage and planing on going back to 1990's.

---

### Post by seepage87 on 2007-12-06
> **garba said:**
> just another piece of bloatware trying to mimick ms exchange, take a look at horde if you are serious about groupware stuff on a linux platform

I should note that I'm *not* serious about groupware stuff on linux.  I am interested in platforms that are a pleasure to use, and having tried the live demo for Zimbra, it certainly is that.  Bloatware isn't denotatively bad, the problems come up when developers are more concerned with adding features and eye-candy than a clean intuitive interface and ensuring everything they've added works without consuming too many resources.  

Just because something is feature rich and aesthetically pleasing doesn't mean it isn't good for some people.  I'm looking for an effective and beautiful web frontend that I can play with and show off to my friends when I'm not at one of my computers.  When I am I'll be using whatever client-side email is catching my fancy at the time.

---

### Post by garba on 2007-12-06
> **seepage87 said:**
> 

Just because something is feature rich and aesthetically pleasing doesn't mean it isn't good for some people.  I'm looking for an effective and beautiful web frontend that I can play with and show off to my friends when I'm not at one of my computers.  When I am I'll be using whatever client-side email is catching my fancy at the time.

well if you're looking for something beautiful zimbra sure is, at least on the outside:)

---

### Post by primski on 2007-12-07
Zimbra is indeed very nice and has lots of features, some of course are unnecessary but they are there if you need them, and you can always turn them off and reduce the bloatware .

Besides, its easy to maintain and upgrade and offers complete collaboration suite, thats why it gets my vote.

---

### Post by Bob_Mendon on 2007-12-08
The trick is getting Zimbra to install on 7.10 when it's really designed for non-debian platforms. Even their community feels that if the application won't install on your distro, then you should change your distro. Good thing Open Office, Gnome Firefox and etc doesn't have that kind of attitude. 

I have decided that there is currently no elegant mail server solutions compatible with Ubuntu 7.10 so I will keep my ClarkConnect server for the time being. I'm begining to think that part of the problem for Ubuntu users to get a better solution is that debian developers just don't want to put the time and energy into making one. I guess they just assume that email is not sexy and that if you want a mail server, you can do it the old fashioned way by spending hours at the command line tweaking sendmail, postfix, dovecot etc.

---

### Post by primski on 2007-12-09
Yea, thats true, its pain to get it working on Gutsy. Thats why i still use Dapper on my production servers. Will just wait until spring and hardy release and then upgrade OS. Hope zimbra will fully support Hardy Heron by then, it should since it will be LTS.

I think zimbra team's favourite OS is Red Hat or Centos though, so naturally it runs best there.

---

