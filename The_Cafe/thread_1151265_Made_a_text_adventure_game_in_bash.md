---
title: "Made a text adventure game in bash"
date: 2009-05-06
forum: The Cafe
---

### Post by thegreenblob on 2009-05-06
Anyone want to play it? lol

I made it pretty much because I was bored and wanted to know if I would do it. It's not that great but I'm proud of it. :P

Here it is: [http://ounderscoreo.com/stuff/CFMC.tar.gz](http://ounderscoreo.com/stuff/CFMC.tar.gz)

The readme explains how to run it. :)

Comments/Questions welcome. lol (Oh and the story associated with it is completely cheesy :P)

---

### Post by benj1 on 2009-05-06
cool. nice cow  :P

theres /tmp for temporary files like bedroom.txt.

---

### Post by thegreenblob on 2009-05-06
> **benj1 said:**
> cool. nice cow  :P

theres /tmp for temporary files like bedroom.txt.

lol thanks. I used the cow from apt-get moo :P

And I knew of /tmp but didn't think to use it. lol. I think I'll change it now.

EDIT: It uses /tmp now.

---

### Post by -grubby on 2009-05-06
```

You try fighting the cow the best you can, you try punching and kicking,
but all of that seems useless. The cow eventually knocks you down and
tramples you to death.

The cow is victorious.

         (__)
         (oo)
   /------\/
  / |    ||
 *  /\---/\
    ~~   ~~

Game Over!

```

:(

EDIT:
```

You reach for the cup cake and then eat it.

You start to feel really faint and then pass out.

You are dead. Turns out the cup cake was poisoned.

Game Over!

```

:(

EDIT:

```

You dodged it just in time.

You disarm him and then call the police. He get arrested. You go home safely.

You win! Congrats!

```

:)

---

### Post by Dr Small on 2009-05-06
> **thegreenblob said:**
> Anyone want to play it? lol

I made it pretty much because I was bored and wanted to know if I would do it. It's not that great but I'm proud of it. :P

Here it is: [http://ounderscoreo.com/stuff/CFMC.tar.gz](http://ounderscoreo.com/stuff/CFMC.tar.gz)

The readme explains how to run it. :)

Comments/Questions welcome. lol (Oh and the story associated with it is completely cheesy :P)
awesome game man! I ought to make a detective game like that, lol

---

### Post by dragos240 on 2009-05-06
Heh.... Bob hired you to find a murderer.... he didn't think it was suicide ..... and you find out that bob was the murderer after all.... why not just accept that it was suicide.

---

### Post by thegreenblob on 2009-05-06
> **dragos240 said:**
> Heh.... Bob hired you to find a murderer.... he didn't think it was suicide ..... and you find out that bob was the murderer after all.... why not just accept that it was suicide.

Not a very logical murderer is he? :P lol

---

### Post by dragos240 on 2009-05-06
No he isn't heh...

EDIT: What a lonely cow, you try to leave he runs after you, as if saying "COME BAK!!!! NAO!!!"

---

### Post by PacSci on 2009-05-06
Very funny, but it's got a few technical glitches. It might be better in Python or Ruby. Nice time-killer, though.

---

### Post by thegreenblob on 2009-05-06
> EDIT: What a lonely cow, you try to leave he runs after you, as if saying "COME BAK!!!! NAO!!!"

Cows live such a sad life :(

> Very funny, but it's got a few technical glitches. It might be better in Python or Ruby. Nice time-killer, though.

lol thanks. Yeah probably would be better in python or ruby but I don't know either of them. I actually plan/want to learn python though. Eventually... I procrastinate too much >.>

---

### Post by Dr Small on 2009-05-06
I'm actually writing one now that involves dialog :)

---

### Post by MaxIBoy on 2009-05-06
I think I found a bug. The text I typed is in **bold** for clarity.
```
You have a short conversation in the car on the way to the scene of
the crime with Bob to get more details that goes something like this.

You: So, what did the police say about your brothers death?
Bob: They said it looked like suicide and called it a day. But I don't buy it.
You: Where was the body found and why don't you think it was suicide?
Bob: It was found in the barn hanging from a piece of rope.
Bob: And he just doesn't seem like the type to do that.
You: I see.
Bob: Well here we are. Here's the key to the front door. I have
a business trip so I have to go I hope you don't mind looking around
by your self.

You think it's strange that he would just drop you off but
you just shrugged it off and forgot about it.

Press enter to continue... **y**
Answer: **wat**
~/hacks/other_people/CFMC$
```If you type "y" there, it'll prompt you for an answer, and when you hit enter, it'll exit.

You should handle actual input gracefully, even if it's not needed.

---

### Post by saulgoode on 2009-05-07
> **dragos240 said:**
> Heh.... Bob hired you to find a murderer.... he didn't think it was suicide ..... and you find out that bob was the murderer after all.... why not just accept that it was suicide.
The life insurance policy did not cover suicidal death.

---

### Post by calvinps on 2009-05-07
> **thegreenblob said:**
> lol thanks. I used the cow from **apt-get moo** :P

And I knew of /tmp but didn't think to use it. lol. I think I'll change it now.

EDIT: It uses /tmp now.

Does apt-get moo show a text cow on your terminal window?? :P :lol: :mrgreen:

---

### Post by benj1 on 2009-05-07
> **calvinps said:**
> Does apt-get moo show a text cow on your terminal window?? :P :lol: :mrgreen:

try it :)

theres one for aptitude, can't remember what it is tho.

if you use alt-f2 the type 'gegls from outer space' you get more cows

---

### Post by jelle_ on 2009-05-07
aptitude -v moo
aptitude -vv moo
....
aptitude -vvvvvv moo

---

### Post by MaxIBoy on 2009-05-07
Apt-get moo simply runs an external program, "cowsay," which is installed on every Linux distro as far as I know. 

By the way, that text game is fun, I enjoyed going through all the possibilities.

---

### Post by thegreenblob on 2009-05-07
> **Dr Small said:**
> I'm actually writing one now that involves dialog :)

What language are you writing it in? :)

