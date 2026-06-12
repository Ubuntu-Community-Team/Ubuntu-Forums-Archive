---
title: "How can i have my desktop like this ?"
date: 2010-09-20
forum: The Cafe
---

### Post by Shoala on 2010-09-20
hello guys ,
check this pic out and if any1 knows how can change desktop like this ( that part which shows system info ) feel free to help me 

PS: I alredy installed Docky .

---

### Post by matchett808 on 2010-09-20
its called conky if you have a search in the forums for conky you'll find loads of help

---

### Post by knightcoder on 2010-09-20
Something like this would help -

[http://www.omgubuntu.co.uk/2010/05/easy-to-use-lucid-themed-conky-bar/](http://www.omgubuntu.co.uk/2010/05/easy-to-use-lucid-themed-conky-bar/)

---

### Post by Shoala on 2010-09-20
ty guys

---

### Post by Shoala on 2010-09-20
Hello again ,
Guys I have got a new problem so once again I need your helps .
 I did exactly like this :

**nstall/Use**

 Downloaded okay? Great. Now I’m going to assume that you don’t  already have Conky installed. To remedy this open a terminal and type: –  
 
[LIST]
[*]sudo apt-get install conky
[/LIST]
 Now you have Conky we need to use the Conky theme.
 
[LIST]
[*]Extract the archive you downloaded a few steps back
[*]Move the *.conkytheme folder *extracted into your home folder  (if it’s not already there)
[*]Run the following in a terminal: *conky -c ~/.conkytheme/conkyrc*
[/LIST]
 You should now see Conky bar on the bottom.




and its Ok and works fine BUT when I restart my pc Its Gone  I tried to add it to startup applicatin and the problem is It starts with out the theme .


all I need to  know is how can I have conky auto start with theme ?


Thank you .

---

### Post by NCLI on 2010-09-20
Add "conky -c ~/.conkytheme/conkyrc" to Startup Applications.

---

### Post by Shoala on 2010-09-20
> **NCLI said:**
> Add "conky -c ~/.conkytheme/conkyrc" to Startup Applications.

thnx mate but my problem is doest load theme and I need to enter '' *conky -c ~/.conkytheme/conkyrc ''  in *terminal 

Is there any way to auto load theme ?

---

### Post by NCLI on 2010-09-20
> **Shoala said:**
> thnx mate but my problem is doest load theme and I need to enter '' *conky -c ~/.conkytheme/conkyrc ''  in *terminal 

Is there any way to auto load theme ?

It should. Try replacing the "~" with /home/your-username

---

### Post by Rasa1111 on 2010-09-20
This may help you even more~ 
Perfect for a noob..
I present you.. Conky~ The easy way!   lol

Conky Wizard~ [http://maketecheasier.com/configuring-conky-the-very-easy-way/2010/08/24](http://maketecheasier.com/configuring-conky-the-very-easy-way/2010/08/24)

 Have fun!

---

### Post by Shoala on 2010-09-20
> **NCLI said:**
> It should. Try replacing the "~" with /home/your-username

Thx Its working

---

