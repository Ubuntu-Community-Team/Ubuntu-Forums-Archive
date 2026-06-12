---
title: "Ubuntu Security Center"
date: 2008-09-04
forum: Ubuntu Brainstorm
---

### Post by plainhunt on 2008-09-04
I am a fairly new Ubuntu User, I think it would be good to have a Security Center built into Ubuntu. With an option to install additional Anti-Virus, Firewall etc. But generally it would be nice to see an application which basically tells you that the system is safe, the ports are closed etc. but in a nice clean graphic form.

Any Opinions?

---

### Post by Slug71 on 2008-09-04
Why would you want that when you dont have to worry about Viruses, Adware or Spyware? It is extremely rare with Linux that you would get affected by any of that. The only reason some people install an Anti-Virus on Linux is so that they don't accidentaly pass a virus on to a Windows user.

---

### Post by nolimit974 on 2008-09-04
sounds like you just came from using windows and liked it's security center.  We linux users don't have problems requiring those tools.  If it wasn't for windows those tools wouldn't even be needed.

---

### Post by jflaker on 2008-09-04
To infect your computer would take a bit of effort on your behalf.  Nothing will just RUN without you knowing.  

A general status window would not be all that bad as just a place to view the status of your IP ports and open connections.

If you want to suggest, go to [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

Think about what you would like to see and post it....

---

### Post by snake444 on 2008-09-06
if there were viruses in ubuntu they cant hurt your system because they will need premission to touch files that are not in your home folder
but another big problem is if virus want to delete your home folder , he doesnt need sudo premision to do that and sometimes your data is much more important than the system data :/

---

### Post by rossjman1 on 2008-09-06
Maybe a good idea in 10 years when Ubuntu actually might have these problems.

---

### Post by gnomeuser on 2008-09-07
> **Slug71 said:**
> Why would you want that when you dont have to worry about Viruses, Adware or Spyware? It is extremely rare with Linux that you would get affected by any of that. The only reason some people install an Anti-Virus on Linux is so that they don't accidentaly pass a virus on to a Windows user.

While we might not currently need a virus scanner at least running a OS without a default firewall is pure insanity, that is not to say we won't ever need that functionality though. Also investigating things like SELinux by default is a good idea from a security stance. Embracing a safe langauge such as C# would also make certain attacks go away entirely. There are also things like stack protection and other security tricks for unsafe langauges we could employ.

We still should never need a security center though, if security:

a) fails to do it's job by default
b) gets in the users way

we have failed. The focus of our implementation should be a state of being secure by default while retaining a usable OS for 99% of all people. 

For this to work we need automatic reporting of policy failures like apport does for crashes but gathering anonymous usage data is important to forming a policy that encapsulates our processes correctly while not breaking vital functionality. 

This will be a multi cycle effort to roll out, iteratively each cycle adding more restrictions. This will also fix bugs in programs as incorrect program behavior will be uncovered as we go. 

Now the good news is that Fedora has done this for years so it's much less painful now to do this kind of thing than it has been. Many bugs have been fixed, our security infrastructure is much nicer now than it has been before and our reference policies have been polished free of most errors. We can make a huge first step if we want, so that Ibex +1 will include many if these technologies.

There is one major thing we need before enabling a firewall and SELinux though, handling upnp securely. Without upnp the user will have to set up open ports manually and messing with NAT on their routers. An all together undesirable situation, not far from what we have today but we can improve this situation and add security at the same time. There are designs and ideas to handle this, but we lack an implementation - not all together undoable given determination and a 6 month cycle.

I would think the iterative cycle would look something like this:

Ibex +1:
Write and deploy (by default) reporting programs for SELinux AVC's. Enable firewall and SELinux is "permissive reporting only" mode during development cycle (disable for production).
Write upnp proxy + SELinux domain policy to handle this.

Ibex +2:
Enable the above by default in restrictive mode, fix bugs. Decide enabling in production release based on the recorded breakage.

This means by Ibex +3 what will be the next LTS release we could have an encapsulated desktop and a strong default policy. Meaning good security by default without restricting the users daily tasks.

One way to reach that goal is the work closely with other distributions to have standard programs and protocols not to mention a bazar for weeding out the policies. Fedora and openSUSE both have a long history of work in this area but we need more centralization and cooperation, getting Ubuntu to play in this area would be very valuable for all of Linux and a major boon for everybodies users as the technology gets rolled out by default. It would mean the top 3 distributions would all have good security by default, setting a good standard for the entire platform and making it a focus for developers to test against.

