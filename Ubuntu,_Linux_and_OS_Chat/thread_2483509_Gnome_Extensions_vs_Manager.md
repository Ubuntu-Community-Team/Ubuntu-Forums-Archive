---
title: "Gnome Extensions vs Manager"
date: 2023-02-01
forum: Ubuntu, Linux and OS Chat
---

### Post by agentl074 on 2023-02-01
Do you use Extensions or Extensions Manager?

---

### Post by iamjiwjr on 2023-02-01
Extensions Manager. Love it.

---

### Post by agentl074 on 2023-02-05
One thing I think would be cool is if Gnome included some of these great extensions by default -- like Coverflow Alt+Tab -- that is already included by default in Linux Mint, but just has to be enabled in the Window settings.

---

### Post by monkeybrain20122 on 2023-02-05
> **agentl074 said:**
> One thing I think would be cool is if Gnome included some of these great extensions by default -- like Coverflow Alt+Tab -- that is already included by default in Linux Mint, but just has to be enabled in the Window settings.

No way. Gnome devs are hostile to the addons because they think these addons intrude into their "design vision". If they want these features they could have built them in themselves. The internet is littered with abandoned addons because every new gnome release breaks backward compatibility. If you need a patchwork of addons to make the DE usable then just another DE. 

There is something different between the addon ecology in gnome shell and FF. FF addons  extends the browser but FF is functional without any. Gnome shell is impossible to use without some addons, at least for me.

---

### Post by Dennis N on 2023-02-05
A number of the most popular gnome-shell extensions have been the work of a gnome developer, Florian Muellner, who works for Red Hat. You can see his contributions listed here:

[https://extensions.gnome.org/accounts/profile/fmuellner](https://extensions.gnome.org/accounts/profile/fmuellner)

If you use gnome-shell extensions, you probably use one or more of them.

---

### Post by metomozer on 2023-02-06
I use extension because it is really work full and easy to use.

---

### Post by agentl074 on 2023-02-06
That makes sense... didn't think about that, but since the extensions are available for each shell, it makes more sense to simply add them to the extensions bank rather than bake them into that particular Gnome release. I guess the Gnome team just lets the distros choose what default extensions they want.

---

### Post by DuckHook on 2023-02-07
> **monkeybrain20122 said:**
> No way. Gnome devs are hostile to the addons because they think these addons intrude into their "design vision".
The main reason that Gnome devs seem to frown upon extensions is more innocent than this. There was a discussion some years ago among them on this issue (I can't find it right now, but remember following it for a bit) and the problem is how extensions break system updates. They were tired of users getting mad at them for breakage that they had no hand in, just because the user installed an extension that they had forgotten about or had taken for granted.

Their compromise solution was not to take extensions away entirely, but to make installing extensions sufficiently difficult that the user would not forget that they were now responsible for their own add&#8209;ons.
> If you need a patchwork of addons to make the DE usable then just [use] another DE.
Yup. I totally agree with this.
> Gnome shell is impossible to use without some addons, at least for me.
Not for me. In fact, my advice&#8212;at least for general users&#8212;is the exact opposite: I advise users to leave their base install as close to its default state as possible, also for the same reasons that Gnome developers do: it forestalls upgrade issues. Modern DEs are so complex that it's a miracle that upgrades happen as seamlessly as they do. Unless one is a power user willing to take responsibility for self&#8209;induced breakage, it's unwise to mess with this state of affairs by monkeying around with customizations or extensions.

---

### Post by monkeybrain20122 on 2023-02-07
> **DuckHook said:**
> 

Not for me. In fact, my advice&#8212;at least for general users&#8212;is the exact opposite: I advise users to leave their base install as close to its default state as possible, also for the same reasons that Gnome developers do: it forestalls upgrade issues. Modern DEs are so complex that it's a miracle that upgrades happen as seamlessly as they do. Unless one is a power user willing to take responsibility for self&#8209;induced breakage, it's unwise to mess with this state of affairs by monkeying around with customizations or extensions.

I guess different people have different preferences. I think the version of gnome shipped with Ubuntu is already tweaked and there are some addons installed by default (dash to dock? ) though some functions are disabled. To get the "pure" gnome experience intended by upstream one has to go to Fedora. I tried that and felt like smashing my computer. 

To be clear, I am not adverse to modern design, I like pretty desktops rather than some win98 look alikes. I use Unity (and now there is an official unity flavour, it is trying to move away from the gnome stack as much as possible, at least for things in the user space like file manager etc, since I didn't know that when I installed 22.04 I just slapped a unity session on top of stock Ubuntu and forget about gnome) but gnome is just pita, not because of its look (it looks pretty) but the functionality and awkwardness, nautilus is enough to drive me up the wall. 

It also seems to be very slow and resource hogging, it uses tracker3 for file indexing and constantly uses up 100% cpu. The first few things I do when installing Ubuntu is 1) Install unity 2) remove snap, 3) make nemo the default file manager 4) disable tracker3.

