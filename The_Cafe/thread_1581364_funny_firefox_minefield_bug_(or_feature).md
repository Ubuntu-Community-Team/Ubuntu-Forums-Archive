---
title: "funny firefox minefield bug (or feature?)"
date: 2010-09-24
forum: The Cafe
---

### Post by Dustin2128 on 2010-09-24
was just looking for a minefield compatible speed dial addon (they really should integrate one into vanilla ffox anyway) when I came across this :) Which is odd, considering that a number of my addons are minefield compatible.

---

### Post by cgroza on 2010-09-24
I guess this will be fixed when it will be officially released.

---

### Post by Dustin2128 on 2010-09-24
> **cgroza said:**
> I guess this will be fixed when it will be officially released.
more likely with beta 7. The betas usually have a decent addon library.

---

### Post by lovinglinux on 2010-09-24
I have been using Firefox 4 since the first beta, including pre versions from nightly and I never came across such issue. I have more than 60 extensions installed and update and install extensions almost on a daily basis.

So I guess it could be a bug in AMO site or a problem with your Firefox user agent string. 

Type **about[noparse]:[/noparse]support** in the address bar, then copy the User Agent string and post it here. It should look like this:

```
Mozilla/5.0 (X11; Linux i686; rv:2.0b7pre) Gecko/20100923 Firefox/4.0b7pre
```

---

### Post by Dustin2128 on 2010-09-24
```
Mozilla/5.0 (X11; Linux i686; rv:2.0b7pre) Gecko/20100924 Firefox-4.0/4.0b7pre Ubuntu/10.04
```

---

### Post by lovinglinux on 2010-09-24
> **Dustin2128 said:**
> ```
Mozilla/5.0 (X11; Linux i686; rv:2.0b7pre) Gecko/20100924 Firefox-4.0/4.0b7pre Ubuntu/10.04
```

It's a bug that affects only the Ubuntu version of Firefox 4 due to some User Agent string incompatibility. I just tested your string with User Agent Switcher and I got the same error message about downloading Firefox.

To fix that, install [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/59/") and change the User Agent to:

```
Mozilla/5.0 (X11; Linux i686; rv:2.0b7pre) Gecko/20100923 Firefox/4.0b7pre
```

Another option would be to get Firefox 4 from Mozilla, which works perfectly.

---

### Post by Dustin2128 on 2010-09-24
> **lovinglinux said:**
> It's a bug that affects only the Ubuntu version of Firefox 4 due to some User Agent string incompatibility. I just tested your string with User Agent Switcher and I got the same error message about downloading Firefox.

To fix that, install [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/59/") and change the User Agent to:

```
Mozilla/5.0 (X11; Linux i686; rv:2.0b7pre) Gecko/20100923 Firefox/4.0b7pre
```Another option would be to get Firefox 4 from Mozilla, which works perfectly.
mk, thanks. Do you aspire to be a core firefox developer or something?

EDIT: OK, this calls for an...
[IMG]http://static.frysforum.com/at/20090727002827780196-0-epic-fail.jpg[/IMG]

---

### Post by lovinglinux on 2010-09-24
> **Dustin2128 said:**
> mk, thanks. Do you aspire to be a core firefox developer or something?

No, that is out of my league. I'm just a Firefox fan who likes to develop extensions for it.

---

### Post by lovinglinux on 2010-09-24
> **Dustin2128 said:**
> EDIT: OK, this calls for an...

Get [Addon Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/15003/"). It is an essential tool for Firefox beta testers. It will allow to install User agent Switcher and any incompatible extension, since it disables compatibility check. Keep in mind some extensions will fail even when installed properly, due to incompatibility in the code itself. User agent Switcher works fine tho.

---

