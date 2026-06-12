---
title: "Is Ubuntu right for me?"
date: 2006-11-11
forum: The Cafe
---

### Post by cypher543 on 2006-11-11
Sorry if this is the wrong place to post this...

I am a Fedora Core 5 user, and I'm absolutely SICK of yum. I've been using Linux for about 2 years now, so I'm not exactly a newbie, but Ubuntu has always had this "Only for newbies" style. I understand that's what you are trying to advertise, but it kind of puts us Intermediate Linux Users off.

So, can I use Ubuntu for the type of things I use Fedora for? Such as hosting a development server for my web projects, developing software (Python, Ruby, Ferite, C/C++, Mono), XGL/Compiz (I understand FC6 comes with this, but I can't upgrade because of a slow connection, which is one reason why I like the 1-CD Ubuntu install).

Thanks,
David

---

### Post by ComplexNumber on 2006-11-11
> 
I am a Fedora Core 5 user, and I'm absolutely SICK of yum.why don't you download apt and use that instead?

> 
So, can I use Ubuntu for the type of things I use Fedora for? Such as hosting a development server for my web projects, developing software (Python, Ruby, Ferite, C/C++, Mono), XGL/Compiz (I understand FC6 comes with this, but I can't upgrade because of a slow connection, which is one reason why I like the 1-CD Ubuntu install).if you have a slow connection, thats 1 good reason NOT to prefer the 1cd install.

---

### Post by .t. on 2006-11-11
Ubuntu is right for everyone!

---

### Post by shining on 2006-11-11
> **cypher543 said:**
> 
So, can I use Ubuntu for the type of things I use Fedora for? Such as hosting a development server for my web projects, developing software (Python, Ruby, Ferite, C/C++, Mono), XGL/Compiz (I understand FC6 comes with this, but I can't upgrade because of a slow connection, which is one reason why I like the 1-CD Ubuntu install).


If there is one thing you can do in one particular distrib, you can do it in any linux distrib. The only problem is that it may not be as easy.
But running servers (unless it's an exotic one, what do you mean by development server?), or developing software (unless it's an exotic language, I never heard about Ferite :)) shouldn't be a problem.

---

### Post by Dual Cortex on 2006-11-11
> **cypher543 said:**
> Sorry if this is the wrong place to post this...

I am a Fedora Core 5 user, and I'm absolutely SICK of yum. I've been using Linux for about 2 years now, so I'm not exactly a newbie, but Ubuntu has always had this "Only for newbies" style. I understand that's what you are trying to advertise, but it kind of puts us Intermediate Linux Users off.

So, can I use Ubuntu for the type of things I use Fedora for? Such as hosting a development server for my web projects, developing software (Python, Ruby, Ferite, C/C++, Mono), XGL/Compiz (I understand FC6 comes with this, but I can't upgrade because of a slow connection, which is one reason why I like the 1-CD Ubuntu install).

Thanks,
David

Well... unless you're an alien or so... remember, Ubuntu is Linux for human beings!

---

### Post by teet on 2006-11-11
> but Ubuntu has always had this "Only for newbies" style

I suppose one could look at it that way.  I started using Ubuntu after I was already somewhat familiar with linux (I had used redhat 9, a couple of the first fedora cores, mandrake, and a few other various distros) so I was sort of an "intermediate" user when I started with Ubuntu and I haven't had any complaints. 

I think I like Ubuntu so much because on a default install it gives me a basic gnome desktop with the major programs I want to use.  From there, I usually use Automatix or something to install all the extra stuff I need and I have a fully functional linux desktop in a few hours time.

-teet

---

### Post by cypher543 on 2006-11-11
> why don't you download apt and use that instead?
Because it isn't an officially supported package manager for Fedora. And frankly, I'd like to try something new.
> if you have a slow connection, thats 1 good reason NOT to prefer the 1cd install.
By slow connection, I meant slow enough that I can't download 3GBs worth of packages in one go. 1 CD for Ubuntu gives me everything I need to start out, and then I'll just apt-get what I need later.
> what do you mean by development server?
Just the basic LAMP setup.

---

### Post by TBOL3 on 2006-11-11
Just download the liveCD, try it, if you like it, put it on your computer.

BTW  aptitude is better the apt-get

---

### Post by ComplexNumber on 2006-11-11
> And frankly, I'd like to try something new.and what exactly did you have i mind if you don't want to use yum or apt-get? there's only Smart and thats available for both the fedora and ubuntu.



> 
By slow connection, I meant slow enough that I can't download 3GBs worth of packages in one go. 1 CD for Ubuntu gives me everything I need to start out, and then I'll just apt-get what I need later.that slow connection is going to hinder you a lot. evrything that you're wanting is on the fedora dvd.

---

### Post by TBOL3 on 2006-11-11
Here's another thought, go to a store, and pick up a copy of FC6, for no more then $10.

What is you'r connection speed anyway?

---

### Post by darrenm on 2006-11-11
I consider myself an intermediate to advanced user, I've used Mandrake/iva, Suse, RedHat, SCO (boo) OpenServer etc. and I work supporting Unix/Linux systems.

I find Ubuntu the most refreshing distro and I can't stand working on anything non-debian now. Everything just makes more sense.

Like configuring the NIC's. In RH based systems its /etc/sysconfig/network-scripts/ifcfg-eth* and on Debian based systems its /etc/network/interfaces
You also have /etc/networks which you can define subnets so the routing tables makes more sense. Everything is just so much better thought out.

The default setup of the packages is much better too. When you install something you get the config files broken down into a few different config files so that if anything changes between software updates your config doesnt change, only the default config files get overwritten. Thats so much  better than having to compare the *.cf.rpmsave and the original *.cf and deciding why it broke.

Lots of little things too make more sense on Debian based systems.

The biggie is APT though. When working on RH systems I have to search pbone for RPM's, find deps that are needed, search pbone some more etc. whereas APT does everything for me. So much better for deps than any RPM based system was including urpmi.

The only things you will miss are chkconfig (theres debs out there anyway) and service (and its debatable if its better typing /etc/init.d/{} restart or service {} restart anyway). The alternatives are invoke-rc.d and update-rc.d but I never use em.

Make the switch to Debian, it kicks ***. Ubuntu is by far the most supported and popular distro out there now and is getting bigger all the time. Any time you want to install anything in the future you can bet its going to be tested on Ubuntu first and FC / RH second.

---

### Post by ComplexNumber on 2006-11-11
> When working on RH systems I have to search pbone for RPM's, find deps that are needed, search pbone some more etc.in that case, you must be a very  inexperienced user of red hat systems. why don't you just install either livna-release or freshrpm-release rpm, then everything is set up for you? answer: because i doubt you have used red hat systems for more than 1 day.
if you think that using debian gets you away from that mythical fairy tale of old called "dependency hell", think again. i had more dependency problems in one day of using ubuntu than in 6 months of using fedora.

---

### Post by TBOL3 on 2006-11-11
Intresting, I've done better with dependincies with ubuntu, I could never get ANYTHING inslled with fedora.

---

### Post by ComplexNumber on 2006-11-11
> **TBOL3 said:**
> Intresting, I've done better with dependincies with ubuntu, I could never get ANYTHING inslled with fedora.
why do you think that is? i was forever getting dependency problems with ubuntu after finally getting the LAN to work (i had to manually change the DNS server from the router to that of my ISP each time i accessed the repos).

---

### Post by TBOL3 on 2006-11-11
That would do it :)

---

### Post by IYY on 2006-11-11
I think Fedora Core is actually more of a newbie distro than Ubuntu, in the sense that a lot more is done via GUI in it.

---

### Post by darrenm on 2006-11-11
> **ComplexNumber said:**
> in that case, you must be a very  inexperienced user of red hat systems. why don't you just install either livna-release or freshrpm-release rpm, then everything is set up for you? answer: because i doubt you have used red hat systems for more than 1 day.
if you think that using debian gets you away from that mythical fairy tale of old called "dependency hell", think again. i had more dependency problems in one day of using ubuntu than in 6 months of using fedora.

Wow where did that one come from?

You are correct I haven't used any FC releases (or non-release should that be)

But you are incorrect that I haven't used Red Hat based distros for more than one day. I started with Mandrake 7 and was using that ever since until I switched to Ubuntu. I also administer a few RH6/7/9 and RHEL4 servers as part of my job.

If you had dependency problems in Ubuntu then you must be a very inexperienced Linux user in general.

---

### Post by ComplexNumber on 2006-11-11
>  If you had dependency problems in Ubuntu then you must be a very inexperienced Linux user in general.i've been using linux since about 1996 you cheeky so'n'so. i had dependency problems in ubuntu because lots of dependency problems exist in ubuntu, so don't tell me they don't. ans what can the user do to rectify them? answer: absolutely nothing. (or don't use multiverse and universe. this leaves about 4500 packages in total to avoid the avalanche of dependency issues).

---

### Post by kvonb on 2006-11-11
```
Wow where did that one come from?
```

..that's the typical "attitude" you get from the fedora camp, they are God, don't ever question them!

RTFM!

---

### Post by Daveski on 2006-11-11
> **cypher543 said:**
> 
...
Just the basic LAMP setup.

If you install the 'server' version of ubuntu it gives the option for a LAMP setup. I think you can then easily install which ever flavour of the desktops [U,K,X]ubuntu with a couple of simple commands (assuming you want a GUI). No doubt some more seasoned users will give you better info on this as I have not actually done this myself.

---

### Post by darrenm on 2006-11-12
> **ComplexNumber said:**
> i've been using linux since about 1996 you cheeky so'n'so. i had dependency problems in ubuntu because lots of dependency problems exist in ubuntu, so don't tell me they don't. ans what can the user do to rectify them? answer: absolutely nothing. (or don't use multiverse and universe. this leaves about 4500 packages in total to avoid the avalanche of dependency issues).

