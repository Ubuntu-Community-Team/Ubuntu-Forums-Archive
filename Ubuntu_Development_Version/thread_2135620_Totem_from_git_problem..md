---
title: "Totem from git problem."
date: 2013-04-14
forum: Ubuntu Development Version
---

### Post by crf on 2013-04-14
I tried building totem from gnome's git repository. It seemed to build fine. I also built from git grilo and grilo plugins.
When I run Totem I get an error.

```
GLib-GIO-ERROR **: Settings schema 'org.freedesktop.Tracker.FTS' does not contain a key named 'min-word-length'
```

The environment has set GRL_PLUGIN_PATH=/usr/local/lib64/grilo-0.2

////

I'm a bit confused about this error. There wasn't much I could find out about it. Just [this commit message]("https://mail.gnome.org/archives/commits-list/2013-February/msg04153.html") Is it a problem with totem, or tracker?

---

### Post by mc4man on 2013-04-14
Don't see any issue here (on a gnome3 ppa + some extra install),  **if tracker isn't installed.**
If tracker is installed then it does cause the crash. Seems like a bug but the problem may be on the Ubuntu (ppa) side. You should file one I guess.

If you wanted to keep totem git (3.9), & tracker then I'd go ahead & give it what it's looking for until fixed. (noting I am never too attached to any dev install..
Now i've no idea what the default should be for min. word length, or if the setting should exist,. (here I've no great use for tracker so not an issue.

So just an example -  use gksudo gedit if you'd rather
```
sudo nano /usr/share/glib-2.0/schemas/org.freedesktop.Tracker.FTS.gschema.xml
```

insert/paste this at bottom** as shown in screen** ("<key type=.. & </key>" should line up, not sure this forum will cooperate
  ```
    <key type="i" name="min-word-length">
      <default>3</default>
      <range min="0" max="200"/>
      <summary>Minimum length of a word to be indexed</summary>
      <description>Words with less characters than this length will be ignored by the indexer.</description>
    </key>
```
(then ctrl+o, enter, ctrl+x  if using nano


Then in terminal - 
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas
```

Should run without error,** if you get an error then correct**, there may be an unrelated warning
screen running no issue except a grilo  grl-upnp warning that's no interest here either

Ultimately better to get this fixed...

(also to note - I've found that make installs of totem are better if installed to /usr with totem packages removed first.

---

### Post by crf on 2013-04-16
Hi, thanks for all the help!

Your solution to add that key to the schema worked. So totem starts.

--
I made a bug report on gnome-buzilla ... It was decided invalid (rightly, I think).
[https://bugzilla.gnome.org/show_bug.cgi?id=698065](https://bugzilla.gnome.org/show_bug.cgi?id=698065)

---

### Post by mc4man on 2013-04-16
Then not sure here where the issue is, guess the added schema key is ok. I'd keep an eye on the gnome ppa's, see what happens when they offer a 3.8 or higher totem

If related to grilo it was decided to allow a while ago but as of yet never determined how to do so...
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1035701](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1035701)
leads to 
[https://bugs.launchpad.net/ubuntu/+source/grilo/+bug/1116098](https://bugs.launchpad.net/ubuntu/+source/grilo/+bug/1116098)

---

### Post by crf on 2013-04-16
I think the problem was an incompatibility caused by that gsettings key name removal between tracker 0.14 and 0.16.
If I remove all the 0.14 tracker packages, leaving just the 0.16 packages, totem runs ok. (no need to edit the schema and glib-compile-schemas)

I download the 0.14 tracker source from ubuntu, and references abound to that min-word-length gsettings key name.

Probably the packages should conflict with one another, but you can have tracker 0.14 and 0.16 installed at the same time.

---

### Post by mc4man on 2013-04-16
Makes sense -  (I think
When I was testing out here the only tracker prepackaged for this install was from the gnome3 ppa - tracker-0.15.4-0ubuntu1~raring1 which exhibits the issue with git totem.
So hopefully the ppa will go to 0.16 when they offer a new totem (probably totem-3.8 release, I never tested that source with the 0.15 tracker to see if it's affected

At the end of the day if one wants grilo support better atm to do one's own build.

(curious - do you have any issue with the totem-mozilla plugin when building to /usr/local?

(- also here I've decided for the moment to go with gst-1.1, for convenience the gnome3 experimental offers packages, the libav plugin uses a self contained libav source, probably 0.9, so doesn't need the current shared libav libs in 13.04
[https://launchpad.net/~ricotz/+archive/experimental](https://launchpad.net/~ricotz/+archive/experimental)

---

### Post by crf on 2013-04-17
Since you asked ...

I notice that there is a *lack* of plugins showing in mozilla when they are installed to the default /usr/local/lib/mozilla/plugins.

If I export MOZ_PLUGIN_PATH=/usr/local/lib/mozilla/plugins and run firefox, then the plugins show up.
If I create a directory ~/.mozilla/plugins/ and copy the plugins to that directory, then firefox also finds them.

(I'm not much of multimedia-on-the-web person. So I never noticed the lack of plugins. It's odd that firefox doesn't search the path where by default the totem plugins are installed.)

I guess you're asking about whether they work to watch video on the web? They did *try* to work, but mostly failed. I'm not sure whether these are real errors, or mistakes/oversights I made while building totem.

This video failed at first when I clicked on it, then succeeded (it played).
[http://movies.apple.com/media/us/findouthow/macosx/2009/apple-findouthow-macosx-anatomy_of_a_mac-cc-us-20120130_r848-10scie.mov?width=640&height=400](http://movies.apple.com/media/us/findouthow/macosx/2009/apple-findouthow-macosx-anatomy_of_a_mac-cc-us-20120130_r848-10scie.mov?width=640&height=400)

This video failed to play
[http://www.break.com/video/tony-gwynn-jr-owns-heckler-2433694/](http://www.break.com/video/tony-gwynn-jr-owns-heckler-2433694/)

---

### Post by mc4man on 2013-04-17
Was mainly asking whether it (browser plugin), worked without add. steps when installed to /usr/local.  I've found it doesn't so the reason why I install to /usr where it's all good OOTB

In any event the 1st. link was ok here, both in browser or in totem. The 2nd one is flash & again is ok as expected. (plugin in /usr

---

