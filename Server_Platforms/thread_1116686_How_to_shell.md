---
title: "How to shell"
date: 2009-04-05
forum: Server Platforms
---

### Post by Spikerok on 2009-04-05
How to make shell script to modify things
1. Read script and add function in between text
so eg
we have a text file called "Hello WORLD!!!"
[PHP]
HELLO WORLD!!!

IM USING UBUNTU 8.10!
AND I LOVE IT!!!

Thank you for reading!
[/PHP]

How can i add some line between "AND I LOVE IT" and "Thank you for reading!"

---

### Post by zigga15 on 2009-04-05
> **Spikerok said:**
> How to make shell script to modify things
1. Read script and add function in between text
so eg
we have a text file called "Hello WORLD!!!"
[PHP]
HELLO WORLD!!!

IM USING UBUNTU 8.10!
AND I LOVE IT!!!

Thank you for reading!
[/PHP]

How can i add some line between "AND I LOVE IT" and "Thank you for reading!"

not sure if you are writing a shell script or a PHP script but n e way.

echo hello
echo
echo hello2

shell scripts use echo to output to terminal. Once you put this into a file then use chmod +x filename, then ./filename and that stuff should print out.

If you are using PHP then you need to learn about "new line characters" just do a google search.

---

