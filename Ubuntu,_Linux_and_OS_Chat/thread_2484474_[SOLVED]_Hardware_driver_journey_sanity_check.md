---
title: "[SOLVED] Hardware driver journey sanity check"
date: 2023-02-28
forum: Ubuntu, Linux and OS Chat
---

### Post by msknight on 2023-02-28
This is potentially going to be a bit of an odd one. I'm having hardware/driver issues and I'm currently sanity checking my decisions in order to work out where to pick my battles.

Although this concerns the latest version of Mint this is kernel/driver related and I'm posting here for thoughts and opinion. *(A bad experience on their forums resulted in me deleting my account and hence I'm asking here)* I'm using the latest version on an old motherboard. Gigabyte GA-890GPA. The processor is an AMD Phenom II X6. We're talking kit from 2010

The processor itself is rather nice, 3.3Ghz, 6 core, still a working and useful processor and machine overall. 14gig of Ram... not too shabby and... useful.

However, there are issues.

Firstly, I started getting some odd behaviour with the graphics card. Loading the live image off USB, with a Gigabyte Nvidea PCI-E graphics card in, I can see the BIOS screen, text is fine, but when it goes into graphical environment, it goes blank. If I use the on-board Radeon, it's fine.

However, what gave me pause for thought is that various things are going unclaimed. Chief among them, the onboard network card a Realtek RTL8111/8168/8411. So I did various readings about drivers not being in the kernel any more, etc. etc. I'm assuming that my graphics issue is most likely, likewise a bus/driver issue.

Here's where I sat down and started thinking. I could go on the journey of sorting this out, getting the drivers, patching them into the kernel, something which would then have to be repeated every time the kernel changed... or do I start installing extra cards like network cards, extra USB, etc. using chipsets which are likely to remain supported for longer, or do I just junk an otherwise useful machine and save myself the time it will take to keep it running. *(I already discarded the option of running a kernel of the age required to get some of this stuff working again, on security grounds, and people were reporting issues with the Realtek drivers from, like, six year ago, so I don't want to go back that far.)*

I'd be interested to hear people's thoughts on this, to help me pick my battles, because I get the feeling that this is going to be something I'm going to continue to face in the future; like my, "power laptop," is a Toshiba with an i7 on board which is now approaching ten years. Similar with some of my workstations; I won't find some of this out until an upgrade, one day, starts to see things not working any more. I feel like I'm standing at a cross roads and have a difficult decision to make.

Grateful for thoughts and insight to help me reach a conclusion.

---

### Post by coffeecat on 2023-02-28
Interesting question(s). As this falls between the two stools of support and discussion, I think it might get more traction in *Ubuntu, Linux and OS Chat* so I've moved it here.

Also, please note that the first two main sections of the forum, *Ubuntu Official Flavours Support* and *Ubuntu Specialised Support*, and all their constituent sub-forums, are reserved for [official flavours of Ubuntu]("https://ubuntu.com/desktop/flavours") only. We have [numerous sub-forums ]("https://ubuntuforums.org/forumdisplay.php?f=446")for distros that are not official Ubuntu flavours, and the Mint one can be found here: [https://ubuntuforums.org/forumdisplay.php?f=453](https://ubuntuforums.org/forumdisplay.php?f=453)

---

### Post by msknight on 2023-02-28
Thank you very much. Good idea.

---

### Post by SeijiSensei on 2023-02-28
I'd start by running
```
sudo ubuntu-drivers install
```

---

### Post by msknight on 2023-03-01
> **SeijiSensei said:**
> I'd start by running
```
sudo ubuntu-drivers install
```

All drivers already installed, according to the response from that command.

---

### Post by DuckHook on 2023-03-01
[LIST=1]
[*]Your logs are your friend. Always start by going over them with a fine tooth comb. That last metaphor is meant very deliberately: logs are too much to digest without proper filtering. For that reason, *grep* is also your friend.
[*]It is unusual for the kernel to drop support for old HW. While this does happen, it is mostly for stuff that is turn of the century. I have lots of gear from 2010 and it's all supported. Most often, the problematic drivers were never in the kernel in the first place. They were loaded as external modules. These would be more likely to get dropped, as they are dependant on the distro maintainers and OEM support. OEMs are notorious for ignoring/dismissing Linux and will eliminate Linux support at the drop of a hat while extending Windows support forever.
[*]I used to wrestle with OEM abandonware out of a sense of irrational cussedness ("I'm not letting some dumb piece of gear defeat me, no siree!"—stupid), but concluded some time ago that it's a waste of my time, serenity and equilibrium. These days, I replace abandoned gear with well supported gear. Not just any supported gear either but stuff that is Linux&#8209;friendly. I'd rather reward Linux friendly folks with my money than those who don't care about my OS.
[*]While it is possible to shoehorn old driver modules into new Linux versions (I've done so), I wouldn't recommend it. Even if they work, old drivers that have gone unmaintained for years have all sorts of unpatched bugs and security holes. Unpatched NICs should especially ring three&#8209;alarm fire bells. Please just junk such components and use supported ones, not just for yourself, but for the rest of us. Pwned computers are a menace to society at large.
[*]For similar reasons, I'm glad that you discarded the option of using obsolete kernels. It's not really an option; more a disaster waiting to happen.
[*]Which components you decide to wrestle with and which you throw in the river (don't *really* do that—it's just an expression) is a matter of personal taste. My own approach has changed with time: I used to proselytize for rehabilitating old gear. I still rehabilitate but more judiciously now, and I've dropped the enthusiasm. It makes no sense to burn up an extra $200 of electricity every year for the sake of salvaging an obsolete box chock full of security holes.
[/LIST]

---

### Post by msknight on 2023-03-02
Thanks all. I think I've come to a decision, which is to send the motherboards and processors for recycling.

When push comes to shove, I've got no real use for them at the moment and have enough machines to do the jobs they're already doing... so they'd just sit around for another few years anyway until they got to the point where they wouldn't run any more.

Things like the laptops... I guess I'll have to take a view if, come the day, I upgrade and things stop working. Mind you, with the 2015 Mac Air, the webcam never worked since day one and I haven't felt the need to enter that battle... so.... yeah.

Thanks for the added perspective. It's really helped me.

---

