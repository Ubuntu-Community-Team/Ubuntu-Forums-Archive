---
title: "several users logged in. Who are they?"
date: 2009-08-11
forum: Server Platforms
---

### Post by gypsumwolf on 2009-08-11
I have 2 servers. When someone logged-in the message says how many users are logged-in. Is there a way to see which users they are by seeing their user-names in a list or something?

---

### Post by garfonzo on 2009-08-11
```
who -u
```

Is that what you're looking for? Or do you mean you want to see who's logged in eveytime you log in? *confused*

---

### Post by gypsumwolf on 2009-08-11
That is exactly what I was looking for. Now u peeked my interest. To view who is logged in every time I am logged in I would guess adding "who -u" to "/etc/profile". Is there another thing your talking about?

---

### Post by garfonzo on 2009-08-12
> **gypsumwolf said:**
> I would guess adding "who -u" to "/etc/profile".
Close. the file you want to edit is called profile, but it is in YOUR home directory. So, ```
~/.profile
```
is the location. Note the dot "." before the word profile. 

That is a script so you can drop a bunch of commands in there that will run every time you log in.

---

### Post by scorp123 on 2009-08-12
> **gypsumwolf said:**
>  To view who is logged in every time I am logged in I would guess adding "who -u" to "/etc/profile". Is there another thing your talking about? I'd do it in a different way.

There are two very nice and useful packages you might be interested in:
[LIST]
[*]landscape-client
[*]update-motd
[/LIST]

Install these two. e.g. via this command:
```
sudo apt-get update && sudo apt-get install landscape-client update-motd
```

The package "landscape-client" will complain that it is useless without a subscription to Canonical Inc.'s "Landscape" remote monitoring service. Just ignore that. It works for what you want it to do, subscription or not.

Once those two packages are installed you have to trigger the execution:
```
sudo update-motd --enable
```

Now, what does all of this do? There is a file: **/etc/motd** .... "motd" stands for "**_M_**essage **_o_**f **_t_**he **_d_**ay" ....  In ancient times UNIX admins would write messages to their users into that file and users would get to see it everytime they log in.

"Out of the box" on Ubuntu this file is only used to display the warning about "Ubuntu comes without any warranty ... " and the other legal bla bla bla. How sad. With the two packages above the file is put to a better use ... to display lots of useful things about your system.

Here is what I get when I login, thanks to these two packages:

```
Linux serenity 2.6.28-15-generic #48-Ubuntu SMP Wed Jul 29 08:54:56 UTC 2009 i686


  System information as of Wed Aug 12 14:50:01 CEST 2009

  System load:    0.38                Swap usage:  0%     Users logged in: 8
  Usage of /home: 33.5% of 200.91GB   Temperature: 47 C
  Memory usage:   23%                 Processes:   171

  Graph this data and manage this system at https://landscape.canonical.com/
```

I guess this is more like what you'd want? Or maybe a good starting point for more customisations?

---

### Post by gypsumwolf on 2009-08-12
That and the "who" are a mixture of what I want. You both helped me.

---

### Post by gypsumwolf on 2009-08-12
Can I add anything I want to "motd" without it being overwritten? It looks like "motd" is written to by another program or script.

Also can I get a message to pop up whenever someone logges-in or out?

e.g.

~#
~#
eric pts/0 2009....
~#

(My server has only a few users)

---

### Post by garfonzo on 2009-08-12
> **gypsumwolf said:**
> Also can I get a message to pop up whenever someone logges-in or out?

I'm not sure about your first question, but as for the second, you could write a little cron job which runs every 5 minutes (or whatever, every 30 seconds, every half hour) which checks the status of whose logged in and spit out a message if things change.

I've not written a cron script/job myself so I don't know about it much. However, I'll soon be setting up my backup schedule on a cron script so that's where I thought your situation might also benefit from a cron script.

---

### Post by scorp123 on 2009-08-13
> **gypsumwolf said:**
> It looks like "motd" is written to by another program or script. Yes, it gets updated here and there by a script. Look at this file: **/etc/motd.tail**

Whatever is in there will be appended to /etc/motd ....

I always delete that file as it only contains the "Ubuntu comes without warranty ..." legal bla bla bla.

---

### Post by gypsumwolf on 2009-08-13
Yay! Another Solved thread.

---

