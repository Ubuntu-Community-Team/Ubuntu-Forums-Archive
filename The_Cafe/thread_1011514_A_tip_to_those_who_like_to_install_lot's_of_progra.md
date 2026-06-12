---
title: "A tip to those who like to install lot's of programs."
date: 2008-12-14
forum: The Cafe
---

### Post by CJ Master on 2008-12-14
Hello,

I'd like to share a tip to ya'll that I figured out recently. Basically, it cuts down the time it takes typing to install different apps.

(note for anybody that doesn't use gnome, substitue 'gedit' for 'vim'.)

Firstly, type in the command:

```
gedit .bash_aliases
```

Now at the end of the file type in:

```
alias install='sudo aptitude install'
alias pacman='sudo aptitude install'
alias get='sudo aptitude install'
```

**Useful tip**: If you don't want aptitude to ask you weather or not your sure to install, add "-y" after all the aptitudes above.

Save.

Now type in the *terminal*:

```
gedit .bashrc
```

Find the section with this:
```
#if [ -f ~/.bash_aliases ]; then
    #. ~/.bash_aliases
#fi
```

...and remove all #.

Save that.


Congrats, your done! You can now type in simply

```
install somepackage
```

instead of

```
sudo apt-get install somepackage
or
sudo aptitude install somepackage
```

Hope this helped!):P

---

### Post by Joeb454 on 2008-12-14
I would highly recommend **AGAINST** using the ```
aptitude -y
``` option.

Mainly because this tells aptitude to assume you want to say yes to **any** questions it has.

Now while you may very well want to agree to it, I believe it's better to have that option available to say no if you wish to.

Just my thoughts

---

### Post by gomes.luiz on 2008-12-14
Hi CJ,

It's very nice tip. I enjoy it.

Thanks

---

### Post by CJ Master on 2008-12-14
Alright, I edited it out. I'm under the impression that it's just for conformation because thats what the aptitude help file said :P

Hey thanks very much gomes!

---

### Post by acelin on 2008-12-14
lot's
lot's
lot's
lot's
lot's
lot's
lot's
lot's
lot's
lot's
lot's
lot's
lot's
lot's

---

### Post by magmon on 2008-12-14
Isnt that alot less secure?

---

### Post by kk0sse54 on 2008-12-14
> **magmon said:**
> Isnt that alot less secure?

How? It still requires the use of sudo thus prompting you for your password.

---

### Post by magmon on 2008-12-14
Thought it removed the need for sudo?

---

### Post by kk0sse54 on 2008-12-14
Removes the need to manually type sudo each time along with aptitude install. Though it's not only limited to sudo aptitude install in that you can use bash aliases for any command.

---

### Post by magmon on 2008-12-14
Ah, ok. Nvm then.

---

### Post by CJ Master on 2008-12-15
> **acelin said:**
> lot's
lot's
lot's
lot's
lot's
lot's
lot's
lot's
lot's
lot's
lot's
lot's
lot's
lot's

I'm sure there's some meaning to this message, but i have no idea what...

[quote=manmon]Isnt that alot less secure?[/quote]

As C!oud replied, nope.

---

### Post by billgoldberg on 2008-12-15
> **magmon said:**
> Thought it removed the need for sudo?

It's just an alias. The command is still "sudo aptitude xxx".

So you still need to enter your password.

Just imagine if that wasn't the case ...

---

### Post by DirtDawg on 2008-12-15
> **magmon said:**
> Isnt that alot less secure?

Don't you mean "a lot's less secure"?

Sorry, couldn't resist. :D

---

### Post by CJ Master on 2008-12-15
> **DirtDawg said:**
> Don't you mean "a lot's less secure"?

Sorry, couldn't resist. :D

No he was correct, he didn't mean "a lot is less secure."

Back on topic :)

---

### Post by igknighted on 2008-12-15
> **CJ Master said:**
> No he was correct, he didn't mean "a lot is less secure."

Back on topic :)

relax, CJ... they're just having a couple giggles about the typo in the thread title.

---

### Post by acelin on 2008-12-15
> **igknighted said:**
> relax, CJ... they're just having a couple giggles about the typo in the thread title.

More like giggles at a common grammatical error made by the majority of speakers, both native and non-native, of the English language.

---

### Post by CJ Master on 2008-12-15
> **igknighted said:**
> relax, CJ... they're just having a couple giggles about the typo in the thread title.

Actually, he was kidding around about a typo in another guy's reply (I think :confused: ) :p

Oh yea, thanks for the heads up for typo in title lol, i'll fix that.

---

### Post by koenn on 2008-12-15
> **Joeb454 said:**
> I would highly recommend **AGAINST** using the ```
aptitude -y
``` option.

Mainly because this tells aptitude to assume you want to say yes to **any** questions it has.

Now while you may very well want to agree to it, I believe it's better to have that option available to say no if you wish to.

Just my thoughts

man aptitude
```

       -y, --assume-yes
           When a yes/no prompt would be presented, assume that the user
           entered “yes”. In particular, suppresses the prompt that appears when installing, upgrading, or removing packages. 
**Prompts for  “dangerous” actions, such as removing essential packages, will still be displayed.** 
```

same goes for apt-get. -y skips the confirmation, but questions about important things (install packages without authentication, ...) will still need a reply.
You can skip those with --force-yes ...

---

### Post by CJ Master on 2008-12-15
^actually didn't know that you could do that with apt-get, thanks!

---

### Post by koenn on 2008-12-16
> **CJ Master said:**
> ^actually didn't know that you could do that with apt-get, thanks!
just don't come complaining when you're doing blind automated upgrades and something breaks :)

---

### Post by fiddler616 on 2008-12-16
Did you really mean for all three aliases to be identical? No apt-get action? (By alias I mean the string the alias is replacing, my terminology is suffering...)

---

### Post by CJ Master on 2008-12-16
> **fiddler616 said:**
> Did you really mean for all three aliases to be identical? No apt-get action? (By alias I mean the string the alias is replacing, my terminology is suffering...)

Not sure what you mean no apt-get action, but yea all 3 are meant to be the same, to suit different preferences.

> just don't come complaining when you're doing blind automated upgrades and something breaks

Oh don't worry, i will :p

*continues to use nonverified updates*

Bleeding edge is fun :D

---

