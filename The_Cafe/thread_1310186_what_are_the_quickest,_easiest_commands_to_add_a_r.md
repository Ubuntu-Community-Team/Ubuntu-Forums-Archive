---
title: "what are the quickest, easiest commands to add a repo and key from the prompt?"
date: 2009-11-01
forum: The Cafe
---

### Post by hoppipolla on 2009-11-01
This never really mattered to me before as it was just me using Ubuntu, but now I'm teaching someone (and possibly multiple people I don't know O.O) and so this is VERY useful to know!

I really want to give a command which is like -

BIT TO ADD REPO && BIT TO ADD KEY && sudo apt-get update

because then basically you've fixed a problem in one copy and pastable command!


Pidgin does it like this:

```
echo deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu `lsb_release --short --codename` main | sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
```

and then this for the key:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
```

I think that's correct...

sorry to act like a noob on this one, I wasn't sure where to post this thread either as it's not so much a SUPPORT thread, it's like a "How to give support" thread! lol :)

Hoppi!

---

### Post by FuturePilot on 2009-11-01
The new "add-apt-repository" command in Karmic.
For example

```
sudo add-apt-repository ppa:banshee-team/ppa
```
Adds the Banshee PPA and fetches the key.

---

### Post by hoppipolla on 2009-11-01
> **FuturePilot said:**
> The new "add-apt-repository" command in Karmic.
For example

```
sudo add-apt-repository ppa:banshee-team/ppa
```
Adds the Banshee PPA and fetches the key.

wow O.O that's super stylish I like that!! Good call! :)

how does it work? i mean... how does it know the full way to access that repo?

---

### Post by sisco311 on 2009-11-01
in karmic:
```
sudo add-apt-repository ppa:pidgin-developers
```

EDIT: :( am i slow?

---

### Post by NoaHall on 2009-11-01
Well, if it's karmic, you don't need to do it like that anymore.

```
sudo add-apt-repository ppa:namehere/ppa 
```

Oops, two people answered before me xD

---

### Post by hoppipolla on 2009-11-01
that really is very cool. so how does it know everything about it already, like where everything is stored?

That's such a leap for Karmic, I'm impressed! I didn't fully realize the implications of this! :)


EDIT -- Also, do you need to add the /ppa on the end? Or does it work that bit out?

---

### Post by sisco311 on 2009-11-01
> **hoppipolla said:**
> wow O.O that's super stylish I like that!! Good call! :)

how does it work? i mean... how does it know the full way to access that repo?


well, if you use the:
```
add-apt-repository **ppa**:<ppa_name>
```
syntax, then it's obvious that it's a ppa repo.

or you can run something like:
```
add-apt-repository "deb http://dl.google.com/linux/deb/ stable non-free"
```

it's probably the same as:
```
echo "deb http://dl.google.com/linux/deb/ stable non-free" | sudo tee -a /etc/apt/sources.list
```
+ a minimal syntax check.

---

### Post by hoppipolla on 2009-11-01
ok wicked. Are there some repos that it won't know the location of just from add-apt-repository ppa:<ppa_name> ?

I mean surely they need to be in some faraway database somewhere... right? o.O

---

