---
title: "How do I totally remove all traces of Ubuntu One on my computer?"
date: 2009-07-21
forum: Ubuntu One (CLOSED)
---

### Post by wersdaluv on 2009-07-21
I want to have a fresh start with Ubuntu One. My configuration is borked. I reinstalled it for a few times but it still isn't working. I still don't see the connect button when accessing the "Ubuntu One" folder on Nautilus. 

How do I remove all traces of Ubuntu One on my computer? I want to have something fresh. That might make Ubuntu One work for me.

---

### Post by cbtengr on 2009-07-21
In Terminal try:

sudo apt-get remove –purge PACKAGENAME

Are you installing in 8.10?  See this thread:

[https://answers.edge.launchpad.net/ubuntuone-client/+question/73276](https://answers.edge.launchpad.net/ubuntuone-client/+question/73276)

---

### Post by Mia1990 on 2009-07-22
Remove the ppa first then

sudo apt-get remove –purge ubuntuone

I think that will do it

---

### Post by wersdaluv on 2009-07-22
All traces, huh? Let's see :D hehe

I'm on Jaunty :D

EDIT:
It doesn't... And oh, I purged with Synaptic. The code's invalid

---

### Post by hockeyhead019 on 2009-07-22
what do you mean you purged with synaptic?

u typed those commands into the terminal right? make sure you're typing:

sudo apt-get remove -purge ubuntuone

into the terminal and not the synaptic search bar :)

---

### Post by growingneeds on 2009-08-21
```
sudo apt-get remove --purge ubuntuone
```

---

### Post by pyjimbo on 2009-09-05
This did not work for me. I needed to do.

sudo apt-get remove --purge ubuntuone**-client**

---

### Post by cariboo on 2009-09-06
You can also add a wildcard to the command:

```
sudo apt-get purge ubuntuone*
```

---

### Post by james_mcl on 2009-10-23
Sorry to resurrect a dead thread, but will these commands still remove all traces of Ubuntu One on a Karmic install?

(Not the RC or beta, I mean the final version when it comes out.)

---

### Post by joshuahoover on 2009-10-26
> **james_mcl said:**
> Sorry to resurrect a dead thread, but will these commands still remove all traces of Ubuntu One on a Karmic install?

(Not the RC or beta, I mean the final version when it comes out.)

For those interested in removing, re-installing, and testing their new Ubuntu One install, please see this newly created FAQ: [https://answers.edge.launchpad.net/ubuntuone-client/+faq/778](https://answers.edge.launchpad.net/ubuntuone-client/+faq/778)

---

### Post by clicker4721 on 2010-01-06
@ joshuahoover: As far as actually getting rid of the program and packages, the thread you gave worked beautifully. But what about the bazillion dependencies it installed with it? Those are just hogging space now. I want to completely get rid of it, without intent to re-install because I use KDE and they do not play well together.

---

### Post by joshuahoover on 2010-01-15
> **clicker4721 said:**
> @ joshuahoover: As far as actually getting rid of the program and packages, the thread you gave worked beautifully. But what about the bazillion dependencies it installed with it? Those are just hogging space now. I want to completely get rid of it, without intent to re-install because I use KDE and they do not play well together.

You should be able to run the following command from a terminal session to remove all unused dependencies: sudo apt-get autoremove

This will show you the packages apt will remove and prompt you to allow it or not.

Thank you,

Joshua

---

### Post by clicker4721 on 2010-02-03
> **joshuahoover said:**
> You should be able to run the following command from a terminal session to remove all unused dependencies: sudo apt-get autoremove

This will show you the packages apt will remove and prompt you to allow it or not.

Thank you,

Joshua
Okay, perfect. Thank you a ton.

---

### Post by spiralx on 2010-02-06
Josh, I'm on 9.10.  When I tried your thread, the terminal said "rm" was an unknown option.

Whenever I click Ubuntu One in the Applications - Internet menu, it comes up with an error, something like "can't find url: ch... shiretoko" - which makes sense (kind of), since Firefox has moved on apace since them thar days!

But - don't know why it should want to "find shiretoko", or what to do about it.  So I thought I'd try un-installing, and re-installing.  But - so far, no go.

(I am told Dropbox is a better option, anyway...?)

---

### Post by joshuahoover on 2010-02-11
> **spiralx said:**
> Josh, I'm on 9.10.  When I tried your thread, the terminal said "rm" was an unknown option.

Whenever I click Ubuntu One in the Applications - Internet menu, it comes up with an error, something like "can't find url: ch... shiretoko" - which makes sense (kind of), since Firefox has moved on apace since them thar days!

But - don't know why it should want to "find shiretoko", or what to do about it.  So I thought I'd try un-installing, and re-installing.  But - so far, no go.

(I am told Dropbox is a better option, anyway...?)

It sounds like you may need to check your preferred web browser at: System->Preferences->Preferred Applications and make sure that your browser of choice is set properly there.

Thanks,

Joshua

---

### Post by spiralx on 2010-02-13
Ahhh...!  Light dawns!  Many thanks!  :D

I guess it came from when I manually added 3.5 (shiretoko) over the older version in a previous incarnation of Ubuntu, many months ago now!  When I upgraded to 9.10, it took the data with it...

---

### Post by karthick87 on 2010-06-09
I am not using ubuntuone,so is it safe to remove ubuntuone from my system..?

---

### Post by duanedesign on 2010-06-10
> **getyourkarthick said:**
> I am not using ubuntuone,so is it safe to remove ubuntuone from my system..?


yes it is safe. Just follow the first 7 steps of[ this FAQ]("https://answers.edge.launchpad.net/ubuntuone-client/+faq/778")

---

### Post by smartmeister on 2010-08-03
thanks a lot, everything went went after reinstalling ubuntu one

---

### Post by Gschischa on 2011-10-28
try this (as root)
> 
dpkg --get-selections|grep ubuntuone|grep -v 'deinstall'|awk '{ print $1}'|xargs apt-get -y purge


---

### Post by wyrvern on 2012-05-14
To fallback entirely, -- ie (gnome classic, etc) 11.10 (is my setup),
should work for some others unless you try to _over_ configure
your setup.

read this URL :

[http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-remove-unity-and.html](http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-remove-unity-and.html)

- wyr

---

### Post by oldos2er on 2012-05-14
Old thread closed.

---

