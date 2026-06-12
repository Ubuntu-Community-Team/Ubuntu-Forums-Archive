---
title: "What's in your .bashrc and .vimrc"
date: 2007-01-17
forum: The Cafe
---

### Post by mlissner on 2007-01-17
My computer just died not too long ago, and I lost all the interesting stuff I had in my .bashrc and .vimrc files. 

.vimrc:
```

#set line numbering
set number
#Set autoindent
set ai
#set case-insensitive searching
set ignorecase

```

.bashrc
```
###MY ADDITIONS##
#Add directories to the path variable.
PATH=$PATH:~/bin/:.
#Add some aliases
alias thunderbird=mozilla-thunderbird
alias bye=exit
alias shred='shred -vuz'
alias sysmon='gnome-system-monitor'

```

What you got?

---

### Post by discord on 2007-01-17
" -*- vim -*-

" tmp disabled
"map N :w [CTRL]-M

" Use Vim settings, rather then Vi settings.
set nocompatible

" Turn on the verboseness to see everything vim is doing.
"set verbose=9

" Stop the annoying bell, use the visual-bell instead.
" set visualbell

" Show (partial) command in status line.
set showcmd

" Allow backspacing over everything in insert mode.
set bs=2

" Always set autoindenting on.
set ai

" Don't wrap lines at the edge of the screen.
set nowrap

" Keep 50 lines of command line history.
set history=50

" Show the cursor position all the time.
set ruler

" Do incremental searching.
set incsearch

" Set ignorecase on.
set ignorecase

" Set 'g' substitute flag on.
set gdefault

" Set the command line to one line high.
set cmdheight=1

" Set 50 lines for the display, 1 for the status line.
if has('gui_running')
  "set lines=48
  set lines=30
  set columns=80
  set mouse=a
endif


set statusline=[%02n]\ %f\ %(\[%M%R%H]%)%=\ %4l,%02c%2V\ %P%*

" Always display a status line at the bottom of window.
set laststatus=2

