---
title: "latex editor with quick preview?"
date: 2009-06-02
forum: The Cafe
---

### Post by afeasfaerw23231233 on 2009-06-02
Is there a latex editor software which provides quick preview?
An editor with the function like this online editor should meet all my needs 
[http://thornahawk.unitedti.org/equationeditor/equationeditor.php](http://thornahawk.unitedti.org/equationeditor/equationeditor.php)

I may not need those function buttons. 

Thanks

---

### Post by perce on 2009-06-02
With emacs you have two options: either you use a plug in called whizzytex, which compiles portions of the file "on the fly" so that you can see what you are typing in real time, or you can use a plugin called auctex which enables a key combination (Ctr-cc) to compile the file, and then you keep a viewer open on the file. The two plug are compatible.

However neither solution is completely optimal: whizzytex is often too slow to be helpful, and the other solution is also kind of slow, because you need to change window and refresh the file. I usually use the second solution.

---

### Post by mihai.ile on 2009-06-02
I am using gedit + gedit-latex-plugin and I just finished creating a live preview for it, if you don't have time to wait until the patch gets in main repository use the patched version from here: [http://openmindedbrain.info/gedit-latex-plugin-live-preview](http://openmindedbrain.info/gedit-latex-plugin-live-preview)

[IMG]http://openmindedbrain.info/sites/default/files/images/latex-preview.preview.png[/IMG]

Edit: This one uses a key combination to save+compile and update the preview automatically, so just edit the LaTeX file and use CTRL-ALT-7 from time to time (this shortcut works in my patched version)

Oh and also suports live preview when working on the imported files :D

---

### Post by meho_r on 2009-06-02
Thanks a lot, mihai007. Have you let people on latex-community forum know of it? If you haven't, I can mention it if you like. And this thing deserves to be on front pages if you ask me ;) Thanks again.

BTW, is there some kind of zoom?

---

### Post by mihai.ile on 2009-06-02
If you think it could be useful, well spread the world, no problem for me :)

---

### Post by meho_r on 2009-06-02
Of course it will be useful :D Will do ;)

As for zoom feature, does it exist or does not? If not, it'll be nice if possible to implement it.

---

### Post by perce on 2009-06-02
Mihai007,

your plugin looks interesting, and if it is faster than whizzytex it will be great. I'm looking forward for it to make into the standard gedit!

---

### Post by mihai.ile on 2009-06-02
it is possible, my proble is that I am concerned with usability and don't want to make the preview even smaller because of unuseful buttons (from som user's perspective) so it will need some usecases before adding this feature.

Oh by the way I submited the patch for gedit-latex-plugin, not gedit but still let's hope it makes it.

---

### Post by thisllub on 2009-06-02
GVim with the latex plugins is great.

\ll
\lv

There is your doc.

---

### Post by conehead77 on 2009-06-02
Im using Kile at the moment which lets you preview a selection or environment. But after reading this thread i will definately try gedit for my latex needs.

---

### Post by zika on 2009-06-02
> **conehead77 said:**
> Im using Kile at the moment which lets you preview a selection or environment. But after reading this thread i will definately try gedit for my latex needs.+1 Thank You very much!

---

### Post by monsterstack on 2009-06-02
Wow. This was unexpected. I shall certainly be using this. Thanks a lot!

---

### Post by Stefanie on 2009-06-02
Use latexmk. It's in the repos, you just run latexmk -pdf -pvc file.tex in a terminal and it will watch your .tex and .bib files for changes, and recompile when necessary. 

You can edit your document in your editor of choice and every time you save your changes the document will be recompiled.

---

### Post by zika on 2009-06-02
> **Stefanie said:**
> Use latexmk. It's in the repos, you just run latexmk -pdf -pvc file.tex in a terminal and it will watch your .tex and .bib files for changes, and recompile when necessary. 

You can edit your document in your editor of choice and every time you save your changes the document will be recompiled.
What a difference a day makes ... .) Cool again ... :) !

---

### Post by zika on 2009-06-04
> **mihai007 said:**
> I am using gedit + gedit-latex-plugin and I just finished creating a live preview for it, if you don't have time to wait until the patch gets in main repository use the patched version from here: [http://openmindedbrain.info/gedit-latex-plugin-live-preview](http://openmindedbrain.info/gedit-latex-plugin-live-preview)

[IMG]http://openmindedbrain.info/sites/default/files/images/latex-preview.preview.png[/IMG]

Edit: This one uses a key combination to save+compile and update the preview automatically, so just edit the LaTeX file and use CTRL-ALT-7 from time to time (this shortcut works in my patched version)

