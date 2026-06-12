---
title: "Fish - the user friendly command line program"
date: 2006-09-03
forum: The Cafe
---

### Post by saracen on 2006-09-03
An attempt at making the command line interface more user-friendly.  Tab completions have descriptions, misspelled options for commands are automatically highlighted, automatic syntax highlighting for more complex commands, and more.

[http://roo.no-ip.org/fish/](http://roo.no-ip.org/fish/)

---

### Post by Omnios on 2006-09-03
Very interesting downloaing it now to check it out

---

### Post by mostwanted on 2006-09-03
Me 2 ^^

I replaced BASH with Fish by going into Edit &#8594; Current profile, selected the second tab and added my own command (fish) to be executed instead of the ordinary BASH shell.

---

### Post by ssam on 2006-09-03
i have seen fish and it looks very interesting. i think i might be a bit hooked on my bash-isms to use it though. it would be nice if some things like syntax highlighting could be put into bash.

seen as ubuntu defaults to nano instead of vi(m), maybe it should be fish instead of bash.

---

### Post by mssever on 2006-09-03
> **mostwanted said:**
> I replaced BASH with Fish by going into Edit &#8594; Current profile, selected the second tab and added my own command (fish) to be executed instead of the ordinary BASH shell.

If you do ```
chsh /usr/bin/fish
``` it will change your default shell everywhere, not just in gnome-terminal.

Anyone else getting weird behavior and segfaults when using fish?

For example, ```
less file1
^Z (to suspend less)
less file2
^Z
fg -
``` Fish prints the following: ```
scott@scott-laptop /e/skel> fg -
Send job 2, 'fg -' to foreground

``` But job 2 doesn't come to the foreground. Besides, the expected behavior is that job 1 would come to the foreground. Also, I don't get my prompt back. I have to go fishing (killall fish :)) to get a prompt.

Next, if you type fg when there are no background jobs, fish crashes with a segfault.

So, while fish is an interesting concept, it needs a lot more work before it will be usable for me.

---

### Post by Note360 on 2006-09-04
Is their any way to set a right prompt?

---

### Post by Wallakoala on 2006-09-04
pretty cool...

I like the highlighting.

It seems a little slower than bash to me though.

---

### Post by 3rdalbum on 2006-09-05
Fish is a touch slower than Bash, but you get a lot more.

You can tab-complete some command parameters, and you can also tab-complete packages when using the apt-get command! The history works well too - if you type "sudo", for instance, and then hit the Up arrow, it will only show you the commands you've typed that started with "sudo".

It's the greatest. I've never had problems with it, but then I never put terminal commands in the background and foreground and stuff.

Oh, and you can change directories without typing cd!

---

### Post by jbuberel on 2008-01-23
I created a debian/ubuntu package for the latest release - v1.23.0 - and it can be downloaded here:

[http://www.buberel.org/fish_1.23.0-1ubuntu1_i386.deb](http://www.buberel.org/fish_1.23.0-1ubuntu1_i386.deb)

Regards,
Jason

---

