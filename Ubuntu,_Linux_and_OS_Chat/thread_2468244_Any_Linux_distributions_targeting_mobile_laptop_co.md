---
title: "Any Linux distributions targeting mobile laptop computing in 2021?"
date: 2021-10-22
forum: Ubuntu, Linux and OS Chat
---

### Post by 6-launchpad-net-cefn-com on 2021-10-22
In 2021 are there any linux distributions that succeed at delivering the basics of a 'mobile computing' use case for aftermarket installation on a laptop.


I consider a minimum 'mobile computing' baseline for reference is...

* a laptop linux build with battery life equivalent to its preinstalled Windows build,
* working wifi and bluetooth audio
* closing the lid goes into hybrid sleep

There seem to be plenty of distros which will get laptops to boot and run off mains power, but every distro+hardware combination I have ever encountered has problems such as...


* the device dies after 25% of its manufacturer stated battery life because some hardware is misconfigured by default, and it's not a focus of the distro to address this
* closing the lid suspends but doesn't go into low power or hibernate leading to the loss of data within hours, and the distro doesn't support hibernation without extensive work
* no power management is installed by default, and the distro doesn't have a 'canonical' way of configuring this
* some component is actually impossible to configure for low power because of proprietary driver issues, and the distro doesn't have up to date information of devices or components which it CAN properly manage for mobile usage to guide installers

These are indications that those distros do not target 'mobile computing'. This makes a typical linux laptop radically worse than an equivalent MacBook in my experience.

I want to identify a distro which targets the 'mobile computing' case, and which is therefore likely to work out of the box without months of effort and likely failure.

I have no experience of the preinstalled Linux market, I don't know what level of mobile-computing support is reliable by default in any of those vendors' distro builds. I can't realistically afford the 'Developer edition' price tags for preinstalled linux models. I can't find any used hardware which came with preinstalled linux, such as System76 or Dell Developer edition, and which is still fairly modern (e.g. 2 or 3 years old) I am looking for an distro that can be installed aftermarket on commodity hardware.

Are there any examples of distro builds which fulfil the listed requirements?

BACKGROUND

In recent years I have relied on Chromebooks which have a linux kernel pre-configured correctly for their target hardware, and which will normally run for 10 hours straight. These fulfil the criteria on paper. They can run XWindows and linux apps via containerised crostini. Unfortunately crostini is not really maintained and is currently unstable on my personal development machine, meaning it routinely experiences hard shutdowns when running or during sleep/hibernation, losing state. Because of the composition of the closed ChromeOS ecosystem, there's no chance of uncovering or fixing those issues. I would like to find a FOSS alternative that meets the criteria of 'mobile computing'.

---

### Post by sudodus on 2021-10-22
I'm asking the following questions in order to find out what kind of help you want from us.

- Do you need experience from fairly new hardware (max 3 years old)?

- Do you need experience from computers delivered with Linux (Dell with Ubuntu or System76 with Pop!_OS)?

- Is working on documents for an 8 hour day without hitting 0% battery mandatory? Or would you be happy if the other specifications can be met?

- Have you got or can you create a tool to test how your specifications can be satisfied? Ideally this tool should be portable, so for example written in bash and calling standard Linux tools.

- Is there some efficient way to monitor the power usage? This would help if you want us to use available hardware for testing.

[hr][/hr]
Have you considered asking Dell and System 76 (the manufacturers) if they have any system, that can satisfy your specifications? I think it is more likely to get a serious answer from System 76, but I may be wrong. Maybe your question will reach a person at Dell who knows and can answer.

---

### Post by 6-launchpad-net-cefn-com on 2021-10-22
A windows laptop typically fulfils some basic benchmarks when running with a Windows OS - e.g. battery life, sleep mode, wifi and bluetooth audio compatibility.

I hope someone can tell me about an aftermarket linux distro which is not notably worse for these three when installed out of the box than its Windows install (on some modern hardware - e.g. no more than 3 years old). 

I can live with a 5% reduction in battery life as the 'cost of linux'. Having a 50% or 80% reduction (which is typical in my experience) can make the build+hardware combination useless as one's daily driver.

I have chosen these three because they embody fundamentals of the 'mobile computing' use case for laptops. In my experience, these benchmarks are also routinely a failure on community linux distros installed aftermarket on commodity laptop hardware. I hope there are exceptions, but I don't know what they are.

I would guess any distro build fulfilling this will be because the community behind the build commits effort to details such as...
* device power management configurations out of the box
* sleep and hibernate behaviours
* guiding adopters towards known hardware having reliable linux driver support for e.g. wifi, bluetooth, audio

I don't know of any distro build which succeeds at fulfilling these criteria out of the box for any hardware. Perhaps someone knows of one.

---

### Post by grahammechanical on 2021-10-22
Over time a laptop battery's ability to hold a charge will diminish. The runtime will be reduced. It is said:

