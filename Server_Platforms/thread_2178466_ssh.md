---
title: "ssh"
date: 2013-10-03
forum: Server Platforms
---

### Post by remo2 on 2013-10-03
What is the ssh command mode when you connect to a server?
Where is the directory you are?
What is the command to get it out?

---

### Post by AtomicPenguin on 2013-10-03
'pwd' will display the name of the current working directory.

I'm not understanding the first and third question. :confused:

---

### Post by Lars Noodén on 2013-10-03
When you connect to a server with ssh, you will get your regular login shell as it is configured on your server.  When your session starts you will be in your home directory on the server, whatever that is set to be.  See **pwd** above.

To end your ssh session with the server you can just close the terminal window or else type **exit** or on a new line enter **~.**

---

### Post by CharlesA on 2013-10-03
> **Lars Noodén said:**
> or on a new line enter **~.**

Does that only work with specific terminal programs? I tried it via putty and it just spit back:

```
charles@Thor:~$ ~
-bash: /home/charles: Is a directory
charles@Thor:~$ ~.
-bash: ~.: command not found

```

---

### Post by sandyd on 2013-10-03
> **CharlesA said:**
> Does that only work with specific terminal programs? I tried it via putty and it just spit back:

```
charles@Thor:~$ ~
-bash: /home/charles: Is a directory
charles@Thor:~$ ~.
-bash: ~.: command not found

```

works here with ssh

---

### Post by CharlesA on 2013-10-03
> **sandyd said:**
> works here with ssh

Thanks. Guess it's a Linux thing then. :)

---

### Post by JnPson on 2013-10-03
If I understood the question correct, you want to know how to connect to a server with ssh? You wanna know what directory you end up in? and how to get out. 

1 You connect to a server trough a terminal, if you are in Linux. Press ctrl+alt+T and type ```
ssh username@server
``` Give your password and press enter. 
2 To see what directory you ended up in, type```
 pwd.
``` 
3 To get out and leave the server, type ```
exit
```

---

### Post by Lars Noodén on 2013-10-03
> **CharlesA said:**
> Thanks. Guess it's a Linux thing then. :)

It should be an ssh client thing, but maybe only with the regular ssh client.  PuTTY is a different animal.  If you look in the manual page for ssh(1) in the section "escape characters" or press **~?** you should see the full list.  You can add or remove port forwarding and levels of verbosity that way too.

---

### Post by CharlesA on 2013-10-03
> **Lars Noodén said:**
> It should be an ssh client thing, but maybe only with the regular ssh client.  PuTTY is a different animal.  If you look in the manual page for ssh(1) in the section "escape characters" or press **~?** you should see the full list.  You can add or remove port forwarding and levels of verbosity that way too.

Ah, cool. Thanks for the info!

---

### Post by scbingham on 2013-10-03
ctrl+d will exit too.

---