> **MaxIBoy said:**
> I think I found a bug. The text I typed is in **bold** for clarity.
```
You have a short ...
```If you type "y" there, it'll prompt you for an answer, and when you hit enter, it'll exit.

You should handle actual input gracefully, even if it's not needed.

I didn't really think of that. :P I'll see what I can do about that later.

> **calvinps said:**
> Does apt-get moo show a text cow on your terminal window?? :P :lol: :mrgreen:

Yes it does. :popcorn:

> **MaxIBoy said:**
> Apt-get moo simply runs an external program, "cowsay," which is installed on every Linux distro as far as I know. 

By the way, that text game is fun, I enjoyed going through all the possibilities.

Thanks. :)

---

### Post by calrogman on 2009-05-07
I think it would be easier to handle unexpected input using
```
case $foobar in
  foo)
    echo foo
    ;;
  bar)
    echo bar
    ;;
  *)
    echo wait what?
    ;;
esac
```
constructs.

---

### Post by BazookaAce on 2009-05-07
[B]You ****** ** just in time.

You ****** *** and then call *** ******. He get *******. You go home safely.

You win! Congrats![/B]

Yey! I did it :P Took me about 7 mins! Btw, the * is for not spoiling the end for people that haven't played yet :)

So far, i enjoyed it!

---

### Post by calrogman on 2009-05-07
> **BazookaAce said:**
> [B]You ****** ** just in time.

You ****** *** and then call *** ******. He get *******. You go home safely.

You win! Congrats![/B]

Yey! I did it :P Took me about 7 mins! Btw, the * is for not spoiling the end for people that haven't played yet :)

So far, i enjoyed it!

I made it on my second try.  Actually quite easy.

---

### Post by pwnst*r on 2009-05-07
i'll have to try that tonight, awesome!  i am a big fan of the old school text adventures like planetfall and the Zork series and even made my own back in the day, lulz.

---

### Post by dragos240 on 2009-05-07
> **calrogman said:**
> I made it on my second try.  Actually quite easy.

I did it in 2 minutes, 1st try.

---

### Post by calrogman on 2009-05-07
I got shot.  Camping near a murder scene was far too tempting.


:(

---

### Post by hatten on 2009-05-07
> **MaxIBoy said:**
> Apt-get moo simply runs an external program, "cowsay," which is installed on every Linux distro as far as I know. 

By the way, that text game is fun, I enjoyed going through all the possibilities.
not on arch by default:
```
&#9556;&#9552;[hatten@tukumon]&#9552;[22:19:47 Thu May 07]&#9552;[~]
&#9562;&#9552;&#9552;&#9552;[$]> cowsay test
bash: cowsay: command not found
```


great game :D

---

### Post by MaxIBoy on 2009-05-07
> **hatten said:**
> not on arch by default:
```
&#9556;&#9552;[hatten@tukumon]&#9552;[22:19:47 Thu May 07]&#9552;[~]
&#9562;&#9552;&#9552;&#9552;[$]> cowsay test
bash: cowsay: command not found
```
great game :DNot sure if Arch counts... I don't think anything is installed on Arch by default.

---

### Post by BazookaAce on 2009-05-07
Cowsay wasn't installed on my 9.04 install be default. I installed it now.

---

### Post by hatten on 2009-05-07
> **MaxIBoy said:**
> Not sure if Arch counts... I don't think anything is installed on Arch by default.
hahahaha, awesome quote :P

Well, it depends on how you see it, you can pretty much uncheck anything from being installed, but im not sure you can uncheck the kernel :P (gotta check that later)

---

### Post by Dr Small on 2009-05-13
I finally finished my text-based adventure game. Try it out and tell me what you think, or how many times you played it before you reached the end =D

Dr Small

---

### Post by benj1 on 2009-05-14
pretty good,nice story line, took me quite a few gos to finish it.

note to others you need to install 'dialog' from the repos.

---

### Post by lisati on 2009-05-14
Eeek! I just went looking for a text-based adventure program to suggest for someone to adapt to Ubuntu and discovered that [www.winsite.com](www.winsite.com) seems to have had the plug pulled! Found what I was looking for elsewhere, and attached it to this post.

---

### Post by thegreenblob on 2009-05-17
> **Dr Small said:**
> I finally finished my text-based adventure game. Try it out and tell me what you think, or how many times you played it before you reached the end =D

Dr Small

Nice. :)

I played about 5-7 times but keep getting a game over :P

*keeps trying*

Edit: Yay, finished it. lol.

---

