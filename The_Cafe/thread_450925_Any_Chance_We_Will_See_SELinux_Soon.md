---
title: "Any Chance We Will See SELinux Soon?"
date: 2007-05-21
forum: The Cafe
---

### Post by jsmidt on 2007-05-21
Any chance SELinux will be default soon?  If so how far away do you think it would be?

---

### Post by Vorian on 2007-05-21
You mean this [SElinux?]("http://www.nsa.gov/selinux/code/download-stable.cfm")

---

### Post by jsmidt on 2007-05-21
Yes.

---

### Post by kerry_s on 2007-05-21
Yeah right, like we all want a back door into are systems.

Open synaptic and do a search, make sure you have all your repos on.

---

### Post by troymcdavis on 2007-05-21
> **kerry_s said:**
> Yeah right, like we all want a back door into are systems.

WHAT? I CAN'T HEAR YOU OVER **YOUR TINFOIL HAT**.

No one would notice if these open source modules had any back doors, right?

---

### Post by Adamant1988 on 2007-05-21
The official word is 'we'll get it when Debian starts doing it'.  Basically Ubuntu doesn't have the developer power to make that happen, so they're going to let Debian do it.

---

### Post by jsmidt on 2007-05-21
> **Adamant1988 said:**
>   Basically Ubuntu doesn't have the developer power to make that happen, so they're going to let Debian do it.

What about SElinux makes it so hard for Ubuntu to maintain?  If Ubuntu already has it what prevents it from being turned on by default?

---

### Post by Adamant1988 on 2007-05-21
> **jsmidt said:**
> What about SElinux makes it so hard for Ubuntu to maintain?  If Ubuntu already has it what prevents it from being turned on by default?

I'm not sure, it has something to do with how it integrates into the kernel or some such, I really didn't speak with the devs at length.  But I did as in #ubuntu-devel and the answer I got was "After Debian gets it".

---

### Post by kerry_s on 2007-05-21
> **troymcdavis said:**
> WHAT? I CAN'T HEAR YOU OVER **YOUR TINFOIL HAT**.

No one would notice if these open source modules had any back doors, right?

It's a joke, some time back they tried to sneak a backdoor into the selinux, but it was discovered. Fun reading-> [http://www.google.com/search?client=opera&rls=en&q=nsa+backdoors+selinux&sourceid=opera&ie=utf-8&oe=utf-8](http://www.google.com/search?client=opera&rls=en&q=nsa+backdoors+selinux&sourceid=opera&ie=utf-8&oe=utf-8)

---

### Post by igknighted on 2007-05-22
> **jsmidt said:**
> Any chance SELinux will be default soon?  If so how far away do you think it would be?

I really really hope not.  I use Fedora quite faithfully, but the very first thing I do is disable SELinux.  It is nothing but a pita for desktop users.  If I ran a big server I might think differently, however.  So maybe an SELinux option for the server install, but thats it.

---

