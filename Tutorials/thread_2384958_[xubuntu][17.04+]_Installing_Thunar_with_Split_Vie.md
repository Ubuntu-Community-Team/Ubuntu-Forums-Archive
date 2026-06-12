---
title: "[xubuntu][17.04+] Installing Thunar with Split View"
date: 2018-02-14
forum: Tutorials
---

### Post by there.is.only.xul on 2018-02-14
[SIZE=3][B]Before proceeding...[SIZE=2]
[/SIZE][/B][SIZE=2]*Quick edit: This applies to Zesty onward. Users of Yakkety and below can add the PPA, install the software and proceed as normal without additional steps in between.*

The instructions provided below will [/SIZE][/SIZE]describe how to install an **outdated** version of Thunar, the file manager for XFCE. Downgrading is necessary because there is no known release I could find for build 1.6.12 with the split view patch installed. Fortunately 1.6.11 isn't too functionally different from 1.6.12, and can be used interchangeably in 17.04 and up.

The reason why users reading this might want to install this version of Thunar is if users are coming from other systems where their file manager had a split pane function for navigating through two separate (sets of) directories in the same window. However, since these instructions are also going to describe how to hold back updates for affected packages, it should go without saying the risk for **system instability** and **upgrade failure** increases with every system-critical package any user holds back and keep downgraded, so all holds should be canceled and all previously-held packages should be upgraded before any major upgrade.

**[SIZE=3]Installation[/SIZE]**
Since the repository shown in the code block below is outdated and has nothing for Zesty onward, some editing in mousepad will be necessary before proceeding with sane installation. There is also an insane approach to *only* downgrade Thunar, but this isn't necessary, and thus will be excluded. Open a terminal and begin with this:
```
sudo add-apt-repository ppa:webupd8team/experiments
sudo mousepad /etc/apt/sources.list.d/webupd8team-ubuntu-experiments-*.list
```

Modify the lines in this [FONT=courier new].list[/FONT] file so they use the archives for [FONT=courier new]yakkety[/FONT] rather than your current distribution: this is the last version this PPA supports. After that, proceed as normal (and since [FONT=courier new]thunar[/FONT] is being downgraded, do that):
```
sudo apt-get update
sudo apt-get install libthunarx-2-0=1.6.11-0ubuntu0.16.10.1+1~webupd8~yakkety thunar-data=1.6.11-0ubuntu0.16.10.1+1~webupd8~yakkety thunar=1.6.11-0ubuntu0.16.10.1+1~webupd8~yakkety
sudo apt-mark hold libthunarx-2-0 thunar-data thunar
thunar -q
```
*If you want to make the above easier, you could *[FONT=courier new]alias 1.6.11-0ubuntu0.16.10.1+1~webupd8~yakkety[/FONT]* into something else smaller for the current bash session only if you're having to type this by hand.*

[SIZE=3][B]Conclusion
[/B][SIZE=2]From the instructions above, you should be able to install Thunar with the split view patch. To see this in effect, open [FONT=courier new]thunar[/FONT] and press [FONT=courier new][F3][/FONT]. While this [/SIZE][/SIZE]isn't for everyone, as most people are alright with only using tabs, for the few of us who would rather move and copy things into another pane it is comforting to know an option for that is there. Just don't forget to perform the following before a distribution upgrade:
```
sudo apt-mark unhold libthunarx-2-0 thunar-data thunar
sudo apt-get install --only-upgrade libthunarx-2-0 thunar-data thunar
```

---

