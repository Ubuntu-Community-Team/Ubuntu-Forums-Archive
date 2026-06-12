---
title: "i am bored :)"
date: 2009-03-27
forum: The Cafe
---

### Post by cmay on 2009-03-27
hi.
i am very bored and i want to write a small c program that should be run from the terminal as i complete newbie only knows how to do this. problem is that in the chain of tools already present on a moderen linux system it is almost impossible to think of a program to start write that is not already there or could be done using two lines of bash scripting. 

the whole idea of using the pipelines and use the already existing programs is great but i get an headache from trying to figure a program out to write that actually would not either just reinvent the wheel or be a complete waste of time. 

i need inspiration please. give me some ideas for something useful to do with my time that i also could learn to program from doing.  can anyone find some program that is not there already and would be useful and simple enough to write so that newbie like me can handle it. 

thanks

---

### Post by koenn on 2009-03-27
can't think of any new programs, but what about trying to rewrite an existing one, and when it's done, compare it to the original. 

maybe a simple one, like 'cat' ? 


More interesting : an echo server: a daemon that listens on a given port and returns (echoes back) whatever text you send it. Great for testing connectivity through firewalls

Or, more of a challenge, fix the main bug in the telnet program : (according to man telnet) 
```
BUGS
     The source code is not comprehensible.

```

maybe start simple : a program that can talk to port 23. Then work out the details of telnetting and add options.

:)

---

### Post by cmay on 2009-03-27
already done cat ,grep, wc ,move, and less inspired  from textbooks about c programming and unix. i call my cat version dog however and i added a option so it filers all the non visibile characters and print them as hex instead and i still have the first working version on a  file somewhere. to be honest i stole and improved some of the textbookexamples so its not all the programs i initialy wrote myself. 

a deamon i never tried and i am sure its not that simple. however if a small program (hello world deamon ) could turn out to become useful even very simple then i could be tempted to try. i still fear its too complex maybe. i have little understanding of deamons as is. 

i was thinking about writing a version of rm that does not remove files wiht out a confimation from the user for every file that is to be removed. but i am not sure if the options rm -i will prevent rm from removing stuff it should not. 

its funny how little i usse the terminal when considering the last months i being using it everyday to learn c programming and i still at the console application learning stage. 

thanks for the input ,any other ideas. :)

---

### Post by koenn on 2009-03-27
have a go at the echo server, then.
The only 'special' part is that you need to know how read from and write to a socket, which is pretty similar to reading from and writing to a file (follows the unix 'everything is a file' paradigm).

make it two-ways and you have a rudimentary chat program.

Once you can do that, any other network-capable program is just a matter of implementing protocol (if you receive 'foo', do bar and send 'baz'), and you could, theoretically, write a console web browser, ftp client, or a game ....

---

### Post by cmay on 2009-03-27
that sounds pretty interesting. i am going to ask google for more information on how to do this and i wil try to make the echo server. if the only tricky part is the socket i think i can be as lucky as getting some working bits of examples i can work on. 

i could also imagine writing a small console browser in fact  since i have been working with parsing html tags as the last exercises so to go from just parsing html tags to somehow be able to show a web page would be pretty neat trick to do sometime. a chat program could be just as useful for my brothers home page so i could maybe really benefit from learning this. maybe  i should take it one step at the time and lets see if google returns me any good informations for a small echo server proram. 

thanks.

---

### Post by dragos240 on 2009-03-27
not related: [http://www.i-am-bored.com/](http://www.i-am-bored.com/)

---

### Post by koenn on 2009-03-27
since you want an example : here's one: 
[http://users.telenet.be/mydotcom/program/c/echosrv.htm](http://users.telenet.be/mydotcom/program/c/echosrv.htm)

it's enough for echo and probably chat.
for a real daemon, you'll also have to look at fork(), to let your program 'fork' itself, i.e. start a new process of itself, so that it can handle a session in one process, while listening for new connections in another. 

for you're 'web browser', I imagine it could be as simple as building proper GET statements and send them out, and parse the file you get in return. It might be more complicated than that (I don't know), if the web server expects some preliminary talk first. You'll may have to check the rfc on http for details.

But I don't want to discourage you, just take it 1 step at the time, and have fun.

---

### Post by cmay on 2009-03-27
thanks for the example. i found a long unix socket tutorial but it would take me at least four or five days to read i think. it wil be fun to try make something out of this. i been searchin on unix scoket tutorials and lots comes up. i am not sure i can write a complete webbrowser as it is maybe a bit more comlicated than just parsing some html tags. 

i am very happy with this link you gave me as i can probely spend some time on this. i bookmarkede it for study over a cup of coffe i am about to be making now:)
thanks for the time to do this.

---

### Post by koenn on 2009-03-28
> **cmay said:**
> 
i am very happy with this link you gave me 

thanks for the time to do this.
no problem. It's just stuff I happen to have lying around from taking notes while studying,  so if it can be put to good use again, so much the better :)

---

### Post by ice60 on 2009-03-28
> **cmay said:**
> i call my cat version dog however and i added a option so it filers all the non visibile characters and print them as hex instead and i still have the first working version on a  file somewhere. to be honest i stole and improved some of the textbookexamples so its not all the programs i initialy wrote myself.
i've seen dog on the internet somewhere, the one i saw looked pretty good, with added features too. which book are you working from?

---

### Post by cmay on 2009-03-28
> **ice60 said:**
> i've seen dog on the internet somewhere, the one i saw looked pretty good, with added features too. which book are you working from?

i am learning  from  brians w kernighans books the unix programming environment and the c programming language and just started on begining linux programming 4 edition so what i learn as i go along is mostly these types of small example programs of already existing programs filtres and how they interact . 

the unix programming invironment is a old book so its still pre ansi code examples which means as i learn to code i have to update the code and modifie it so its  following the new standards and as i read more than one book togheter i combine many of the things i learn in the procces of rewriting the example program.  

my dog was a cat examle program that i added both features to and made differnet options for using getopt and actually as i always had done the cat command on c sources i wanted to check for errors from terminal and i forget to add the .c extention and cat prints the progam instead i started to use dog for this purpose.  this way the terminal does not print garbage when i forget to add .c extenstions to files i just want a quick look at without opening a textedtior. 

i started to write on the echo server by the way. i am for a start just going to modifie the example i was giving and add getopt then when i know a bit more about what is happening i will try work on it some more.

---

### Post by ice60 on 2009-04-11
> **cmay said:**
> i am learning  from  brians w kernighans books the unix programming environment and the c programming language and just started on begining linux programming 4 edition so what i learn as i go along is mostly these types of small example programs of already existing programs filtres and how they interact . 

the unix programming invironment is a old book so its still pre ansi code examples which means as i learn to code i have to update the code and modifie it so its  following the new standards and as i read more than one book togheter i combine many of the things i learn in the procces of rewriting the example program.  

my dog was a cat examle program that i added both features to and made differnet options for using getopt and actually as i always had done the cat command on c sources i wanted to check for errors from terminal and i forget to add the .c extention and cat prints the progam instead i started to use dog for this purpose.  this way the terminal does not print garbage when i forget to add .c extenstions to files i just want a quick look at without opening a textedtior. 

i started to write on the echo server by the way. i am for a start just going to modifie the example i was giving and add getopt then when i know a bit more about what is happening i will try work on it some more.
i did see your reply, i don't know why i didn't say anything? 

anyway, good stuff. i'm really lazy and impatient when it comes to programming, i think if i ever want to become good i'll have to do a course. although the last computer course i did was a bit of a disaster lol.

---

