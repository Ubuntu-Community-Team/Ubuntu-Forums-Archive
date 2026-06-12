---
title: "Why does &quot;apt-get upgrade&quot; fail...?"
date: 2011-04-29
forum: The Cafe
---

### Post by nattynarwhal on 2011-04-29
Hiya. So I installed Natty, and when I do:

```

sudo apt-get update && sudo apt-get upgrade

```

It fails constantly @ upgrade step. I thought Canonical were this Uber giant company with lots of $$$ and server bandwidth?

---

### Post by tgm4883 on 2011-04-29
> **nattynarwhal said:**
> Hiya. So I installed Natty, and when I do:

```

sudo apt-get update && sudo apt-get upgrade

```

It fails constantly @ upgrade step. I thought Canonical were this Uber giant company with lots of $$$ and server bandwidth?

yea the servers are probably still getting hammered. I'll assume thats the issue, but you didn't really post any error messages so my guess is as good as "ferrets have eaten through your phone line"

---

### Post by tjwoosta on 2011-04-29
^this

also the community cafe is not a support section.

---

### Post by nattynarwhal on 2011-04-29
> **tjwoosta said:**
> ^this

also the community cafe is not a support section.

:D LOL

Okay, thanks for the feedback.

---

### Post by juancarlospaco on 2011-04-29
sudo do-release-upgrade

---

### Post by nattynarwhal on 2011-04-29
> **juancarlospaco said:**
> sudo do-release-upgrade

What do you propose I upgrade TO? 11.10? :D

---

### Post by el_koraco on 2011-04-29
Ain't no upgrades gonna be working right for a while now.

---

### Post by earthpigg on 2011-04-29
nice signature, el_koraco. perhaps it applies to the subject of this thread? :P

---

### Post by el_koraco on 2011-04-29
well, that's why I posted. Btw, I suggest running apt-get dist-upgrade in the early stages of releases. It handles everything better. And read what it is trying to do, the server situation might mean that some updates will not arrive to your server in time, and apt has been having a habit of removing entire desktops during the alpha and beta phases. 

Do not use aptitude unless you're on LTS. Ever.

---

### Post by Elfy on 2011-04-29
[http://ubuntuforums.org/showpost.php?p=10741769&postcount=22](http://ubuntuforums.org/showpost.php?p=10741769&postcount=22)

---

