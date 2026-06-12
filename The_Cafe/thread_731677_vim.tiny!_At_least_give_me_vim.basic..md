---
title: "vim.tiny?! At least give me vim.basic."
date: 2008-03-22
forum: The Cafe
---

### Post by elamericano on 2008-03-22
I'm a little late, but I've been living on 6.06. Beta install was smooth, except for the jolt of missing vim options. Are you kidding me? I'm pretty sure there was 1MB of unused space on the cd. They downgraded me for nothing. And even if they *were* down to their last megabyte, I'm quite sure that the search for useless crap wasn't exhausted so that they needed to start trimming essentials.

It probably won't get added back until they move to DVD... or maybe some genius will figure they're still saving 1MB. :roll:

Is there a bug open already?

---

### Post by 23meg on 2008-03-22
[QUOTE=elamericano]Is there a bug open already?[/QUOTE]

Why don't you do a search and see for yourself?

---

### Post by elamericano on 2008-03-22
I'm avoiding duplication of effort ;-)

Seriously though, if this happened in Edgy, I'm a little late to the party. If nobody answers, I'll take that as my answer.

BTW, if someone were to look, you didn't say where they should start. That's not very helpful.

---

### Post by 23meg on 2008-03-22
I was assuming you knew or could easily find out where Ubuntu's bug tracker is and how to do a search in it. 

Here: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

Bugs in the *vim* source package: [https://bugs.launchpad.net/ubuntu/+source/vim](https://bugs.launchpad.net/ubuntu/+source/vim)

I'd also do a search for mailing list discussions where the rationale may have been mentioned.

[http://www.nabble.com/Ubuntu-f12717.html](http://www.nabble.com/Ubuntu-f12717.html)

---

### Post by macogw on 2008-03-22
Yeah, bash auto-complete requires the bash-completion package now too.  I complained about that on IRC.  Something like "first they take out half of vim, now bash..." and someone said "they've always had vim tiny" I'm like "bull!  Dapper had *proper* vim"  Not sure about Edgy, but Feisty definitely had half-brained vim.

---

### Post by elamericano on 2008-03-23
There it is:

[https://bugs.launchpad.net/ubuntu/+source/vim/+bug/118970](https://bugs.launchpad.net/ubuntu/+source/vim/+bug/118970)

invalid, of course :-P

The reasoning seems to be that a vi (non-vim) was required, thus the additional space requirement for vim would be the full 1.6MB, and the need is less since vi was already included. Bah.

Just the cost of adding unnecessary new features. Like I said. It'll come back when they use DVDs as the standard distribution medium.

---

### Post by 23meg on 2008-03-23
[QUOTE=elamericano]
The reasoning seems to be that a vi (non-vim) was required, thus the additional space requirement for vim would be the full 1.6MB,
[/QUOTE]

vim-runtime alone is 5.5MB. 

[QUOTE=elamericano]Like I said. It'll come back when they use DVDs as the standard distribution medium.[/QUOTE]

In other words, never.

[QUOTE=macogw]Yeah, bash auto-complete requires the bash-completion package now too. [/QUOTE]

It was split because it's no longer supported upstream (says the changelog, which a good FOSS citizen is supposed to read before complaining).

---

### Post by macogw on 2008-03-23
> **23meg said:**
> 
It was split because it's no longer supported upstream (says the changelog, which a good FOSS citizen is supposed to read before complaining).

Making a separate package is fine, but then not installing the package (ie. cutting features) isn't.

---

### Post by 23meg on 2008-03-23
The point of making a separate package is moving it to Universe. Software that isn't supported upstream can't stay in Main, especially in a release that will be supported for five years.

---

### Post by elamericano on 2008-03-23
> **23meg said:**
> It was split because it's no longer supported upstream (says the changelog, which a good FOSS citizen is supposed to read before complaining).

Mom? Is that you?

---

### Post by danbuter on 2008-03-23
I see vim as valuable memory being wasted, myself :).

---

### Post by bruce89 on 2008-03-23
> **elamericano said:**
> Mom? Is that you?

Sigh:

```
bash-completion (20060301-0ubuntu1) hardy; urgency=low

  * Initial release, split out from the bash package.
    The software currently is unsupported upstream.
[...]
 -- Matthias Klose < [email]doko@ubuntu.com[/email]>   Fri, 08 Feb 2008 16:46:34 +0100
```

Notice the version number?

---

### Post by macogw on 2008-03-23
> **danbuter said:**
> I see vim as valuable memory being wasted, myself :).

How?  It's only in memory when you're using it.  If you're not using it, it's not using any memory, and if you are using it, the memory's not being wasted.

---

### Post by igknighted on 2008-03-23
> **macogw said:**
> How?  It's only in memory when you're using it.  If you're not using it, it's not using any memory, and if you are using it, the memory's not being wasted.

methinks he's an emacs guy... ewww... :P

---

### Post by macogw on 2008-03-23
> **igknighted said:**
> methinks he's an emacs guy... ewww... :P
It's still not using any memory when not in use, either way.  And anyway, Emacs uses a *lot* of memory.  One of my friends had his Emacs section terminated by one of the SAs at school with the message "You're raping Hobbes" (Hobbes is the name of the server) because he managed to consume half the server's CPU and memory with his one Emacs process.

---

