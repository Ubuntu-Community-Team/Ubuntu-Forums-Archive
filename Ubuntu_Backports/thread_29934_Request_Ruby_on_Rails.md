---
title: "Request: Ruby on Rails"
date: 2005-04-26
forum: Ubuntu Backports
---

### Post by GentleHatemonger on 2005-04-26
In Debian Unstable, you can
```
apt-get install rails
``` 

whereas in Ubuntu, you have to follow [http://wiki.rubyonrails.com/rails/show/RailsOnUbuntuDebianTestingAndUnstable](http://wiki.rubyonrails.com/rails/show/RailsOnUbuntuDebianTestingAndUnstable)

it'd be really nice to be able to apt-get install rails

---

### Post by mlambie on 2005-06-16
I completely agree.

Is there any work to move these packages into the unofficial repositories?

---

### Post by jdong on 2005-06-16
I'll see what's possible.

---

### Post by marko on 2005-06-20
Any updates?  I also would like this very much.

---

### Post by DancingSun on 2005-07-05
I think it is be more worthwhile to put [RubyGems](http://rubyforge.org/projects/rubygems/) into the repository.

Once we have that, getting Ruby on Rails would be as easy as:
```
gem install rails
```

---

### Post by weeroona on 2005-07-10
[QUOTE=DancingSun]I think it is be more worthwhile to put [RubyGems](http://rubyforge.org/projects/rubygems/) into the repository.

Once we have that, getting Ruby on Rails would be as easy as:
```
gem install rails
```[/QUOTE]
 RubyGems or Rails would be quite nice!
:)

---

### Post by zeroK on 2005-07-12
Since rails now requires 1.8.2 backporting 1.8.2 would be nice too :-)

---

### Post by regeya on 2005-07-13
[QUOTE=zeroK]Since rails now requires 1.8.2 backporting 1.8.2 would be nice too :-)[/QUOTE]
Indeed.  There are minor incompatibilities between the Hoary 1.8.2 packages and 1.8.2 final.  Why did Hoary ship with a prerelease, anyway?   Final Ruby release date was *two days* after the RC packages in Hoary--and Hoary didn't come out until nearly FOUR MONTHS LATER.  Hm.

---

### Post by DancingSun on 2005-07-13
[QUOTE=regeya]Indeed.  There are minor incompatibilities between the Hoary 1.8.2 packages and 1.8.2 final.  Why did Hoary ship with a prerelease, anyway?   Final Ruby release date was *two days* after the RC packages in Hoary--and Hoary didn't come out until nearly FOUR MONTHS LATER.  Hm.[/QUOTE]

Yes, I believe this is the biggest problem with package repositories.  It's hard to keep in sync with the progress of other software releases.

---

### Post by stoffe on 2005-07-24
>     Rails requires Ruby version 1.8.2 (2004-12-25) or later.
    You're running 1.8.2 (2004-12-23); please upgrade to continue.
Hehe, typical - two days diff. :)

Anyhow, I second the above request to get a newer Ruby for this. For now, backing to Rails 0.13.0 is sufficient for it to work. Also, rubygems would indeed be nice.

---

### Post by GeneralZod on 2005-07-25
[QUOTE=stoffe]Hehe, typical - two days diff. :)

Anyhow, I second the above request to get a newer Ruby for this. For now, backing to Rails 0.13.0 is sufficient for it to work. Also, rubygems would indeed be nice.[/QUOTE]

I think a newer Ruby was all that was preventing me from installing [this](http://ubuntuforums.org/showthread.php?t=34208), too, so thirded!

---

### Post by anders5737 on 2005-07-26
I'd also like to see improved Ruby support which hopefully includes the fix of this bug [http://bugzilla.ubuntu.com/show_bug.cgi?id=12613](http://bugzilla.ubuntu.com/show_bug.cgi?id=12613) which I run into...  :neutral:

---

### Post by stoffe on 2005-07-28
Any news? Do we need to file a separate request for Ruby 1.8.2 maybe? I really, really need this. :)

Thanks!

---

### Post by mlambie on 2005-08-09
Any news? Ruby and RoR seems to be gaining some serious momentum. I'd like to jump on without moving to Breezy.

---

### Post by DancingSun on 2005-08-09
If you are an Ubuntu AMD64 user, check [this](http://ubuntuforums.org/showthread.php?t=48905&page=1) out for Ruby 1.8.2 and RubyGems.

---

### Post by lassel on 2005-08-10
I don't know if it makes a difference but I just have to so here goes nothing: 

ME TOO !!

:)

---

