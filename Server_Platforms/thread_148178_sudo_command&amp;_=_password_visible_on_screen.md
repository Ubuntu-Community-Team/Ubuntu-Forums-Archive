---
title: "sudo command&amp; = password visible on screen?"
date: 2006-03-21
forum: Server Platforms
---

### Post by virgule on 2006-03-21
Watch out guys! if you want to run something via sudo but keep access to the shell you must use the -b switch. 'sudo' and '&' should never be seen in the same command.
```

sudo -b command # is good
sudo command & # is bad

```
Original message is below
Is this a bug or a feature? :)
```

  [virgule @ ~ ]# sudo synpatic&
[1] 8104
  [virgule @ ~ ]# Password:
my passord right here!
bash: my: command not found

[1]+  Stopped                 sudo synpatic
  [virgule @ ~ ]#

```

---

### Post by henriquemaia on 2006-03-21
A feature.

The thing is that when you put the **&** in front of the command with sudo, the command **sudo** goes to the background. He aks your pass, but the task is already on the background, so ignores what you type. You type the password thinking you're answering the password request, but you're just typing  it plain on the terminal line.

Don't use **&** with sudo or, at least, use one sudo command first without **&** and then you can use that (because sudo remembers your password and don't ask it again for some time).

---

### Post by mentok on 2006-03-21
You can try ```
sudo 'command&'
``` I beleive that will run sudo in the foreground when it asks for your password and then run command in the background.

Edit: Never mind, doesn't work.

---

### Post by virgule on 2006-03-21
Nope. It does not :-k 

I tried several syntax they all fail the same way or simply not work.
```

sudo 'command&'
sudo 'command &'
sudo "command&"
sudo "command &"
sudo & command
```

But I found the way in the man pages \\:D/ its the -b switch!
```

sudo -b command

```
[quote=man sudo(8)]
-b  The -b (background) option tells sudo to run the given command in the background. 
Note that if you use the -b option you cannot use shell job control to manipulate the process.
[/quote]

Don't you think some code should be added/modified in sudo in order to prevent such a mishap? Over-the-shoulder password sniffing could work..

---

### Post by ssam on 2006-03-22
i usually start the command with
```
sudo command
```
and then ctrl-z to pause it and
```
bg
```
to background it. or
```
fg
```
to forground it.

---

