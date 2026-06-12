---
title: "Suggestion to Canonical re. Ubuntu"
date: 2008-04-23
forum: Testimonials &amp; Experiences
---

### Post by Voxan on 2008-04-23
Hi all,

About me first (before any negative comments appear): I am a Ubuntu enthusiast since 3 months, I happily made the switch on my more than 2 year old laptop Acer Aspire 3020 (still haven't managed to have the WiFi card work though).

These comments may be incorrect because i am not an experienced user yet, so please correct me if applicable.

I have 2 objections:


1) I'm slightly concerned about Hardy Heron in so far as it ships software that includes beta software (Firefox 3 beta 5) and it does not always include the latest version of the Linux kernel (2.6.24 instead of 2.6.25 that was released a week ago).

I don't use Ubuntu as a professional, but I'm thinking that companies (Canonical's primary target) will feel concerned about that, if they have to deploy Ubuntu on 50+ PCs. Of course, the auto update process will solve these problems, but can we not suggest to Canonical to release a "clean" uptodate ISO let's say every 3 months after a new release, that would include the latest packages/kernels etc? It would save a lot of time & bandwidth to everyone if we consider an installation in a few months on 50+ PCs in a company! Also it's psychologically better not to have any "beta" software running as for people from the Windows world it means great instability (I know that some beta Linux apps run are more reliable than many final Windows apps, but that is not obvious in everyone's mind, especially for companies thinking of switching).


2) The auto update application is actually very slow to release new packages! I do not know how to compile sources without looking up a tutorial online, but I do enjoy having the latest stable version of a package. For Firefox, I had to wait 2 weeks for the auto update to offer me the update to 2.0.0.14 (even though I checked manually everyda if new updates were available), so during 2 weeks I was potentially under threat as some security fixes had been patched with the new version! Same problem for Pidgin, I wanted the latest version, which I had to download from their website and compile on my own (takes time on my slow PC!) as only an old version is available in the repositories! What's even more stupid is now the auto updater asks to "update" to the old version! It is the same problem for many packages! A Mac or Windows user can benefit from the latest open source applications immediately when we have to wait sometimes a long time before benefiting from them!



For the rest, it's all good. Keep up the good work. I wish Hardy Heron will be THE Linux desktop OS (and that it natively supports my WiFi...).

Give me your thoughts, on how to make our cherished OS better!

---

### Post by jdrodrig on 2008-04-23
> **Voxan said:**
> 
1) I'm slightly concerned about Hardy Heron in so far as it ships software that includes beta software (Firefox 3 beta 5) and it does not always include the latest version of the Linux kernel (2.6.24 instead of 2.6.25 that was released a week ago).


There is of course a stability tradeoff, in releasing very latest releases...but that is the magic of linux, you can *choose* to upgrade it if you want..freedom!

---

### Post by jdrodrig on 2008-04-23
> **Voxan said:**
> Hi all,

I don't use Ubuntu as a professional, but I'm thinking that companies (Canonical's primary target) will feel concerned about that, if they have to deploy Ubuntu on 50+ PCs. Of course, the auto update process will solve these problems, but can we not suggest to Canonical to release a "clean" uptodate ISO let's say every 3 months after a new release, that would include the latest packages/kernels etc? 

I am afraid I dont understand your point. are you saying you rather have a larger update every three months than a more segmented upgrade every week or so? The obvious answer is that you can choose not to do the weekly or so upgrades..

I think the philosophy of canonical is not to wait to have a "major" upgrade but to release the latest/stable version of single components as they become available...

---

### Post by Vadi on 2008-04-24
I'm afraid shipping a kernel that's out just a week before release, with an LTS version, is not exactly proper.

FF3 has been in testing for quite a while now though; and they can't use FF2 because that won't be supported for 3 years down the road.

---

### Post by Voxan on 2008-04-24
Hello & thank you for your comments.

> **jdrodrig said:**
> I am afraid I dont understand your point. are you saying you rather have a larger update every three months than a more segmented upgrade every week or so? The obvious answer is that you can choose not to do the weekly or so upgrades..

I did not mean that, I was just thinking not everyone will deploy Hardy today. So if every 3 months after a release Canonical released an ISO with all new supported updates included then it would be a major argument in favor of Ubuntu. If in August 2008 some businesses are thinking of switching to Linux and hesitate between some of the major distros, they may choose to go for a distro that has released an ISO/CD/DVD more recently than the upcoming Hardy, just as it would seem more uptodate "out of the box".

My understanding is it would only take a very short time for Canonical to do so, instead of having an ISO up to 6 months old present on the server and then having to upgrade all packages (waste of time & bandwidth). So my message was targeting new users.

> **Vadi said:**
> I'm afraid shipping a kernel that's out just a week before release, with an LTS version, is not exactly proper.

FF3 has been in testing for quite a while now though; and they can't use FF2 because that won't be supported for 3 years down the road.

Ok Vadi, thanks.


Anyone has any comments on the 2nd part of my intial suggestions?

---

### Post by linuxlizard on 2008-04-24
Well, the second part is that way because people don't like to break their systems. Linux is a little different from windows- everything has to be working in harmony and a new version of the gimp for example, might require the latest version of a dozen dependencies or whatever. Each of these have to be working properly with other apps and dependencies and so forth, like a big chain. Every linux has their own way of dealing with this problem. Some tend to have more bleeding edge software and then users get their systems broken every so often and accept it and deal with it. Ubuntu is geared towards novice as well as expert users, so they side for as close as possible to the latest while keeping systems safe from breaking. And they do a pretty good job of it.

You can do a couple of things as a user if you want things more current:
1) Make sure you have backports enabled in your repositories
2) Visit getdeb.net and bookmark it. They regularly update their packages to the latest and their package list is constantly expanding. If you have hardy, they won't have a lot at the moment, but if you take a look at gutsy you will see that they have many many apps. It grows over the months until the next release.
3) Many apps have the latest versions on their homepage, and offer either deb files which can be installed by clicking on them on the site, or instructions for adding them to your list of repositories so autoupdater will find them just like normal ubuntu type packages. Wine is an example of an app that offers this service.

