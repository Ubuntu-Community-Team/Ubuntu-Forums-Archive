---
title: "Somebody tell me everything i need to install I.E. in ubuntu..?"
date: 2006-09-05
forum: The Cafe
---

### Post by jason.b.c on 2006-09-05
I just spent the better part of an hour and a half downloading internet explorer trying to install it through wine and after the damn thing finished downloading it wouldn't install correctly...

It started to install and then after (what i thought) it had finished i was told it couldn't (or wasn't) installed ......](*,) 


What do i do to get it in here the right way..?

---

### Post by croak77 on 2006-09-05
winetools.

---

### Post by jason.b.c on 2006-09-05
> **croak77 said:**
> winetools.

[-(    I've got that , What else...???

---

### Post by GuitarHero on 2006-09-05
Why would you want that awful browser anyway?  Wine is all you should need if it is possible.

---

### Post by croak77 on 2006-09-05
> **jason.b.c said:**
> [-(    I've got that , What else...???

Did you install everything in order? Or try; 

[http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html)

---

### Post by aysiu on 2006-09-05
**Step 1.** Make sure you have extra repositories enabled by following these instructions:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

**Step 2.** Install *cabextract* and *wine* by pasting this command into the terminal: ```
sudo aptitude update && sudo aptitude install cabextract wine
```

**Step 3.** Download IEs4Linux and follow the instructions for installing Internet Explorer:
[http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html)

In answer to GuitarHero's question, people sometimes need IE for website design to see how 88% of the people who use the web will see the website. Other people need it for IE-only websites that even User Agent Switcher can't handle.

---

### Post by GuitarHero on 2006-09-05
I create standards complient code and leave it up to the browser to properly render it, may not be the best way to do it but opera and firefox never have a problem with it.  I tend to switch everyone I know over to firefox ha.

---

### Post by aysiu on 2006-09-05
> **GuitarHero said:**
> I create standards complient code and leave it up to the browser to properly render it, may not be the best way to do it but opera and firefox never have a problem with it.  I tend to switch everyone I know over to firefox ha.
That's what I do for my personal websites. But if you actually design websites for clients who have non-profit organizations or businesses (and they *pay you money*), then it's a good idea to test how the site will look and behave in the most popular web browser, no matter how awful you think it is.

---

### Post by jason.b.c on 2006-09-05
> **aysiu said:**
> **Step 1.** Make sure you have extra repositories enabled by following these instructions:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

**Step 2.** Install *cabextract* and *wine* by pasting this command into the terminal: ```
sudo aptitude update && sudo aptitude install cabextract wine
```

**Step 3.** Download IEs4Linux and follow the instructions for installing Internet Explorer:
[http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html)

In answer to GuitarHero's question, people sometimes need IE for website design to see how 88% of the people who use the web will see the website. Other people need it for IE-only websites that even User Agent Switcher can't handle.

You know it's funny you mention all that, Especialy **IEs4Linux**, I installed that one as well and i have to say:    "It dosen't freakin work..!"

How the heck do i launch it...????


I have wine..

I have cabextract..

I repo's enabled..

So..?, How the heck..???

---

### Post by aysiu on 2006-09-05
Paste these commands in the terminal. This can, of course, all be done graphically, but it's a lot easier to just paste in the commands: ```
wget -c http://www.tatanka.com.br/ies4linux/downloads/ies4linux-2.0.1.tar.gz
tar -xvzf ies4linux-2.0.1.tar.gz
cd ies4linux-2.0.1/
chmod +x ies4linux
./ies4linux
sudo mv ~/bin/ie6 /usr/bin/ie6
``` Then, to launch it, just use the command ```
ie6
``` **Translation**:
Download the zipped installer file from the IEs4Linux website
Unzip it
Change to the newly unzipped directory.
Install IEs4Linux
Move the launcher to the regular launcher path

---

### Post by jason.b.c on 2006-09-06
It still won't launch...

> jason@Hp-Vectra-VL:~$ ie6
bash: ie6: command not found
jason@Hp-Vectra-VL:~$ /usr/bin/ie6
bash: /usr/bin/ie6: No such file or directory
jason@Hp-Vectra-VL:~$



What's wrong with this thing...???

---

### Post by cjm5229 on 2006-09-06
Try adding this to the end of your sources list.   	 	 	 	 	 	 	 	 	  ## Bleeding edge wine repository for Dapper ## only uncomment it if you need it ## deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main ## deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main Then remove wine and reinstall the latest version. Then install IE4Linux. You should have Icons on your desktop. You can also install it in Crossover Office, if all else fails. I have IE5.0, IE5.5, and IE6.0  installed with IE4Linux with no problem at all.
I installed wine with Automatix.

---

### Post by jason.b.c on 2006-09-06
AH-HA   -  It works, It must not have installed correctly before or something...:-D

---

### Post by eric.stone on 2006-09-28
Hi.  I'm having trouble installing IE6 on my AMD64.  Followed your instructions and got the following:


Installing IE 6
 Initializing
 Creating Wine Prefix
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
Your wine does not have wineprefixcreate installed. Maybe you are running an old Wine version. Try to update it to the  latest version.
](*,)

---

### Post by maniacmusician on 2006-09-28
did you try this:
> 
Try adding this to the end of your sources list. ## Bleeding edge wine repository for Dapper ## only uncomment it if you need it ## deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main ## deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main Then remove wine and reinstall the latest version. Then install IE4Linux. You should have Icons on your desktop. You can also install it in Crossover Office, if all else fails. I have IE5.0, IE5.5, and IE6.0 installed with IE4Linux with no problem at all.
I installed wine with Automatix.

aka are you running the latest version of wine?

---

### Post by aysiu on 2006-09-28
I don't think Wine works for 64-bit. They don't have a binary for it in the Ubuntu repositories...

---

### Post by maniacmusician on 2006-09-28
> **aysiu said:**
> I don't think Wine works for 64-bit. They don't have a binary for it in the Ubuntu repositories...
duh, i didn't even catch that in his post, thanks for pointing it out.

you might find this useful: [How to build 32-bit Wine on a 64-bit (x86-64) system]("http://wiki.winehq.org/WineOn64bit")

---

### Post by eric.stone on 2006-09-29
Thanks for the 32 on 64 bit lead, I'll let you know how it goes.
E

---

