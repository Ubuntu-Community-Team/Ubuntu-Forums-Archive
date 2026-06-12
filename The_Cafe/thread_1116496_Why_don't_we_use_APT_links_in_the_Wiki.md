---
title: "Why don't we use APT links in the Wiki ?"
date: 2009-04-05
forum: The Cafe
---

### Post by YannBuntu on 2009-04-05
Hi all,

if you don't know how convenient is an APT link, just click on this APT link (**_[apt://supertux]("apt://supertux")_**) with Firefox to see what happens: it proposes you to install the package "supertux" and installs it if you click on "Install". 
Image how powerful and convenient it is! you install a package in 1 click , without opening your Package Manager ! :guitar:

The French Team is using it in its wiki (Documentation) since Gutsy, and it's sooo convenient! :KS
In the French wiki pages, we can find for example:
"To install the game, just _[install the following package]("https://help.ubuntu.com/community/InstallingSoftware#Installing%20a%20Package")_: ** _ [supertux](apt://supertux)_**." 
So that the user has the choice to use his Package Manager OR to click directly on the APT link.


Now why don't we use it in the English wiki ???

Do you know whom from the Wiki Team I should propose this to? -> EDIT : ok I sent a message to the ubuntu-doc ML.


See also : **[http://brainstorm.ubuntu.com/idea/19004/](http://brainstorm.ubuntu.com/idea/19004/)**


EDIT: before the Documentation enables APTURL, we can try to use the [http://pkgb.net/](http://pkgb.net/) workaround (which is a little less convenient). I made a first example with VLC:
[https://help.ubuntu.com/community/MultimediaApplications#VLC](https://help.ubuntu.com/community/MultimediaApplications#VLC)
What do you think about it?

---

### Post by Newuser1111 on 2009-04-05
> **YannBuntu said:**
> Hi all,

if you don't know how convenient is an APT link, just click on this APT link (**_[apt://supertux]("apt://supertux")_**) to see what happens.
Yes, it is possible to install a package in 1 click , without opening your Package Manager ! :guitar:
My Comp says:
"Firefox doesn't know how to open this address, because the protocol (apt) isn't associated with any program."

---

### Post by majamba on 2009-04-05
"Firefox doesn't know how to open this address, because the protocol (apt) isn't associated with any program." 

mine is saying the same not working

i think you should apt to aptitude

apt is not protocal i can ftp,smb,afp,nfs and so many otthers.

---

### Post by 23meg on 2009-04-05
> **YannBuntu said:**
> Do you know whom from the Wiki Team I should propose this to?

You don't have to propose it to anyone; just use it where it's appropriate. It's not a server-side feature; you simply create regular links in the form "apt://foo".

Note, however, that [wiki.ubuntu.com]("https://wiki.ubuntu.com") is not intended for documentation or support.

----

Edit: I was wrong; apparently it does require server-side configuration. I was assuming it would work, since some other non-HTTP protocols (including irc://) work. I found a relevant bug report:

[https://bugs.launchpad.net/ubuntu-website/+bug/226054/](https://bugs.launchpad.net/ubuntu-website/+bug/226054/)

---

### Post by CraigPaleo on 2009-04-05
Good idea. They do make life easier. I wonder why they aren't working for some. Older version of Firefox maybe?

---

### Post by Newuser1111 on 2009-04-05
> **CraigPaleo said:**
> Good idea. They do make life easier. I wonder why they aren't working for some. Older version of Firefox maybe?Actually, it's because I'm still running Vista.
But I just downloaded Ubuntu 9.04 Beta! Which I will try tomorrow.

---

### Post by YannBuntu on 2009-04-05
> **23meg said:**
> you simply create regular links in the form "apt://foo".
I tried to add some in the Documentation but the APT://package link redirects automatically to something like 
[https://help.ubuntu.com/community/apt://package](https://help.ubuntu.com/community/apt://package) 
so that I think there is something to change in the Documentation behaviour toward APT links...

Sorry if I mix "wiki" and "Documentation", but we use the same word for both in France, as the Documentation is wiki-edited.

---

### Post by david_lynch on 2009-04-05
Works fine here - it asks if I want to install the package supertux. I click yes, and it installs. 

Of course, I'm running linux here - surely nobody would expect that to work on ms windoze?

---

### Post by binbash on 2009-04-05
Not everyone visits that pages use linux.

---

### Post by YannBuntu on 2009-04-05
sorry i forgot to mention that:
1) you need to be on Ubuntu 7.10 or later
2) you need the package "apturl" to be installed (it is generally installed by default)
3) you need a compatible web browser:

- it works by default with Firefox and Epiphany if they are normally installed from the repositories
- if you use a version of Firefox or Epiphany that you didn't install from the repositories, or if you use Swiftfox, Opera or Konqueror, you need to enable the apturl in your browser with a (quite simple) procedure that i can describe later ([in French here]("http://doc.ubuntu-fr.org/apturl")) in a Documentation page.

---

### Post by Polygon on 2009-04-05
> **YannBuntu said:**
> I tried to add some in the Documentation but the APT://package link redirects automatically to something like 
[https://help.ubuntu.com/community/apt://package](https://help.ubuntu.com/community/apt://package) 
so that I think there is something to change in the Documentation behaviour toward APT links...

Sorry if I mix "wiki" and "Documentation", but we use the same word for both in France, as the Documentation is wiki-edited.

you are doing it wrong, there is a wiki formatting code (don't ask me what it is, the documentation of the wiki software ubuntu uses is TERRIBLE) that makes it so you can specify links, as opposed to wiki links (links that get appended to help.ubuntu.com/community)

---

### Post by jpeddicord on 2009-04-05
disclaimer: yes, I am affiliated with the following site.

Until the wiki is fixed to allow apt: links, consider using pkgb.net. It works just like apt: links, but the URL is different: [http://pkgb.net/supertux](http://pkgb.net/supertux) is equivalent to apt:supertux. As long as the visitor is using Ubuntu, they will be directed right to the Install link using apturl.

---

### Post by YannBuntu on 2009-04-05
> **jacobmp92 said:**
> Until the wiki is fixed to allow apt: links, consider using pkgb.net. It works just like apt: links, but the URL is different: [http://pkgb.net/supertux](http://pkgb.net/supertux) is equivalent to apt:supertux. As long as the visitor is using Ubuntu, they will be directed right to the Install link using apturl.
Hi Jacob!
Thank you for this tip, I think this is a good compromise before the wiki is fixed to allow APT links.

I made an example with VLC:
[https://help.ubuntu.com/community/MultimediaApplications#VLC](https://help.ubuntu.com/community/MultimediaApplications#VLC)

What do you think about it ?

---

### Post by jpeddicord on 2009-04-05
> **YannBuntu said:**
> Hi Jacob!
Thank you for this tip, I think this is a good compromise before the wiki is fixed to allow APT links.

I made an example with VLC:
[https://help.ubuntu.com/community/MultimediaApplications#VLC](https://help.ubuntu.com/community/MultimediaApplications#VLC)

What do you think about it ?

Looks pretty good. Perhaps I should expand the documentation included on pkgb, it is a little sparse past the "click the green button to install."

---

### Post by YannBuntu on 2009-04-06
> **jacobmp92 said:**
> Looks pretty good. 
I'm happy to hear that. :p
Someone else's opinion?

By the way, I am very surprised I got no answer on the ubuntu-doc mailing list... EDIT: ok, i received answer.
what is the right way to discuss such a topic: on the ML or on this forum ? 
The French rule is to discuss wiki subjects only on the wiki ML, but as I got no answer on the ML, I will continue here (and send another mail on the ML):

If you agree, next steps will be :
**1) Add the "pkgb.net method" to this page:** [https://help.ubuntu.com/community/InstallingSoftware#Installing%20a%20Package](https://help.ubuntu.com/community/InstallingSoftware#Installing%20a%20Package)
**2) Simplify all pages in the Documentation, according to _[this example]("https://help.ubuntu.com/community/MultimediaApplications#VLC")_** (the VLC one).
At the same time, we need an admin of the Documentation wiki system to:
**3) Enable the apturl links in the Documentation**
When this is done, we can :
**4) Replace all "pkgb links" by "apt://" links.**

---

### Post by popey on 2009-04-06
[https://lists.ubuntu.com/archives/ubuntu-doc/2009-January/012318.html](https://lists.ubuntu.com/archives/ubuntu-doc/2009-January/012318.html)

"> It is. Maybe we should go through the wiki doing a global replace of 
> "apt-get install" with "click apt://" :)  (note for the humour 
> impaired, this is not a serious suggestion, but you get the idea). 

This is a discussion which should continue on the ubuntu-doc list, but 
for the record: apt urls don't currently work on the documentation 
wiki. The question of whether to use them has been discussed by the 
documentation team, and a request has been made to the sysadmins back 
in September last year (ticket 3005 for those interested) to enable 
apt urls on the server that runs the wiki. 

As for the non-wiki part of the help website, we're hoping to 
introduce apt-url links in those documents during this release cycle. "

---

### Post by YannBuntu on 2009-04-07
Thank you for your reply Popeydc. i continued the discussion on the ML.

The question (that i asked on the ML) is now: is it ok to massively use _**[this kind of syntax]("https://help.ubuntu.com/community/MultimediaApplications#VLC")**_ in the Documentation ?

EDIT: I made another example: [https://help.ubuntu.com/community/Thunderbird#Installation](https://help.ubuntu.com/community/Thunderbird#Installation)

---

### Post by jpeddicord on 2009-04-07
I haven't used Moin in a while, but I do know that you can use templates. Just brainstorming, but would it be more useful to do something like this?

```
=== VLC ===
VLC (formerly the VideoLAN Client) is a kind of Swiss Army knife of media players. It plays any file you can throw at it, audio or video; plays DVD’s and CD’s; boasts a variety of skins; and much more.

<<Include(InstallPackage(vlc))>>
```

(Guessing the syntax for the InstallPackage bit, I'm not sure if templates can accept arguments.) This way when apt: links are available, it only has to be switched in one template instead on a bunch of pages.

---

### Post by YannBuntu on 2009-04-07
Jacob, i tried your syntax in the Documentation but it didn't work...

FYI: according to the ML, the Documentation sysadmin will soon enable APT links.(request was done 7 months ago...)

---

### Post by Mazza558 on 2009-04-07
> **binbash said:**
> Not everyone visits that pages use linux.

But you'd think that if they're trying to find out how to install an app on Ubuntu, they'd actually be on Ubuntu itself?

---

### Post by jpeddicord on 2009-04-07
> **YannBuntu said:**
> Jacob, i tried your syntax in the Documentation but it didn't work...

FYI: according to the ML, the Documentation sysadmin will soon enable APT links.(request was done 7 months ago...)

It's just a thought [for now]. The template doesn't exist, and I don't think that is the right syntax for sending arguments to templates (if they can take them at all, I'm stabbing in the dark.)

---

### Post by YannBuntu on 2009-04-07
[https://help.ubuntu.com/community/Games](https://help.ubuntu.com/community/Games) done, i will then do sub-pages.

---

### Post by ddrichardson on 2009-04-07
> **YannBuntu said:**
> Jacob, i tried your syntax in the Documentation but it didn't work...

FYI: according to the ML, the Documentation sysadmin will soon enable APT links.(request was done 7 months ago...)
The sysadmin for the site is nothing to do with the Documentation Team. All teams need to request other teams to do things from time to time.

---

### Post by YannBuntu on 2009-04-09
APT links have been enabled!

The Documentation will soon become much more convenient  :KS :KS :KS

---

