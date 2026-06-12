---
title: "End of Flatpak on Ubuntu - TheRegister article."
date: 2023-02-24
forum: The Cafe
---

### Post by Tadaen_Sylvermane on 2023-02-24
[https://www.theregister.com/2023/02/23/ubuntu_remixes_drop_flatpak/](https://www.theregister.com/2023/02/23/ubuntu_remixes_drop_flatpak/)

They feel threatened by Flatpak apparently.

---

### Post by ajgreeny on 2023-02-24
But unless I'm mistaken Ubuntu and Canonical have never used flatpack as a default! Have I missed something related to a suggestion that flatpacks should be the default?

As for snaps? Well that's very different, and now, of course, snaps are most definitely default applications for some Ubuntu versions.

---

### Post by Tadaen_Sylvermane on 2023-02-24
Near as I can tell they are removing it from being able to be installed. Easily anyway. Likely won't be in the repositories. I have no doubt someone will make a package somewhere but it's the first shot across the bow probably. Kick them out of the highest concentration of home users so people are pushed toward Snap. I wonder if this is what they figure they should have done back in the Upstart & Unity days. Just lock stuff out. 

Any flavors that use flatpak will be disowned as well. That could be interesting. I'm not sure what does but just the threat of it suggests it's out there and too easy for most folks to use > snaps.

---

### Post by guiverc on 2023-02-24
> **Tadaen_Sylvermane said:**
> Near as I can tell they are removing it from being able to be installed. Easily anyway. Likely won't be in the repositories. I have no doubt someone will make a package somewhere but it's the first shot across the bow probably. Kick them out of the highest concentration of home users so people are pushed toward Snap. I wonder if this is what they figure they should have done back in the Upstart & Unity days. Just lock stuff out. 

Any flavors that use flatpak will be disowned as well. That could be interesting. I'm not sure what does but just the threat of it suggests it's out there and too easy for most folks to use > snaps.

No FLATPAK changes will occur in the repositories, none was announced nor discussed.

The official details can be read here - [https://discourse.ubuntu.com/t/ubuntu-flavor-packaging-defaults/34061](https://discourse.ubuntu.com/t/ubuntu-flavor-packaging-defaults/34061)

> As part of our combined efforts, the Ubuntu flavors have made a joint  decision to adjust some of the default packages on Ubuntu: Going  forward, the Flatpak package as well as the packages to integrate  Flatpak into the respective software center **will no longer be installed  by default in the next release due in April 2023**, Lunar Lobster. Users  who have used Flatpak will not be affected on upgrade, as flavors are  including a special migration that takes this into account. Those who  haven&#8217;t interacted with Flatpak will be presented with software from the  Ubuntu repositories and the [Snap Store 35]("https://snapcraft.io/store").


I added the bold; ie. on any of the ISOs you download from ubuntu.com (*which include all Ubuntu flavors*), no ISO for 23.04 or later will include the package `flatpak` on it.

If a user wants to install it, they'll have to `sudo apt install flatpak` manually (*via command or in their chosen package manager*).

```
guiverc@d7050-next:/de2900/lubuntu_64$   rmadison flatpak
 flatpak | 0.11.3-3         | bionic/universe          | source, amd64, arm64, armhf, i386, ppc64el, s390x
 flatpak | 1.0.9-0ubuntu0.4 | bionic-security/universe | source, amd64, arm64, armhf, i386, ppc64el, s390x
 flatpak | 1.0.9-0ubuntu0.4 | bionic-updates/universe  | source, amd64, arm64, armhf, i386, ppc64el, s390x
 flatpak | 1.6.3-1          | focal/universe           | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 flatpak | 1.6.5-0ubuntu0.4 | focal-security/universe  | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 flatpak | 1.6.5-0ubuntu0.4 | focal-updates/universe   | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 flatpak | 1.12.7-1         | jammy/universe           | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 flatpak | 1.14.0-2         | kinetic/universe         | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 flatpak | 1.14.1-1         | lunar/universe           | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 flatpak | 1.14.2-1         | lunar-proposed/universe  | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
guiverc@d7050-next:/de2900/lubuntu_64$ 

```

You'll note the package is there (*bionic & later supported*), it's 'universe' thus is a community supported.  The change is that package is no longer included on ISOs.

For some *flavors*, eg. Lubuntu, there is no change, as `flatpak` wasn't included on any release; it always had to be manually added if required, thus this page

[https://discourse.lubuntu.me/t/using-flatpaks-on-lubuntu/4021](https://discourse.lubuntu.me/t/using-flatpaks-on-lubuntu/4021)

which talks about how to add Flatpak to a Lubuntu install will be no different on Lubuntu 23.04 as any prior *supported *release.  

All *flavors* agreed with the change (*I've opened a doc which contains the signoff details on another screen*), the official announcement, with other Ubuntu Community groups also being involved prior to anything being made public. I've seen many blog posts recently that *stretch* the facts (*even if only slightly*) so as to achieve *click-baity* titles & thus get people opening the blogs, but I'd suggest reading official statements too.

FYI:  The Register article starts "By order of Canonical"....   I disagree with the that title somewhat, but 'click-baity' titles are to be expected. I received notifications of the discussions many weeks ago through various groups (ie. due to my *flavor* involvement, due to my ....) and one word I'd say is more accurate than "order" would be "suggestion".

ie. a more accurate title would be  (*in my view anyway*)

"After suggestion from Canonical: Official Ubuntu flavors will stop including Flatpak by default".

But I was (am?) involved in those discussions, where as Liam Proven was not, thus my view differs.  No order was made, it was a request with reason for the requested change, long discussion that took place over some time, before agreement was reached & each *flavor* signed off.

---

### Post by ian-weisser on 2023-02-24
Folks, when you see something sly in El Reg related to Ubuntu, PLEASE check it out on discourse.ubuntu.com before jumping to the conclusion that a whole group of long-term, reliable, respected, open-source contributors have suddenly and jointly decided that villainy is a great idea after all.

You have access to the truth. Use that access.

In other words, don't be a sucker for everything you are told by a stranger *who makes money from your outrage*.

Let's break this down:

- The flagship Ubuntu Desktop, Ubuntu Server, and Ubuntu Core releases have never included flatpak with a stock install. They are completely unaffected.
- Existing installs are unaffected. Flatpak remains in the Ubuntu repositories. Nothing is being taken away.
- Only new installs of those flavors that include flatpak are affected. This is a sliver of the whole pie (sorry, but true).
- Folks who want flatpak compatibilty are welcome to install it: [FONT=courier new]sudo install flatpak[/FONT]. It's packaged, tested, in the Universe repo for all supported releases of Ubuntu, and readily available.

Since flatpak users are NOT renowned for being fragile and delicate folks who clutch their pearls and faint at the slightest change in weather, I predict that they will have no problem adapting to the minor change.

---

### Post by ajgreeny on 2023-02-25
Thanks for the clarification of this.

I expected something similar, but as I use no flatpack nor snap packages it wasn't important to me so I didn't search any further.

---

### Post by monkeybrain20122 on 2023-02-25
I never use any "official support" from Ubuntu for flatpak anyway. I installed and update the few flatpak apps I have manually. I installed the flatpak extension for gnome software store but it never works very well anyway (very slow to start, auto update is hit and miss) It would be nice to have some integration with the app store for inexperienced users since snap sucks. Nowadays I am hesitant to recommend stock Ubuntu to new users. I hate to have people complaining that even Firefox doesn't work in Linux.

---

### Post by DuckHook on 2023-02-25
> **ian-weisser said:**
> …fragile and delicate folks who clutch their pearls and faint at the slightest change in weather…
Lovely use of poetic imagery. From a period perspective, sorta goes with your choice of Avatar too. O:)

---

### Post by coffeecat on 2023-02-25
> **ian-weisser said:**
> Folks, when you see something sly in El Reg related to Ubuntu, PLEASE check it out on discourse.ubuntu.com before jumping to the conclusion that a whole group of long-term, reliable, respected, open-source contributors have suddenly and jointly decided that villainy is a great idea after all.

+1

However, I would rephrase that as follows:

> Folks, when you see something - *about anything at all* - in El Reg, PLEASE check it out with an authoritative source before becoming yet another victim of profit-related click-bait. 

---

### Post by mIk3_08 on 2023-02-25
Thanks for the info guys.

---

### Post by Tadaen_Sylvermane on 2023-02-25
> Folks, when you see something sly in El Reg related to Ubuntu,

Thank you. I'm recently learning that that site is a fair bit dramatic all to often. My apologies for stirring a nothing burger up like this. Seemed worth mentioning at the time.

---

### Post by DuckHook on 2023-02-25
> **Tadaen_Sylvermane said:**
> &#8230;stirring a nothing burger up like this&#8230;
Don't be so hard on yourself. I found this thread to be a very instructive teaching moment.

And it's what the Cafe is for.

---

### Post by ian-weisser on 2023-02-25
Had you not raised it, somebody else would have.

Somebody always does, and we've all taken a turn.

---

### Post by ne29914 on 2023-02-25
The author on TheReg ("Liam Proven") seems to throw a rash about anything Ubuntu/Canonical. I was silly enough to link to another article about "Pro".
Seems to be a bit of a drama queen.

---

### Post by DuckHook on 2023-02-25
> **ne29914 said:**
> …Seems to be a bit of a drama queen.
Or a troll who happens to work as a journalist.

---

### Post by Claus7 on 2023-02-25
Hello,

is this related to the fact that the latest isos are ~ 5,5GB when the previous ones are at least 1GB less? 

Regards!

---

### Post by DuckHook on 2023-02-25
> **Claus7 said:**
> Hello,

is this related to the fact that the latest isos are ~ 5,5GB when the previous ones are at least 1GB less? 

Regards!
Sorry, but I'm not making the connection between FlatPak and your question. What is it that you suspect?

I will say that bloat is a neverending source of frustration. And it's not a contest that we are winning.

It's not too difficult to compare the packing list of the various distros to see what inflates the ISO although I've never done so. It's probable that most of the newest bloat is snap related—snap FF gets installed by default these days, so it will drag in all of that bloated snap infrastructure.

---

### Post by Claus7 on 2023-02-25
Hello,

> **DuckHook said:**
> ...It's probable that most of the newest bloat is snap related—snap FF gets installed by default these days, so it will drag in all of that bloated snap infrastructure.

Thank you. I hadn't make the connection between snap and size. You answered both of my queries: drop of flatpak is not size related and for the additional ~1GB in isos.

Regards!

---

### Post by ian-weisser on 2023-02-25
> **Claus7 said:**
> is this related to the fact that the latest isos are ~ 5,5GB when the previous ones are at least 1GB less? 

You have access to the actual statement, which includes the reason(s): [https://discourse.ubuntu.com/t/ubuntu-flavor-packaging-defaults/34061/1](https://discourse.ubuntu.com/t/ubuntu-flavor-packaging-defaults/34061/1)

Install .iso image sizes is **not** listed as a reason.

---

### Post by ian-weisser on 2023-02-26
> **DuckHook said:**
> It's probable that most of the newest bloat is snap related&#8212;snap FF gets installed by default these days, so it will drag in all of that bloated snap infrastructure.

[ ... ]

EDIT: Well, I was wrong! DuckHook's analysis is superior, so I will use that instead.

Folks must make their own decisions about whether the benefits outweigh the increased size. My own opinion is that snaps look promising.

Get ready for more snaps-by-default: Printing (CUPS 3.x) looks like might be next. Perhaps LibreOffice also. Both are already in the Snap store.

---

### Post by DuckHook on 2023-02-26
This is my default install of FF in a fresh Jammy LXD virtual machine. No other packages installed. Just FF.
```

duckhook@vm8:~$  snap list
Name                       Version           Rev    Tracking         Publisher   Notes
bare                       1.0               5      latest/stable    canonical&#10003;  base
core                       16-2.58.2         14784  latest/stable    canonical&#10003;  core
core18                     20230207          2697   latest/stable    canonical&#10003;  base
core20                     20230126          1822   latest/stable    canonical&#10003;  base
firefox                    110.0-3           2356   latest/stable/…  mozilla&#10003;    -
gnome-3-38-2004            0+git.6f39565     119    latest/stable/…  canonical&#10003;  -
gtk-common-themes          0.1-81-g442e511   1535   latest/stable/…  canonical&#10003;  -
snap-store                 41.3-66-gfe1e325  638    latest/stable/…  canonical&#10003;  -
snapd                      2.58.2            18357  latest/stable    canonical&#10003;  snapd
snapd-desktop-integration  0.1               49     latest/stable/…  canonical&#10003;  -


duckhook@vm8:~$  snap info core

--snip--

  latest/stable:    16-2.58.2 2023-02-15                  (14784) 122MB -

duckhook@vm8:~$  snap info core18

--snip--

  latest/stable:    20230207 2023-02-18 (2697) 58MB -
  
duckhook@vm8:~$  snap info core20

--snip--

  latest/stable:    20230126 2023-02-08 (1822) 66MB -

duckhook@vm8:~$  snap info gtk-common-themes

--snip--

  latest/stable:    0.1-81-g442e511 2022-06-28 (1535) 96MB -

duckhook@vm8:~$  snap info gnome-3-38-2004

--snip--

  latest/stable:    0+git.6f39565 2022-09-30 (119) 363MB -

duckhook@vm8:~$  snap info snap-store

--snip--

  latest/stable:     41.3-66-gfe1e325 2022-11-29 (638) 48MB -

duckhook@vm8:~$  snap info snapd

--snip--

  latest/stable:    2.58.2                 2023-02-15 (18357) 52MB -

duckhook@vm8:~$  snap info firefox

--snip--

  latest/stable:    110.0-3      2023-02-16 (2356) 252MB -

```
1,057 MB of snap versus 56 MB for a deb.

---

### Post by TenPlus1 on 2023-02-26
Something as important as a web browser should be installed using the native package manager (deb) to have it run the best it can with full compatibility.

---

### Post by grahammechanical on 2023-02-26
Ubuntu developers do not take responsibility for updating Flatpack. I think the same applies to Appimage. It seems that Ubuntu developers do not want the user to assume that if a Flatpack app is installed by default on a Ubuntu Flavour the user will neglect to update the Flatpack because they assume the Ubuntu developers will do it for them. Which they will not. The installation will then become vulnerable.

[https://www.omgubuntu.co.uk/2023/02/ubuntu-flavors-no-flatpak](https://www.omgubuntu.co.uk/2023/02/ubuntu-flavors-no-flatpak)

> They reason, someone using a flavor offering Flatpak *might*  assume the tech receives the same level of support, bug fixes, and  development attention as repo and snap apps do from Ubuntu&#8217;s community  of developers or Canonical themselves.
   Which is not the case.


I think this is a reasonable position for Ubuntu developers to take. Flatpacks and Appimages can still be installed in Ubuntu. It is our choice and our responsibility.

Regards

---

### Post by ian-weisser on 2023-02-26
> **DuckHook said:**
> 
1,057 MB of snap versus 56 MB for a deb.


Ach, I had indeed forgotten the core dependencies.

I doff my hat, add salt, and begin to eat it.

Thank you for the clear, straightforward, unarguable analysis.

---

### Post by DuckHook on 2023-02-26
> **ian-weisser said:**
> …I doff my hat, add salt, and begin to eat it.
*gasp* :shock:

Don't do that… It's a priceless Civil War artifact!

---

### Post by ne29914 on 2023-02-26
> **DuckHook said:**
> This is my default install of FF in a fresh Jammy LXD virtual machine. No other packages installed. Just FF.
...
1,057 MB of snap versus 56 MB for a deb.

This is mine:
```
macro@1dk6910p:~$ snap list


Command 'snap' not found, but can be installed with:


sudo apt install snapd

```
Quite frankly, I don't mind too much about package sizes. I mean, what's the price of storage these days?
But I dislike adding more layers of abstraction and intransparency to my system.
I'll stay with PPAs.

---

### Post by DuckHook on 2023-02-26
> **ne29914 said:**
> …Quite frankly, I don't mind too much about package sizes. I mean, what's the price of storage these days?
Bloat is not really about storage. It is indicative of inefficiency, sloth and bad coding. Not an exact proxy—more correlation than causation—but it is pretty indicative.

Obviously, a caveat is needed here—I don't want to slander good people doing good work—sometimes large code is unavoidable because we are dealing with large tech, but historically, bloat is bad news.

We don't need to go any further than proprietary OSes for an example of this. They are massive, lumbering beasts of bloat. They are also inefficient, obscurantist, dodgy, kludgy messes. Is this a coincidence? I don't think so.

We used to take pride in Linux because it was lean and mean. It was also appreciably more secure, transparent, direct and efficient. Was this likewise a coincidence? I likewise don't think so.

The bloat dragged in by snaps may be necessary and innocuous or it may be taking us in a bad direction. I haven't made up my mind on which. But, given the poor history of bloatware, I think the onus is on its proponents to convince me that it is okay.

---

