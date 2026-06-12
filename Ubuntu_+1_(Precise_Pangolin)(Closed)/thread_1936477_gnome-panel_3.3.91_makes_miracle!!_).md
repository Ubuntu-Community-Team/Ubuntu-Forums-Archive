---
title: "gnome-panel 3.3.91 makes miracle!! :)"
date: 2012-03-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by tista on 2012-03-06
Really thanks jbicha and Peter Hurley!  (LP: #828392)...

Today finally we could control gnome-panel's appearance almost perfectly!
Now it seems to be slaved theme settings, Yeah we had some ugly experiences on gtk3 gnome-panel theming, but it almost fixed... So cool. :)

It must help the "Classic session" lovers abviously.

Regards,
Tista

---

### Post by lucazade on 2012-03-06
> **tista said:**
> Really thanks jbicha and Peter Hurley!  (LP: #828392)...

Today finally we could control gnome-panel's appearance almost perfectly!
Now it seems to be slaved theme settings, Yeah we had some ugly experiences on gtk3 gnome-panel theming, but it almost fixed... So cool. :)

It must help the "Classic session" lovers abviously.

Regards,
Tista

gnome-panel3 porting was a disaster.. don't think that theme fixes could change my opinion. Still full of glitches and artifacts, random grey boxes on session logout..

---

### Post by tista on 2012-03-06
> **lucazade said:**
> gnome-panel3 porting was a disaster.. don't think that theme fixes could change my opinion. Still full of glitches and artifacts, random grey boxes on session logout..

Ohh pity... :(

Really? Needed more love? ;)

Cheers,
Tista

---

### Post by lucazade on 2012-03-06
> **tista said:**
> Ohh pity... :(

Really? Needed more love? ;)

Cheers,
Tista

yep.. i'd say rewrite from scratch..  :)
or simply help slickpanel project:
[http://whyareyoureadingthisurl.wordpress.com/category/programming/vala/](http://whyareyoureadingthisurl.wordpress.com/category/programming/vala/)

---

### Post by jbicha on 2012-03-06
There's a bit more theme work to be done in light-themes itself. You can track the same [bug]("http://pad.lv/828392").

---

### Post by anewguy on 2012-03-07
Hey, I'm new to this, so forgive me if I'm asking something stupid!  There is a group of users using Gnome Shell who want an application to update the gnome-shell.css file so they don't have to hit or miss through an editor.

I've started work on the project, using basic C and GTK.  One of the users noticed this thread and wondered if it's the app they are looking for.  I did follow the link to slickpanel and not being familiar with this I'm not sure exactly what it is doing.

So.........here comes the dumb question part.........is the gnome-panel being talked about here and in the slickpanel page the same as the gnome-shell.css file used by Gnome Shell?

If so, I could stop my crude efforts and perhaps look at one of these 2 tools to see what is being talked about and how it will work for them.

Thanks in advance!
Dave ;)

---

### Post by lucazade on 2012-03-07
> **anewguy said:**
> Hey, I'm new to this, so forgive me if I'm asking something stupid!  There is a group of users using Gnome Shell who want an application to update the gnome-shell.css file so they don't have to hit or miss through an editor.

I've started work on the project, using basic C and GTK.  One of the users noticed this thread and wondered if it's the app they are looking for.  I did follow the link to slickpanel and not being familiar with this I'm not sure exactly what it is doing.

So.........here comes the dumb question part.........is the gnome-panel being talked about here and in the slickpanel page the same as the gnome-shell.css file used by Gnome Shell?

If so, I could stop my crude efforts and perhaps look at one of these 2 tools to see what is being talked about and how it will work for them.

Thanks in advance!
Dave ;)

Slickpanel is similiar to gnome-panel or xfce4-panel but written in Vala and using Gtk3.. it provides a classic taskbar and an indicator area. 
Unfortunately it is a young project and developed only by a single guy so it is still not mature...  but it is really promising!
It is a fork of wingpanel used in ElementaryOS plus a configuration tool.. too bad I don't know Vala so I'm not able to help him.

---

### Post by anewguy on 2012-03-07
Okay, thanks for the explanation!  Sounds like something I may look into later - although I must ask how this toolbar and indicator area differ from that provided by the gnome-shell package? 

