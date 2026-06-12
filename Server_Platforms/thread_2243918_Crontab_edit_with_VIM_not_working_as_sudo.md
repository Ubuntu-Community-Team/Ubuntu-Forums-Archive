---
title: "Crontab edit with VIM not working as sudo"
date: 2014-09-12
forum: Server Platforms
---

### Post by smeerbartje on 2014-09-12
I'm having troubles with editing my crontab. This is what happens: when I edit crontab as my own user 'crontab -e', everything works fine. The environment var "EDITOR" is read and /usr/bin/vim is started as the editor for the crontab. However, when I try to edit the crontab for root (by typing 'sudo crontab -e'), I receive the following errors:

```
Error detected while processing /home/rogier/.vimrc:
line    1: E319: Sorry, the command is not available in this version: syntax enableError detected while processing /home/rogier/.vim/colors/solarized.vim:
line  141: E319: Sorry, the command is not available in this version: let s:terms_italic=["rxvt","gnome-terminal"]
line  147: E319: Sorry, the command is not available in this version: let s:terms_noitalic=["iTerm.app","Apple_Terminal"]

```
For some reason, the .vimrc file is interpreted wrong and I don't know how to solve this.

---

### Post by nerdtron on 2014-09-12
This server has no GUI right?  What what happens if you use the default .vimrc file? I mean, from your error I think you copied the .vimrc from a desktop and used it on the server?

---

### Post by smeerbartje on 2014-09-12
Hi, indeed, the server is not running a GUI. The .vimrc is as follows. As you can see, it's not very complex.

[FONT=System]syntax enable
set background=dark
colorscheme solarized[/FONT]

---

