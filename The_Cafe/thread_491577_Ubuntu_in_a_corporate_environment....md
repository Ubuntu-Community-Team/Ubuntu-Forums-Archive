---
title: "Ubuntu in a corporate environment..."
date: 2007-07-03
forum: The Cafe
---

### Post by hellomatts on 2007-07-03
I hope that this was not already asked in this forum... however, I am playing around with WIndows Vista and Ubuntu to upgrade our office of approx. 25 systems... I was wondering if anyone else has had the chance to use Ubuntu in a corporate environment, and if so, how there experience has been thus far...

Thanks!

---

### Post by GMU_DodgyHodgy on 2007-07-03
> **hellomatts said:**
> I hope that this was not already asked in this forum... however, I am playing around with WIndows Vista and Ubuntu to upgrade our office of approx. 25 systems... I was wondering if anyone else has had the chance to use Ubuntu in a corporate environment, and if so, how there experience has been thus far...

Thanks!

I am working with my wife to see if I can replace her Windows desktop for her accounting and tax practice.  

The only real hiccup thus far is her tax software which is a windows based program used by a many medium and large size firms.

---

### Post by prizrak on 2007-07-03
Won't have much problem if you make sure that all the hardware works and necessary software either has an Ubuntu counterpart or is runnable under WINE. Setting up a print server might be a bit of a challenge, an e-mail system is also another thing to watch out for. Evolution seems to work pretty well as an Outlook replacement but it won't work with Exchange as well as it would need to in an organization.

---

### Post by HermanAB on 2007-07-03
You will end up with one or two Windows only programs.  If those happen to run on Wine - cool, problem solved.  Otherwise, you may have to install WinXP or Win98SE (much faster) on Qemu (or VMware Server) to run those obstreperous applications.  Emulation is getting easier by the day - it really isn't hard to do anymore.

I fire up VMware with WinXP once a year to do my taxes.  The rest of the time it is Linux only.  

Nowadays the question is not whether Linux is ready for the desktop, but whether Windows will *ever* be ready for the desktop, since unlike Linux, Windows is regressing.

Cheers,

Herman

---

### Post by kamaboko on 2007-07-03
> **HermanAB said:**
> You will end up with one or two Windows only programs.  If those happen to run on Wine - cool, problem solved.  Otherwise, you may have to install WinXP or Win98SE (much faster) on Qemu (or VMware Server) to run those obstreperous applications.  Emulation is getting easier by the day - it really isn't hard to do anymore.

I fire up VMware with WinXP once a year to do my taxes.  The rest of the time it is Linux only.  

Nowadays the question is not whether Linux is ready for the desktop, but whether Windows will *ever* be ready for the desktop, since unlike Linux, Windows is regressing.

Cheers,

Herman

This is precisely why Linux is not ready for the corporate world, particularly as it applies to the financial world.  I've got a buddy who manages over 200 million in client portfolios.  I can assure you he would never try to run something in "emulation" or "virtualization" when it comes to mission critical information.  All of his financial software is made for the MS platform, and I'm not talkin about QuickBooks.

---

### Post by darkog on 2007-07-04
> **kamaboko said:**
> This is precisely why Linux is not ready for the corporate world, 

Not really entirely a reason why he can't switch to Ubuntu -- but alot depends how those accounting apps are used. 

For example, if it's Quickbooks we are talking about, and not everyone has a license for it or needs access to the app at the same time, they could install it on an WinXP workstation and use rdesktop to rdp to it. Just a thought.  

What they want to do is add up what it's going to cost them in licenses for Visa & all the other windows apps needed and compare that figure to how much they might save if they go with an Ubuntu solution and tweak the  way they use their accounting apps.

What he will definately run into is a lot of ticked off windows users who can't understand why everything is different and changed. So it's really important to explain to people the reasons why things will change, and give them support, and training and understanding during the migration phase.

---

