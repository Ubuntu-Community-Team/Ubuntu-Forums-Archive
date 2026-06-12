---
title: "Uninstall Evolution"
date: 2007-02-05
forum: Repositories &amp; Backports
---

### Post by code-breaker on 2007-02-05
I have edgy. I use Thunderbird so I would like to uninstall evolution. But when I select it for removal in synaptic, a list of other packages comes up that will be uninstalled as well, including ubuntu-desktop. 

This has happened to me once before, where I tried to uninstall some application and ubuntu-desktop was selected for removal as well. I thought at the time, well, there's no way that means the actual ubuntu desktop. But yes, it was. I lost everything. Luckily it was a new install (which is why I wasn't more cautious). 

So, what can I do to uninstall evolution?

---

### Post by bapoumba on 2007-02-05
Hello,
ubuntu-desktop is a meta-package, that ties up whole packages of a release via dependencies. That said, if you remove just one of these packages (evolution), dependencies are broken and ubuntu-desktop gets removed. 
By itself, ubuntu-desktop can safely be removed, but this can be a problem on upgrades for ex, and on dist-upgrades. What happened to you, was probably because of other packages that were removed at the same time.

So, if you are not running low on space, just keep evolution, and keep ubuntu-desktop. Just remove evolution from the menu, if you wish.

---

### Post by miaviator278 on 2007-02-14
You could run for the senate with an answer like that.   

There is a way to either modify the ubuntu desktop package or create a script to make a fake evolution package,   i have the same issue, and will be getting rid of evolution this week.

I understand that this also isn't an answer, but i am saying don't give up and "just keep evolution".

---