" Set the cinoptions. Use the default for everything except the ( option.
set cinoptions=(0

" Set the number of screen lines to keep above and below the cursor when
" scrolling like emacs.
" set SCROLLOFF=9999

" Insert two spaces after a period with every joining of lines.
" I like this as it makes reading texts easier (for me, at least).
set joinspaces

" showmatch: Show the matching bracket for the last ')'?
set showmatch

" allow tilde (~) to act as an operator -- ~w, etc.
set tildeop

" not using source tags
" set tags=./tags,../tags,/mnt/Disc/Develop/Src/tags,/mnt/Disc/Products/Src/tags,/mnt/Disc/Products/Java/tags

" This shows spaces and tabs characters. Visual Whitespace.
" set list
"set listchars=tab:»·,trail:·
"set listchars=trail:·
"set list!

" Java specific stuff
let java_highlight_all=1
let java_highlight_debug=1
let java_ignore_javadoc=1
let java_highlight_functions=1
let java_mark_braces_in_parens_as_errors=1

" use the old style html comments.  This is for Cold Fusion.
let html_wrong_comments=1

"this is auto by default
"  set makeprg=make

" TagList settings.
let Tlist_WinWidth = 25

"if has("gui")
  " set the gui options to:
  "   g: grey inactive menu items
  "   m: display menu bar
  "   r: display scrollbar on right side of window
  "   b: display scrollbar at bottom of window
  "   t: enable tearoff menus on Win32
  "   T: enable toolbar on Win32
  " set go=gmrb
"endif

" VimSpell settings.
let spell_executable = "aspell"
let spell_auto_type = "mail,text,html"

" ************************************************************************
" C O M M A N D S
"
command! CD cd %:p:h

" ************************************************************************
" K E Y   M A P P I N G S
"
"set winaltkeys=no
nmap <M-Space> :simalt ~<CR>

imap <M-j> <Down>
imap <M-k> <Up>
imap <M-h> <Left>
imap <M-l> <Right>
imap <M-Space> ^[ a

imap <M-w> <C-Right>
imap <M-W> ^[Wi
imap <M-b> <C-Left>
imap <M-a> <C-Left>
imap <M-B> ^[Bi
imap <M-e> ^[ea
imap <M-E> ^[Ea
imap <M-$> <End>
imap <M-0> <Home>

map <Leader>e :Explore<cr>
map <Leader>s :SExplore<cr>

" Make p in Visual mode replace the selected text with the "" register.
vnoremap p <esc>:let current_reg = @"<cr>gvdi<c-r>=current_reg<cr><esc>

" Make <C-Left> and <C-Right> act the same in Insert Mode as in Normal Mode.
imap <c-left> <c-o><c-left>
imap <c-right> <c-o><c-right>

" Don't use Ex mode, use Q for formatting
map Q gq

" Make tab in v mode work like I think it should (keep highlighting):
vmap <tab> >gv
vmap <s-tab> <gv

" Jump to the tag associated with current word.  If more than one match is
" found, display list of matching tags.
map <C-\> :exec "stjump " . expand("<cword>")<CR>

" Make <F7> insert the function header.
"map <F7> :call <SID>FunctionHeader(expand("%:e"))<CR>

" Make <F8> diff the current buffer with it's file on disk.
"nmap <F8> :w !diff -w -B -c5 -p - % >tmp.diff<CR>:sp tmp.diff<CR>

" Date/Time stamps
" %a - Day of the week
" %b - Month
" %d - Day of the month
" %Y - Year
" %H - Hour
" %M - Minute
" %S - Seconds
" %Z - Time Zone
iab YDATETIME <c-r>=strftime(": %a %b %d, %Y %H:%M:%S %Z")<cr>
map ,L mz1G/Last modified:/e<Cr>CYDATETIME<Esc>`z
map ,date :let @z=strftime("%A %b %d, %Y")<Cr>"zpa
map ,time :let @z=strftime("%H:%M:%S %Z")<Cr>"zpa

" Map <m-/> to start searching when in insert mode.
imap <m-/> <c-o>/

" Map <m-$> to move to end of line in insert mode.
imap <m-$> <c-o>$

" Map <m-0> to move to the beginning of the line in insert mode.
imap <m-0> <c-o>0

" Map <m-^> to move to the first non-blank character of the line in insert
" mode.
imap <m-^> <c-o>^

" Map <m-e> to move to the end of a word in insert mode.
imap <m-e> <c-o>e

" Map <m-b> to move to the beginning of a word in insert mode.
imap <m-b> <c-o>b

" Map <c-s> to write current buffer.
map <c-s> :w<cr>
imap <c-s> <c-o><c-s>
imap <c-s> <esc><c-s>

" Select all.
map <m-s-a> ggVG

" 'Paste' from clipboard.
map <m-s-p> "*p

" 'Copy' to clipboard.
map <m-s-y> "*Y
vmap <m-s-y> "*y
" 
" 'Cut' to clipboard.
map <m-s-x> "*x
vmap <m-s-x> "*x

" Undo in insert mode.
imap <c-z> <c-o>u

" Window Manager.
nn  <F9> :WMToggle<CR>

" Display the number of lines in the range in the Status Line.
" com! -range -nargs=0 Lines :echo <line2> - <line1> + 1

" Switch syntax highlighting on.
syntax on

" Load my color scheme.
colorscheme evening
if has("gui_running")
	colorscheme torte
endif

" ************************************************************************
" B E G I N  A U T O C O M M A N D S
"
if has("autocmd")
  " Enable file type detection.
  " Use the default filetype settings, so that mail gets 'tw' set to 72,
  " 'cindent' is on in C files, etc.
  " Also load indent files, to automatically do language-dependent indenting.
  filetype plugin indent on

  " When starting to edit a file:
  "   For .txt and .doc files, do not expand tabs to spaces and set tabs to 8.
  "   For all other languages, expand tabs to spaces and set tabs to 2.
  " expandtab removed from the next line
  au BufNewFile,BufEnter * set ts=2 sw=2
  au BufNewFile,BufEnter *.txt,*.doc set noexpandtab ts=3 sw=3 tw=72

  " Normally don't automatically format 'text' as it is typed, only do this
  " with comments, at 79 characters.
  au BufNewFile,BufEnter *.c,*.h,*.java set formatoptions-=t tw=79

"  augroup html
"    " Remove all html autocommands
"    au!
"
"    " Automatically search for the "Last modified" string and replace it with
"    " the timestamp.
"    autocmd BufWritePre *.htm,*.html norm ,L
"  augroup END
endif

" GUI ONLY type stuff.
if has("gui")
"  :menu MyVim.ASCII\ Chart :call AsciiChart()<cr>
"  :menu MyVim.Dec-Hex\ Chart :call Dec2Hex()<cr>
"  :menu MyVim.Current\ File.Convert\ Format.To\ Dos :set fileformat=dos<cr> :w<cr>
"  :menu MyVim.Current\ File.Convert\ Format.To\ Unix :set fileformat=unix<cr> :w<cr>
"  :menu MyVim.Current\ File.Remove\ Trailing\ Spaces\ &&\ Tabs :%s/[ 	]*$//g<cr>
"  :menu MyVim.Current\ File.Remove\ All\ Tabs :retab<cr>
"  :amenu MyVim.Insert.Date<Tab>,date <Esc><Esc>:,date<Cr>
"  :amenu MyVim.Insert.Date\ &Time<Tab>,datetime <Esc><Esc>:let @z=YDATETIME<Cr>"zpa
"  :amenu MyVim.-SEP1- <nul>
"  :amenu MyVim.&Global\ Settings.Toggle\ Display\ Unprintables<Tab>:set\ list!	:set list!<CR>
"  :amenu MyVim.-SEP2- <nul>
"  :amenu MyVim.Buffer\ Explorer<Tab>:BufExplorer :BufExplorer<cr>
"  :amenu MyVim.Calendar<Tab>:Calendar :Calendar<cr>
"  :amenu MyVim.Tag\ List<Tab>:Tlist :Tlist<cr>

  " Set the font to use.
  "set guifont=LucidaTypewriter\ 10
  set guifont=Monospace\ 11

  " Let Windows process the Alt-key
  "set winaltkeys
  "set mousehide
endif

" Do my personal sourcing...
"if has("win32")
"  source $HOME/vim/vimfiles/macros/matchit.vim
"  " source $HOME/vim/vimfiles/macros/ruler.vim
"  " source $HOME/vim/vimfiles/macros/blockcmd.vim
"  " source $HOME/vim/vimfiles/macros/toggleFold.vim
"  " source $HOME/vim/vimfiles/macros/boxes.vim
"else
"  source /usr/local/share/vim/vim61/macros/matchit.vim
"  " source ~/.vim/macros/blockcmd.vim
"  " source ~/.vim/macros/toggleFold.vim
"endif

"set vi='256,\"512,h,%,ra:,rb:,rd:
"let g:winManagerWindowLayout="BufExplorer,FileExplorer,TagList"

"set number
"set foldcolumn=4

"set printoptions=number:y

set showmatch " this should show a matching bracket when you close one

" MENUS
source $VIMRUNTIME/menu.vim
set wildmenu
set cpo-=<
set wcm=<C-Z>
map <F4> :emenu <C-Z>
" EOF

---

### Post by 23meg on 2007-01-17
[This one]("http://www.ubuntuforums.org/showpost.php?p=485014&postcount=5") goes in my .inputrc but I just thought it deserves a mention here since it makes so much sense.

---

### Post by KaeseEs on 2007-01-17
hehe... my section from /etc/bash.bashrc (so it's available from root, too)
```

#@version   0.5.6.24
#@begun     13 APR 2006
#@update    29 DEC 2006

#say what we're doin
clear
/usr/bin/tty
echo "Loading user aliases and functions..."

#commands
alias cl='clear'
alias cd..='cd ..'
alias sd='sudo shutdown -h now'                                   # shutdown
alias rs='sudo shutdown -r now'                                   # restart
alias pl='sudo /etc/cron.daily/prelink'                           # prelink
alias mu='sudo mount /dev/sdb1'                                   # mount USB drive (see /etc/fstab)
alias uu='sudo umount /dev/sdb1'                                  # unmount USB drive (see /etc/fstab)
alias ll='ls -l'                                                  # list files w/ attributes
alias lh='ls -lh'                                                 # list files w/ attributes ( human-readable sizes )
alias la='ls -lA'                                                 # list all files w/o attributes
alias lah='ls -lah'                                               # list all files w/ attributes ( human-readable sizes )
alias df='df -h -t xfs -t ext3 --sync'                            # list partitions & their stats
alias fw='ftp kaesees.122mb.com'								  # opens ftp connection to my website
alias svnc='svn commit --username kaesees'						  # commits to svn
alias svnu='svn update --username kaesees'						  # updates from svn
alias svns='svn status'											  # gets svn status
alias svnl='svn log --username kaesees'							  # gets log from svn
alias mcd='sudo mount -t auto /dev/hda /media/cdrom0'			  # mounts cdrom
alias ucd='sudo umount /media/cdrom0'							  # unmounts cdrom

fr()  {
          clear;                                                  # clear
          echo "                          Used      Free";        # output
          free -m|grep -;                                         # dsp RAM
      }

alias kg='sudo killall gdm gkrellm gkrellmd'                      # kill gdm  
alias kp='sudo killall gkrellm gkrellmd kuake'                    # kill progs

#update functions
us()  {  
         sudo cp -i /etc/bash.bashrc ~/config/bash.bashrc.old;    # backup bash config file to ~/config
         sudo cp -i ~/config/bash.bashrc /etc/bash.bashrc ;       # then update it from ~/config
         return;                                                  # return nothing
      }

uk()  {
         cp -i ~/.fluxbox/keys ~/config/keys.old;                 # backup fluxbox keys file to ~/config
         cp -i ~/config/keys ~/.fluxbox/keys;                     # then update it from ~/config
      }

um()  {
         cp -i ~/.fluxbox/menu ~/config/menu.old;                 # backup fluxbox menu file to ~/config
         cp -i ~/config/menu ~/.fluxbox/menu;                     # then update it from ~/config
      }

alias ms='sudo sh /home/mike/script/mait'                         # calls system maitenance script
alias sl='sudo slocate -u -e /media/hda1 /media/usbdrv'           # builds a slocate database for linux partition only
alias sa='sudo slocate -u'                                        # builds a slocate database for all mounted partitions

#initializations
alias io='sh /home/mike/bin/opera &'                              # init opera
alias ix='xinit'                                                  # init x-server (configure via ~/.xinitrc)
alias ig='sudo gdm && cl &'                                       # init gdm
alias ii='sudo sh ~/config/noip/debian.noip2.sh start'            # init noip2 IP/DNS forwarding dynamic updater
alias ia='sudo /usr/sbin/apache2ctl start'                        # init Apache2 HTTP server

#edits
alias ek='vim /home/mike/config/fkeys'                            # edit fluxbox hotkeys
alias em='vim /home/mike/config/fmenu'                            # edit fluxbox menu
alias ei='vim /home/mike/config/fapps'                            # edit fluxbox init apps
alias es='vim /home/mike/config/bash.bashrc'                      # edit shell config
alias eg='sudo dpkg-reconfigure xserver-xorg'                     # edit xconfig ['graphics']

#restarts
alias rg='kg && ig'                                               # restart gdm by killing then starting
alias ra='sudo /usr/sbin/apache2ctl restart'                      # restart Apache2 HTTP server

#apache commands
# see 'ia' in initializations
# see 'ra' in restarts
alias ka='sudo /usr/sbin/apache2ctl stop'

```

As you can see, it's a cluster of piecemeal additions, made over a long period, with some stuff refactored every so often (in the real version, there are old 'alternative' implementations of many functions commented out). It all works, though:mrgreen:  If you want to know what an old-school UNIX kernel looks like nowadays, imagine this with #ifdef statements, kernel func calls, and GOTOs.

---

### Post by ice60 on 2007-01-17
hi, you can get preconfigured .bashrc and i suppose .vimrc files too from here -
[http://dotfiles.com/](http://dotfiles.com/)

here are the bash files -
[http://dotfiles.com/index.php?app_id=3](http://dotfiles.com/index.php?app_id=3)

check this one out :o
[http://dotfiles.com/files/3/318_profile](http://dotfiles.com/files/3/318_profile)

here are the vim files -
[http://dotfiles.com/index.php?app_id=9](http://dotfiles.com/index.php?app_id=9)

---

### Post by deadlydeathcone on 2007-01-17
My .bashrc is pretty basic:

```
alias agu='sudo apt-get update'
alias agdu='sudo aptitude dist-upgrade'
alias agi='sudo aptitude -r install'
alias agr='sudo aptitude purge'
alias ags='apt-cache search'
alias acs='apt-cache show'
alias agis='apt-get -b source'
alias agid='sudo apt-get build-dep'
alias package='sudo dpkg-buildpackage -rfakeroot'
alias trash='sudo rm -rf $HOME/.Trash/*'
alias checkdisk='sudo touch /forcefsck'
alias skipcheck='sudo touch /fastboot'
alias lsd='ls -d */'
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias hist='history | grep'
alias pbi='sudo pbuilder build *.dsc'
alias pbu='sudo pbuilder update'
alias g='gnome-open'
alias naut='gnome-open .'
alias sg='sudo gnome-open'
alias snot='sudo gnome-open .'
```

---

### Post by deadlydeathcone on 2007-01-17
My .bashrc is pretty basic:

```
alias agu='sudo apt-get update'
alias agdu='sudo aptitude dist-upgrade'
alias agi='sudo aptitude -r install'
alias agr='sudo aptitude purge'
alias ags='apt-cache search'
alias acs='apt-cache show'
alias agis='apt-get -b source'
alias agid='sudo apt-get build-dep'
alias package='sudo dpkg-buildpackage -rfakeroot'
alias trash='sudo rm -rf $HOME/.Trash/*'
alias checkdisk='sudo touch /forcefsck'
alias skipdisk='sudo touch /fastboot'
alias lsd='ls -d */'
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias hist='history | grep'
alias pbi='sudo pbuilder build *.dsc'
alias pbu='sudo pbuilder update'
alias g='gnome-open'
alias naut='gnome-open .'
alias sg='sudo gnome-open'
alias snaut='sudo gnome-open .'
```

edit:
Thanks ice60, that's awesome.

---

### Post by anaconda on 2007-01-17
Good idea nice to see what others have in their .vimrc
my .vimrc:

```
colorscheme darkblue
set nu
set gfn=DejaVu\ Sans\ Mono\ 9
set enc=latin1
set ic
set scs
set mousef
set ai
set si
set ts=4
set sw=4
set co=135
set lines=50
set cindent shiftwidth=4
set nowb
set nobk
set cursorline
set hlsearch
syntax on
```

hmm .after reading discord:s .vimrc this seems quite short... but works well for me.

---

### Post by Mateo on 2007-01-19
are aliases restricted to 1 line commands?

---

### Post by anaconda on 2007-01-19
> **Mateo said:**
> are aliases restricted to 1 line commands?

I guess they are, but it wouldn't be a restriction, because you can make VERY long lines. And you can always use && to run several commands.. 

eg.
ls && cd foo
would first do ls and then change directory to foo...

---

### Post by Mateo on 2007-01-19
ok i'll give that a try, thanks.  btw, what is the difference between using & and &&?  i've seen both before...

---

### Post by darrenm on 2007-01-19
Absolute essential for Ubuntu:

```
alias agu='sudo apt-get update'
alias agi='sudo apt-get install'
alias agd='sudo apt-get dist-upgrade'

```

Bah didnt spot the earlier post. Not just me then ;)

---

### Post by mlissner on 2007-01-20
There a bunch of these, and the one you really want isn't &&.

&& will do the second command if and only if the first one is completed successfully as in cd && ls, which will change to your home directory and then (if the cd is successful), list its contents.

|| will do the second thing ONLY if the first one fails. For example, echo success || echo failure will echo success, but if that command fails, it will say failure.

Ending a command with & will make it run in the background, as in firefox &, thereby freeing up your terminal for more command entry.

But to answer the question about aliases, you've got two options: 
1. use semicolons as in alias dog=cat; alias ll='ls -l'; etc. 
2. put them all in a file in your home directory. Say it's called aliasfile, you could then run it with your .bashrc file by making it executible with a chmod 755 aliasfile, and then putting the command aliasfile in your .bashrc. I think that'll work.

If you have problems with these, let me know. I'll be happy to explain further. The reason you don't want to use && above is because if one of your aliases doesn't work, the rest won't get processed.

On one final note, to determine if a process in the terminal ended successfully, after it ends do a echo $?. That will tell you the exit code for the former process. Generally, if it returns zero, it ended well. If it returns one (or something else), it did not. 

Ok. Good luck out there.

---

### Post by po0f on 2007-01-20
Mateo,

You can break up long lines up with slashes:
```
[FONT="Courier New"]alias really_long_command="do some stuff && \
    do some more stuff && \
    done doing stuff"[/FONT]
```

It will make a mutli-command alias more readable to put them on separate lines.  Should work, but I haven't tested it.

---

### Post by mlissner on 2007-01-20
This is true, but like I said before, you're going to want to use semicolons, not &&....

The other important thing to to make sure you do a backslash and then hit enter as the VERY next key. Otherwise, if there is a space there or something it won't work.

---

### Post by po0f on 2007-01-20
mlissner,

Well, if you're setting an alias for a chain of commands, not just a single command with a bunch of weird options, you probably *do* want to separate them with &&.  If one fails, the other commands won't run.  I think that's the point.

[quote=mlissner]... The reason you don't want to use && above is because if one of your aliases doesn't work, the rest won't get processed. ...[/quote]
I really don't understand this either.  How does Bash process aliases?  When they're run, right?  So how would a && in one alias, if it's placed correctly or otherwise, affect another alias, when neither alias was run?

---

### Post by KaeseEs on 2007-01-20
No, what he's saying is that if you chain aliases together with &&s, the failure of one prevents all the rest from running.  Generally, I desire that behavior when I do sequences, but some may not.

If you want to do a bunch of things with one command, however, your best bet is to make it a function, like so:

```
fr()  {
          clear;                                                  # clear
          echo "                          Used      Free";        # output
          free -m|grep -;                                         # dsp RAM
      }
```

* The above function outputs a formatted table displaying used and free RAM, w/ buffers and cache factored out.

---

### Post by ice60 on 2007-01-30
here's my .bashrc right now -

```
# There are 3 different types of shells in bash: the login shell, normal shell
# and interactive shell. Login shells read ~/.profile and interactive shells
# read ~/.bashrc; in our setup, /etc/profile sources ~/.bashrc - thus all
# settings made here will also take effect in a login shell.
#
# NOTE: It is recommended to make language settings in ~/.profile rather than
# here, since multilingual X sessions would not work properly if LANG is over-
# ridden in every subshell.

# Some applications read the EDITOR variable to determine your favourite text
# editor. So uncomment the line below and enter the editor of your choice :-)
#export EDITOR=/usr/bin/vim
#export EDITOR=/usr/bin/mcedit

#############################################################################################
######################  STUFF I ADDED BELOW  ##################################################
#############################################################################################

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"


###############
### aliases ###
###############

alias df='df -h'
alias h='history'
alias d='cd /home/iceni60/Desktop'
alias duck='du -skc * | sort -rn'
alias cpuu="ps -e -o pcpu,cpu,nice,state,cputime,args --sort pcpu | sed '/^ 0.0 /d'"
alias memu='ps -e -o rss=,args= | sort -b -k1,1n | pr -TW$COLUMNS'
alias pg='ps aux | grep'  #requires an argument

# apt
#alias search='apt-cache search'
#alias agi='sudo apt-get install'
#alias agr='sudo apt-get remove'
#alias agu='sudo apt-get update'
#alias agg='sudo apt-get upgrade'
#alias sources='sudo gedit /etc/apt/sources.list'

# interactive
alias cp='cp -i'
alias mv='mv -i'
alias rm='mv --target-directory=$HOME/.Trash/'

# Directory navigation aliases
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias .....='cd ../../../..'

# Unpacking aliases
alias untarbz2='tar -xvfj'
alias untargz='tar -xvfz'

# display facts of the day
alias today='grep -h -d skip `date +%m/%d` /usr/share/calendar/*'

# network
alias net1='watch --interval=2 "sudo netstat -apn -l -A inet"'
alias net2='watch --interval=2 "sudo netstat -an --inet --inet6"'  
alias net3='sudo lsof -i'
alias net4='sudo netstat -ano -l -A inet'
alias net5='watch --interval=2 "sudo netstat -tulpan"'
alias net6='sudo netstat -tulpan'
alias net7='watch --interval=2 "sudo netstat -utapen"'
alias ping='ping -c 10'

# listings
alias ls='ls --color=auto'
alias lls='ls -l -h -g -F --color=auto'
alias lc='ls -CF'
alias ll='ls -l'
alias lsp='ls -p'
alias lss='ls -shax'
alias lsss='ls -shax | sort -rn'
alias lst='ls -alt'
alias lst20='ls -alt | head -20'

# scripts
alias calc='sh /home/iceni60/scripts/calc.sh'
alias whatsmyip='/home/iceni60/scripts/whatsmyip.sh'

# chmod commands
alias mx='chmod a+x'
alias 000='chmod 000'
alias 644='chmod 644'
alias 755='chmod 755'

# lynx web browser
alias bbc='lynx -term=vt100 http://news.bbc.co.uk/text_only.stm'
alias nytimes='lynx -term=vt100 http://nytimes.com'
alias dmregister='lynx -term=vt100 http://desmoinesregister.com'

# WELCOME SCREEN
#######################################################

clear

echo -ne "Hello $USER today is "; date
echo -e "${WHITE}"; cal ; echo ""; 
echo -ne "${CYAN}";echo ""
echo -ne "${LIGHTBLUE}Uptime for this computer is ";uptime | awk /'up/ {print $3,$4}'


# NOTES
#######################################################

# To temporarily bypass an alias, we preceed the command with a \  
# EG:  the ls command is aliased, but to use the normal ls command you would 
# type \ls 

#################
### FUNCTIONS ###
#################

function    ff               { find . -name $@ -print; }

function    rmd              { rm -fr $@; }

function    osr              { shutdown -r now; }
function    osh              { shutdown -h now; }

function    mfloppy          { mount /dev/fd0 /mnt/floppy; }
function    umfloppy         { umount /mnt/floppy; }

function    mdvd             { mount -t iso9660 -o ro /dev/dvd /mnt/dvd; }
function    umdvd            { umount /mnt/dvd; }

function    mcdrom           { mount -t iso9660 -o ro /dev/cdrom /mnt/cdrom; }
function    umcdrom          { umount /mnt/cdrom; }

function    psa              { ps aux $@; }
function    psu              { ps  ux $@; }
function    lpsa             { ps aux $@ | p; }
function    lpsu             { ps  ux $@ | p; }

function    dub              { du -sclb $@; }
function    duk              { du -sclk $@; }
function    dum              { du -sclm $@; }

function    dfk              { df -PTak $@; }
function    dfm              { df -PTam $@; }
function    dfh              { df -PTah $@; }
function    dfi              { df -PTai $@; }

function    dmsg             { dmesg | p; }

#####################################
# ##### ENVIRONMENT VARIABLES ##### #
#####################################

declare -x HISTFILE=~/.bash_history
declare -x HISTCONTROL=ignoreboth
declare -x HISTFILESIZE=50
declare -x HISTSIZE=50




############################## ##################################
# ##### PROMPT SECTION ##### ####################################
############################## ##################################

##PS1="\[[32m\]\u:\w > \[[39m\]"
##PS1="\[[31m\][\[[32m\]\u\[[31m\]]\[[32m\]\w > \[[39m\]"
#PS1="\[[40;1;31m\][\[[1;32m\]\u\[[1;31m\]]\[[49;1;32m\]\w > \[[22;39m\]"
#PS1="\[[1;31m\][\[[1;32m\]\[[47m\]\u\[[1;31m\]\[[49m\]]\[[1;32m\]\w > \[[22;39m\]"
##PS1="\[[31m\][\[[36m\]\u\[[31m\]]\[[36m\]\w > \[[39m\]"

###################### the above is a separate prompt which can be used instead of below. NOTE: only ONE line at a time should be uncommented. so there are 5 different prompts above!!!!!

# color_name='\[\033[ color_code m\]'

rgb_restore='\[\033[00m\]'
rgb_black='\[\033[00;30m\]'
rgb_firebrick='\[\033[00;31m\]'
rgb_red='\[\033[01;31m\]'
rgb_forest='\[\033[00;32m\]'
rgb_green='\[\033[01;32m\]'
rgb_brown='\[\033[00;33m\]'
rgb_yellow='\[\033[01;33m\]'
rgb_navy='\[\033[00;34m\]'
rgb_blue='\[\033[01;34m\]'
rgb_purple='\[\033[00;35m\]'
rgb_magenta='\[\033[01;35m\]'
rgb_cadet='\[\033[00;36m\]'
rgb_cyan='\[\033[01;36m\]'
rgb_gray='\[\033[00;37m\]'
rgb_white='\[\033[01;37m\]'

rgb_std="${rgb_white}"

if [ `id -u` -eq 0 ]
then
    rgb_usr="${rgb_red}"
else
    rgb_usr="${rgb_green}"
fi

[ -n "$PS1" ] && PS1="${rgb_usr}`whoami`${rgb_std} \W ${rgb_usr}\\\$${rgb_restore} "

unset   rgb_restore   \
        rgb_black     \
        rgb_firebrick \
        rgb_red       \
        rgb_forest    \
        rgb_green     \
        rgb_brown     \
        rgb_yellow    \
        rgb_navy      \
        rgb_blue      \
        rgb_purple    \
        rgb_magenta   \
        rgb_cadet     \
        rgb_cyan      \
        rgb_gray      \
        rgb_white     \
        rgb_std       \
        rgb_usr

```
i love it. it even has a message for me when i first open a terminal. i got the whatsmyip and bash calculator from this link -
[http://www.bashscripts.org/downloads/Scripts/crouse/](http://www.bashscripts.org/downloads/Scripts/crouse/)

i just made it right now after i accidentally wiped my HDD and lost all my OS's and i hadn't backed anything up, not even my bookmarks :rolleyes: 

if there are any mistakes, or something which might be done better another way will someone let me know?

---

### Post by mlissner on 2007-02-23
po0f - sorry for the long time with no response. I had stopped reading this thread for a time.

The difference between running something like:
alias rm='rm -i'; alias cp='cp -i'

and something like:
alias rm='rm -i' && alias cp='cp -i'

Is that if alias rm='rm -i' fails in the first example, no harm done; alias cp='cp -i' still gets run.

However, in the second example, alias cp='cp -i' will run ONLY if alias rm='rm -i' returns an exit code of zero. Thus, if you screw up the alias rm='rm -i' in the second example, neither of your aliases will get processed, which I believe is undesired...

It's more applicable to times when you're doing something like:
grep $USER * > /dev/null && echo 'ALERT: Your username is in a file!'

Which would search for your username in all the files in the current directory (duh), and then if (and only if) it found some, it would return an alert.

Help?

---

### Post by picpak on 2007-02-23
Don't use vim, I don't have a .vimrc.

Here's my .bashrc:

```
source ~/.bash_aliases
PS1='\u@\h:\w\$ 
```

...Nothing to see there. My .bash_aliases:

```
alias kill='pkill'
alias apt='sudo apt-get install'
alias remove='sudo apt-get remove'
alias search='apt-cache search'
alias edit='mousepad'
alias suedit='sudo mousepad'
alias i='sudo dpkg -i'
alias update='sudo apt-get update'
alias upgrade='sudo apt-get upgrade'
alias clean='sudo apt-get clean'
alias df='df -Hl'
alias home='cd ~'
alias mktar='tar -cvf'
alias mkbz2='tar -cvjf'
alias mkgz='tar -cvzf'
alias untar='tar -xvf'
alias unbz2='tar -xvjf'
alias ungz='tar -xvzf'
alias xorg.conf='sudo mousepad /etc/X11/xorg.conf'
alias sources.list='sudo mousepad /etc/apt/sources.list'
```

oh, and regarding dotfiles.com...whoever posted the .nanorc for sources.list is awesome. Check it out!

[[IMG]http://img145.imageshack.us/img145/7287/sourceslistrr1.th.png[/IMG]](http://img145.imageshack.us/my.php?image=sourceslistrr1.png)

---

### Post by pluckypigeon on 2009-09-24
anyone else??:):P

---

### Post by dragos240 on 2009-09-24
Bashrc:
PATH=/usr/local/bin
export PATH

---

### Post by schauerlich on 2009-09-24
> **dragos240 said:**
> Bashrc:
PATH=/usr/local/bin
export PATH

... you don't have /bin or /sbin in your $PATH?

---

### Post by -grubby on 2009-09-24
> **dragos240 said:**
> Bashrc:
PATH=/usr/local/bin
export PATH

Uhh...

---

### Post by dragos240 on 2009-09-24
:p

---

### Post by kk0sse54 on 2009-09-24
> Bashrc:
PATH=/usr/local/bin
export PATH 

An annoying feature but last time I checked didn't most linux distros install their binaries in /usr/bin as default instead of /usr/local/bin?

---

### Post by schauerlich on 2009-09-24
> **C!oud said:**
> An annoying feature but last time I checked didn't most linux distros install their binaries in /usr/bin as default instead of /usr/local/bin?

He apparently likes manually specifying all commands he runs that aren't in /usr/local/bin. Such as a lot of them.

---

### Post by PurposeOfReason on 2009-09-24
I've been looking for this vim theme forever but I've asked the uploader enough questions already, lol. I've just been revamping my desktop for winter/fall.

[http://supertrain.deviantart.com/art/xmonad-9-4-09-135909391](http://supertrain.deviantart.com/art/xmonad-9-4-09-135909391)

---

