---
title: "Single Worst Idea in 10.10"
date: 2010-11-04
forum: The Cafe
---

### Post by mahy on 2010-11-04
(this is not meant as a flamewar)

Hi folks,

Maverick is on the whole a very good move forwards. My bluetooth adapter and card reader finally work in it without any necessary configuration change. However, there have been some not-so-good modifications as well, the most mis-fired of them all is the keyboard layout icon in Gnome, which DOES NOT DISPLAY CURRENT LAYOUT. I really don't know what the added benefit is (the new icon is not even nice!), but it's a huge complication when you have many layouts configured. I've got the feeling the author of this change only uses a single layout and thus doesn't need it. :( Please somebody tell me it'll be gone in the next release.

(I'm sorry if this is an improper place for such a discussion. I couldn't find any better on these forums.)

---

### Post by juancarlospaco on 2010-11-04
*Wheres the Bug Report ?*

---

### Post by _outlawed_ on 2010-11-04
What worst idea? 10.10 is perfect...for me at least. :)

---

### Post by zekopeko on 2010-11-04
> **mahy said:**
> (this is not meant as a flamewar)

Hi folks,

Maverick is on the whole a very good move forwards. My bluetooth adapter and card reader finally work in it without any necessary configuration change. However, there have been some not-so-good modifications as well, the most mis-fired of them all is the keyboard layout icon in Gnome, which DOES NOT DISPLAY CURRENT LAYOUT. I really don't know what the added benefit is (the new icon is not even nice!), but it's a huge complication when you have many layouts configured. I've got the feeling the author of this change only uses a single layout and thus doesn't need it. :( Please somebody tell me it'll be gone in the next release.

(I'm sorry if this is an improper place for such a discussion. I couldn't find any better on these forums.)

What are you talking about? Screenshot?

---

### Post by Sandlst on 2010-11-04
> **juancarlospaco said:**
> *Wheres the Bug Report ?*Managed to find one [https://bugs.launchpad.net/ubuntu/+bug/663630]("https://bugs.launchpad.net/ubuntu/+bug/663630")

mhay, you should subscribe to this bug report so you are kept up to date on the status of the bug.

---

### Post by mahy on 2010-11-05
> **zekopeko said:**
> What are you talking about? Screenshot?

Here you are. The Keyboard layout indicator icon is the third one from the left.

And I even subscribed to the above mentioned bug, but hey, this is **nowhere near a bug!** It must've been a deliberate decision to replace the layout code (such as "US" or "DE") with that weird keyboard symbol...

---

### Post by andymorton on 2010-11-05
I'm using 10.10 on my HP Mini 110. Everything works and I haven't got any complaints. :)

---

### Post by phredbull on 2010-11-05
> **andymorton said:**
> I'm using 10.10 on my HP Mini 110. Everything works and I haven't got any complaints. :)
Yes, everything is perfect. Now go back to your unicorns and rainbows in Perfectland. You've been very helpful to the OP.

Back on topic, why would the OP file a bug report? This isn't a bug, it's thoughtless UI design.

---

### Post by Sukarn on 2010-11-05
> **phredbull said:**
> Yes, everything is perfect. Now go back to your unicorns and rainbows in Perfectland. You've been very helpful to the OP.

Back on topic, why would the OP file a bug report? This isn't a bug, it's thoughtless UI design.

Off-topic : lol

On-topic : "thoughless UI designs" are also supposed to be dealt with through the mechanism of bug reports.

---

### Post by NightwishFan on 2010-11-05
Is than an indicator or a gnome applet? Either way it certainly is a bug and along the lines of a papercut. Which Ubuntu likes solving.

---

### Post by P4man on 2010-11-05
I hit the "affect me too" link. Pretty braindead decision, I have to agree. ALso nominated it for 100 paper cuts.

As a workaround, you can enable a keyboard led (like scroll lock) to show the status. Check keyboard preferences > layouts > options > use keyboard LEd...

---

### Post by grahammechanical on 2010-11-05
What do you mean, > DOES NOT DISPLAY CURRENT LAYOUT?

It does on my setup. I have Greek and English (UK) keyboard layout. My minor moan is that in 10.04 I could cycle through the keyboard layouts by clicking on the icon. Now we get a drop down menu and have to select a layout.

Regards.

---

