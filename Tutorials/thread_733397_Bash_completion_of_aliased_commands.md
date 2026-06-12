---
title: "Bash completion of aliased commands"
date: 2008-03-23
forum: Tutorials
---

### Post by olejorgen on 2008-03-23
**Problem:** When you alias some command, custom completion no longer works.
Eg.
```

alias agi='sudo apt-get install'
agi fire<tab> # does not work
```
This pretty much removes the advantage of having the alias in the first place. Especially when you want to install libgnome-settings-daemon-dev 8-[

**Solution:**
Most completers are defined as a bash function. My solution wraps the original completer. This obviously only works for function completers. (ie. complete -F).

This should in principle work on any distribution with a recent bash and the completion pacackge. It's tested on feisty.

make-completion-wrapper.sh :
```
# Author.: Ole J
# Date...: 23.03.2008
# License: Whatever

# Wraps a completion function
# make-completion-wrapper <actual completion function> <name of new func.>
#                         <command name> <list supplied arguments>
# eg.
# 	alias agi='apt-get install'
# 	make-completion-wrapper _apt_get _apt_get_install apt-get install
# defines a function called _apt_get_install (that's $2) that will complete
# the 'agi' alias. (complete -F _apt_get_install agi)
#
function make-completion-wrapper () {
	local function_name="$2"
	local arg_count=$(($#-3))
	local comp_function_name="$1"
	shift 2
	local function="
function $function_name {
	((COMP_CWORD+=$arg_count))
	COMP_WORDS=( "$@" \${COMP_WORDS[@]:1} )
	"$comp_function_name"
	return 0
}"
	eval "$function"
	echo $function_name
	echo "$function"
}
```
This will wrap a completer, adjusting the aliased arguments. Save it in a file called make-completion-wrapper.sh or add it to your ~/.bashrc file

To find out what the completer function is called:
Open a terminal and type:
```
complete -p <command name>
```
Example:
```

$ complete -p apt-get
complete [color="red"]-o filenames[/color] -F [color="blue"]_apt_get[/color] apt-get
$ complete -p oocalc 
complete [color="red"]-o filenames -d -X '.[^./]*'[/color] -F [color="blue"]_ooexp_[/color] oocalc
```
The blue output is the name of the completer function, and the red is extra information. If -F is missing you can not use this method to wrap the completer.

As an example of usage lets add completion to alias agi='apt-get install' and alias acsh='apt-cache show'
Add this to your ~/.bashrc :
```

# ...
. /home/me/path-to-make-completion-wrapper.sh # or the content of make-completion-wrapper.sh
# aliases and completion code:
alias [color="brown"]agi[/color]='[color="green"]sudo apt-get install[/color]'
make-completion-wrapper [color="blue"]_apt_get[/color] _agi [color="green"]apt-get install[/color]
complete [color="red"]-o filenames[/color] -F _agi [color="brown"]agi[/color]
alias acsh='apt-cache show'
make-completion-wrapper _apt_cache _acsh apt-cache show
complete -o filenames -F _acsh acsh

```
- Note that we've duplicted the red output from complete -p.
- _agi and _acsh are arbitrary names, but to avoid name crashes, you should pick something distinct.

If you just want to test if it works, paste the above code (substitute path to make-completion-wrapper.sh first) in a terminal and try to type ```
agi fire<tab><tab>
```

Just remove the changes in your ~/.bashrc if you want to remove the completion or if something went wrong.

**Related information**
[http://ubuntuforums.org/showthread.php?t=392508&highlight=bash+completion](http://ubuntuforums.org/showthread.php?t=392508&highlight=bash+completion)
[http://www.debian-administration.org/articles/316](http://www.debian-administration.org/articles/316)
[http://www.debian-administration.org/articles/317](http://www.debian-administration.org/articles/317)

PS: It shoud be possible to completely automate this process by parsing the output from **complete**

---

### Post by andr3w on 2009-01-16
Thanks very much. This is awesome.

---

### Post by benjamin-agaric on 2009-07-13
When I followed these steps for "gv" aliasing "gvim" it did not work:

```

# Autocomplete made to work for alias gv="gvim"
# $ complete -p gvim
complete -o filenames -F _filedir_xspec gvim
 . /home/ben/customhome/make-completion-wrapper.sh
alias gv='gvim'
make-completion-wrapper _filedir_xspec _gv gvim
complete -o filenames -F _gv gvim

```

source ~/.bashrc

produces

```

_gv

function _gv {
	((COMP_CWORD+=0))
	COMP_WORDS=( gvim ${COMP_WORDS[@]:1} )
	_filedir_xspec
	return 0
}

```

And the completion still doesn't work.  Funny, I don't remember having to do anything for autocompletion to work for aliased functions in ubuntu 8.

Mayhaps i am working too hard to try to save two letters...

---

### Post by lian1238 on 2009-07-30
Thank you! Works great.

---

### Post by balshetzer on 2009-11-24
Thanks for your post.

> **olejorgen said:**
> PS: It shoud be possible to completely automate this process by parsing the output from **complete**

I followed through on your suggestion and wrote a snippet that will run through all your aliases and add a wrapper where possible:

[http://stackoverflow.com/questions/342969/how-do-i-get-bash-completion-to-work-with-aliases/1793178#1793178]("http://stackoverflow.com/questions/342969/how-do-i-get-bash-completion-to-work-with-aliases/1793178#1793178")

---

### Post by justmailnaveen on 2011-09-22
Does it still works. I mean on ubuntu 11.04

---

### Post by aihtdikh on 2012-03-08
> **benjamin-agaric said:**
> When I followed these steps for "gv" aliasing "gvim" it did not work:

*snip*

And the completion still doesn't work.  Funny, I don't remember having to do anything for autocompletion to work for aliased functions in ubuntu 8.

Mayhaps i am working too hard to try to save two letters...

I doubt you're still looking, three years later, but for searchers:
In the last line, you were telling complete to attach your new _gv function to the word 'gvim' - that should have been 'gv'.

However, you don't actually need this wrapper script for your case.
Because you are aliasing a single word for another single word, you can simply apply the original completion function (_filedir_xspec) directly:
```
complete -o filenames -F _filedir_xspec gv
```This wrapper is for cases where you are adding extra words to the alias, so the original function won't work by itself - you type "agi", for example, but the completion function expects to see both "apt-get" and also "install".

> **justmailnaveen said:**
> Does it still works. I mean on ubuntu 11.04

Yes, I'm using it happily on 11.10.
Only change I made was to remove the two 'echo' lines at the bottom - they are just for debugging.

Thanks olejorgen, much appreciated.

---

### Post by phistakis on 2012-05-30
cool wrapper..
i've started writing it into my bashrc in order to use all my git aliases, when i realized i have a lot of code reuse, so i wrote this function:

# usage: gitalias <alias> <original command>
function gitalias () {
alias $1="$2"
make-completion-wrapper _git _$1i $2
complete -o bashdefault -o default -o nospace -F _$1i $1
}

and now instead of writing 3 lines per alias i'm simply replacing
alias gc='git checkout
with:
gitalias gc 'git checkout'

if you want to use this for anything other than git, just replace the '_git' in the middle with your completer function (or with $3...)

oh, and you might wanna change its name as well... :)

---

### Post by verqix on 2012-10-20
[SIZE="2"][B]update:
Seems like this might have been the effect of . ~/.bashrc instead of reloading the terminal, leaving some old functions intact.

It might also be that it works when you use a function instead of an alias.[/B][/SIZE]

[SIZE="1"]I've tried to use this wrapper (slightly renamed by removing make to remove confusion) with:

[FONT="Fixedsys"]alias makeb='make "$@" | grep -i "built"'
completion-wrapper _make _makeb make
complete -o bashdefault -o default -o nospace -F _makeb makeb[/FONT]

Now when I type:

[FONT="Fixedsys"]makeb motor[/FONT]

without autocompletion, it makes the motor and outputs the lines where "built" appears. With autocompletion, I can autocomplete on command line correctly, but when I run the command I get:

[FONT="Fixedsys"]grep: motor: No such file or directory[/FONT]

This leads me to believe the command it executes is:

[FONT="Fixedsys"]make | grep -i "built" motor[/FONT]

Instead of:

[FONT="Fixedsys"]make motor | grep -i "built"[/FONT]

Now, I think there is a solution in passing on the parameters a certain way, but I don't see how that can be done right now. Perhaps someone else will find a way. In the meanwhile, I'll keep experimenting.[/SIZE]

---

### Post by Korn on 2013-02-17
Especially for git I have found this shortcut function which works better than make-completion-wrapper:
```
    __define_git_completion () {
    eval "
        _git_$2_shortcut () {
            COMP_LINE=\"git $2\${COMP_LINE#$1}\"
            let COMP_POINT+=$((4+${#2}-${#1}))
            COMP_WORDS=(git $2 \"\${COMP_WORDS[@]:1}\")
            let COMP_CWORD+=1

            local cur words cword prev
            _get_comp_words_by_ref -n =: cur words cword prev
            _git_$2
        }
    "
    }

    __git_shortcut () {
        type _git_$2_shortcut &>/dev/null || __define_git_completion $1 $2
        alias $1="git $2 $3"
        complete -o bashdefault -o default -o nospace -F _git_$2_shortcut $1
    }

__git_shortcut  ga   add
__git_shortcut  gb   branch
__git_shortcut  gc   commit
__git_shortcut  gd   diff
__git_shortcut  go   checkout
__git_shortcut  gcp  cherry-pick

```

Source: [https://github.com/bronson/dotfiles/blob/731bfd951be68f395247982ba1fb745fbed2455c/.bashrc#L81](https://github.com/bronson/dotfiles/blob/731bfd951be68f395247982ba1fb745fbed2455c/.bashrc#L81)

Problem with make-completion-wrapper and git was for "go" as "git checkout" for example:
git checkout <tab> shows a list of all branches.
While go <tab> shows a list of all files in the directory.

I think this is because the make-completion-wrapper function does not set COMP_LINE and COMP_POINT. Also _get_comp_words_by_ref is not called and so "cur words cword prev" are not set which are expected to be set by the _git_* functions.

Maybe the make-completion-wrapper function can be changed accordingly?

//edit
Also have a look at this discussion here:
[http://thread.gmane.org/gmane.comp.version-control.git/185184/focus=185232](http://thread.gmane.org/gmane.comp.version-control.git/185184/focus=185232)

//edit2
Edited the function to also work with cherry-pick (the git function is called _git_cerry_pick).
```
    __define_git_completion () {
         # Because cherry-pick has the function _git_cherry_pick
         n2=${2//-/_}
    eval "
        _git_$2_shortcut () {
            COMP_LINE=\"git $2\${COMP_LINE#$1}\"
            let COMP_POINT+=$((4+${#2}-${#1}))
            COMP_WORDS=(git $2 \"\${COMP_WORDS[@]:1}\")
            let COMP_CWORD+=1

            local cur words cword prev
            _get_comp_words_by_ref -n =: cur words cword prev
            _git_$n2
        }
    "
    }
```

//edit3
Ok, so finally I have only one function for creating the wrapper function:
```
#!/bin/sh
# Author.: Ole J
# Date...: 23.03.2008
# License: Whatever

# Wraps a completion function
# make-completion-wrapper <actual completion function> <name of new func.> <alias>
#                         <command name> <list supplied arguments>
# eg.
# 	alias agi='apt-get install'
# 	make-completion-wrapper _apt_get _apt_get_install apt-get install
# defines a function called _apt_get_install (that's $2) that will complete
# the 'agi' alias. (complete -F _apt_get_install agi)
#
#make-completion-wrapper _git_checkout _git_checkout_shortcut go git checkout
function make-completion-wrapper () {
	local comp_function_name="$1"
	local function_name="$2"
	local alias_name="$3"
	local arg_count=$(($#-4))
	shift 3
	local args="$*"
	local function="
function $function_name {
	COMP_LINE=\"$@\${COMP_LINE#$alias_name}\"
	let COMP_POINT+=$((${#args}-${#alias_name}))
	((COMP_CWORD+=$arg_count))
	COMP_WORDS=("$@" \"\${COMP_WORDS[@]:1}\")

	local cur words cword prev
	_get_comp_words_by_ref -n =: cur words cword prev
	"$comp_function_name"
	return 0
}"
	eval "$function"
#	echo $function_name
#	echo "$function"
}
    __git_shortcut () {
	# Because cherry-pick has the function _git_cherry_pick
	n2=${2//-/_}
        type _git_${n2}_shortcut &>/dev/null || make-completion-wrapper _git_$n2 _git_${n2}_shortcut $1 git $2
        complete -o bashdefault -o default -o nospace -F _git_${n2}_shortcut $1
    }

    __apt_cache_shortcut () {
        type _apt_cache_$2_shortcut &>/dev/null || make-completion-wrapper _apt_cache _apt_cache_$2_shortcut $1 apt-cache $2
        # is not executed automatically. Normally only on first apt-cache <tab>
        [ ! -f /usr/share/bash-completion/completions/apt-cache ] || source /usr/share/bash-completion/completions/apt-cache
        complete -F _apt_cache_$2_shortcut $1
    }
```

Saved this as /usr/local/bin/make-completion-wrapper and use it in my $HOME/.bashrc :
```
if [ -f /usr/local/bin/make-completion-wrapper ]; then
        . /usr/local/bin/make-completion-wrapper

        # qhe
        make-completion-wrapper _quilt_completion _qhe qhe quilt header -e
        complete -o filenames -F _qhe qhe
        # apt-policy
        __apt_cache_shortcut apt-policy policy
        # apt-show
        __apt_cache_shortcut apt-show show

        # __git_shortcut  gs   status # no completion for git status
        __git_shortcut  ga   add
        __git_shortcut  gb   branch
        __git_shortcut  gc   commit
        __git_shortcut  gd   diff
        __git_shortcut  go   checkout
        __git_shortcut  gcp  cherry-pick
fi
```

---

### Post by ninovolador on 2013-04-12
HELP! i',m sorry for reviving this old post, but this isn't (entirely) working for me!

Here is my output of "complete -p apt-get":
bash: complete: apt-get: no hay completado de especificación
(in english it would be "bash:complete: apt-get: no completion specification")

BUT when i do "apt-get <tab> <tab>" i still get the autocompletion feature. IN FACT, when i "complete -p apt-get" after that, i get  "complete -F _apt_get apt-get"

Then, my alias do autocomplete, but if i close that terminal, it does not do that anymore..

any clues?

---

### Post by Korn on 2013-04-13
Yes, this behavior also exists for apt-cache. It seems the function for bash completion only gets created at the first "apt-cache <tab>".
So I had to integrate this code in my [alias completion code]("https://gist.github.com/ckorn/4999102"):

> [ ! -f /usr/share/bash-completion/completions/apt-cache ] || source /usr/share/bash-completion/completions/apt-cache

The code you need is this:
> [ ! -f /usr/share/bash-completion/completions/apt-get ] || source /usr/share/bash-completion/completions/apt-get

Call this before you call "complete -F".

---

### Post by ninovolador on 2013-04-14
Thank you very much!!!

---

