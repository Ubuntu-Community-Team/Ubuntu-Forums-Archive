---
title: "How many of you find yourselves hitting 'TAB' when posting instructions?"
date: 2008-08-06
forum: The Cafe
---

### Post by raul_ on 2008-08-06
I was just posting some instructions and I wrote '... /et', went for my TAB key, and ended up with a totally useless post. 

Does this happen to you?

---

### Post by klange on 2008-08-06
Someone, maybe myself, should write a tab-completion extension for Firefox...
(I've checked, there isn't one, at least not for FF3)

---

### Post by FuturePilot on 2008-08-06
Yes, I've accidentally done it a number of times when helping on the forums here, and then I get confused because then it stops typing. :(

---

### Post by -grubby on 2008-08-06
Tab completion for Firefox would be a godsend

---

### Post by init1 on 2008-08-06
Yeah, that's happened to me with Google searches too.

---

### Post by Newuser1111 on 2008-08-06
Why?

Does tab do something I didn't know it did?

---

### Post by mc4100 on 2008-08-06
> **Newuser1111 said:**
> Why?

Does tab do something I didn't know it did?

Auto-completion, try it:
Open a Terminal and type
```
cd Deskt
``` and then press TAB before you finish.

---

### Post by Newuser1111 on 2008-08-06
> **mc4100 said:**
> Auto-completion, try it:
Open a Terminal and type
```
cd Deskt
``` and then press TAB before you finish.I probably wont be using it.

---

### Post by sub2007 on 2008-08-06
I'm pretty sure I must have done that at some point, I know I do it a lot when writing bash files in vi.

I also do it in OpenOffice with autocomplete (normally doesn't end well) and Google searches autocomplete. Basically anything that needs to autocomplete my instinct is to press TAB even though it nearly always doesn't work! :D

---

### Post by raul_ on 2008-08-06
And I always get that feeling, like someone just told me that Santa doesn't exist..

---

### Post by th3james on 2008-08-06
> **sub2007 said:**
> I'm pretty sure I must have done that at some point, I know I do it a lot when writing bash files in vi.

I also do it in OpenOffice with autocomplete (normally doesn't end well) and Google searches autocomplete. Basically anything that needs to autocomplete my instinct is to press TAB even though it nearly always doesn't work! :D

Alongside the tab thing, i find whenever i've been using vim for a while, i type :w at the end of each sentence...



:wq

---

### Post by Dr Small on 2008-08-06
> **FuturePilot said:**
> Yes, I've accidentally done it a number of times when helping on the forums here, and then I get confused because then it stops typing. :(
Done that many times, and even in IRC, I try to tab complete a word. :S

[quote=nathangrubb]Tab completion for Firefox would be a godsend[/quote]
+1

[quote=th3james]Alongside the tab thing, i find whenever i've been using vim for a while, i type :w at the end of each sentence...



:wq[/quote]

I use ':q' for exit in my terminal.
On Dvorak, it goes, Shift / Colon / Q, so all three keys are directly beside each other for easy an easy, speedy key press :)

---

### Post by klange on 2008-08-06
> **nathangrubb said:**
> Tab completion for Firefox would be a godsend

Half way there, I have a way to get what bash would tab-complete for a given string.
```
#!/bin/bash
echo -en "PS1=\"\"\nset -v\n$@\t>>>>_END_" | bash -i 2>&1 | grep -i \>\>\>\>_END_ | sed s/\>\>\>\>_END_//
```
We're controlling an interactive bash to:
1. Set the prompt to be nothing.
2. Echo all commands processed (we type "[something]<enter>" it prints "[something]".)
3. Send our command, followed by a tab and a faulty redirect. The redirect stops bash from actually executing.
4. 'set -v' forces bash to print the tab-completed command and our faulty redirect
5. We grep for it, as we get a lot of bs (errors, input from compgen, etc.)
6. We sed it out
The result is that the tab-completed string is printed to standard out:
```
$ tabc apt-get in
apt-get install 

```
(This should work in any other shell that has a way to echo commands that have been entered before executing them and can be crashed with something simple appended to the end of a command)

Now to write a Firefox plugin that does this with the current line when you hit tab, then I'll add smarter options. :)

Just need to learn how to write Firefox extensions...

---

### Post by schauerlich on 2008-08-06
> **Newuser1111 said:**
> I probably wont be using it.

That's what I thought when I first saw it, but the more you use the terminal the more you'll find yourself using it. I accidently try to tab-complete in nano a lot.

---

### Post by Zeotronic on 2008-08-06
I overlooked the 'and USB coffee machines' part and said yes... I don't often find myself giving instructions, but it still messes me up.

---

### Post by tamoneya on 2008-08-06
i used to do it all the time but I managed to get around it by typing the commands in terminal and then copy pasting into the forums.  It would be much easier though if it was built into firefox or maybe just the ubuntu forums.

---

### Post by ice60 on 2008-08-06
> **Dr Small said:**
> Done that many times, and even in IRC, I try to tab complete a word. :S
i think BitchX does tab completion, i've never used it though, i've got irssi, that does a little bit of tab completion though.

EDIT: i just saw this script for irssi that lets you tab complete words from /usr/share/dict/words. dictcomplete.pl on this page -
[http://juerd.nl/site.plp/irssi](http://juerd.nl/site.plp/irssi)

i've never done it on a forum, i don't believe so many people have done it, it doesn't make sense; you only hit tab when you know it's likely to be completed. have you all hacked your /etc/bash_completion file? or do you use that shell that i think inspired bash completion? maybe it's the c shell??

EDIT: ok i get it, it's when you're typing instructions that can be completed if you were using a terminal :D

---

### Post by powerpleb on 2008-08-07
> **nathangrubb said:**
> Tab completion for Firefox would be a godsend

That's what [vimperator]("http://vimperator.mozdev.org/") is for (among other things)

---

### Post by billgoldberg on 2008-08-07
I use tab completion a lot in the terminal, but I'm never temped to do it outside of the terminal.

I don't see how it could help.

I guess it could be used to complete words in things like openoffice.org and firefox, but I wouldn't like this.

Like I'm one of the only people I know that doesn't this feature on my gsm. 

I still type all the letters on the T9 interface.

---

### Post by raul_ on 2008-08-07
> **billgoldberg said:**
> I use tab completion a lot in the terminal, but I'm never temped to do it outside of the terminal.

I don't see how it could help.

I guess it could be used to complete words in things like openoffice.org and firefox, but I wouldn't like this.

Like I'm one of the only people I know that doesn't this feature on my gsm. 

I still type all the letters on the T9 interface.

The question is more if you're so used to using bash's autocomplete feature, that you try to use it when posting commands in the forums like 'cd /etc/X11/'

---

### Post by klange on 2008-08-07
> **powerpleb said:**
> That's what [vimperator]("http://vimperator.mozdev.org/") is for (among other things)

It won't tab-complete commands and paths typed into text boxes, will it?

---

### Post by powerpleb on 2008-08-07
> **WindowsSucks said:**
> It won't tab-complete commands and paths typed into text boxes, will it?
No, it can't do that.

---

### Post by ice60 on 2008-08-07
here's another of those vim/emacs like browsers, maybe it can tab complete??
**Conkeror**
[http://conkeror.mozdev.org/](http://conkeror.mozdev.org/)
[http://conkeror.mozdev.org/index.php](http://conkeror.mozdev.org/index.php)

---

