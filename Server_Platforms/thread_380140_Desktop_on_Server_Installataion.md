---
title: "Desktop on Server Installataion"
date: 2007-03-09
forum: Server Platforms
---

### Post by ton80 on 2007-03-09
Hi Forum,

Quick question...
Is it problematic to install server components on a regular Ubuntu 6.10 install?  Meaning, is it ok to do an installation of Ubuntu 6.10 and then add LAMP components and FTP server?  Or is there another way to get desktop on server install?  I have a need for a gui interface on the server for development reasons...and system limitations.  What would be the best solution....keeping security in mind.

Thanks,
Mike

---

### Post by Aberrix on 2007-03-09
there should be any problems, just do a

```
sudo apt-get install desktop
```

that will add all the GUI stuff to your server install.

---

### Post by ton80 on 2007-03-09
OH,
That looks too easy.

Will give it a try.

Thanks,
Mike

---

### Post by Aberrix on 2007-03-09
> **ton80 said:**
> 
That looks too easy.

it really is, I <3 apt-get.

It's just so easy!

---

### Post by ton80 on 2007-03-10
> **Aberrix said:**
> there should be any problems, just do a

```
sudo apt-get install desktop
```

that will add all the GUI stuff to your server install.

OK,
I ran the command as stated above.  I got the error message "Couldn't find package desktop".

I have added "universe" to all repositories listed in /etc/apt/sources.list

So maybe, at least for me, it is not that easy!

What now?

Mike

---

### Post by Nikron on 2007-03-10
There's two ways to do this...

sudo apt-get install ubuntu-desktop
sudo apt-get install xubuntu-desktop
sudo apt-get install kubuntu-desktop

will get you the normal ubuntu install with the lamp server
Be warned though, this will install _everything_ like gaim, evolution, etc... 


So,  I just installed

xorg and fluxbox because it was lighter...

---

### Post by Kinslayer on 2007-03-29
> **Aberrix said:**
> there should be any problems, just do a

```
sudo apt-get install desktop
```

that will add all the GUI stuff to your server install.

You realise this is the exact opposite of what he asked?

---

### Post by statichz on 2007-03-30
I have just installed the server version on my pc. ( I dont know if thats what i should have picked or not) but its what i downloaded and burned.

I think i am running into the same issues that this person has.

When i startup the computer it comes up to a command line. I dont know what to enter in order to view a desktop like you show in the front page. I tried all three of those commands that you just posted (sudo apt-get install unubutu) and i get the same response from all three. It cant find a pakage. For starters i dont even know if i am doing the right thing to view a desktop. Please help, im tired of XP and I am dreading the Vista upgrade. I need something diffrent. Am willing to learn.

---

### Post by Kinslayer on 2007-03-31
I'm sorry I wasn't more helpful with my previous post.  I was in the middle of figuring it all out myself...

I already have a the desktop, and wanted to add the server stack.  This was the terminal command line I used to add the server components (LAMP server):  ```
apache2 php5-mysql libapache2-mod-php5 mysql-server
```

The site is at [http://lost-souls.co.nr](http://lost-souls.co.nr) and if it's up, then I must have done something right.

I found this page to be invaluable here (it's where I got the above commands):  
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Those who installed the server and want the desktop, i.e. after the install you are looking at a you@computer :~$ prompt blinking at you, should use the commands graciously supplied by Aberrix & Nikron to get the nice pretty GUI.  



,,, And thanks to everyone whose posts here helped me out with this.

---

### Post by Kinslayer on 2007-03-31
Statichiz, is what you are typing at the prompt specifically "sudo apt-get install unubutu" or "sudo apt-get install ubuntu-desktop"?  The latter should hopefully work.

---

