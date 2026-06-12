---
title: "Modify XML syntax higlighting file sh to deal with bash in gedit, pluma, etc."
date: 2020-06-06
forum: Ubuntu Dev Link Forum
---

### Post by Paddy Landau on 2020-06-06
I wonder if you could help me with something that has frustrated me for some time.

There are many XML files for syntax highlighting for use with editors, e.g. [FONT=lucida console]gedit[/FONT] and [FONT=lucida console]pluma[/FONT], in the shared area:
[FONT=lucida console]/usr/share/gtksourceview-3.0/language-specs[/FONT]

There isn't one for Bash. Most of the time, the workaround is to use the [FONT=lucida console]sh[/FONT] syntax highlighting, but there are a couple of problems with using it for Bash. The worst one that I've come across is where command substitution, using quotes, is used within a [FONT=lucida console]case[/FONT] block. An example follows:
```
#!/bin/bash

case ${SOMETHING} in
    ( 'a' )
        FILENAME="$( readlink "${ARG}" )"
        ;;
esac
CONFUSING_LINE="case esac"
```
If you put this into [FONT=&amp]gedit[/FONT] with the [FONT=lucida console]sh[/FONT] syntax highlighting, you'll notice that *everything* after the [FONT=lucida console]readlink[/FONT] command is shown as being in quotes — apart from sections that actually are within quotes!

Having this structure in a long script file leads to the syntax highlighting after this point being useless. Well, worse than useless, because it incorrectly highlights quoted content.

So…

I decided that I'd copy the existing [FONT=lucida console]sh.lang[/FONT] to [FONT=lucida console]bash.lang[/FONT], and modify it to work with Bash. It didn't take me long to realise that, despite the file being quite short, I was hopelessly lost. I cannot get my head around how to fix this!

Can you help, please? I'd love to finally fix this and submit it for the many people who have also asked about Bash highlighting in [FONT=lucida console]gedit[/FONT] and other editors.

Thank you

---

### Post by webaake on 2020-06-06
I've just tried your code in Mousepad and I couldn't make heads or tail of it. But Mousepad has a lot of options for marking code/script.

---

### Post by norobro on 2020-06-06
Works fine on my system with the latest sh.lang file from here: [https://gitlab.gnome.org/GNOME/gtksourceview/tree/master/data/language-specs](https://gitlab.gnome.org/GNOME/gtksourceview/tree/master/data/language-specs)

[ATTACH=CONFIG]286119[/ATTACH]

---

### Post by Paddy Landau on 2020-06-07
> **norobro said:**
> Works fine on my system with the latest sh.lang file from here: [https://gitlab.gnome.org/GNOME/gtksourceview/tree/master/data/language-specs](https://gitlab.gnome.org/GNOME/gtksourceview/tree/master/data/language-specs)
That's fantastic, thank you! I shall make a note of that link in case of future problems.

---