### Post by anders5737 on 2005-08-14
[QUOTE=DancingSun]If you are an Ubuntu AMD64 user, check [this](http://ubuntuforums.org/showthread.php?t=48905&page=1) out for Ruby 1.8.2 and RubyGems.[/QUOTE]

How ironic. I have a AMD 64 system but is actually running on i386 install just to reduce the everyday hacking/tweaking that has to be done. But, now, as indicated  on the link above, it seems that Ruby (on Rails) has better support on AMD64 than on i386... time to upgrade to AMD 64 perhaps! ;)

---

### Post by Wolki on 2005-08-14
On the Rails Wiki is a Howto for installing on Hoary.

[http://wiki.rubyonrails.com/rails/show/RailsOnUbuntuDebianTestingAndUnstable](http://wiki.rubyonrails.com/rails/show/RailsOnUbuntuDebianTestingAndUnstable)

I've successfully installed it following the instructions there. The problematic part is installing an up-to-date version of ruby, I used the alternate method (building from a progeny source deb) explained in the wiki with good results. When it tells you to install emacsen, it is not installable. Later on, when you "dpkg -i *.deb", it'll tell you exactly which package to install; if do that it works.

---

### Post by npaladin2000 on 2005-08-15
This is Ubuntu. We use Python here.  Fear the snake. :)

---

### Post by DancingSun on 2005-08-15
[QUOTE=anders5737]How ironic. I have a AMD 64 system but is actually running on i386 install just to reduce the everyday hacking/tweaking that has to be done. But, now, as indicated  on the link above, it seems that Ruby (on Rails) has better support on AMD64 than on i386... time to upgrade to AMD 64 perhaps! ;)[/QUOTE]
Well, that repository is more of a community project.  So it's not official Ubunutu AMD64 support.  But we got some pretty knowledgable guys working on making the deb package, so if there's some software that can be legally freely distributed that you really want to use on Ubuntu64, you're welcomed to make a request in the thread.

Actually, it was I that requested the Ruby and RubyGems packages.  Got kind of tired waiting for the backports team to respond and, plus, I found out that the backports team were not porting anything to Ubuntu64 at that time, so I made my request to Tamir (the guy  that started that Ubuntu AMD64 repository).  Even though the backports team have started to port software for AMD64, Tamir's AMD64 repository can still serve as a bleeding-edge repository, as the backports only port packages that are already in the developement version of Ubuntu.

---

### Post by bleers on 2005-08-28
Hi,
I'm a real Linux (K)Ubuntu newbie.
I would like to install Ruby, RubyGems, Rails (via Gems), irb.. on i386.
Please could somebody answer my questions?

1) Whick distro is most suitable to install and work with RoR, Ubuntu or Kubuntu? 
Or should I switch to other Linux distro's?

2) Should I install it from source or just via Synaptics.. or apt-get?
And in which directory?
I would like to install it in /usr/local/bin

Thank you.

---

### Post by DancingSun on 2005-08-28
[QUOTE=bleers]Hi,
I'm a real Linux (K)Ubuntu newbie.
I would like to install Ruby, RubyGems, Rails (via Gems), irb.. on i386.
Please could somebody answer my questions?

1) Whick distro is most suitable to install and work with RoR, Ubuntu or Kubuntu? 
Or should I switch to other Linux distro's?

2) Should I install it from source or just via Synaptics.. or apt-get?
And in which directory?
I would like to install it in /usr/local/bin

Thank you.[/QUOTE]
[list=1]
[*]Any LInux distro should be suitable for RoR.  There shouldn't be any differences.
[*]The easiest way to install on Ubuntu is from Synaptic.  However, you may need to install RubyGems manually (I'm on Ubuntu64 so I'm not sure if RubyGems in the repositories for i386).  Consult the [RubyGems manual](http://docs.rubygems.org/) on how to install manually.
[/list]

---

### Post by bleers on 2005-08-29
DancingSun, thnx for your reply.
Ok that's clear.
Do you know in which directory it's recommended to install:
- Ruby: /usr/local/bin ?
- Gems: /usr/local/bin ?
- Rails: /usr/local/bin ? OR /home/<user>

cya

---

### Post by DancingSun on 2005-08-29
[QUOTE=bleers]DancingSun, thnx for your reply.
Ok that's clear.
Do you know in which directory it's recommended to install:
- Ruby: /usr/local/bin ?
- Gems: /usr/local/bin ?
- Rails: /usr/local/bin ? OR /home/<user>

cya[/QUOTE]
If you use Synaptic or Apt, it will take care of all the install procedures by itself.  When installing RubyGems manually, it will also take take care of all the install location via a script.  When installing Ruby on Rails, It will install at the default gems location.

In short, you don't need to know where it's installed :)

---

### Post by bleers on 2005-08-29
[QUOTE=DancingSun]If you use Synaptic or Apt, it will take care of all the install procedures by itself.  When installing RubyGems manually, it will also take take care of all the install location via a script.  When installing Ruby on Rails, It will install at the default gems location.