### Post by P4man on 2010-11-05
Funny. It start working here too since .. just now lol. I just installed kubuntu-desktop to try out KDE, no idea if its related.

---

### Post by NCLI on 2010-11-05
Are you kidding, the dividing line between the window frame and the toolbar in the new theme is way worse:

[IMG]http://imgur.com/1f8ur.png[/IMG]
RAAAAAGE!!!!

On-topic: Added myself to the bug report as well, dumb idea.

---

### Post by zekopeko on 2010-11-05
> **grahammechanical said:**
> What do you mean, ?

It does on my setup. I have Greek and English (UK) keyboard layout. My minor moan is that in 10.04 I could cycle through the keyboard layouts by clicking on the icon. Now we get a drop down menu and have to select a layout.

Regards.

The OP used the old notification area and you have the new indicator applet.

---

### Post by MasterNetra on 2010-11-05
> **grahammechanical said:**
> What do you mean, ?

It does on my setup. I have Greek and English (UK) keyboard layout. My minor moan is that in 10.04 I could cycle through the keyboard layouts by clicking on the icon. Now we get a drop down menu and have to select a layout.

Regards.

The OP is using 10.10 not 10.04.

And how do you add this indicator anyway? I don't see it in the list of panel objects. And don't see anything but accessibility which looks nothing like it.

---

### Post by grahammechanical on 2010-11-05
MasterNetra, What do you mean?

> The OP is using 10.10 not 10.04.

I am using 10.10 as well. The indicator appears when you add another keyboard layout. In 10.04 the indicator did not show an image of a keyboard. Just an abbreviation of the language. GBr = United Kingdom. Gre = Greece. Now, in 10.10 we get both but the OP is complaining that he only gets the keyboard icon.

regards

---

### Post by mahy on 2010-11-05
> **grahammechanical said:**
> Now, in 10.10 we get both but the OP is complaining that he only gets the keyboard icon.


Exactly, I'm only getting the icon. Yes it appeared when I added another layout, but that's it, no language code... This is really puzzling.

---

### Post by zekopeko on 2010-11-05
> **mahy said:**
> Exactly, I'm only getting the icon. Yes it appeared when I added another layout, but that's it, no language code... This is really puzzling.

But is it the notification area icon or the indicator icon? That part is unclear to me.

---

### Post by TheNessus on 2010-11-05
remove all "keyboard-input" or "input-keyboard" (don't remember percisely) icons from /usr/share/icons/ to have text only and no keyboard icon.  (how? run search as root and it would find it, from the search you delete what you want)

Sometimes, rarely, it would show an icon of a missing picture; very ugly icon. killall gnome-panel would fix it. But I only encountered it ocne so far.

---

### Post by Mr. Picklesworth on 2010-11-05
As I mentioned in the bug report, this is not how it behaves by default in Ubuntu. You're getting the wrong behaviour because you have removed the indicator applet; it's using the system tray, with the behaviour from upstream. Add Indicator Applet back to your panel, log out, log in and it should work nicely with the functionality that was added in Ubuntu.

---

### Post by TheNessus on 2010-11-06
> **Mr. Picklesworth said:**
> As I mentioned in the bug report, this is not how it behaves by default in Ubuntu. You're getting the wrong behaviour because you have removed the indicator applet; it's using the system tray, with the behaviour from upstream. Add Indicator Applet back to your panel, log out, log in and it should work nicely with the functionality that was added in Ubuntu.

Forget about functionality, it's the icon that is the worst idea :) remove it!

---

### Post by mahy on 2010-11-09
> **Mr. Picklesworth said:**
> As I mentioned in the bug report, this is not how it behaves by default in Ubuntu. You're getting the wrong behaviour because you have removed the indicator applet; it's using the system tray, with the behaviour from upstream. Add Indicator Applet back to your panel, log out, log in and it should work nicely with the functionality that was added in Ubuntu.

In other words: It's not a bug, it's a feature! :)

Sincerely, I hate unnecessary icons that clog up my system tray. That's why I kick them out as many as possible. Now you're telling me I have to allow two unnecessary icons (Indicator Applet and keyboard icon) just to get the layout code? Now that's what I call a horrible idea.

P.S. The reason I don't use the Indicator Applet is that I don't use Evolution and I don't use Empathy. I've uninstalled both of them. The added value of these "improvements" for me is zero. :(

---

