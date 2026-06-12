---
title: "Fonts all messed up after upgrading"
date: 2013-04-05
forum: Ubuntu Development Version
---

### Post by Helkaluin on 2013-04-05
After upgrading from Quantal, all my UI fonts become the default serif font.  Even the terminal font is changed.

I've double checked the settings in Advanced Settings to no avail.

[ATTACH=CONFIG]240976[/ATTACH]

---

### Post by dino99 on 2013-04-05
dconf-tool might help

or let the system recreate a clean settings base for : .local , .config, .gnome2, .gconf  (renamed them, or simply delete the fonts related entries inside; they are recreated on the next reboot)

---

### Post by Helkaluin on 2013-04-05
No use.  The relevant values are changed by Advanced Settings anyway.

---

### Post by Helkaluin on 2013-04-05
Problem exists in LightDM as well: instead of the Ubuntu font I've got (what I believe is) DejaVu Serif.

I'm utterly clueless.  I've tried re-installing fontconfig and xft packages but still the problem is still there.

---

### Post by ft_ on 2013-04-05
did you try :
**sudo dpkg-reconfigure fontconfig**
?

---

### Post by Helkaluin on 2013-04-05
> **ft_ said:**
> did you try :
**sudo dpkg-reconfigure fontconfig**
?

Yup.

Even curiouser: the fonts are all fine in Firefox!

---

### Post by dino99 on 2013-04-05
> **Helkaluin said:**
> Yup.

Even curiouser: the fonts are all fine in Firefox!

see that too; i suppose its a transitional problem; will see later if its become better

---

### Post by Helkaluin on 2013-04-05
> **dino99 said:**
> see that too; i suppose its a transitional problem; will see later if its become better

So you're experiencing the same problem?

Did you notice which packages were upgraded when this happened?

Can anyone else on this forum confirm the problem?

---

### Post by dino99 on 2013-04-06
i have not paied too much attention about that issue, but you can check the synaptic history to know which packages have been upgraded

---

### Post by Helkaluin on 2013-04-06
Problem somehow solved after reinstalling the xft, freetype, and pango libs, purging the Arphic uming and ukai fonts, and then re-installing the fonts.

I still don't understand what went wrong.  But the problem's solved for now.

---

### Post by cariboo on 2013-04-06
I marked the thread solved for you.

---

### Post by Helkaluin on 2013-04-06
> **cariboo907 said:**
> I marked the thread solved for you.

Thanks.

I couldn't find the 'Mark thread as solved' button that used to be under 'Thread tools' before the vBulletin upgrade.  Is it moved somewhere else?

---

### Post by zika on 2013-04-06
> **Helkaluin said:**
> Thanks.

I couldn't find the 'Mark thread as solved' button that used to be under 'Thread tools' before the vBulletin upgrade.  Is it moved somewhere else?Try to edit Your first post (if You are OP) in the thread... You'll find what You're looking for...

---

### Post by cariboo on 2013-04-06
> **Helkaluin said:**
> Thanks.

I couldn't find the 'Mark thread as solved' button that used to be under 'Thread tools' before the vBulletin upgrade.  Is it moved somewhere else?

We've asked Canonical IS to install a list in plugins we gave them, including the solved plugin, we should see it enabled after they have gone through a security check up.

---

