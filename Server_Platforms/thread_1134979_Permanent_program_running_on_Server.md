---
title: "Permanent program running on Server?"
date: 2009-04-24
forum: Server Platforms
---

### Post by Terminator0506 on 2009-04-24
Hey, I've got a vServer with Ubuntu 32bit.
Now I want to run a program on this server.
I tried to use "nohup" in putty. It ran perfectly but as I turned off my PC, it killed the process.

I want it to run 24h a day... Can you help me please?


Sorry if my english isn't as nice as yours, I'm a 15year old student from Germany! :D

---

### Post by jimv on 2009-04-24
When you start the program, type it like this to run it in the background:

nohup &

You should be able to see it running by typing "ps -a"

---

### Post by BkkBonanza on 2009-04-24
Note, you can't just run nohup &
You need to run,
nohup someprogram &
The nohup is supposed to stop it being sent a terminate signal when the shell exits.

Another probably more flexible way to do this is to use screen.
Type, **man screen** to learn more about this. With screen it's easy to detach the program and later re-attach it.

---

### Post by jimv on 2009-04-24
> **BkkBonaza said:**
> Note, you can't just run nohup &
You need to run,
nohup someprogram &
The nohup is supposed to stop it being sent a terminate signal when the shell exits.

Another probably more flexible way to do this is to use screen.
Type, **man screen** to learn more about this. With screen it's easy to detach the program and later re-attach it.

I thought nohup was a program :D

---

### Post by Terminator0506 on 2009-04-24
First thanks for your answers...
I want to do it as easy as possible. So the program is in directory /root/ and is called PennerBot32 ...

So I have to type **nohup /root/PennerBot32 &**, right?

Yesterday I typed in PuTTY: **nohup /root/PennerBot32** - it ran perfectly but just until I turned off my computer...

Is the & important? Or can somebody now give me another possibility to run it 24h a day?
If possible immediately the whole code? (:

Greets


Edit: What's that? I turned on my computer and the program is running now?! In the morning today as my computer was turned off, the program wasn't running, I saw it in school... Wtf?!

---

### Post by BkkBonanza on 2009-04-24
Programs have a nasty habit of not running when the power's off... not sure what we can do about that.

The & makes the program start and run in the background so that you can continue with other stuff in the foreground. IF you want it to start and run whenever you power up then that's a whole different thing.

---

### Post by Terminator0506 on 2009-04-24
> **BkkBonaza said:**
> Programs have a nasty habit of not running when the power's off... not sure what we can do about that.

I've got a vServer. It's power is on, I just turn off my Computer... And the program turns off when I turn off my own Computer, not the Server...

---

### Post by BkkBonanza on 2009-04-24
Ok. It's a bit more clear what you're meaning now. Turning off your computer isn't meaning turning off the server - so you have two computers.

When you login with ssh (terminal) any programs which are attached to the shell will be terminated when the shell terminates. There are a number of ways around this and according to the manual nohup is supposed to prevent that. But I never use nohup and don't have expereince with what it does or not.

I can tell you that I have used screen and it does work the way you want. So you could backup and read the screen manual to help you understand how to use it.

Briefly, you start the program by typing,
**screen /root/PennerBot32 **
Then you type **ctrl-a** then **d** and it will detach from the console and run independently. You can re-attach later (even after exiting your terminal and coming back) by typing **screen -r**. It will come back to the foreground. You can detach and re-attach any number of times as you wish.

But this will not restart your program if the server reboots or power cycles. If you want your program to start at boot then the simplest way is to add a line to **/etc/rc.local** which starts the program by root during the boot sequence. If you want to get fancy you can add it as a script in /etc/event.d which allows you to use **respawn** to cause it to be restarted any time it gets killed for some reason.

---

