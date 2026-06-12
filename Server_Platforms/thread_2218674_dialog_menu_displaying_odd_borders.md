---
title: "dialog menu displaying odd borders"
date: 2014-04-21
forum: Server Platforms
---

### Post by LHammonds on 2014-04-21
When using "dialog" to make menus, they used to show a nice graphic-like border around the menu items but now it shows text instead.  Not sure how or when this happened though.

Example:
```
dialog --title "Confirmation"  --yesno "Want to quit?" 6 20
```

Outputs:
```

                      lqqConfirmationqqqqk
                      x Want to quit?    x
                      tqqqqqqqqqqqqqqqqqqu
                      x < Yes > < No  >  x
                      mqqqqqqqqqqqqqqqqqqj
```

This is how it is supposed to look:
[IMG]http://4.bp.blogspot.com/_yqqceaP4wog/Szl2Ds5SVII/AAAAAAAACVE/P-iMQcs_Y4Q/s400/unix-dialog-yesnoBox-shell-script.JPG[/IMG]

Is there some kind of terminal emulation or variable something that needs to be set to make it work right?

**EDIT #1:** I'm using PuTTY 0.63 connecting to Ubuntu Server 12.04.4 (dialog 1.1-20111020) and Ubuntu Server 14.04 (dialog 1.2-20130928)

**EDIT #2**: I can use the "--ascii-lines" option to clean it up but I'd prefer the graphic option if possible.

**EDIT #3:** Here is the solution to this problem which also fixes the aptitude menu:


[LIST=1]
[*]When using PuTTY to connect, click on Window -> Translation -> Remote character set.  Change to UTF-8
[*]Type the following in your SSH/Telnet session to verify the locale you are using is UTF-8:
```
locale
``` 
[*]Type the following in your SSH/Telnet session:
```
echo 'export NCURSES_NO_UTF8_ACS=1' >> ~/.bashrc
``` 
[*]Logout and log back in for the changes to take affect. 
[/LIST]


Thanks,
LHammonds

---

### Post by Habitual on 2014-04-21
Mr Hammonds:
[http://www.linuxquestions.org/questions/linux-general-1/extra-characters-coming-with-dialog-command-4175497687/#post5134493](http://www.linuxquestions.org/questions/linux-general-1/extra-characters-coming-with-dialog-command-4175497687/#post5134493) may help.

---

### Post by LHammonds on 2014-04-21
Thanks for the link.

My setting was already UTF8 so I thought I'd try an older version of PuTTY and 0.62 worked.  Went back to 0.63 and its broke again.  So it looks like I'll stick with 0.62.

**EDIT:** I was thinking about just using [COLOR=#ff0000]**--ascii-lines**[/COLOR] as a bandaid fix but the problem cropped up when going into the aptitude menu.

Thanks,
LHammonds

---

### Post by Habitual on 2014-04-21
Well, you and I both know that just because something is "new" doesn't mean too much these days. :)

---

### Post by LHammonds on 2014-04-21
Ya, I know...I was just updating my "How To" dox for installing Ubuntu Server 14.04 and thought I'd update my tools to the current versions since the last time I did this doc was 2 years ago. :)

---

### Post by Habitual on 2014-04-22
Your HowTos rock!

---

### Post by slickymaster on 2017-11-02
Reopened per OP request

---

### Post by LHammonds on 2017-11-03
Solution can be found in 1st post in EDIT #3 section.

LHammonds

---

### Post by Doug S on 2017-11-03
Oh, Thank you. I have been using "--ascii-lines".

---

