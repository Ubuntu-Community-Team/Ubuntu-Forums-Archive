---
title: "Avast error in Ubuntu 9.10"
date: 2010-05-21
forum: Security
---

### Post by ravisunny2 on 2010-05-21
[FONT=Times New Roman][SIZE=3]The **Avast! for Linux** installation went through without any error (in Ubuntu 9.10), and Avast appeared in the **Applications** menu.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]But, when I ran **Avast**, I got the following error message.[/SIZE][/FONT]
> 
[SIZE=3][FONT=Times New Roman][FONT=Times New Roman][SIZE=3]Avast! Error[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]An error occured in avast! engine: Invalid argument.[/SIZE][/FONT]
[/FONT][/SIZE]
 
[FONT=Times New Roman][SIZE=3]Any help or suggestions would be appreciated. [/SIZE][/FONT]

---

### Post by cariboo on 2010-05-21
You'll probably get a quicker answer to your question [here]("http://forum.avast.com/index.php?board=2.0"), we really don't support 3rd party apps, as they aren't in the repositories.

---

### Post by ravisunny2 on 2010-05-21
[FONT=Times New Roman][SIZE=3]Sorry, **carriboo907**.[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]Didn't realize I couldn't post the avast problem here.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]The link above gives me :[/SIZE][/FONT]
[FONT=Times New Roman][FONT=Times New Roman][SIZE=3]> [FONT=Times New Roman][FONT=Times New Roman]Internet Explorer cannot display the webpage[/FONT][/FONT][/SIZE][/FONT]
[/FONT]

---

### Post by OpSecShellshock on 2010-05-21
> **ravisunny2 said:**
> [FONT=Times New Roman][SIZE=3]Sorry, **carriboo907**.[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]Didn't realize I couldn't post the avast problem here.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]The link above gives me :[/SIZE][/FONT]
[FONT=Times New Roman]
[/FONT]

Link has two "http://" in it. Right click and copy, paste into the address bar and backspace over one of them.

---

### Post by cariboo on 2010-05-21
Thanks OpSecShellshock, that's the third one today :), I should proof read my links before posting them.

@ravisunny2

It's not that you shouldn't post a question about av-scanners, not many of us use them, so you may have to wait for quite a while before getting an answer.

Most av-scanners only scan for Windows malware, so unless you're running a mail server, there isn't a great need to run one.

---

### Post by ravisunny2 on 2010-05-22
[LEFT]                                         [FONT=Times New Roman][SIZE=3]All is well, **carriboo907**. :)

I happen to have a **MS Windows** mindset, and the transition is slow.
[/SIZE][/FONT]  [LEFT] [FONT=Times New Roman][SIZE=3]

[/SIZE][/FONT]  [/LEFT]
            [LEFT][FONT=Times New Roman][SIZE=3]This seems to have solved my problem.

[/SIZE][/FONT][FONT=Times New Roman][SIZE=3][COLOR=Black]cd /etc/init.d/[/COLOR][/SIZE][/FONT][/LEFT]
        [LEFT][FONT=Times New Roman][SIZE=3][COLOR=Black]      sudo gedit Rcs[/COLOR][/SIZE][/FONT][FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT] [FONT=Times New Roman][SIZE=3]

After the comments added 

[/SIZE][/FONT] [/LEFT]
        [LEFT][FONT=Times New Roman][SIZE=3]sudo sysctl -w kernel.shmmax=128000000[/SIZE][/FONT][/LEFT]
   
   [/LEFT]

---

### Post by jejemon on 2010-05-22
yeah I agree not many people in this community use Anti Virus softwares. 
Well I suggest you start embracing the Linux way of using / setup the machine. 
Seriously you do not really need to have Anti Virus on your linux machine

[pantry solutions Denver](http://www.shelfgenie.com/blog/roll-out-shelves-denver)
[Conference Tables](http://www.eqaofficefurniture.com/conference-tables-cat-300.html)

---