Oh and also suports live preview when working on the imported files :D
What happened with the site? I used Your SW yesterday but due to unfortinate crash of Jaunty (due to my over-tweaking it) I wanted to reinstall it (I've reinstalled whole system which is very uncommon for me, the damage was big enough) but site is unavailable ... ?

---

### Post by mihai.ile on 2009-06-04
The website is up and running right now...

---

### Post by zika on 2009-06-04
> **mihai007 said:**
> The website is up and running right now...
Cool! Loading ... Nothing ... :( Problem loading page ...
Made it! Thank You again for a great piece of LaTeX magic world ... :)

---

### Post by conehead77 on 2009-06-04
I played a little bit with the gedit latex plugin but the latex toolbar and build tools dont show when i open a .tex file. I need to make a new latex document and then open the file i want to edit.
Is this the normal behavior or am i doing something wrong?

---

### Post by mihai.ile on 2009-06-04
This issue has to do with the gedit-latex-plugin and not with the preview I made for it but, no, it's not normal. When I open .tex files the toolbar gets automatically. from the plugin webpage ([http://live.gnome.org/Gedit/LaTeXPlugin](http://live.gnome.org/Gedit/LaTeXPlugin)) you can get to bug reports, maybe you find something useful, if not try submitting a new one (try to start gedit from the terminal when opening the file, so you see the error)

Oh by the way: do you have spaces in the path? it could be this...

---

### Post by zika on 2009-06-04
> **conehead77 said:**
> I played a little bit with the gedit latex plugin but the latex toolbar and build tools dont show when i open a .tex file. I need to make a new latex document and then open the file i want to edit.
Is this the normal behavior or am i doing something wrong?
This kind of behavior happens to me when attributes of a .tex file are not "right". Due to last night's reinstall I have a bunch of files that were rescued from previous installation by copying to Vista partition and then copied back to Ubuntu partition after re-install. So, the have -rwxrwxrwx  1 zika zika   59189 2009-01-27 10:21 instead of -rw-r--r--  1 zika zika   203 2009-06-04 08:55 ... Maybe You have similar issue.

---

### Post by conehead77 on 2009-06-04
I reported the bug. When i work with new created .tex documents it seems to work just fine... 

And thanks for your preview plugin, works great!

---

### Post by conehead77 on 2009-06-04
> **zika said:**
> This kind of behavior happens to me when attributes of a .tex file are not "right". Due to last night's reinstall I have a bunch of files that were rescued from previous installation by copying to Vista partition and then copied back to Ubuntu partition after re-install. So, the have -rwxrwxrwx  1 zika zika   59189 2009-01-27 10:21 instead of -rw-r--r--  1 zika zika   203 2009-06-04 08:55 ... Maybe You have similar issue.

Unfortunately not, it seems to be an error when using multiple .tex files and assigning a master document.

---

### Post by corney91 on 2009-06-04
I use Winefish and Evince - it's not exactly live updating but I love it :)
I type out the LaTeX in Winefish and whenever I feel like it press F1 (F2 for .pdf) and Evince, which I have the file open with, automatically updates the changes :)

---

### Post by mihai.ile on 2009-06-05
This is the way I used do do LaTeX, gedit one window, evince in the other but after some time I just couldn't stand it anymore (ALT-TAB)...

---

### Post by zika on 2009-06-05
> **mihai007 said:**
> This is the way I used do do LaTeX, gedit one window, evince in the other but after some time I just couldn't stand it anymore (ALT-TAB)...
I'm glad You did not so You've given us a great gift ... :) Thank You again. One of the things that is and will be used on an hourly (not daily) basis ...

---

### Post by mihai.ile on 2009-06-06
Ok so it seems that the live preview patch was accepted and will be available in the next (0.2rc2) version of the gedit-latex-plugin, for the ones that want to try it right away just download the version from the gedit-latex-plugin svn repository (revision 339 or above), check [http://live.gnome.org/Gedit/LaTeXPlugin/Development](http://live.gnome.org/Gedit/LaTeXPlugin/Development) for more information on the svn version.

For the others, you can still download and extract the patched version archive that I put on [http://openmindedbrain.info/gedit-latex-plugin-live-preview](http://openmindedbrain.info/gedit-latex-plugin-live-preview)

---

### Post by zika on 2009-06-06
> **mihai007 said:**
> Ok so it seems that the live preview patch was accepted and will be available in the next (0.2rc2) version of the gedit-latex-plugin, for the ones that want to try it right away just download the version from the gedit-latex-plugin svn repository (revision 339 or above), check [http://live.gnome.org/Gedit/LaTeXPlugin/Development](http://live.gnome.org/Gedit/LaTeXPlugin/Development) for more information on the svn version.

For the others, you can still download and extract the patched version archive that I put on [http://openmindedbrain.info/gedit-latex-plugin-live-preview](http://openmindedbrain.info/gedit-latex-plugin-live-preview)
For us that vere more than brave and tried it several days ago, do we need to prepare to that update of original plugin or it will just be updated "on fly" ... ?

---

### Post by mihai.ile on 2009-06-06
right now the version released several days ago is almost identic to the one patched yesterday, so I would say to download only when the stable 0.2rc2 will be available for download, so check from time to time the [http://live.gnome.org/Gedit/LaTeXPlugin](http://live.gnome.org/Gedit/LaTeXPlugin) (the download menu), probably this will also be the version patched in the next ubuntu release.

---

### Post by macabro22 on 2009-06-30
How come its 2009 and this still is not in the repo?

---

### Post by mihai.ile on 2009-06-30
it is already, just that it's the 0.1 version and without live preview.

---

### Post by macabro22 on 2009-06-30
hmm...

```
 apt-cache showpkg gedit-latex-plugin
Package: gedit-latex-plugin
Versions: 
0.2rc1-1ubuntu1 (/var/lib/apt/lists/br.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-amd64_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/br.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-amd64_Packages
                  MD5: 72d68704366c227bad1c9cd0779b0c88


Reverse Depends: 
Dependencies: 
0.2rc1-1ubuntu1 - python (0 (null)) python-support (2 0.7.1) gedit (2 2.20.0) rubber (0 (null)) python-dbus (0 (null)) texlive (0 (null)) python-enchant (0 (null)) 
Provides: 
0.2rc1-1ubuntu1 - 
Reverse Provides: 

```

---

