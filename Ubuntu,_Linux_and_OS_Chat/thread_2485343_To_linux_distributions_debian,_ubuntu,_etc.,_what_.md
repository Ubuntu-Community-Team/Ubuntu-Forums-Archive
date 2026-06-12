---
title: "To linux distributions debian, ubuntu, etc., what is needed for users"
date: 2023-03-27
forum: Ubuntu, Linux and OS Chat
---

### Post by hufeng1987 on 2023-03-27
[COLOR=#292C32][FONT=&quot]I think all Linux distributions should look to RHEL distributions to learn one advanced management lesson. That is eternal immortality.[/FONT][/COLOR]

[COLOR=#292C32][FONT=&quot]What does that mean, specifically? It means that Ubuntu, debian will kill itself, or can be described as suicidal, when faced with a severe test of load pressure.[/FONT][/COLOR]

[COLOR=#292C32][FONT=&quot]RHEL, on the other hand, has a very smart strategy. It always keeps the tty accessible to the Linux console. It always keeps the system able to respond to control commands.[/FONT][/COLOR]

[COLOR=#292C32][FONT=&quot]It can rather perform tasks very slowly, even when the load is as high as 90,85, and it can still respond without killing itself.[/FONT][/COLOR]

[COLOR=#292C32][FONT=&quot]This is crucial when running Linux in an enterprise environment. Because if you use debian/ubuntu, your business machines, one by one, will commit suicide, the server kneel, is hundreds of servers one after another.[/FONT][/COLOR]

[COLOR=#292C32][FONT=&quot]RHEL Linux, on the other hand, is unyielding and never dies. You can log in to each machine, operate it, and kill any business that is taking up too much resources.[/FONT][/COLOR]

[COLOR=#292C32][FONT=&quot]Keep the system running smoothly.[/FONT][/COLOR]

[COLOR=#292C32][FONT=&quot]This is the strongest gesture of Linux.[/FONT][/COLOR]

[COLOR=#292C32][FONT=&quot]So if there's one thing I love about RHEL, it's that it's immortal;.[/FONT][/COLOR]

[COLOR=#292C32][FONT=&quot]If there's anything wrong with debian/Ubuntu, it's that it kills itself.[/FONT][/COLOR]

---

### Post by TheFu on 2023-03-27
Thanks for sharing your opinion.  Happy that RHEL works for your needs.  It doesn't work for our needs or for our clients.  

If your debian or Ubuntu servers are "killing itself", then the admin is at fault.  Don't blame the cake for the faults of the baker.

Don't get me wrong, we are happy to install and manage RHEL servers, if that's their wish.  Some want/need it for different reasons.  There's no single reason to pick any specific distro. It is a complex choice that is both technical and political in many organizations.  If the software vendor prefers Debian, then that's what we run.  If they prefer Ubuntu, same.  If they prefer RHEL, we want to know exactly why that is ... our a RHEL-based distro work for their requirements or not?

And when it comes to Desktops, the requirements are vastly different than for Server. I think we can all agree about that too.

I don't want to leave the impression that Ubuntu Servers are perfect. They are not, but neither are RHEL, SuSE, or any other servers. Each has strengths and weaknesses.  The best choice is usually a compromised solution.

---

### Post by BBQdave on 2023-03-28
> **hufeng1987 said:**
> [COLOR=#292C32][FONT=&amp]RHEL Linux, on the other hand, is unyielding and never dies. You can log in to each machine, operate it, and kill any business that is taking up too much resources.[/FONT][/COLOR]

[COLOR=#292C32][FONT=&amp]...So if there's one thing I love about RHEL, it's that it's immortal; [/FONT][/COLOR][COLOR=#292C32][FONT=&amp]If there's anything wrong with debian/Ubuntu, it's that it kills itself.[/FONT][/COLOR]

I'm always suspicious of absolute generalizations. Not sure if this is frustration and a rant, or someone trying to stir the pot :P

Either way, I agree with @TheFu. I would look more at the baker, than the cake mix :)

---

### Post by grahammechanical on 2023-03-29
Let us not forget the big, big, difference between RHEL (Red Hat Enterprise Linux) and Debian/Ubuntu Linux. RHEL has to be purchased. Perhaps the original poster will come back to this thread and tell us the cost. But I doubt it.

I would also like the original poster to explain why the Red Hat Enterprise Linux web site does not reveal the cost up front?

Regards

---

### Post by TheFu on 2023-03-29
RHEL has a free-for-developers program. [https://developers.redhat.com/articles/faqs-no-cost-red-hat-enterprise-linux](https://developers.redhat.com/articles/faqs-no-cost-red-hat-enterprise-linux)  16 nodes mixed with physical and virtual systems.  To me, this seems similar to the free PRO access that Canonical provides. Some may say it is more generous, since it isn't 5.  OTOH, Ubuntu "Members" have access to 50.

As for standard pricing, It is competitive with MS-Windows Server licenses.  [https://www.redhat.com/en/store/linux-platforms](https://www.redhat.com/en/store/linux-platforms)
$350 = Server
$180 = Workstation
$2500 = Data center
There are about 6 other prices on that link for specific features, say openshift.

I've never heard of RHEL being used for workstations. That's completely new to me.  Seems like an odd idea.  Internally, Redhat people use Fedora.

---

### Post by BBQdave on 2023-03-29
> **TheFu said:**
> I've never heard of RHEL being used for workstations. That's completely new to me.  Seems like an odd idea.  Internally, Redhat people use Fedora.

RHEL Workstations would be comparable to LTS. And part of a package to set up a given business.

Way back you could purchase RedHat Workstation as a stand alone product. But I do not believe that is so now.

Fedora is surprisingly stable for the frequent upgrades it goes through.

---

### Post by TheFu on 2023-03-30
> **BBQdave said:**
> RHEL Workstations would be comparable to LTS. And part of a package to set up a given business.

Way back you could purchase RedHat Workstation as a stand alone product. But I do not believe that is so now.

Fedora is surprisingly stable for the frequent upgrades it goes through.

I bought a Redhat desktop distro in the late 1990s.  Probably have the CDROM around here somewhere. I'd been running Gentoo before that and found out that Redhat knew more about kernel tuning than I did. Their desktop ran faster than my custom-kernel-build desktop with Gentoo.

Redhat sells a "workstation" today - look at the link I've already posted.

---

### Post by BBQdave on 2023-03-30
> **TheFu said:**
> Redhat sells a "workstation" today - look at the link I've already posted.

Okay, I stand corrected :)

I thought the workstation was combined with servers, as in setting up a full service for a given business. I thought RedHat stopped selling individual workstations.

Then I (like you) question who the customer is for the RHEL Workstation product. Since Fedora, or Ubuntu LTS, or Debian, or so many other stable GNU/Linux distros are available.

---

### Post by #&amp;thj^% on 2023-03-30
> **TheFu said:**
> 

I've never heard of RHEL being used for workstations. That's completely new to me.  Seems like an odd idea.  Internally, Redhat people use Fedora.

The support is way better than say a Fedora forum...personal care is the key.

---

### Post by DuckHook on 2023-03-30
One only has to lurk on the RHEL forums to see that RH is far from "immortal". It is just as capable of kernel panics and system&#8209;freezing segfault "suicide". It may be more stable than Ubuntu's standard releases, but this is due to the ultra&#8209;conservative approach that RH takes to change, which also means that it is missing many useful and interesting kernel features/modules and the fastest, most performative drivers. That is the price that one always pays for stability.

---

### Post by #&amp;thj^% on 2023-03-30
> **DuckHook said:**
> One only has to lurk on the RHEL forums to see that RH is far from "immortal". It is just as capable of kernel panics and system&#8209;freezing segfault "suicide".
Did I ruffle a few feathers? No system is Imortal>>No System 
> **DuckHook said:**
> 
 It may be more stable than Ubuntu's standard releases, but this is due to the ultra&#8209;conservative approach that RH takes to change, which also means that it is missing many useful and interesting kernel features/modules and the fastest, most performative drivers. That is the price that one always pays for stability.
Agreed, I was first introduced to Linux through RH, but I prefer my non redhat systems.
Customer support was my main kudo's,  plain and simple.

---

### Post by TheFu on 2023-03-30
RH didn't exist when I started. I was an SLS user for a year before the easier-to-install distro, Slackware, came along. ;)
I did run RH on my first dual CPU "server" at home for years. Dual CPU, not dual core.  I'm still using the same case today.  

BTW, that RH server was hacked through a bug in BIND.  I'm not blaming RH for my poor administration. The hack worked because I was 3 months behind on patching BIND. They got in, but couldn't get any farther, thanks to a chroot and some always updated perl code that I'd been running.

---

### Post by VMC on 2023-03-31
A rather odd topic...[COLOR=#292C32][FONT=&amp] Coming from someone that's been around for 8 years, with zero Beans. [/FONT][/COLOR]"[COLOR=#292C32][FONT=&amp]That is eternal immortality." [/FONT][/COLOR][COLOR=#292C32][FONT=&amp]Sounds like a[/FONT][/COLOR] religious fervor.
I can never remember using or even trying RH, and I've used almost all the oldies.

---

