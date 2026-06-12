---
title: "Editor other than vi for server"
date: 2012-01-25
forum: Server Platforms
---

### Post by sheld0r on 2012-01-25
I just installed Ubuntu Server 11.10 as a virtual machine and I was just curious what people use to edit there configurations other than vi.  I was a huge fan of gedit on Ubuntu workstation, because of the line numbers and ease of use.  Can I use anything other than vi with Ubuntu server that has line numbers and what not?

I had trouble getting Ubuntu workstation running with the nic drivers and video under Hyper-V as a vm, but now that I got Ubuntu server running I'm super stoked.

Any recommendations?

---

### Post by CharlesA on 2012-01-25
There are other CLI editors - nano comes to mind. It is similar to gedit, but doesn't have all the features of vim.

---

### Post by HunterDX77M on 2012-01-25
> **sheld0r said:**
> I just installed Ubuntu Server 11.10 as a virtual machine and I was just curious what people use to edit there configurations other than vi.  I was a huge fan of gedit on Ubuntu workstation, because of the line numbers and ease of use.  Can I use anything other than vi with Ubuntu server that has line numbers and what not?

I had trouble getting Ubuntu workstation running with the nic drivers and video under Hyper-V as a vm, but now that I got Ubuntu server running I'm super stoked.

Any recommendations?

If line numbers are your only problem, vi does support them and they can be activated easily. Like the other user said, nano is also good as it is simple and easy to use and the commands are always on the screen (whereas vi might require a tutorial).

---

### Post by amauk on 2012-01-25
vim is a technical text editor with a high learning curve
As mentioned above, if you want something simpler try nano

Just for the record though, to turn on line numbers in vim
```
:set number
```
and off
```
:set nonumber
```

---

### Post by KdotJ on 2012-01-25
I just thought I'd add my +1 to nano. It is a very simple editor and the commands are easy. It's the only CLI editor that I use.

---

### Post by sheld0r on 2012-01-25
Love this forum!  As a Linux newbie to post a question and get answers literally within minutes is just awesome!  

I've added the line numbers in vi, so I'll give this a try for a bit.  Thank you amauk for the commands.  I will also take a peak at nano.  

Thanks again for the input!

---

### Post by CharlesA on 2012-01-25
> **amauk said:**
> vim is a technical text editor with a high learning curve
As mentioned above, if you want something simpler try nano


Yeah, the learning curve is a bit of a pain, but once you get used to what vim can do, you are golden. ;)

I've have to turn on line numbers when troubleshooting scripts and if you don't want to turn them on each time, you can create a .vimrc file with the options you want.

Most of the .vimrc tutorials/tips/hints I have seen are monsters though.

---

### Post by sheld0r on 2012-01-25
> **CharlesA said:**
> Yeah, the learning curve is a bit of a pain, but once you get used to what vim can do, you are golden. ;)

I've have to turn on line numbers when troubleshooting scripts and if you don't want to turn them on each time, you can create a .vimrc file with the options you want.

Most of the .vimrc tutorials/tips/hints I have seen are monsters though.

I'm digging in on the Squid configuration, so that will be a blast!!

---

