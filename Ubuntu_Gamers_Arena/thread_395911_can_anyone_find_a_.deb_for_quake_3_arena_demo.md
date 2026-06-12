---
title: "can anyone find a .deb for quake 3 arena demo"
date: 2007-03-28
forum: Ubuntu Gamers Arena
---

### Post by Dot Communist on 2007-03-28
it gives me some weird file from there website with what i dont know what do do with

---

### Post by hikaricore on 2007-03-29
Is the quake3 demo called quake3.bin or quake.sh, something like that?

What you need to do is open a terminal and change to the directory you have the file in:

If the file is on your desktop, you would do:

```
cd ~/Desktop
```

Then you'll need to chmod the file +x to allow it to be run:

```
chmod +x FileNameGoesHere
```

Then you'll be able to run the installer like so:

```
sudo ./FileNameGoesHere
```

Obviously you replace FileNameGoesHere with the name of the actual installer file.

---

### Post by Perfect Storm on 2007-03-29
> **Dot Communist said:**
> it gives me some weird file from there website with what i dont know what do do with

Do as hikaricore says.
It's very rarely that you'll find commercial/non-gpl .deb package. Usually they use scripts instead.

---

### Post by Dot Communist on 2007-03-29
it does some stuff then gives me this

konsole: ERROR: can not execute ././linuxq3ademo-1.11-6.x86.gz.sh

btw i dont use KDE or console :/

---

### Post by hikaricore on 2007-03-29
hmm that's odd, I'm not sure why it won't run the install script

try:

```
sudo -s
```

then after you login to the sudo console

```
./linuxq3ademo-1.11-6.x86.gz.sh
```

This assumes you are in the same directory as the installer file, which I have no doubt that you are.

---

### Post by Dot Communist on 2007-03-31
> **hikaricore said:**
> hmm that's odd, I'm not sure why it won't run the install script

try:

```
sudo -s
```

then after you login to the sudo console

```
./linuxq3ademo-1.11-6.x86.gz.sh
```

This assumes you are in the same directory as the installer file, which I have no doubt that you are.
same thing happens :confused:

---

### Post by Majorix on 2007-03-31
try typing only

```
linuxq3*.sh
```

---

### Post by Jarn on 2007-04-02
Doesn't the .gz mean it's gzipped? Maybe that's the problem...?

---

### Post by airtonix on 2007-04-16
how big is the file?

what does it look like ina text editor?

me thinks this "script" that commercial peeps use is supposed to ungzip it maybe?

or maybe it assumes its in an enviroment where gzip decompression is native(as in upon access)

---

### Post by fakie_flip on 2007-04-19
Why not get Open Arena instead? It plays very good without the sound problems, and it is open source.

---

### Post by sanone on 2007-04-20
> **fakie_flip said:**
> Why not get Open Arena instead? It plays very good without the sound problems, and it is open source.

And it is ugly as hell.. and nobody plays it :)

---

### Post by Perfect Storm on 2007-04-20
Could be something about it, well not many at least, poll we made on UGA; [http://gaming.gwos.org/e107_plugins/poll/oldpolls.php?1](http://gaming.gwos.org/e107_plugins/poll/oldpolls.php?1)

---

### Post by hikaricore on 2007-04-21
> **sanone said:**
> And it is ugly as hell.. and nobody plays it :)

Maybe you havn't seen the most recent release of Open Arena... because it's beautiful.

And I play it.

---

### Post by crane on 2007-04-22
Yea I just recently took a look at it as well. I wouldn't mess with the Q3 Demo. You may have a hard time finding the game if you choose to buy.
 I would suggest [Warsow]("http://www.warsow.net/"), [Open Arena]("http://openarena.ws"), or a few of the others. Quake3 is fun, but you may have sound issues as well as it being a limited demo.

---

### Post by fakie_flip on 2007-04-23
> **crane said:**
> Yea I just recently took a look at it as well. I wouldn't mess with the Q3 Demo. You may have a hard time finding the game if you choose to buy.
 I would suggest [Warsow]("http://www.warsow.net/"), [Open Arena]("http://openarena.ws"), or a few of the others. Quake3 is fun, but you may have sound issues as well as it being a limited demo.

I agree. Sauerbraten is also a good free fps game. I love playing with instagib. There's also WoP and Alien Arena 2007.

---

### Post by leilei on 2007-04-23
> **crane said:**
>  You may have a hard time finding the game if you choose to buy.

Quake3 is still very available, including trilogy bundled forms with the other two quakes.

---

