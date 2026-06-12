---
title: "HOWTO: Colour syntax highlighting in nano"
date: 2005-09-03
forum: Tutorials
---

### Post by Taoism on 2005-09-03
**Please note:** When I previewed this post, the boards are adding large space gaps into the regular expression examples that have long lines.  You will have to remove the gaps for the words that I split by the gaps to be correctly found by the regular expression.

I'm not an uber Linux person, but I did find out about how to add syntax highlighting to files when using nano as an editor in a terminal window, and thought I would add to this forum :)

[nano](http://www.nano-editor.org/) is an editor you run from inside a terminal window.  If you can't get into X or are simply using a terminal and don't want to be bothered with gedit, then nano is an easy, and simple editor to use.

You can add syntax highlighting to certain files you edit in nano in an easy way.

By default the nano documentation is stored in /usr/share/doc/nano:

```

youngka@quidditch:~
Sat Sep 03 21:01:15 $ cd /
youngka@quidditch:/
Sat Sep 03 21:31:40 $ sudo find -name nano
Password:
./usr/share/doc/nano
./usr/share/nano
./usr/bin/nano
./usr/lib/menu/nano
./bin/nano
youngka@quidditch:/
Sat Sep 03 21:31:59 $

```

we want a file from a subdirectory of the nano documentation:

```

Sat Sep 03 21:31:59 $ ls -al /usr/share/doc/nano
total 188
drwxr-xr-x     3 root root  4096 2005-08-23 23:08 .
drwxr-xr-x  1085 root root 28672 2005-09-03 13:54 ..
-rw-r--r--     1 root root  1523 2003-12-29 00:04 AUTHORS
-rw-r--r--     1 root root  3419 2002-07-18 20:08 BUGS.gz
-rw-r--r--     1 root root 10033 2004-11-18 21:38 changelog.Debian.gz
-rw-r--r--     1 root root 53142 2004-06-27 21:36 changelog.gz
-rw-r--r--     1 root root  2179 2004-11-18 21:39 changelog.l10n.gz
-rw-r--r--     1 root root   501 2004-11-18 21:38 copyright
drwxr-xr-x     2 root root  4096 2005-09-03 15:29 examples
-rw-r--r--     1 root root 31246 2004-06-27 21:38 faq.html
-rw-r--r--     1 root root 13136 2004-06-27 21:36 NEWS.gz
-rw-r--r--     1 root root  2354 2003-03-24 07:08 README
-rw-r--r--     1 root root   427 2004-11-18 21:38 README.Debian
-rw-r--r--     1 root root  2870 2003-12-29 00:04 THANKS
-rw-r--r--     1 root root  2032 2003-12-29 00:04 TODO
-rw-r--r--     1 root root  1066 2003-03-24 07:09 UPGRADE
youngka@quidditch:/
Sat Sep 03 21:34:03 $ ls -al /usr/share/doc/nano/examples/
total 16
drwxr-xr-x  2 root root 4096 2005-09-03 15:29 .
drwxr-xr-x  3 root root 4096 2005-08-23 23:08 ..
-rw-r--r--  1 root root 7699 2003-12-27 10:35 nanorc.sample
youngka@quidditch:/
Sat Sep 03 21:34:13 $

```

To be fair, the nanorc.sample file was actually a .gz file that I extracted by simply typing:

```

gunzip <filename>

```

Copy the nanorc.sample file to your home directory and rename it:
```

youngka@quidditch:/
Sat Sep 03 21:34:27 $ cp /usr/share/doc/nano/examples/nanorc.sample ~
youngka@quidditch:/
Sat Sep 03 21:37:24 $ mv ~/nanorc.sample ~/.nanorc
youngka@quidditch:/
Sat Sep 03 21:38:44 $ 

```

In a slightly ironic and amusing (to me at least) twist, I then opened .nanorc in gedit to make my initial edits to the file.  Consult the documentation for nano for what all the early stuff in the config file means.  What we want is the end of the file.

Near the end of the file are several examples of syntax definitions for different types of files.  A simple one to quickly see and verify the colouring works is the xorg.conf syntax definition from a wiki I found:

```

## syntax highlighting in xorg.conf
##
syntax "xorg" "xorg\.conf$"
color brightwhite "(Section|EndSection|Sub[sS]ection|EndSub[sS]ection)"
# keywords
color yellow "[^A-Za-z0-9](Identifier|Screen|InputDevice|Option|RightOf|LeftOf|Driver|RgbPath|FontPath|ModulePath|Load|VendorName|ModelName|BoardName|BusID|Device|Monitor|DefaultDepth|View[pP]ort|Depth|Virtual|Modes|Mode|DefaultColorDepth|Modeline|\+vsync|\+hsync|HorizSync|VertRefresh)[^A-Za-z0-9]"
# numbers
color magenta "[0-9]"
# strings
color green ""(\\.|[^\"])*""
# comments
color blue "#.*"

```

Paste it into the end of the .nanorc, and save the file (if in gedit) - no need to close it.  Then in a terminal window type:

```

youngka@quidditch:/
Sat Sep 03 21:37:40 $ nano /etc/X11/xorg.conf
youngka@quidditch:/
Sat Sep 03 21:43:27 $

```

And you should see the file is colourized for easier editing from within nano!  I didn't like the colours the default had.   I'm a bit of a throwback to C programming in Borland, so I always set all my editors to show me all comments in green (and italic if possible).  So, I went back to the .nanorc file that was still open in gedit and changed the comment color for the xorg.conf syntax file to green (and adjust a couple other colours to look better in my eyes).

I played around with my version of the xorg.conf file to look like this (my terminal is black background with green text by default):
```

## syntax highlighting in xorg.conf
##
syntax "xorg" "xorg\.conf$"
color brightwhite "(Section|EndSection|Sub[sS]ection|EndSub[sS]ection)"
# keywords
color yellow "[^A-Za-z0-9](Identifier|Screen|InputDevice|Option|RightOf|LeftOf|Driver|RgbPath|FontPath|ModulePath|Load|VendorName|ModelName|BoardName|BusID|Device|Monitor|DefaultDepth|View[pP]ort|Depth|Virtual|Modes|Mode|DefaultColorDepth|Modeline|\+vsync|\+hsync|HorizSync|VertRefresh)[^A-Za-z0-9]"
# numbers
color magenta "[0-9]"
# strings
color white ""(\\.|[^\"])*""
# comments
color green "#.*"

```

Not much of a change, but a small one, and it is easy to do.  If you make a mistake with a regular expression, nano will pause in loading the file you want to edit to alert you to the error.

If you play with the colour definitions and make your own, for file types you prefer, it is important to remember that nano applies the color highlighting in a top-down fashion, from first to last (which is why all the definitions usually put the comment regex as the last line of the syntax section for a given file type.

After playing with nano for a while, I have come up with a syntax definition I would like to share.

First though, I did find another site (wiki) with three definitions listed:
[Nano Context Highlighting](http://gentoo-wiki.com/TIP_Nano_Context_Highlighting) is a wiki entry on a Gentoo wiki.  This is the wiki that I got the xorg.conf syntax definition from.

I decided to try and write my own syntax definition, and one file that I do interact with on occassion in a terminal is the apache configuration file (apache2.conf or httpd.conf). 

In the spirit of sharing, here is the syntax file I came up with.  I am not saying it is the best that can be done, and I do plan to tweak it more, but here it is none-the-less:

```

## Apache httpd.conf highlighting
##
#how to add sites-enabled files?  "default" is too generic to keep in here I think
syntax "Apache2" "apache2\.conf$" "httpd\.conf$" "default"

# for reference... I don't want to keep scrolling back up ;)
## Legal colors: white, black, red, blue, green, yellow, magenta, cyan.
## You may use the prefix "bright" to mean a stronger color highlight.

# Apache Directives?
color brightwhite "(ServerRoot|(Lock|Pid)File|Timeout|(Max)?KeepAlive(Requests|Timeout)?)"
color brightwhite "(User|Group|LogFormat|ErrorLog|Include|(Script)?Alias)"
color brightwhite "(ErrorDocument|AccessFileName|UseCanonicalName|TypesConfig|DefaultType)"
color brightwhite "(HostnameLookups|IndexOptions|(Readme|Header)Name|LanguagePriority)"
color brightwhite "(AddIcon(ByEncoding|ByType)?|DefaultIcon|IndexIgnore|BrowserMatch)"
color brightwhite "(Add(Encoding|Language|(Default)?Charset|Type|Handler)|DirectoryIndex)"
color brightwhite "(DocumentRoot|Server(Admin|Signature)|LogLevel|CustomLog)"
color brightwhite "((Force)?LanguagePriority|NameVirtualHost)"

# These are all config tokens that appear inside module/directory brackets
color yellow "(SetHandler|Order|Deny|Allow|SetOutputFilter|AllowOverride|FileInfo|AuthConfig|Limit)"
color yellow "([^A-Z0-9a-z]Options|Indexes|(\+|\-)?SymLinksIfOwnerMatch|Includes(NoExec)?|(\+|\-)?MultiViews)"
color yellow "(None|allow,deny|deny,allow|(allow)? from (all)?|Prefer|Fallback)"
color yellow "(Add(Handler|OutputFilter)|NumServers|AcceptMutex)"
color yellow "((Min|Max)Spare(Threads|Servers)|Start(Threads|Servers))"
color yellow "(MaxClients|(Max)?ThreadsPerChild|MaxRequestsPerChild)"
color yellow "(FancyIndexing|VersionSort|ExecCGI|FollowSymLinks)"

# Highlight boolean toggles (i.e. KeepAlive On)
color brightred "(On|Off)[[:space:]]*$"

#log levels
color brightred "[[:space:]]+(debug|info|notice|warn|error|crit|alert|emerg)[[:space:]]*$"
color brightred "[[:space:]]+(combined|common|referer|agent)[[:space:]]*$"

#BrowserMatch directives
color brightred "[[:space:]]+(redirect\-carefully|nokeepalive)[[:space:]]*"
color brightred "[[:space:]]+(force\-response\-1\.0)[[:space:]]*"
color brightred "[[:space:]]+(downgrade\-1\.0)[[:space:]]*"

#AddType application params
color brightred "[[:space:]]+application/[a-zA-Z\-]+[[:space:]]*"

#AddHandler param
color brightred "[[:space:]]+type-map[[:space:]]*"

# Numbers 
color magenta "[[:space:]]+[0-9]+[[:space:]]*"

# IP Addresses
color magenta "(/)?(2[0-5]{2}|1[0-9]{2}|[1-9][0-9]|[1-9])(\.(2[0-5]{2}|1[0-9]{2}|[1-9][0-9]|[0-9])){3}([[:space:]]+::(2[0-5]{2}|1[0-9]{2}|[1-9][0-9]|[0-9])/(2[0-5]{2}|1[0-9]{2}|[1-9][0-9]|[0-9]))?"

# Stolen from the HTML example further up this file
color brightcyan start="<" end=">"

# strings
color white ""(\\.|[^\"])*""

# Unix-based paths
# can't use \] in the regex for some reason?!? Maybe a bug?
# this is preventing a 100% "to the end of the line" match for a few
# lines (the trailing characters from ] to the EOL are not highlighted.
# if anyone knows how to make it work, let me know.. ;)
color white "[[:space:]]+(/[/\[\^#A-Za-z0-9\.\*\_\-]+)+"

# Comments - match 0 or more spaces/tabs preceding the comment
color green "^[[:space:]]*#.*"


```

One thing I did notice is that capture-suppression in regular expressions does not work in nano - i.e. I tried something like (?:KeepAlive )(On|Off) and the ?: kept resulting in errors.  I think there is also a (maybe) a bug with the right square bracket not being able to be escaped in a class definition : [\[] will work, but [\]] throws an error.

If anyone else has some sybtax definitions for nano they could share, please add them to this thread!

Here is one more I found for the road (don't remember where, sorry):

```

## Here is an example for shell scripts
##
 syntax "shellscript" "\.sh$" ".bashrc"
 color brightgreen "^[a-zA-Z_0-9]+\(\)"

 color brightwhite "\<(case|do|done|elif|else|esac|exit|fi|for|function|if|in|local|read)\>"
 color brightwhite "\<(return|select|shift|then|time|until|while)\>"
 color brightwhite "(\{|\}|\(|\)|\;|\]|\[|`|\\|\$|<|>|!|=|&|\|)"
 color brightwhite "-(e|d|f|r|g|u|w|x|L)\>"
 color brightwhite "-(eq|ne|gt|lt|ge|le|s|n|z)\>"
 
 # commands
 color brightblue "\<make\>" 
 color brightblue "\<(alias|cat|cd|chmod|chown|cp|echo|env|eval|export|grep|install|let|ln|ls)\>"
 color brightblue "\<(mkdir|mv|rm|sed|set|tar|touch|umask|unset)\>"
 # a program I installed
 color magenta "(figlet)"
 # variables?
 color brightred "\$\{?[a-zA-Z_0-9]+\}?"
 # strings?
 color brightyellow ""(\\.|[^\"])*"" "'(\\.|[^'])*'"
 # comments
 color green "#.*$"


```

Thanks for reading and I hope you found this at least interesting, if not useful!

Cheers,
Keith.

---

### Post by Taoism on 2005-09-04
I did a syntax for highlighting a Conky (.conkyrc) file:

```

## Conky config highlighting
## 
syntax "Conky" ".conkyrc$"

# keywords
color brightblue "(use_spacer|background|use_xft|xftfont|xftalpha)" 
color brightblue "(mail_spool|update_interval|own_window)"
color brightblue "(double_buffer|minimum_size)"
color brightblue "(draw_(outline|borders|shades)|stippled_borders)"
color brightblue "border_(margin|width)"
color brightblue "default_((shade_|outline_)?color)"
color brightblue "(alignment|gap_x|gap_y|no_buffers|uppercase)"
color brightblue "^TEXT[[:space:]]*$"

# Highlight boolean toggles
color brightred "[[:space:]]+(yes|no)[[:space:]]*"

# Conky position descriptors
color brightred "(top_left|top_right|bottom_left|bottom_right)[[:space:]]*$"

# Numbers 
color magenta "[[:space:]]+([[:space:]]*([0-9]\.?))+[[:space:]]*"

# variables
color brightred "\$\{?[a-zA-Z_0-9\# ]+\}?"

# Comments - match 0 or more spaces/tabs preceding the comment
# back assertions don't seem to work, so we have to assume that all
# comments will start on a new line (otherwise the RGB colour codes
# will cause their lines to get treated as comments
color green "^[[:space:]]*#.*"

# apply after comments (it's just easier)
# colour codes
color white "[[:space:]]+\#[0-9A-Fa-f]{6}"

```


Cheers,
Keith.

---

### Post by Xk2c on 2005-09-04
Have a look here :

[http://forums.gentoo.org/viewtopic.php?p=1382452#1382452](http://forums.gentoo.org/viewtopic.php?p=1382452#1382452)


:D

Have Fun..

---

### Post by Taoism on 2005-09-04
Cool stuff!  I posted my syntax defs onto that thread, and borrowed a few for myself!  Thanks for pointing it out to me!

Cheers,
Keith.

---

### Post by Xk2c on 2005-09-04
Your are welcome.

 ;-)

---

### Post by xmux on 2007-04-05
Hey i did this how to but something i did wrong and now my nano doesnt work!! How can i get it back?? i tried already sudo apt-get remove nano and apt-get install nano but it doesnt work!! 

When it runs on terminal the letters looks like UFO alphabet!! Can someone help me??

---

### Post by xmux on 2007-04-05
> youngka@quidditch:/
Sat Sep 03 21:34:27 $ cp /usr/share/doc/nano/examples/nanorc.sample ~
youngka@quidditch:/
Sat Sep 03 21:37:24 $ mv ~/nanorc.sample ~/.nanorc
youngka@quidditch:/
Sat Sep 03 21:38:44 $

I think in this time it happend!!
you can see it also [IMG]http://stud3.tuwien.ac.at/~e0427152/Screenshot.png[/IMG]

What should i do???

thanks

---

### Post by xmux on 2007-04-05
hey thanks, me idiot i wrote some false things!! now i got it back again thanks anyway!! I moved the nanorc to somewhere which doesnt exist...

thanks anyway!!

---

### Post by tennvolsmb on 2007-07-12
ok im having the same problem but i dont know how to fix it please someone help!!!

---

### Post by qasimlone on 2008-04-01
I have followed all the steps. It still does not show the colours. How ever if i add errors to nanorc file. Nano gives me error before starting. It means that it is reading the file before starting but its not working :(

---

### Post by akssoon on 2009-04-15
Even more syntax highlighting configurations can be found here:
[wiki.linuxhelp.net]("http://wiki.linuxhelp.net/index.php/Nano_Syntax_Highlighting")

---

### Post by minimalmiser on 2010-08-31
There is no bug with the square brackets [] in nano regex....
The line:
[SIZE=4]          color brightyellow "[[]hello]"[/SIZE]
will highlight any instance of [SIZE=4][hello][/SIZE].
Just dont place right square brackets inside the character group, no need for escapes.[SIZE=4]
[/SIZE]

---

### Post by wayover13 on 2012-01-07
I don't do any programming, so nano's canned syntax-highlighting configurations were not of much use to me. Rather I'm a writer/lecturer and was hoping to use nano as a sort of outliner for writing projects and lecture notes. I wanted to get it to do something approximating one of the neat things vimoutliner does, namely, to make differing outline levels appear in differing colors.

I didn't manage to find any pre-made solutions in my internet searches. And, to be frank, regex documentation is not very approachable for the non-technical user. The fact that nano seems to honor a somewhat non-standard form of regex made things yet more confusing. But it seems I have finally met with success.

The first thing that needs to be done in order for this to work is to tell nano to use auto-indentation. That's done by entering ```
set autoindent
```into your ~/.nanorc file

About the most helpful bit of information I found in my searches regarding highlighting the indented outline levels came from this site: [http://tuxradar.com/content/text-editing-nano-made-easy](http://tuxradar.com/content/text-editing-nano-made-easy) . Using that, I came up with my own syntax highlighting scheme for outlines, which I'll paste below: ```
syntax "outl" "\.outl$"
color brightwhite "(^).*$"
color brightred "(^[[:blank:]]).*$"
color brightgreen "(^[[:blank:]][[:blank:]]).*$"
color magenta "(^[[:blank:]][[:blank:]][[:blank:]]).*$"
color brightblue "(^[[:blank:]][[:blank:]][[:blank:]][[:blank:]]).*$"
color yellow "(^[[:blank:]][[:blank:]][[:blank:]][[:blank:]][[:blank:]]).*$"
```
What that does is cause nano to apply the syntax highlighting to any file that has the extension .outl. There are five indentation levels, and the specified color gets applied to each. More color levels could be added, up to the number of colors nano can display (Valid colors: white, black, red, blue, green, yellow, magenta, cyan), depending on the background color of your terminal. Of course colors can be made to repeat after a certain indentation level as well (as vimoutliner does), for those who really need to go overboard in outlining.

Anyway, that's my non-programmer's contribution to this thread.

James

---

### Post by wayover13 on 2012-01-07
Actually, the more "elegant" way to do this, as I discovered, is to specify a number in curly brackets rather than to repeat the "blank" regex. Thus: ```
syntax "outl" "\.outl$"
color brightwhite "(^).*$"
color brightred "(^[[:blank:]]).*$"
color brightgreen "(^[[:blank:]]{2}).*$"
color magenta "(^[[:blank:]]{3}).*$"
color brightblue "(^[[:blank:]]{4}).*$"
color yellow "(^[[:blank:]]{5}).*$"
```
I've also discovered that the "blank" regex apparently indicates all whitespace, so the coloring will be applied to new lines that begin with either (a) space(s) or (a) tab(s). I'd rather have it apply only to tabs and not to spaces, but at this point I believe that cannot be done.

James

---

