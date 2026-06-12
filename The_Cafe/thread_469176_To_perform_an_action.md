---
title: "To perform an action?"
date: 2007-06-09
forum: The Cafe
---

### Post by SheNux on 2007-06-09
I've seen those coffee cups with code for how to make a coffee printed on them.

I've got the same kind of idea but for a shirt or tattoo.

Hypothetically, say I were to perform an action, say, slicing a tomato?

So far I've got this:

[I]
SheNux@linux:~$ mount /dev/knife /home/SheNux/hand
SheNux@linux:~$ mount /dev/tomato /home/kitchen/counter
SheNux@linux:~$ -slice /dev/tomato
SheNux@linux:~$
bash: -slice: command not found
SheNux@linux~$[/i]

I want the command to fail on purpose. How's that so far? Any tips on refining the code so it's clearer and more true to general terminal bash? Geekier?

Forgive me if my terminology is a little wrong, I'm still learning! Criticism and tips are much appreciated!

---

### Post by orange2k on 2007-06-09
maybe you have to do it as root...;)

---

### Post by SheNux on 2007-06-09
Will it make much difference doing it as root? I'm failing the command on purpose, perhaps I don't know how to cut tomatoes? :D If root will make it geekier then of course!

---

### Post by orange2k on 2007-06-09
Sudo makes it geekier, of course, but then you`ll have to know what you`re doing or else you`ll slice your fingers instead of tomatoes...

---

### Post by FuturePilot on 2007-06-09
I think you need to do this first```
cd /knife
```
```
./configure --prefix=/usr
```
```
sudo make
```
```
sudo checkinstall
```
:lolflag:I like your idea.

---

### Post by SheNux on 2007-06-09
> **orange2k said:**
> Sudo makes it geekier, of course, but then you`ll have to know what you`re doing or else you`ll slice your fingers instead of tomatoes...
Lol! :D

And FuturePilot, I've got no idea what you're on about except for cd /knife which does indeed make sense!

[I]SheNux@linux:~$ mount /dev/knife /home/SheNux/hand
SheNux@linux:~$ mount /dev/tomato /home/kitchen/counter
SheNux@linux:~$ cd /knife
SheNux@linux:~$ -slice /dev/tomato
SheNux@linux:~$
bash: -slice: command not found
SheNux@linux~$[/I]

---

### Post by orange2k on 2007-06-09
If you`re unsure on how to slice tomatos be sure to do this:

sudo apt-get install cook

or better yet

sudo apt-get install dial restaurant:-\"

---

### Post by reacocard on 2007-06-09
> **SheNux said:**
> I've seen those coffee cups with code for how to make a coffee printed on them.

I've got the same kind of idea but for a shirt or tattoo.

Hypothetically, say I were to perform an action, say, slicing a tomato?

So far I've got this:

[I]
SheNux@linux:~$ mount /dev/knife /home/SheNux/hand
SheNux@linux:~$ mount /dev/tomato /home/kitchen/counter
SheNux@linux:~$ -slice /dev/tomato
SheNux@linux:~$
bash: -slice: command not found
SheNux@linux~$[/i]

I want the command to fail on purpose. How's that so far? Any tips on refining the code so it's clearer and more true to general terminal bash? Geekier?

Forgive me if my terminology is a little wrong, I'm still learning! Criticism and tips are much appreciated!

How about

```
mount /dev/knife /home/SheNux/hand
mount /dev/tomato /home/kitchen/counter
/usr/bin/knife -slice /dev/tomato
ERROR: did not specify number of slices
```

:D

EDIT: made a bit better.

---

### Post by darklemming54 on 2007-06-09
> **orange2k said:**
> 
or better yet

sudo apt-get install dial restaurant:-\"


Don't forget

```

sudo apt-get install libphone


