---
title: "VI config"
date: 2013-08-11
forum: Ubuntu, Linux and OS Chat
---

### Post by The-Server-4dmin on 2013-08-11
I have been playing with VI for 10+ years now. Anyone have a good vimrc file. 


Here is my .vimrc

```

**set** **number**
**set** **history**=[COLOR=#009999]700[/COLOR]
**set** [COLOR=#0086B3]autoread[/COLOR]
**set** **so**=[COLOR=#009999]7[/COLOR]
**set** [COLOR=#0086B3]wildmenu[/COLOR]
**set** [COLOR=#0086B3]wildignore[/COLOR]=*.**o**,*~,*.pyc
**set** [COLOR=#0086B3]ruler[/COLOR]
**set** [COLOR=#0086B3]cmdheight[/COLOR]=[COLOR=#009999]2[/COLOR]
**set** **hid**
**set** [COLOR=#0086B3]backspace[/COLOR]=[COLOR=#0086B3]eol[/COLOR],**start**,indent
**set** [COLOR=#0086B3]ignorecase[/COLOR]
**set** [COLOR=#0086B3]smartcase[/COLOR]
**set** [COLOR=#0086B3]hlsearch[/COLOR]
**set** [COLOR=#0086B3]incsearch[/COLOR]
**set** [COLOR=#0086B3]lazyredraw[/COLOR]
**set** [COLOR=#0086B3]magic[/COLOR]
**set** [COLOR=#0086B3]showmatch[/COLOR]
**set** **mat**=[COLOR=#009999]2[/COLOR]
**set** [COLOR=#0086B3]noerrorbells[/COLOR]
**set** [COLOR=#0086B3]novisualbell[/COLOR]
**set** [COLOR=#0086B3]t_vb[/COLOR]=
**set** **tm**=[COLOR=#009999]500[/COLOR]
[COLOR=#0086B3]syntax[/COLOR] enable 
**colorscheme** desert
**set** [COLOR=#0086B3]background[/COLOR]=[COLOR=#0086B3]dark[/COLOR]
**set** [COLOR=#0086B3]encoding[/COLOR]=utf8
**set** [COLOR=#0086B3]ffs[/COLOR]=unix,dos,mac
**set** [COLOR=#0086B3]nobackup[/COLOR]
**set** [COLOR=#0086B3]nowb[/COLOR]
**set** [COLOR=#0086B3]noswapfile[/COLOR]
**set** [COLOR=#0086B3]smarttab[/COLOR]
**set** [COLOR=#0086B3]shiftwidth[/COLOR]=[COLOR=#009999]4[/COLOR]
**set** [COLOR=#0086B3]tabstop[/COLOR]=[COLOR=#009999]4[/COLOR]

```

---

### Post by cariboo on 2013-08-11
Thread moved, as this isn't a Cafe thread.

---

### Post by kpothi on 2013-08-14
I haven't used VI at all. So, I'm not sure, if .vimrc file works with VI. Assuming, you use VIM, there are plenty of good .vimrc configurations available in Github, [Gist.Github](https://gist.github.com/search?q=vimrc), etc. Additionally, I keep in touch with the latest developments by reading blogs such as [UseVIM](http://usevim.com/).

---

### Post by evilsoup on 2013-08-14
Here's the .vimrc I use for prose writing. I can toggle the spellcheck with F5, and toggle the syntax highlighting with F6 (it's useful to turn them off when I want a distraction-free environment).

```

syntax on
set wrap
set linebreak
set spell spelllang=en_gb
map <f5> :set spell! spelllang=en_gb <enter>
map <F6> :if exists("g:syntax_on") <bar> syntax off <bar> else <bar> syntax enable <bar> endif <enter> <enter>

```

I hope nobody minds if I pimp my blog here, but I use this in conjunction with GNU Screen to have a fullscreen, centred, distraction-free writing environment as detailed [here](http://evilsoup.wordpress.com/2013/08/04/distraction-free-writing-on-linux/).

---

