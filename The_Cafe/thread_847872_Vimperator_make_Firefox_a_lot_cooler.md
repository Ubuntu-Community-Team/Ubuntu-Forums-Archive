---
title: "Vimperator: make Firefox a lot cooler"
date: 2008-07-03
forum: The Cafe
---

### Post by RiceMonster on 2008-07-03
If you like and use Vim (which you should), check out [vimperator](http://vimperator.mozdev.org/). It's an addon that makes firefox behave like Vim (using similar commands and keybindings). I think it's great.

---

### Post by macogw on 2008-07-03
I've used it, but I'd really prefer a way to use vim commands inside these text boxes, so I stop typing :wq at the end of my posts and then having to backspace it out.

---

### Post by mrgnash on 2008-07-03
Very cool. Thanks a lot of the heads up :D

---

### Post by mrgnash on 2008-07-03
By the way, is there any way that you can retain the functionality of the 'awesome bar' with this setup?

---

### Post by Trail on 2008-07-03
The name is fail.

Looks too much like 'vimprator'

---

### Post by RiceMonster on 2008-07-03
> **mrgnash said:**
> By the way, is there any way that you can retain the functionality of the 'awesome bar' with this setup?

type :set guioptions+=mT

---

### Post by brunovecchi on 2008-09-26
This is exactly was I was looking for. After hours of browsing, my wristle hurt. Not anymore.
Gnome-Do + Vimperator = bye byer rodent.

---

### Post by chucky chuckaluck on 2008-09-26
when's nanorator coming out?

---

### Post by Dr Small on 2008-09-26
I love Vimperator. I've had it on Firefox for about a week, and it is awesome. I can't imaging going back to the old Firefox layout. I turned off the tab-bar, for a more qualifying experience, also :)

---

### Post by brunovecchi on 2008-09-26
There's also **muttator**, a Thunderbird extension to make it a behave like Vim. It's in early development though.

---

### Post by Dr Small on 2008-09-26
> **brunovecchi said:**
> There's also **muttator**, a Thunderbird extension to make it a behave like Vim. It's in early development though.
Yes, I saw that, but I don't use Thunderbird.

---

### Post by jazty on 2009-02-01
Does anybody know how to turn the status bar on while in fullscreen with Vimperator? I found a ticket that seems to explain something, but I can't get it to work: [http://vimperator.org/trac/ticket/45]("http://vimperator.org/trac/ticket/45").

---

### Post by init1 on 2009-02-01
Eh, I tried to go mouseless once by using dwm and vimperator. I just couldn't make the switch.

---

### Post by cardinals_fan on 2009-02-01
> **init1 said:**
> Eh, I tried to go mouseless once by using dwm and vimperator. I just couldn't make the switch.
I'm loving that combo right now :)

---

### Post by thisllub on 2009-02-01
Openbox,Gmrun & Vimperator is near perfection.

---

### Post by juanmoreno92 on 2009-02-09
Vimperator is the best thing to happen to me since sliced bread.

---

### Post by Cl0ud9 on 2009-02-09
[Firemacs]("https://addons.mozilla.org/en-US/firefox/addon/4141") is great if you like and use emacs(which you should).

---

### Post by Dr Small on 2009-02-09
> **Cl0ud9 said:**
> [Firemacs]("https://addons.mozilla.org/en-US/firefox/addon/4141") is great if you like and use emacs(which you should).
This is not the place to be talking about your beloved OS. We are talking about Vimperator which uses Vim functionality; not emacs :D

---

