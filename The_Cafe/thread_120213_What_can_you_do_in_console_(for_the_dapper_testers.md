---
title: "What can you do in console (for the dapper testers)"
date: 2006-01-21
forum: The Cafe
---

### Post by BoyOfDestiny on 2006-01-21
OK first off, not saying X breaks often in dapper (only once for me), it is awesome, and I'm glad to test it (although I'm a bit paranoid about rebooting now)

So the point of this thread... fun/useful things you can do without X, some which might help you restore your system...

Ok, I'm still a bit green, but here are some fun things to try
(remember ctrl alt F1,F2,etc to switch to other virtual consoles)

sudo apt-get update
sudo apt-get dist-upgrade

if that doesn't help you ;)

sudo apt-get install bb links

bb is a cool demo using aalib

links is a text mode browser (press the letter g, and put the addy you want and you'll be on your way, not to mention you can download that dapper daily iso to bail you out)

Now for those with more experience,

perhaps how to burn an iso from commandline

maybe some of your favorite text mode games (i.e. nethack... if someone can tell me how to change the key mapping that would make me happy)

using aalib or libcaca to watch movies in textmode (I had no luck with mplayer in that respect...)
or games in textmode using those libs...

---

### Post by Stormy Eyes on 2006-01-21
I can write bad science fiction in the console using vim. :)

---

### Post by 23meg on 2006-01-21
I often type ```
fortune
```

---

### Post by Adrian on 2006-01-21
```
sudo aptitude install nethack-console

```

Nethack will keep you busy until the fixed X packages arrive :)

---

### Post by majikstreet on 2006-01-21
sudo dpkg-reconfigure xserver-xorg

get familiar with that command.

---

### Post by ssam on 2006-01-21
the bsdgames packages has some little games.

perhaps you could use the time constructively, maybe learn python. just type
```
python
```
to start it, then you can try things like
```
msg = "ubuntu"
print msg
for letter in msg:
    print "give me a", letter

```

---

### Post by kabus on 2006-01-21
Get screen, probably the most useful console app ever.

Here's a nice introduction :

 [http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)

and this guy has some great config examples on his blog :

[http://phraktured.net/blog/gnu-screen/](http://phraktured.net/blog/gnu-screen/)

> 
perhaps how to burn an iso from commandline

cdrecord dev=/dev/hdx foo.iso

---

