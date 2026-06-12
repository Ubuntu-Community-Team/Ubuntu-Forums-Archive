---
title: "VIM error"
date: 2008-05-20
forum: Windows
---

### Post by frito on 2008-05-20
I installed gvim to my windows xp and i get this error when i try to edit with it

```
Error detected while processing C:\Program Files\Vim\_vimrc:

line    1:
E518: Unknown option: source 

line    2:
E121: Undefined variable: arg1
E15: Invalid expression: arg1 =~ ' ' | let arg1 = '"' . arg1 . '"' | endif

line   21:
E171: Missing :endif
```

I know i never should have used a windows box but I figured you guys would know what to do

---

### Post by nick_h on 2008-05-20
It would help if you posted your _vimrc file (which is the ~/.vimrc file in Ubuntu?).

You could always try renaming it to get rid of the errors.

---

### Post by p_quarles on 2008-05-20
Moved to Windows Discussions.

---

### Post by frito on 2008-05-22
my .vimrc is as follows:
```
set nocompatible source $VIMRUNTIME/vimrc_example.vim source $VIMRUNTIME/mswin.vim behave mswin set diffexpr=MyDiff() function MyDiff() let opt = '-a --binary ' if &diffopt =~ 'icase' | let opt = opt . '-i ' | endif if &diffopt =~ 'iwhite' | let opt = opt . '-b ' | endif let arg1 = v:fname_in
  if arg1 =~ ' ' | let arg1 = '"' . arg1 . '"' | endif
  let arg2 = v:fname_new
  if arg2 =~ ' ' | let arg2 = '"' . arg2 . '"' | endif
  let arg3 = v:fname_out
  if arg3 =~ ' ' | let arg3 = '"' . arg3 . '"' | endif
  let eq = ''
  if $VIMRUNTIME =~ ' '
    if &sh =~ '\<cmd'
      let cmd = '""' . $VIMRUNTIME . '\diff"'
      let eq = '"'
    else
      let cmd = substitute($VIMRUNTIME, ' ', '" ', '') . '\diff"'
    endif
  else
    let cmd = $VIMRUNTIME . '\diff'
  endif
  silent execute '!' . cm
```

---

### Post by nick_h on 2008-05-22
The first line of the script should be split out into multiple lines with one command per line.

---

