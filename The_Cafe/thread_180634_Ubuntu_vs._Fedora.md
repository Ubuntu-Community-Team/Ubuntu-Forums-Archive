---
title: "Ubuntu vs. Fedora"
date: 2006-05-22
forum: The Cafe
---

### Post by slavik on 2006-05-22
Upper management gave an OK on putting in some lookup terminals running linux.

Lower management decided that Fedora would be better because he knows it and claims that it is more secure and more stable. I understand that Ubuntu and Fedora are pretty much the top 2 linux distros (Ubuntu being on top).

Long story short, lower management wants cold hard facts why Ubuntu is better than Fedora.

Please remember that these will be lookup terminals with only firefox running.

---

### Post by DigitalDuality on 2006-05-22
I think the issue is a pretty moot point.  Linux OS's as a whole are all really secure.  As to stability, i find them to be equal in stability.  Fedora has a bit better hardware support on some things.  Ubuntu has better hardware support on others.

Secuina.com is a site that keeps track of vulnerability.  

Fedora Core 5 had 10 Secunia Advisories with 0% unpatched.  (Recently Released within the last 3 months)
for a more detailed report check this:
[http://secunia.com/product/8808/](http://secunia.com/product/8808/)

Ubuntu 5.10 Breezy had 51 Secunia Advisories, again with 0% unpatched.  (been out for about..7-8 months)
[http://secunia.com/product/6606/](http://secunia.com/product/6606/)

To me it's not really the number of advisories as it is the % of problems that go unpatched and the response time to repair the problem.  If you don't do your updates, you're asking for trouble.  Same goes for Windows and OS X.

You're also looking at another main difference that brings up questions of security.

Sudo (ubuntu) .... or Su (fedora)?  

Su, leaves you logged in as root as long as you like...while sudo changes your permissions for only a single command. Once that command completes your permissions revert back to the ones you had when you logged in. (in ubuntu, sudo actually lasts for a short period of time after the command is complete, but i think it's only maybe 5-10 minutes max).

Common sense to me would dictate that sudo creates better security practice and less room for error.

Ubuntu, unlike Fedora, also has the root account disabled by default, also a security plus.

But there's nothing regarding, su or sudo, or the root account you could pull off in the "other" OS.  This is just what comes out of the box.

Make of it what you will.

---

### Post by RAV TUX on 2006-05-22
ubuntu wins. The end.

---

### Post by Lord Illidan on 2006-05-22
I'd say Ubuntu. You are best off going to the fedora forums to ask for reasons to install Fedora.

I think a lot of fuss is made about their SELinux which is mostly unwarranted. Ubuntu is quite secure, and easier to use, imho.

---

### Post by slavik on 2006-05-22
the systems are p2 with 128MB ... I doubt either will be incompatible with the system

what I was also thinking was creating 2 scripts, one on start up and on logout that would log the person back in (or just in) and start Firefox ... I believe the firefox thing can be done with gnome-sessions.

I would also not want the logged in user to be able to do anything (maybe create a copy of the user or re-create the user every time the system boots?

---

### Post by ComplexNumber on 2006-05-22
fedora has rpm which is the chosen package management by the LSB. also, i would definitely agree with fedora being more stable. its also more attractive IMO. that orange is enough to scare any new user away. ubuntu has the advantage of having root account disabled, but i'm struggling to think of any other advantage.

---

### Post by kanem on 2006-05-22
[QUOTE=slavik]
Lower management decided that Fedora would be better because he knows it... [/QUOTE]
Is this the guy that's going to be maintaining it? I'd say that's most important thing given that everything else is just about equal. Why make someone work with something they're not comfortable with?

---

### Post by TrailerTrash on 2006-05-22
What about release support. The Dapper will have at least a 3 year desktop support, so what dose Fedora have. How long are their versions supported for...like updates and stuff?

---

### Post by Lovechild on 2006-05-22
Fedora is better for the given deployment, it's geared towards that kind of deployment and it has proactive security meassures in the OS which means you can sleep soundly rather than get up at 4 am to patch your network - belt and suspenders.

---

### Post by Lovechild on 2006-05-22
[QUOTE=TrailerTrash]What about release support. The Dapper will have at least a 3 year desktop support, so what dose Fedora have. How long are their versions supported for...like updates and stuff?[/QUOTE]

Every Fedora release has 2 years of support from Red Hat then it's passed on to the Fedora Legacy project for security maintance - so in theory you have support forever. Realistically 3-4 years is what's to be expected for each release as well as tested upgrade paths to newer versions.

---

### Post by Iandefor on 2006-05-22
[quote=ComplexNumber]fedora has rpm which is the chosen package management by the LSB.[/quote] Why?! It's crap compared to dpkg.

---

### Post by Lovechild on 2006-05-22
[QUOTE=Iandefor]Why?! It's crap compared to dpkg.[/QUOTE]

Let's take a class in argumentation shall we, when you make a claim the burdon of proof is on YOU.

Besides the LSB only recommends RPM it doesn't demand it, you can use DEB and be compliant.

---

### Post by Iandefor on 2006-05-22
[quote=Lovechild]Let's take a class in argumentation shall we, when you make a claim the burdon of proof is on YOU.

Besides the LSB only recommends RPM it doesn't demand it, you can use DEB and be compliant.[/quote] Meh, was just expressing an opinion. If I make an argument, I'm not going to bother couching it in relative terms like "crap". Would you like to hear why I dislike rpm?

---

### Post by Lucho on 2006-05-22
Which one? Definately Ubuntu if you have any brazilians working there-
Fedora translates as *stinky* in Portuguese.   :mrgreen: :mrgreen:

---

### Post by ComplexNumber on 2006-05-22
[quote=Iandefor]Why?! It's crap compared to dpkg.[/quote] ask the LSB that. they're not likely to be selecting it as a standard if its so "crap". i found dpkg a nightmare to use compared to rpm

---

### Post by Lovechild on 2006-05-22
[QUOTE=Iandefor]Meh, was just expressing an opinion. If I make an argument, I'm not going to bother couching it in relative terms like "crap". Would you like to hear why I dislike rpm?[/QUOTE]

I would like you to make informed posts, if you say "it's crap" that begs for explaination.

---

### Post by Iandefor on 2006-05-22
[quote=ComplexNumber]ask the LSB that. they're not likely to be selecting it as a standard if its so "crap". i found dpkg a nightmare to use compared to rpm[/quote] [quote=Iandefor]Meh, was just expressing an opinion.[/quote] 
Also: YMMV.

---

### Post by Iandefor on 2006-05-22
[quote=Lovechild]I would like you to make informed posts, if you say "it's crap" that begs for explaination.[/quote] The fact that rpm can only really handle dependencies, and not suggested/recommended packages is alone annoying enough. Synchronizing to rpm repositories takes forever, and the whole system feels hackneyed. That's why I don't like rpm.

Okay, so maybe I ought to have said why I don't like it right up front.

I'm entitled to base opinions off of personal experience, regardless of how much it may annoy you.

You may find that being less offensive will require less energy in the long run. If you have anything more to say to me, I'd appreciate it if you pm'ed it- I'd rather this thread remain on track.

---

### Post by slavik on 2006-05-22
thanks for giving me reasons ... none of them work for either ... the only thing that needs to run on these lookup terminals is X with firefox ... nothing else.

as far the user using it is concerned, he only has firefox running and that's it ... these machines (besides the input/output) are completely locked up so they don't even need USB support ... as for network trouble, this is on the college network which is firewalled.

Ubuntu also doesn't listen to any ports by default anyway and I was also thinking of creating an image and untarring the image everytime the user is logged in (which is at boot time) and the system will log the user out, replace the dir with the image and log the user in through a cronjob to be run at midnight ... how's that?

I was also thinking of disabling the execute flag on everything except firefox and needed X binaries.

Another thing is that I am going to work there for at most another year, but the lower management will be there for a while ... so I am thinking of letting fedora go on those boxes so I have less potential work to do :)

as for rpm vs. dpkg ... from someone who I asked about, rpm = dependency hell (although apt takes care of that for dpkg) ... but apt is more mature than yum ...

---

### Post by Virogenesis on 2006-05-22
Personaly I wouldn't use either as stock as ubuntu comes preloaded with gnome and with firefox running.... on 128mb... not good I would consider using xubuntu   .

---

### Post by ComplexNumber on 2006-05-22
> .. but apt is more mature than yum ... ....1) rpm has apt, 2) you're not forced to use yum, 3) dependency hell exists to the same degree on debian systems as rpm systems. also, one is not forced to use the command line.

---

### Post by slavik on 2006-05-22
[QUOTE=ComplexNumber]....1) rpm has apt, 2) you're not forced to use yum, 3) dependency hell exists to the same degree on debian systems as rpm systems. also, one is not forced to use the command line.[/QUOTE]
the other has synaptic which is only a GUI for apt :)

EDIT: @ virogenesis ... I am not looking to run beyond just gnome ... maybe not even gnome, just a plain X with a plain window manager and firefox ...

---

### Post by TrailerTrash on 2006-05-22
To be honest.....I would install CentOS. We have that on a server and 1 desktop at work and its more than rock solid. I think its more stable than Fedora. IMHO. :p

---

### Post by ComplexNumber on 2006-05-22
>  the other has synaptic which is only a GUI for apt both deb and rpm systems have synaptic. i've used it on suse and now fedora. [here]("http://rpm.pbone.net/index.php3/stat/4/idpl/2730831/com/synaptic-0.57.2-26.rhfc5.at.i386.rpm.html") it is for fedora 5.

---