```

---

### Post by FuturePilot on 2007-06-09
> **reacocard said:**
> How about

```
mount /dev/knife /home/SheNux/hand
mount /dev/tomato /home/kitchen/counter
/usr/bin/knife -slice /dev/tomato
ERROR: did not specify number of slices
```

:D

EDIT: made a bit better.

Hahaha, that's good.

---

### Post by SheNux on 2007-06-09
LMAO I love geek humour, you've got me crackin' up!

> mount /dev/knife /home/SheNux/hand
mount /dev/tomato /home/kitchen/counter
/usr/bin/knife -slice /dev/tomato
is great!

Now guys I love the idea of installing new skills like cook and dial-restaurant (and libphone to go with!) but I wanted to hopefully stick to the first format I had and keep it simple-ish without a textwall of commands because remember, I want to put it on a sticker or get it tattooed (varied of course, won't be about slicing tomatoes!) on myself, alot like this HTML tatt which I just looove:
[IMG]http://i52.photobucket.com/albums/g32/StaticRaisins/htmlback.jpg[/IMG]

I love your ideas and improvements, keep them coming! :D

---

### Post by jgrabham on 2007-06-09
sudo apt-get a life

:]

---

### Post by reacocard on 2007-06-09
> **jgrabham said:**
> sudo apt-get a life

:]

```
sudo apt-get install a-life
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package a-life
```

Can I file a request for this to be included in gutsy? I think a lot of people would benefit.

---

### Post by FuturePilot on 2007-06-09
> **reacocard said:**
> ```
sudo apt-get install a-life
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package a-life
```

Can I file a request for this to be included in gutsy? I think a lot of people would benefit.
Lol you crack me up:lolflag:

Well you could always build it from source
```
cd /a-life
./configure
sudo make
sudo checkinstall
```

But make sure you have the dependency liba-life
You might also need the life-dev package

---

### Post by reacocard on 2007-06-09
> **FuturePilot said:**
> But make sure you have the dependency liba-life

But that depends on libgirlfriend, libjob, and libsocial, which aren't in the repos either. :sad:

EDIT: It also conflicts with libgeek, which a lot of other stuff depends on.

---

### Post by FuturePilot on 2007-06-09
It seems like a lot of libs conflict with libgeek:(

---

### Post by red_five on 2007-06-10
I like the general idea, but I'd do it slightly differently.

```

sudo aptitude install ginsu-blade
mount /dev/cutting-board /kitchen/counter/space1 -o type=plastic
mount /dev/salad-bowl /kitchen/counter/space2 -o type=wooden
touch /kitchen/counter/cutting-board/tomato
ginsu-blade --size=4 --units=inch --slices=8 --type=wedges --input=/kitchen/counter/cutting-board/tomato --output=/kitchen/counter/salad-bowl
ginsu-blade --wash --location=kitchen-sink --stow-when-dry

```

And, of course, if you swing KDE, you can install kinsu-blade!

---

### Post by retrow on 2007-12-01
> **reacocard said:**
> But that depends on libgirlfriend, libjob, and libsocial, which aren't in the repos either. :sad:

Bite the bullet and try:

```
sudo alien -d -c girlfriend.rpm
```

As for libjob and libsocial, you need to modify the girlfriend source file

```


# [COLOR="Blue"]include[/COLOR]<omp.h>
#[COLOR="Blue"] include[/COLOR]<job.h>
# [COLOR="Blue"]include[/COLOR]<social.h>

main()
{
[COLOR="Red"]double[/COLOR] friends, beers, wine, sports, movies;

...
```

gcc -Wall -o girlfirend girlfriend.c -lm -fopenmp

P.S.: On second thought screw the -lm switch
:guitar:

---

### Post by Nekiruhs on 2007-12-01
> **FuturePilot said:**
> It seems like a lot of libs conflict with libgeek:( Lets see:
lib-life
lib-job
lib-social
lib-girlfriend
lib-rich
lib-success
lib-house
lib-windows

Maybe we should file a bug report and tell the MOTUs.

---

