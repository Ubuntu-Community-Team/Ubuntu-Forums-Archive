---
title: "Will there be a Lucid 10.4 release for Ubuntu Studio?"
date: 2010-04-21
forum: Ubuntu Studio
---

### Post by jukingeo on 2010-04-21
Hello all,

Pretty much as the subject says:

Will there be an LTS Ubuntu Studio Lucid (10.4) release?  Will it release at the same time as regular Ubuntu Lucid?

Thanx,

Geo

---

### Post by cub on 2010-04-21
Yes. I have already tried out the Ubuntu Studio 10.04 BETA 2. The release schedule should be the same.

---

### Post by jukingeo on 2010-04-21
> **cub said:**
> Yes. I have already tried out the Ubuntu Studio 10.04 BETA 2. The release schedule should be the same.

Will Lucid have Jack 2 and FFADO 2.0 on it preinstalled?  That was always a big pain for me on an installation of US in the past.  I stuck with Hardy 8.04 because of LTS, but 8.04 has issues with Jack out of the box and it is set up for the older FreeBob for firewire support. 

Basically what I am hoping for with Lucid is that all I have to do to set up Ubuntu Studio on a computer is to install it on a system and then plug my firewire audio device in and go.  Basically a 'canned' system.

I am also hoping there will be improved video editing support in the new Ubuntu Studio as well.  Keeping my fingers crossed there.

Anyway, thanx for the heads up.

Geo

---

### Post by philip5 on 2010-04-21
> **jukingeo said:**
> Will Lucid have Jack 2 and FFADO 2.0 on it preinstalled?  That was always a big pain for me on an installation of US in the past.

Looks like Lucid will come with Jack 0.118+svn3796 and ffado 2.0 so no jack 2 out of the box.

---

### Post by jukingeo on 2010-04-22
> **philip5 said:**
> Looks like Lucid will come with Jack 0.118+svn3796 and ffado 2.0 so no jack 2 out of the box.

Why aren't they going with Jack2? Isn't that the latest iteration of Jack?

---

### Post by trulan on 2010-04-22
Not really.  Jack2 (jackdmp) is a different implementation of the same concept.  I've used both and I personally prefer Jack1 (jackd) for firewire.  The main 'benefit' for using Jack2 is multi-processor support, and I found I had to set the firewire process to non-threaded (via RTIRQ) to get any kind of stability on Jack2.  In a nutshell, using ffado, Jack2 sees a lot more xruns than jack1, but they are much smaller when they occur.  That's been my experience.

---

### Post by jukingeo on 2010-04-23
> **trulan said:**
> Not really.  Jack2 (jackdmp) is a different implementation of the same concept.  I've used both and I personally prefer Jack1 (jackd) for firewire.  The main 'benefit' for using Jack2 is multi-processor support, and I found I had to set the firewire process to non-threaded (via RTIRQ) to get any kind of stability on Jack2.  In a nutshell, using ffado, Jack2 sees a lot more xruns than jack1, but they are much smaller when they occur.  That's been my experience.

Ahhhh, I see.  The person that recommended Jack2 to me probably thought I had a newer multi-core processor.   I am still on a Pentium 4 actually. 

So Jack2 isn't fully stable, huh?  I guess that could be the reason why it isn't implemented yet into an Ubuntu release.

Ok, well that clears that up.

Thanx,

Geo

---

### Post by trulan on 2010-04-24
I'm not going to say Jack 2 isn't fully stable.  And I also have a multi-core processor.  I just found it less solid than Jack1 when using firewire.  It may actually be better with Alsa, I can't say.  But it's definitely a parallel version rather than a newer version.

Jack2 has been, and will be, readily available in several good PPA's, so it's pretty easy to upgrade to it if you want.  It's a little trickier, but doable nontheless, to roll back to Jack1 if you decide you don't like Jack2.

---

### Post by jukingeo on 2010-05-01
Hello all, 

I just been to the Ubuntu Studio website and they already have a Lucid version posted to download.  So naturally I did so.

Now I never did an update over an existing setup before.  So how do I install Ubuntu Studio Lucid over Hardy WITHOUT loosing data.   I am working on a project right now and can't afford to have everything wiped on an upgrade.

Thank You,

Geo

---

### Post by cub on 2010-05-01
> **jukingeo said:**
> Hello all, 

I just been to the Ubuntu Studio website and they already have a Lucid version posted to download.  So naturally I did so.

Now I never did an update over an existing setup before.  So how do I install Ubuntu Studio Lucid over Hardy WITHOUT loosing data.   I am working on a project right now and can't afford to have everything wiped on an upgrade.
Do you have your data/documents on /home which is on a separate partition? In that case, just make sure you don't change file system or format that partition. I've upgraded several times and my /home has been safe.
But if it's all on one big / partition I'm not so sure. In any case do backups to an external disk before the upgrade. Which you might do already..or if not should consider if it's important data..:)

---

### Post by mango42 on 2010-05-02
> **jukingeo said:**
> I am working on a project right now and can't afford to have everything wiped on an upgrade.

OUCH! Is this a bread and butter project or just personal? If the former, I would strongly advise putting any system upgrade in abeyance until finished. Even allowing updates can pork things (eg: Hydrogen files that won't load after non-PPA updates)

Also, Clonezilla and/or PartImage are your true friends in such a situation, IMO:-

[http://clonezilla.org/](http://clonezilla.org/)

and

[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

---

### Post by jukingeo on 2010-05-02
> **cub said:**
> Do you have your data/documents on /home which is on a separate partition? In that case, just make sure you don't change file system or format that partition. I've upgraded several times and my /home has been safe.
But if it's all on one big / partition I'm not so sure. In any case do backups to an external disk before the upgrade. Which you might do already..or if not should consider if it's important data..:)

Yes, I do have the /home partition and I have done a reinstall before, but while my data was intact, all the programs were wiped and I had to reinstall all my programs.  So that is what I am trying to avoid.

> **mango42 said:**
> OUCH! Is this a bread and butter project or just personal? If the former, I would strongly advise putting any system upgrade in abeyance until finished. Even allowing updates can pork things (eg: Hydrogen files that won't load after non-PPA updates)

Also, Clonezilla and/or PartImage are your true friends in such a situation, IMO:-

[http://clonezilla.org/](http://clonezilla.org/)

and

[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

No, it isn't a bread and butter project, but it is more like...I just fixed Ubuntu Studio a few months ago via a reinstall and my programs were wiped, and I don't want to have to go and reinstall everything again...type of deal.

There are some video editing projects I am working on and I don't want my settings to be 'reset' that is all.

However, from what I been hearing, it seems that Lucid is going through it's 'buggy' phases and I probably will wait a bit until they work out most of the kinks.

Thanx,

Geo

---

