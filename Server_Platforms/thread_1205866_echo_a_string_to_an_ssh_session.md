---
title: "echo a string to an ssh session"
date: 2009-07-06
forum: Server Platforms
---

### Post by three_jeeps on 2009-07-06
Hi:
I am running 8.04 server and am trying to send a text string from an application program to a ssh session.  Here are the details:
I am running an application called 'heyu' for home automation (among other things).  The heyu engine, which when running, can execute scripts.  Scripts are of the form: script name, trigger,action. Trigger is the action that causes the specified action to occur.  One of the actions that can happen is: echo "hall light on" which would cause the text in quotes to be written to a log file.  What I would like to have happen is to have any such text messages written to the terminal window of an ssh session (if one is running at the time of the trigger).
So, my questions are:
1. How can I redirect the text output to the ssh session? I have tried redirecting to stdout with no success. I've also tried piping it to 'more' (which sends output to stdout) with no success.
2.  If I have multiple ssh sessions open, how can I specify what to what session the text should go to?
3. As I understand it, the scripting language has full knowledge of the bash environment, so I can directly access aliases.

Any help/suggestions/pointers is appreciated....
Thanks
John

---

### Post by pdwerryhouse on 2009-07-06
You can write to the tty of the ssh session ... for example:

```
echo "hello" > /dev/pts/8
```

You can find the tty of your current terminal using the tty command:

```
$ tty
/dev/pts/8

```

Alternatively, the w command will list all the ttys in use:

```
 09:25:48 up 2 days, 11:43,  9 users,  load average: 0.01, 0.08, 0.09
User     tty     From              login@   idle  JCPU  PCPU  what
paul     tty8    :0               Mon 6pm   1:06              /bin/sh /home/pau
paul     pts/1   :0.0             Mon 6pm   1:40    38        bash 
paul     pts/2   :0.0             Mon 6pm   1:35     2        bash 

```

---

### Post by three_jeeps on 2009-07-07
> **pdwerryhouse said:**
> You can write to the tty of the ssh session ... for example:

```
echo "hello" > /dev/pts/8
```

You can find the tty of your current terminal using the tty command:

```
$ tty
/dev/pts/8

```

Thank you! I now know that /pts/0, pts/1 are the ssh terminal sessions.
A follow up question...Because I will not know how many or what  number of the terminal sessions are running, is it possible to write to /pts/*, (to send the message to all of them) or, is there a clever way to at the instant the message is to be sent, see what sessions are open, and send to one or all of them?

(Essentially write a bash script to:
w|grep "pts/" and get the number  after the '/'(store in 'arg'), and pass that to the line 'echo "Sensor triggered"> /pts/arg  )

Thanks
John

---

### Post by koenn on 2009-07-07
```
for PTS in $(w |grep -o pts/.) ; do echo "make coffee"  >>/dev/$PTS; done
```

it works, in that the string "make coffee" appeared in all terminal sessions I had open. It didn't actually get me any coffee.

---

### Post by three_jeeps on 2009-07-07
> **koenn said:**
> ```
for PTS in $(w |grep -o pts/.) ; do echo "make coffee"  >>/dev/$PTS; done
```

it works, in that the string "make coffee" appeared in all terminal sessions I had open. It didn't actually get me any coffee.

Thanks! worked for me... no coffee  either, but I made my own frape!

---

### Post by koenn on 2009-07-07
if you inly want the pseudo-terminals where an ssh session is tunning, you could also try this :
```

w |grep ssh |grep -o pts/.
```

---

