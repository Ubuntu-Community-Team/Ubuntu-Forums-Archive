---
title: "How to run application in backrgound"
date: 2009-07-02
forum: Server Platforms
---

### Post by user328 on 2009-07-02
Hey,

I am running HLDS (Half Life Dedicated Server). When I start it this is what i put, ./hlds_run -command cstrike ....
Now that i started it, i want to start the second server. In order to do that i can use ctrl+c, but this is going to exit the application. I need to scroll it down (I guess) and start another one.
How can I do that?
Thanks

---

### Post by Lucky. on 2009-07-02
Shoot!  I know there's some command line argument to fork the process and return to the command prompt...shoot, can't remember what it is though...

---

### Post by Boondoklife on 2009-07-02
try command & =P

or even better if it produces output then do command > /var/log/command.log &

---

### Post by user328 on 2009-07-02
So what command do I use? Sorry, I am new to linux

---

### Post by Boondoklife on 2009-07-02
Um the command is what every you want to run just put the & after it.

---

### Post by user328 on 2009-07-02
Thanks, i figured it out

---

### Post by dlmarti on 2009-07-02
nohup the_command_you_want_to_run &

nohup detaches the command from the terminal, so closing the terminal won't kill the command.

The ampersand pushes the command to background.

nohup also has the added benefit of creating a log (in the current directory) of the programs text output (useful in debugging).

---

### Post by skintythe1andonly on 2009-07-02
You may want to have a look at [screen]("http://www.oreillynet.com/linux/cmd/cmd.csp?path=s/screen"). Its the best way of multitasking at the command line

---

