---
title: "Is there currently any way to permanently upgrade to ubuntu next?"
date: 2014-04-17
forum: Ubuntu Development Version
---

### Post by Kiori on 2014-04-17
as in, to make ubuntu effectively a rolling release? i remember talks about it a while back, about creating a symlink or whatnot. so did it happen?
Shouldn't information like this be pinned?

---

### Post by craig10x on 2014-04-17
I had e-mailed Colin Watson some months ago as he was the developer working on it....he told me he still had some bugs to work out on it and could only do that in his spare time....since then, it would seem really nothing has happened with it...

---

### Post by Kiori on 2014-04-17
Thx Craig, that sucks though... :/
If i want to easily upgrade to the lastes greatest has any one used the command "[COLOR=#333333][FONT=monospace]do-release-upgrade -d"?
i didnt want to have to edit apt files all the time.[/FONT][/COLOR]

---

### Post by grahammechanical on 2014-04-17
About a month ago I converted a Trusty install to update not from the trusty repositories but from the devel repositories. I get an error message when I update because not all the devel repositories are enabled but trusty has continued to be updated into 14.04. I now wait over the next few days/weeks to see if the devel repositories continue to be updated with code for the 14.10 development branch. If so then the development branch based upon devel repositories is our "rolling release" Ubuntu.

We are  still waiting to hear from Mark Shuttleworth what the 14.10 code name will be. He is very late in giving us that information. Without that code name the new development branch repositories cannot be set up. Unless the devel repositories are now the development branch repositories. I ran this code

```
sudo sed -i 's/trusty/devel/g' /etc/apt/sources.list
```

And got these repositories in the Other software tab

Ubuntu development series - Officially supported non-free drivers
Recommended updates
Ubuntu development series - Community maintained
Ubuntu development series - Restricted software
Unsupported updates
Important security updates
Canonical partners - Software packaged by Canonical for their partners [not enabled by default]
Independent - Provided by third party software developers
Pre-release updates

From this link devel is listed as a Ubuntu distribution

[http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)

I wait and see. Regards.

---

### Post by craig10x on 2014-04-17
Perhaps that is it, then... will be interesting to see what happens for you in the next few weeks...though a bit puzzling why Colin hasn't announced anything about the symlink since i wrote to him....also, Mark Shuttleworth again talked about just having LTS and converting the 6 month version to a sort of rolling release that would get new stuff much in the same way as say, your android phone gets updated to new stuff...This is supposed to take place at "Convergence" which they expected with during the 14.10 or 15.04 periods...

---

### Post by Kiori on 2014-04-23
Thanks guys, i was actually refering to Devel, i remember someone talking about it a while back, i just didnt recall the proper name. Lets hope it works, and test it.

edit: tried devel today, it linked to some trusty and some utopic, its weird. i guess its not there yet, lets wait til may and see.

---

### Post by vagrale on 2014-04-23
Try this
```
sudo sed -i 's/trusty/utopic/g' /etc/apt/sources.list
```
```
sudo apt-get update && sudo apt-get dist-upgrade
```

[[IMG]http://i.imgur.com/cOPxbSzs.png[/IMG]]("http://i.imgur.com/cOPxbSz.png")

:)

---

### Post by Kiori on 2014-04-24
> **vagrale said:**
> Try this
```
sudo sed -i 's/trusty/utopic/g' /etc/apt/sources.list
```
```
sudo apt-get update && sudo apt-get dist-upgrade
```

[[IMG]http://i.imgur.com/cOPxbSzs.png[/IMG]]("http://i.imgur.com/cOPxbSz.png")

:)


Thanks, but we were talking about a permanent solution, so we dont have to do that every update. ;)

---

### Post by vagrale on 2014-04-24
Maybe you can do that with a script, to change automatically the repositories when a newer version is available.

---

