---
title: "The Ubuntu Juggernaut: Resistance Is Futile"
date: 2005-10-16
forum: The Cafe
---

### Post by matthew on 2005-10-16
Article/review: [http://distrowatch.com/dwres.php?resource=review-ubuntu]("http://distrowatch.com/dwres.php?resource=review-ubuntu")

---

### Post by m0biu5 on 2005-10-16
Ah, that was a fun article to read. Good find!

---

### Post by Goober on 2005-10-16
Well, that was very entertaining.  I shall have to look into this 686 Kernel business . . . 

And I continue to self-debate about getting a Firewall . . .

---

### Post by mstlyevil on 2005-10-16
[QUOTE=Goober]Well, that was very entertaining.  I shall have to look into this 686 Kernel business . . . 

And I continue to self-debate about getting a Firewall . . .[/QUOTE]

 Just get a router with a built in hardware firewall. Then you don't need to worry about a software firewall in Linux.

---

### Post by Goober on 2005-10-16
[QUOTE=mstlyevil]Just get a router with a built in hardware firewall. Then you don't need to worry about a software firewall in Linux.[/QUOTE]

I have considered that, but I have heard horror stories from friends saying that they don't allow you to play Online Multiplayer games easily, and they are just generally, from what I understand, harder to change to allow access then Software ones.  

I don't think I need a Firewall for Linux anyway, I only use the 'net for surfing at forums like this, e-mails, and upgrading/updating Breezy.

---

### Post by Ubunted on 2005-10-16
[QUOTE=Goober]I only use the 'net for surfing at forums like this, e-mails, and upgrading/updating Breezy.[/QUOTE]

Then no, you don't. I have Firestarter, but only as an easy GUI tool that allows me to open Bittorrent ports at will.

---

### Post by WildTangent on 2005-10-16
[QUOTE=Goober]I have considered that, but I have heard horror stories from friends saying that they don't allow you to play Online Multiplayer games easily, and they are just generally, from what I understand, harder to change to allow access then Software ones.  

I don't think I need a Firewall for Linux anyway, I only use the 'net for surfing at forums like this, e-mails, and upgrading/updating Breezy.[/QUOTE]
My Dlink router performs like a champ, I haven't had any gaming problems, and looking at the logs, I see it blocks ALOT of crap.

-Wild

---

### Post by skirkpatrick on 2005-10-16
I use a Linksys WRT54G and there are 3 people in my house that play online games from MMPORG to FPS and I've never had any problems.  The only problem you will see is if you host a game server, then you have to open ports for it.

---

### Post by poofyhairguy on 2005-10-16
I wish the review would not give advice like this:

> 
If you're a little more daring, you might want to add the debian-marillat repository to /etc/apt/sources.list (use testing/main). This will allow you to install Lame, MPlayer and other software which has "problems" with software patents and the DMCA. As for just where you can find the nearest debian-marillat repositories, you'll have to do some Googling.

Seeing as how thats a fast way to break your box in the long run.

---

### Post by benplaut on 2005-10-17
it's a decent review, but the guy didn't really understand sudo, it seems...

---

### Post by xmastree on 2005-10-17
He also forgot to mention one of Ubuntu's greatest assets. **The Forums** :cool:

---

### Post by Sheinar on 2005-10-17
[QUOTE=xmastree]He also forgot to mention one of Ubuntu's greatest assets. **The Forums** :cool:[/QUOTE]
He did?

> A big plus is the helpful and friendly Ubuntu online community. When you're racking your brain with what seems like an insurmountable problem, it's good to know that assistance is just a few mouse clicks away.

---

### Post by agger on 2005-10-17
[QUOTE=benplaut]it's a decent review, but the guy didn't really understand sudo, it seems...[/QUOTE]

No - he didn't seem to understand that the point of disabling the root account is to never run or login as root.

Another point, though: Might he be right in being nervous over running as a sudoer during "normal" work?

To put it another way: Might somebody be able to attack Ubuntu machines specifically by assuming the user is a sudoer and trying to sniff or guess the password?

Because that would mean it might be preferrable to have two levels here, using a "normal" user to su to a sudo user, do the changes there, and then go back to the normal user.

This makes it all more complicated, but it might be "wrapped" to make it transparent for the user.

---

### Post by xmastree on 2005-10-17
[QUOTE=Sheinar]He did?[/QUOTE]Ah, well, ok. I missed that bit... :rolleyes:

---

### Post by Wolki on 2005-10-17
[QUOTE=poofyhairguy]I wish the review would not give advice like this:

Seeing as how thats a fast way to break your box in the long run.[/QUOTE]

I thought the same. Especially since we have great wiki pages with understandable instructions on how to install and configure all of that.

The sudo part is also questionable (sudo is *not* the same as giving each user admin rights), and configuring repositories has a gui which could have been mentioned.

Overall, not a really bad review, but I read better ones that have up-to-date information.

---

### Post by Mr. Electric Wizard on 2005-10-17
Regarding the firewall.
I just took my Router/with/firewall out of the equation on my home network, and intalled an IPCop firewall with 3 network zones.
I have been very satisfied with this firewall.

---

