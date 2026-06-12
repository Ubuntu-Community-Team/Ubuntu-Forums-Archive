---
title: "If you were an office migrating from XP,  would you rather deploy Ubuntu LTS or RHEL?"
date: 2013-12-24
forum: Ubuntu, Linux and OS Chat
---

### Post by TeamRocket1233c on 2013-12-24
I've been putting some serious thought into this since last night, but although RHEL is the de-facto enterprise distro for its 10 year support subscription, Ubuntu LTS with paid support from Canonical does seem like a pretty good deal if you were an office migrating from XP and saw switching to Linux as a better option than upgrading to Win8.1.

I mean it would be easier to set up and manage than RHEL because of using APT, which is easier to manage than YUM. Also, it uses newer software than RHEL and doesn't go stale as quick due to upgrading every five years instead of every ten years.

As for support window, Ubuntu LTS' support window isn't as long as RHEL's, but five years is still a pretty good support window.

Yet on RHEL's side, Redhat has had more time in the field than Canonical, and has a longer support window, but it goes stale quicker than Ubuntu LTS, has older software, and is harder to manage. 

Also, I see RHEL as more of a server distro, while Ubuntu LTS is great for both the server and the desktop, so you'd be more able to use one distro both clientside and serverside with LTS than you would with RHEL.

Just my $0.02 on the Ubuntu LTS vs. RHEL debate, but I'd like to here you guys' input on this debate.

---

### Post by CharlesA on 2013-12-24
Depends on what your IT team has more experience with.

---

### Post by buzzingrobot on 2013-12-24
In the real world, cost would be the primary factor, assuming the needed applications can run on either OS. Comparisons of types of service, support levels, response time, etc., are also critical.

Given virtualization, the current age of RHEL is much less of an issue. And, most businesses run custom software anyway. If a business never needs to run anything but Office and other Windows apps, though, it should just move to Win7.

Issues such as Apt vs Yum are not at all important. They're just tools that do the same thing.  The admin(s) you'd hire would be expected to handle software management using whatever tool they preferred.

---

### Post by Hodevah on 2013-12-24
With respect to learning curves when migrating from one OS to another OS (compared to RHEL), in my opinion I would have to suggst Ubuntu.

---

### Post by miguelpires on 2013-12-25
HI,
It depends the needs, but, I prefer Ubuntu over Fedora/RHEL. The main problem that the business faces is the specific software, like:

- ERPs 
- Autocad
- Other specific programs.

For my company the main problem was the ERP. We save a lot of money, in IT costs, but some of our programs need the "windows" so we make VMS of the windows and use only for that part. 

About the payed support from Canonical, in my humble opinion is to expensive for little business. +1.000€ for one year! I think if they low the price or make the price intill the end off life of the product is more apellative for small business (+- the costs of a Windows licence but with support!!!! better sallyings I think)

Only my 2 cents.
Regards
Miguel

---

### Post by buzzingrobot on 2013-12-25
In a large organization, employee retraining costs (including downtime) and potential morale problems (people often see software changes as being forced on them for arbitrary reasons) need to be considered.  Retaining as much existing software as possible limits problems and expenses.  For many, that would argue for moving from XP to Win7, where existing XP apps would likely run well, greatly reducing training and other costs.

---

### Post by lykwydchykyn on 2013-12-27
If I'm a company wanting to deploy a Linux distro in my shop, I'm looking for a vendor that clearly wants to support this.  RH is clearly in business to support businesses that use RHEL.
I don't get this vibe from Canonical.  From what I can see Canonical is interested in getting OEM deals for mobile, or getting my cloud business, or getting some Amazon affiliate money from Joe user.  Even taking LTS into account, their technology stack is changing at breakneck pace.  If my goal is to deploy a stable, long-term OS solution for my company's desktops, I get no impression that Canonical is interested in meeting my needs.

---

### Post by tgalati4 on 2013-12-27
I would install Windows 8 on everything and then go work for a competitor.

---

### Post by deadflowr on 2013-12-27
> **tgalati4 said:**
> I would install Windows 8 on everything and then go work for a competitor.

Sabotage?:lolflag:

---

### Post by neu5eeCh on 2013-12-27
Okay, I know squat about these issues but...

I wonder if the DE doesn't come into play? Does it matter that RHEL is still using Gnome 2? Aren't the odds fairly strong that RHEL will, at some point, switch to Gnome Shell? Seems to me, given Gnome Shell's [overwhelmingly negative reception ]("http://www.zdnet.com/is-gnome-staring-into-the-abyss-7000001833/")(I think the linked article is still relevant?) that Unity would be a more stable and stronger choice (if the DE matters at all). Feel free to shoot me down. :popcorn:

---