### Post by QDR06VV9 on 2014-04-24
Here is what I got after 
```
sudo sed -i 's/trusty/utopic/g' /etc/apt/sources.list
```
And
```
sudo apt-get update && sudo apt-get dist-upgrade
```

```
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libruby2.1 ruby2.1 rubygems-integration
The following packages will be upgraded:
  base-files lintian ruby
3 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,754 kB of archives.
After this operation, 14.8 MB of additional disk space will be used.
```

Not much as expected
```
Distributor ID:    Ubuntu
Description:    Ubuntu Utopic Unicorn (development branch)
Release:    14.10
Codename:    utopic
```

---

### Post by grahammechanical on 2014-04-24
For about a month I have been running Trusty off devel repositories just waiting for the changeover. The installation successfully moved from trusty development branch to 14.04 LTS but as yet it has not become utopic unicorn development branch. The devel repositories  could be a little behind the utopic repositories, At least in my neck of the woods. I haven't seen that many unicorns around here lately, either.

---

### Post by ventrical on 2014-04-24
> **grahammechanical said:**
> For about a month I have been running Trusty off devel repositories just waiting for the changeover. The installation successfully moved from trusty development branch to 14.04 LTS but as yet it has not become utopic unicorn development branch. The devel repositories  could be a little behind the utopic repositories, At least in my neck of the woods. I haven't seen that many unicorns around here lately, either.

I had the same issue. So I changed /devel/ to /utopic/. I am not sure if arbitrary names are still allowed. Before last cycle I could put in any name in sources.list and still get the updates.

btw .. since Mark S. is encouraging us to  :

> 
 So bring your upstanding best to the table &#8211; or the forum &#8211; or the  mailing list &#8211; and let&#8217;s make something amazing. Something unified and  upright, something about which we can be universally proud.

 I would hope you can help out with some new experiments I have in mind ... Muuhahahahahaha..:)lol

Regards..

---

### Post by grahammechanical on 2014-04-25
I now have the definitive answer. If we are running the development version on the devel repositories then the installation will roll first on the released version on released day and then onto the next development version a few days after release day.

So, with trusty tahr on the devel repositories lsb_release -a gave me 

"Ubuntu Trusty Tahr (development branch)" two weeks before release day and

"ubuntu 14.04 LTS" on release day and now (8 days after release day) I get

> graham@Sdb8-Roll-Dev:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Utopic Unicorn (development branch)
Release:    14.10
Codename:    utopic

And all from updating daily. So, install a daily image of utopic and change the repositories to devel by

```
sudo sed -i 's/utopic/devel/g' /ect/apt/sources.list
```

Then update/upgrade and may be even dist-upgrade and by daily updating that install will roll over to 15.04 development branch come this November. This code will change 14.04 to 14.10 development branch on the devel repositories

```
sudo sed-i 's/trusty/devel/g' /ect/apt/sources.list
```

My login screen says Ubuntu 14.10. There is a long way to go but things are starting.

Regards.

---

### Post by ventrical on 2014-04-25
I have a couple of spare installs of trusty  with /devel/ . I'll check into that.

Thanks.

---

### Post by craig10x on 2014-04-25
If that works maybe you should tell Colin Watson (the ubuntu developer) about it...he is the one that was working on the symlink for it ;)
Maybe you can tell him what you did and he could verify it...perhaps even use it...unless that was the way he intended it to work in the first place...
Let me know if you need his e-mail...i think i still have it and could pm it to you...then after you get the story you could let the folks know here..

---

### Post by Kiori on 2014-04-25
It would be great if devel worked, i mean how hard can it be to make a proper link to the latest version?

---

### Post by zika on 2014-04-26
> **ventrical said:**
> I have a couple of spare installs of trusty  with /devel/ . I'll check into that.
> **ventrical said:**
> I am not sure if arbitrary names are still allowed. Before last cycle I could put in any name in sources.list and still get the updates. Muuhahahahahaha..:)lol
Same unique installs that did not bother which branch they use?
To qoute You:
> **ventrical said:**
> Muuhahahahahaha..:)lol