---

### Post by olskar on 2008-09-13
Check out this firewall gui for ufw, looks great

[http://gufw.tuxfamily.org/screenshots.html](http://gufw.tuxfamily.org/screenshots.html)

---

### Post by irrdev on 2008-09-16
Never had a single virus after running linux for several years. Windows, yes, requires a security center, but not Linux. Not only are there far fewer viruses out there for Linux, but Linux's security model is extremely good. The very worst that can happen when running as a normal user, is that your home directory is wiped clean. A better idea would be to include a simple backup utility with the LiveCD...

---

### Post by gnomeuser on 2008-09-16
> **irrdev said:**
> Never had a single virus after running linux for several years. Windows, yes, requires a security center, but not Linux. Not only are there far fewer viruses out there for Linux, but Linux's security model is extremely good. The very worst that can happen when running as a normal user, is that your home directory is wiped clean. A better idea would be to include a simple backup utility with the LiveCD...

.. just lose my homedir..

I have 700 gigs of data there, any kind of breach that makes that disappear will make me utter phrases most unfit for a gentleman (and trust me is just happened due to a hardware crash - luckily I had a recent backup so most of it is back).

What do people keep in their home dir. Personal documents, honeymoon pictures, music, source code projects, their adressbook, all their settings that makes the desktop theirs. Home movies of irreplaceable moments - e.g. imagine losing the video of your childs firststeps or your wedding (now imagine telling your spouse what happened..). 

You might say so take backups (great I now have 2 home brewed solutions that are likely to fail or be broken into), put it online.. well uploading 700 gigs of data to S3 will take what 6-12 months on your average internet connection and then there's the cost. 

Let us protect that data as best we can, you know.. just in case. 

There are two big fallacies in security:

1) Security is only for servers
2) It's no big deal to lose your home dir

1 is obvious, botnets are not made up of servers, they are breached desktops, there are millions of desktops and for this use these machines are easy targets with high pay off. Security applies to all machines. If not concerned for you, then think of the harm your machine might cause if breached to others as part of a botnet.

2 is also obvious, all data loss is unacceptable. We should prevent it where we can, this includes enabling security options by default.

The objection still stands as to a security center though, if it doesn't work by default we tend to lose. Configurability is important only for cases where the default secure mode fails, often a solution should we found in that policy instead of allowing the user to turn it off. It's a power user feature to tinker with the security settings, we should probably not directly encourage average users to do that, that is not to say we can't have good tools available to tweak it in relevant cases for those who know what they are doing.

(please note, not all of the above is intended to be a direct reply to the quoted post, I just feel the matter of security is important to get right and it illustrated a point to one of a few common cases of relative indifference towards security)

---

### Post by signifer123 on 2008-09-16
Anybody know of a write once filesystem?

So your files can't be deleted by any normal means, or by viruses.

---

### Post by Yannick Le Saint kyncani on 2008-09-16
> **signifer123 said:**
> Anybody know of a write once filesystem?

Hi signifer, well, that would be any filesystem mounted read-only, wouldn't it ?

---

### Post by signifer123 on 2008-09-16
> **Yannick Le Saint kyncani said:**
> Hi signifer, well, that would be any filesystem mounted read-only, wouldn't it ?

No but then you can't write to it, i'm thinking a filesystem that s basically a multisession CD/DVD. You can write to it, and read from it, but not overwrite or delete(well truly delete).

what else would it do other than knowing what ports are open, and maybe a wrapper around netstat. I don't even know of a linux virus scanner, that's open source.

---

