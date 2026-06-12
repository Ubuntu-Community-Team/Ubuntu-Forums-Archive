---
title: "Post your .vimrc w/ screenshot"
date: 2005-10-12
forum: The Cafe
---

### Post by Ride Jib on 2005-10-12
I'm enjoying the tweaking ability of vim, and would like to see what schemes and features others have going on. I'll get it started....
```
set nocompatible                "Use Vim extensions
set backspace=indent,eol,start  "More powerful backspacing
set textwidth=80                "Wrap at 80 char
"set number                      "Line numbers
set nobackup                    "No backup file
set ruler                       "Show cursor position always
set showmode                    "Tell when in insert mode
set showmatch                   "Show matching () {} etc
set hlsearch                    "Highlight what is searched for
set incsearch                   "Highlight as you type

if &t_Co > 2
  syntax on
endif

augroup filetype
        au!
        au! BufRead,BufNewFile *.ypp    set filetype=yacc
        au! BufRead,BufNewFile *.y      set filetype=yacc
        au! BufRead,BufNewFile *.treecc set filetype=yacc
        au! BufRead,BufNewFile *.flex   set filetype=lex
augroup END

set bg=dark
hi clear
if exists("syntax_on")
  syntax reset
endif


"Allowable colors: red, yellow, green, blue, magenta,
"                  cyan, white, black, gray
hi Normal ctermfg=white ctermbg=none
hi ErrorMsg ctermfg=white ctermbg=lightblue
hi Visual ctermfg=lightblue ctermbg=fg cterm=reverse
hi VisualNOS ctermfg=lightblue ctermbg=fg cterm=reverse,underline
hi Todo ctermfg=red ctermbg=darkblue
hi Search ctermfg=white ctermbg=darkblue
hi IncSearch ctermfg=darkblue ctermbg=gray
hi SpecialKey ctermfg=darkcyan
hi Directory ctermfg=cyan
hi Title ctermfg=magenta cterm=bold
hi WarningMsg ctermfg=red
hi WildMenu ctermfg=yellow ctermbg=black cterm=none
hi ModeMsg ctermfg=lightblue
hi MoreMsg ctermfg=darkgreen ctermfg=darkgreen
hi Question ctermfg=green cterm=none
hi NonText ctermfg=darkblue
hi StatusLine ctermfg=blue ctermbg=gray cterm=none
hi StatusLineNC ctermfg=black ctermbg=gray cterm=none
hi VertSplit ctermfg=black ctermbg=gray cterm=none
hi Folded ctermfg=darkgrey ctermbg=black cterm=bold
hi FoldColumn ctermfg=darkgrey ctermbg=black cterm=bold
hi LineNr ctermfg=gray cterm=none
hi DiffAdd ctermbg=darkblue cterm=none
hi DiffChange ctermbg=magenta cterm=none
hi DiffDelete ctermfg=blue ctermbg=cyan
hi DiffText cterm=bold ctermbg=red
hi Cursor ctermbg=brown
hi lCursor ctermbg=darkgreen

hi Comment ctermfg=lightgreen
hi Constant ctermfg=cyan cterm=none
hi Identifier ctermfg=gray cterm=none
hi Statement ctermfg=red cterm=bold
hi PreProc ctermfg=yellow cterm=bold
hi Type ctermfg=darkyellow cterm=none
hi Special ctermfg=magenta cterm=none
hi Underlined cterm=underline
hi Ignore cterm=none

```

---

### Post by z0mbie on 2008-04-12
I really like your vimrc. I was hoping for more posts on this topic.

---

### Post by fedex1993 on 2008-04-12
Yeah i using vim now that i know that it is customizable i think imight use it as a default text editor

---

### Post by Shii on 2008-04-13
command Crlf :%s/^M//g  (^M = Ctrl+V Ctrl+M)

Good way to "fix" your Windows text files :)

Type :Crlf and all the ^Ms will go away. It will also make the file unreadable in Windows Notepad, but you don't care about Notepad, right?

---

### Post by Random_Dude on 2011-07-13
Well I'm not sure if this is considerate necromancy.
Since there is an .emacs file thread, why not revive this one too?

Here is my .vimrc:

