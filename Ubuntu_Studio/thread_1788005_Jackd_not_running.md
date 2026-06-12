---
title: "Jackd not running"
date: 2011-06-21
forum: Ubuntu Studio
---

### Post by tpearso22 on 2011-06-21
I can't use several of my programs because jackd isn't running although it is installed. And I assume that's also why neither ardour or audacity will pick up on any input. Help would be greatly appreciated.

---

### Post by Pablo_F on 2011-06-22
Hi, 

Please, (try to) start jackd via Jack Control and paste here the content of the message window.

Also, tell us the terminal output of 

arecord -l && aplay -l

Cheers, Pablo

---

### Post by tpearso22 on 2011-06-23
[attach]195841[/attach]

---

### Post by tpearso22 on 2011-06-23
I get no input from the recording jack on my sound card. When I run rakarrack it asks is jackd running? I'm just assuming they're related but this same version of studio runs perfectly fine in vmware and I have no problems with jackd. I've already replaced the sound card and wasn't the problem.

---

### Post by Pablo_F on 2011-06-24
Hi, 

Please, press the start button and, once jack is started, press the Message button, and paste here the contents of that window. Of course, also if jack fails to start, paste the messages.

Then, open a terminal [Control-Alt-T] and paste the output of the command I told you.

Then we will see. 

Cheers, Pablo

---

### Post by tpearso22 on 2011-06-26
Sorry that took so long ive been busy.

---

### Post by Pablo_F on 2011-06-27
Hi, 

Don't use gedit.

In Jack Control there are a Start button and a Messages button.  We need the contents of the Messages window. On the other hand, *arecord -l && aplay -l* has lowercase l, not uppercase I. 

You don't need to take screenshots. Just copy-paste text.

---

### Post by tpearso22 on 2011-07-04
Ok I have no clue what you're talking about everytime I open jack control it opens g edit. And when I ran that command with lowercase is it didn't work so I did uppercase and that screenshot was the result.

---

### Post by Pablo_F on 2011-07-05
Hi, 

Are you opennig qjackctl (aka Jack Control) from the Sound and Video applications menu? Or from the command line: *qjackctl*

As for the other question, it is lowercase L, not uppercase i
You can always copy-paste.

Cheers, Pablo

---

### Post by tpearso22 on 2011-07-10
I was using the search I wasn't aware that those were the same I'm a linux newb I'm not going to lie. But the messages say:

cannot connect to server socket err=1 
cannot connect to server socket
jack server is not running or cannot be detected

---

### Post by Pablo_F on 2011-07-10
Hi, 

I am willing to help you but it is very difficult through the forums. You need interactive help. I suggest you join the #ubuntustudio support chat at freenode.net. You can jump in this channel through the web browser at:

[http://webchat.freenode.net/?channels=ubuntustudio](http://webchat.freenode.net/?channels=ubuntustudio)

Good luck! Pablo

---