### Post by Lars Noodén on 2012-01-25
As far as I know, nano cannot do line numbers.  But one trick when working with configuration files is to invoke it with the [-w](http://manpages.ubuntu.com/manpages/oneiric/en/man1/nano.1.html) option to disable wrapping of long lines.  That can help prevent long lines from getting screwed up.

---

### Post by Cheesemill on 2012-01-25
I usually install vim on my servers and create an alias in my ~/.bashrc
```
alias vi='vim'
```To enable coloured syntax highlighting, line numbers, and several other goodies I use the ~/.vimrc file from my Arch workstation:
```
" .vimrc
" See: http://vimdoc.sourceforge.net/htmldoc/options.html for details

" For multi-byte character support (CJK support, for example):
"set fileencodings=ucs-bom,utf-8,cp936,big5,euc-jp,euc-kr,gb18030,latin1
       
set tabstop=4       " Number of spaces that a <Tab> in the file counts for.
 
set shiftwidth=4    " Number of spaces to use for each step of (auto)indent.
 
set expandtab       " Use the appropriate number of spaces to insert a <Tab>.
                    " Spaces are used in indents with the '>' and '<' commands
                    " and when 'autoindent' is on. To insert a real tab when
                    " 'expandtab' is on, use CTRL-V <Tab>.
 
set smarttab        " When on, a <Tab> in front of a line inserts blanks
                    " according to 'shiftwidth'. 'tabstop' is used in other
                    " places. A <BS> will delete a 'shiftwidth' worth of space
                    " at the start of the line.
 
set showcmd         " Show (partial) command in status line.

set number          " Show line numbers.

set showmatch       " When a bracket is inserted, briefly jump to the matching
                    " one. The jump is only done if the match can be seen on the
                    " screen. The time to show the match can be set with
                    " 'matchtime'.
 
set hlsearch        " When there is a previous search pattern, highlight all
                    " its matches.
 
set incsearch       " While typing a search command, show immediately where the
                    " so far typed pattern matches.
 
set ignorecase      " Ignore case in search patterns.
 
set smartcase       " Override the 'ignorecase' option if the search pattern
                    " contains upper case characters.
 
set backspace=2     " Influences the working of <BS>, <Del>, CTRL-W
                    " and CTRL-U in Insert mode. This is a list of items,
                    " separated by commas. Each item allows a way to backspace
                    " over something.
 
set autoindent      " Copy indent from current line when starting a new line
                    " (typing <CR> in Insert mode or when using the "o" or "O"
                    " command).
 
set textwidth=79    " Maximum width of text that is being inserted. A longer
                    " line will be broken after white space to get this width.
 
set formatoptions=c,q,r,t " This is a sequence of letters which describes how
                    " automatic formatting is to be done.
                    "
                    " letter    meaning when present in 'formatoptions'
                    " ------    ---------------------------------------
                    " c         Auto-wrap comments using textwidth, inserting
                    "           the current comment leader automatically.
                    " q         Allow formatting of comments with "gq".
                    " r         Automatically insert the current comment leader
                    "           after hitting <Enter> in Insert mode. 
                    " t         Auto-wrap text using textwidth (does not apply
                    "           to comments)
 
set ruler           " Show the line and column number of the cursor position,
                    " separated by a comma.
 
set background=dark " When set to "dark", Vim will try to use colors that look
                    " good on a dark background. When set to "light", Vim will
                    " try to use colors that look good on a light background.
                    " Any other value is illegal.
 
set mouse=a         " Enable the use of the mouse.
 
filetype plugin indent on
syntax on
```

+1 for the learning curve but it's worth it.
I've never come across a machine that doesn't have vi installed.

---

### Post by a2j on 2012-01-25
I don't use vi, instead, I use vim ;)

---

### Post by CharlesA on 2012-01-25
> **Cheesemill said:**
> I usually install vim on my servers and create an alias in my ~/.bashrc
```
alias vi='vim'
```

I haven't had to do that when I installed vim on Lucid. Interesting.

---

### Post by Cheesemill on 2012-01-25
> **CharlesA said:**
> I haven't had to do that when I installed vim on Lucid. Interesting.

Probably not. I'm running Arch on my workstation at the moment.

I wouldn't be surprised if the Ubuntu package either creates the symlink for you or overwrites the vi binary.

---

### Post by kevdog on 2012-01-26
For real basic editing you really need to know about 5 commands -- this is because I'm really stupid and I can only remember a few commands.  These however have gotten me by for years.  (I only use vi,vim for quick edits and in case of emergenices -- ie editing the sshd_config file over my android phone):

Esc -- this backs you out of editing mode and goes to command mode (the mode you can go up and down or right and left on lines -- you can move around)
i = insert (enters editing mode -- starts insertion before current character)
a = append (enters editing mode -- starts insertion after current character)
x = delete character (used in command mode)
dd = delete line (used in command mode)

:wq OR Cntl-zz (Hold Cntl key down and hit the z key twice) = write changes and quit. 

If you just plain screw up the file and need to get out of the file without saving changes:
:q!

That's it.  That's my primer.  Now you too can use vi for several years rather slowly but like a pro!

---

### Post by CharlesA on 2012-01-26
> **Cheesemill said:**
> Probably not. I'm running Arch on my workstation at the moment.

I wouldn't be surprised if the Ubuntu package either creates the symlink for you or overwrites the vi binary.

Yep, you'd be right. vi is symlinked to /etc/alternatives/vi which is symblinked back to /usr/bin/vim.basic

---

