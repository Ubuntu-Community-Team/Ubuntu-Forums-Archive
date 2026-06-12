---
title: "software problems"
date: 2010-12-22
forum: Security
---

### Post by 21stCenturyBreakdown on 2010-12-22
Everytime i try and install something from ubuntu software center..i get that message, also earlier i tryed to remove open-jdk6 and i think that broke it =(

---

### Post by Verbeck on 2010-12-22
close any software-center/synaptic and from a terminal (application>accessories), run [I]
sudo apt-get update && sudo apt-get install -f
[/I]and try again

---

### Post by 21stCenturyBreakdown on 2010-12-22
ahh, thanks :D also i have a problem with something called open-jkd6-jre i believe..when i try and remove with package manager, i get a message it wants to install some un verified packages.

---

### Post by BbUiDgZ on 2010-12-22
> **21stCenturyBreakdown said:**
> ahh, thanks :D also i have a problem with something called open-jkd6-jre i believe..when i try and remove with package manager, i get a message it wants to install some un verified packages.

open-jkd6-jre is the java runtime i think..

---

### Post by 21stCenturyBreakdown on 2010-12-22
i know..i want to remove it, but i can't without istalling some untrusted software

---

### Post by sikander3786 on 2010-12-22
Software Center > Edit > Software Sources > Change your download server to Main.

Then from Applications > Accessories > Terminal, post the complete output of this command.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by 21stCenturyBreakdown on 2010-12-22
no wait..now im doing that

---

### Post by sikander3786 on 2010-12-22
Close any other package managers like Software Center, Synaptic, Update Manager or another instance of apt-get or aptitude. They can't be run simultaneously.

If that doesn't solve the problem, simply log out and log back in and post the output.

---

### Post by 21stCenturyBreakdown on 2010-12-22
i also get that with computer jainitor...when nothing else is running

---

### Post by sikander3786 on 2010-12-22
> **21stCenturyBreakdown said:**
> i also get that with computer jainitor...when nothing else is running
Did you try logout/login?

---

### Post by 21stCenturyBreakdown on 2010-12-22
seems to have fixed it..by the way is there a problem on ubuntu that would need a reinstall, like windows?

---

### Post by cariboo on 2010-12-22
You'll see people recommending a re-installation, but in most cases it's easier to fix things than it is to do a re-install.

---

### Post by sikander3786 on 2010-12-23
As *cariboo907* said, almost any problem in Linux can be fixed without a re-install. What is needed is patience :-)

For the moment, you can mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

### Post by 21stCenturyBreakdown on 2010-12-23
thanks :)
my problem is solved now
thanks again

---

