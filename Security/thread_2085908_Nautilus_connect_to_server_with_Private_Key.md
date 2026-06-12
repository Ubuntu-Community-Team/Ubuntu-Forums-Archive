---
title: "Nautilus: connect to server with Private Key"
date: 2012-11-19
forum: Security
---

### Post by DIFORT on 2012-11-19
Hello everybody :)

I am very new on Linux... I think I will be able to ask my question properly. I want to connect to the ssh of my University. With the terminal, I do that:

ssh x.x.x.x -p x -i privatekey -l myuser

And it connects correctly. But when I try to do: Places --> Connect server.. It is not working. I don't know what have to do with the private key in this case.

Thanks for advance.

---

### Post by MadsRC on 2012-11-19
you should be able to do it with you username prepended to the server. So server would be: [email]user@server.tld[/email]

And just leave username and password blank.

See: [http://askubuntu.com/questions/102608/key-based-ssh-login-with-nautilus-connect-to-server](http://askubuntu.com/questions/102608/key-based-ssh-login-with-nautilus-connect-to-server)

---

### Post by DIFORT on 2012-11-19
Hello MadsRC,

Thanks for the answer, I did that but when I click to connect, Nautilus ask me for the password (and I don't have a password, I have a file that is privatekey). So still I don't know how to connect to th server.

---

EDIT: ok now it works, I've just done  this:

```
ssh-add my_private_key

```

and then execute nautilus as you said:

[IMG]http://i.stack.imgur.com/bCz3x.png[/IMG]

:)

---

### Post by MadsRC on 2012-11-19
I'm glad it worked out :)

---

### Post by h00dlum on 2012-11-22
If you set up your remote connection in your user ssh config file (~/.ssh/config) and use key authentication you only need the server name you've assigned to the connection, the type of connection, and potentially the directory.

---