### Post by RiceMonster on 2009-02-09
> **Cl0ud9 said:**
> [Firemacs]("https://addons.mozilla.org/en-US/firefox/addon/4141") is great if you like and use emacs(which you shouldn't).

Yeah more or less

---

### Post by sertse on 2009-02-09
I personally use keyconfig, and manually rebind my firefox to use e/links keybindings :D

---

### Post by Dr Small on 2009-02-14
Here's a little custom command that I just wrote (after reading the documentation). It takes you to the Noah Webster 1828 dictionary and looks up the word for you, based on your input.

Like, the usage would be:
```
:define battle
```

Here's the command:
```
:command -nargs=1 define tabopen http://1828.sorabji.com/r.sorabji?word=<args>
```

Of course, you can replace the address to your own dictionary if you please, but this saves me a few clicks from a search engine when I want to look up the definition of a word. :)

Cheers!

---

### Post by dannytatom on 2009-02-14
I've been using it for a few days now, and it's pretty cool.  I never use Vim, so it's a bit confusing still.

---

### Post by AopicieR on 2009-02-27
Hi,

I've been using Vimperator for quite a while now and I love it. Still I have three questions:
1) Is there a command similar to vim's "q:"? Let's say you've mistyped an URL and now you want to change it. How do you do it? At the moment I have to type : and then use the arrow keys to first scroll through the command history and then through the URL, which is unbearably slow. Even the standard emacs commands like Ctrl-p to go up in the history don't work.

2) When using hints I can type the first few letters of a link to narrow down the possibilities. But what if I want to jump to a field of some form which doesn't contain anything? The search field of this forum is a good example. Here the hint number it gets is 3 which is ok, but on other sites the number will be very large and I often mistype it.

Ok, I found the answer to question 3. 
set editor=urxvt -e vim -f 
in .vimperatorrc works fine.
3) When pressing Ctrl-i in a form gvim opens. Is there a way to invoke vim for this? I know that I can use "set editor" to define the editor called, but of course setting it to vim doesn't work. I've tried setting it to urxvt -e vim, but that doesn't work either.

Thank you.

---

### Post by sharon.gmc on 2009-02-27
I think Vimperator is pretty cool!

---

### Post by maple on 2009-03-06
> **tantris said:**
> Hi,
1) Is there a command similar to vim's "q:"? Let's say you've mistyped an URL and now you want to change it. How do you do it? At the moment I have to type : and then use the arrow keys to first scroll through the command history and then through the URL, which is unbearably slow. Even the standard emacs commands like Ctrl-p to go up in the history don't work.


If I understand what your saying, try 'shift+o'. Just like 'o' but puts the current url in there. same with 't' and 'shift+t'

---

### Post by mcduck on 2009-03-06
Is there anything that makes Firefox behave like ed? :D

---

### Post by thisllub on 2009-03-06
> **Dr Small said:**
> Here's a little custom command that I just wrote (after reading the documentation). It takes you to the Noah Webster 1828 dictionary and looks up the word for you, based on your input.

Like, the usage would be:
```
:define battle
```

Here's the command:
```
:command -nargs=1 define tabopen http://1828.sorabji.com/r.sorabji?word=<args>
```

Of course, you can replace the address to your own dictionary if you please, but this saves me a few clicks from a search engine when I want to look up the definition of a word. :)

Cheers!

Why would you use the Webster dictionary?
All the spelling is wrong and it is his fault.

---

### Post by Dr Small on 2009-03-06
> **thisllub said:**
> Why would you use the Webster dictionary?
All the spelling is wrong and it is his fault.
Because that's the dictionary I use.

---

### Post by kk0sse54 on 2009-03-06
Opera & Vimperopera FTW! :D

---

### Post by DeadRobot on 2009-03-07
Wow this is seriously cool.

One questions.

After typing :bmarks and getting to the list of bookmarks is there a way to access these bookmarks by the keyboard or do you have to click on them with the mouse?

---

### Post by AopicieR on 2009-03-08
> **maple said:**
> If I understand what your saying, try 'shift+o'. Just like 'o' but puts the current url in there. same with 't' and 'shift+t'
Thanks, this is an improvement over ":" and then "arrow up". Still it would be nice to be able to modify the url without the arrow keys. If at least "Ctrl-f" and "Ctrl-b" were available instead of "arrow right" and "arrow left"...

---

