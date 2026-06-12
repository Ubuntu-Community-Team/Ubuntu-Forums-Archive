---
title: "How to set up password protection for specific applications?"
date: 2011-07-02
forum: Security
---

### Post by tazboxe on 2011-07-02
Hi, is there a way to make a password key-ring for a list of specific applications, specifically; all the applications relating to preferences. I'm running Ubuntu 11.04, I'm the only user, I disabled all login password requirements because they were annoying me and I'm cool with anybody using any of my applications as long as they aren't capable of changing my system in any way. Some of the applications I would like to be on the list include the terminal, the network connections preferences, the keyboard preferences. I wan't to be prompted for a password before opening these programs.

*Taz*

---

### Post by nerdy_kid on 2011-07-02
well, this is one way -- but note that anyone who knows what he/she is doing can reverse this really easy...

for each program (I'm using the terminal for example):

```

cp  /usr/share/applications/gnome-terminal.desktop ~/.local/applications/
gedit ~/.local/applications/gnome-terminal.desktop

```

append "gksu " without quotes to the "Exec" line.  That will prompt for a password now, but it will also run as root -- that might not work for the network preferences and some other apps.  Maybe just set up a guest account, and enable auto screen locking?

{edit}
to reverse the above:  remove the file(s) you copied into .local/share/applications, in my example above the file is gnome-terminal.desktop

---

### Post by tazboxe on 2011-07-02
> **nerdy_kid said:**
> well, this is one way -- but note that anyone who knows what he/she is doing can reverse this really easy...

for each program (I'm using the terminal for example):

```

cp  /usr/share/applications/gnome-terminal.desktop ~/.local/applications/
gedit ~/.local/applications/gnome-terminal.desktop

```

append "gksu " without quotes to the "Exec" line.  That will prompt for a password now, but it will also run as root -- that might not work for the network preferences and some other apps.  Maybe just set up a guest account, and enable auto screen locking?

{edit}
to reverse the above:  remove the file(s) you copied into .local/share/applications, in my example above the file is gnome-terminal.desktop

I should mention that I'm rather new to Ubuntu so could you explain it to me as you would to a two year old, I don't quite get what you mean. I pasted the code into the terminal, I got that far but then I wasn't sure what to do next. :(

---

### Post by cariboo on 2011-07-02
What nerdy_kid is suggesting, is not a very good idea, as all the configuration files would be in root's home directory, which is only accessible by the root user, which is disabled by default.

What applications do you want to block? If we knew that, we would know how to help you solve the problem.

---

### Post by nerdy_kid on 2011-07-02
> **tazboxe said:**
> I should mention that I'm rather new to Ubuntu so could you explain it to me as you would to a two year old, I don't quite get what you mean. I pasted the code into the terminal, I got that far but then I wasn't sure what to do next. :(

ah, my apologies, just ignore what I said to do then as it probably won't really work anyway...

However, would enabling the guest account and setting the computer to automatically lock the screen perhaps be a easier solution?

---