---

### Post by DuckHook on 2023-02-07
But monkey&#8230;

You are a power user who will take ownership of your customizations. In all the years that you've been on these forums, I haven't seen you haul any devs over the coals for breakage that you were responsible for.

If you replace Nautilus with, say, Nemo, then you know exactly what you are doing and won't whine about it if something goes south. That's not the case with general users. Not a month goes by that we don't get some frantic user pleading for help because their dock has disappeared or their desktop won't launch. More often than not, they did something to it that they don't even remember.

When Canonical customizes Gnome to their own standards, then Canonical takes on the burden of maintaining those customizations. No problem there. But when a user takes that further, then the user is essentially turning a standard product into something that is unique and specific to themselves. The more add&#8209;ons, the more unique, until it gets so twisted out of shape that no one can possibly predict or manage the consequences. 99% of update/upgrade problems are a result of such actions.

This is the reason that the proprietary DEs are locked down so tightly. Their business model is scared to death of user tweaks that break something, but that the user then blames on the vendor.

Linux is powerful, but "with great power comes great responsibility", an adage that, for all its pop roots, is perfectly true and one which general users too often don't really understand.

---

### Post by BBQdave on 2023-02-07
> **monkeybrain20122 said:**
> Actually I think the version of gnome shipped with Ubuntu is already tweaked and there are some addons installed by default (dash to dock? ) though some functions are disabled. To get the "pure" gnome experience intended by upstream one has to go to Fedora. I tried that and felt like smashing my computer.

It's funny how "your mileage will very" with desktop experience :)

I have Fedora 37 on one laptop and Ubuntu 22.04LTS on another. I like the flow of F37. I like the use of the Super Key to bring up choices of function, and the rest of the time the focus is on the application(s) I am using in that desktop window. It's personal preference of course :)

I like Ubuntu 22.04LTS too. You lose some desktop space with the dock, but one click and you have your pinned application. And you can auto-hide the dock too. Nice desktop, nice experience with a nod to traditional function.

I'm a Gnome fan, so both distros are comfortable to me :)

---

### Post by monkeybrain20122 on 2023-02-07
> **DuckHook said:**
> But monkey…

You are a power user who will take ownership of your customizations. In all the years that you've been on these forums, I haven't seen you haul any devs over the coals for breakage that you were responsible for.



Well I wouldn't call myself a power user, there is still much I don't know. I am intermediate at best. :)

When I switched to Ubuntu (and later tried other distros as well) I knew what I was signing up for. I like Ubuntu because it is modern, stable but also allows a lot of tweaking and customization because it is still Linux, so you can do "power user" things if you want to but you don't have to like in some difficult distros, that way I learned in my own pace without being overwhelmed like in arch where you have to do ten thousand things before you could get the system up and running, I never even touched gentoo :) With that it also comes with the risk that you may break things so usually I own my mistakes (except if some security updates kill your display or some such things, then it is squarely the devs' fault, that is very very rare, but does happen)