### Post by Neon Lights on 2008-09-18
> **signifer123 said:**
> 
what else would it do other than knowing what ports are open, and maybe a wrapper around netstat. I don't even know of a linux virus scanner, that's open source.
I believe ClamAV is available in the repos. [: it's open source.

---

### Post by v.cecchetto on 2008-09-19
Take a look at this firewall GUI (fieryfilter):

[http://0pointer.de/lennart/projects/fieryfilter/](http://0pointer.de/lennart/projects/fieryfilter/)

Some screenshot:

[IMG]http://0pointer.de/lennart/projects/fieryfilter/screenshots/fieryfilter-0.2-connection.png[/IMG]

[IMG]http://0pointer.de/lennart/projects/fieryfilter/screenshots/fieryfilter-0.3-rules.png[/IMG]

[IMG]http://0pointer.de/lennart/projects/fieryfilter/screenshots/fieryfilter-0.2-log.png[/IMG]

From the author (README):

WARNING: This is a pre-alpha version, it will probably format your
harddisk. Consider it a "preview version".

Requirements:

    Linux 2.4 with Netfilter and ip_queue
    Gtk 2.2.1
    libipq
    Good knowledge of Netfilter, iptables and especially Linux

---

### Post by Ellipsis on 2008-09-20
I generally agree that Ubuntu does not currently need a major security utility for users. But I think many people are used to it in Windows and even though Linux is highly secure we want to seem MORE secure by for example following the suggestion of having some kind of enabled SELinux security enabled by the next LTS. Also some basic utility like the GUI for UFW should also be included in some sort of limited capacity.

Any system can be hacked when attacked by someone with enough time and motivation, sure what they lose might be less valuable but even that hack it going a little too far.

Someway of providing protection for the home folder is not a bad idea as long as it does not interfere with the rest of the system. The same principles should apply to the security center have it present but keep it "out of your face."

Again security here is a little redundant but if you want to truly look bulletproof you must raise the shields, Remember that competition a few months back where they pitted Windows vs. OSX vs. Ubuntu? I want Linux (and Ubuntu being it's representative) to win and prove EVERYTIME that it is the best. Moreover, when threats do arise we should be ready and not caught with our pants down as Microsoft has so many times.

---

### Post by cprofitt on 2008-09-20
> **nolimit974 said:**
> sounds like you just came from using windows and liked it's security center.  We linux users don't have problems requiring those tools.  If it wasn't for windows those tools wouldn't even be needed.

Hilarious statement.considering that the first virus was not written for Windows.

[link]("http://en.wikipedia.org/wiki/Timeline_of_notable_computer_viruses_and_worms#1970-1979")

---

### Post by smartboyathome on 2008-09-21
Though we've come a long way security wise since the 1970s. We may not be impenetrable, but we do have vastly better security than Windows, which for now gives us no need to worry about viruses. Maybe a few will pop up later, but I doubt there will be nearly as many as in Windows, and that they will last as long.

---

### Post by gnomeuser on 2008-09-21
> **smartboyathome said:**
> Though we've come a long way security wise since the 1970s. We may not be impenetrable, but we do have vastly better security than Windows, which for now gives us no need to worry about viruses. Maybe a few will pop up later, but I doubt there will be nearly as many as in Windows, and that they will last as long.

Which is why Windows XP SP2 and later have a default on firewall and all manners of stack protection while Ubuntu has.. none (well not technically true, there propolice stack protection is turned on in gcc by default now but I think a number of packages still disable it).

Linux as a whole might in certain areas have a better design for security but it is not as you claim vastly better. Even if we were, using Windows as the measuring stick for security is a bad idea - that's like saying, I don't smell like dog excrements, I smell like dog excrements with a touch of perfume which surely is vastly superior.

Even a security minded distributions like Fedora, which has active and proactive security enabled by default recently got compromised (though not seriously). Surely if a distro is still able to be attacked succesfully when it truly cares about security, Ubuntu which does not do all what Fedora does, is a sitting duck - no matter if it's better than Windows, it's still not good enough, nobody really is but at least Ubuntu has the option of riding on the work done by others to add tested and proven security enhancements. 

We need to do much better to claim good security be default.

---

### Post by Ellipsis on 2008-09-21
> **gnomeuser said:**
> Which is why Windows XP SP2 and later have a default on firewall and all manners of stack protection while Ubuntu has.. none (well not technically true, there propolice stack protection is turned on in gcc by default now but I think a number of packages still disable it).

Linux as a whole might in certain areas have a better design for security but it is not as you claim vastly better. Even if we were, using Windows as the measuring stick for security is a bad idea - that's like saying, I don't smell like dog excrements, I smell like dog excrements with a touch of perfume which surely is vastly superior.

Even a security minded distributions like Fedora, which has active and proactive security enabled by default recently got compromised (though not seriously). Surely if a distro is still able to be attacked succesfully when it truly cares about security, Ubuntu which does not do all what Fedora does, is a sitting duck - no matter if it's better than Windows, it's still not good enough, nobody really is but at least Ubuntu has the option of riding on the work done by others to add tested and proven security enhancements. 

We need to do much better to claim good security be default.

I think we got to start early before we see any threats so that developers get used to working with security features in the bigger distributions.

But it would also be important to enable some kind of security menu so that new/inexperienced users do not try to further enhance their security through other means and end up compromising it or worse messing up their system.

---

