---
title: "Ubuntu Post-Intrepid should be 9.05"
date: 2008-08-29
forum: Ubuntu Brainstorm
---

### Post by Fixman on 2008-08-29
The last two Ubuntu distributions (Gutsy and Hardy) were released on the last day of the month, and the first versions of those had many hardware-related bugs, revealing lack of non-mainstream testing. I do not doubt Intrepid Ibex will have the same problems, because of the "compulsory" 6-month release rate. However, by being both Gutsy and Hardy (and Intrepid) released on the last day of the month, is it to ask if two or three more weeks of "public betas" is trally a big difference (besides of the changing of the "version number" of the distribution) to not having a month of "New Ubuntu broke my computer" threads on the forum. This is why the Ubuntu that will go next to Intrepid Ibex should be names "Ubuntu 9.05" and be released after 7, not 6, months (on may 2009).

---

### Post by gnomeuser on 2008-08-29
and then people will wait to jump on till the public betas.. then we decided to do .1 releases to signal stability and people will wait for those. 

It's merely delaying the date at which the influx of people happens, which is when we see the massive live scale testing. Remember even the most valiant squad of QA testers can not hit every possible combination of hardware, and in a collection of software as big as a Linux distribution then even hitting the default installed apps in all common cases is hard.

The only way to ensure your end product is tested would be to write a test each time a bug is fixed to ensure it is tested for with each package update. Since this is prohibitedly time ineffecient the other major option is doing everything you can to ensure that the development branch is always in an installable state and encouraging people to use it. This does require being more conservative in the development cycle than one might expect but the more hands we have available for testing the better.

The latter option is greatly aided by tools like apport and kerneloops which makes it trivial to report problems. 

Another thing, never ever encourage running any system, especially a development branch with black box proprietary kernel modules and the likes. The amount of crashes caused by these is huge and there is nothing we can do to fix them in pretty much all cases. This becomes a problem because it floods your bugtracker and takes qualified developers time away from fixable problems to managing the flood of bugs. It also makes your platform appear less stable and thus discourages testers to jump onboard. They need to go away, and be replaced with something we can fix.. yes this will suck for some users but only for a little while if we invest time and money in making it happen.

I say this having years of Free Software QA experience, the only way to get things tested is to prioritize a strategy that lets users test at low risk, make it trivial or better yet automate bug reporting as much as possible and finally do what you can to prevent bug spam for things you can't fix - 3 simple rules.

---

### Post by tamoneya on 2008-08-29
> **Fixman said:**
> The last two Ubuntu distributions (Gutsy and Hardy) were released on the last day of the month, and the first versions of those had many hardware-related bugs, revealing lack of non-mainstream testing. I do not doubt Intrepid Ibex will have the same problems, because of the "compulsory" 6-month release rate. However, by being both Gutsy and Hardy (and Intrepid) released on the last day of the month, is it to ask if two or three more weeks of "public betas" is trally a big difference (besides of the changing of the "version number" of the distribution) to not having a month of "New Ubuntu broke my computer" threads on the forum. This is why the Ubuntu that will go next to Intrepid Ibex should be names "Ubuntu 9.05" and be released after 7, not 6, months (on may 2009).

I agree a little more time on betas might be nice but then that would put ubuntu out of sync with other upstream projects with the 6 month release cycle.

---

### Post by insane_alien on 2008-08-30
you do realise that with an extra month there will still be the exact same problems?

we're NEVER going to have a 100% flawless release. nobody is. we cannot test on all hardware configurations, software configurations and even BIOS versions can affect stability.

most of the installs(>90%) are successful another 8% will have trivial problems that need some basic configuration and the rest will have something pretty severe.

this is damn good for what the devs are doing.

---

### Post by apoth on 2008-08-30
You move from flat out new feature development to a bug fixing period and back again. Having a longer cycle will make no difference at all to software quality. You could argue that a longer proportion of the cycle as feature freeze would make for more stable software (at the expense of features) but releasing every 7 months instead of 6? I'm afraid that's crazy!

---

### Post by durand on 2008-08-30
If the ubuntu devs think that an extra month is needed, then they will postpone a release like with ubuntu dapper which became 6.06, two extra months. However, a 6 month release schedule is pretty efficient and as said above, an extra month is not going to fix all the bugs.

---

