---
title: "[Howto] Setup and use Leafnode-2 with the newsreader slrn"
date: 2008-01-24
forum: Tutorials
---

### Post by andrew.46 on 2008-01-24
This guide has been transferred to the Ubuntu Community Wiki:

[https://help.ubuntu.com/community/Leafnode2](https://help.ubuntu.com/community/Leafnode2)

However support is still available in this thread, feel free to ask any questions :).

---

### Post by Mary.Riley on 2008-02-03
That's super useful. Thank you for the tutorial.

---

### Post by andrew.46 on 2008-02-03
Hi Mary:

> **Mary.Riley said:**
> That's super useful. Thank you for the tutorial.

It is my pleasure! I hope you enjoy this amazing sodtware. A fellow australian has produced a nice macro that places an 'X-NNTP-Proxy'' (leafnode 2' header in slrn which may interest you:

[http://piggo.com/~troy/slrn#custom](http://piggo.com/~troy/slrn#custom)

He does not give the *full* syntax on the page, which is:

```

define post_hook ()
{
  set_string_variable ( "custom_headers",
    sprintf ("Message-ID: <%s>\nX-NNTP-Proxy: Leafnode-2 (http://www-dt.e-technik.uni-dortmund.de/~ma/leafnode/beta/)", create_msg_id ()));
}

define followup_hook()
{
  set_string_variable ( "followup_custom_headers",
    sprintf ("Message-ID: <%s>\nX-NNTP-Proxy: Leafnode-2 (http://www-dt.e-technik.uni-dortmund.de/~ma/leafnode/beta/)", create_msg_id ()));
}

define reply_hook()
{
  set_string_variable ( "reply_custom_headers",
    sprintf ("Message-ID: <%s>\nX-NNTP-Proxy: Leafnode-2 (http://www-dt.e-technik.uni-dortmund.de/~ma/leafnode/beta/)", create_msg_id ()));
}



```

All the very best,

   Andrew

PS My apologies for giving mangled syntax in the initial post, I have corrected it.

---

### Post by andrew.46 on 2009-04-07
Hi,

I have updated the guide to the most stable, recent version of Leafnode-2 and I suspect I shall leave the guide to slumber quietly now. There has been little interest in the guide, which is a great pity as Leafnode-2 is a fantastic piece of software and once setup no trouble to administer.

I will be available for questions but in the meantime slumber on my least utilised guide :-).

All the best,

Andrew

---

### Post by alipensen on 2009-05-19
Thanks very much for the update on the guide.
[RIGHT][[COLOR=#ffffff]_wow gold_[/COLOR]]("http://www.wowgold.net/")[/RIGHT]
Just to let you know; it's still appreciated, even if not the most popular!

---

### Post by andrew.46 on 2009-05-19
Hi alipensen,

> **alipensen said:**
> Thanks very much for the update on the guide.
[RIGHT][_wow gold_]("http://www.wowgold.net/")[/RIGHT]
Just to let you know; it's still appreciated, even if not the most popular!

Thanks for your kind words, I do plan on at the very least testing the guide under Karmic Koala and ensuring that it works there. But thanks again or a little encouragement :-).

Andrew

---

### Post by kevinguillorytraining on 2009-10-09
Thanks for a nice how-to.

---

### Post by andrew.46 on 2009-10-09
Hi kevin,

> **kevinguillorytraining said:**
> Thanks for a nice how-to.

My pleasure! Good to see that this guide is still being used, as I promised above I intend polishing it a little with the release of Karmic Koala which is only a few weeks away now...

All the best,

Andrew

---

### Post by andrew.46 on 2009-10-27
Hmmm.... unfortunately this version of leafnode-2 does not compile under Karmic Koala. I shall investigate..... Looks like the latest version fails as well, I have [posted to leafnode-list]("http://www.dt.e-technik.uni-dortmund.de/pipermail/leafnode-list/2009q4/002180.html").

Andrew

---

### Post by orphean on 2009-11-23
I managed to get leafnode up and running easily enough with the leafnode in the official universe repository.  It seems to work fine so far, I was curious what benefit your procedure gives? :)

