---
title: "Quick review of Windows-based PVR software"
date: 2008-05-21
forum: Windows
---

### Post by r76 on 2008-05-21
*I'm writing this because I have some free time whilst waiting for SQL Server to uninstall from XP...*

Although MythTV is maybe the biggest PVR solution on these forums, I found it needlessly cumbersome and confusing.  I also wanted to find some software for a Windows box at home - ideally I want to be able to access BBC iPlayer etc through an interface on the TV.  I'm quite happy running Kaffeine and FreeGuide on my Ubuntu machine, but I haven't found as good an app as Kaffeine for Windows.  Also I kind of feel the EPG guide browser (I use FreeGuide on either OS) should really be a built in function, to schedule recording, mark favourites etc.

Anyway a recent purchase of Nero 8 promted me to try out the "Nero Home" functionality - so I thought I'd compare it with other current PVR solutions as well as the Hauppauge software bundled with my DVB-T tuner.  I was genuinely curious to find out what Windows software is out there that fills this role.

[LIST]
[*]**Hauppauge WinTV6** (download version WinTV CD4.4) - downloaded the latest version, only works with Hauppauge tuner. Closed source. Small community, but no community software development.
[*]**Nero Home** (Nero 8 version) - comes bundled with the main Nero programs.  Closed source.  No real community input.
[*]**GB-PVR** (v1.2.9) - freeware. Closed source. Good, active community.
[*]**MediaPortal**( 1.0 RC1) - freeware. Open source. Good, active community.
[/LIST]

**Hauppauge WinTV 6** (WinTV CD v4.4).  The supplied software is easily installed.  It has recently improved since the WinTV2000 software, but that legacy is still evident in the frustrating menu design.  Moreover, the fact that there are three separate programs for the TV, scheduled recordings, and EPG, and they aren't even linked properly together is laughable.  It sort of defeats the purpose.  The EPG is also stunningly poor in functionality and layout.  It feels like Hauppauge don't even use their own software - if they did they would surely spend some time rewriting it.  Programming recordings is particularly painful compared to Kaffeine, with it's built in EPG and timer functionality.

**Nero Home**. Ready to run after the install of the Nero suite (which is itself painless).  Setup is quick, simple and done through the media interface.  The limited options are not overwhelming to the beginner. Once running, interface was incredibly slow, TV rendering was poor (uses Nero codecs) and the interface mediocre.
Important: care must be taken if running the Nero Scout (media indexing) application, especially on Vista, it can slow disk access.

**GB-PVR**.  Quick to install and configure, by following well-written wiki.  Only one config app (background service) and one media interface app makes for intuitive setup.  Lightning fast when running, allows choice of codecs (found Cyberlink gave better TV picture). Default skin ok but downloaded community skin from wiki which was nicer.  Remote worked as expected.  Internet access to EPG and recording functions also easy to set up. Very simple for other family members.

**MediaPortal**.  Long install process involves installing SQL server.  I installed the default MS one - beware! Ensure you have a system restore point as this totally screwed up my system and refused to uninstall.  Configuration is complex, and there are several configuration tools in addition to the initial set of dialogue windows and SQL install. Although the wiki covers each of the settings and is mostly up to date, the setup can be daunting as there are just so many nested settings to go through.  When you've set all this up and boot into the program, the settings dialogue in the media interface seems to be a wizard for much of what you just configured.  I'm confused by that.  MediaPortal takes the longest to load of any of the programs, although the interface feels snappy.  Although the Hauppauge remote mostly worked well, I got trapped in Live TV and nothing responded, not even ctrl-alt-del, so I had to switch the power off. Although Mediaportal uninstalls itself well enough, the Microsoft SQL server has been a nightmare.  I am now four hours and two system restores into getting rid of it.

[LIST]
[*]**[COLOR="DarkRed"]Results[/COLOR]**
[*]**Hauppauge software**: [COLOR="#8b0000"]**1/5**[/COLOR].  Doesn't even make an effort.
[*]**Nero Home**: [COLOR="#8b0000"]**2/5**[/COLOR]. Impossibly slow for everyday use
[*]**GB-PVR**: [COLOR="Red"]**5/5**[/COLOR]. Fantastic software, simple to configure, I'll be keeping this one.  Nice look, and the fastest loading, channel changing and (on a par with MediaPortal) menu navigation.  Now all it needs is a simple web interface to iPlayer etc and I'll be laughing :)
[*]**MediaPortal**: [COLOR="DarkRed"]**3/5**[/COLOR]. Although I found it cumbersome and unusable, I'm sure it will evolve over time and is worth keeping an eye on.  Particularly since it is open source and gathering a lot of pace.  Configuration felt more complex than MythTV, was unenjoyable and overkill - I personally just want an appliance-like experience similar to commercial integrated solutions - it's only TV after all! The SQL problems are Microsoft's and not the from this software itself.
[/LIST]

[FONT="Arial"]System: 2.4GHz Dell Inspiron 8500 laptop, Hauppauge Nova TD USB dual DVB tuner and remote control, s-video connection to TV[/FONT]

---