```
"==============================================================="
"                          General Settings
"==============================================================="
" Disable behaviour like vi, must be the first line!!!!
:set nocompatible

"will replace backslashes with forward slashes when expanding file names
:set shellslash

"Line Numbers
:set number

"Enable mouse in the CLI
:set mouse=a

" Syntax highlight
:syntax on 

"Color Scheme
if has('gui_running')
    :colo wombatCHANGED
else
    :set t_Co=256
    :colorscheme peachpuff
endif

"Search
:set hlsearch
:set incsearch "Incremental Search

"Turn off text warp
:set tw=0 wrap linebreak

"Identing
set smartindent            " Smartly autoindents
set cindent                " Strictly indents only for .c files
set expandtab               " Convert Tab to spaces
set tabstop=4              " Tab is 4 spaces
set shiftwidth=4           " Number of spaces of autoindent


"Automatically save and load folds
set viewoptions-=options
augroup vimrc
    autocmd BufWritePost *
    \   if expand('%') != '' && &buftype !~ 'nofile'
    \|      mkview
    \|  endif
    autocmd BufRead *
    \   if expand('%') != '' && &buftype !~ 'nofile'
    \|      silent loadview
    \|  endif
augroup END

" Hide the mouse pointer while typing
:set mousehide

" Make the command-line completion better
:set wildmenu



"==============================================================="
"                       General Keybindings
"==============================================================="

"Remap ESC key
"inoremap <Tab> <Esc>
ino jj <esc>
cno jj <c-c>

let mapleader="," "change the leader to be a comma vs slash

"Load Most Recently Used Files
map <F2> :MRU<kEnter>

" Toggle the NERDTree on an off with F3
nmap <F3> :NERDTreeToggle<CR>
" Close the NERDTree with Shift-F3
nmap <S-F3> :NERDTreeClose<CR>

"open/close the taglist 
map <F4> <Esc>:TlistToggle<cr>

"Map different NERDComent keybinding
nmap gc <Leader>ci
vmap gc <Leader>ci

"Map terminal
map <F12> <Esc>:vs<kEnter>:ConqueTerm bash<kEnter>

"clear last search highlighting
nmap <C-h> :noh<kEnter>


"Paste over a visually selected area without having the selection placed in the default register
function! RestoreRegister()
  let @" = s:restore_reg
  return ''
endfunction

function! s:Repl()
    let s:restore_reg = @"
    return "p@=RestoreRegister()\<cr>"
endfunction

" NB: this supports "rp that replaces the selection by the contents of @r
vnoremap <silent> <expr> p <sid>Repl()

" shortcuts for copying to clipboard
nmap <leader>y "+y

" copy the current line to the clipboard
nmap <leader>Y "+Y
nmap <leader>p "+p


"Remap keys to delete without saving in the register
noremap d "_d
noremap dd "_dd
noremap D "_D
noremap s "_s

"==============================================================="
"                                LaTeX
"==============================================================="
" REQUIRED. This makes vim invoke Latex-Suite when you open a tex file.
filetype plugin on

" IMPORTANT: win32 users will need to have 'shellslash' set so that latex
" can be called correctly.
set shellslash

" IMPORTANT: grep will sometimes skip displaying the file name if you
" search in a singe file. This will confuse Latex-Suite. Set your grep
" program to always generate a file-name.
set grepprg=grep\ -nH\ $*

" OPTIONAL: This enables automatic indentation as you type.
filetype indent on

" OPTIONAL: Starting with Vim 7, the filetype of empty .tex files defaults to
" 'plaintex' instead of 'tex', which results in vim-latex not being loaded.
" The following changes the default filetype back to 'tex':
let g:tex_flavor='latex'

"Define PDF as default format to .tex
let g:Tex_DefaultTargetFormat = 'pdf'
let g:Tex_MultipleCompileFormats='pdf, aux'

"Count words in LaTeX (NOT WORKING PROPERLY)
function! WC()
    let filename = expand("%")
    let cmd = "texcount -1 " . filename
    let result = system(cmd)
    echo result 
endfunction

command WC call WC()



"==============================================================="
"                              MATLAB
"==============================================================="

"Correct settings in order to use the matchit.vim script
source $VIMRUNTIME/macros/matchit.vim 

"Integration of the mlint Matlab code checker with the :make command
autocmd BufEnter *.m    compiler mlint



```Cheers :cool:

---

