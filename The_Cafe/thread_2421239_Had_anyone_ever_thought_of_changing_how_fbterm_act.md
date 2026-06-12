---
title: "Had anyone ever thought of changing how fbterm acts?"
date: 2019-06-18
forum: The Cafe
---

### Post by there.is.only.xul on 2019-06-18
If you don't know, fbterm is a terminal which runs in the frame buffer of your TTY. There. Now you know. However, there's something else;

fbterm adds its own hacks to make 256 colours play nice, since [FONT=courier new]xterm-256color[/FONT] is ass and [FONT=courier new]linux[/FONT] doesn't support it. But then I read this in the man pages;

> A new terminfo database entry named "fbterm" was added to use these private sequences, all program based on terminfo should work with it. By default, FbTerm sets environment variable "TERM" to value "linux", user need run "TERM=fbterm /path/to/program" to enable 256 color mode.

...What? If fbterm adds fbterm to terminfo, why doesn't it set TERM to fbterm? So for the last few days I've been beating my head against a solid brick wall as no matter what I do with fbterm or zsh it just doesn't want to comply with my idea of how things should work (unless, of course, I tell my [FONT=courier new].zshrc[/FONT] to e[FONT=courier new]xport TERM="fbterm"[/FONT] in which case it doesn't work in X, and I don't know how to make it TTY-conditional.)

This isn't asking how to make what I want happen, which is basically to add into my [FONT=courier new].zshrc[/FONT] a TTY-conditional TERM for 256 colours in fbterm without having to manually type [FONT=courier new]TERM=fbterm[/FONT] every single time. This is asking... *why [FONT=courier new]linux[/FONT]?* If fbterm has its own terminfo entry I have to manually define *anyway*, why doesn't it use its own terminfo definition by default? That would make the most sense right?

Had anyone ever thought of patching fbterm so it uses its own terminfo definition automatically?

---

### Post by TheFu on 2019-06-18
I know nothing about zsh. Sorry.

I'd check if XDG_SESSION_TYPE  is set.  Any value is probably sufficient to know it is a GUI, not tty.
Or check XDG_SESSION_DESKTOP  for any value.

I'm a pure xterm user. HATE colors. Most setups are too hard to read.

---

