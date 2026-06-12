---
title: "Have Wine 1.0.1 would like 1.2?"
date: 2011-02-28
forum: Wine
---

### Post by rob2nd9th on 2011-02-28
Hi have gone back to 9.04 - the Jaunty Jackalope due to problems with 10.4 
How ever my wine is now back to 1.0.1 and I would like it to be 1.2 and I cant seem to find how to do this? have been round the block on it, I do remember updating my repository's but cant find that info any more :(

thanks for any help.

---

### Post by howefield on 2011-02-28
Have you tried adding the Wine repository, from the terminal...

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```

```
sudo apt-get update
```

```
sudo apt-get install wine1.2
```

---

### Post by rob2nd9th on 2011-02-28
```
sudo: add-apt-repository: command not found
```

tried most combo of this
 
```
sudo apt-get install wine1.3
```
```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
```

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

ect..

been round and around? have an Identical laptop that fine and tried to copy the usr/bin files but just cant work out how to gain permission to do it.

---

### Post by howefield on 2011-02-28
My apologies, the command should have been

```
sudo apt-add-repository ppa:ubuntu-wine/ppa
```

---

### Post by rob2nd9th on 2011-02-28
Nope, its got me baffled, Im missing something?? 

```

:~$ sudo apt-add-repository ppa:ubuntu-wine/ppa
sudo: apt-add-repository: command not found
```


```
 sudo apt-get install wine1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wine1.2
```

---

### Post by howefield on 2011-02-28
I was right first time, I thought I had got it wrong after your unknown command error.

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```


You could try manually adding the repository.

Go to System > Administration > Software Sources and from the "Other Software" tab press the Add button.  Then paste this line in

```
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu jaunty main
```

Then press the Add Source button.

Add the key from this page.
[http://keyserver.ubuntu.com:11371/pks/lookup?search=0x883E8688397576B6C509DF495A9A06AEF9CB8DB0&op=index](http://keyserver.ubuntu.com:11371/pks/lookup?search=0x883E8688397576B6C509DF495A9A06AEF9CB8DB0&op=index)

Reload your package lists and try installing wine.

---

### Post by rob2nd9th on 2011-02-28
> **howefield said:**
> ```
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu jaunty main
```

Thats the one Thanks,, top stuff  :)

---

