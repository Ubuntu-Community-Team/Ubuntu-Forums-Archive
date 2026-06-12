---
title: "Adding aliases for some commands in Ubuntu Budgie"
date: 2017-02-09
forum: Ubuntu, Linux and OS Chat
---

### Post by nstojic66 on 2017-02-09
Hey everyone,

My name is Nikola and I'm one of the team members that works on Ubuntu Budgie (previously known as budgie-remix until 16.10, Ubuntu Budgie from 17.04 release)

I was wondering on community's opinion about using aliases to make some commands shorter and to encourage the use of terminal for new users.

For example if we're using ```
sudo apt-get update
```, why not shorten it to sudo update or just "update". Searching for new app? ```
sudo search vlc
``` instead of ```
apt-cache search vlc
```. There are probably more examples but these were the first that I thought of that would be useful for normal users. 
```
(sudo apt-add-repository ppa:ubuntuwine/ppa - > sudo add repo ppa:ubuntuwine/ppa)
```

For some commands there is no reason to shorten them or make them different like for example ls > dir or cp>copy to mirror Windows.

Users should know how to utilize some terminal commands later on, but for the start it should be a little more accessible for new people, who are new to the Linux world along with some basic linux commands kept intact.

I would love to hear your opinion on using aliases  introduce new users to terminal.

---

### Post by &amp;KyT$0P# on 2017-02-09
> **nstojic66 said:**
> I was wondering on community's opinion about using aliases ... to encourage the use of terminal for new users.
No.  Pre-defined aliases only confuse new users.

The moment they have to use a Linux system which doesn't have those aliases, they'll be in over their heads.  They will think that because they're comfortable with the aliases, they know all the basic Terminal commands.  Reality is, they'll find it like speaking Elvish to Amish dairy farmers.  Well, I did...until I really learned how to customise the [FONT=Courier New].bashrc[/FONT] file and happened upon the alias definitions in there.

Until I learned [FONT=Courier New].bashrc[/FONT], I didn't even know that some of the commands I typed were aliases.  Neither will any other new users.  We get accustomed to the aliases, get them under our fingers, and then be surprised when they fail.  And most users won't figure out why.

But if you can solve for this problem, it's an interesting idea. :)

---

### Post by bearlake on 2017-02-10
> **halogen2 said:**
> No.  Pre-defined aliases only confuse new users.


+1 and not just new users.

---

### Post by TheFu on 2017-02-10
Had someone ask about why some commands work with 
```
command
```
 and others need
```
./command
```
 and others work with
```
sh command
```
Because they didn't understand the **PATH** and execute permission bits.  Confusing *magic* when you don't understand.

"search" can mean many different things, "pkg-search"?  I seldom need to search for packages - maybe once a year.
"add" can mean many different things too. I'd think bc was shorter when I wanted to add things.

BTW, apt-get has been replaced by "apt".

If your distro adds many default aliases, be certain to let folks know. Probably need to be clear in any how-to that aliases are being provided for convenience.

I have lots and lots of aliases from carried forward from my systems over the last 20+ yrs.  If your aliases conflict or break things, that would be bad and unexpected. OTOH, I generally remove the default Ubuntu aliases, since they either conflict or are never used.  For example, ls=ls -F is my favorite. The extra information provided is worth it.

I've seen some helpful CLI learning tools. Perhaps one of those could be helpful?  Can't find any names now, but remember one that showed the manpage synopsis at the top when a command was entered.

The more I think about this, the more I like the idea.  Think I'll incorporate this into my teaching.  That and filling my ~/bin/ with scripts over the years has helped.

---

### Post by nstojic66 on 2017-02-10
> **TheFu said:**
> Had someone ask about why some commands work with 
```
command
```
 and others need
```
./command
```
 and others work with
```
sh command
```
Because they didn't understand the **PATH** and execute permission bits.  Confusing *magic* when you don't understand.

"search" can mean many different things, "pkg-search"?  I seldom need to search for packages - maybe once a year.
"add" can mean many different things too. I'd think bc was shorter when I wanted to add things.

BTW, apt-get has been replaced by "apt".

If your distro adds many default aliases, be certain to let folks know. Probably need to be clear in any how-to that aliases are being provided for convenience.

I have lots and lots of aliases from carried forward from my systems over the last 20+ yrs.  If your aliases conflict or break things, that would be bad and unexpected. OTOH, I generally remove the default Ubuntu aliases, since they either conflict or are never used.  For example, ls=ls -F is my favorite. The extra information provided is worth it.

I've seen some helpful CLI learning tools. Perhaps one of those could be helpful?  Can't find any names now, but remember one that showed the manpage synopsis at the top when a command was entered.

The more I think about this, the more I like the idea.  Think I'll incorporate this into my teaching.  That and filling my ~/bin/ with scripts over the years has helped.

I agree. However, the main point is actually to show them that it's just a shortcut: For example: alias update='sudo apt-get update; echo The default command is sudo apt-get update, this is just short command'. When user executes 'update' it will update everything and show him what's the default command, or in this case, full command to finish this task. Replacing default commands is counterproductive, however, having shortcuts and explaining it on our website, welcome center, would be added for convenience.

---

