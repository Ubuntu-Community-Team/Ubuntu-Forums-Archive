---
title: "cpu stress testing with pi"
date: 2009-12-26
forum: The Cafe
---

### Post by mr clark25 on 2009-12-26
to start, i want to know if there is a way to compare the output of 2 commands, and do something if the two outputs are different. (like stop or bring up a warning) i also need it to work with the "watch" command.

this is a summary of what i have come up with so far:
the program "pi" works great for this. (command: sudo apt-get install pi)
and this command works great for stressing a cpu: watch -n.1 pi 2000000
the only catch is that you must run this command several times, all in separate terminals, all at the same time. (one for each thread your cpu has) i recommend that you run two for each thread because cpu usage will drop to about 90% every so often if you don't. 

you may need to increase the number after "pi" if you have a faster cpu. i just used 2000000 as an example. i have a processor with 2 threads, and, if i run this in 4 terminals at once, it works just as good as prime95. (makes my cpu get just as hot)

so, for now, i need to know if there is a command (or a way to) that compares the output of two commands, and alert me if the two outputs are different.

i will post back later with more.

---

### Post by mr clark25 on 2009-12-26
i was trying to get super pi to work on a computer to see how it compares to other computers. but, i kept getting an error, no matter what i did. so, i started trying to find an alternative.
i then just typed "pi" into a terminal. it said that i needed a program to do that. so, i installed the program. i quickly found out that i can chose how many digits to calculate pi to by typing a number after i type pi. then i went to the forums to try to find out how many digits super pi calculated pi to. turns out that that number is 1048576. so, i then typed this into the terminal: pi 1048576 and timed it myself. i posted to the forums about this and found out about the "time" command. i also figured out that it is much faster than super pi, so the results weren't comparable.

i knew there had to be some use for this. i had the system monitor open on accident when i typed "pi 500000" into a terminal. i noticed that the cpu usage spiked. i knew then that i had found an use for this. i did some experimenting, and came to what i have now.

i got some facts together:
1. this works great for stress testing, but i can only test my cpu for heat output. (the "stress" part of "stress test")
2.i need a way to compare the output of two commands. (the "test" part of "stress test")
3.i cant do this by myself. i don't know enough to finish this.

i think this holds a lot of potential. if i could compare two commands (while running the "watch" command), i could really do something with this.

---

### Post by lisati on 2009-12-26
> **mr clark25 said:**
> reserved

Don't be shy!

---

### Post by MooPi on 2009-12-26
Wouldn't be easier just to use prime 95. It works off known results and if an error logs it stops the test on failure. Good for testing over clocked machines and testing if your going to get dependable results from older equipment.

---

### Post by mr clark25 on 2009-12-26
> **MooPi said:**
> Wouldn't be easier just to use prime 95. It works off known results and if an error logs it stops the test on failure. Good for testing over clocked machines and testing if your going to get dependable results from older equipment.

i really like the idea of the program being native to linux. that is one of the things that got me started on this.

---

### Post by mr clark25 on 2009-12-29
bump...

i dont want this idea to disappear...

---

### Post by MooPi on 2009-12-29
Your problem as I see it , is that there is already a good solution for stress testing and is friendly to Linux. For others to be interested enough to contribute there would need to be a problem or deficiency in this area to generate involvement. This may be your burden to bare the leg work on this. I wish you luck as I haven't a clue how to implement your idea. I find your idea better suited as a benchmark versus stress testing. The time it takes for "pi"to reach conclusion could be compared to differing machines.

---

### Post by happyhamster on 2009-12-29
Comparing output is possible with the "diff" command. Just re-direct the output of pi into files, then use diff on those files. For example:

pi 20000 >a.txt

pi 20000 >b.txt

diff a.txt b.txt

If both files are identical, you'll get no output. All of this could be put into some script to get things running automatically (using bash or python or such language). Don't know anything about any of those though, so can't help you there.

You could try your idea in the programming section of the forums (Development & Programming --> Programming Talk). You might get lucky and get someone interested into writing something.

---

### Post by mr clark25 on 2009-12-31
ok, thanks!

i have gotten started with scripting, so ill try it myself. ill post back here if im successful.

i think that one command is all i needed, so thanks!

---

### Post by 3rdalbum on 2009-12-31
The Phoronix Test Suite has the "cpuburn" benchmark that is designed for stress testing your CPU.

---

### Post by mr clark25 on 2010-01-04
i got done scripting. (i think its bash scripting) unpack the .tar.gz file on your desktop, and execute "run". if you get any output, your cpu isn't stable. there is a file titled "directions". it explains some things, but it may not have enough detail for some.

i would be happy for any more suggestions.

---

