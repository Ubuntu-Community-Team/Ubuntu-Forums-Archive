---
title: "Developer Summit Day 1 finishes"
date: 2007-10-29
forum: The Fridge Discussions
---

### Post by TheFridge on 2007-10-29
The [Ubuntu Developer Summit]("https://wiki.ubuntu.com/UDS-Boston") (UDS) for 8.04 (Hardy Heron), currently underway in Cambridge, Massachusetts, has just finished the first day. 
 Like previous summits, this UDS starts the first day with an intro talk and then breaks into seperate sessions, usually in tracks such as Server, Mobile, Edubuntu, etc. For a look at what was discussed today, see the [day&#8217;s schedule]("http://people.ubuntu.com/~scott/uds-boston-2007/2007-10-29/index.html"). 
 Every subsequent summit gets bigger and bigger, making it harder for people to get to all the sessions they want or need to and also far too many to talk about here, but here are a few highlights from some of the sessions:
 **Gobuntu**
Gobuntu is the completely free derivative of Ubuntu. Announced last this year and first shipped with 7.10, there is still a lot of work to do. Recent commenters have noticed that Gobuntu ships default Firefox, which includes completely non-free icons. For 8.04, this will be replaced by Epiphany. Firmware is another key issue, with both in and out of kernel firmware is considered non-free. For the out of kernel firmware, it needs to moved to the restricted component and for the in-kernel firmware, this is bit more difficult and will require a seperate kernel, something that should be fixed by the time 8.04 releases. Lastly, the issue of certain multimedia packages might need to moved to restricted from main, although this issue requires more discussion. The [gobuntu-hardy]("https://blueprints.edge.launchpad.net/ubuntu/+spec/gobuntu-hardy") spec is now in Drafting.
 **Telling users about LoCo teams and other local resources**
One of the key problems new users face is finding existing local resources, such as their LoCo team. The best place to tell users about these resources is shortly after install. As such, the installer Ubiquity will need to be modified to tell users about where to find these resources, as well as possibly modifying Pidgin to open to the default LoCo IRC channel, not #ubuntu. The [identifying-users-and-local-groups]("https://blueprints.edge.launchpad.net/ubuntu/+spec/identifying-users-and-local-groups") is still in discussion, although a session has not been scheduled for tomorrow.
 **Hardy artwork**
There were two discussions of the artwork in Hardy today, one covering the theme and the other about the icons. For the theme, a final idea has not yet been laid down, but the discussion steered toward unifying the Mobile and Desktop themes, keeping the orange elements with less gloss. For the icons, the need to keep the Tango guidelines (although not the icon theme) as well as the need for a palette. The relevent specs, [hardy-theme]("https://blueprints.edge.launchpad.net/ubuntu/+spec/hardy-theme") and [hardy-icon-them]("https://blueprints.edge.launchpad.net/ubuntu/+spec/hardy-icon-theme") are both currently still in discussion although neither has a session scheduled for tomorrow.
 **NetworkManager for dialup devices**
A great many devices still use the dialup technology of PPP these says, including many cel-based modems such as Edge or HSDPA and ASDL modems using PPP over Ethernet (PPPoE). Thankfully, the next version of NetworkManger, 0.7, will support PPP, although it is not clear exactly how many of these devices will be supported, due to the enormous number of configuration options and different devices in existance around the world. It was further stated that Ubuntu already supports as many ISDN and WinModems as is possible. The [dial-up-suport spec]("https://blueprints.edge.launchpad.net/ubuntu/+spec/dial-up-support") is now in the Drafting stage.
 **Interacting better with upstream**
It is critical that Ubuntu has good relationships with our upstream application developers, all the way from the larger projects such as GNOME or KDE down to the very smallest of developers. Generating a set of conventions on how to talk with upstream was the major goal here, including such suggestions as praising publicly, criticizing in private, working with both our direct upstream of Debian and the original application author. The [modelling-better-upstream-connections]("https://blueprints.edge.launchpad.net/ubuntu/+spec/modelling-better-upstream-connections") is still in discussion, although another session in not scheduled for tomorrow.
 **Quote of the Day: John (Maddog) Hall**
 [INDENT]Stop trying to solve social issues with technical solutions, as it is often more expensive and ultimately not useful.
[/INDENT] If you are at UDS and did not see your spec covered, feel free to email the author, [EMAIL="corey.burger@ubuntu.com"]Corey Burger[/EMAIL] with a short summary to be included in the day&#8217;s writeup.
 And of course, if you want to help out with UDS, all the sessions are broadcast via SIP and the notes are edited on Gobby, a collaborative editor. For more information, see the [previous Fridge article on participating in UDS]("http://fridge.ubuntu.com/node/1196"). See you tomorrow!
 

[More...](http://fridge.ubuntu.com/node/1199)

---

