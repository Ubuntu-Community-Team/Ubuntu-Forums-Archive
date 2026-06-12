---
title: "HOW TO: VI Syntax Highlighting"
date: 2008-06-27
forum: Server Platforms
---

### Post by promodus on 2008-06-27
There are two things I like to change to vim on a default ubuntu install.

First of all, when using insert mode and using the arrow keys the BCDA that shows up at the beginning of each line is a bit of a nuisance to me.

Secondly, I like to have the syntax highlighting when editing scripts.

```
apt-get remove vim-tiny
apt-get install vim vim-runtime
echo set nocompatible >> ~/.vimrc
echo syntax on >> ~/.vimrc
```

Thats it... :wink:

---