### Post by ice60 on 2007-05-22
i think it's in debian now, but it's disabled by default. i just did a search for it so you can read about it there if you want.
[http://wiki.debian.org/SELinux](http://wiki.debian.org/SELinux)

generally linux desktop users aren't interested in security tools like this. i searched the forums for SELinux the other day and it looks like about 2 people are using it lol

---

### Post by hanzomon4 on 2007-05-22
It's already compiled into ubuntu debs but it has no default policy.

---

### Post by Pobega on 2007-05-22
> **Adamant1988 said:**
> The official word is 'we'll get it when Debian starts doing it'.  Basically Ubuntu doesn't have the developer power to make that happen, so they're going to let Debian do it.

Debian won't be adding SELinux to it's distribution by default as far as I know, and I'm not even sure how interested in it (If they are **at all**) they are. So the Ubuntu developers are most likely on thier own for this one.

---

### Post by Adamant1988 on 2007-05-22
> **Pobega said:**
> Debian won't be adding SELinux to it's distribution by default as far as I know, and I'm not even sure how interested in it (If they are **at all**) they are. So the Ubuntu developers are most likely on thier own for this one.

It is there (the packages are installed) making it function is the hard part.

---

### Post by brim4brim on 2007-05-22
Don't want it installed especially not by default.

---

### Post by gnomeuser on 2007-05-22
> **kerry_s said:**
> It's a joke, some time back they tried to sneak a backdoor into the selinux, but it was discovered. Fun reading-> [http://www.google.com/search?client=opera&rls=en&q=nsa+backdoors+selinux&sourceid=opera&ie=utf-8&oe=utf-8](http://www.google.com/search?client=opera&rls=en&q=nsa+backdoors+selinux&sourceid=opera&ie=utf-8&oe=utf-8)

No they didn't, when you accuse people of something like that you need to provide evidence.. all you did was present a Google search with all the usual SELinux tinfoil hat non-sense.

When SELinux was first presented it was basically rewritten from scratch to forfill the requirements for inclusion into the kernel tree, the code is heavily audited by both members of the NSA (these people do more than just spying, they also to security research for the benefit of protecting American communication infrastructure.. SELinux is the result of such work) and several engineers amongst others Dan Walsh at Red Hat and many others.

There is no SELinux backdoor, there never was and there never will be. Please remove tinfoil hat and prove me wrong.

---

### Post by gnomeuser on 2007-05-22
> **ice60 said:**
> 
generally linux desktop users aren't interested in security tools like this. i searched the forums for SELinux the other day and it looks like about 2 people are using it lol

But they are interested in ensuring their bank accounts are safe and they are interested in avoiding virii spy/malware. Safe browsing etc. is also a major requirement for certain deployments and a major security boon for your average user if done right (read: SELinux). There might not be many users screaming for security but they do want it and it is something we sell Linux on, currently our proactive security in the deployed LTS release are worse than Windows XP SP2 (and Feisty isn't much better though it does do canary insertion).

If we want to continue to offer users a superior platform we cannot ignore security and we have to stop this fallacy of claiming security is only required for servers. It's not, the biggest problems online are botnets used for DDoS'ing and spamming, these are desktop machines since they are so easy to break into, deploying technology proactively to ensure Linux will be protected as best as possible will stop this before it becomes a problem.

We need to not suck as badly as Windows and OS X. Fixing problems after the fact is not a good solution, we cannot rely on users continually keeping their systems up to date. We have technology to stop close to 50% of all security flaws without a patch.. it's well tested and has low impact.. to not deploy it would be a serious blunder.

We need SELinux, we needed it for Dapper, it was promised for Hoary.. it's still not deployed. Ubuntu has still not learned the advantage of having good security, I fear we'll only learn after a major breach and our users can't afford that.

---

### Post by ice60 on 2007-05-22
gnomeuser, when i said "lol" that was aimed at linux users and not security software. i love computer security. :)

---

### Post by jsmidt on 2007-05-22
I notice some of you think it would be bad for desktop users if SElinux was turned on by default.  Would you feel the same way about apparmor?  Did you know using apparmor is one off the [topics at UbuntuLive]("http://www.ubuntulive.com/cs/ubuntu/view/e_sess/13497")?

---

### Post by Andrewie on 2007-05-22
> **jsmidt said:**
> I notice some of you think it would be bad for desktop users if SElinux was turned on by default.  Would you feel the same way about apparmor?  Did you know using apparmor is one off the [topics at UbuntuLive]("http://www.ubuntulive.com/cs/ubuntu/view/e_sess/13497")?


Apparmor and SElinux and pretty much the same thing, and personally I have nothing against them. When they first came out they we're very annoying but now they aren't much of a problem.

---

### Post by ice60 on 2007-05-22
i use suse as my main distro, partly because it had just come out when i got my new computer plus other distros didn't work as well with my hardware. but, i dual-boot with ubuntu now, and use suse far more because it uses apparmor.

if i'm using irssi, or some other network based program, and there's a 0-day i know i'm safe with suse and apparmor :D with ubuntu i'd be pwnd :eek:

---

### Post by Andrewie on 2007-05-22
> **ice60 said:**
> i use suse as my main distro, partly because it had just come out when i got my new computer plus other distros didn't work as well with my hardware. but, i dual-boot with ubuntu now, and use suse far more because it uses apparmor.

if i'm using irssi, or some other network based program, and there's a 0-day i know i'm safe with suse and apparmor :D with ubuntu i'd be pwnd :eek:

does OpenSuse enable apparmor by default? 10.2 user

---

### Post by brim4brim on 2007-05-22
> **jsmidt said:**
> I notice some of you think it would be bad for desktop users if SElinux was turned on by default.  Would you feel the same way about apparmor?  Did you know using apparmor is one off the [topics at UbuntuLive]("http://www.ubuntulive.com/cs/ubuntu/view/e_sess/13497")?

My reservation would be the NSA involvement in SELinux given I'm not American, I don't want it in my OS.

---

### Post by mips on 2007-05-22
> **kerry_s said:**
> Yeah right, like we all want a back door into are systems.


Here we go again. We have been down this road before.

It's open source, the community has full access to the code. Anyone that wants to can verify the code and do integrity checks on it.

[http://ubuntuforums.org/showthread.php?t=338133](http://ubuntuforums.org/showthread.php?t=338133)
[http://ubuntuforums.org/showthread.php?t=328393](http://ubuntuforums.org/showthread.php?t=328393)

I have no trust in the US government and have an absolute loathing for it. Despite that I see nothing wrong with SELinux.

---

### Post by ice60 on 2007-05-22
> **Andrewie said:**
> does OpenSuse enable apparmor by default? 10.2 user
yeap, it's been in suse for a while now. Novell develops it. it comes enabled with about 10 profiles, but there are alot more already made that you can drop in to the apparmor directory.

i really wish everyone would have an interest in SELinux and/or Apparmor, they aren't easy to setup, but if enough people posted about them there'd be lots of HowTos. i had to work it out myself. :-({|=

as it is linux is fairly safe, but with application firewalls, or HIPS, or whatever you want to call them, linux would be almost 100% safe (although doing stupid things will always be risky)

---

### Post by G Morgan on 2007-05-22
> **brim4brim said:**
> My reservation would be the NSA involvement in SELinux given I'm not American, I don't want it in my OS.

So you do not trust the clever people involved in the kernel team. The NSA can do what they like, we have source and that source is vetted. Trust me, SELinux is checked more strictly than other stuff given it's roots.

---

### Post by jsmidt on 2007-05-22
> **ice60 said:**
>  SELinux and/or Apparmor, they aren't easy to setup, but if enough people posted about them there'd be lots of HowTos. i had to work it out myself. :-({|=

How much easier is apparmor to set up thenSElinux?  Is there a good HowTo for Ubuntu?  By the way, thanks for all the helpful comments.

---

### Post by Rhox on 2007-05-22
Considering that the vast majority of people won't be able to configure it and that there is no point probably like 10 years.

---

### Post by Andrewie on 2007-05-22
> **ice60 said:**
> yeap, it's been in suse for a while now. Novell develops it. it comes enabled with about 10 profiles, but there are alot more already made that you can drop in to the apparmor directory.

i really wish everyone would have an interest in SELinux and/or Apparmor, they aren't easy to setup, but if enough people posted about them there'd be lots of HowTos. i had to work it out myself. :-({|=

as it is linux is fairly safe, but with application firewalls, or HIPS, or whatever you want to call them, linux would be almost 100% safe (although doing stupid things will always be risky)

I had no idea, I've been using apparmor all this time. You learn something new everyday

---

### Post by gnomeuser on 2007-05-22
> **jsmidt said:**
> I notice some of you think it would be bad for desktop users if SElinux was turned on by default.  Would you feel the same way about apparmor?  Did you know using apparmor is one off the [topics at UbuntuLive]("http://www.ubuntulive.com/cs/ubuntu/view/e_sess/13497")?

AppArmor has the following problems:

a) Autogenerated profiles (which aren't ensured to work between application versions)
b) Path based profiles (this leads to.. interesting security problems)
c) Not in the kernel currently and with little prospect of getting there (meaning we carry a patched kernel forever potentially)

SELinux is in the kernel, it has the right design, tremendous vendor support and a very well designed reference policy developed upstream (NSA alongside Fedora and Red Hat). I feel that AppArmor would be a terrible mistake to deploy, it carries risks both in compromises of security and maintainability.

---

### Post by jsmidt on 2007-05-23
> **gnomeuser said:**
> 

SELinux is in the kernel, it has the right design, tremendous vendor support and a very well designed reference policy developed upstream .... I feel that AppArmor would be a terrible mistake to deploy....

Can anybody with experience running both and SElinux Machine and one with apparmor please comment on how much harder an SElinux machine is to manage.  Are we talking just a little bit harder or allot.

---

### Post by gnomeuser on 2007-05-23
> **jsmidt said:**
> Can anybody with experience running both and SElinux Machine and one with apparmor please comment on how much harder an SElinux machine is to manage.  Are we talking just a little bit harder or allot.

Since I've used both:

As a user, SELinux and AppArmor should be zero work. If there's maintance work required we lose - luckily both systems in that regard are non-interactive. When it comes to editing policies, AppArmor is in a format near to what would be considered shell script and it has capabilities to generate a profile from looking at logging output. SELinux is basically an expressive scripting language, it's a lot harder to get into but there are troubleshooter apps you can run which will tell you what a given warning means and encourage you to file it and point you to ways of allowing it.

AppArmor from the stance of Ubuntu the distro means constantly having to patch the kernel, this means added insecurity (patching can go wrong, cause slowdowns in deployment of new security updates etc.) and added cost of development since we have to add this feature everytime instead of just using the already included SELinux. 

SELinux is making headway on usability but ultimately as a single user, the policy you need for a system is shipped from your vendor (Ubuntu in this case), it's open for you to read to avoid trust issues and if tested right during the development cycle and before issuing stable updates should cause no problems. The same thing is true for AppArmor, the default policy should suffice.

I'll continue to make a passionate plea for SELinux, it's getting good vendor backup, upstreams are picking it for security deployment (X.org e.g. is getting a SELinux module to do fun things) and so long as you don't need to alter policies (and as a user you really shouldn't) it is as easy to use as AppArmor. We are still talking going from something Mom needs to read an O'Reilly book hard to do, to Mom needs to learn bash and needs to know what every question the generator asks her means kinda hard to do - security of this kind is not going to be easy to alter for everybody but it will be zero work to benefit from it as a user. Policy making is not easy, it's hard - but it is open and at least in the case of SELinux well documented (I haven't looked that hard at AppArmors documentation)

Some people would say SELinux/AppAmor hinders them, and they are right policy based security deployments does put limits certain things, for security reasons or to avoid bugs (memory managment is a big problem here). Reporting such issues should be made as easy as possible to get the solved instead of encouraging disabling security - SELinux does that with the troubleshooter (but it needs extending to hook up to the distro bugtracker).

Regardless of the solution, so long as users can report a policy problem with a single click, it's likely not going to be a bigger problem and those of use nuts enough to want to edit the policies have to do a little bit of reading.. just like if we want to code anything else.

---

### Post by jsmidt on 2007-05-23
So if the devs are saying "When Debian gets it," what is the main reason Debian can't just port it from Fedora?  If the policies are the problem are Fedora's not that great?  Why not use theirs?

---

### Post by FyreBrand on 2007-05-23
> **jsmidt said:**
> So if the devs are saying "When Debian gets it," what is the main reason Debian can't just port it from Fedora?  If the policies are the problem are Fedora's not that great?  Why not use theirs?Because Fedora does things their own way.  It's almost like using an entirely different OS for some installs (try getting a LAMP stack running in Debian and then Fedora).

Gnomeuser:  I think SELinux is a good idea, but it's learning curve is so steep it's nearly insane.  It's just not usable yet, in it's current form, for most users, even the savvy.  With every version of Fedora it gets better, but it's still a huge pita.

---

### Post by jiminycricket on 2007-05-23
I read on Planet Debian that a Debian Developer is working on better SELinux support.

I agree that AppArmor has its own set of problems that SELinux avoids.

If anyone wants to see how SELinux works, the soon to be released Fedora 7 will have it by default.

---

### Post by gnomeuser on 2007-05-23
> **jiminycricket said:**
> I read on Planet Debian that a Debian Developer is working on better SELinux support.

I agree that AppArmor has its own set of problems that SELinux avoids.

If anyone wants to see how SELinux works, the soon to be released Fedora 7 will have it by default.

SELinux has been default since the Fedora Core 3 release, install any recent version of Fedora

The policy being the upstream default (regardless of the FUD spread above) should be close to directly portable to Ubuntu.

---

### Post by gnomeuser on 2007-05-23
> **FyreBrand said:**
> Because Fedora does things their own way.  It's almost like using an entirely different OS for some installs (try getting a LAMP stack running in Debian and then Fedora).

Gnomeuser:  I think SELinux is a good idea, but it's learning curve is so steep it's nearly insane.  It's just not usable yet, in it's current form, for most users, even the savvy.  With every version of Fedora it gets better, but it's still a huge pita.

How is enabled by default hard for users... sure if they want to alter policy themselves it's hard but that's like saying we shouldn't include programs written in C since it's antiquated and hard. Most users just benefit from the default policy, if that policy impedes the default install in any way that's not intended it's a bug and should be filed.

Can it be better, sure.. untill a computer is one button labelled "do what I want" or it reads your mind it's always possible to improve a situation. Given what we get from an SELinux deployment I think it is absolutely worth it... we are after all talking a proven record of stopping NEARLY HALF of all security issues without a patch.

Also Fedora does not reinvent the wheel as you claim, we stick to upstream as much as possible. But that has no baring on the debate at hand.

---

### Post by jsmidt on 2007-05-24
> **gnomeuser said:**
> 

Can it be better, sure.. untill a computer is one button labelled "do what I want" or it reads your mind it's always possible to improve a situation. 

I'm all for a computer that can read my mind.

---

### Post by Polygon on 2007-05-24
i researched this on wikipedia, correct me am i wrong, but basically does this just add like another set of permissions to the existing user/group/owner permissions, and adds a "access" level (as in standard, confidential, etc)?

---

### Post by gnomeuser on 2007-05-24
> **Polygon said:**
> i researched this on wikipedia, correct me am i wrong, but basically does this just add like another set of permissions to the existing user/group/owner permissions, and adds a "access" level (as in standard, confidential, etc)?

It's a lot more involved than that, SELinux today let's you label network packages, it has an extremely involved domain context concept.. it's allows you a very granular level of control on nearly everything in your system, who can access what in which contexts. This allows us easily to define policies for something like ssh to ensure that if it's broken into, it cannot do anything outside it's context. Think of it like putting a very restrictive firewall around every application, it does suspect memory allocation and it's denied, it attempts to access files outside the context limitations and it's denied. You get a very nice way to restrict applications and ensure that they are harder to break into and if they are broken into it is restricted to that app (so what if Apache is compromised, it can't poke outside and elevate a remote exploit to say a remote root to install a rootkit, it can't install a spamrelay, it can't alter your firewall settings etc.).

The Fedora wiki has some good documentation and presentations available on SELinux and how it works. What users generally like about this kind of deployment is even if something bad happens.. no spyware, no access to their bank records, etc. With SELinux we have the chance to obsolete spyware before it becomes a problem (and trust me, it will become a problem the more widely used Linux becomes.. you ship preinstalled on Dell PCs now for consumers.. how long till we get some really bad exploits used against desktop software?)

---