For now, I guess I'll continue on with my program as well.

Thanks again!

Dave ;)

---

### Post by NHclimber on 2012-03-20
> **lucazade said:**
> gnome-panel3 porting was a disaster.. don't think that theme fixes could change my opinion. Still full of glitches and artifacts, random grey boxes on session logout..

"Random grey box on logout" fixed in latest upstream along with being able to theme vertical panels properly.

I'm not trying to minimize the effort that must have gone into porting gnome-panel to gtk+3;  clearly herculean effort was necessary.  At this point though, many of the "glitches and artifacts" are theme, theming engine and gtk+ bugs:

Transparent window list buttons -> [https://bugs.launchpad.net/light-themes/+bug/926490](https://bugs.launchpad.net/light-themes/+bug/926490)
Transparent show desktop button -> [https://bugs.launchpad.net/light-themes/+bug/923788](https://bugs.launchpad.net/light-themes/+bug/923788)
(Fix Released) Border artifact around window list and notification area -> [https://bugs.launchpad.net/light-themes/+bug/920843](https://bugs.launchpad.net/light-themes/+bug/920843)
(Fix Released) Icons cropped in show desktop button and window list -> [https://bugs.launchpad.net/light-themes/+bug/926487](https://bugs.launchpad.net/light-themes/+bug/926487)
Handle not rendered properly -> [https://bugs.launchpad.net/light-themes/+bug/920832](https://bugs.launchpad.net/light-themes/+bug/920832)[INDENT]** this is actually a unico engine bug but the dev refuses to acknowledge it -- wait until gtk+ containers start implementing the css box model and this is going to be right back in the unico engine **
[/INDENT](Fix Released) Bluetooth icon doesn't show up in indicator-applet-complete/Bluetooth-applet not autostarted -> [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/924098](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/924098)
(Fix Released) Separator not themed -> [https://bugs.launchpad.net/light-themes/+bug/945644](https://bugs.launchpad.net/light-themes/+bug/945644)
Style classes persist after being removed -> [https://bugzilla.gnome.org/show_bug.cgi?id=671565](https://bugzilla.gnome.org/show_bug.cgi?id=671565)
Sizing cache doesn't account for style changes -> [https://bugzilla.gnome.org/show_bug.cgi?id=672197](https://bugzilla.gnome.org/show_bug.cgi?id=672197)
gtk_widget_reset_style rebuilds paths prematurely -> [https://bugzilla.gnome.org/show_bug.cgi?id=672088](https://bugzilla.gnome.org/show_bug.cgi?id=672088)

GTK+ 3.3 contains a massive overhaul of CSS style providers which includes fixes for state changes: [http://git.gnome.org/browse/gtk+/commit/?id=899a381d31fa8f94466bc38e4d77a7f0d9498b9f](http://git.gnome.org/browse/gtk+/commit/?id=899a381d31fa8f94466bc38e4d77a7f0d9498b9f)

What makes working on gnome-panel truly painful is:
a) integration with everything
b) the deep widget hierarchy previously necessary to implement all the little tweaks and interfaces
c) no tool to explore window/widget hierarchy and properties - this is a major shortcoming of gtk development

To my mind what still needs to be done is:
a) Fix random applet crashes on startup (what bug # is this?)  I haven't had this happen in a while -- I wonder if it was related to this fix -> [http://git.gnome.org/browse/gnome-panel/commit/?id=1f7748b4b91ee45d4e3eb65e7cd177afdd39681d](http://git.gnome.org/browse/gnome-panel/commit/?id=1f7748b4b91ee45d4e3eb65e7cd177afdd39681d)
b) Back out a local gtk+ patch and see if that's what fixes the icon/text overlap in the window list buttons -- this doesn't happen on my dev machine anymore
c) Expose mechanism to effectively theme the notification-area (like padding around/between icons)
d) Add configuration/ui for text rotation for vertical panels
e) Fix dragging empty panels
f) Fix Launcher animation
g) Add a better icon than "mail-message-new" to notification-daemon

Anything else?

---

