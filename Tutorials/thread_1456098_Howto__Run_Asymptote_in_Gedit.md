---
title: "Howto : Run Asymptote in Gedit"
date: 2010-04-16
forum: Tutorials
---

### Post by chellier on 2010-04-16
Hello,

[Asymptote]("http://asymptote.sourceforge.net/") is a vector graphics language.

For the syntax highlighting in Gedit, download 
[AsyGeditv3.tar.gz]("http://cgmaths.fr/cgFiles/AsyGedit/") and extract the contents.1) Copy asy.lang in the directory : ~/.local/share/gtksourceview-2.0/language-specs .

2) Copy asymptote.xml in the directory : ~/.local/share/mime/packages

3) With a terminal, go to the directory ~/.local/share and run: update-mime-database mime

4) Restart Gedit.

For compilation in Gedit,

1) copy[COLOR=Black] [COLOR=#990000]cg-asyeps[/COLOR] and[/COLOR][COLOR=#990000][COLOR=Black] cg-asypdf in the directory : [/COLOR][/COLOR][COLOR=Black][COLOR=#330099]~/.gnome2/gedit/tools/[/COLOR][/COLOR][COLOR=#990000] 
[COLOR=Black]
2) In this directory : [/COLOR][/COLOR][COLOR=Black][COLOR=#009900]chmod u=rwx cg-*[/COLOR][/COLOR][COLOR=#990000]

[COLOR=Black]3) For pdf : Ctrl+F4, and for eps : Ctrl+F5.

More explication and syntax highlighting here : [http://cgmaths.fr/Atelier/Asymptote/ColCompGedit.html](http://cgmaths.fr/Atelier/Asymptote/ColCompGedit.html)

Christophe

Edit 28/08/2010 : New version
Edit 12/06 : New version : AsyGeditv3
[/COLOR][/COLOR]

---

### Post by Benzjaminz on 2010-08-31
great. thanks.

---

### Post by ionospheric on 2011-08-24
Hi chellier,

this is really great. When I installed it, syntax highlighting worked immediately, however compiling did not. Pressing CTRL-F5 did nothing.
Eventually I figured out what the problem was. I went into Edit-> Preferences -> Plugins and enabled the "External Tools". After that, It worked. Hope this may help somebody.

---

