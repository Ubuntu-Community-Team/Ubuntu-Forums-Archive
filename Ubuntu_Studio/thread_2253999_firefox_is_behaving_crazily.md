---
title: "firefox is behaving crazily"
date: 2014-11-24
forum: Ubuntu Studio
---

### Post by woodsyboredom on 2014-11-24
running 14.04 on an older dell xps desktop. i use google chrome for my web browser but i have some .swf files that only play on a html flash player in firefox. since upgrading, firefox won't open properly. when i try to open firefox it just keeps opening new tabs very quickly and it reopens itself when i closes it and goes right on opening tabs. i have to close it several tines before it stops. i've uninstralled and reinstalled firefox to no effect. can anyone help by either helping me fix firefox or helping to figure out how play .swf files on chrome?

thanks

---

### Post by flaymond on 2014-11-24
I believe that chrome got it own flash player add-on...try it

---

### Post by tgalati4 on 2014-11-24
There is both debug and safe-mode switches that you can use.  It's possible you have a plug-in that is not working with the newest version.  Open a terminal:

```
firefox -safe-mode
```

or

```
firefox --debug
```

Try renaming the video file with *.flv and open with *vlc*.

---

### Post by pfeiffep on 2014-11-25
> **woodsyboredom said:**
> running 14.04 on an older dell xps desktop. i use google chrome for my web browser but i have some .swf files that only play on a html flash player in firefox. since upgrading, firefox won't open properly. when i try to open firefox it just keeps opening new tabs very quickly and it reopens itself when i closes it and goes right on opening tabs. i have to close it several tines before it stops. i've uninstralled and reinstalled firefox to no effect. can anyone help by either helping me fix firefox or helping to figure out how play .swf files on chrome?

thanksFire Fox has a setting "show my windows and tabs from last time"  This is a selectable item reached from Preferences | General Tab | Startup
Perhaps yours is set incorrectly for your preferences. The other 2 options are:
1) Show a blank page
2) show my home page.

---

### Post by kurt18947 on 2014-11-25
You could also delete the /home/.mozilla folder. This will also delete your bookmarks, extensions (I think) and any other customization so be sure you're not deleting anything difficult to replace.   Aother trick I've used when I suspect something funky in Firefox or any other app is to create a temporary user.  If a problem exists in a normal  user account but not in the temporary user's account you know the problem lies somewhere in the the normal user's home folder.

---

