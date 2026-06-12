---
title: "Icons Still Stuck..."
date: 2006-07-21
forum: The Cafe
---

### Post by Zodiac on 2006-07-21
I am going to try and illistrate this issue as best I can...

Here goes:

My icons are "stuck". 

If I change my theme, whatever icon I changed via alacarte, if I even click on an icon in alacarte, it is stuck there, no matter what other theme I choose.

For example, my internet icon is stuck in human, even though I am currently using the tango icon set.

Also, if I choose a theme other than human, my logout prompt reverts to some old hideous one. 

What the hell is going on?

Thanks!

---

### Post by ComplexNumber on 2006-07-21
you need to change your default icons. go into /usr/share/icons, and look for the directory called 'default'. it wll have an index.theme file in it that looks something like this:
> [Icon Theme]
Inherits=Bluecurve my system is fedora, so thats why its bluecurve. yours will have Human. change this to the one that you want it to be by using 'gksudo gedit index.theme'

-------------------

**ignore the above. i think i may have misunderstood.**

the situation that you describe doesn't sound right at all. i have tango at the moment, and my menu is correctly showing the tango icons. do any non-human icons show up anywhere when you change the theme?

---

### Post by Zodiac on 2006-07-21
Mine says:

[Icon Theme]
Inherits=Human

Already... and it still does not work...

---

### Post by ComplexNumber on 2006-07-21
**Zodiac**
i've edited my post. have another look.

---

### Post by Zodiac on 2006-07-21
If I have the default Human theme enabled, then switch to say Silicon, which uses the Tango icon set, any menus that I messed with in Alacarte are stuck and the logout dialog reverts to an old one. 

If I manually go into Alacarte and change the icon to Tango, it will show up properly, but then if I use the theme selector to go back to Human, the icon remains tango until I manually edit it in Alacarte again. 

Also, I cannot get the new logout dialog unless I am using the human theme.

Weird eh?

---

### Post by ComplexNumber on 2006-07-21
yeah, it does sound weird (as i understand it), but i can't help but get the feeling that there is some point that i'm missing.
the way i understand it, it definitely isn't like that on my system. some icon themes are more complete than others. some are quite minimal, so if you change to that theme, the icons in the menu revert to the default(in your case, Human) or the theme that it inherits because those icons aren't actually included in the theme. however, tango icons are pretty complete. therefore, if you change to tango, the Accessories, Games, Graphics, Internet, and all the other menu catagories  have their icon changed to Tango. 

i'm wondering if its something to do with the permissions of your icon themes. go into the tango icon themes and find the following icon:
/usr/share/icons/Tango/24x24/categories/applications-development.png
now click on the permissions. you will see Owner, Group, Others. which of those have the 'read' permissions set?

---

### Post by Zodiac on 2006-07-21
> **ComplexNumber said:**
> yeah, it does sound weird (as i understand it), but i can't help but get the feeling that there is some point that i'm missing.
the way i understand it, it definitely isn't like that on my system. some icon themes are more complete than others. some are quite minimal, so if you change to that theme, the icons in the menu revert to the default(in your case, Human) or the theme that it inherits because those icons aren't actually included in the theme. however, tango icons are pretty complete. therefore, if you change to tango, the Accessories, Games, Graphics, Internet, and all the other menu catagories  have their icon changed to Tango. 

i'm wondering if its something to do with the permissions of your icon themes. go into the tango icon themes and find the following icon:
/usr/share/icons/Tango/24x24/categories/applications-development.png
now click on the permissions. you will see Owner, Group, Others. which of those have the 'read' permissions set?

Yea, just so you know, these are general application icons that should be changing, like internet and office.

I checked the permissions and all groups have read access.

Also, every single theme is effected by this... once I set a theme, unless I manually change the effected icons in Alacarte, I can't switch the icons. It isn't neccasarily a theme problem per se... as any theme is potentially effected if I manually set it.

---

### Post by ComplexNumber on 2006-07-21
ahhh heck! i thought that may be the posible solution. if possible, have a look through some of the other icons in tango to see if the read permission isn't set for Others and Groups. that would cause them not to show up. it happened with me once with the gperfection icon set - i noticed that some icons weren't being shown, even though the icons were present in the theme.....so i went to /usr/share and made all the icons readable by using the command (sudo) 'chmod -R 755 icons'. this would make it readable by all, writable only by root, and executable by all. thats meant to be their default.

i'm sure there is a simple solution to your problem.

---

### Post by Zodiac on 2006-07-21
Well, it can't hurt to try...

---

### Post by Zodiac on 2006-07-21
Doh! Still stuck... darn it.

I feel like it must be an Alacarte bug or something...

---

### Post by ComplexNumber on 2006-07-21
> **Zodiac said:**
> Doh! Still stuck... darn it.

I feel like it must be an Alacarte bug or something...
it won't be an alacarte bug because the icons that show up isn't controlled by alacarte when the icon theme is selected. alacarte just gives the option of changing the icons already selected by the theme.

btw do you have the icon-naming-utils that should be installed in parallel with Tango? if not get them from [here]("http://tango.freedesktop.org/Tango_Icon_Library#Download") and install them.
other than that, i'm out of ideas unless i experience a sudden eureka moment at some point :p

---

### Post by Zodiac on 2006-07-21
I would install, but those directions are awful...

Terrible in fact.

Can I just use synaptic?

---

### Post by ComplexNumber on 2006-07-21
> **Zodiac said:**
> I would install, but those directions are awful...

Terrible in fact.

Can I just use synaptic?
if its in the repos, yes. i get the impression that those icon naming utilities are not just going to be part of tango in the future. i seem to remember that another icon set that i have on my system uses them. they are intended to standardise on the naming conventions between the icon sets. 
but do install them by whatever means if they are not currently installed. if you are installing them from source, the usual   './configure  --prefix=/usr'.......'make'....'sudo make install'  is uneventful and causes no errors.

---

