---
title: "Gksudo problem in bash script"
date: 2011-06-02
forum: Ubuntu Dev Link Forum
---

### Post by ktsangop on 2011-06-02
Hello everyone!
I would like some help regarding gksudo command in a script i am trying to develop.

I am trying to develop a gui method to edit nfs exports. I use zenity for the dialogs and i would like to be able to edit the /etc/exports file. 

I am trying to do this with gksudo command like this :
```
gksudo echo $myfolder $IPVAR\(ro\) >> /etc/exports
```
But when the script reaches this line no password promt appears and i get a "permission denied" on terminal

whereas in line:
```
myinterfaces=`gksudo ifconfig | grep -o eth[0-9]`
```
everything is executed correctly.

The only way i managed to do it is by calling the script in terminal like this:
```
gksudo ./myscript 
```

But i want no terminal in my application...!
:)

Is there a way to do it? I think i have some kind of syntax error but tried everything i could (after researching).

Thanks in advance!

---

### Post by DaithiF on 2011-06-02
Hi,
try:
```
echo $myfolder $IPVAR\(ro\) | gksudo tee -a /etc/exports
```

when redirecting output, bash opens the files for writing before executing the command, so in your example you are actually trying to open /etc/exports for appending as your user, which of course fails.  you don't need to be root to echo text, you need to be root to write to that file, so turn things around, echo the text as your user and append it to the file sa root using the tee command.

---

### Post by ktsangop on 2011-06-04
Well i get the password prompt now. And i get no permission denied on terminal.
But nothing is appended on the file
:S

---

