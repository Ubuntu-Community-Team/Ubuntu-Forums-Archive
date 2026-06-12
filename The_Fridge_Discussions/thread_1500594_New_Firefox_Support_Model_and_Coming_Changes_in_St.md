---
title: "New Firefox Support Model and Coming Changes in Stable Updates"
date: 2010-06-03
forum: The Fridge Discussions
---

### Post by TheFridge on 2010-06-03
The desktop team has been working since the Karmic UDS on the following blueprint: [https://blueprints.edge.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model](https://blueprints.edge.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model)

 The upshot of the blueprint is that there will be some changes to users&#8217; desktops if they are currently Hardy, Jaunty or Karmic users.

 In Lucid, we put in a lot of effort to ensure these updates will be easier in the future (Firefox now uses bundled libraries rather than system libraries, we have reduced the number of applications in the archive using xulrunner, and dropped a lot of extensions too). The update for Lucid is quite trivial, but the update in Hardy, Jaunty and Karmic is not quite as simple. When we roll out the new version, we also need to update the following:

 <ul> All the Firefox extensions that we ship in the archive
 Language packs
 In addition to this, we are going to be porting some applications which are currently using xulrunner 1.9 to either the latest version of xulrunner (1.9.2.4) or Webkit. However, this can happen after the Firefox rollout, as the 2 xulrunner versions can be installed in parallel. We have a [list of the affected applications]("https://edge.launchpad.net/~ubuntu-mozilla-security/+archive/ppa"). We won&#8217;t be porting all of the applications on that list, but will be focusing on the applications which are exposed to insecure content [I](at the bottom of
the page)[/I].

 **Why:**

 Firefox 3.0 (and xulrunner 1.9) are now unsupported by Mozilla. Rather than backporting security fixes to these now, we are moving to a support model where we will be introducing major new upstream versions in stable
releases. The reason for this is the support periods from Mozilla are gradually becoming shorter, and it will be more and more difficult for us to maintain our current support model [in the future]("https://wiki.ubuntu.com/DesktopTeam/Specs/Lucid/FirefoxNewSupportModel").

 **When:**

 Next week, Mozilla will release Firefox 3.6.4 as a minor update to the 3.6 series. This will be rolled out to Lucid, Hardy, Jaunty and Karmic (along with xulrunner 1.9.2.4).

 **Call for Testing:**

 Packages will be hosted in the [Ubuntu Mozilla Security team PPA]("https://edge.launchpad.net/~ubuntu-mozilla-security/+archive/ppa").

 As this is being rolled out as a security update (rather than a SRU), there is no bug report tracking this. The rollout is being covered (and will be announced) by USN-930-1.

 Clearly, there are significant risks associated with the update. In addition to ensuring that Firefox and all the extensions still function correctly after the update, we also need to ensure:

 **1.** All the Firefox plugins (eg, Flash) still work
**2.** The actual upgrade to the latest version goes smoothly
**3.** We don&#8217;t break Hardy -> Lucid and Jaunty -> Karmic upgrades
**4.** The upgrade works with the *-updates pocket disabled

 Applications that are ported to the latest version of xulrunner (or to Webkit) will also need testing. However, we will also need to test every application [on the list]("https://wiki.ubuntu.com/DesktopTeam/Specs/Lucid/FirefoxNewSupportModel/xulrunner-list") in *(even the ones which aren&#8217;t being updated)*, with the latest version of xulrunner installed on the system. The reason for this is that most applications dynamically load one of the GRE&#8217;s on the system, and some of these applications will load 1.9.2.4 if it is present. I already know of 1 API change in 1.9.2.4 which had been causing me problems with applications I&#8217;ve been porting, so it&#8217;s possible that the same issue will affect applications we aren&#8217;t
porting if they load the newest GRE.

 You can help testing the upgrade by following the instruction on [https://lists.ubuntu.com/archives/ubuntu-devel/2010-June/030811.html](https://lists.ubuntu.com/archives/ubuntu-devel/2010-June/030811.html)

 Originally posted on the [ubuntu-devel-announce]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2010-June/000719.html") by Sebastien Bacher on Tue Jun 1 11:59:25 BST 2010

 

[More...](http://fridge.ubuntu.com/node/2051)

---

