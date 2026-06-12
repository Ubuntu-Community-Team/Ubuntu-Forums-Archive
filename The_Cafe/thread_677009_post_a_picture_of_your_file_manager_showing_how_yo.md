---
title: "post a picture of your file manager showing how you've set it up."
date: 2008-01-24
forum: The Cafe
---

### Post by ice60 on 2008-01-24
i'd love to see how people have their File Managers setup, it's not something you see much, i'd like to see if i can get some ideas.

here's my FM, it's thunar, i've added the Custom Actions plugin to add right-click options.

[[IMG]http://img517.imageshack.us/img517/3081/thunarww1.th.png[/IMG]](http://img517.imageshack.us/my.php?image=thunarww1.png)

---

### Post by macogw on 2008-01-24
This is my preferred file manager:
[img]http://ubuntuforums.org/attachment.php?attachmentid=57385&stc=1&d=1201198000[/img]

---

### Post by Lostincyberspace on 2008-01-24
> **ice60 said:**
> i'd love to see how people have their File Managers setup, it's not something you see much, i'd like to see if i can get some ideas.

here's my FM, it's thunar, i've added the Custom Actions plugin to add right-click options.

[[IMG]http://img517.imageshack.us/img517/3081/thunarww1.th.png[/IMG]](http://img517.imageshack.us/my.php?image=thunarww1.png)
where did you get your theme?

I don't have it set up yet will post when I do.

---

### Post by ukripper on 2008-01-24
> **macogw said:**
> This is my preferred file manager:
[img]http://ubuntuforums.org/attachment.php?attachmentid=57385&stc=1&d=1201198000[/img]

very similiar to mine:)

---

### Post by Nano Geek on 2008-01-24
As you can see, I've customized mine extensively. :)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=57389&d=1201199255[/IMG]

---

### Post by ice60 on 2008-01-24
> **Lostincyberspace said:**
> where did you get your theme?

I don't have it set up yet will post when I do.

the compiz theme is CubicDots, but i think i hacked the rest of the theme.

 i picked Murrina-Black in gtk-chtheme for the GTK bit, i might have made some changes with Murrina-Black, i don't know.

the controls are RoyaltyGrey (i changed something with it, i can't remember)

---

### Post by FuturePilot on 2008-01-24
Here's mine
[[IMG]http://img244.imageshack.us/img244/8146/nautilusqp2.th.png[/IMG]](http://img244.imageshack.us/my.php?image=nautilusqp2.png)

---

### Post by fuscia on 2008-01-24
thunar (i wish it were called 'tuna', though).

---

### Post by p_quarles on 2008-01-24
> **fuscia said:**
> thunar (i wish it were called 'tuna', though).
I'm certain that your recent feline wallpaper would share that sentiment. ;)

Mostly Bash for file maintenance. I find that some tasks are easier with a dual-paned file manager, though, and I like Krusader.

---

### Post by nikef on 2008-01-24
Here is mine

---

### Post by Ebuntor on 2008-01-24
> **nikef said:**
> Here is mine

I was wondering, which dock is that?

---

### Post by macogw on 2008-01-24
> **p_quarles said:**
> 
Mostly Bash for file maintenance. I find that some tasks are easier with a dual-paned file manager, though, and I like Krusader.
Other tasks, like bath renaming of files, are *much* more easily done with bash.  The rename command is a great one.

---

### Post by macogw on 2008-01-24
> **Ebuntor said:**
> I was wondering, which dock is that?

AWN with the awn-curves add-on.  I think awn-curves has to be compiled from CVS or SVN or something.  There are directions somewhere on the forum.

---

### Post by Ebuntor on 2008-01-24
> **macogw said:**
> AWN with the awn-curves add-on.  I think awn-curves has to be compiled from CVS or SVN or something.  There are directions somewhere on the forum.

Thanks for the info, sure looks a lot better than the default look.

---

### Post by ExpatPaul on 2008-01-24
> **asjdfwejqrfjcvm msz34rq33 said:**
> As you can see, I've customized mine extensively. :)

What a coincidence! That's almost exactly like mine ;)

---

### Post by nikef on 2008-01-24
> **Ebuntor said:**
> I was wondering, which dock is that?

Hi its the awn curves dock  :)

here is a how two ,2 get it up an running 


[http://ubuntuforums.org/showthread.php?t=572019](http://ubuntuforums.org/showthread.php?t=572019)

---

### Post by ice60 on 2008-01-24
> **macogw said:**
> This is my preferred file manager:
[img]http://ubuntuforums.org/attachment.php?attachmentid=57385&stc=1&d=1201198000[/img]
it would be cool to start a thread about using a terminal for your FM, with all the things you can add to improve functionality e.g. -

```
# interactive
alias cp='cp -vi'
alias mv='mv -vi'
alias rm='mv --target-directory=$HOME/.Trash/'

# Directory navigation aliases
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias .....='cd ../../../..'

# chmod and permissions commands
alias mx='chmod a+x'
alias 000='chmod 000'
alias 644='chmod 644'
alias 755='chmod 755'
alias perm='stat --printf "%a %n \n "' # requires a file name e.g. perm file
```

i like this unpacking alias best. to decompress any archive - rar, zip, tar.bz2 etc, i just run -
```
unpack archive_name
```
i got it from here -
[http://www.comp.eonworks.com/scripts/uncompress_unpack_script-19990920.html](http://www.comp.eonworks.com/scripts/uncompress_unpack_script-19990920.html)

---

### Post by RebounD11 on 2008-01-24
Here's mine ... another one with "extreme customization" :D

---

### Post by p_quarles on 2008-01-24
> **macogw said:**
> Other tasks, like bath renaming of files, are *much* more easily done with bash.  The rename command is a great one.
Oh, I agree. Actually, the main reason I've used Krusader recently is that I've been migrating my music collection to .flac: replacing old MP3/Vorbis files with the new ones. Given the sorry state that the collection's tree is in (e.g., multiple similar folder names, long names with spaces, etc.), I've found it easier to drag and drop. Apart from that, mv, cp and rm -- throw in tab completion and wildcards -- is perfect.

---

### Post by Ebuntor on 2008-01-24
> **nikef said:**
> Hi its the awn curves dock  :)

here is a how two ,2 get it up an running 


[http://ubuntuforums.org/showthread.php?t=572019](http://ubuntuforums.org/showthread.php?t=572019)


Looks really nice. More polished than the normal theme I use. Thank you.

I'm installing it now. :)

---

### Post by nikef on 2008-01-24
> **Ebuntor said:**
> Looks really nice. More polished than the normal theme I use. Thank you.

I'm installing it now. :)

Thats cool :)

any problems i am sure Niko will help you out ,have fun  :)

---

### Post by xinix on 2008-01-24
Midnight Commander
[[IMG]http://img444.imageshack.us/img444/6258/snapshot2sg5.th.png[/IMG]](http://img444.imageshack.us/my.php?image=snapshot2sg5.png)

---

### Post by ice60 on 2008-01-24
here's one of TuxCmd, i got the latest standalone executable -
[http://tuxcmd.sourceforge.net/](http://tuxcmd.sourceforge.net/)
[http://tuxcmd.sourceforge.net/screenshots.php](http://tuxcmd.sourceforge.net/screenshots.php)


EmelFM2 is another nice dual-pane FM
[http://emelfm2.net/](http://emelfm2.net/)
[http://emelfm2.net/ScreenShots](http://emelfm2.net/ScreenShots)

in the past i found tuxcmd would sometimes crash, but i'm really happy there's a newer version to try out now!

---

### Post by 23meg on 2008-01-24
Nautilus using gvfs in Hardy:

[IMG]http://i29.tinypic.com/14e2xoy.jpg[/IMG]

If you'd like to help test it, [see this]("http://ubuntuforums.org/showthread.php?t=676747").

---

### Post by -Rick- on 2008-01-24
Konqueror ;)

---

### Post by macogw on 2008-01-24
> **ice60 said:**
> it would be cool to start a thread about using a terminal for your FM, with all the things you can add to improve functionality e.g. -

```
# interactive
alias cp='cp -vi'
alias mv='mv -vi'
alias rm='mv --target-directory=$HOME/.Trash/'

# Directory navigation aliases
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias .....='cd ../../../..'

# chmod and permissions commands
alias mx='chmod a+x'
alias 000='chmod 000'
alias 644='chmod 644'
alias 755='chmod 755'
alias perm='stat --printf "%a %n \n "' # requires a file name e.g. perm file
```

i like this unpacking alias best. to decompress any archive - rar, zip, tar.bz2 etc, i just run -
```
unpack archive_name
```
i got it from here -
[http://www.comp.eonworks.com/scripts/uncompress_unpack_script-19990920.html](http://www.comp.eonworks.com/scripts/uncompress_unpack_script-19990920.html)
I just use
```
set -o vi
alias ls='ls --color'
alias l='ls -hAl --color'
alias sup='sudo aptitude update && sudo aptitude full-upgrade -y
```
The first line lets me use vi commands for my bash input method, so I can hit Esc while in bash and go 3bcw or whatever I need to do to change a command I'm typing (or that I arrowed up to).  Adding ```
alias lart='ls -lArt'
``` might be a good one too.  That lists all files (except . and ..) sorted in reverse time order with a long listing (so you can see the time), which means that when the terminal scrolls to the bottom automatically (for your next command to go in), the most recently edited files are there at the bottom, which could be useful when you're trying to figure out what changed right before it broke.

---

### Post by ice60 on 2008-01-25
> **macogw said:**
> I just use
```
set -o vi
alias ls='ls --color'
alias l='ls -hAl --color'
alias sup='sudo aptitude update && sudo aptitude full-upgrade -y
```
The first line lets me use vi commands for my bash input method, so I can hit Esc while in bash and go 3bcw or whatever I need to do to change a command I'm typing (or that I arrowed up to).  Adding ```
alias lart='ls -lArt'
``` might be a good one too.  That lists all files (except . and ..) sorted in reverse time order with a long listing (so you can see the time), which means that when the terminal scrolls to the bottom automatically (for your next command to go in), the most recently edited files are there at the bottom, which could be useful when you're trying to figure out what changed right before it broke.
i have almost that exact alias, (maybe i'll change it to a big A)  -
```
lt is aliased to `ls -latr'
```
it's one of the commands i use to find flash movies, or youtube clips, in my browser cache. i use this one too -
```
lss is aliased to `ls -shAxSr'
```
i'm sure there's a better way to do it lol, but it shows the files sizes with the biggest last.

---

### Post by Lord DEA on 2008-01-27
This is mine. I like the colorful rounded candy-like buttons from mac...:lolflag:

---

### Post by b0rka7a on 2008-01-27
Here's mine:
[ATTACH]57781[/ATTACH]
I'm using Kubuntu :)

---

### Post by FuturePilot on 2008-01-27
> **23meg said:**
> Nautilus using gvfs in Hardy:

[IMG]http://i29.tinypic.com/14e2xoy.jpg[/IMG]

If you'd like to help test it, [see this]("http://ubuntuforums.org/showthread.php?t=676747").

Wow, that's pretty nice.:)
I'm excited to see Nautilus with the overhauled code base.

---

### Post by samwyse on 2008-01-27
[[img]http://xs123.xs.to/xs123/08040/konqueror2988.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs123&d=08040&f=konqueror2988.png)

Nothing special, except I patched it to have the normal three view buttons. The gradients I need to tweak, I'm still messing a bit with QtCurve that I installed last night. The tooltip feature should be in every filemanager.

---

### Post by samwyse on 2008-01-27
> **-Rick- said:**
> Konqueror ;)

I sometimes use split view for folders / Konsole / webpage, but not all of them at once ;)

---

### Post by new2*buntu on 2008-01-27
Here is mine:

---

### Post by ukripper on 2008-01-28
i bet many will recognise this:popcorn:

---

### Post by -grubby on 2008-01-28
My 2 favorite file managers..

---

