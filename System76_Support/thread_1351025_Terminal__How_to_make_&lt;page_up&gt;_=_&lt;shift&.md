---
title: "Terminal:  How to make &lt;page up&gt; = &lt;shift&gt; + &lt;page up&gt; ?"
date: 2009-12-09
forum: System76 Support
---

### Post by watchpocket on 2009-12-09
There are a couple of things I'd like to change in my (new, Karmic, gnome) terminal.

First, I'd like to be able to scroll with just the **<page up**> and **<page down> **keys by themselves, without having to also press **<shift>**.  (The way you can in Firefox.)

Where/how can I re-map or whatever?

Also, I've gotten very accustomed to (on the old MacSSH) a situation where, when editing a file in Vim, when I exit Vim, I still see the file exactly as I did before exiting (the file still occupying the whole window, or almost the whole window), except that everything has shifted up one (or two) line(s) to make room for my shell prompt, which appears at the bottom of the terminal window.  

I can still sit and ponder the file after I've closed out of the editor.

With gnome terminal, when I exit Vim, WHOOSH, the file disappears completely and the screen (somewhat rudely, to me) returns to exactly how it looked before I opened the file.  This bugs me, because I didn't tell it to do that.

I would very much like to have the previous situation with my terminal, so that when I exit a file in Vim, or Less, or More, etc, (esp. Vim), the file *stays there*, with my Zsh prompt at the bottom.

Thanks for any suggestions.

---

### Post by hal10000 on 2009-12-10
> Where/how can I re-map or whatever?

Maybe you're lucky with the **bind** command. It is a shell-builtin function and this is what the bash manpage says about bind:
```

bind [-m keymap] [-lpsvPSV]
       bind [-m keymap] [-q function] [-u function] [-r keyseq]
       bind [-m keymap] -f filename
       bind [-m keymap] -x keyseq:shell-command
       bind [-m keymap] keyseq:function-name
       bind readline-command
              Display  current  readline key and function bindings, bind a key sequence to a readline function or macro, or set a
              readline variable.  Each non-option argument is a command as it would appear in .inputrc, but each binding or  com&#8208;
              mand  must be passed as a separate argument; e.g., &#8217;"\C-x\C-r": re-read-init-file&#8217;.  Options, if supplied, have the
              following meanings:
              -m keymap
                     Use keymap as the keymap to be affected by the subsequent bindings.   Acceptable  keymap  names  are  emacs,
                     emacs-standard, emacs-meta, emacs-ctlx, vi, vi-move, vi-command, and vi-insert.  vi is equivalent to vi-com&#8208;
                     mand; emacs is equivalent to emacs-standard.
              -l     List the names of all readline functions.
              -p     Display readline function names and bindings in such a way that they can be re-read.
              -P     List current readline function names and bindings.
              -v     Display readline variable names and values in such a way that they can be re-read.
              -V     List current readline variable names and values.
              -s     Display readline key sequences bound to macros and the strings they output in such a way that  they  can  be
                     re-read.
              -S     Display readline key sequences bound to macros and the strings they output.
              -f filename
                     Read key bindings from filename.
              -q function
                     Query about which keys invoke the named function.
              -u function
                     Unbind all keys bound to the named function.
              -r keyseq
                     Remove any current binding for keyseq.
              -x keyseq:shell-command
                     Cause shell-command to be executed whenever keyseq is entered.

              The return value is 0 unless an unrecognized option is given or an error occurred.

```

I have no experience with this command, but i hope this can help you out.

---

### Post by drewbenn on 2009-12-10
I was curious, because these were things that I'd kind of like, but never seemed critical enough to go investigate.  I did a little looking and found this: [http://www.shallowsky.com/linux/noaltscreen.html](http://www.shallowsky.com/linux/noaltscreen.html) .  Aliasing ls to 'less -X' in my .bashrc (note: doing it like that link suggested didn't work for me) is the only one I've tried myself, though.  Good luck...

---

