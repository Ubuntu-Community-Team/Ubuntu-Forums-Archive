---
title: "Apps not showing in Ubuntu bar?"
date: 2009-07-01
forum: Wine
---

### Post by X_Splinter on 2009-07-01
Hi there.

I restore Wine to its default settings and now every time i isntall something via Wine the app dont show in the ubuntu bar - wine - programs -

Why?

What should i do?

---

### Post by ackanao on 2009-07-01
Hi X_Splinter

I think this solves your problem:

[http://wiki.winehq.org/FAQ#head-34c8b5d78823a60c9651b4c9848c06a1aa8fea48]("http://wiki.winehq.org/FAQ#head-34c8b5d78823a60c9651b4c9848c06a1aa8fea48")

---

### Post by X_Splinter on 2009-07-01
> **ackanao said:**
> Hi X_Splinter

I think this solves your problem:

[http://wiki.winehq.org/FAQ#head-34c8b5d78823a60c9651b4c9848c06a1aa8fea48]("http://wiki.winehq.org/FAQ#head-34c8b5d78823a60c9651b4c9848c06a1aa8fea48")

Hi there.

I have the wine bar with programs folder showing.
The thing is that it does not update its self.

Any ideas?

I even try the menu edtion, but the application are not there.
It is like Wine do not put shortcuts of the installed app folder on the bar

---

### Post by X_Splinter on 2009-07-06
Any information could be useful

---

### Post by Augsburg on 2009-07-06
You can do it manually-

System > Preferences > Main Menu

---

### Post by ackanao on 2009-07-06
GoTo "~/.config/menus" folder and open "applications.merged" file; To make app menus visible again, delete <Deleted/> tag. Or delete everything related to Wine and just leave:

```
	<Menu>
		<Name>wine-wine</Name>
	</Menu>
```

Goto "applications-merged" folder and delete any files related to your app. Then try to install that app again.

---

### Post by X_Splinter on 2009-07-06
Ok I got it. It should do for the future applications

Thanks

---

### Post by ackanao on 2009-07-06
I'm glad I was able to help.

Cheers,
ackanao

---

