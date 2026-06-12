---
title: "Suspend and hibernate options gone after upgrading to CE?"
date: 2007-05-02
forum: Ubuntu Christian Edition
---

### Post by naked on 2007-05-02
When I got back to my laptop after doing some errands, I noticed it was off!  My battery had died because didn't suspend.  When I went to check it out, I noticed that suspend was gone from my shutdown screen, and also suspend and hibernate options where missing from gnome-power-manager as well.

Any thoughts?  What would CE install that might affect this?

L

---

### Post by naked on 2007-05-02
Does the convert script keep a log of all that it does?

I seem to remember it removing something and thinking that it wasn't a big deal, but maybe this is what is causing my problems?

L

---

### Post by tak1150 on 2007-05-03
I have the same problem too. I thought I might have done something silly and I didn't want to post it quite yet. But now that I see somebody else has the same problem... 
I just did CE convert to 3.0 and this happened!

Here's my /etc/gdm/gdm.conf-custom (or is it even relevant?)

```

[daemon]
RemoteGreeter=/usr/lib/gdm/gdmgreeter

[security]
AllowRoot=false

[xdmcp]
Enable=false

[gui]

[greeter]
GraphicalThemedColor=#dbb183
GraphicalTheme=login-scan-fusion

```

I may try a fresh install of Ubuntu CE 3.0 ,,,
Brother Jeremy said the convert script was tested on a fresh install of Feisty. So maybe it doesn't work with not-so-fresh Feisty... :( 

Thanks.

---

### Post by naked on 2007-05-03
Well I had LOTS of problems running the convert script on a customized Feisty.  So I did a fresh install today, and immediately ran the convert_me script, and then I ran into this problem.

So I don't know if it is related to non-fresh install, maybe the script?

L

---

### Post by dakotadare2b on 2007-05-03
The issue must have something to do with the gnome power manager, or the way it is configured to work in CE. The default Feisty has the hibernate and suspend options, as I had done a fresh install of Feisty; but after the CE conversion they are no longer available.

I don't have Ubuntu installed on my laptop yet, so I guess I didn't pay too much attention until you mentioned it.

Might have to do some looking around for a possible solution, unless Jereme has one. :confused: 

Randy

---

### Post by naked on 2007-05-03
Tada!

Open up the Conf Editor (System Tools) and go to 'apps -> gnome-power-manager' and check 'can_hibernate' and 'can_suspend'

Their back!

L

---

### Post by mhancoc7 on 2007-05-03
> **naked said:**
> Tada!

Open up the Conf Editor (System Tools) and go to 'apps -> gnome-power-manager' and check 'can_hibernate' and 'can_suspend'

Their back!

L

Thanks for finding the solution. I will keep this in mind for future releases.

Jereme

---