### Post by jbicha on 2012-03-20
@NHClimber, wow, that's an epic post with the number of bug links you  posted. You probably should remove the Fix Released bugs though to make  it easier for readers to scan through.

> **NHclimber said:**
> 
 What makes working on gnome-panel truly painful is:
 c) no tool to explore window/widget hierarchy and properties - this is a major shortcoming of gtk development
 
Well, of course gnome-shell has looking glass (Alt-F2, lg, then click the eyedropper) which is such a tool.

> **NHclimber said:**
> 
  To my mind what still needs to be done is:
  a) Fix random applet crashes on startup (what bug # is this?)  I haven't  had this happen in a while -- I wonder if it was related to this fix  -> [http://git.gnome.org/browse/gnome-panel/commit/?id=1f7748b4b91ee45d4e3eb65e7cd177afdd39681d](http://git.gnome.org/browse/gnome-panel/commit/?id=1f7748b4b91ee45d4e3eb65e7cd177afdd39681d)
  b) Back out a local gtk+ patch and see if that's what fixes the  icon/text overlap in the window list buttons -- this doesn't happen on  my dev machine anymore
  c) Expose mechanism to effectively theme the notification-area (like padding around/between icons)
  d) Add configuration/ui for text rotation for vertical panels
  e) Fix dragging empty panels
  f) Fix Launcher animation
  g) Add a better icon than "mail-message-new" to notification-daemon


a. Good if things don't crash now! :)
c. Of course, we use indicators by default now instead of the notification area, partly because the notification area is so terrible. Fixing this would be nice for all the other distros like Debian which won't use indicators by default.
d. That never existed for gnome-panel 2 either, right?
g. Why notification-daemon and not notify-osd?

---

### Post by lucazade on 2012-03-20
> **NHclimber said:**
> "Random grey box on logout" fixed in latest upstream along with being able to theme vertical panels properly.
...

@NHclimber

woa! thanks for the answer..well, I was critical because I spent a lot of time helping Cimitan to create Ambiance/Radiance themes and unfortunately panel was really hard to theme decently.

Now I have to admit that things improved a lot.
Going to check every bug report you posted to see if you covered everything :)

---

### Post by dino99 on 2012-03-20
> **jbicha said:**
> 
Well, of course gnome-shell has looking glass (Alt-F2, lg, then click the eyedropper) which is such a tool.

Looks like GS is in standby, still waiting  3.3.90-0ubuntu2 as you have written some days ago on an other thread of yours.

---

### Post by NHclimber on 2012-03-20
> **jbicha said:**
> You probably should remove the Fix Released bugs though to make  it easier for readers to scan through.
Ok, I edited the post and marked them as (Fix Released).

> **jbicha said:**
> Well, of course gnome-shell has looking glass (Alt-F2, lg, then click the eyedropper) which is such a tool.
I know -- but I wish LookingGlass had been efforted as a standalone; it's not useful for what's needed here.

> **jbicha said:**
> a. Good if things don't crash now! :)
Yup :)  But I also don't like bugs to mysteriously disappear without knowing why.

> **jbicha said:**
>  c. Of course, we use indicators by default now instead of the notification area, partly because the notification area is so terrible. Fixing this would be nice for all the other distros like Debian which won't use indicators by default.
Even in ubu, some things don't use indicators. Eg, UPS status is not shown in applet-indicator-complete, only via notifications.

> **jbicha said:**
>  d. That never existed for gnome-panel 2 either, right?
Right. The underlying code to actually do the text rotation either way is there (same in indicator-applet-complete).  It's just not exposed to be configurable and there's no api for applets to query what the current state should be.

> **jbicha said:**
>  g. Why notification-daemon and not notify-osd?
The icon displayed in the NaTray is actually supplied by the app via a status icon (gtk wraps the X protocol with the GtkStatusIcon api - [http://developer.gnome.org/gtk3/stable/GtkStatusIcon.html](http://developer.gnome.org/gtk3/stable/GtkStatusIcon.html)); in this case, notification-daemon supplies "mail-message-new" which is a somewhat random choice, mostly because no better choices exist. I have no idea what notify-osd uses.

---

### Post by NHclimber on 2012-03-20
> **lucazade said:**
> @NHclimber

woa! thanks for the answer..well, I was critical because I spent a lot of time helping Cimitan to create Ambiance/Radiance themes and unfortunately panel was really hard to theme decently.

Now I have to admit that things improved a lot.
Going to check every bug report you posted to see if you covered everything :)
I'm ok with you criticizing gnome-panel -- or really anything else too :)

You should hear me swearing on my 30th logout/login cycle to see if the most recent effort worked -- or how hard I type my login password on that 30th login :)