When messing around i think it is important to know what is reversible what is not. If something is reversible the steps to undo should be clear. My problem with a lot of online tutorials is that they tell you how to do x y z but don't tell you whether it is reversible or if it is how. I think a lot of frustrations can be avoided if people communicate their advice better so the novice could assess the risk of whether they go ahead with certain modifications or not.

---

### Post by monkeybrain20122 on 2023-02-07
> **BBQdave said:**
> It's funny how "your mileage will very" with desktop experience :)

I have Fedora 37 on one laptop and Ubuntu 22.04LTS on another. I like the flow of F37. I like the use of the Super Key to bring up choices of function, and the rest of the time the focus is on the application(s) I am using in that desktop window. It's personal preference of course :)

I like Ubuntu 22.04LTS too. You lose some desktop space with the dock, but one click and you have your pinned application. And you can auto-hide the dock too. Nice desktop, nice experience with a nod to traditional function.

I'm a Gnome fan, so both distros are comfortable to me :)

I do have gnome on Arch but it is customized to behave more like unity than stock gome shell. Again I killed nautilus and replaced it with nemo and installed a bunch of addons. Arch is one of those distros that you are expected to mess around :) I tried kde, it is very customizable but it seems kind of bloated and the plasma widgets do funky things like moving around the dock and opening in different virtiual desktops (some maybe bugs, some maybe customizable, who knows, when you have 10,000 configuration options for almost anything. :))

---

### Post by agentl074 on 2023-02-07
I wouldn't recommend installing extensions that are iffy... but there are plenty of safe extensions like Coverflow Alt+Tab, Gnome Weather... but I would recommend being very conservative with any extensions. I remember when I installed one Cinnamon Applet on Linux Mint and I had to reboot and remove the extension... so yeah, there are some extensions that don't play well. I would stick with the extensions that have been proven on other distros (like Mint) -- such as Alt+Tab, Weather, and other conservative extensions that are part of the distribution's factory environment.

---

### Post by monkeybrain20122 on 2023-02-07
If one is looking for extensions maintained by OS makers maybe one can look at Pop! OS (from system76, but you can grab and install it on any Linux compatible hardware) I heard good things about it. It is actually 99% Ubuntu under the hood but with some tweaks and different defaults, it comes with its own customized gnome shell with some different name that I can't remember. Nothing cannot be achieved yourself starting with stock Ubuntu, but I heard that it gives better user experience out of the box. As DuckHook said, novice users should keep tinkering to the minimum, better let the OS's maintainers take care of it as much as possible.


Disclaimer: I never use it myself. Just from talking to some guy in a coffee shop the other day.

---

### Post by DuckHook on 2023-02-07
> **monkeybrain20122 said:**
> I do have gnome on Arch but it is customized to behave more like unity than stock gome shell.
There is no way that anyone who has Gnome layered on top of Arch gets to dodge the moniker: "power user".

You are definitely a power user. :p
> **agentl074 said:**
> I wouldn't recommend installing extensions that are iffy... but there are plenty of safe extensions like Coverflow Alt+Tab, Gnome Weather... but I would recommend being very conservative with any extensions. I remember when I installed one Cinnamon Applet on Linux Mint and I had to reboot and remove the extension... so yeah, there are some extensions that don't play well. I would stick with the extensions that have been proven on other distros (like Mint) -- such as Alt+Tab, Weather, and other conservative extensions that are part of the distribution's factory environment.
But what is "iffy" and what isn't? What is "conservative" and what isn't. I ran into a problem with an extension meant to show lyrics with rhythmbox. It ran fine by itself. Gnome weather extension also ran fine—by itself. And both played nice in Focal. It was when I installed the two of them together after upgrading to Jammy that they corrupted the whole DE. And I mean serious corruption. My entire desktop disappeared including the dock, the tray and the launcher. I know how to recover from stuff like that, but not the average user. They wouldn't even know how to launch a browser to start asking for help.

