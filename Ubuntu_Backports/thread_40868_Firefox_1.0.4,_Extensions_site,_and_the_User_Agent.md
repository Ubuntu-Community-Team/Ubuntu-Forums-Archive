---
title: "Firefox 1.0.4, Extensions site, and the User Agent String"
date: 2005-06-10
forum: Ubuntu Backports
---

### Post by thephotoman on 2005-06-10
Okay, here's the deal:

The user agent string in the build of Firefox in the Backport system is as follows:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.8) Gecko/20050526 Firefox/1.0 (Ubuntu package 1.0.4)

However, to access [http://addons.mozilla.org/](http://addons.mozilla.org/) (to get extensions), it needs to read as follows:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.8) Gecko/20050526 Firefox/1.0.4 (Ubuntu package 1.0.4)

in order to access the extensions site.  Of course, the User Agent Modifier exetnsion can handle the change, but to get it, the easiest way is to use the Addons site, which is inaccessable otherwise.

Could we get this fixed in the next version?  I mean, they did this because of the code execution problems in 1.0.3, but it makes life hard for UBP users.

---

### Post by jdong on 2005-06-11
You can also use about:config to make this change.

It's in every user's profile, so my package can't correct it.

---

### Post by DarkSilver on 2005-06-11
you can change it manually

1/ go to : about:config
2/ and change **general.useragent.vendorSub **to [b]1.0.4
[/b]3/ then, restart Firefox
4/ [https://addons.mozilla.org/](https://addons.mozilla.org/) will work

---

### Post by thephotoman on 2005-06-12
Yeah, found and did that.  Thanks for the tip, though, as it may come in handy for other people.

---

### Post by DarkSilver on 2005-06-13
[QUOTE=jdong]You can also use about:config to make this change.

It's in every user's profile, so my package can't correct it.[/QUOTE]
???
by default, there is nothing in the prejs.js about that !!
The deb package must have its own version in the default config... I don't understand why Firefox 1.0.4 has the vendorSub defined to 1.0 only ...

Why don't you do in your parckage something that do :
 ```
echo "user_pref("general.useragent.vendorSub", "1.0.4");" >> #FIREFOX_PROFILE_FOLDER#/prefs.js
```

---

### Post by jdong on 2005-06-13
[QUOTE=DarkSilver]???
by default, there is nothing in the prejs.js about that !!
The deb package must have its own version in the default config... I don't understand why Firefox 1.0.4 has the vendorSub defined to 1.0 only ...

Why don't you do in your parckage something that do :
 ```
echo "user_pref("general.useragent.vendorSub", "1.0.4");" >> #FIREFOX_PROFILE_FOLDER#/prefs.js
```[/QUOTE]
It's a no-no to touch /home/* from a .deb package.

---

### Post by DarkSilver on 2005-06-13
[QUOTE=jdong]It's a no-no to touch /home/* from a .deb package.[/QUOTE]

yes, i understand so : ```

Add to /etc/mozilla-firefox/pref/firefox.js:
pref("general.useragent.vendorSub", "1.0.4") 
``` (it is linked by /usr/lib/mozilla-firefox/defaults/syspref )

---

