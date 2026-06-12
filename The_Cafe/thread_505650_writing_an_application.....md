---
title: "writing an application...."
date: 2007-07-20
forum: The Cafe
---

### Post by luckyd on 2007-07-20
Hi all, I had an idea the other day for an application. Since I have found getdeb.net so useful I was wondering if there would be a way to make or write an simple pretty app like add/remove... to access it. I have absolutely not programing experience, but I would love some. If anyone has any ideas for how to do this or could point in the right direction for what to learn, please do so. 

P.S. It might complicate things that getdeb.net isn't set up as repo

---

### Post by apoth on 2007-07-20
It'll be a lot to take on from scratch, but this is the route I'd take:

1. Learn ruby. It's open, it's relatively simple, it's a great language. For the purposes of this you just need to pick up enough to run a ruby script and download a file.

2. Get Glade-3 from the repositories, you can use this to create a GUI.

3. Put the lot together.

I'll leave it to you to break this down further if you choose this route, others might offer different routes, perhaps python instead of ruby. Do some googling and read up. Start with "hello world" programs, they're simple examples to get you started with a programming language.

I'm sure you'll have plenty of questions along the way but as this might you months even it's probably worth waiting until you get to a particular stage to answer specifics.

Good luck. :)

---

### Post by luckyd on 2007-07-20
as far as the "hello world" languages I do actually know a bit of basic, not that that would help at all. Just wanted to throw that out there...

---

### Post by Old Pink on 2007-07-20
Then it'd just be like running a browser window pointed at getdeb.net with a slightly different interface? I think you're better off working with the nice guys at getdeb.net to build a repository, which you can then add to your sources.list and get updates from or browse in Add/Remove :)

---

### Post by picpak on 2007-07-20
I fail to see why'd you do this when you can just add a repo.

[list=3][*] Edit /etc/apt/sources.list:

```
gksudo gedit /etc/apt/sources.list
```

[*] Add the following:

```
deb http://ubuntu.org.ua/ getdeb/
```

Save it and exit.


[*] Then run:

```
sudo apt-get update
```[/list]

Now you can install the packages through apt-get or Synaptic.

---

