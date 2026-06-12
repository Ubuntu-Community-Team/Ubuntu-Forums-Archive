---
title: "list packages by origin"
date: 2010-08-05
forum: Server Platforms
---

### Post by surfer on 2010-08-05
the synaptic package manager has the nice feature that packages can be listed by their origin (the url given in [FONT="Courier New"]/etc/apt/sources.list[/FONT]).

how can i do this on the command line? i'd especially like to see all the available packages and the ones that are installed.

tanks in advance!

---

### Post by surfer on 2010-08-06
bump...

---

### Post by surfer on 2010-08-11
50+ views but no replies?

...anybody?

---

### Post by surfer on 2010-08-18
one more desperate try... anybody?

---

### Post by LightningCrash on 2010-08-18
are you wanting to display packages by the repo they come from?
similar to what yum does?

---

### Post by surfer on 2010-08-18
i've never used redhat/fedora, so i do not know what yum is able to. but yes, i'd lite to "display packages by the repo they come from".

---

### Post by stlsaint on 2010-08-18
Yes this is possible :popcorn:
See here on: [ExploringRepos]("https://help.ubuntu.com/community/Repositories/Ubuntu#Exploring%20the%20Repositories")

---

### Post by surfer on 2010-08-18
thanks for the link. but that only explains how to do it in synaptic. as i said: i know how to do this in synaptic and would like to know how to do it on the command line.

---

### Post by stlsaint on 2010-08-18
Your going to want to read up on Apt-Get for that.

---

### Post by nymack66 on 2010-08-18
My question is why? What is the objective here?

---

### Post by lykwydchykyn on 2010-08-18
check out aptitude, I *think* it can do this, but I can't confirm that right now since I'm in the middle of an update :).

Aptitude should already be installed on server edition, just run "sudo aptitude".

---

### Post by surfer on 2010-08-18
> **nymack66 said:**
> My question is why? What is the objective here?

i use FAI. in the reops there, there is e.g. the package initramfs-tools (which must only be used in the fai chroot environment). i'd like to make sure that i have the package with the correct origin on my server (origin: lucid) and in my chroot (origin: fai). ok?

---

### Post by surfer on 2010-08-18
> **lykwydchykyn said:**
> check out aptitude, I *think* it can do this, but I can't confirm that right now since I'm in the middle of an update :).

Aptitude should already be installed on server edition, just run "sudo aptitude".

will try that. thanks.

---

### Post by eshneto on 2010-08-18
Well, isn't it obnoxious when someone that doesn't know the answer to the problem keeps asking why do you want that solution? I would like to know why do you want to know "why?" if you're not going to help anyway? Dude!

I once needed that solution too. And also did not get any help from the forums. Let me explain why, if it does matters that much to you...

The folks here at my university installed Ubuntu and, without my knowledge, enabled the backports ppa. Needless to say, the latest update broke everything around here, since KDE4.5 is being tested (funny enough, Fedora guys are always able to update KDE without messing around the whole desktop, but Ubuntu dev team seems unable to do so).

I had to disable the repository and remove a whole bunch of packages from the command line. It was very difficult, but I eventually got the desktop running again.

Now I would love to know an easy way of doing this from the command line.

Also, "believing" isn't enough, since I do know about aptitude and most Ubuntu user will also know. Furthermore, if a user is novice enough to ignore aptitude's existence, it will likely be difficult to him/her find the way to obtain such listing. I am myself an experienced user and couldn't do much within aptitude's tui - even though the functionality may be there and it is just my way of thinking about menu organization that doesn't match aptitude's developers (also, even though I like aptitude and use exclusively it for package administration, I still think that saying that it doesn't have Super Cow Powers is a ridiculous and annoying way of giving error messages, but maybe I am overly dull to understand the joke).

As an example, by looking at man pages, I found that
dpkg --get-selections
lists all your installed packages, but does not show from which repository it comes.

Now I know that I can use synaptic to find out if there still are "alien" packages in my system, and I will definitely try do so. Actually the only help I got from this forum was from the guy that started this thread!

I definitely think that people who do not know how to provide a solution should _not_ answer why the question is being asked because it is likely that he/she won't help even if there is a good reason for that question to be asked. Open another thread asking why something would be needed and wait to see if someone bothers to answer!

---

### Post by lykwydchykyn on 2010-08-19
> **eshneto said:**
> 

Also, "believing" isn't enough, since I do know about aptitude and most Ubuntu user will also know. Furthermore, if a user is novice enough to ignore aptitude's existence, it will likely be difficult to him/her find the way to obtain such listing. I am myself an experienced user and couldn't do much within aptitude's tui - even though the functionality may be there and it is just my way of thinking about menu organization that doesn't match aptitude's developers (also, even though I like aptitude and use exclusively it for package administration, I still think that saying that it doesn't have Super Cow Powers is a ridiculous and annoying way of giving error messages, but maybe I am overly dull to understand the joke).



I'm sorry my answer isn't up to your rigorous standards of what constitutes a helpful response.  Next time I just shan't bother.

---

### Post by surfer on 2010-08-19
> **lykwydchykyn said:**
> I'm sorry my answer isn't up to your rigorous standards of what constitutes a helpful response.  Next time I just shan't bother.

any help is appreciated! thank you!

as long as a post suggests something i can try, i'm happy with it!

and yes... the 'why' question was not really helpful.

---

### Post by surfer on 2010-08-19
i just found [this script]("http://goonmill.org/static/dpkg-origins"). it does something along the lines of what i need... the output is just not very usable. but it's a good starting point anyway!

---

### Post by eshneto on 2010-08-19
> **surfer said:**
> i just found [this script]("http://goonmill.org/static/dpkg-origins"). it does something along the lines of what i need... the output is just not very usable. but it's a good starting point anyway!

The best thing about this script is that it nicely outputs the ppa's packages separately from all the rest for the very reason synaptic doesn't show them to me anymore: I've disabled the ppa!

Thank you surfer.

---

