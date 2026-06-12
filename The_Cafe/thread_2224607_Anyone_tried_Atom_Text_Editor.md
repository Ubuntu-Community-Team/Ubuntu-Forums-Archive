---
title: "Anyone tried Atom Text Editor?"
date: 2014-05-17
forum: The Cafe
---

### Post by vasa1 on 2014-05-17
Supposed to be very similar to Sublime:
[http://www.webupd8.org/2014/05/atom-text-editor-ubuntu-ppa-update.html](http://www.webupd8.org/2014/05/atom-text-editor-ubuntu-ppa-update.html)

but it's only available as 64-bit.

---

### Post by nick-featch on 2014-05-17
Yep. I've been using it all week and I'm impressed. You'll have to install some extra packages like project-manger if you want to mimic all of sublimes features for now [https://atom.io/packages/search?q=project-manger](https://atom.io/packages/search?q=project-manger) 

Its stable, has good Git intergration and supports many lanuages [https://atom.io/packages/search?utf8=%E2%9C%93&q=language](https://atom.io/packages/search?utf8=%E2%9C%93&q=language). 

I really like the Monokai theme. Also recommend adding the Autocomplete Plus package.

You should have play if you haven't already?

Oh it trims whitespace by default. You may wish to look up that package and switch it off or use something like [https://github.com/zhengjia/rstrip](https://github.com/zhengjia/rstrip) to "fix" you're project in a single commit.

---

### Post by pqwoerituytrueiwoq on 2014-05-17
I just wanted to say thank you for making this thread
this editor seems to be awesome i just tried it out, have not really done any real work with it yet but so far i really like it, i have been using geany till now wishing it had better syntax highlighting, especially handling in-line JS in HTML files
[[IMG]http://www.zimagez.com/miniature/screenshot-05172014-015551pm.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-05172014-015551pm.php")
the santax higlighting is great even handles regex in js
i installed the autocomplete plus and auto complete paths addon and disabled them and cant seem to enable them
when ever i hit / it opened a bottom panel
edit: re-enabled them by editing .atom/config.cson
it is no longer opening that bottom panel web inspector anymore, no idea why it was opening on me

also grabed the color picker addon, seems it was made for a mac keyboard
is there a way to press a "cmd" key on a windows keyboard?

---

### Post by vasa1 on 2014-05-17
> **pqwoerituytrueiwoq said:**
> ... i have been using geany till now wishing it had better syntax highlighting, especially handling in-line JS in HTML files
[[IMG]http://www.zimagez.com/miniature/screenshot-05172014-015551pm.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-05172014-015551pm.php")
...
Can you upload (pastebin an html file that has in-line js). It's possible you may get better results with another colorscheme (theme). Some are here: [https://github.com/kugel-/geany-themes](https://github.com/kugel-/geany-themes).

Re. the rest, I haven't installed Atom as yet but hope to do so soon. I'm interested in the markdown preview option. 

Linux Action Show looked at Atom at around 6:15 into this video: [https://www.youtube.com/watch?v=9YQpwoxBAY8](https://www.youtube.com/watch?v=9YQpwoxBAY8)

---

### Post by pqwoerituytrueiwoq on 2014-05-17
> **vasa1 said:**
> Can you upload (pastebin an html file that has in-line js). It's possible you may get better results with another colorscheme (theme). Some are here: [https://github.com/kugel-/geany-themes](https://github.com/kugel-/geany-themes).

Re. the rest, I haven't installed Atom as yet but hope to do so soon. I'm interested in the markdown preview option. 

Linux Action Show looked at Atom at around 6:15 into this video: [https://www.youtube.com/watch?v=9YQpwoxBAY8](https://www.youtube.com/watch?v=9YQpwoxBAY8)
i think you miss read that, was saying it was better in atom, but the lack of highlight +mid click to copy/paste is getting on my nerves
[[img]http://www.zimagez.com/miniature/screenshot-05172014-113414pm.php[/img]](http://www.zimagez.com/zimage/screenshot-05172014-113414pm.php)

---

### Post by nick-featch on 2014-05-18
Alt should be the same as Cmd but doesn't seem to always work and I can confirm its not for Color Picker. Hmmm maybe Unity's HUD is interferring this can be configured [http://askubuntu.com/questions/151951/how-do-i-prevent-ubuntu-from-capturing-the-alt-key-to-show-the-hud](http://askubuntu.com/questions/151951/how-do-i-prevent-ubuntu-from-capturing-the-alt-key-to-show-the-hud)

If you select a package and click the "Open in Atom" button you can change the keymap to something like "ctrl-alt-c". I think you need to restart Atom for that change to take effect. Also if the package is updated you'll need to apply your change again.

Looks like the middle click issue is going to fixed soon - [https://github.com/atom/atom/issues/2244](https://github.com/atom/atom/issues/2244)

---

### Post by pqwoerituytrueiwoq on 2014-05-18
it cant be unity messing with it here, i am using xfwm4

---

### Post by nick-featch on 2014-05-18
Oh right sorry.

---

### Post by hyperreal on 2014-05-22
I've tried it.  It's a nice, clean editor with a beautiful user interface, but configuration is too cumbersome and insufficient for my preferences.

---

### Post by HiImTye on 2014-05-22
I like vim, which supports all the features of Atom

---

### Post by pqwoerituytrueiwoq on 2014-05-22
anyone know how to get this feature?
[[img]http://www.zimagez.com/miniature/screenshot-05222014-082104am.php[/img]](http://www.zimagez.com/zimage/screenshot-05222014-082104am.php)

---

### Post by Habitual on 2014-05-22
> **vasa1 said:**
> Supposed to be very similar to Sublime:
[http://www.webupd8.org/2014/05/atom-text-editor-ubuntu-ppa-update.html](http://www.webupd8.org/2014/05/atom-text-editor-ubuntu-ppa-update.html)

but it's only available as 64-bit.
Yes, but does it **print**?

---

### Post by PartisanEntity on 2014-05-23
I heard about it recently at an event called Codefront.io, would like to try it out.

---

### Post by sethj3 on 2014-05-24
Did anyone have any issues installing it? I had [a few]("http://ubuntuforums.org/showthread.php?t=2225314d") relating to the version of nodejs I had.  

Other than that, it looks pretty cool!

---

### Post by sethj3 on 2014-05-24
> **HiImTye said:**
> I like vim, which supports all the features of Atom

Atom has a vim plugin :P  

> **Habitual said:**
> Yes, but does it **print**?

Hm, you know, I can't find a print option.. I'm sure it will be added eventually, atom is still heavily in development.

---

### Post by Habitual on 2014-05-24
> **sethj3 said:**
> I can't find a print option.
Bummer.

---

### Post by mcduck on 2014-05-27
I've been using Atom for a while now, and I really like it apart from couple of small issues (some of which I can live with, and some which actually seriously limit how useful it is for my work).

Lack of primary selection to copy/paste is of course annoying, and print support would be quite useful. But the big issue I'm having is that it doesn't seem to handle editing on files mounted through GVFS correctly, and actually behaves in destructive way if I even try doing that. So, I can't use it to directly edit files on web servers, mounted through the file manager's FTP connection, for some reason trying to save the file causes Atom to throw an error, open the inspector panel, and delete all contents of the file. So I can still use it for editing local files, but majority of my coding is about editing and updating files on FTP servers and I still need to use Gedit for those...

...and the startup time is a bit annoying, although that isn't a big deal for me as I'm not constantly opening and closing the editor anyway.

Hopefully all the issues will get sorted out over time, as otherwise I'm really enjoying using Atom and the plugins and relatively easy customization options thanks to web technologies make it my favourite editor this far.

---

### Post by Habitual on 2014-05-27
SublimeText2 has a pretty neat feature:
I can open more than a "few" new tabs and have stuff in each one.
I can close the editor and re-open and all the tabs' content remains, even if unsaved.
It's the "perfect" scratch pad editor.

Aside from the lack of printing support, I see no reason to change.

---

### Post by kyle20 on 2014-05-29
> **hyperreal said:**
> I've tried it.  It's a nice, clean editor with a beautiful user interface, but configuration is too cumbersome and insufficient for my preferences.
I second that! After playing around with it for the last 2 hours, I think i will stick with Sublime

---

### Post by hwindle83 on 2014-06-10
I would try it, but I'm too used to Vim and I built myself a text editor called Jotter anyway, so I just use that. I think I had an invite but then I promptly lost the email somewhere.

---

