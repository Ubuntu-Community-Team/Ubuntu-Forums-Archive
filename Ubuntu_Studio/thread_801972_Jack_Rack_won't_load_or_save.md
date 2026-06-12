---
title: "Jack Rack won't load or save"
date: 2008-05-21
forum: Ubuntu Studio
---

### Post by brandjamie on 2008-05-21
Hi, I hope someone here can help me. This is probably an easy problem for a lot of people but its confusing the h*ll out of me. 

Jack Rack won't save or load .rack files. I"ve searched everywhere and the only mention of this problem is  [here ]("http://stevehusted.com/ubuntu-804-home-studio/"): 

     [CENTER]  *NOTE* JACK Rack 1.4.7 on Ubuntu is broken. It was broken on Gutsy and it’s still broken on Hardy. So I simply grabbed 1.4.4-4, the previous version, which was already compiled as a .deb for Ubuntu amd64, and now I can actually save .rack config files.[/CENTER]

I'd be quite happy installing an old version of Jack Rack as per the suggestion above. Trouble is, if i try to install version 1.4.4-4 the synaptic manager will not let me - telling me i already have a later version.  

If I try to uninstall Jack Rack 1.4.7, the manager tells me it is part of a larger application and wants to unintstal 'Ubuntu studio - audio' which i suspect may be a bad idea!!!

Any suggestions as to what I can do? 

Thanking you in advance, 
J.

---

### Post by Stochastic on 2008-05-21
It's actually fine to uninstall ubuntustudio-audio as long as that's the only package it tries to uninstall.  That's a meta package used to install all the audio apps; once they're installed you have no need for the meta anymore.

You're right about the save thing, in hardy - I can't save either (I don't have a saved file to try to open though).  But Gutsy's repo version of jack rack is 1.4.4 so the comment that it was broken in Gutsy and can somehow be fixed by reverting to 1.4.4 seems strange (though he's probably talking about 1.4.7 not saving in a gutsy system).

This launchpad bug claims that compiling 1.4.7 from source will fix the issue [https://bugs.launchpad.net/ubuntu/+source/jack-rack/+bug/211798](https://bugs.launchpad.net/ubuntu/+source/jack-rack/+bug/211798)

---

### Post by brandjamie on 2008-05-21
Thanks, that was all the reassurance I needed. I uninstalled and re-installed the old version (actually 1.4.3 as according to the Jack Rack website it's 'stable' whereas 1.4.4 isn't). - It's working fine now. 

I'll leave compiling from the source to a later date (got a new guitar yesterday so now i just want to play!).

Thanks again. 
J.

---

### Post by EuPhobos on 2008-07-15
I try compile from source 147 version, it does not solve a problem.

---

### Post by qduaty on 2008-07-27
File picker seems to require gnome support, so it must be compiled against libgnomeui-2.0. Install libgnomeui-dev.

Edit: here is my fixed deb (version changed to -ubuntu2 to prevent dpkg from updating it from the repository)

---

### Post by Stochastic on 2008-07-28
qduaty, please submit all patches through launchpad.  These forums can reek havoc on version tracking.  This is a legitimate bug that needs a legitimate fix, please submit via launchpad, or at least talk to a member of the UbuntuStudio team (mailing list or IRC will work quite well).

**To others viewing this thread:** please be aware that the .deb qduaty has supplied has not undergone community review to prove that it will not break your system, open up major security holes, or install a hidden script to copy your credit card details etc... (I'm not implying that it does contain said flaws, just warning there is no proof yet that it doesn't - I haven't even reviewed its code yet).  If this change is submitted via Launchpad, then you can consider it to be safe.  Please see this link for official updates on the matter: [https://bugs.launchpad.net/ubuntu/+source/jack-rack/+bug/211798](https://bugs.launchpad.net/ubuntu/+source/jack-rack/+bug/211798)

---

### Post by qduaty on 2008-07-28
[QUOTE=Stochastic;5472294]please be aware that the .deb qduaty has supplied has not undergone community review to prove that it will not break your system, open up major security holes, or install a hidden script to copy your credit card details etc.../QUOTE]

Well, isn't it obvious? This approach (e.g. a binary patch), is well known on the internet; statistically speaking, it will work for most users, resulting in severe consequences you mentioned above, for others perhaps including you. Nothing makes us free from thinking. Thank you for your help; I already forwarded the solution to the launchpad.

---

### Post by Stochastic on 2008-08-05
Until a patch is submitted on that bug, it might be worth noting that a LASH session will easily save/open a jack rack configuration (though this doesn't help those who have .rack files they want opened).

---

