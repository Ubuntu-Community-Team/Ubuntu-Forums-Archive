---
title: "Protect against virus"
date: 2007-06-27
forum: Security Discussions
---

### Post by mxsteini on 2007-06-27
Hi there,
after a small talk with a customer, I googled the web for "linux virus".
After the third page I stoped reading that things because none of that pages was newer the 3 years or so.

For myself I have a spam and virusfilter on my web/mailserver. But in 6 years daily-use I newer saw a virus.

So, what do you think about / know about linux-viruses?
How do you (Do you) protect your system?

---

### Post by nsleiman on 2007-06-27
> **mxsteini said:**
> Hi there,
after a small talk with a customer, I googled the web for "linux virus".
After the third page I stoped reading that things because none of that pages was newer the 3 years or so.

For myself I have a spam and virusfilter on my web/mailserver. But in 6 years daily-use I newer saw a virus.

So, what do you think about / know about linux-viruses?
How do you (Do you) protect your system?

I never protect my linux box, i've heard about rootkit ([http://en.wikipedia.org/wiki/Rootkit](http://en.wikipedia.org/wiki/Rootkit) )or something similar but personally never had to clean/remove a virus :)

---

### Post by Circus-Killer on 2007-06-27
only have a firewall and rootkit checker at the moment.

i setup my firewall using firestarter. and i use chkrootkit to scan for rootkits.
only protection i have.

virus' arent really too much of a problem in linux, because even when a linux machine is infected, damage is limited and is usually cut off very quickly from spreading. i've heard that there are roughly 30 linux virus around. but none of which that are roaming around out of control.

---

### Post by mjwhitfield on 2007-06-27
> So, what do you think about / know about linux-viruses?I know there are so few I don't waste brain power or system resources on them.
> How do you (Do you) protect your system?By using Linux :)

---

### Post by insane_alien on 2007-06-27
generally, i don't but every now and then i'll run a sweep to make sure i haven't accidentally downloaded an infected file that i could pass on to a  windows computer. they have enough problems without me giving them viruses. out of the 3000 viruses(i probably need tone down the dodginess of my browsing) i have came across a grand total of ZERO have done anything other than sit there.

gotta love linux. you can even adopt a policy of click on EVERYTHING and be fine.

---

### Post by Nekiruhs on 2007-06-27
Don't take me wrong, there are a few linux viruses out there. In order to get one though, you have to actively persue it, then give it your root password. Theres all of like 3 of em, and Ubuntus immune to em.

---

### Post by ruza on 2007-06-27
It is simple to make linux virus. 

<snip> in a executable text file

Point: If you do not use root account you are allmost totally secure. 

Ive heared of some new Open Office virus... Anything about that?

---

### Post by mjwhitfield on 2007-06-27
that's not a virus - it can't spread.

---

### Post by Nekiruhs on 2007-06-27
> **ruza said:**
> It is simple to make linux virus. 

<snip> in a executable text file

Point: If you do not use root account you are allmost totally secure. 

Ive heared of some new Open Office virus... Anything about that?
Its a flaw in OO itself, basically, you run open office as root, and somehow, the virus makes a macro in OO. delete stuff.
a) its proof of concept
b) You still have to run OO as root, and who does that?

---

### Post by ruza on 2007-06-27
Anything you can do in terminal(everything) you can do in executable file. So you can maike it spread.

---

### Post by Nekiruhs on 2007-06-27
> **ruza said:**
> Anything you can do in terminal(everything) you can do in executable file. So you can maike it spread.But you cant spread stuff like that in a terminal. Could you give us an example of the commands please?

---

### Post by Cypher on 2007-06-27
> **ruza said:**
> Anything you can do in terminal(everything) you can do in executable file. So you can maike it spread.

Care to elaborate on what you mean?

---

### Post by ruza on 2007-06-27
I dont know how to spread it to random foldes. But i can spread it to predefined folders ullimited number of times. With the help of a C program

#include<stdio.h>
main()
{
   while(1)
   system("sh 'path to executable file'");
}

and in the file should be something like this:

sudo cp 'path to file'  'first path'
.  .  .  .  .  .  .  .  .  .  .  .  .  .  .  . 
.  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .
.  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .
sudo cp 'path to file'  'n-th path'

<snip>

You can even add few lines in C code that can make new executable files that will have random name (rand-function) and copy them everywhere you want. And again and again...

---

### Post by mxsteini on 2007-07-01
One point is that mostly the system is enough protected againg any malware. But how are the userdata?
I would be much more anoyed if someone deletes my mailfolder or projectfolder.

So, does anyone know a website or database with all (mostly all) known linux-viruses?

---

### Post by Atomic Dog on 2007-07-01
> **Nekiruhs said:**
> Its a flaw in OO itself, basically, you run open office as root, and somehow, the virus makes a macro in OO. delete stuff.
a) its proof of concept
b) You still have to run OO as root, and who does that?


What if you turn off password prompt for using sudo?  I have done this in the past (not now).  Would this proof of concept macro execute or does OO have to explicitly be run as root?

---

### Post by mxsteini on 2008-02-20
Thanks to all comments
but one question remains:
Is there a page with all known linux viruses? :confused::confused:

---

### Post by bodhi.zazen on 2008-02-20
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

---

### Post by rlange on 2008-02-20
Sophos thinks there is a problem now. 

Read it here.

[http://www.sophos.com/security/blog/2008/02/1062.html](http://www.sophos.com/security/blog/2008/02/1062.html)

---

### Post by garyed on 2008-02-20
If anyone writes a     sudo rm /    virus in an executable file, could it just sit dormant & wait for someone to become root before it executes?  
 That would be pretty scary.

---

