---
title: "Shell Editor - Deciding on a Default"
date: 2009-12-28
forum: Server Platforms
---

### Post by Xiuh on 2009-12-28
I've decided it's about time I pick out a good editor that I can use while in the shell. In the past, I refused to learn how to use an editor, instead I slunk by with Nano (which I also wasn't very efficient with). That said, I'm trying to find an editor that I'll invest the time into getting over the learning curve.

[LIST]
[*]What I'm needing the editor for:
[*]Editing etc files
[*]writing shell scripts
[*]Making small adjustments with C/C++ files
[*]Editing GNU Make files
[*]Default editor for different packages (SVN repo management mainly
[/LIST])

The two things I'm really interested in is syntax highlighting and diff.

Here are my points of confusion. I am aware many people prefer using Vim or Emacs. However, I am confused on all the different variants available. Second, I get caught up what editor integrates with other utilities. For example, I had all but decided on settling with Vim, but reconsidered after seeing how emac integrates in with *info*. Third, there are lots of other editors, for example Joe and gedit, that seem like popular choices. I wasn't sure if something of that sort might hit middle ground between simple editors and a full blown IDE. Finally, beyond vim and emacs, I can't get a very clear picture of how established some of these other editors currently stand. It's certainly nice when you have a good wealth of documentation to pick from. 

Perhaps I'm pondering such unnecessarily, but as mentioned, I'm relatively clueless in this category. If anyone had any thoughts, I'd certainly appreciate if you shared them.

---

### Post by capscrew on 2009-12-28
> **Xiuh said:**
> I've decided it's about time I pick out a good editor that I can use while in the shell...

The two things I'm really interested in is syntax highlighting and diff.

Here are my points of confusion. I am aware many people prefer using Vim or Emacs. However, I am confused on all the different variants available...

Perhaps I'm pondering such unnecessarily, but as mentioned, I'm relatively clueless in this category. If anyone had any thoughts, I'd certainly appreciate if you shared them.

Boy you sure know how to start a long thread.  This ought to be good!  :D

I went through this dilemma years ago.  

Emacs has lots of features and you can *live in the IDE*, but has an arcane configuration language.  

Vim (and Gvim) is a little more more straightforward with many config scripts online.  The modal interface initially puts some users off.  One for viewing and another for editing.  

Gedit is a nice editor, but in some areas it is dumb.  It integrates well with Gnome but sometimes has troubles with the system.  I believe it uses GVFS userspace only.

Bluefish is a nice editor for HTML code, but it does not have a visual editor built in like Dreamwever does.

All the others are simple editors or specific IDE's and may or may not be available on other OS's.

Ultimately I ended up with VI (Vim and Gvim).  I use it on UNIX (Solaris), Linux and Windows OS's.  Very customizable and consistent in all the environments.

Just one users opinion.

---

### Post by SecretCode on 2009-12-28
I have never got into vi* or emacs. I am happy with nano where it's the only thing installed but my favourite *shell* editor is [SIZE="3"]joe[/SIZE]. It does the syntax highlighting (for the file types I normally edit - and as I understand it's extensible) and it's fully customisable in options and keystrokes.

---

### Post by CharlesA on 2009-12-28
I usually use nano for quick edit/creating files where I don't need to know syntax.

vi if I'm writing scripts, or deleting lines while testing scripts.. dd is my friend in vi.

---

### Post by Xiuh on 2009-12-28
Thanks for sharing guys. I actually started poking around with vim and Joe this evening. I'm a bit hesitant to settle on Joe. I liked the setup, which, from first look keeps keystrokes similar to vi. On the other hand, It's rare that I'll see an existing system that already has Joe compiled and ready to go versus the availability of Vim (Just something extra to do, which at some point I might not even be on a system I admin). 

On Vim....I've read a couple different tutorials on setting up various things on Ubuntu the last few months. A few of the authors are very adamant about removing the (slimmed down version?) of Vim on a generic default Ubuntu Server setup. After removal instructions, they'll suggest installing the (full version?) of Vim. They briefly mention odd results using Vi while using sudo root. Is there more information about this or even necessary that I look into it further?

---

### Post by fancypiper on 2009-12-30
Have you tried the built in editor of the [Midnight Commander](http://www.trembath.co.za/mctutorial.html)?

For the command line, this is my must have app.

---

### Post by lloyd_b on 2009-12-30
> **Xiuh said:**
> Thanks for sharing guys. I actually started poking around with vim and Joe this evening. I'm a bit hesitant to settle on Joe. I liked the setup, which, from first look keeps keystrokes similar to vi. On the other hand, It's rare that I'll see an existing system that already has Joe compiled and ready to go versus the availability of Vim (Just something extra to do, which at some point I might not even be on a system I admin). 

On Vim....I've read a couple different tutorials on setting up various things on Ubuntu the last few months. A few of the authors are very adamant about removing the (slimmed down version?) of Vim on a generic default Ubuntu Server setup. After removal instructions, they'll suggest installing the (full version?) of Vim. They briefly mention odd results using Vi while using sudo root. Is there more information about this or even necessary that I look into it further?

You *will* want to upgrade from the "vim-tiny" that's installed by default - it has no support for syntax highlighting!  Just do a "sudo apt-get install vim" to get the "full" version (well, the full command-line version.  There's the "vim-full" package that includes 'gvim', the gui version).

Lloyd B.

---

### Post by Barriehie on 2010-01-01
> **capscrew said:**
> Boy you sure know how to start a long thread.  This ought to be good!  :D
...
Emacs has lots of features and you can *live in the IDE*, but has an arcane configuration language.  
...


The learning curve is a bit also but when you get the basics down you can't compute without it!  I've got my 2 page cheat sheet which once I typed it up I don't have to use. :)  In regards to the configuration language it is a bit befuddling but I've yet to be stumped when looking for scripts online.  Loads of info [[color="blue"]here[/color]](http://www.emacswiki.org/emacs-en/).

---