In short, you don't need to know where it's installed :)[/QUOTE]

But before installing RubyGems one need to install Ruby first.
1. Is it possible to install Ruby in /usr/local/bin via Synaptics?
2. Which of the directories is recommended to install RubyGems and then via Gems -> Rails?
**/home/...** OR **/usr/(local/)bin** ?

---

### Post by DancingSun on 2005-08-29
[QUOTE=bleers]But before installing RubyGems one need to install Ruby first.
1. Is it possible to install Ruby in /usr/local/bin via Synaptics?
2. Which of the directories is recommended to install RubyGems and then via Gems -> Rails?
**/home/...** OR **/usr/(local/)bin** ?[/QUOTE]
[list=1]
[*]I don't know, Ubuntu and Debian has their own set of rules for where the files go, and I would say those are the "recommended" installation locations.  In either case, install Ruby via Synaptic, and you will be able to view where the files are installed by clicking on the "properties" button with the Ruby package selected.  If you don't like it, uninstall it, and install it manually, which is beyond me.
[*]I would recommend you to just run the install script for installing RubyGems.  If you customize the install locations you might run into other problems that were dependent on these default locations.  All gems installed via RubyGems are controlled by RubyGems and are centrally installed in a "gems" directory.  So you don't really have a say on where the gems are installed.
[/list]

I almost forgot something.  Ruby on Rails has many dependencies on the Ruby standard library, and unfortunately, the Ruby package in Ubuntu repositories don't have the standard library included (you have to install each library separately).  So take a look at this [wiki page](http://wiki.rubyonrails.com/rails/show/RailsOnUbuntuDebianTestingAndUnstable) and install all the libraries before using RubyGems to install Rails.

---

### Post by DancingSun on 2005-08-29
I just saw that Ruby on Rails is available on the the Ubuntu Backports.  So you could install it via Synaptic as well.  But I would recommend installing it via RubyGems, as RubyGems has support for installing and managing multiple version of the same gem.  Plus it makes installing all the other Ruby software easy and you won't have to wait for the backports to provide the package.

---

### Post by bleers on 2005-09-09
Yo DancingSun.. thanks for your really good advice.
i'm sorry for my awaiting reply.

how am i able to check the proper path for ruby?
as this 
[wiki](http://wiki.rubyonrails.com/rails/show/GettingStartedWithRails) shows. Howto to check before she-bang..? Or is it all arranged with the install again?

---

### Post by stoffe on 2005-09-09
[QUOTE=bleers]Yo DancingSun.. thanks for your really good advice.
i'm sorry for my awaiting reply.

how am i able to check the proper path for ruby?
as this 
[wiki](http://wiki.rubyonrails.com/rails/show/GettingStartedWithRails) shows. Howto to check before she-bang..? Or is it all arranged with the install again?[/QUOTE]
 Type in a terminal:
**which ruby**
And it should show you the path.

---

### Post by joepetrini on 2005-10-21
I recently got rails running on apache2 w/ fastcgi on breezy.  Instructions on how to do it from start to finish:
[http://fo64.com/articles/2005/10/20/rails-on-breezy]("http://fo64.com/articles/2005/10/20/rails-on-breezy")

---

### Post by stoffe on 2005-10-21
Nice. :) Maybe some of that belongs on the RoR wiki too: [http://wiki.rubyonrails.com/rails/pages/RailsOnUbuntuDebianTestingAndUnstable](http://wiki.rubyonrails.com/rails/pages/RailsOnUbuntuDebianTestingAndUnstable)

---

### Post by viniosity on 2005-12-07
I followed [http://fo64.com/articles/2005/10/20/rails-on-breezy](http://fo64.com/articles/2005/10/20/rails-on-breezy) this walkthrough and it was amazingly helpful. I now have RoR running with Apache2.  I also need to have some PHP sites running on the same server.  Does anyone know how to modify this setup to make that happen?

I'm assuming something in apache2's sites-enabled sites-available would have to change to disable FastCGI for particular sites but I don't know how to do that..

Thanks in advance..

---

### Post by Tim___ on 2005-12-12
I find the simplest way to do any thing with ruby is to use gem for package management. 

I created a deb using checkinstall which you can find at [http://home.config.com/tim](http://home.config.com/tim)

Then just run "gem update" & "gem install rails"

You can create you're own *.deb using checkinstall by running 

"checkinstall ruby setup.rb" inside the rubygem directory. 

Have a nice day

---

### Post by samiam on 2005-12-18
I followed this: [http://fo64.com/articles/2005/10/20/rails-on-breezy](http://fo64.com/articles/2005/10/20/rails-on-breezy).  Step by step instructions.  Works!

---

