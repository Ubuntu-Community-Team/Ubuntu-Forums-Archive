---
title: "Run script/command when login?"
date: 2012-05-20
forum: Server Platforms
---

### Post by DingusFett on 2012-05-20
Hi guys, I am setting up a web server and would just like to know how to have a command automatically run when I login (will be via SSH)? If it matters, the server is using 11.04

---

### Post by MG&amp;TL on 2012-05-20
Unless I'm wrong, putting it in ~/.bashrc should work. Logging in implicitly starts a shell. Sorry, but I don't know the "proper" way to do things.

---

### Post by DingusFett on 2012-05-20
Thanks mate, that was exactly what I was looking for. I'm very new to Ubuntu and Linux in general, but very keen to learn. I'm used to OpenVMS where you have a login.com file that runs when you login so was hoping for something similar where I can add commands to run automatically and this seems to be what I'm looking for.

---

### Post by MG&amp;TL on 2012-05-20
> **DingusFett said:**
> Thanks mate, that was exactly what I was looking for. I'm very new to Ubuntu and Linux in general, but very keen to learn. I'm used to OpenVMS where you have a login.com file that runs when you login so was hoping for something similar where I can add commands to run automatically and this seems to be what I'm looking for.

No problem. Although if you ever use a system where you forward X (or similiar), that probably won't work. Have fun!

---

### Post by Jonathan L on 2012-05-20
> Unless I'm wrong, putting it in ~/.bashrc should work. Logging in implicitly starts a shell.

Hi Dingus (and MG)

That should work, but might execute the command more often that intended.  Probably more "proper" to put it in .profile which is run once per login; .bashrc is run once per shell.

Hope that helps.

Kind regards,
Jonathan

---

### Post by markbl on 2012-05-20
You can put it in .bashrc, or .profile, but if you just want to run the script on ssh logins then:
```

if [ -n "$SSH_TTY" ]; then
   $HOME/bin/run_ssh_login_script
fi

```

---

### Post by DingusFett on 2012-05-20
Thanks guys, it is really just a one-line command that feeds a random string from 'fortune' into 'cowsay' for my own amusement whenever I login. The server I am setting up as a basic web and email server mostly just to learn about setting up basic server, so I will be the only one logging in.

---