I'm flabbergasted. I copy exactly what you say to me then *I'm* a cheeky so n so?!

Just out of interest - not saying theres anything wrong with it for a moment but if you prefer FC/RH to Ubuntu why are you posting (quite a lot) in a Ubuntu forum?

---

### Post by TheWizzard on 2006-11-12
> **cypher543 said:**
> Sorry if this is the wrong place to post this...

I am a Fedora Core 5 user, and I'm absolutely SICK of yum. I've been using Linux for about 2 years now, so I'm not exactly a newbie, but Ubuntu has always had this "Only for newbies" style. I understand that's what you are trying to advertise, but it kind of puts us Intermediate Linux Users off.

So, can I use Ubuntu for the type of things I use Fedora for? Such as hosting a development server for my web projects, developing software (Python, Ruby, Ferite, C/C++, Mono), XGL/Compiz (I understand FC6 comes with this, but I can't upgrade because of a slow connection, which is one reason why I like the 1-CD Ubuntu install).

Thanks,
David

i switched from fedora to ubuntu about half a year ago. fedora and ubuntu both have their pros and cons. 
the major differences are in package management, and networking.

advantages of ubuntu over fedora are, in my opinion:
- kde support
- very good community help and exellent howto's

a disadvantage is the lack of new software in the backports.

---

### Post by darrenm on 2006-11-12
Face it guys, from now on there is only going to be one desktop Linux and all other distros will get more and more niche. Novell could see it happening which is why they took the easy way out.

[http://www.google.com/trends?q=fedora%2C+ubuntu](http://www.google.com/trends?q=fedora%2C+ubuntu)
[http://www.google.com/trends?q=redhat%2C+ubuntu](http://www.google.com/trends?q=redhat%2C+ubuntu)

Theres loads more sources showing the downward spiral of Red Hat/FC, Opensuse etc. and the continual rise of Ubuntu but I'm sure you get the picture.

---

### Post by teet on 2006-11-12
> **ComplexNumber said:**
> in that case, you must be a very  inexperienced user of red hat systems. why don't you just install either livna-release or freshrpm-release rpm, then everything is set up for you? answer: because i doubt you have used red hat systems for more than 1 day.
if you think that using debian gets you away from that mythical fairy tale of old called "dependency hell", think again. i had more dependency problems in one day of using ubuntu than in 6 months of using fedora.

You seem to have a very hostile attitude ComplexNumber.  People are only trying to help.

-teet

---

### Post by ComplexNumber on 2006-11-12
> **teet said:**
> You seem to have a very hostile attitude ComplexNumber.  People are only trying to help.

-teet
quite the contrary. somebody has to correct other peoples slanted info.

---

