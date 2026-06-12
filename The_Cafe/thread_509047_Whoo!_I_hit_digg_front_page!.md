---
title: "Whoo! I hit digg front page!"
date: 2007-07-24
forum: The Cafe
---

### Post by jdong on 2007-07-24
I decided to write an article on zsh (that super cool shell) and it hit the front page of digg. I didn't expect so many people to be interested in it :)


Just in case you guys missed it, it's [http://www.digg.com/linux_unix/Introduction_to_zsh_a_powerful_and_smart_Linux_Unix_shell](http://www.digg.com/linux_unix/Introduction_to_zsh_a_powerful_and_smart_Linux_Unix_shell)

I highly recommend for everyone to at least give zsh a shot. It comes packaged in Ubuntu, and in the article I provided an excellent .zshrc (configuration) file to go along with it, along with a rough tour of the coolest parts (i.e. help+autocomplete, typo correction, etc)

---

### Post by juxtaposed on 2007-07-24
> Are you a bash user wishing your shell would be smarter and even faster? This article gives a good overview of zsh's features, including typo correction and intelligent autocompletion.

Shells are like different ways to use the command line, right? Wouldn't it all be the same anyway, as something like "mount /dev/sdb4" cant really be changed much.

Reading the comments there is odd. Its a wealth of things that sound odd and I don't understand :P Like "Prior to being forced to use ksh on AIX for my job, I always was a bash die-hard. Now that I've been forced to use ksh with vi as the line editor, I am a complete convert. I think I'll give zsh a go." sounds pretty weird when I hardly knew there was a difference. I should read about this stuff on wikipedia instead of asking people things and editing the post a lot... I'm tired...

---

### Post by starcraft.man on 2007-07-24
> **jdong said:**
> I decided to write an article on zsh (that super cool shell) and it hit the front page of digg. I didn't expect so many people to be interested in it :)


Just in case you guys missed it, it's [http://www.digg.com/linux_unix/Introduction_to_zsh_a_powerful_and_smart_Linux_Unix_shell](http://www.digg.com/linux_unix/Introduction_to_zsh_a_powerful_and_smart_Linux_Unix_shell)

I highly recommend for everyone to at least give zsh a shot. It comes packaged in Ubuntu, and in the article I provided an excellent .zshrc (configuration) file to go along with it, along with a rough tour of the coolest parts (i.e. help+autocomplete, typo correction, etc)

Great job jdong. I'll look into the guide later (mildly busy at this instant) I love fiddling with CLI/shells :D.

---

### Post by jdong on 2007-07-25
> **juxtaposed said:**
> Shells are like different ways to use the command line, right? Wouldn't it all be the same anyway, as something like "mount /dev/sdb4" cant really be changed much.

Reading the comments there is odd. Its a wealth of things that sound odd and I don't understand :P Like "Prior to being forced to use ksh on AIX for my job, I always was a bash die-hard. Now that I've been forced to use ksh with vi as the line editor, I am a complete convert. I think I'll give zsh a go." sounds pretty weird when I hardly knew there was a difference. I should read about this stuff on wikipedia...

Shells are different ways to use the commandline, yes, but each shell has a different set of features....

For example, what if you typed "muotn /dev/sdb4" and hit enter? Bash would tell you that it's an invalid command. Zsh says:
```

zsh: correct 'muotn' to 'mount' [nyae]? 

```


I give numerous other examples and screenshots of what zsh does over (most) other shells in the article too.

---

### Post by juxtaposed on 2007-07-25
> For example, what if you typed "muotn /dev/sdb4" and hit enter? Bash would tell you that it's an invalid command. Zsh says:

Spell checking commands sounds pretty cool, i'll have to read your article then and try it then :)

---

