---
title: "SSH tunnel"
date: 2005-05-24
forum: Server Platforms
---

### Post by Infernal on 2005-05-24
can someone tell me how to set up an SSH tunnel on ubuntu 5.0.4?

thx

---

### Post by dataw0lf on 2005-05-24
This is a rather broad question.  What are you trying to tunnel with ssh? Here's a good rundown of the basics of ssh tunnelling:
[http://www.rzg.mpg.de/networking/tunnelling.html](http://www.rzg.mpg.de/networking/tunnelling.html)

---

### Post by Infernal on 2005-05-24
to connect to my pc from everywhere, so i can upload/download files from/to it

---

### Post by spartas on 2005-05-24
Essentially, just run the following command

```

sudo apt-get install ssh

```

Then you can connect from anywhere using the following command:
```

ssh [username]@[I.P. address or hostname]

```

But you will probably want to refer to the [lighted path](http://ubuntuguide.org/#sshserver) for more information

---