So, it is precisely this matter of judgment—this determination of what is "safe" and what isn't—that makes extensions so fraught. There is no way for you to establish that Coverflow or Weather or Lyrics is safe. This is just an assumption you make because you haven't run into any issues so far. But you haven't stress tested these extensions, especially when they are installed in their countless permutations and under esoteric setups. Wayland? Xorg? PulseAudio? Jack? Pipewire? What if the user has replaced their default WM with Enlightenment?

I admit that I have a few extensions installed. But, like monkeybrain, I know what I'm doing, how to recover from even major breakage and won't blame the devs when it's my own fault. In short, I'm a power user.

And it seems to me that the default must err on the side of caution. We don't assume that everyone is a power user.

I think that sans extensions is exactly the right approach to take with Gnome. Both Canonical and Gnome itself has made the right decision here. If users want to mess around with the default, then buyer beware. Moreover, the process should not be simple as a warning that they are now on their own.
> **monkeybrain20122 said:**
> If one is looking for extensions maintained by OS makers maybe one can look at Pop! OS (from system76, but you can grab and install it on any Linux compatible hardware) I heard good things about it. It is actually 99% Ubuntu under the hood but with some tweaks and different defaults, it comes with its own customized gnome shell with some different name that I can't remember. Nothing cannot be achieved yourself starting with stock Ubuntu, but I heard that it gives better user experience out of the box. As DuckHook said, novice users should keep tinkering to the minimum, better let the OS's maintainers take care of it as much as possible.
This is an elaboration of your previous comment:
> If you need a patchwork of addons to make the DE usable then just [use] another DE.
…and I agree with it completely. Go to another flavour. Even another distro, but you should stay as close as possible to default on that one too.

---

### Post by zebra2 on 2023-02-08
I'm using Ubuntu 23.04 which for me so far is perfect.  I don't use extensions.  If I can add something to my experience with a software ware i will try it. Otherwise it is default install plus my list of preferred applications for me.

---

### Post by agentl074 on 2023-02-22
> **DuckHook said:**
> There is no way that anyone who has Gnome layered on top of Arch gets to dodge the moniker: "power user".

You are definitely a power user. :p

But what is "iffy" and what isn't? What is "conservative" and what isn't. I ran into a problem with an extension meant to show lyrics with rhythmbox. It ran fine by itself. Gnome weather extension also ran fine&#8212;by itself. And both played nice in Focal. It was when I installed the two of them together after upgrading to Jammy that they corrupted the whole DE. And I mean serious corruption. My entire desktop disappeared including the dock, the tray and the launcher. I know how to recover from stuff like that, but not the average user. They wouldn't even know how to launch a browser to start asking for help.

So, it is precisely this matter of judgment&#8212;this determination of what is "safe" and what isn't&#8212;that makes extensions so fraught. There is no way for you to establish that Coverflow or Weather or Lyrics is safe. This is just an assumption you make because you haven't run into any issues so far. But you haven't stress tested these extensions, especially when they are installed in their countless permutations and under esoteric setups. Wayland? Xorg? PulseAudio? Jack? Pipewire? What if the user has replaced their default WM with Enlightenment?

I admit that I have a few extensions installed. But, like monkeybrain, I know what I'm doing, how to recover from even major breakage and won't blame the devs when it's my own fault. In short, I'm a power user.

And it seems to me that the default must err on the side of caution. We don't assume that everyone is a power user.



Yeah, that's what happens when extensions break and all extentions are disabled. Fair enough... but most people that I speak with who use any Linux distro are at least CompTIA A+ -- like myself, but I realize that not everyone is....

---

### Post by maglin2 on 2023-02-24
To go back to the original question, across my three Linux machines I only have one extension. 

That is to display battery voltage in the top bar on a laptop that has very poor correlation between battery state and %/time remaining. Hence Upower alarms/actions aren't timely enough to prevent low voltage crash. Firmware issue I think.

I used Extension Manager to locate and install it, and found it simple to use and effective.

---

### Post by papakanush2 on 2023-03-07
+1 for extensions manager.

---

