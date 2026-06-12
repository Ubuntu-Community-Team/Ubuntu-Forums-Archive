---
title: "Tiger rootkit detector"
date: 2009-08-01
forum: Security
---

### Post by kg84 on 2009-08-01
Hi guys...

I have just run Tiger and rebooted. Somehow, the running of this has knackered my boot-up into Ubu (on dual boot HP DV6 with Vista home premium).

I can still boot into Ubu fine, but it now takes three times as long and as I am booting into Ubu I am presented with a black screen displaying a bunch of stuff in the process of starting up. None of it seems bad. A few examples include Firestarter (FAIL - ie it appears that this is failing to start), TOR (complete with the message stating 'Dont rely on it for strong anonymity) and at the end I wait for abot 45 seconds whilst Mail Trannsfer Agent starts.

Whats up? Anyway I can get rid of this at start up?

Cheers.

---

### Post by kg84 on 2009-08-01
A bit more.

Firefox 3.5.1 does not seem to be saving its history / tabs opened.

Even the settings for the Ghostery add-on have reverted to default.

This is weird indeed.

Screenie attached shows an odd message displayed in FF when it starts.

EDIT: FF will now not save new book marks and indeed all of its settings have reverted to default (ie saving history, saving passwords etc)

---

### Post by kg84 on 2009-08-02
OK...

Running FF as root from the terminal restores my history and bookmarks.

Why would running tiger knacker so much?

(I have the HTML report if anyone would like a look at it).

---

### Post by hansdown on 2009-08-02
Hi kg84.

I think tiger is just pointing out vulnerabilities to your system.

I am by no means an expert, but my limited knowledge tells me this is likely the case.

> TIGER has one primary goal: report ways 'root' can be compromised.

This is from the package site.

[http://packages.ubuntu.com/jaunty/admin/tiger](http://packages.ubuntu.com/jaunty/admin/tiger)

Have you changed any firewall settings?

---

### Post by kg84 on 2009-08-02
> **hansdown said:**
> Hi kg84.

I think tiger is just pointing out vulnerabilities to your system.

I am by no means an expert, but my limited knowledge tells me this is likely the case.



This is from the package site.

[http://packages.ubuntu.com/jaunty/admin/tiger](http://packages.ubuntu.com/jaunty/admin/tiger)

Have you changed any firewall settings?

Hiya hansdown...

Nope, I changed no settings at all. I just ran $ sudo tiger -H, waited for it to finish and then rebooted. It was upon the reboot that all this started.

So odd that my start up time for Ubu is now around 4 mins instead of less than one. And then there's all the other stuff being displayed at start up too.

OK I see that tiger includes other apps, including the MTA - this will explain i guess why I see this thing starting when I boot into Ubu (any way I can stop it from starting up at this time?) And is this the reason for seeing other stuff starting up when I boot into Ubu, including Firestarter, which gets marked as FAIL. ?

Thanks :)

---

### Post by hansdown on 2009-08-02
The best I'm able to offer is a comparison output.

[http://taufanlubis.wordpress.com/2008/02/08/security-checker-tiger/](http://taufanlubis.wordpress.com/2008/02/08/security-checker-tiger/)

As far as stopping the startup problems,this should be left for someone who understands this program better than I.

---

### Post by kg84 on 2009-08-02
> **hansdown said:**
> The best I'm able to offer is a comparison output.

[http://taufanlubis.wordpress.com/2008/02/08/security-checker-tiger/](http://taufanlubis.wordpress.com/2008/02/08/security-checker-tiger/)

As far as stopping the startup problems,this should be left for someone who understands this program better than I.

My report looks very similar to the one in your link.

Lots of WARN's and a few FAIL's.

Thanks :)

---

### Post by kg84 on 2009-08-02
OK...

all that gumph at start up has been eliminated, courtesy of...

```
sudo sysv-rc-conf
```I zapped a few things including the Sendmail MTA and upon reboot, we are back to normal.

Now to sort FF :) (Any ideas on the message displayed in FF when run as non-root [see screenie a few posts back])

If any else has any thoughts on this matter, I'm all ears.

Cheers

---

### Post by hansdown on 2009-08-02
The part about firefox scares me the most.

Is it a threat to security? Almost certainly it could be.I love firefox, but it has been shown to have weaknesses, many are patched quickly by the devs.

The biggest problems are "user created". Please don't take that wrong.

If you save passwords,etc. in firefox, you stand a risk of them becoming known to whomever. It is not an ubuntu problem, it is placed squarely upon firefox's ability to defend against someone cracking the security.

---

### Post by kg84 on 2009-08-02
> **hansdown said:**
> The part about firefox scares me the most.

Is it a threat to security? Almost certainly it could be.I love firefox, but it has been shown to have weaknesses, many are patched quickly by the devs.

The biggest problems are "user created". Please don't take that wrong.

If you save passwords,etc. in firefox, you stand a risk of them becoming known to whomever. It is not an ubuntu problem, it is placed squarely upon firefox's ability to defend against someone cracking the security.


I never save any passwords in FF :)

But this FF problem is really starting to  upset me. Running it as non-root I have no history or tabs saved, nor to I have any fwd/back or page reload buttons - what the hell is this about?

Running sudo firefox and it runs fine.

As for your 'user created' statement - I agree. No doubt, there is something here staring me in the face that I cannot see. Something of my own making - after all nonsense like this just doesnt happen on its own.

it's all a learning experience, I guess :)

---

### Post by hansdown on 2009-08-02
I can honestly say that, I have never had to use root permissions to run firefox.

I have no desire to disrespect the hard work of the people who have brought us firefox, or tiger, but a bug report may be required for one of these.

---

### Post by kg84 on 2009-08-02
> **hansdown said:**
> I can honestly say that, I have never had to use root permissions to run firefox.

I have no desire to disrespect the hard work of the people who have brought us firefox, or tiger, but a bug report may be required for one of these.


I too have never had to run FF as root - until today :(

And yes, a bug report is in order.

Now, just to get FF completely uninstalled and to try again :)

---

### Post by Sidewinder1 on 2009-08-02
This is just a WAG (wild a$$ed guess) on my part but it sounds like the difference between running GUIS (like FF) with "sudo" instead of the correct way, with "gksudo".  Have a look at the following link:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

HTH,
Side

---

### Post by kg84 on 2009-08-02
> **Sidewinder1 said:**
> This is just a WAG (wild a$$ed guess) on my part but it sounds like the difference between running GUIS (like FF) with "sudo" instead of the correct way, with "gksudo".  Have a look at the following link:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

HTH,
Side

Thanks for that. I had not used gksudo, only sudo, in order to make my knackered FF work :P

I have managed to get rid of FF altogether plus everything else associated with it and have just completed a nice fresh install, so all is well.

Still, its damn odd how things went today after running Tiger.

---

### Post by Sidewinder1 on 2009-08-02
Glad to have been of assistance. :-)

---

