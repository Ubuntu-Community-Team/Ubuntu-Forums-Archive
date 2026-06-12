---
title: "Tremulous problem"
date: 2007-06-10
forum: Ubuntu Gamers Arena
---

### Post by Hightide on 2007-06-10
Hi 
I have downloaded the tremulous.run file, run in terminal and then it says 'dont have permissions'  

what does this mean and what can I do?

Hightide  ;)

---

### Post by steveneddy on 2007-06-10
Why don't you just install it from Synaptic? It's in the repos.

---

### Post by Hightide on 2007-06-10
Hi 
thankyou for your reply.

tried synaptic with no luck!

---

### Post by hikaricore on 2007-06-10
> **steveneddy said:**
> Why don't you just install it from Synaptic? It's in the repos.

OP is using dapper, I don't believe it was in the repos for dapper.

---

### Post by hikaricore on 2007-06-10
> **Hightide said:**
> Hi 
I have downloaded the tremulous.run file, run in terminal and then it says 'dont have permissions'  

what does this mean and what can I do?

Hightide  ;)

From the terminal you need to do the following:

```
chmod +x tremulous.run
sudo ./tremulous.run
```

Upon installation completion **DO NOT** launch the game from the installer or this will cause problems with the game.  Launch it from your Applications/Games menu or a terminal after.

Good luck


--Aaron

---

### Post by Hightide on 2007-06-11
Hi AAron

yes successfully installed but cant find in application games menu. How do I launch in Terminal?

Paul;)

---

### Post by hikaricore on 2007-06-11
I don't remember off the top of my head, but try typing:

```
tremulous
```

^_^

Sometimes new icons don't show up in gnome until you log out and back in, but you can manually add them with the menu editor once you know the name of the application's binary.

---

### Post by Hightide on 2007-06-12
Hi great stuff man

all is well

love this ubuntu!!!:)

---

