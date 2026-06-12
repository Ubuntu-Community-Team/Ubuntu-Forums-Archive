---
title: "My plans for Linux"
date: 2019-06-06
forum: Ubuntu, Linux and OS Chat
---

### Post by ubotbuddy on 2019-06-06
The following are Linux flavors I am planning on downloading and installing.


Ubuntu  (i'm already using this one)
Arch Linux
Debian
openSUSE
Linux Mint


There is rhyme and reason why I am doing this.


I provide software support for proprietary software application.  Many of the users have been wanting the application on their Linux systems.  So I will be testing our software on the ones I have listed above.


I have started with Ubuntu using VirtualBoxes of Windows XP, 7 and 10.  Now I am moving to Wine and the other available linux apps that provide windows execution.


Ubuntu will be my primary OS.  The others will be simple default setups just for testing purposes.  I'm not planning on becoming an expert in these flavors (maybe Ubuntu lol).


Are there any linux distros that might be good to consider?  I won't be able to do all of them but I want to keep relevant ones available.


No, I did not mention any Apple products.  That platform is not in my budget unless someone wants to give me one.  :)


I welcome all comments.  


Thanks


Buddy

---

### Post by crip720 on 2019-06-06
Thinking a Fedora/CentOS/Redhat version, after testing Ubuntu/Debian and Arch.  Mint should only be needed to make sure it works, since based on Ubuntu. Think they are the big three platforms that most others are based on.

---

### Post by ubotbuddy on 2019-06-06
Thanks for sharing.  I'll add them to my second phase of todos.

Didn't Redhat switch to a paid version a few years ago?

Buddy

---

### Post by mastablasta on 2019-06-07
yes you need to pay for redhat. however centos is built from redhat source libraries and fedora is redhat testing version (or more like releases between the LTS).

---

### Post by ubotbuddy on 2019-06-07
That's good to know.  Thanks for sharing.

Buddy

---

### Post by Rubi1200 on 2019-06-07
You might want to also look into Slackware and Gentoo for something more, let's say, different.

---

### Post by kurt18947 on 2019-06-07
I'm not in the I.T. biz but I think the U.S. corporate world is more likely to run Red Hat if they run any sort of Linux. So yeah, that would be one to consider, well CentOS due to price.

---

### Post by ubotbuddy on 2019-06-07
Thanks.  I made notes for future reference when I get to these.

i was doing more reading on Wine HQ site and during some Googling I came across these.

PlayOnLinux  -free (based on Wine)
CrossOver     -paid (based on Wine)
Lutris

Are these worth considering at some point?  CrossOver just because they provide support for WineHQ and the app may be more stable.  I did watch a few videos of Lutris and I was impressed by the way it sets up the environment.  I realize gamers are using it mostly but could business apps benefit...I don't know.

As I develop my testing process I don't want to miss a good thing or waste my time on the wrong rabbit trail.

Thanks for any comments.

Buddy

---

### Post by TheFu on 2019-06-07
You need to target the Linux versions that your clients use.  I wouldn't try to target all, since each additional OS brings additional support costs.
You didn't say - is this a server product or desktop product?  Below, I assume servers. 
The industry also matters.  Financial people will use RHEL - about 90% of the time.
Cloudy companies will use CentOS/Debian/Ubuntu, except the huge cloudy people who will have 100% custom linux versions.

CentOS - that covers RHEL of the same version.  You need v7 and v8 now.
Debian Stable, whatever that is.

All the others are "also ran" especially if you aren't creating a native application.  My business won't touch WINE solutions. We'll go with a native competitor or install it on Windows and remotely access it.  WINE is just too much hassle and breaks too often.

Very few businesses will ever have Arch for any servers. Arch is a developer distro, not business.  More businesses will have SUSE Enterprise than Arch and Gentoo and Slackware combined.

My company uses Ubuntu Server primarily. We don't dictate which client OS our people run.  We are very different from most companies.

---

### Post by ubotbuddy on 2019-06-08
The product I provide support for is a programming platform.  It's built with C# and .Net and we also have APIs in the product whereby Python routines can be pulled in.  There are some businesses that use it but the bulk of our user community are independent people carving out a business for themselves as well as the few Blackhatters abusing the product.

For the most part, it runs great on Windows but not every computer is like the one next to it.  What we have found, in some limited testing, is that once Mac users configure their system correctly they have fewer issues since they are running on Parallels within their OS.  In a couple of User instances they have overcome their Windows issues by running Linux using Wine.  Unfortunately, they won't share what they did for fear their unique system will be compromised for whatever reason.

So for now, we are targeting this potential solution for us to our main stream users that don't have a huge hardware budget.

I would share the product's name here but my purpose is to not get more sales.  I'm not a sales guy or even an affiliate person.  I'm just a 61+ year old computer geek keeping my sideline job (easy monthly money) relevant within this industry.

Thanks

Buddy

---

### Post by mastablasta on 2019-06-10
> **ubotbuddy said:**
>  In a couple of User instances they have overcome their Windows issues by running Linux using Wine. 

Wine runs on MacOS.

it is not an emulator. instead it convinces the software that it is running on Wine. sometimes you would need to add certain original microsoft libraries to make it work. sometimes software needs older libraries. it realyl is hit or miss. All crossover, play on linux, proton (from Steam), Lutris use Wine. they just to a better or worse job at preconfiguring it. so as long as you know how to configure it, and what to run when certain error appears or what it means you could make a script yourself.


so for example you can install Oblivion (game) in wine. but it won't run by default. it needs additional and original library, you need to set some libraries to ignore or something like that. and you do that through menu, or commands or configuration file and configure it. then it all runs.

now if you install it for example in Lutris, all this pre-configuration is done for you, because someone else identified what is needed to make the game run and then preconfigured it. if these ocnfigurations are maintained (means with each version someone checks if all is still good) then installing a software is as easy as in windows. 

so if you wan to run your customised software and make it easy to install you would need to set it up. see if there are any issues, then resolve them and create the install script.

---

### Post by TheFu on 2019-06-10
WINE is a layer of compatible win32 calls translated into the native Linux calls.  If there was a 1-for-1 translation, that would make WINE a trivial layer, but because all OSes use global variables with state data stored internally, the WINE layer has to know what needs to be local-only data and what needs to be available for the duration of the total environment run.  I know that WINE was only available on x86 CPUs, so when/if apple changes to non-x86 CPUs, all those users will likely have issues, unless they use a CPU emulator below the WINE environment.

I spent about a month figuring out how to get Quicken 2011 working under WINE.  Only got the main stuff working well. None of the tax planning things ever worked. They were tied into online resources and IEv5 (I think).  At my next Quicken 2013 install, the settings for 2011 didn't work and I just didn't care enough to go through all the effort again. Since I had a Windows machine inside a VM doing very little, I just loaded it there and stopped fighting.  Windows runs reasonably well in a virtual machine and putting software used once a week into that VM isn't a big deal, I would prefer an easy WINE install.  I don't think Intuit has any interest based on their multiple attempts to get out of the home-user software business.

No issues with easy, legal, money here.

---

### Post by ubotbuddy on 2019-06-10
Thanks for sharing guys.  I figured there was going to work.  Nothing comes for free ... there's always a price to pay.

Buddy

---