Most things right now are hard to theme properly because the box model hasn't really been implemented in most containers.  Eg, the NaTray padding would be trivial if GtkAlignment or GtkBox or GtkGrid implemented the CSS box model.  Without that, a bunch of subclassing code ends up being the least hacky.  But GtkAlignment is not really coded to be subclassed (ie, it doesn't expose an interface designed to be used specifically by derived classes), so an alternative implementation using CSS style properties is about the same amount of code. Which is wasted effort in an application and should just be done in the base library as part of the overall migration plan. Which is why I'm trying to find out what that plan is .... [http://mail.gnome.org/archives/gtk-devel-list/2012-March/msg00058.html](http://mail.gnome.org/archives/gtk-devel-list/2012-March/msg00058.html)

FYI - I guarantee I haven't covered everything -- I can see there's been a bunch of regressions in Precise (like with the text color). Feel free to post links here in this thread to bugs you feel need to get address wrt gnome-panel.  I'll at least look at them.

---

### Post by lucazade on 2012-03-27
@NHclimber

Checked your bug list and it is correct.. I've some other bugs to report.

1) Sound volume applet present in notification area.. this is a duplicate becuase we already use indicator-sound by default:
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/965288](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/965288)

2) Battery icon present in notification area.. this is a duplicate becuase we already use indicator-power by default:
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/965279](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/965279)

3) The indicator applet appears with just some up and down scroll arrows, and I have to scroll down before it fills in and shows the 3 items, and then the scroll arrows disappear:
[https://bugs.launchpad.net/indicator-applet/+bug/965953](https://bugs.launchpad.net/indicator-applet/+bug/965953)

4) When adding the main menu applet to the bottom panel (not the menu bar, just the icon) the taskbar list of open apps have cropped icons inside buttons.
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/965969](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/965969)

5) Nautilus creates two buttons on the taskbar:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/965974](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/965974)

---

### Post by NHclimber on 2012-03-27
> **lucazade said:**
> @NHclimber

Checked your bug list and it is correct.. I've some other bugs to report.

1) Sound volume applet present in notification area.. this is a duplicate becuase we already use indicator-sound by default:
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/965288](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/965288)

2) Battery icon present in notification area.. this is a duplicate becuase we already use indicator-power by default:
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/965279](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/965279)

3) The indicator applet appears with just some up and down scroll arrows, and I have to scroll down before it fills in and shows the 3 items, and then the scroll arrows disappear:
[https://bugs.launchpad.net/indicator-applet/+bug/965953](https://bugs.launchpad.net/indicator-applet/+bug/965953)

4) When adding the main menu applet to the bottom panel (not the menu bar, just the icon) the taskbar list of open apps have cropped icons inside buttons.
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/965969](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/965969)

5) Nautilus creates two buttons on the taskbar:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/965974](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/965974)

Good finds -- I'll go through the list, repro them, and confirm the bugs.

ISTR the nautilus two-button-bug in the tasklist being a gnome-panel bug -- notice how it eventually times out and disappears.  I could be wrong here, though -- maybe it's related to that gedit bug when run as root where the 2nd blank file appears and doesn't go away on it's own ;)

To that list, I can add this:
Transparent panels aren't transparent -- at least, not completely
[https://bugs.launchpad.net/gnome-panel/+bug/966697](https://bugs.launchpad.net/gnome-panel/+bug/966697)

I filed it against gnome-panel because that's where it's most obvious but it's actually a GTK 3.4 bug just recently introduced which completely breaks how gnome-panel simulates a transparent background. Fun stuff :/

Especially thanks for suggesting some solutions in those bug reports -- I'll try those too!

---

