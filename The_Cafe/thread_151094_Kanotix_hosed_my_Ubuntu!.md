---
title: "Kanotix hosed my Ubuntu!"
date: 2006-03-27
forum: The Cafe
---

### Post by Lucho on 2006-03-27
I don`t know in which forum to post, so I'll put it here. Sorry if I
 picked the wrong forum.
Like the title says, I haven`t had a good weekend. I had decided to try
Kanotix 64, since I had a windows partition I wasn`t using (three months 
without Windows and I and my comp have never been so productive!
WOO-HOO! :D ). I loaded kanotix 64 in live cd mode, selected the "install
to HD" option, verified that everything was in order, and began. 
   Well, The results surprised me, to say the least. The installer listed very 
clearly my choice of partition- hda3- but it installed it in a different one. Yes,
instead of hda3 it went to hdb3, which is (um, WAS) my Ubuntu 64. After all
the work fine-tuning my breezy 64, kanotix wiped it off the hd :shock: .
**Begin Rant***
   People, I tried to get information on another forum, and only got a bunch of
"it's a problem between the chair and the screen, were you drinking, was it late
at night, etc." I saw very clearly what the installer reported. It said one thing on 
the screen and did something different. I wasn't blind, drunk, or sleepy; kanotix 64
showed an installation to hda3, and installed to hdb3. 
**End Rant**
 I spent yesterday going over my hardware, but not being a technician I can't
rule out a hardware problem. I tried the kanotix home site and forum, but so far
no replies. Any idea what could have happened? I miss my breezy 64; it was 
working like a thoroughbred :cry:

---

### Post by taurus on 2006-03-27
If kanotix installed itself on /dev/hdb3, then there is nothing you can do to recover your Ubuntu since it already formatted the partition before it installed on it!!!  I am not sure whether that's a bug in the installer of Kanotix but I doubt it...  That's why peole keep saying to back up your stuff before you install anything on your machine even though you intend to install it somewhere else!

---

### Post by Lucho on 2006-03-27
I know that the installer reformats the partition first; that's why I was so ticked
off at Kanotix 64. Fortunately, all my data is on a different partition. The only
data I lost was some gnome and kde themes- no big deal. 
  I can't rule out a bug in the installer. I'm looking into whether my cd is a
release candidate or the final version ( stupid me, I forgot to write it on the cd).
Right now I'm still considering a hardware issue, even though everything SEEMS
to be running 100%.

---

### Post by TrailerTrash on 2006-03-27
Ive had Kanotix hose my Windows partition. Ive had Vector hose my Windows partition. Ive had Slackware to hose my Windows Partition. Ive had ARK to hose ALL partitions. And last, ive had Yoper to hose my Windows partition. Yes i do know what im doing (most of the time).](*,)

---

### Post by Lucho on 2006-03-27
So you`ve had various linux distros hose your Windows partition. And you consider this
a bad thing? :twisted: :twisted: 

  Sorry, I couldn't resist.

---

### Post by taurus on 2006-03-27
[QUOTE=Lucho]So you`ve had various linux distros hose your Windows partition. And you consider this
a bad thing? :twisted: :twisted: 

  Sorry, I couldn't resist.[/QUOTE]
I couldn't even get Linux to hose my Windows partition because I DON'T have Windows partition on my machines...  ;)

---

### Post by mstlyevil on 2006-03-27
[QUOTE=taurus]I couldn't even get Linux to hose my Windows partition because I DON'T have Windows partition on my machines...  ;)[/QUOTE]

What the heck is Windows? :rolleyes:

---