### Post by bapoumba on 2007-02-14
@ miaviator278: yes, I know this is not much of an answer :/
You may me interested in checking that thread out ;)
[http://www.mail-archive.com/ubuntu-devel-discuss@lists.ubuntu.com/msg00090.html]("http://www.mail-archive.com/ubuntu-devel-discuss@lists.ubuntu.com/msg00090.html")

---

### Post by Ian Clark on 2008-02-28
My Evolution is corrupted to the limit.  Every time I open it, it gets stuck on "formatting" (for the gmail account), then gives me the option to wait or force quit.  It even crashes my computer if I start it up.  Wow I wish I could uninstall this junk.

<revision>
That was related to a conflict with a mousegestures add-on in FF.  Evolution is up and going now.

---

### Post by redDEADresolve on 2009-03-07
> **Ian Clark said:**
> My Evolution is corrupted to the limit.  Every time I open it, it gets stuck on "formatting" (for the gmail account), then gives me the option to wait or force quit.  It even crashes my computer if I start it up.  Wow I wish I could uninstall this junk.

<revision>
That was related to a conflict with a mousegestures add-on in FF.  Evolution is up and going now.

Try deleting the .evolution folder in your home directory. This will eliminate the gmail format loading.

---

### Post by Ian Clark on 2009-03-08
Tried that, but when hitting send/receive to get into my gmail box, it hangs for five minutes on "fetching summary information for new messages in INBOX", then hangs forever (gets stuck) on "filtering new messages".  Evolution at this point is totally useless.  Furthermore, I check my home folder, and the .evolution folder has been recreated.

---

### Post by kidux on 2009-03-08
> **Ian Clark said:**
> Tried that, but when hitting send/receive to get into my gmail box, it hangs for five minutes on "fetching summary information for new messages in INBOX", then hangs forever (gets stuck) on "filtering new messages".  Evolution at this point is totally useless.  Furthermore, I check my home folder, and the .evolution folder has been recreated.
Every time you open Evolution it will re-create that folder if it's not there.

---

### Post by m-p{3} on 2009-03-09
It's still redundant to have two mail clients on the same system, especially if you don't plan to use both.

I personally prefer Thunderbird to Evolution.

---

### Post by Ian Clark on 2009-03-11
> **m-p{3} said:**
> It's still redundant to have two mail clients on the same system, especially if you don't plan to use both.

I personally prefer Thunderbird to Evolution.

Perhaps it has something to do with China.  I tried Thunderbird as well, and getting the mail times out with that, too (while going to the gmail website gets me in very quickly).  I know there are webcop issues here, and previously I couldn't get into Gmail from my home computer - even on the official website, though it was fast on my work computer.  Hmmm.

---

### Post by Ottoko on 2009-06-16
I think I found a way to "disable" evolution

```
sudo apt-get remove evolution
```Edit apt.conf (you need to create one if it doesn't exist) 

```
sudo nano /etc/apt/apt.conf
```Add evolution to ignore list

```
// Completely ignore the following packages (not regexp)
// Ignore { };
Ignore { "evolution"; };
// Do not try to update the following packages
//Hold {
//"rh-postgres*";
//"XFree86-Xvfb*";
//MySQL*};           
```I'm not sure if this works, but I will found out at next update and post here :)

---

### Post by Ian Clark on 2009-06-17
Yo, Ottoko, if that works tell us.  I can't wait.

---

### Post by frederik.nnaji on 2009-06-23
this is really a pain in the rear!
not even the standard email client offers proper functionality.. that is a must-have!
i recommend ubuntu to so many people, maybe i should wait with that, until its integrated emailclient starts working out of the box..

this said, i think it is important to ask what client you would recommend instead? really thunderbird?

is the google integration better there?
how about the system integration into gnome etc?

---

### Post by frederik.nnaji on 2009-06-23
okay i guess the solution will be for them to replace evolution with a proper integration of thunderbird, next to its brother in arms "Firefox"

Thunderbird 3 beta is running on my box with ubuntu karmic since 10min, and i can't stop liking it!

google integration is fabulous from the start, and i want to really remove the bulky evolution..
evolution is good work, and a good idea, but it has failed me too much to still be enjoyable.. unfortunately...
and fortunately Mozilla Thunderbird has never really managed to fail me :D

please do post your report about your experiences comparing Evolution and Thunderbird 3

---

### Post by qamelian on 2009-06-23
> **frederik.nnaji said:**
> okay i guess the solution will be for them to replace evolution with a proper integration of thunderbird, next to its brother in arms "Firefox"

Thunderbird 3 beta is running on my box with ubuntu karmic since 10min, and i can't stop liking it!

google integration is fabulous from the start, and i want to really remove the bulky evolution..
evolution is good work, and a good idea, but it has failed me too much to still be enjoyable.. unfortunately...
and fortunately Mozilla Thunderbird has never really managed to fail me :D

please do post your report about your experiences comparing Evolution and Thunderbird 3
I'm at the opposite end of the spectrum. Evolution has never let me down, while Thunderbird was an end-user nightmare for me. Add to that the fact that I need the feature set in Evolution and Thunderbird (even with the lightning / sunbird add-in) doesn't measure up for me. 

That said, Evolution is probably overkill for most home users and isn't going to please everybody! :)

---

### Post by redDEADresolve on 2009-06-23
both are awesome email clients

---

### Post by frederik.nnaji on 2009-06-23
> **qamelian said:**
> I'm at the opposite end of the spectrum. Evolution has never let me down, while Thunderbird was an end-user nightmare for me. Add to that the fact that I need the feature set in Evolution and Thunderbird (even with the lightning / sunbird add-in) doesn't measure up for me. 

That said, Evolution is probably overkill for most home users and isn't going to please everybody! :)

sounds reasonable, i was also supprised by the richness in features of evolution...
you give me hope, that it might still be worthwhile to hope for bugfixes in evolution, since the contacts/calendar features are really good attempts at the matter of an integrated groupware/pim suite.

thanks a lot for your opinion, you have already changed mine for the better!

---

### Post by qamelian on 2009-06-23
> **redDEADresolve said:**
> both are awesome email clients
I need the PIM features offered by Evolution as well, though. Also, Thunderbird had a habit of corrupting my mailstore on a regular basis, in such a way that messages would replicate and I would end up with the same message appearing 3 or 4 times. I experienced way too much breakage on Tbird, both on Windows and Linux, to feel comfortable even recommending it to anyone now.

---

### Post by frederik.nnaji on 2009-06-23
> **qamelian said:**
> I need the PIM features offered by Evolution as well, though. Also, Thunderbird had a habit of corrupting my mailstore on a regular basis, in such a way that messages would replicate and I would end up with the same message appearing 3 or 4 times. I experienced way too much breakage on Tbird, both on Windows and Linux, to feel comfortable even recommending it to anyone now.

seems like one must go by main features and useability, not by the smaller bugs.. .. while picking a prog to stick with.

on the other hand, F/OSS has a habit of breaking its own code after a major release sometimes.. so patience seems to be a good method.

i will use both clients at my convenience, since IMAP is working equally well on both.

PIM is essential.. so evolution can't miss for now.. hope they'll fix the issues, then i'll stick with it.

---

### Post by frederik.nnaji on 2009-06-23
> **redDEADresolve said:**
> both are awesome email clients
i agree fully - for the email part.
for the PIM part i must unfortunately say, thunderbird doesn't cut it..

---

### Post by frederik.nnaji on 2009-06-23
> **Ian Clark said:**
> Yo, Ottoko, if that works tell us.  I can't wait.
u still sure u need to do this?

---

### Post by Ian Clark on 2009-06-24
> **frederik.nnaji said:**
> u still sure u need to do this?

Yeah I'd love to get rid of Evolution because it isn't functional (gmail in China gets totally stuck, of no use) and sometimes I'll click on an email function accidentally which will slow down or stop my whole system.  Better not to have it at all.  Tried thunderbird, too, but still stuck (just a bit better performance, but still of no use).

---

### Post by frederik.nnaji on 2009-06-24
very sorry to hear that about china..
we don't imagine such censoring over here.. Germany is very 21st century in this respect.

i personally find it hard to believe, that evolution alone won't leave the system simply...
i'll uninstall it testwise, to see if i can help you.
yet i am running karmic, and you obviously are running intrepid..
let's see

---

### Post by celian on 2010-01-10
I for one think this was a very valid subject, to have the freedom to add and remove any applications one desires, and not have any of them pushed upon the system, especially since there are no direct dependencies between evolution and the rest of Ubuntu. It's an email client, not a kernel module.

Just thinking back on the days when Internet Explorer was an obligatory part of windows, and could not be removed..

Luckily in 9.10 I seem to be able to remove evolution without breaking anything, so hooray!

---

### Post by frederik.nnaji on 2010-01-10
> **celian said:**
> I for one think this was a very valid subject, to have the freedom to add and remove any applications one desires, and not have any of them pushed upon the system, especially since there are no direct dependencies between evolution and the rest of Ubuntu. It's an email client, not a kernel module.

Just thinking back on the days when Internet Explorer was an obligatory part of windows, and could not be removed..

Luckily in 9.10 I seem to be able to remove evolution without breaking anything, so hooray!


yeah, such contribution is precisely what shapes the thinking that free software builds upon..
let's see what the devs decide upon for lucid..
i have nothing against evolution, but its notification policy is really something we need to work on soon..

---

### Post by cebif on 2010-01-30
Thats one of the things about linux in general that is disagreeable with me. Why do applications carry so many dependencies with other applications and parts of the OS function itself? Everything seems totally tied in a large web.
In other OS's that I have tried any application can be uninstalled without uninstalling everything else. In windows (used upt to XP) it warns you if lib files might still be needed by other applications and even lets you know when no other applications are depenent upon then, so you either do a partial uninstall or complete.
I think it might be possible to do a partial uninstall too with linux but it is more obscure commandline for it. 
I have also tried Beos/Haiku OS, and it is very basic to remove any application. There doesn't seem to be any dependencies with that.

---

### Post by IanW on 2010-02-10
If you really don't use Evolution at all, it can all be safely removed from your system except for "evolution-data-server-common", which is a dependancy of popup notifications etc.

---

### Post by Ian Clark on 2010-02-16
> **IanW said:**
> If you really don't use Evolution at all, it can all be safely removed from your system except for "evolution-data-server-common", which is a dependancy of popup notifications etc.

I simply selected "evolution" from synaptic and marked for complete removal. This removed evolution and some dependencies, and didn't include the evolution-data-server-common you mentioned. It works great! thanx

---

### Post by kamaji792 on 2010-02-17
[QUOTE=celian;8641178...

Luckily in 9.10 I seem to be able to remove evolution without breaking anything, so hooray![/QUOTE]

I have been having similar problems when un-installing evolution.  
The comment that it was part of the pseudo package gnome-desktop saved me from a second re-install to get my desktop back.

The warning I want to add is I think you can un-install evolution so long as you don't un-install **empath** as well.  I now realise that having removed empathy, when I removed empathy there were a lot of packages that got removed at the same time.

Additionally as people seem to be commenting on Evolution vs. Thunderbird.  I'm a Thunderbird/Lightning fan.  Probably because I use it on Windows.  I have tried evolution and found it refershingly easy to get running but I like lightning (TB extension) over the evolution PIM features.

Currently my only gripe with lightning is getting a network server running for it.  But that has more to do with me being a bear of small brain.

Ultimately I think there is enough space for both, though it would be nice to choose.

atb

---

