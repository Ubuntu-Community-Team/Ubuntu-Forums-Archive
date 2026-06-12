---
title: "RE; Firewall"
date: 2013-01-31
forum: Security
---

### Post by offgridguy on 2013-01-31
Regarding firewall settings using ufw here.

[https://wiki.ubuntu.com/BasicSecurity/Firewall](https://wiki.ubuntu.com/BasicSecurity/Firewall)

When i get to this command and paste it into the terminal, i get invalid clause message??

```
sudo ufw allow out 51413/tcp sudo ufw allow out 51413/udp sudo ufw allow out 6969/tcp

```
:confused:

---

### Post by steeldriver on 2013-01-31
I would think they need to be separate commands; either

```
sudo ufw allow out 51413/tcp ; sudo ufw allow out 51413/udp ; sudo ufw allow out 6969/tcp
```or

```
sudo ufw allow out 51413/tcp 
sudo ufw allow out 51413/udp 
sudo ufw allow out 6969/tcp
```

---

### Post by offgridguy on 2013-01-31
> **steeldriver said:**
> I would think they need to be separate commands; either

```
sudo ufw allow out 51413/tcp ; sudo ufw allow out 51413/udp ; sudo ufw allow out 6969/tcp
```or

```
sudo ufw allow out 51413/tcp 
sudo ufw allow out 51413/udp 
sudo ufw allow out 6969/tcp
```
You could be right, however the other commands to that point worked verbatim. perhaps the
addition of && between commands ??  Thanks for the reply, I will try your suggestion.

---

### Post by Doug S on 2013-01-31
I edited the wiki. I think 3 separate lines was the original intent, but it did not render as such.
 
Edit: It is 3 separate lines in [Dandertux's original forums thread]("http://ubuntuforums.org/showthread.php?t=1876124").

---

### Post by offgridguy on 2013-01-31
> **Doug S said:**
> I edited the wiki. I think 3 separate lines was the original intent, but it did not render as such.
It does work as three separate  commands, thanks.

---

### Post by bodhi.zazen on 2013-01-31
it is a small technical issue, but with bash, on the command line, ";" means to continue. So you can type it all on one line. If it did not work there was a typo.

```
bodhi@ubuntu~# echo "1" ; echo "2"
1
2
```


With that in mind, 3 separate lines on the wiki is more readable and less technical (IMO)

On the command line, && and || are logical operators, and / or

```
bodhi@ubuntu~# ecko "1"
zsh: command not found: ecko

bodhi@ubuntu~# ecko "1" || echo "wrong command"
zsh: command not found: ecko
wrong command

bodhi@ubuntu~# ecko "1" && echo "wrong command"
zsh: command not found: ecko
bodhi@ubuntu~#
```

sure I am using zsh, same thing in bash.

---

### Post by offgridguy on 2013-01-31
bohdi.zazen, thanks for the info, i am glad the wiki has been edited as well.  I knew it wasn't a typo on my part as i was pasting it into the terminal.

---

### Post by Ms. Daisy on 2013-01-31
My bad. Thanks for fixing it Doug.

And that reminds me I never replaced the photos. That was the whole reason I copied Dangertux's thread into the wiki. 

Offgridguy- take some screen shots while you work on that! ;)

---

### Post by offgridguy on 2013-02-01
> **Ms. Daisy said:**
> 

Offgridguy- take some screen shots while you work on that! ;)

:-k

---

