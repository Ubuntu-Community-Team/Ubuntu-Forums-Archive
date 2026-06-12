---
title: "Is there a way to keep track of what packages you install?"
date: 2008-06-02
forum: The Cafe
---

### Post by PrimoTurbo on 2008-06-02
I want to keep my system clean and I'm wondering if there is some command or software that can keep track of packages that are installed and their dependencies. This would be great for uninstalling.

For example if I check the log it shows something like.

02/06/08 - 12:15 PM - Installed apache, java.
02/06/08 - 12:25 PM - Installed mplayer, nonfreecodecs.

That's just an example.

---

### Post by Kingsley on 2008-06-02
There's information in /var/log/apt/term.log and /var/log/aptitude

---

### Post by Kingsley on 2008-06-02
Oh, I almost forgot about /var/log/dpkg.log also.

---

### Post by Bubba64 on 2008-06-02
> **Kingsley said:**
> Oh, I almost forgot about /var/log/dpkg.log also.

This or the other two commands do not work for me I used terminal with the basic copy paste then I used sudo then I looked under search fro the places what is the secret for access that I am missing besides a few synapses.

---

### Post by bufsabre666 on 2008-06-02
> **Bubba64 said:**
> This or the other two commands do not work for me I used terminal with the basic copy paste then I used sudo then I looked under search fro the places what is the secret for access that I am missing besides a few synapses.

did you add the name of a text editor

ie
```
sudo gedit /var/log/dpkg.log
```

---

### Post by Kingsley on 2008-06-02
> **Bubba64 said:**
> This or the other two commands do not work for me I used terminal with the basic copy paste then I used sudo then I looked under search fro the places what is the secret for access that I am missing besides a few synapses.
Oops. You need to open it up in a text editor or viewer.

I prefer to use less.
```
less /var/log/dpkg.log
```

---

### Post by Bubba64 on 2008-06-02
> **Kingsley said:**
> Oops. You need to open it up in a text editor or viewer.

I prefer to use less.
```
less /var/log/dpkg.log
```

Thanks to the last two posters I can install a distribution and have it set up and running in less than an hour at least on my own computers which have ancient components so I have never really tried to learn a lot of the stuff I should know, I have used other methods for install history like synaptic or history in terminal if I install from there, but this information is quite helpful.

---

### Post by gn2 on 2008-06-02
You can access the history in Synaptic.

Another useful tool for keeping track of what's installed is AptOnCD.

---

### Post by klange on 2008-06-02
As long as you use DEBs or Apt*, they'll all appear in your dpkg logs. Every package I've ever installed appears in Synaptic - even OOo3.

---

