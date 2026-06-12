---
title: "I'm a moron (used the terminal instead of the GUI)"
date: 2007-01-06
forum: The Cafe
---

### Post by aysiu on 2007-01-06
I don't know why I did this, but I did.

I spent about half an hour recording some songs off record. Then I tried to move them from one folder to another using the terminal. Instead of using ```
mv
``` for some reason I was *thinking* move but actually typed *re*move: ```
rm
``` Those songs are all gone now.

I'm a moron. From now I'd better stick to the GUI.

---

### Post by 23meg on 2007-01-06
If you find yourself caught in this kind of thing often, it helps to set plain language aliases that point to commands and get a habit of using those aliases instead of the commands.

---

### Post by aysiu on 2007-01-06
> **23meg said:**
> If you find yourself caught in this kind of thing often, it helps to set plain language aliases that point to commands and get a habit of using those aliases instead of the commands.
Yeah, but I may still end up typing the wrong thing. After all, my mind was *thinking* "move," but clearly my fingers were thinking something else ("remove"). Aliases assume your mind and fingers are working together. Thanks for the suggestion, though.

---

### Post by 23meg on 2007-01-06
[QUOTE=aysiu]my mind was thinking "move," but clearly my fingers were thinking something else ("remove").[/QUOTE]There's a possibility of confusion coming from the multi-purpose nature of the "mv" command and the fact that the word "remove" includes "move".

Three basic file management operations correspond to these commands:

*move* --> mv
re*move* --> rm
rename --> mv

Note that the word "delete" is perhaps more associated than the word "remove" with getting rid of a file, and "rm" doesn't resemble the word "delete" at all.  

Given the rough foreknowledge that these operations are handled with these commands, but without knowledge of which does which, and judging only by the appearance of the commands, your mind may easily be fooled into thinking "rm" is used for renaming, and "mv" for removing and moving. But that's not the case; there's a discrepancy between the common expectation of the uninformed or unprepared user and the actual function. 

I don't know if this was the case in your accident, but I've heard of other people who use the commands infrequently and forget their exact function falling into this trap. With aliases, you can have your own rules if you disagree with those of the *nix convention

---

### Post by Iarwain ben-adar on 2007-01-06
I know what you mean aysiu,

I tried installing something, and had to delete a certain folders content.

Instead of using ```
rm /home/iarwain/someprogramfolder/*
```

I used ```
 rm * /home/iarwain/someprogramfolder
```

Needless to say, i lost most of my ~'s contents :oops:


Iarwain

---

### Post by fuscia on 2007-01-06
aren't you afraid you might right-click on 'delete' instead of 'paste'?

---

### Post by ice60 on 2007-01-06
i use this bash alias -
```
alias rm="mv $@ --target-directory=${HOME}/.Trash"
```
so all things 'removed' go to the bin.

i've used this one too in the past -
```
alias rm='rm -i'
```
that just asks you if you are sure.

---

### Post by Haegin on 2007-01-06
I have seen another person who had a problem like this who whipped up a handy bash script to move it to an archive instead of deleting and that archive was cleared every so often (manually or with a cron job) by deleting everything that was older than a certain date. I found it with google but the alias to move it to the normal recycle bin seems more useful (so long as you remember to empty it!)

---

### Post by atihimself on 2007-01-06
it's little offtopic but once i tried to compile something and i had to use word default, somehow my fingers were shure that it's spelled deafult... after 2 hours and many forum threads i found out it was my own spelling mishap not some unknown error. lol

---

### Post by mips on 2007-01-06
> **ice60 said:**
> i use this bash alias -
```
alias rm="mv $@ --target-directory=${HOME}/.Trash"
```so all things 'removed' go to the bin.

i've used this one too in the past -
```
alias rm='rm -i'
```that just asks you if you are sure.

That is not really a good idea. You are getting use to this particular rm behaviour and becoming complacent. When you work on another system with a 'real' rm it's going to byte you as there will be no safety net.

---

