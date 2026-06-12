---
title: "Drop elevated privileges through terminal"
date: 2011-05-02
forum: Security
---

### Post by black_cat on 2011-05-02
I'm absolute beginner ubuntu user, need help.....!!!!#-o
How to *Drop all elevated privileges* through terminal....???

---

### Post by Dave_L on 2011-05-02
Is this what you mean?

```
sudo -k
```

For more info:

```
man sudo
```

---

### Post by sj1410 on 2011-05-02
please be more specific on your requirement.

---

### Post by black_cat on 2011-05-02
> **Dave_L said:**
> Is this what you mean?

```
sudo -k
```For more info:

```
man sudo
```


no its doesn't what I mean....!!!
you know to kill sudo timestamp command must be like this "sudo -k"

my question is how to kill gksudo timestamp...???

---

### Post by CandidMan on 2011-05-02
Same command that Dave_L gave:
press Alt + F2, then type ```
sudo -k
```
hit enter

---

### Post by black_cat on 2011-05-03
> **CandidMan said:**
> Same command that Dave_L gave:
press Alt + F2, then type ```
sudo -k
```hit enter


Thanks work find, for me.
But what I exactly mean is?
"I did set authentication mounting where add code some like -> timestamp_timeout on sudoer"

This setting will effect every mounting you must enter user password. After do enter password correctly some icon (figured key) applet was show and that for Drop all elevated privileges.
My question is how to do Drop elevated privileges but use terminal (CLI)...???:popcorn:

---

### Post by CandidMan on 2011-05-03
My understanding is that your 'desktop' and any terminal are independent of each other. They run in separate parts of the memory(?). So anything you do in the CLI doesn't directly affect the desktop.
If you put this command into the terminal ```
w
``` you'll probably see that you're logged in twice.
Like I'm logged into "tty7" and "pts/0".
Try cycling through the consoles by pressing Ctrl + Alt + F1,F2,...F7 
(I've just done that and it's scrambled my screen (sigh))

---

### Post by black_cat on 2011-05-04
> **CandidMan said:**
> My understanding is that your 'desktop' and any terminal are independent of each other. They run in separate parts of the memory(?). So anything you do in the CLI doesn't directly affect the desktop.
If you put this command into the terminal ```
w
``` you'll probably see that you're logged in twice.
Like I'm logged into "tty7" and "pts/0".
Try cycling through the consoles by pressing Ctrl + Alt + F1,F2,...F7 
(I've just done that and it's scrambled my screen (sigh))


I get it, Thanks CandidMan.:KS
That's why ubuntu get you Applet (key) show up, cause terminal and desktop are independent separated process.

---

### Post by hariprasad1001 on 2013-01-28
> **black_cat said:**
> I get it, Thanks CandidMan.:KS
That's why ubuntu get you Applet (key) show up, cause terminal and desktop are independent separated process.
can u please say how to install packages in software center..because whenever i tried it shows "drop elevated privilages" and failed to download...

please help it is vey useful to me now....
thank you

---

### Post by sandyd on 2013-01-28
**Necromancing - thread closed**
Please do not post in threads that are more than one year old, as lots of changes occur between Ubuntu releases, and the solution(s) and problem(s) listed may not apply to current releases.

If you want to get help with your issue, please start a new thread.

Thanks!

---

