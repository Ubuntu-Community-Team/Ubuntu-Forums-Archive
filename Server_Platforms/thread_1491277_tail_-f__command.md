---
title: "tail -f  command"
date: 2010-05-23
forum: Server Platforms
---

### Post by AresArtemis1 on 2010-05-23
hi, I am debugging an application product on the server command line, any professional know how to return to root command line screen while I am using **tail -f** 	  command?

best regards,:guitar:

---

### Post by CharlesA on 2010-05-23
Open another terminal or another ssh session.

Otherwise, I suppose you could send it to the background, but then you wouldn't see the output.

---

### Post by AresArtemis1 on 2010-05-23
could you tell me how to just ending the process of debugging and return to the regular command line

appreciate:guitar:

---

### Post by GlazedDonut on 2010-05-23
ctrl-c works for me

---

### Post by CharlesA on 2010-05-23
CTRL+C would kill it.

---

### Post by sylvester_0 on 2010-05-23
Not sure what you're asking for but "tail -f&" will allow you to still run the tail and use the terminal at the same time. The terminal won't be highly usable though, especially if your tail is producing alot of output.

---

### Post by jerome1232 on 2010-05-23
screen

[http://linux.die.net/man/1/screen](http://linux.die.net/man/1/screen)

---

