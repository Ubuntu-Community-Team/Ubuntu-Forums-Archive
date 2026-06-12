---
title: "Ubuntu"
date: 2022-12-11
forum: Security
---

### Post by gordie692 on 2022-12-11
Hi guys question to ask maybe dumb but lets see i have an older hp desktop 8 gigs intel core due onboard video I was thinking Ubuntu 18.04 I notice 2 dates 2023 and 2028 end of life would that OS work thought 18.04 would be lighter then 20.04 this system has a hard time wayland I switch back back org video any questions

---

### Post by TheFu on 2022-12-11
> **gordie692 said:**
> Hi guys question to ask maybe dumb but lets see i have an older hp desktop 8 gigs intel core due onboard video I was thinking Ubuntu 18.04 I notice 2 dates 2023 and 2028 end of life would that OS work thought 18.04 would be lighter then 20.04 this system has a hard time wayland I switch back back org video any questions

I don't see any question and no punctuation.   Do you have one?  A question, that is.

BTW, that's a terrible thread title ... on a forum for Ubuntu.  Something more descriptive will capture more eyes.

---

### Post by ian-weisser on 2022-12-11
It seems like this is a will-my-hardware-work-with-Ubuntu question. It's difficult to tell. You're asking us to speculate what your question might be,

The Ubuntu Desktop installer has a "Try Ubuntu" environment specifically to answer those kinds of questions without touching your hard drive. Use it to test your hardware.

Installing 18.04 seems unwise, as support will --as you pointed out-- end very soon. Try a newer release.

---

### Post by ajgreeny on 2022-12-11
If that hardware has any difficulty running the OS fast enough for you try one of the lower resource requiring versions such as Ubuntu Mate, Xubuntu, or even Kubuntu, which ought to run faster, as the default gnome version is the one that needs the highest resources of all of the versions available.

---

### Post by maglin2 on 2022-12-11
My guess is that there are two implied questions.
What is the actual support end date for Ubuntu 18.04? (answered eg here [https://ubuntuforums.org/showthread.php?t=2481818&p=14122693#post14122693 ]("https://ubuntuforums.org/showthread.php?t=2481818&p=14122693#post14122693"))
Will this machine run better with 18.04 than it does with 20.04? I have a machine with a very old intel twin core processor and I didn't find that was the case, but who knows with a different machine and setup.

---

### Post by DuckHook on 2022-12-11
I suspect that maglin2 parsed the OP's original post accurately.

I have a couple of old Core Duo laptops running Jammy without problems. The fact that the OP has 8GB of RAM is also a good sign. There should be no problem running a modern kernel on such a machine *provided* the chosen flavour avoids heavy graphics.

@gordie692

I've found that all 'buntu flavours have lately upped their resource requirements to the point that really old HW slows down. This includes the old standby that I *used* to recommend: Lubuntu. If I were you, I would still start off with that flavour first. If you find that it's too slow, then I actually recommend leaving the Ubuntu ecosystem altogether and trying something like Bodhi.

That said, you will also find that the biggest performance bottleneck is no longer the distro, but the apps. Running a modern web browser like Firefox or Chromium is very resource&#8209;intensive. It will make more demands on your HW than the OS will. Therefore, your likely pain point won't be the distro that you choose, but the apps that you use. Skinny flavours/distros like Lubuntu or Bodhi try to bundle apps that won't hit system resources as hard, but people have come to expect all sorts of bells and whistles on their apps these days, so substituting lower powered apps is often met with dismay and even hostility. The maintainers of skinny distros have my sympathy for the knife edge they have to walk between their larger goals and the unrealistic expectations of their users.

As a power user, here's what I would do today for an old, limited system:

[LIST=1]
[*]First, install Ubuntu Server.
[*]Then, from the command line, install a stripped down and really basic GUI like lxqt-core
[*]Then, choose miserly apps that just sip system resources: Epiphany instead of Firefox, Sylpheed instead of Thunderbird, Abiword instead of Libreoffice etc.
[*]Avoid any sort of non-default system bloat. Don't add utilities, extra services, eye&#8209;candy or bells and whistles.
[*]Don't even think about apps like GIMP, Inkscape or Blender. This is not the machine for such demanding apps.
------------------
[*]On the HW side, if there is one thing you can do that will make the biggest difference, it is to replace the old decrepit HDD with a SSD.
[/LIST]
You may find the link in my sig useful: The Best 'buntu Flavour

---

### Post by DuckHook on 2022-12-11
On further reading, since you placed this in the security subforum, I'm guessing that you may be asking whether 18.04 ends in 2023 or 2028.

Canonical has a program called [ESM]("https://ubuntu.com/security/esm"). If you subscribe to [Ubuntu Pro]("https://ubuntu.com/pro"), then 5 machines qualify for ESM (for free) and security updates are extended for those machines from 5 years to 10. Corporations that value stability over anything else and who have written custom apps that they don't want to rewrite every 5 years will find that paying for this subscription is worthwhile. For the rest of us, I'm not sure how useful it really is. The IT world is like dog years&#8212;5 calendar years is like 40 human years. So much changes that I wouldn't be comfortable using such an old system.

For example, even though an ESM 18.04 is good to 2028, it won't run Nextcloud because the version of PHP in 18.04 is obsolete and Nextcloud no longer supports it. Even though 18.04 still gets security releases, this does me no good if Nextcloud won't get security releases. Therefore, one of the supposed benefits of running an old release&#8212;its longevity&#8212;turns out to be a superficial one because it can't run a modern, secure platform.

In general, I recommend keeping at least moderately up to date. Though it's tempting to fall behind and not have to deal with upgrades, it will eventually catch up with you, usually at a point when the transition will then be very painful.

---

### Post by gordie692 on 2022-12-11
Thanks guys for all your help sorry it I put in wrong post box just lot on my mind but thanks

---

### Post by maglin2 on 2022-12-12
Your Core Duo may have a slightly higher Passmark than my T4400 ([https://www.cpubenchmark.net/compare/1122vs1004/Intel-Pentium-T4400-vs-Intel-Core2-Duo-T7700](https://www.cpubenchmark.net/compare/1122vs1004/Intel-Pentium-T4400-vs-Intel-Core2-Duo-T7700)).
That machine has just been upgraded to vanilla 22.04. It has an SSD and 4GB RAM.
It's not quick, but it's not desperately slow either.
The SSD, as Duckhook suggests, makes a big difference.

---