### Post by buzzingrobot on 2013-12-27
> **VTPoet said:**
> 
I wonder if the DE doesn't come into play? Does it matter that RHEL is still using Gnome 2? 


In my experience, the DE matters less that you might think because many employees in many organizations never really use the DE. They'll spend almost all their time working with one or two applications, very often run full screen. My dentist office for example, used to use a Linux application platform for office management:  billing, appointments, ordering, staff scheduling, records, notes, etc.  Each function ran as a separate full screen activity.  Last year, the office switched to the same app platform running on Windows.  You have to look close to see the difference.

Employees handling routine traditional office tasks will, of course, see a variety of applications like mail, spreadsheet, etc.  

The biggest issue with employees is very often the hassle of learning new software. They don't want to do it.  Typically, from their point of view, the old software was working fine and they knew how to use it.  Then, here comes management foisting off something new on them for reasons that aren't made clear, putting them through the headache of learning to use it.  

>  Aren't the odds fairly strong that RHEL will, at some point, switch to Gnome Shell?
 
Red Hat has said RHEL 7 will use Gnome Shell with the Gnome fallback look. The Gnome team has officially adopted several extensions that provide that interface on Gnome Shell. That's reflected in the current RHEL 7 beta.  RH says they believe it will be the most familiar to current customers who actually do use the interface.

I've seen reports of usability studies with people with little, if any, Windows experience.  Those say the basic Gnome Shell interface was the easiest to learn.  Out of the box, Gnome Shell is very focused.  There's usually one way to do something.  That makes it easy to learn. (And annoys experienced users who want to do things another way.)

---

### Post by neu5eeCh on 2013-12-27
Thanks. That all makes sense.

Did you ever find out why your Dentist switched to Windows?

---

### Post by buzzingrobot on 2013-12-27
> **VTPoet said:**
> 

Did you ever find out why your Dentist switched to Windows?

They told me they were unhappy with the folks they used for support.

---

### Post by lykwydchykyn on 2013-12-28
> **buzzingrobot said:**
> They told me they were unhappy with the folks they used for support.

Good case in point:  the support relationship is easily as (if not more) important as the software itself for business customers.

---

### Post by SeijiSensei on 2013-12-28
I've been using Lubuntu for a while now rather than Kubuntu on some of my weaker hardware.  I think people coming from XP would find it a compatible desktop environment.  You could run the LXDE desktop on top of RedHat as well.

Is there anyone in your community that provides Linux support?  As lykwydchykyn observes, support can be a lot more important than which distro you choose.  I also think his/her observations about the support models for RedHat vs. Canonical are pretty accurate.  I'd prefer to hire a public company with a long history (nearly two decades now) and a focus on business users over a company that relies primarily on financial support from a single wealthy individual and focuses mostly on consumer desktops and now mobile devices.

---

### Post by buzzingrobot on 2013-12-28
> **SeijiSensei said:**
> 
Is there anyone in your community that provides Linux support? 

Red Hat is local here.  I'm about 20 minutes away from their HQ downtown.

  >  As lykwydchykyn observes, support can be a lot more important than which distro you choose.  I also think his/her observations about the support models for RedHat vs. Canonical are pretty accurate.  I'd prefer to hire a public company with a long history (nearly two decades now) and a focus on business users over a company that relies primarily on financial support from a single wealthy individual and focuses mostly on consumer desktops and now mobile devices.

I'd probably go with RH, as well, without having any specifics in mind, but I'm pretty sure that the enterprise support arm of Canonical run's on the same model as competitors like RH and Suse. I don't know if that part of the company is turning a profit, but it's intended to and it is unlikely Mark S. would willingly sustain a business failure out of pocket. (I don't think he ought to be expected to support Ubuntu-on-the-desktop, either.  So, while I'm not especially interested in the mobile device efforts, I hope they succeed and make barrels of money. In the very near future, Linux vendors who don't target mobile devices will find themselves occupying a small and shrinking niche market.)

But, yes, all things being equal (meaning costs) support is the main thing.  It's all plumbing to businesses, just stuff they need to have but aren't particularly interested in and just want to work without drawing attention to itself.

---

### Post by Allavona on 2013-12-29
In a business environment you want proven, stable, and reliable software. RHEL has this. Gnome 2 is even more functional with RH added developement of it. The old principle of if it works don't fix it comes into play. From a business standpoint, 10 years of support is better than five. RHEL specializes in this field. You want it for home use? Get CentOS/Scientific. You wanna play in the RHEL testbed? Get Fedora
Yum has improved drastically through the years and rpm is an extremely stable, proven package format.

I can't say anything from the Ubuntu side as I've no experience with their coporate/business side of things. But anything is probably better than MS's god-awful support.

---

