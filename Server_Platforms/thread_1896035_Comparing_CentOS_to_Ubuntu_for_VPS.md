---
title: "Comparing CentOS to Ubuntu for VPS"
date: 2011-12-16
forum: Server Platforms
---

### Post by Mohamed GadAllah on 2011-12-16
I am really in a need to know major differences in between for those who used both centos and ubuntu servers regarding VPS.
And which one is better regarding stability and security and memory usage?

---

### Post by Dangertux on 2011-12-16
A VPS to do what? It kind of depends.

Both can be secured equally well. Though for stability and performance I would say CentOS/RHEL is head and shoulders above Ubuntu Server, for some reason it's just very heavy. Though it's still a great OS.

---

### Post by Mohamed GadAllah on 2011-12-16
I've just ordered a new VPS hosting fully unmanaged and almost no support and I am on my own on the whole thing.
The VPS for hosting a website and I will use ISPConfig control panel.
That is all, so which one I should go through?
Ubuntu or CentOS
Hope that I express it clearly the right way.

---

### Post by Mohamed GadAllah on 2011-12-16
- later edit - 
I forget to mention that I am following tutorials from how-to-forge
And now I am following this one to setup the VPS
[http://www.howtoforge.com/perfect-server-centos-6.0-x86_64-ispconfig-3](http://www.howtoforge.com/perfect-server-centos-6.0-x86_64-ispconfig-3)

---

### Post by Dangertux on 2011-12-16
> **Mohamed GadAllah said:**
> I've just ordered a new VPS hosting fully unmanaged and almost no support and I am on my own on the whole thing.
The VPS for hosting a website and I will use ISPConfig control panel.
That is all, so which one I should go through?
Ubuntu or CentOS
Hope that I express it clearly the right way.

Well, I know VPS providers really limit resources (or bill you insanely if they don't). It depends on a few things since you're talking about a web site/application.

1 - How optimized is your code? You're going to kill resources with any OS if your DB is getting hit hard on every query.

2 - How much traffic are you getting? Though this is more in relation to bandwidth , in conjunction with #1 this can kill memory usage too.

So honestly, it's really a toss up. I'd go with centOS but you'd be fine with Ubuntu  as well.

---

### Post by Mohamed GadAllah on 2011-12-16
> **Dangertux said:**
> kill memory usage
This is the main key point I keep found on each goggling review ... But to put you in the big picture I'll use Drupal CMS (almost all core modules) and expecting to get 40k visits per day.

But honestly no support like ubuntu ... this is why I am in a big confusion

---

### Post by Dangertux on 2011-12-16
I mean if it's a serious workload, as much as I'd love to promote Ubuntu... I'd have to say choose CentOS. It's more stable, it's been proven longer and ...Well deep down inside it's red hat :-/

You may have to decide for yourself though. I'm just giving my suggestion on what I'd do.

---

### Post by Mohamed GadAllah on 2011-12-16
> **Dangertux said:**
> I mean if it's a serious workload, as much as I'd love to promote Ubuntu... I'd have to say choose CentOS. It's more stable, it's been proven longer and ...Well deep down inside it's red hat :-/

You may have to decide for yourself though. I'm just giving my suggestion on what I'd do.
Like 

Honestly the kind of honest and help I found in Ubuntu really makes me wish you all the best.

You deserve my respect and I hope if I can donate for ubuntu.

---

### Post by Dangertux on 2011-12-16
> **Mohamed GadAllah said:**
> Like 

Honestly the kind of honest and help I found in Ubuntu really makes me wish you all the best.

You deserve my respect and I hope if I can donate for ubuntu.

Well I hope it works out for you regardless of which you choose. Like I said those are my recommendations, and while I love Ubuntu and I think it would work, in terms of getting the BEST stability and performance, my vote still goes with Red Hat based systems. This is my opinion ; and your mileage may vary, like I said use what works for you. Either way you'll do fine I'm sure they are both great OS'es.

---

### Post by Mohamed GadAllah on 2011-12-16
> **Dangertux said:**
> Well I hope it works out for you regardless of which you choose. Like I said those are my recommendations, and while I love Ubuntu and I think it would work, in terms of getting the BEST stability and performance, my vote still goes with Red Hat based systems. This is my opinion ; and your mileage may vary, like I said use what works for you. Either way you'll do fine I'm sure they are both great OS'es.
I've made up my mind on centos 6 64bit.

---

### Post by Dangertux on 2011-12-16
Sounds good, I responded to your PM by the way.

---

### Post by Mohamed GadAllah on 2011-12-16
I am amazed by the fast of the replying guys.

---

### Post by HermanAB on 2011-12-16
Linux is Linux is Linux...

The difference between distros is just in the shiny desktop schtuff that doesn't matter to a server setup.

That being said, the CentOS/Red Hat server wizards are generally much better than the (mostly non-existent) Ubuntu ones.

---

### Post by DaveyG on 2011-12-16
[QUOTE=HermanAB]The difference between distros is just in the shiny desktop schtuff that doesn't matter to a server setup.[/QUOTE]

I totally disagree. Every Linux distribution is different, in many ways. Regardless of the interface

---

### Post by Mohamed GadAllah on 2011-12-16
For a new guy like me, what shall I pick? or choose?

---

### Post by DaveyG on 2011-12-16
> **Mohamed GadAllah said:**
> For a new guy like me, what shall I pick? or choose?

Depends on knowledge, intentions etc. Command line or desktop environment, package manager or compile and so on. Only advice I can give is to use what you think is best, use what suits you

---

### Post by Mohamed GadAllah on 2011-12-16
> **DaveyG said:**
> Depends on knowledge, intentions etc. Command line or desktop environment, package manager or compile and so on. Only advice I can give is to use what you think is best, use what suits you
I am totally newbie to linux and have no previous experience so i do not have any preferences to stick to so i am asking about the best and the right one to use and start with.
I am using putty to access my VPS and I read that command line always the better then gui.
So please advise.

---

### Post by DaveyG on 2011-12-16
Personally, I'd unanimously choose CentOS. Alternatively, Debian

---

### Post by Mohamed GadAllah on 2011-12-17
And if we are comparing CentOS vs Debian?

---

### Post by SeijiSensei on 2011-12-17
There really isn't a single right answer to this question.  I recently built a server and tried both Ubuntu 10.04 LTS and CentOS 6.  I stuck with the latter because it has better support for a key application I use (MailScanner).  I've used RedHat or CentOS almost exclusively on servers.  

Other differences include choice of package management system (rpm/yum vs deb/apt), differences in configuration files and where they are stored, and differences in things like the name of log files.  If you've never built a server before, of if you've not used Linux before, I'd recommend CentOS.  If you have experience with Ubuntu or Debian, I'd suggest Debian.

---

### Post by DaveyG on 2011-12-17
[QUOTE=SeijiSensei]There really isn't a single right answer to this question.[/QUOTE]

I was kind of trying to say that... But, I agree with your reply:

[QUOTE=SeijiSensei]if you've not used Linux before, I'd recommend CentOS. If you have experience with Ubuntu or Debian, I'd suggest Debian.[/QUOTE]

---

### Post by Mohamed GadAllah on 2011-12-17
Does CentOS has more support and more tutorials?

---

### Post by crashed111 on 2011-12-17
Normally when it comes to servers I normally use Ubuntu if the server has a relatively low workload as the stock packages in the repo are normally newer. However for a high workload and reliability I will always use a RHEL based system as I do find the Red Hat way a bit easier than the Debian way when it comes to management and also for reliability. 

Either will work fine just remember when it comes to remote server CLI all the way and no GUI :)

---

### Post by DaveyG on 2011-12-17
[QUOTE=crashed111]CLI all the way and no GUI :)[/QUOTE]