---

### Post by andrew.46 on 2009-11-23
Hi orphean,

> **orphean said:**
> I managed to get leafnode up and running easily enough with the leafnode in the official universe repository.  It seems to work fine so far, I was curious what benefit your procedure gives? :)

The repository leafnode is the stable version, sometimes known as leafnode 1, while this guide deals with the development version known as leafnode 2. To tell the truth if you are happy enough with the repository version I would advise you to stick with it. In particular 2009 has been a turbulent year for Leafnode 2 with some big changes (lua scripting) which still have not settled in vey well.

Andrew

---

### Post by orphean on 2009-11-23
Ahh. Sounds like something I should read up on since leafnode 1 is a seriously slick piece of software and it sounds like the new version is getting more bells and whistles.  Thank you for putting up this guide so I can play with the new version (probably in a vm if it is as turbulent as you say.)

And just to editorialize for a bit, any readers of this thread who are wondering if they should do this: yes, you should!  USENET is still a great resource where you can get connected with highly clued in people (as well as a... colorful cast of other folk at times).

If your ISP no longer provides USENET access you can get free, text-only (which is all you need really unless you are into copyright infringement or pornography), USENET access from sites like eternal-september.org so you really have nothing to lose to check it out.

Anyway, back to the thread proper.

---

### Post by andrew.46 on 2009-11-23
Hi orphean,

> **orphean said:**
> Thank you for putting up this guide so I can play with the new version (probably in a vm if it is as turbulent as you say.)

Don't forget there is a small compilation problem under Karmic that requires [a patch]("http://www.dt.e-technik.uni-dortmund.de/pipermail/leafnode-list/2009q4/002181.html") that will hopefully be rolled into the next release. BTW can I ask what newsreader you are using with leafnode?

Andrew

---

### Post by orphean on 2009-11-23
[quote=andrew.46]BTW can I ask what newsreader you are using with leafnode?[/quote]

Of course, I use gnus via emacs for the majority of my newsreading.  I have slrn setup on a server of mine for quick checks from ssh when I'm out and about.

Tried pan for a while and it is a nice program, but I'm just a weirdo who enjoys the gnus way more.

---

### Post by andrew.46 on 2009-11-24
Hi orphean,

> **orphean said:**
> Tried pan for a while and it is a nice program, but I'm just a weirdo who enjoys the gnus way more.

I will admit to having experimented or some time with gnus, I even printed off the slightly crazy manual and read it from cover to cover. I certainly got it all working but I eventually decided that I would never truly embrace lisp and emacs so I would never truly understand what I was doing with this incredibly flexible newsreader. And I guess at heart I am really am a diehard slrn user :).

BTW there will hopefully be some moves soon to fix up some of the confusion that has swirled around leafnode 2 for the better part of 2009:

[http://www.dt.e-technik.uni-dortmund.de/pipermail/leafnode-list/2009q4/002208.html](http://www.dt.e-technik.uni-dortmund.de/pipermail/leafnode-list/2009q4/002208.html)

and hopefully this will reward the faithful, such as myself, who have been patiently running the last 2008 version ever since it was released.

All the best,

Andrew

---

### Post by orphean on 2009-11-24
> **andrew.46 said:**
> I will admit to having experimented or some time with gnus

I'm a big fan of gnus but I'm the first to admit it is incredibly arcane and not for everyone.  Like so many others things when dealing with Emacs the trick is to learn the bare minimum to get it up and running and then figure out the customizations.  The manual suffers from the same problem as a lot of FOSS documentation in that it is a fantastic reference but a poor guide.

The only thing I didn't like about gnus was that since Emacs is single-threaded it could be dog slow (that's one of the primary reasons slrn was created actually!). Leafnode fixes that for me.

> **andrew.46 said:**
> BTW there will hopefully be some moves soon to fix up some of the confusion that has swirled around leafnode 2 for the better part of 2009

