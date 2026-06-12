---
title: "Multitasking?"
date: 2010-04-25
forum: Server Platforms
---

### Post by emalamisura on 2010-04-25
Ok first off, excuse me for my sheer ineptitude on asking this question.  I am by far a GUI guy...

If you are running Ubuntu Server and not using XWindows or any shells, how do you go about running multiple console applications at the same time?

For example I would like to run the mongo daemon and the mongo console...Is this possible?

Thanks,
Eric

---

### Post by renkinjutsu on 2010-04-25
Firstly, there are up to 6 virtual terminals for those things you want to glance at quickly..

There's also a nice little GNU utility you can download and install ```
sudo aptitude install screen
```
which gives you multiple terminals within one terminal (although you'll have to switch between them) and they continue to operate even after you log off.

Another tip is that you can send jobs to the background by adding a '&' after the command

```
$ updatedb &
```
to see the jobs running in your background:```
$ jobs
```
to kill a job in the background ```
kill %[COLOR="Red"]jobnumber[/COLOR]
```

or to send an existing job to the background
```
updatedb # oops, forgot to put the &
^Z  # this means ctrl+Z and will suspend the job
bg %[COLOR="Red"]jobnumber[/COLOR] # will send suspended job into background and continue it

```

---

### Post by craigp84 on 2010-04-25
That was a really good answer renkinjutsu, i liked it a lot. Complete.

---

### Post by mariolopezjr on 2010-04-27
Yes, that was a great post and explanation, I will definitely file this for later. I'd rather not install an extra application when functionality that makes this possible already exists. :)

---