= Less resource usage. You noted some good points on your post. For more updated repo packages, Ubuntu. Imop best security: RH based. But newest isn't always best, and sometimes older isn't always best either

---

### Post by Habitual on 2011-12-17
> **Dangertux said:**
> ...Though for stability and performance I would say CentOS/RHEL is head and shoulders above Ubuntu Server,....

I agree.

---

### Post by Dry Lips on 2011-12-19
> **Dangertux said:**
> Though for stability and performance I would say CentOS/RHEL is head and shoulders above Ubuntu Server, for some reason it's just very heavy. Though it's still a great OS.

I find it amusing that everyone who has voiced their opinion essentially have 
agreed with this notion. I mean, this is an Ubuntu forum after all... I'm not saying
that you're all wrong, because I'm still fairly new to this server thing, and I've never
used CentOS.

But do you care to elaborate? What is this based on? Experience, benchmarks or just 
a gut feeling? Again, I'm not saying you're wrong, I'm just curious and would like
some more information... So you think Ubuntu is too heavy for a server distro?

(What about Debian then? Is there a significant difference between, say, Ubuntu Lucid
and Debian?)

----

Edit: I found a very interesting discussion about Ubuntu vs CentOS here:
[http://www.linkedin.com/groups/Ubuntu-Server-Edition-CentOS-65688.S.79737313](http://www.linkedin.com/groups/Ubuntu-Server-Edition-CentOS-65688.S.79737313)

---

### Post by Habitual on 2011-12-19
I admin, all day every day... 

My personal choice for a server of *mine* is CentOS hands down, but this also depends where it's being hosted.

I work for a [Managed Service Provider]("http://www.cirrhus9.com/") of the AppLogic Grid Computing Software, CentOS is the default OS on every application/appliance/server.

We also have half a dozen Client Instances up at AWS where Ubu is installed on every single Instance I help manage there. CentOS Images are available.

Admin'ing under either doesn't make any difference to me, under the hood, they're all pretty much the same.

CentOS is a rock-solid and dependable Server OS and my First Choice.

---

### Post by Mohamed GadAllah on 2012-01-07
The hosting provider told me that they are now using Debian for all servers and servers are using OpenVZ for vitalization.

So does it differ now or you still stick to the opinion?

And does using the same OS as the main server makes any differ or not?

They already did migrated my node few days ago now.

---

### Post by Habitual on 2012-01-07
> **Mohamed GadAllah said:**
> ....now using Debian for all servers and servers are using OpenVZ for vitalization....

Debian Proper is perfectly fine for such an environment.

Question: Ask if you can install Ubuntu, or clarify "now using Debian".

---

### Post by Mohamed GadAllah on 2012-01-07
> **Habitual said:**
> Debian is perfectly fine for such an environment.
Does Ubuntu tutorials or help stuffs can be used or applied to Debian?
Or it is not?

---

### Post by Habitual on 2012-01-07
> **Mohamed GadAllah said:**
> Does Ubuntu tutorials or help stuffs can be used or applied to Debian?
Or it is not?

Depends...
They are for the most part, the switchable parts of a bigger machine that is Linux.
Knowledge can come from any source. It may even be dated info, but remember that _the Technique_[s] should still be valid.

Knowing Debian assumes you could also know Ubuntu.
Knowing Ubuntu assumes you could also know Debian.

As I have said, under the hood, they are pretty much all the same.

[http://www.google.com/cse/home?cx=016212844476379046035:5cta2rjlwko&hl=en](http://www.google.com/cse/home?cx=016212844476379046035:5cta2rjlwko&hl=en)
is my "Linux Dork Sites 2" Google Custom Search portlet for 40'ish Linux-Specific sites.

Here's a winner too:
[http://www.server-world.info/en/](http://www.server-world.info/en/) has lots of screenshots as the tutorials.

If ya need more, lemme know.
Subscribed with interest....

---

### Post by Mohamed GadAllah on 2012-01-07
> **Habitual said:**
> Depends...
They are for the most part, the switchable parts of a bigger machine that is Linux.
Knowledge can come from any source. It may even be dated info, but remember that _the Technique_[s] should still be valid.

Knowing Debian assumes you could also know Ubuntu.
Knowing Ubuntu assumes you could also know Debian.

As I have said, under the hood, they are pretty much all the same.

[http://www.google.com/cse/home?cx=016212844476379046035:5cta2rjlwko&hl=en](http://www.google.com/cse/home?cx=016212844476379046035:5cta2rjlwko&hl=en)
is my "Linux Dork Sites 2" Google Custom Search portlet for 40'ish Linux-Specific sites.

Here's a winner too:
[http://www.server-world.info/en/](http://www.server-world.info/en/) has lots of screenshots as the tutorials.

If ya need more, lemme know.
Subscribed with interest....
Really much appreciated with your new inputs ... but you really make it more difficult for me as I do not know any one of them ... and all I am trying to do is just to know which one is better for the long run and stick with it and learn it and use it.
Really can not make up my mind for any yet :( 
lease advise for CentOS or Debian?

But why I keep read the exact same phrase that CentOS is the industry standard

Really a lot of confusion right here.

---

### Post by Habitual on 2012-01-07
> **Habitual said:**
> CentOS is a rock-solid and dependable Server OS and my First Choice.

Learn it. Live it. Love it.

---

### Post by Mohamed GadAllah on 2012-01-07
> **Habitual said:**
> Learn it. Live it. Love it.
It seems that there is no any other way around it.

Please I understand that google is the friend,, but not all the time.

Please may you give any guide of how to search for this in google

"setting up the vps server from scratch using centos 6"

as I can only find thehowtoforge and it is really a bit hard for me and many commands reporting not found.

Thanks a lot and too much appreciated.

---

### Post by Habitual on 2012-01-07
Well, I suggest WebMin. Check it out at webmin.com
It is a fairly good tool for new admins.

[http://www.how2centos.com/installing-webmin-on-centos-5-5-tutorial/](http://www.how2centos.com/installing-webmin-on-centos-5-5-tutorial/)

---

### Post by Mohamed GadAllah on 2012-01-07
> **Habitual said:**
> Well, I suggest WebMin. Check it out at webmin.com
It is a fairly good tool for new admins.

[http://www.how2centos.com/installing-webmin-on-centos-5-5-tutorial/](http://www.how2centos.com/installing-webmin-on-centos-5-5-tutorial/)
Yes I've tried the automatic installation with the following command:
```
**wget [http://software.virtualmin.com/gpl/scripts/install.sh](http://software.virtualmin.com/gpl/scripts/install.sh)**
                             **chmod u+x install.sh**
                             **./install.sh**
```
Then log in to the control panel [www.domain.com:10000](www.domain.com:10000)
Then really a very huge options for webmin, virtualmin, and usermin

---

### Post by SeijiSensei on 2012-01-09
> **Mohamed GadAllah said:**
> Yes I've tried the automatic installation with the following command

CentOS uses the "yum" package manager.  I strongly discourage installing packages any other way until you have a lot more experience under your belt.

To install webmin on CentOS 6, follow the directions [here](http://www.webmin.com/rpm.html) to add the Webmin repository.  Once everything is in place, you can run "yum install webmin" to download and install the package.  One important benefit of using repositories is that the package will be automatically updated as new releases come out.

Most mainstream packages like Apache, PostgreSQL or Postfix won't need to have a separate repository added.  Webmin is an exception in this regard as are a few other common packages like [VirtualBox]("http://www.virtualbox.org/").

---

