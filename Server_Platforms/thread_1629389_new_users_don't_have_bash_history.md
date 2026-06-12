---
title: "new users don't have bash history"
date: 2010-11-23
forum: Server Platforms
---

### Post by goseph on 2010-11-23
Hi all!

I just installed Ubuntu Server Edition and I've found that my first user has a bash history and I can turn on a coloured prompt by editing my .bashrc etc but new users don't have that!

I did : 

useradd -d /home/newb -m newb
passwd newb

and the correct looking .bashrc file appears to be in /home/newb but it is being ignore by bash when logged in as newb. Instead I am presented with just a dollar prompt instead of "newb@server"

how can I sort out my users with proper prompts?

Thanks for any help or hints

Luke

---

### Post by redmk2 on 2010-11-23
> **goseph said:**
> Hi all!

I just installed Ubuntu Server Edition and I've found that my first user has a bash history and I can turn on a coloured prompt by editing my .bashrc etc but new users don't have that!

I did : 

useradd -d /home/newb -m newb
passwd newb

and the correct looking .bashrc file appears to be in /home/newb but it is being ignore by bash when logged in as newb. Instead I am presented with just a dollar prompt instead of "newb@server"

how can I sort out my users with proper prompts?

Thanks for any help or hints

Luke
Since you did not define the default shell, is it possible that the default is sh (which is really **[COLOR="DarkRed"]dash [/COLOR]**).

What to you get with ```
getent passwd|grep newb
```

You can declare the default shell and then set the prompt if you  need to. Usually this is the new users decision as to shell and prompt.

---

