---
title: "dot slash command"
date: 2008-02-12
forum: Server Platforms
---

### Post by intodesi on 2008-02-12
I am running a dot slash command ./ to execute a file, how do i Stop it, or run it in another instance so i can continue to work while its running?

Thanks

---

### Post by LaRoza on 2008-02-12
You can run a program in the background with a "&".

```

gedit&

```

a "./" isn't anything special, it only is specifying the path to the executable. A . means "this directory".

---

### Post by intodesi on 2008-02-12
I was having a problem using gedit in the server enviroment because of no gui and really dont want a gui. I am new to any linux platform/flavor, ,  but would like to learn through just the terminal (i think thats what its called)

Gedit wont work though

says command not found, so i am not sure if i am doing something wrong or?

is there a way to use the dot slash command with the & ?

---

### Post by banewman on 2008-02-12
gedit needs a gui - if in terminal only mode then type - 
nano filename
 and that will open the file with the nano editor - nano has the controls listed at the bottom - ^ is the ctrl button
:)

---

### Post by intodesi on 2008-02-12
its not something i need to open with a text editor though, its an actual compilation i would like to run.

I know about nano i was using that to edit ini and txt files.

when i type ./server it starts it up and runs it, but after i start it i cant do anything else, and i cant exit from it, or move to a different project, whatever, while its running., and i have to manualy turn off my machines power to get it to start...

---

### Post by banewman on 2008-02-12
You can get different terminals by typing - 
ctrl-alt-F2 to ctrl-alt-f6
if you have one app running from login  type  -   ctrl-alt-F3
and you get a new terminal - if you type   top   you can find the   PID   of a running app - then press k and then type the PID # and enter and the app will be "killed"

---

### Post by intodesi on 2008-02-12
Thank you very much :) was just what I was looking for..Much Apreciated hehe

---

### Post by Skoude on 2008-02-12
I suggest that you learn how to use screen..

With screen you can for example leave your programs running in a background while you log off from the server. And then when you log in again, you can have the same screen back on :)

here is more information about it: 
[http://www.gnu.org/software/screen/#TOCintroduction](http://www.gnu.org/software/screen/#TOCintroduction)

---

### Post by lespaul_rentals on 2008-02-12
Try the following:

```
nohup <process> &
```

There should then be a line that says something similar to:

```
Process output appended to file...
```

After that, you should have a new line on your terminal where you can run another process:

```
user@yourhostname: $
```

To stop the old process, run:

```
killall <process name>
```

---

### Post by intodesi on 2008-02-13
actually the alt ctrl f jeys work great :P just what i needed..

---

### Post by netztier on 2008-02-13
> **intodesi said:**
> actually the alt ctrl f jeys work great :P just what i needed..

Yes, they do and can really get you out of trouble if something is wrong with the box.

Once you'll have discovered how great it is to log into the machine from remote via SSH, you'll be asking for the same possibility: to have multiple screens/sessions available without having to open multiple parallel SSH connections

That's when you'll remember that someone suggested using **screen** for exactly that purpose ;-)

regards

Marc

---

