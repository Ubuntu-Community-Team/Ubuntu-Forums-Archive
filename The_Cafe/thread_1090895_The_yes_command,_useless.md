---
title: "The yes command, useless?"
date: 2009-03-08
forum: The Cafe
---

### Post by dragos240 on 2009-03-08
Okay, i was just looking through my /usr/bin and found the yes command, it's pretty funny, but looks pretty useless.... It just outputs y forever. Why was this created?

---

### Post by gletob on 2009-03-08
someone should make a no command!

---

### Post by uknowho008 on 2009-03-08
my guess is that if your running a bunch of commands that you know you want run and you dont want to keep pressing y. just have the yes command do it for you??

---

### Post by dragos240 on 2009-03-08
> **gletob said:**
> someone should make a no command!

agreed.

---

### Post by RichardLinx on 2009-03-08
You know when your installing new software and you have to keep answering questions y/n? ;) I assume that's what it could be used for anyway. Though I've never installed software where I had to say "y" (yes) more then about twice.

---

### Post by linuxisevolution on 2009-03-08
I created an alias with bash that tells my computer to shut down if I type Die in terminal:

```
 $> die
The system is going down for maintenance NOW! 
```

Oh, and type sudo apt-get moo , and then type "yes actually I have"

And you will find the reason :D

---

### Post by yabbadabbadont on 2009-03-08
> **gletob said:**
> someone should make a no command!

```
yes n
```

;)

---

### Post by init1 on 2009-03-08
It was for automatically affirming (y/n) prompts

---

### Post by Dougie187 on 2009-03-08
Very useful.

Imagine your program test requires a lot of user input for yes/no questions. So you do this.

```
 yes | ./test 
```

And now you don't have to answer any of the questions.

---

### Post by k2t0f12d on 2009-03-08
The yes command outputs any specified string to stdin.  By default the string output is "y" and "y" will be output if no other string is specified.  To output any other string specify it after the yes command, i.e.```
$ yes <string>
```

---

### Post by cariboo on 2009-03-08
I'm surprised no one suggested looking at:

```
man yes
```

> yes - output a string repeatedly until killed

Jim

---

### Post by zmjjmz on 2009-03-08
It's also great for making sexual innuendos in bash.

---

### Post by CJ Master on 2009-03-08
> The yes command, useless?

Yes

---

### Post by MaxIBoy on 2009-03-08
Warning, this is an **extremely irritating fork bomb**. It's harmless, but it will produce extreme slowness that will get worse and worse until the program is killed. (The command to stop it is "killall bash.")

You'll probably have to save it to a shell script file and run it, because it's two lines.
```
b=\' c=\\ a='yes $( echo b=$c$b c=$c$c a=$b$a$b; echo $a ) | bash &'
yes $( echo b=$c$b c=$c$c a=$b$a$b; echo $a ) | bash &
```Adapted from a BASH quine I found here: [http://c2.com/cgi/wiki?QuineProgram](http://c2.com/cgi/wiki?QuineProgram)

---

### Post by Dr Small on 2009-03-08
Piping yes into fsck saved me a lot (and I mean, a lot) of keypresses one time ...

---

### Post by MaxIBoy on 2009-03-08
If I'd known about "yes" that one time I was restoring from a backup with some scratched CDs, I wouldn't have had to leave some heavy weights on my "enter" key. :D

---

### Post by Dr Small on 2009-03-08
> **MaxIBoy said:**
> If I'd known about "yes" that one time I was restoring from a backup with some scratched CDs, I wouldn't have had to leave some heavy weights on my "enter" key. :D
I never considered doing that, lol :D

---

### Post by yabbadabbadont on 2009-03-08
> **Dr Small said:**
> I never considered doing that, lol :D

Many people just wedge it down with a paper clip.

---

### Post by MaxIBoy on 2009-03-08
I stacked two dimes on the key, then I put a quarter on the dime, then I balanced a small dish on the quarter, then I put my cell phone in the dish.

It worked, too.

Then the program didn't need my input anymore, and the enter key started making it beep. :D

---

### Post by Dr Small on 2009-03-08
> **yabbadabbadont said:**
> Many people just wedge it down with a paper clip.
I have a huge ball bearing (which I use for a paperweight/desk ornament) on my desk, and it sits quite fine on my Return key. I shoulda thought of that and saved my finger, hand and key :)

---

### Post by MikeTheC on 2009-03-08
> **gletob said:**
> someone should make a no command!

[img]http://4.bp.blogspot.com/_9iMIweN5ntc/SW5W04ZYjwI/AAAAAAAAAM4/J_jQlvp8Ukk/s400/Yes+Bit+Recolor.jpg[/img]
[font=arial]*Yes!!!*[/font]

---

### Post by MaxIBoy on 2009-03-08
[img]http://design.osu.edu/carlson/history/images/tron-images/bitno.jpg[/img]

Nononononononononononononononononononono...

---