### Post by hellomatts on 2007-07-04
Thanks for all the responses! 

Has anyone had any experience in using this in the corporate environment? If not Ubuntu, perhaps other distros? And if so, how well/bad did it go?

In our situation the only Windows only program that we have running is the CRM GoldMine, but most of the office hates the program, and we are looking for a web based replacement such as Vtiger or SugarCRM...

---

### Post by darkog on 2007-07-04
Switch to SugarCRM. It's great and they will be very happy.

---

### Post by igknighted on 2007-07-04
> **kamaboko said:**
> This is precisely why Linux is not ready for the corporate world, particularly as it applies to the financial world.  I've got a buddy who manages over 200 million in client portfolios.  I can assure you he would never try to run something in "emulation" or "virtualization" when it comes to mission critical information.  All of his financial software is made for the MS platform, and I'm not talkin about QuickBooks.

Ummm, I hate to burst your bubble but virtualization is precisely where corporations are moving.  People are figuring out that neither Linux nor windows can fully meet their needs and want both... with less hardware required.  Why else would companies like VMWare market their products at large corporations and charge such ridiculous fees??

---

### Post by jiminycricket on 2007-07-04
> **prizrak said:**
> Won't have much problem if you make sure that all the hardware works and necessary software either has an Ubuntu counterpart or is runnable under WINE. Setting up a print server might be a bit of a challenge, an e-mail system is also another thing to watch out for. Evolution seems to work pretty well as an Outlook replacement but it won't work with Exchange as well as it would need to in an organization.

Some of these companies who want to get off Windows need to pool their money and pay WINE coders or Codeweavers to get WINE to support those applications.  I'm sure in the end it will be less than Microsoft licensing where you pay twice (one for the Windows on the machine, one for the Microsoft Software Assurance that you can ONLY use as a upgrade, which forces you to buy Windows TWICE!)

---

### Post by darkog on 2007-07-04
> **igknighted said:**
> Ummm, I hate to burst your bubble but virtualization is precisely where corporations are moving.  People are figuring out that neither Linux nor windows can fully meet their needs and want both... with less hardware required.  Why else would companies like VMWare market their products at large corporations and charge such ridiculous fees??

Actually, you are incorrect. The reason they go virtualization is becuase they did studies somewhere stating that most servers get utilized 20 to 30 %. So the idea is to setup a virtu. env, and run more than one NOS on the same box so they can get more utilization out of them, over 80% and supposedly get their moneys worth on their hardware purchase.

There are stories I have heard of people claiming that they get better server performance from some NOS's running them in virtual. -- I personally have not had that experience, but it's worth noting here.

Anyway, back to the OP, if you can get than away from the windows CRM fat client lockin and move to something else, you would be on your way to a Ubuntu environment. You might have to run them both in parallel for a while before you migrate fully though. 25 is a very small network. So i don't think it's going to be any real trouble.

---

### Post by GordonCopestake on 2007-07-13
I would happily change to Ubuntu at work (and use it at home) however in a corporate envirionment applications like Outlook (for exchange server access) and Visio are used (and relied on) too much. 

At the end of the day, people in corporate envirionments dont really care what OS they run, they just want to get on with work. If the OS gets in the way they will change to one that doesn't (like xp). 

If I can't check my email at work, rather than mess around trying to get outlook working under wine i'll just install XP as it's quicker and guarenteed to work.

---

### Post by Elijah on 2007-07-13
It worked for a startup. 

I've helped setup around 5+ desktops and 2 servers using linux only (redhat+ubuntu) and then later when the business grew we managed to increase to around 5 more desktops and upgraded our servers to gentoo. 

Unfortunately, this is a web development environment we are in. We are in need of IE to test our sites, also Safari. That means we absolutely require at least one desktop to run windows so we can vnc into it. 

The company grew some more but a lot of the developers are switching to windows (just because a lot of them are trained using it in their college). This month all our desktops will be switching to Vista and the only Linux server to remain would be just one I guess... and our development server to FreeBSD.

