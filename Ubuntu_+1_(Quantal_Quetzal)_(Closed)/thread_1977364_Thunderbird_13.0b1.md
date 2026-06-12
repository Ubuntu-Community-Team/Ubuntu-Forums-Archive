---
title: "Thunderbird 13.0b1"
date: 2012-05-10
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by pressureman on 2012-05-10
It's that time again, ladies and gentlemen. The next beta version of Thunderbird just landed in the repos, and as usual, the Lightning calendar addon hasn't quite caught up. It also has a few odd theme issues.

If you need Lightning to to work, I suggest you apt pin Thunderbird at 12.0 for a bit longer, until Lightning gets rebuilt.

Add the following to your /etc/apt/preferences:

```

Package: thunderbird*
Pin: version 12.0.1+build1-0ubuntu0.12.04.1
Pin-Priority: 1001

```

---

### Post by Miykel on 2012-05-10
I just installed the 13 version and it seems fine, even added the nautilus add on,looks very nice.
Regards Miykel

---

### Post by pressureman on 2012-05-10
I'm sure it's ok to use - but the point of my post was that if you're reliant on Lightning calendar addon, you should hold back for now, as it is not compatible with TB 13.

If you're not using Lightning... go for it... live on the edge ;-)

I just thought the toolbars looked a bit strange, like they weren't picking up the desktop theme.

---

### Post by Miykel on 2012-05-10
Excuse my ignorance but what is lightning, is the lightdm or is something else.???
Regards Miykel

---

### Post by cariboo on 2012-05-10
Lightning is a calendar add-on for Thunderbird, search the Software Centre or synaptic for xul-ext-lightning.

---

### Post by Miykel on 2012-05-10
Thanks Guys, The add on I was talking about is the Nautilus add on which gives a nice appearance in Thunderbird and Firefox.
Regards Miykel

---