---

### Post by seeker5528 on 2014-04-27
Looks like devel is working now, after a week or two of continuing to point to trusty, started getting the utopic updates a couple days ago.

---

### Post by happywise on 2014-05-03
Nice info, thanks guys :)

---

### Post by Alan F on 2014-05-05
> **Kiori said:**
> It would be great if devel worked, i mean how hard can it be to make a proper link to the latest version?

The 'devel' repositories are merely a copy of the latest development branch, complete with that branches name in the files. Hence the string of error messages each time one reloads the repository data.

It has been like this for over 6 months. It seems, to me as with Kiori, perhaps naively, that very little work would be required to make the 'devel' repository work as a 'rolling release' and maintain it.

In the absense of this work, what is the purpose of 'devel'?

---

### Post by grahammechanical on 2014-05-05
As I said in an earlier post, I had an install of Trusty development branch running on the devel repositories and it rolled into Ubuntu 14.04 LTS on release day and then 8 days later it rolled into Utopic Unicorn 13.10 development branch.

As far as I am concerned this is as near as we get to having a Ubuntu rolling release. I read or may be I heard (cannot say for certain) of some developers having Ubuntu phones/tablets on the devel repositories. And then there is this

> [COLOR=#333333][FONT=Ubuntu]When you install, you need to name the Ubuntu device image channel used to obtain the image.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]In most cases, you can simply use the **devel** channel, which gets the latest released image on the version of Ubuntu that is currently under development.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]You may want an image based on the most recent released Ubuntu. That&#8217;s what the **stable** channel gets you: the most recent released Ubuntu for devices image that is based on the most recent Ubuntu release.[/FONT][/COLOR]


From here

[http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/](http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/)

And this

[COLOR=#333333][FONT=Ubuntu]> One often uses convenient aliases starting with **devel** and **stable** instead of explicitly stating the Ubuntu release code name:[/FONT][/COLOR]> 

[LIST]
[*]devel: Refers to the current development Ubuntu release. For example, if trusty is under development (and not yet released), devel indicates trusty.
[*]stable: Refers to the most recent Ubuntu release. For example, if trusty is under development (and not yet released), stable indicates saucy.
[/LIST]
[COLOR=#333333][FONT=Ubuntu]> One often uses convenient aliases starting with **devel** and **stable** instead of explicitly Each alias can be used for all channel variants for that release. For example, one may use the following aliases:[/FONT][/COLOR]

[LIST]
[*]devel
[*]devel-proposed
[*]devel-customized
[*]devel-customized-proposed
[*]stable
[*]stable-proposed
[*]stable-customized
[*]stable-customized-proposed
[/LIST]


From here

[http://developer.ubuntu.com/start/ubuntu-for-devices/image-channels/](http://developer.ubuntu.com/start/ubuntu-for-devices/image-channels/)

I only know that right now I am running Utopic Unicorn (development branch) with devel repositories that started out as Trusty Tahr (development branch) on devel repositories. The really interesting time will come when image updates are tested on the desktop.

Regards.

---

### Post by Alan F on 2014-05-05
All of the above makes sense except for the shower of error messages when reloading/updating the repositories ( expecting 'devel' got 'utopic' ) This does not reflect well on the overall polish of the system.

Looking at the gb.archive ([http://gb.archive.ubuntu.com/ubuntu/dists/](http://gb.archive.ubuntu.com/ubuntu/dists/)) the active directories for Utopic are "utopic/proposed" and "utopic". These were the first to be created/updated after trusty was 'stable'. At this time the 'devel' directories did not change, but followed 'trusty'.

On 23 April the 'devel' directory contents were changed to be identical to 'utopic'. From that time you were running 'utopic' with the error message "expecting 'devel' got 'utopic'"

PPAs are operating in the same way. 

So if this is what Canonical means by a "Rolling Release" I agree that it does actually achieve that objective but are they not concerned about the error messages?

This use of the 'devel' directories will only make sense when the contents move away from that in Utopic.

---

### Post by grahammechanical on 2014-05-05
You are missing the point. The suggestion that Ubuntu become a rolling release was rejected. It is very unlikely that there will every be a rolling release of Ubuntu in the way that you think there should be. It has been stated by the person at the very top that if a user wants stability they should install an LTS version. If a user wants the bleeding edge they should install the development branch. Those who install the development branch ought not to expect "polish." 

Up until the middle of April the devel repositories were delivering updates from the trusty repositories. Then at the end of April as the new utopic repositories started to get upgraded packages then the devel repositories started delivering those same packages. The devel repositories will move away from the utopic repositories when the 15.04 codename repositories get set up and start receive updates.

Those of us running the development branch on the utopic repositories also get error messages because some of the utopic repositories do not yet exist and will not exist until after release day, such as backports repository. This is life on the bleeding edge. And sometimes we bleed.

Regards.

---

### Post by craig10x on 2014-05-05
More recently, Mark Shuttleworth did comment and mention that when convergence takes place between ubuntu desktop/phones/tablets/tv etc (which they think may happen by 14.10 or 15.04 release) that he thought it would be a good idea to have just 2 versions on Ubuntu..the LTS as it is now and instead of new 6 month versions that would become a stable core version which would get new "stuff" when it is stable and ready in the same was as say, your android gets new apps automatically installed to update them... (this would be different then development which as grahammechanical mentioned, is "bleeding edge")...

However, whether this actually happens, remains to be seen...if it does, i get the impression it would be a stable core with a kind of semi-rolling nature but new apps and major changes would only be added in when they are "ready for prime time" ;)

As grahammechanical pointed out, development is NOT considered to be ubuntu's rolling release...the only thing that might happen that would be in anyway remotely like that would be what i just described to you...

---

### Post by Kiori on 2014-05-06
If devel is working afterall, then it does make sence for the time being to keep it that way.(simply as a link to the latest) Having each release with its own name-format organizes things, specially in launchpad, so we know bugs and stuff came from that release cycle, etc.
That is... until we go full rolling relese. :D

---

### Post by buzzingrobot on 2014-05-07
Isn't using the devel repos something entirely different than using a rolling release?

My understanding of a rolling release is that new packages considered stable enough for release are, in fact, pushed out individually as they become available, rather than being held for accumulative release in a periodic new distribution release.

On the other hand, packages in development are just that: In development aka unstable.

if I used a rolling release, I expect things to keep working after updates.  If I'm tracking the Utopic dev branch, I'd anticipate breakage along the way.

---

### Post by craig10x on 2014-05-07
@buzzingrobot: exactly...and what Mark Shuttleworth is now talking about is making the 6 month version into a kind of rolling release...there would be no more new 6 month versions, that would be replaced by a stable core version which would get new apps and changes when they are STABLE and READY not like in the development version..this would happen around the time of convergence...makes a lot sense...they wouldn't have to keep doing new 6 month versions anymore and inventing new names for them...:)

Let's hope the developers are willing to go along with the idea...;)

---

### Post by craig10x on 2014-05-29
A bit off topic but just curious...what is the current kernel being run on Ubuntu 14.10?  (I mean the one that the software center installed not the ones some of you guys jump ahead to for testing out)....
Thanks :D

Also, has 14.10 changed much yet....or is it still basically 14.04 at this point in time...Not jumping back to development myself...but my curiousity got the better of me...LOL

---

### Post by Elfy on 2014-05-29
Linux hob-unicorn 3.15.0-3-generic #7-Ubuntu SMP Mon May 26 07:50:34 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by philinux on 2014-05-29
> **craig10x said:**
> A bit off topic but just curious...what is the current kernel being run on Ubuntu 14.10?  (I mean the one that the software center installed not the ones some of you guys jump ahead to for testing out)....
Thanks :D

Also, has 14.10 changed much yet....or is it still basically 14.04 at this point in time...Not jumping back to development myself...but my curiousity got the better of me...LOL

Just bit the bullet and upgrade to utopic on one of my 14.04 installs.

839 packages upgraded.

For utopic packages see here. [http://packages.ubuntu.com/utopic/kernel/](http://packages.ubuntu.com/utopic/kernel/)

---

### Post by slickymaster on 2014-05-29
> **craig10x said:**
> A bit off topic but just curious...what is the current kernel being run on Ubuntu 14.10?  (I mean the one that the software center installed not the ones some of you guys jump ahead to for testing out)....
Thanks :D

Also, has 14.10 changed much yet....or is it still basically 14.04 at this point in time...Not jumping back to development myself...but my curiousity got the better of me...LOL

Well, today there was a major change, Ubuntu's "old" upstart/sysvinit policy was changed to what Debian currently uses.

You can see the full details [here]("https://lists.ubuntu.com/archives/ubuntu-devel/2014-May/038333.html").

---

### Post by craig10x on 2014-05-30
Thanks guys...appreciate it! :D 
 @philinux: well... sure sounds like a FEW things were changed ;)

---

### Post by craig10x on 2014-06-02
Is Ubuntu 14.10 supposed to get mir and unity 8?
Just wondering...thought i read somewhere that it's official that would happen...unless they changed their mind ;)

Also...how has 14.10 been running...has it been stable and reliable?

---

### Post by Mateusz Stachowski on 2014-06-03
> **craig10x said:**
> Is Ubuntu 14.10 supposed to get mir and unity 8?
Just wondering...thought i read somewhere that it's official that would happen...unless they changed their mind ;)

Also...how has 14.10 been running...has it been stable and reliable?

They have plans to make a new [Unity 8 flavour]("https://lists.ubuntu.com/archives/ubuntu-desktop/2014-May/004494.html") mainly for developers.

> Iain Lane

Hi,


The desktop team would like to add a new flavour (ish, we don't plan to
have any formal releases at this point) of Ubuntu which contains the
Unity 8 desktop and the new applications which have been developed for
the touch project.


The initial intention is to provide a product which developers can use
to figure out the work that's required to make a desktop product based
on this software usable, and to create a space for experimentation to
figure out the best ways of carrying out the required integration. We
still plan to migrate pieces of the current desktop over, but we are
very mindful of the need to not destabilise the desktop and upset its
users, and are hopeful that developing this flavour in parallel will
mean that migrations will truly happen when software is ready instead of
as a result of pressure to get work into the hands of users early.

---

### Post by grahammechanical on 2014-06-03
The QA tracker has placeholders for Ubuntu Desktop (Unity 8) amd64 and Ubuntu Desktop (Unity 8) i386. The links to the download information do not, as yet, contain any information. So, it seems that this idea is progressing and perhaps should be a new thread. We might find out more information during UDS.

---

### Post by craig10x on 2014-06-03
Very good...how has the stability been on 14.10 so far...any major problems or pretty smooth going?
I've been tempted to get back in but so far have managed to resist ;) :D

---

### Post by cariboo on 2014-06-03
UDS is next week, so we should see what the plans for Utopic are towards the end of the week.

---

### Post by craig10x on 2014-06-03
Just wondering...if i did decide to upgrade into 14.10 development, my usual way to upgrade is using the iso installer's option to do so...so i know how to do it that way...
If instead, i wanted to try the method using the ubuntu updater (since i never did that before) what terminal commands to you enter to trigger that off?

---

### Post by DogMatix on 2014-06-04
> **craig10x said:**
> Just wondering...if i did decide to upgrade into 14.10 development, my usual way to upgrade is using the iso installer's option to do so...so i know how to do it that way...
If instead, i wanted to try the method using the ubuntu updater (since i never did that before) what terminal commands to you enter to trigger that off?

grahammechanical mentions how to update your sources.list to development repositories in [post #4]("http://ubuntuforums.org/showthread.php?t=2217534&p=12991133#post12991133") and vagrale mentions how to update your sources.list to utopic repositories in [post #7]("http://ubuntuforums.org/showthread.php?t=2217534&p=12999892#post12999892")

---

### Post by startas on 2014-06-04
Well, one thing that is bad using development versions is that quite a few ppas are only for stable ubuntu versions, like wine, qbittorrent and so on, so you cant test everything.

---

### Post by grahammechanical on 2014-06-04
> [COLOR=#000000]what terminal commands to you enter to trigger that off?[/COLOR]

> sudo do-release-upgrade -d

[https://help.ubuntu.com/12.10/serverguide/installing-upgrading.html](https://help.ubuntu.com/12.10/serverguide/installing-upgrading.html)

> [COLOR=#000000]quite a few ppas are only for stable ubuntu versions, like wine, qbittorrent and so on, so you cant test everything.[/COLOR]

install the ppa using add-apt-repository. That will set up the repository/software source as a utopic repository but the the ppa for utopic does not exist. So, edit the repository url and change the distribution to trusty from utopic and the install the software. We do that in System Settings>Software and Updates>Other Software>Edit. After the application has been installed disable the ppa and it then it will not prevent normal updates.

I have used this to install audio-recorder from its trusty ppa into Utopic. So, I am able to test if it runs on Utopic as well as it runs on 14.04.

Oh, stuff like wine is in the Utopic software centre. But if you want the latest from the ppa, then try it this way.

Regards.

---

### Post by startas on 2014-06-04
I know that way, but it doesnt work always, sometimes dependencies packages are different version, and you cant install program.

---

### Post by craig10x on 2014-06-04
Thanks...i am considering it...although another thing i might do is just install a newer kernel from Utopic...i was considering that also...

I am very happy with the way my 14.04 is running expect for one problem...the last kernel update brought back the instability problems (with radio streams, playing mp3s and you tube music videos which i previously reported on) which 14.04 originally took care of...

However i recently tested a live session of utopic, and the kernel currently in use on 14.10 corrected that problem on my hardware...but i wasn't sure how risky it would be to install the current 14.10 kernel on my 14.04 install...
Also, i would need some information on how to do that...and what you would need to do to remove it if it causes problems...

When you install an advanced kernel on a system that is using an older one (like Trusty)...is there much chance of borking things?  Also, assuming it runs fine, what happens when you get software updates from ubuntu?  do you get updates for the kernel you newly installed or for the old one that currently runs on the system (Trusty in this case)...

---

### Post by craig10x on 2014-06-04
Oh i did find this neat article on how to do it:
[http://linuxg.net/how-to-install-kernel-3-15-rc-4-on-ubuntu-linux-mint-and-their-derivative-systems/](http://linuxg.net/how-to-install-kernel-3-15-rc-4-on-ubuntu-linux-mint-and-their-derivative-systems/)

Still, i was wondering if anyone here can tell me these three things:
Is it really risky to add this 14.10 kernel to 14.04 at this time?   Will it cause problems with other stuff as they get updated in 14.04?  What happens when you get the updates? (will it be updated on the utopic kernel or updated on your previous trusty kernel)...

---

### Post by zika on 2014-06-04
> **craig10x said:**
> Oh i did find this neat article on how to do it:
[http://linuxg.net/how-to-install-kernel-3-15-rc-4-on-ubuntu-linux-mint-and-their-derivative-systems/](http://linuxg.net/how-to-install-kernel-3-15-rc-4-on-ubuntu-linux-mint-and-their-derivative-systems/)

Still, i was wondering if anyone here can tell me these three things:
Is it really risky to add this 14.10 kernel to 14.04 at this time?   Will it cause problems with other stuff as they get updated in 14.04?  What happens when you get the updates? (will it updated on the utopic kernel or update on your previous trusty kernel)...I do not see any possible risk, I've been using mainline kernels (almost all the time I'm using 999 (daily) and some of 997, 996, 994...) for more than couple of years, as far as I remeber, both in U+1 periods and in „regular“ ones, and I was/am very happy with them... 3.15 is already at rc8 pending final version... Waiting for 3.16... Just take a look on names of these packages and You will see why they will not interfere with any of those that will come through „regular“ upgrades...

---

### Post by craig10x on 2014-06-04
Thank you Zika....sounds encouraging :D
Just two more things...when installed, what happens with the ubuntu software updater...would it be giving me kernel updates on the trusty kernel or the utopic kernel that i installed?
Also, if i had to remove it, will grub automatically boot back into the previous (trusty) kernel?

---

### Post by zika on 2014-06-04
> **craig10x said:**
> Thank you Zika....sounds encouraging :DYou're welcome...
> **craig10x said:**
> Just two more things...when installed, what happens with the ubuntu software updater...would it be giving me kernel updates on the trusty kernel or the utopic kernel that i installed?
As I wrote:> **zika said:**
> ...Just take a look on names of these packages and You will see why they will not interfere with any of those that will come through &#8222;regular&#8220; upgrades...No collision is imminent if names are OK...
> **craig10x said:**
> Also, if i had to remove it, will grub automatically boot back into the previous (trusty) kernel?&#8222;Automatically&#8220; is ill defined here. It depends of which kernel You add to Your system. In Grub, if not changed from default, it will boot from the kernel with &#8222;highest&#8220; number (not freshest) so, for example, 3.15-rc8 takes precedence on 3.15-999 even though 999 is fresher than rc8... And so on...You might have to change Grub configuration file(s)... (/etc/default/grub + update-grub...)

---

### Post by craig10x on 2014-06-04
Also, i would imagine you could probably adjust it on the grub menu itself, right? (when you boot up and go into the manual settings where you can change the kernel order to the one you want to boot off)
Oh yes, and what about updates...would you get updates on that utopic kernel as a result of installing it in trusty?

---

### Post by zika on 2014-06-04
> **craig10x said:**
> Oh yes, and what about updates...would you get updates on that utopic kernel as a result of installing it in trusty?Now I'm confused and starting to suspect I misunderstood You from the very start... I was talking about kernel .deb-s from mainline ([http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/))... If „utopic“ in their name bothers You it shouldn't because it is there just for naming and ordering purposes, it is not firmly connected to Ubuntu release per se... By using [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) You do not get any kind of automatic upgrades, it is not PPA as others are... If You think about adding .deb from Ubuntu repositories again You should not worry as long as You take care about names and version numbers... (as wrote above)...
So, make Your words „utopic kernel“ more precise...

---

### Post by craig10x on 2014-06-04
I guess i am getting confused then :confused:
so, the method he showed in my linked article, is the ppa mainline, correct?  And with that i would not get any further updates?  So then if in the future i wanted a newer update on that kernel i would need to do it manually again, then?

---

### Post by zika on 2014-06-04
> **craig10x said:**
> I guess i am getting confused then :confused:
so, the method he showed in my linked article, is the ppa mainline, correct?  And with that i would not get any further updates?  So then if in the future i wanted a newer update on that kernel i would need to do it manually again, then?For mainline: my point exactly, its how it works...
Do not forget to clean leftovers regularly so not too much space get wasted and Grub get clogged with unnecessary (old) kernels...

---

### Post by craig10x on 2014-06-04
Thanks :D
One last item: does anyone have a link to the ubuntu page that shows the release schedule for the point versions of 14.04, like 14.01 and so forth...i can't seem to locate it...
edit: i found it...never mind...thanks again to all...

---