This is good news!  Is there a PPA for leafnode-2 currently?  If not, I'd be willing to set one up, or, help with the creation of a 'leafnode-2' team for ubuntu.  While I do FOSS work with Gnome I have never been more than a user of Ubuntu so I am not familiar with how things work for the project.

---

### Post by andrew.46 on 2009-11-25
Hi orphean,

> **orphean said:**
> The only thing I didn't like about gnus was that since Emacs is single-threaded it could be dog slow (that's one of the primary reasons slrn was created actually!).

I remember seeing some mention of that on the slrn website. In fact if you have a peek at the html source of the [slrn site]("http://slrn.sourceforge.net/") you might see:

```
<meta name="author" content="Andrew Strong">
```

This is me :). I gained that information from John E. Davis in a personal email and he was kind enough to allow me to rewrite the website when he took over development of slrn a while back.

> Is there a PPA for leafnode-2 currently?  If not, I'd be willing to set one up, or, help with the creation of a 'leafnode-2' team for ubuntu.

There is no PPA for leafnode 2 unfortunately, I suspect the easy access to leafnode 1 from the repository combined with the relative complexity of setting up leafnode 2 has dampened the enthusiasm of most.

All the best,

Andrew

---

### Post by EdKo66 on 2010-02-16
> --sysconfdir=/etc/leafnode \With this line I get an invalid variable name. I checked it several times but I believe I typed it correctly. 

Using Ubuntu 9.10. Do I have to switch to an older version to get it working, or will that not work either?

(edit: I see that i have other problems as well. Can't get root access, can't edit any files ;( Guess I need to reinstall everything)

---

### Post by andrew.46 on 2010-06-21
I have added in the patch required to build leafnode 2 under Lucid...

Andrew

---

### Post by kindahero on 2011-03-28
First of all thanks for your time write the tutorial.. 

I followed your tutorial carefully, seems my setup is working. I use gnus instead of elrn.

Two nitpicks right now is, there is no inetd.conf on default ubuntu installation. first one has to install inetutils-inetd package.

second, no syslog.conf, So look for rsyslog.conf and rsyslog.d/ forlder.


My question is, how to have full control on leafnode fetchings,
suppose, I want to have totally fetched group locally.
I dont want to news to be expired and deleted.( cheap memory after all). etc

This must be simple , I cant find anywhere.?

---

### Post by andrew.46 on 2011-04-03
> **kindahero said:**
> First of all thanks for your time write the tutorial.. 

I followed your tutorial carefully, seems my setup is working. I use gnus instead of slrn.

Great news :). I will admit that I had thought this guide had been dead and buried for some time so good to hear that it has still proven useful.

> Two nitpicks right now is, there is no inetd.conf on default ubuntu installation. first one has to install inetutils-inetd package.

second, no syslog.conf, So look for rsyslog.conf and rsyslog.d/ forlder.

Things have obviously changed a little since I last ran through this guide. I have to have a serious think about whether to update the guide or get the Forums moderators to mark it as officially outdated. I will admit to a few doubts as to how many Ubuntu users would find this guide useful.....


> My question is, how to have full control on leafnode fetchings,
suppose, I want to have totally fetched group locally.
I dont want to news to be expired and deleted.( cheap memory after all). etc

I believe the global setting you are after is:
```

expire = 24800
```

in /etc/leafnode/config and this will keep all messages in all groups for 68 years. Have a look at *groupexpire* as well to manipulate settings for individual groups. BTW I maintain the Leafnode 2 package for Slackbuilds.org, you might be interested in using another patch that I have added in for Slackware users:

[http://slackbuilds.org/slackbuilds/13.1/network/leafnode/applyfilter_plugleak.diff](http://slackbuilds.org/slackbuilds/13.1/network/leafnode/applyfilter_plugleak.diff)

It can be added in the same manner as the gcc patch I have used in the Ubuntu guide.

Andrew

---

### Post by orphean on 2011-04-29
Slrn has really good support for customizing the colors it uses.  I'm a Zenburn junkie and just wanted to share a reasonable approximation of Zenburn in slrn:
```
color unread_subject    "color188"              "color237"      "bold"
color article           "color188"      "color237"
color author            "color223"      "color237"
color boldtext          "color188"      "color237"      "bold"
color box               "color237"              "color234"
color cursor            "color109"      "color237"
color date              "color188"      "color237"
color description       "color188"      "color237"
color error             "color174"              "color237"      "blink"
color frame             "color144"      "color236"
color from_myself       "color133"      "color237"      "bold"
color group             "color188"      "color237"      "bold"
color grouplens_display "color188"      "color237"
color header_name       "color65"               "color237"      "bold"
color header_number     "color65"               "color237"
color headers           "color223"      "color237"
color neg_score         "color65"               "color237"
color pos_score         "color109"              "color237"
color high_score        "color174"              "color237"      "bold"
color italicstext       "color133"      "color237"      "bold"
color menu              "color108"      "color234"
color menu_press        "color188"      "color237"
color message           "color188"      "color237"
color normal            "color188"      "color237"
color pgpsignature      "color188"      "color237"
color quotes            "color109"              "color237"
color quotes1           "color174"      "color237"
color quotes2           "color181"              "color237"
color quotes3           "color223"              "color237"
color quotes4           "color187"              "color237"
color quotes5           "color116"              "color237"
color quotes6           "color217"              "color237"
color quotes7           "color133"              "color237"
color response_char     "color65"               "color237"      "bold"
color signature         "color174"              "color237"
color selection         "color144"      "color234"      "bold"
color status            "color108"      "color234"
color subject           "color188"      "color237"
color thread_number     "color188"      "color237"      "bold"
color tilde             "color65"               "color237"      "bold"
color tree              "color174"              "color237"      "bold"
color underlinetext     "color188"              "color237"      "underline"
color url               "color188"              "color237"      "bold"
color verbatim          "color65"               "color237"

```

And a quick picture of the results:
[IMG]http://i.imgur.com/bEafv.png[/IMG]

Not trying to hijack the thread but if you're setting up slrn anyway I thought this might be a good place to share this.

Edit: Changed picture to a less polemic usenet post, whoops.

---

### Post by andrew.46 on 2011-04-29
I have an advantage in that I created and maintain the slrn website so my own setup can be seen here:

Screenshots of slrn at work
[http://slrn.sourceforge.net/screenshots.html](http://slrn.sourceforge.net/screenshots.html)

but the whole Neo thing is no longer present on my setup :).

---

### Post by pajus on 2011-06-26
Hello,
I have little problem.
I would like to run netnews/usenet on my server.
I just need run nntp server, and use it like private newsgroup. To communicate with my colleagues.


I've installed leafnode2. It works properly (I can do telnet). 

But now I need to add some newsgroup, but I don't know why. I've found on the internet, that I have to create newsgroups in ```
/var/lib/news/leafnode/active
``` but this is not working. I only know newsgroups like a user, so I am not really sure how should I continue to set newsserver properly.
Actually I've found some "how to" in book, where are chapters about Cnews or Inn. I thought with leafnode it would be much easier

Could anybody help? Thank you

---

### Post by andrew.46 on 2011-06-27
It sounds like you are after 'local' groups. Have a look here for a quick explanation:

[http://www.andrews-corner.org/leafnode.html#local](http://www.andrews-corner.org/leafnode.html#local)

Hopefully this is what you mean?

---

### Post by pajus on 2011-06-27
Yep. I have found it yesterday, but thanks.

I have one more question. Is it somehow possible to delete articles and messages (I mean manually, for example if i write something by mistake)? or make backup of spool and use same newsgroup articles and messages on other server?

---

### Post by andrew.46 on 2011-06-28
> **pajus said:**
> Yep. I have found it yesterday, but thanks.

That is my page btw, I maintain the leafnode 2 slackbuild script for slackbuilds.org. It is my shame that the Ubuntu guide is in a little disrepair at the moment though :(.

> **pajus said:**
> I have one more question. Is it somehow possible to delete articles and messages (I mean manually, for example if i write something by mistake)? or make backup of spool and use same newsgroup articles and messages on other server?

Best way is to catch your message in *out.going* and edit or delete there, the little utility *newsq* will be useful there. As for backing up and transporting the news spool this is answered well in [2.11]("http://www.dt.e-technik.uni-dortmund.de/~ma/leafnode/beta/FAQ.html#x1-140002.11") of the leafnode FAQs and hopefully one of these techniques will work for you.

---

### Post by pajus on 2011-06-28
Thank you very much again!
The web page is very useful. I've found there almost everything that I needed. Under Ubuntu Leafnode2 is very similar.
Only to restart inet.d I used ```
$/etc/init.d/openbsd-inetd restart
``` and I didn't need some things to set, but that is because way I use newsgroup.

---

### Post by andrew.46 on 2011-07-16
OK I have reworked the guide somewhat to work with Natty Narwhal and also added in a few of the patches I have used in my other distro. I will rewrite some of the blurb tomorrow evening and then do a clean install on my 64 bit VM and hopefully this will future proof the guide a little.

I have absorbed a few suggestions from this thread, only oddity being that when I installed the openbsd-inetd super server I had a default inetd.conf which I know was not the case for one user. I shall have a close look tomorrow when I install on a clean system....

---

### Post by silveringking on 2011-08-28
Hey here is a problem:

> root@ns353440:~/leafnode_build/leafnode-2.0.0.alpha20081229a# --sysconfdir=/etc/leafnode \
> 
-bash: --sysconfdir=/etc/leafnode: No such file or directory
[email]root@ns353440:~/leafnode_build/leafnode-2.0.0.alpha[/email]20081229a# 

Btw since I installed all those packages this nasty > keeps appearing to me. What can I do about these two things?

Again it is 10.04...

---

### Post by andrew.46 on 2011-08-29
Hmmm..... I am a little suprised that this guide still has some following :). Might be worth starting from scratch as I have added in a new version which eliminates the need for any patching + a few more improvements. BTW best run as an ordinary user with the use of sudo... As to the phantom '<' mark I suspect you have simply missed the final line or character in a copy and paste.

---

### Post by silveringking on 2011-08-30
Dude it was me who told me to follow your guide a few weeks ago... I simply didn't have the time to do it until now... Sometimes life has complications you see... Not everything is computers. Don't you agree?

---

### Post by andrew.46 on 2011-08-30
> **silveringking said:**
> Not everything is computers. Don't you agree?

Completely :).

---

### Post by silveringking on 2011-08-30
Ok then play some WOW and work on that guide ;).

---

### Post by silveringking on 2011-09-17
Hi! I just wanted to know how things are! Thanks!

---

### Post by andrew.46 on 2011-09-18
> **silveringking said:**
> Hi! I just wanted to know how things are! Thanks!

Everything is well here :). You may have noticed that I have finished updating the guide with a new version of Leafnode 2 which has been running very well on my system. Hopefully this will also run nicely on your own system :).

---

### Post by andrew.46 on 2012-04-09
This guide has been transferred to the Ubuntu Community Wiki:

[https://help.ubuntu.com/community/Leafnode2](https://help.ubuntu.com/community/Leafnode2)

However support is still available in this thread, feel free to ask any questions :).

---

### Post by bodhi.zazen on 2012-04-09
> **andrew.46 said:**
> This guide has been transferred to the Ubuntu Community Wiki:

[https://help.ubuntu.com/community/Leafnode2](https://help.ubuntu.com/community/Leafnode2)

However support is still available in this thread, feel free to ask any questions :).

Great wiki page. I have given the link to your wiki to some people on IRC and it was well received.

---

### Post by andrew.46 on 2012-04-16
> **bodhi.zazen said:**
> Great wiki page. I have given the link to your wiki to some people on IRC and it was well received.

Thanks for the feedback :).

---

