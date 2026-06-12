---
title: "Some questions on viruses and social engineering"
date: 2005-03-27
forum: Server Platforms
---

### Post by UbuWu on 2005-03-27
I read some quite interesting threads on the forums about viruses on linux today. A few questions came up though:

1. Several people mentioned that a virus wouldn't be able to do much harm as it could only ruin your home directory. Am I the only one that thinks that is a small disaster in itself as well as a lot of people are too lazy too make backups?

2. I read some comments on vbscript making it too easy for every scriptkiddie to make his own virus. Doesn't python come close here?

3. If some malicious code gets executed, are there any mechanisms that prevent it from just waiting for the user to enter his password as he starts synaptic or some other program and using it to get root access?

4. I was amazed that I could do the following so easy:
alias sudo='echo Password:'
It would require a little more work to let it act just like your using sudo and stealing your password. And if I am right all it would require is add some lines to your ~/.bashrc file right? Any comments on this?

---

### Post by dataw0lf on 2005-03-28
> 1. Several people mentioned that a virus wouldn't be able to do much harm as it could only ruin your home directory. Am I the only one that thinks that is a small disaster in itself as well as a lot of people are too lazy too make backups? 
A personal disaster, sure.  But I think the point is more toward a server or something similar getting hit. Sure, losing your mp3s and porn sucks, but it's better than your var, boot, etc.  getting slammed.
> 2. I read some comments on vbscript making it too easy for every scriptkiddie to make his own virus. Doesn't python come close here? 
.... I don't get the comparison to Python.  I think you're confused.  VBScript is Microsoft's answer to JavaScript.
> 3. If some malicious code gets executed, are there any mechanisms that prevent it from just waiting for the user to enter his password as he starts synaptic or some other program and using it to get root access? 
If someone gets some malicious code onto your box, they're probably going to be able to gain root access somehow.  However, process hijacking is a complex topic.  I suggest you read up on security a little more.
> 4. I was amazed that I could do the following so easy:
alias sudo='echo Password:'
It would require a little more work to let it act just like your using sudo and stealing your password. And if I am right all it would require is add some lines to your ~/.bashrc file right? Any comments on this? 
You'd be surprised at what you can write in a bash script.

---

### Post by nemin on 2005-03-28
[QUOTE=dataw0lf]A personal disaster, sure.  But I think the point is more toward a server or something similar getting hit. Sure, losing your mp3s and porn sucks, but it's better than your var, boot, etc.  getting slammed.[/QUOTE]
Hmm, I don't completely agree with you. I've got my whole desktop system installed very shortly : I put in the Ubuntu CD, install it and do some apt-getting... For me, and for most people I guess, it'll be much harder to restore my personal data and settings, if it's even possible at all!
For a server ofcourse, things are different, but viruses usually hit desktops of stupid users, who click OK on everything without thinking ;)

---

### Post by dataw0lf on 2005-03-28
[QUOTE=nemin]Hmm, I don't completely agree with you. I've got my whole desktop system installed very shortly : I put in the Ubuntu CD, install it and do some apt-getting... For me, and for most people I guess, it'll be much harder to restore my personal data and settings, if it's even possible at all!
For a server ofcourse, things are different, but viruses usually hit desktops of stupid users, who click OK on everything without thinking ;)[/QUOTE]
I guess I was trying to explain the difference between a 'personal' loss, and a 'crippling' loss.

---

### Post by r_a_trip on 2005-03-28
*1. Several people mentioned that a virus wouldn't be able to do much harm as it could only ruin your home directory. Am I the only one that thinks that is a small disaster in itself as well as a lot of people are too lazy too make backups?*

Until now GNU/Linux has always enforced user separation, so normally nobody runs as root by default. This makes it very hard for a virus to execute system wide if it is run by a user smart enough to know not to fill in his root password without thought. (This is thinking home-user, corporate users don't have root access).

Due to the diverse nature of all available Distro flavors, it is harder to write a generic virus that will exploit all Distro's at once. The odds of a devastating GNU/Linux virus attack are smaller than on "that other platform". GNU/Linux is not an easy target and its users are more knowledgable. (I hope this stays this way). It will take a very cunning viruswriter to produce something on the scale of Code Red for GNU/Linux.

Does this mean that GNU/Linux is impervious to infection and attack? No, absolutely not, but if a user uses his common sense and keeps up to date, the chances of disaster become very slim. Always be on guard, even if you feel that GNU/Linux is pretty safe.

Loosing your home directory sucks, but it holds the lesson that you will have to keep your stuff safe yourself. If you are old enough to vote, you are old enough to know you have to keep your data safe. Harsh, but the inevitable truth. Developers can only do so much, the rest is up to us users.

To all GNU/Linux newcomers:
Learn the basic GNU/Linux skills. There are lots of good books on the subject. It will be well worth it. Use your system with confidence and the knowledge that you can fix it when things go awry. Don't be the helpless victim, learn and take care of your own computer.

---