> On average, a laptop battery lasts about 1,000 charge cycles or **between 2-4 years of typical use**.  That's when you should expect to replace your laptop battery. If you're  OK to use it plugged in more often than you used to, there's no need to  replace the laptop battery

The reduction in battery life is not the cost of using Linux. It is the cost of using the laptop and then recharging it again and again. This happens on laptops running operating systems by Microsoft & Apple. In fact, it was reported the other year that a very major supplier of smartphones and tablets was deliberately using a software update to change settings to slow down (throttle back) the device in order to prolong battery life. Some people claimed it was being done to cause user dissatisfaction and set the user up for purchasing the next model to be released.

You want to buy secondhand three year old laptops and install on it a Linux distribution that is not tailor made for the machine's hardware then expect Linux to somehow recondition a used battery.

Linux distributions can extend the working life of older hardware because the hardware requirements are not so severe as required by the latest operating systems of certain commercial corporations. Linux distributions offer a variety of desktop environments. Some desktop environments require less powerful Graphic Processing Units (GPU) than other desktop environments. I guess that those desktop environments would not run down the battery as fast as the other desktop environments.

Some laptops have been produced with hybrid graphics. There is one GPU for office type use and a more powerful GPU for more visual intensive applications such as games. The operating system automatically switches between the two Graphic Processing Units. And so battery runtime is increased. Do not expect Linux to do that automatic switching. 

Buy a laptop with hybrid graphics, install Linux and only use the onboard GPU and not the high power discrete GPU and battery run time will be longer than otherwise.

P.S. Or buy a budget Linux laptop that doesn't suck.

[https://www.omgubuntu.co.uk/2021/10/starlabs-starlite-mark-iv-specs-price](https://www.omgubuntu.co.uk/2021/10/starlabs-starlite-mark-iv-specs-price)

Regards










Linux distributions are not tailor made for specific hardware.

---

### Post by GhX6GZMB on 2021-10-24
My experience is, that Linux is less of a power hog than Win10 on laptops. Just the search indexing (which is on as default on Win10) makes the HDD indicator look like a techno rave light show.
And due to the fact, that Linux is not bundled with second- and third-rate unnecessary apps (as Win10 is) that partially run in the background (without user accept), I suspect that CPU load is much lower, mening less power consumption.

I run only laptops (3 pcs.), all with Lubuntu 20.04.

---

### Post by Tadaen_Sylvermane on 2021-10-25
[https://www.chromium.org/chromium-os](https://www.chromium.org/chromium-os)

Same as Chromium vs Google Chrome. Missing the Google specific bits. But that doesn't help the Crouton issue I suppose. If the Chromebooks hit the mark however then it may be a start?

---

### Post by DuckHook on 2021-10-25
[list=1]
[*]No one can make Linux as organic as Apple. The reason for this is obvious: Apple's control of both the HW and OS is tyrannical. So tyrannical that these two elements, which are two *distinct* elements in the real world, may as well be considered a single conflated element when it comes to Apple. This gives Apple users a holistic experience that cannot be duplicated without similar tyrannical HW/SW control. The bad side of such tyranny is lack of flexibility and being confined to the Apple jail. Apple users don't care about flexibility or being jailed so, for them, the match works.
[*]Windows remains so dominant on the desktop that laptop manufacturers will go out of their way to cater to its quirks, bugs and flaws. They will not even think of doing so with Linux, which remains a marginal OS on the desktop. The realistic upshot is that, on new laptops, your experience with Windows is unlikely to be matched in Linux.
[*]However, on older machines (which both Apple and Microsoft happily abandon with each new OS version), the opposite is true. I have old laptops that won't even install the latest proprietary OSes but which still run tickety&#8209;boo on Linux. So, if you owned older laptops like I do, your question would be reversed: "why can't Win 11 be as responsive, flexible, secure, private and usable on my laptop as Linux?"
[*]WIFI, Bluetooth and shiny new bells and whistles will always suffer in any comparison between Linux and Windows, due to (2) above—equipment manufacturers will bend over backwards to accommodate Windows but do not give a rat's keester about timely Linux support. Since most such equipment requires proprietary drivers, Linux is either at their mercy, or must wait for some generous soul to reverse engineer the shiny new bits so that it can be added to the kernel.
[/list]
Chromebooks are an example of the HW/SW dynamic that comes close to that of Apple's, outlined in (1) above. The OEM takes pains to make sure that all of the elements look and feel holistic, and that the user gets a seamless experience. The downsides are the inflexibility and the jail, which you have already found so limiting.

There is no panacea. If you want to install Linux on aftermarket or used HW, you will have to be prepared to wrestle with some post installation tweaking and some sub&#8209;optimal constraints. I consider it a small price to pay for freedom, but then, that's me.

---