### Post by mips on 2007-01-06
[http://wiki.yak.net/592](http://wiki.yak.net/592)
[http://recover.sourceforge.net/linux/](http://recover.sourceforge.net/linux/)
[http://recover.sourceforge.net/linux/recover/](http://recover.sourceforge.net/linux/recover/)
[http://recover.sourceforge.net/unix/](http://recover.sourceforge.net/unix/)

Dunno if you have compatible file systems or how much disk usage you have gone through after the rm.

---

### Post by shining on 2007-01-06
> **mips said:**
> That is not really a good idea. You are getting use to this particular rm behaviour and becoming complacent. When you work on another system with a 'real' rm it's going to byte you as there will be no safety net.

If you can use rm, I believe you can also set the aliases you want. It's quick to add an alias on a new system.
And anyway, when I'm using gui, I never delete things without paying attention thinking that they will be in the Trash anyway, I just delete what I want. But occasional errors are always possible.
I also did a big mistake once, using console for removing files. I'm always using tab completion, and this time, I didn't check how the path completed, I just typed <tab> then enter directly. It took me a few seconds to realize it wasn't deleting what I wanted, so I cancelled it.
The problem is I wasn't sure which files it started to delete. I don't remember how I figured it out, but it seemed it didn't start with important files, so I was lucky :)

---

### Post by Bloodfen Razormaw on 2007-01-06
[http://www.ubuntuforums.org/showthread.php?t=59334](http://www.ubuntuforums.org/showthread.php?t=59334)

---

### Post by aysiu on 2007-01-06
> **fuscia said:**
> aren't you afraid you might right-click on 'delete' instead of 'paste'?
Not really. Since my "delete" in Thunar just moves things to the trash.

---

### Post by picpak on 2007-01-06
*sigh* I did the exact same thing once too. I have a bash alias, del, which runs rm -rf. I wanted to delete one of my songs through the terminal, so I typed del Music/. I didn't know what the full filename was, so I hit tab twice to see all the filenames. My brain was thinking too fast, I hit enter without typing in the filename, and bam! I deleted all my music.

So I made myself a script:

```
#!/bin/sh

if ( ! "$@" | grep Music > /dev/null 2>&1); then
	echo "What are you, crazy?!?!?!?"
else
	rm -rf "$@"
fi

```

*edit* OMFG! I deleted it again testing this script! ](*,)

---

### Post by fuscia on 2007-01-06
> **aysiu said:**
> Not really. Since my "delete" in Thunar just moves things to the trash.

i hate 'trash', but thunar does so rock.

---

### Post by kio_http on 2009-11-12
Its gone nothing doing! ):P

---

### Post by koleoptero on 2009-11-12
Wow, talking about necromancy...
[IMG]http://www.w3bdevil.com/forums/Old-MummyHead.jpg[/IMG]

---

### Post by JillSwift on 2009-11-12
This is why I bump my Backup Wednesday thread. 


Ouchies!

---

### Post by kio_http on 2009-11-12
> **koleoptero said:**
> Wow, talking about necromancy...
[IMG]http://www.w3bdevil.com/forums/Old-MummyHead.jpg[/IMG]

Wow I didn't realize it was so old!

---

### Post by Simian Man on 2009-11-12
That sucks man.  I think most of us who have used Linux for long enough have been burned like this at some point :(.

---

### Post by kio_http on 2009-11-12
> **Simian Man said:**
> That sucks man.  I think most of us who have used Linux for long enough have been burned like this at some point :(.

I think he's got over it by now this is an old thread!

---

### Post by hoppipolla on 2009-11-12
aww that sucks man, but yeah it's a risk of using the terminal.. you don't get many second chances ._.

I don't often make mistakes in the terminal, but when I was new I accidentally removed the /etc directory one time... Suse was NOT happy!! :o

> **kio_http said:**
> I think he's got over it by now this is an old thread!

oh yeah wow I didn't spot that either! I would be laughing if he was still mourning the loss of his tracks nearly 3 years on! xD

---

### Post by kio_http on 2009-11-12
> **hoppipolla said:**
> 


oh yeah wow I didn't spot that either! I would be laughing if he was still mourning the loss of his tracks nearly 3 years on! xD

+1
Me too.
Guess he'll have a laugh if he sees the thread too!

---

### Post by fromthehill on 2009-11-12
sudo chmod -R 777 *

while standing in '/' I pressed ENTER instead of /var/www/stuff/
after that all the icons and graphics from every single program slowly disappeared :D

never give everyone all permissions to all files
too much freedom kills :P

---

### Post by aysiu on 2009-11-12
I don't get why this thread was revived.

---

