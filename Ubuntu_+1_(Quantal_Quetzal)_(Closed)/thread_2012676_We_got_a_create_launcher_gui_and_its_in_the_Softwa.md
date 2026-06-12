---
title: "We got a create launcher gui and its in the Software Center"
date: 2012-06-29
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by philinux on 2012-06-29
[http://iloveubuntu.net/meet-create-launcher-easy-example-based-launcher-creation-tool](http://iloveubuntu.net/meet-create-launcher-easy-example-based-launcher-creation-tool)

Well I hope it is. On android at the moment.

[edit] ah, well I've edited the title now I'm back at pc.

Not in repo but SC as a free but you have to buy app process.

So the apt: link in the article does not in fact work.

---

### Post by mc4man on 2012-06-29
With the current delivery type can't see getting much attention or use
(- SC > Purchase > Ubuntu SSO potential nonsense  > then probably give credit card for price of zero, ect.

The odds of SSO working seem to be 50-50, right now it gives a "server error 500" (even though I'm currently logged into UbuntuOne & Launchpad

(Also will only show in SC in 12.04 & maybe 11.10

---

### Post by diesch on 2012-06-29
If you prefer to get you software from a PPA have a look at [Arronax](http://www.florian-diesch.de/software/arronax/)

---

### Post by mc4man on 2012-06-29
> **diesch said:**
> If you prefer to get you software from a PPA have a look at [Arronax](http://www.florian-diesch.de/software/arronax/)
That I've tried & works very well, the only small downside is MimeTypes are to be entered single line only though there is a workaround for that

---

### Post by diesch on 2012-06-29
> **mc4man said:**
> That I've tried & works very well, the only small downside is MimeTypes are to be entered single line only though there is a workaround for that

You can enter several MIME types per line seperated by semicolon (";"). Technically the newsline just get converted to semicolons.

I'll change the label in the next release.

---

### Post by mc4man on 2012-06-29
> **diesch said:**
> You can enter several MIME types per line seperated by semicolon (";"). Technically the newsline just get converted to semicolons.

I'll change the label in the next release. 

OK - was wondering why it worked when pasting in whatever;whatever;ect
Didn't think to try manually typing (took the label to heart..

---

### Post by mc4man on 2012-06-30
Well - after giving up using existing LP id & password set up a new user for ubuntu SSO & downloaded (no credit card needed

The app is ok - very well documented
Overall I think Arronax is better featured & more accessible to bug reports ect.
(edit: not to say that the create launcher app doesn't have some interesting options

The create launcher app has a bit of a flaw - 
For any launcher to set as the default thru a file's > properties.., (or even show on the regular "open with" menu),  it needs to have it's Exec= line end in <space>%<letter> typically %U, %u, or %f
(or even show on the regular "open with" menu

The app doesn't add this to it's .desktop's Exec= & for some reason "" the Exec= command.
So if a user added it to the command in the gui then for example %U would be inside the "" which is not right & will cause the launcher to fail

Was curious about the Dash 'hint' deal
Turns out Dash also searchs .desktops based on the Comment= line which is useful to know for self made .desktops

Edit: the quoting of the Exec= command turns out to be a poor idea, very limiting
It also prevents the setting of an env - Ex
This is no good
Exec="env UBUNTU_MENUPROXY=0 /opt/bin/audacious"
nor this - 
Exec="env UBUNTU_MENUPROXY=0 /opt/bin/audacious %U"
nor
Exec="/opt/bin/audacious %U"

Likely other examples - someone should tell the dev, I think he speaks mainly german

---

### Post by philinux on 2012-07-05
Update - Drag and drop support.

 [http://iloveubuntu.net/handy-launcher-creator-arronax-003-released-dragdrop-support](http://iloveubuntu.net/handy-launcher-creator-arronax-003-released-dragdrop-support)

---

