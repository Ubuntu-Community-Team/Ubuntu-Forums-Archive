---
title: "Play DVD movies with one click of your mouse"
date: 2009-04-29
forum: The Cafe
---

### Post by mdpalow on 2009-04-29
Seeing a lot of people having problems playing DVD's.

Just a reminder that QuickStart can help you load all the necessary codec files with one click.

Save yourself the hassle of trying to remember all the commands.

See my link below and put it in your toolbox for later.

mdpalow

---

### Post by Saint Angeles on 2009-04-29
i usually just make sure that people are adding the medibuntu repository...

---

### Post by billgoldberg on 2009-04-29
One copy/paste command:

```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

---

### Post by fatality_uk on 2009-04-29
> **billgoldberg said:**
> One copy/paste command:

```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

Exactly!!!

I would usually bundle something like this into a bash script and pass it to new users.

---

### Post by richg on 2009-04-29
I tried the "easy" instructions about a year ago on my desktop. Did not work for me. Someone suggested Mint 6 and I was able to view DVDs right out of the box.

Installed Mint 6 on my wireless laptop with the same nice results. 

I find that confusing as Mint is built on 8.10 and 8.10 did not work for me either.

I now suggest Mint 6 to people but I admit, Ubuntu has better forums.

Rich

---

### Post by doas777 on 2009-04-29
"QuickStart"? kono wa desu ka?

---

### Post by dragos240 on 2009-04-29
This? (Polite)
(My attempt at translating)

---

### Post by dmizer on 2009-04-29
Let's remember that these are English speaking forums.

Thank you :)

---

### Post by doas777 on 2009-04-29
> **dmizer said:**
> Let's remember that these are English speaking forums.

Thank you :)

sorry, I'm just trying to use the japanese, lest I use it. dragos, your right on. 
"What is this?"

---

### Post by dragos240 on 2009-04-29
Thank you. I try.

---

### Post by doas777 on 2009-04-29
I'm glad we've established that, so now what is 'Quickstart'? got a link op?

---

### Post by dmizer on 2009-04-29
> **doas777 said:**
> got a link op?

Link is in the OP's sig.

---

### Post by Tews on 2009-04-29
Quick Start is a backup utility for Ubuntu.  Ive been using it for just about a year, and frankly, I cant see myself using anything else ..

Get it [[color=blue]here...[/color]]("http://www.quickstart.freeforums.org/")

---

