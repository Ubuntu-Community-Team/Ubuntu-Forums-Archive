---
title: "Alphabetical Keyboard"
date: 2013-01-25
forum: The Cafe
---

### Post by docbear on 2013-01-25
I work in China, teaching teachers to teach. One little niggling problem has always been getting younger students to do much with computers. There's plenty of software that could be used, but the niggle is the keyboard. Nearly all the systems here come with a bog-standard 'us' QWERTY keyboard, and use an IM to make Chinese characters... So writing in English (the goal) is not a hardware problem *per se*.

Well, the trouble is it's really a challenge to get children to understand why the 'English' alphabet they have just spent so much time learning is all jumbled up on the keyboard.

My solution was to get a cheap keyboard, prise the letter caps off with a couple of spoons, then re-arrange them in alphabetic order.

The QWERTY keyboard has a PS/2 connector, the ALPHA is USB, so I just leave them both plugged up all the time.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=230604&stc=1&d=1359109969[/IMG]

Then I simply made a couple of launchers on my worstation to choose the desired layout.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=230605&stc=1&d=1359109969[/IMG]

The launchers do this:

Alpha: ```
sudo cp /usr/share/X11/xkb/symbols/alpha /usr/share/X11/xkb/symbols/us
```

QWERTY: ```
sudo cp /usr/share/X11/xkb/symbols/qwerty /usr/share/X11/xkb/symbols/us
```

Have a look at /usr/share/X11/xkb/symbols/us and you can see how I did it. 

On my little Hasee netbook I use for teaching, I did the same swapping around of key caps, but it has the 'us' keyboard just mapped for Alpha.

It works out pretty well.

---

### Post by Sef on 2013-01-25
Moved to the community cafe.

---

### Post by grahammechanical on 2013-01-25
Does this work in the sense that the students learn to type English words at a reasonable speed?

Do you tell them of the problems they will have if they come to Europe, Australia, New Zealand, or USA to study or work?

Regards.

---

### Post by docbear on 2013-01-26
It does get them making words rather quickly. They learn 'keyboard' later on (in high school).

Not sure what the long-term is? Will it interfere with later learning?

Don't know, but it gets them using the early learning software right away.

---

### Post by pqwoerituytrueiwoq on 2013-01-26
probally should tell them the keybord is arranged like that based on most commonly used keys, and give them the option of using the "us" keyboard

---

### Post by Paqman on 2013-01-26
> **docbear said:**
> 
Not sure what the long-term is? Will it interfere with later learning?


They'll have to relearn their muscle-memory later, yes. Since this is inevitable, I would be inclined to just make them do it right from the start. Instead of having to climb the learning curve twice they'll only do it once.

> **pqwoerituytrueiwoq said:**
> probally should tell them the keybord is arranged like that based on most commonly used keys

The QWERTY layout was designed so that the arms of a manual typewriter wouldn't jam. Essentially the most used keys were arranged to be as far apart from each other as possible, not where they were the most comfortable for the user.

Now that we don't use manual typewriters the only reason we use QWERTY is because everybody is used to it. There are alternative key layouts that are supposed to be better, but won't ever see widespread adoption.

---

### Post by Artemis3 on 2013-01-26
Indeed, and the Chinese keyboard also has the western letters arranged in the qwerty fashion, so its better to leave the layout alone...

[img]http://robrohan.com/wp-content/uploads/2007/06/finished.jpg[/img]

The only explanation needed is the truth: "qwerty" was designed to reduce jamming in mechanical typewriter machines, a historical reason.

---

### Post by Gremlinzzz on 2013-01-26
:popcorn: Just tell em in the real world outside your class,the keyboards will have the western letters arranged in the qwerty fashion.

---

### Post by Sef on 2013-01-26
> probally should tell them the keybord is arranged like that based on most commonly used keys

No it is not. The qwerty keyboard is based on slowing you up, so your fingers did not go to fast because in old typewriters the keys could get jammed if you went too fast.

---

### Post by Paqman on 2013-01-27
> **Sef said:**
> No it is not. The qwerty keyboard is based on slowing you up, so your fingers did not go to fast because in old typewriters the keys could get jammed if you went too fast.

Actually it's the opposite; the qwerty arrangement was intended to allow you go as fast as possible on a manual typewriter. 

The idea was that when typing in English the typist was more likely to strike keys from opposite sides of the keyboard alternately, meaning the arms were less likely to clash and interrupt.

---

### Post by Jakin on 2013-01-27
I understand the QWERTY being hard for young children, but if a child gets used to a keyboard such as the OP, it may make it harder to transition to a standard keyboard later on. 
Either way, if you never used a keyboard before, regardless its layout, and regardless your age, you are going to have to learn how to input with it. 
So why do it twice?

---