---

### Post by GavinZac on 2007-08-28
> **kamaboko said:**
> This is precisely why Linux is not ready for the corporate world, particularly as it applies to the financial world.  I've got a buddy who manages over 200 million in client portfolios.  I can assure you he would never try to run something in "emulation" or "virtualization" when it comes to mission critical information.  All of his financial software is made for the MS platform, and I'm not talkin about QuickBooks.

I work for EMC, owners of VMWare. Your "buddy" would be best advised not to make such ignorant and downright incorrect statements in front of colleagues as he'll look quite silly **when** his firm joins the list of VMWare customers. virtualisation is pretty much top of most company's agenda's.

---

### Post by perspectoff on 2007-08-28
I think the Windows blankie-holders don't realize why they need Microsoft Exchange.

Unix (and then linux) was developed for multiple users in mind all-along, unlike all Microsoft products, which were developed with a focus on the single user. 

Once Ubuntu reaches significant market saturation, business-software vendors will write more programs for it. They will be delighted to find out how much easier it is to have a corporate environment in Linux than in any Microsoft OS.

---

### Post by mips on 2007-08-28
The one thing I have never seem is how to support Linux in a corporate with 20 000+ desktops. On windows it is easy. How do you do it on Linux?

---

### Post by perspectoff on 2007-08-28
BTW -- have you checked out the Case Studies on this website?

---

### Post by Wolki on 2007-08-28
> **mips said:**
> The one thing I have never seem is how to support Linux in a corporate with 20 000+ desktops. On windows it is easy. How do you do it on Linux?

I suggest asking Novell, I guess they (or Peugeot Citroen) have an idea:
[http://www.novell.com/news/press/psa_peugeot_citro_eumln_chooses_suse_linux_enterprise_desktop_from_novell](http://www.novell.com/news/press/psa_peugeot_citro_eumln_chooses_suse_linux_enterprise_desktop_from_novell)

---

### Post by hkgonra on 2007-08-28
Actually most big business runs on os400 or unix software for their big accouting programs, Linux works just fine with those.

---

### Post by smiggs on 2007-08-28
> **hkgonra said:**
> Actually most big business runs on os400 or unix software for their big accouting programs, Linux works just fine with those.

Unfortunately, that's not entirely true. The newer software packages are based on Windows servers and written for Windows client, my company is in the process of rolling out the Microsoft Dymanics accounting software. Thankfully it'll replace a load of excel spreadsheets but using it on Linux is going to be wishful thinking.

The trick with software such accounts packages is Terminal Server and Citrix, alot of vendors actually pitch their packages to include these so to cut down on network overheads. So if you can move the applications to these mediums you'll be all set for Linux desktop so long as Accounts can live without Excel (you could even put that on terminal server!).

---

### Post by mips on 2007-08-29
> **Wolki said:**
> I suggest asking Novell, I guess they (or Peugeot Citroen) have an idea:
[http://www.novell.com/news/press/psa_peugeot_citro_eumln_chooses_suse_linux_enterprise_desktop_from_novell](http://www.novell.com/news/press/psa_peugeot_citro_eumln_chooses_suse_linux_enterprise_desktop_from_novell)

I was hoping someone here would know.

Maybe I should fire of an email to Canonical but I wonder if they would want to charge me for the information from a support perspective?

---

### Post by Wolki on 2007-08-29
> **mips said:**
> I was hoping someone here would know.

Maybe I should fire of an email to Canonical but I wonder if they would want to charge me for the information from a support perspective?

What's your specific problem or question? "How to support 20,000 desktops" is a large topic.

---

### Post by mips on 2007-08-30
> **Wolki said:**
> What's your specific problem or question? "How to support 20,000 desktops" is a large topic.

I have several but I have to go out now. I will post them a bit later on.

---