---

### Post by Voxan on 2008-04-24
Great thanks for the message linuxlizard :). Really to the point.

Hey guys Hardy is out on time as promised. Well done Canonical & the community :guitar:
I already have the ISO, will install this weekend!

---

### Post by hyper_ch on 2008-04-25
if you roll it out on a regular schedule to a few machines again, then I'd suggest you setup a mirror for the ubuntu repositories.

Then you would not required for each individual machine to fetch the updates from the net but you would set them to fetch the updates from your own mirror.

---

### Post by hyper_ch on 2008-04-25
> **jdrodrig said:**
> I think the philosophy of canonical is not to wait to have a "major" upgrade but to release the latest/stable version of single components as they become available...

Actually, there are no updates within a release... just bug fixing and security fixes will be provided...

---

### Post by Voxan on 2008-05-14
Wow I am sure Mark Shuttleworth himself must have read my post, or that some of his employees has. Indeed, this comes from his blog ([http://www.markshuttleworth.com/archives/146](http://www.markshuttleworth.com/archives/146)):

"We also committed, for the first time, to a regular set of point releases for 8.04 LTS. These will start three months after the LTS, and be repeated every six months until the next LTS is out. These point releases will include support for new hardware as well as rolling up all the updates published in that series to date. So a fresh install of a point release will work on newer hardware and will also not require a big download of additional updates."

I had suggested more than 2 weeks ago I think:

> **Voxan said:**
> I don't use Ubuntu as a professional, but I'm thinking that companies (Canonical's primary target) will feel concerned about that, if they have to deploy Ubuntu on 50+ PCs. Of course, the auto update process will solve these problems, but can we not suggest to Canonical to release a "clean" uptodate ISO let's say every 3 months after a new release, that would include the latest packages/kernels etc? It would save a lot of time & bandwidth to everyone if we consider an installation in a few months on 50+ PCs in a company! Also it's psychologically better not to have any "beta" software running as for people from the Windows world it means great instability (I know that some beta Linux apps run are more reliable than many final Windows apps, but that is not obvious in everyone's mind, especially for companies thinking of switching).

I'm a rockstar!

---

### Post by ukripper on 2008-05-14
> **Voxan said:**
> Hi all,

About me first (before any negative comments appear): I am a Ubuntu enthusiast since 3 months, I happily made the switch on my more than 2 year old laptop Acer Aspire 3020 (still haven't managed to have the WiFi card work though).

These comments may be incorrect because i am not an experienced user yet, so please correct me if applicable.

I have 2 objections:


1) I'm slightly concerned about Hardy Heron in so far as it ships software that includes beta software (Firefox 3 beta 5) and it does not always include the latest version of the Linux kernel (2.6.24 instead of 2.6.25 that was released a week ago).



.25 is not a stable kernel. Even number are stable releases of kernels that is why hardy wasn't ship with .25. u can live with beta software but not with unstable kernel release

---

### Post by smartboyathome on 2008-05-14
> **ukripper said:**
> .25 is not a stable kernel. Even number are stable releases of kernels that is why hardy wasn't ship with .25. u can live with beta software but not with unstable kernel release

Not true. They went away with that some time ago. It is a stable kernel release, just like others.

---

### Post by Keyper7 on 2008-05-14
> **Voxan said:**
> Wow I am sure Mark Shuttleworth himself must have read my post, or that some of his employees has. Indeed, this comes from his blog ([http://www.markshuttleworth.com/archives/146](http://www.markshuttleworth.com/archives/146)):

"We also committed, for the first time, to a regular set of point releases for 8.04 LTS. These will start three months after the LTS, and be repeated every six months until the next LTS is out. These point releases will include support for new hardware as well as rolling up all the updates published in that series to date. So a fresh install of a point release will work on newer hardware and will also not require a big download of additional updates."

I had suggested more than 2 weeks ago I think:



I'm a rockstar!

I think you're just joking, but in case you're not, a planned 8.04.1 release for July is on the Hardy Release Schedule since its first version, and I've been hearing about the commitment to a point release each three months since before January.

---

### Post by ukripper on 2008-05-15
I think 8.04.1 will make major difference

---

