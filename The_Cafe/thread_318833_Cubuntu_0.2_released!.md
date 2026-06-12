---
title: "Cubuntu 0.2 released!"
date: 2006-12-14
forum: The Cafe
---

### Post by alecjw on 2006-12-14
I'm sorry i skipped 0.1 - it did exist, but i couldn't get a repository going in time to release it.

Cubuntu is a fully featured (or as fully featured as you can get without a desktop environment) command line based Ubuntu derivative. It includes web browsers (lynx and links2), e-mail clients (mutt and elmo), a media player (cplay), an RSS reader (raggle) and some games amongst other things.

You will need an Ubuntu command line/server installation.
You can get cubuntu by adding the following line to your sources.list:
deb [http://alecjw.zexxo.net/apt](http://alecjw.zexxo.net/apt) edgy main
You then need to enable the ubuntu universe and (probably, but I'm not sure) multiverse repositories.
Then run these commands:
sudo aptitude update
sudo aptitude -y upgrade
sudo aptitude -y install cubuntu

---

### Post by meng on 2006-12-14
Cool! Kudos.

---

### Post by dbbolton on 2006-12-14
i wish i were knowledgable enough to use that. i can't imagine how efficient it must be.

---

### Post by tbroderick on 2006-12-14
> **alecjw said:**
> I'm sorry i skipped 0.1 - it did exist, but i couldn't get a repository going in time to release it.

Cubuntu is a fully featured (or as fully featured as you can get without a desktop environment) command line based Ubuntu derivative. It includes web browsers (lynx and links2), e-mail clients (mutt and elmo), a media player (cplay), an RSS reader (raggle) and some games amongst other things.


So that means there are three console browsers installed by default? w3w, lynx and links2?

---

### Post by 3rdalbum on 2006-12-15
I had this idea ages ago, but I never got around to implementing it. Congratulations!

A quick question: Does it come with Twin?

---

### Post by alecjw on 2006-12-15
> **tbroderick said:**
> So that means there are three console browsers installed by default? w3w, lynx and links2?

Yeah. Some people wanted links2 (mainly me) and some people wanted lynx. I dunno about w3w, is that a depeendency of one of them?

---

### Post by spockrock on 2006-12-15
will this play my videos as ascii art??

---

### Post by xopher on 2006-12-15
> will this play my videos as ascii art??

:D Hopefully

---

### Post by spockrock on 2006-12-15
I know vlc does that, but if cubuntu does that would be the most bad a** thing ever....

---

### Post by Henrik on 2006-12-15
Cool! Have you though about including accessibility tools like eSpeak, Festival, speakup, Esmacspeak? Blind people might find this derivative quite useful. Some use gnome with Orca but many prefer the text interface. Does it run as a live CD?

Also see: [http://oralux.org/](http://oralux.org/)

---

### Post by DirtDawg on 2006-12-15
How big is the final distribution?

---

### Post by alecjw on 2006-12-15
> **spockrock said:**
> will this play my videos as ascii art??

No it doesn't, but if you can tell me a program which can do that, it might get in to version 0.3.

---

### Post by alecjw on 2006-12-15
> **DirtDawg said:**
> How big is the final distribution?

When you install the metapackege, it has to downlad about 60mb of packages, which somehow become 130mb when unpacked.

---

### Post by alecjw on 2006-12-15
> **Henrik said:**
> Cool! Have you though about including accessibility tools like eSpeak, Festival, speakup, Esmacspeak? Blind people might find this derivative quite useful. Some use gnome with Orca but many prefer the text interface. Does it run as a live CD?

Also see: [http://oralux.org/](http://oralux.org/)

Nope, I haven't, but it certainly sounds like a good idea. I'll look into it.

And so far, it's just a metapackage, no CD's

> **3rdalbum said:**
> A quick question: Does it come with Twin?

No. I'd never heard of it until now, but as with Henrik's suggestion, I'll look into it.

---

### Post by Rhapsody on 2006-12-15
> **alecjw said:**
> Yeah. Some people wanted links2 (mainly me) and some people wanted lynx. I dunno about w3w, is that a depeendency of one of them?

I believe he/she was referring to [w3m](http://w3m.sourceforge.net/). It's the only text-based browser listed on the [W3C XHTML media type test page](http://www.w3.org/People/mimasa/test/xhtml/media-types/results), though tests on my [own site](http://pointlessness.freehostia.com/) has indicated that Links2 has at least some support as well.

---

### Post by 23meg on 2006-12-15
> **alecjw said:**
> No it doesn't, but if you can tell me a program which can do that, it might get in to version 0.3.
Mplayer with the aa and caca output modules can do it.

---

### Post by tbroderick on 2006-12-15
> **alecjw said:**
> Yeah. Some people wanted links2 (mainly me) and some people wanted lynx. I dunno about w3w, is that a depeendency of one of them?

w3m should be included in any Ubuntu install cause it's part of ubuntu-standard meta package.  I was just wondering why there was three browsers. Not a big deal.

---

### Post by fuscia on 2006-12-15
no love for elinks? i've always found it easier to get into sites like yahoo, which can be a pain in the butt for text browsers.

---

### Post by K.Mandla on 2006-12-17
> **23meg said:**
> Mplayer with the aa and caca output modules can do it.
Yup. Nothing beats watching The Matrix in ASCII.

[http://www.oreilly.com/pub/h/4441](http://www.oreilly.com/pub/h/4441)

It's worth installing mplayer just for that. 8)

---

### Post by Redlance on 2006-12-17
ZOMG!! Someone beryl this distro ;D
just kidding :D
<hides>

---

### Post by DirtDawg on 2006-12-23
What happened to this project? Is it on break for the Holidays or is it DOA?

---

### Post by alecjw on 2006-12-24
> **DirtDawg said:**
> What happened to this project? Is it on break for the Holidays or is it DOA?

0.3 will be released as soon as i can find a way of getting dpkg-scanpackages to work :D

---

### Post by zgornel on 2006-12-24
Great. Finally something for a 386 :D

---

### Post by malaprohibita on 2006-12-24
I've just got to ask: what games are available in this release?  :twisted:

---

### Post by alecjw on 2006-12-24
> **malaprohibita said:**
> I've just got to ask: what games are available in this release?  :twisted:

In version 0.2, nethack and dopewars. 0.3 will have empire too.

---

### Post by DirtDawg on 2006-12-24
> **alecjw said:**
> In version 0.2, nethack and dopewars. 0.3 will have empire too.

That reminds me, I found a package called [BSD games]("http://packages.ubuntu.com/edgy/games/bsdgames") that includes a text version of tetris, among other things. I haven't tried it yet, but it looks like a good fit. Thought you'd like to know.

---

### Post by alecjw on 2006-12-24
> **DirtDawg said:**
> That reminds me, I found a package called [BSD games]("http://packages.ubuntu.com/edgy/games/bsdgames") that includes a text version of tetris, among other things. I haven't tried it yet, but it looks like a good fit. Thought you'd like to know.

Cool. Thanks.


Edit: BSD Games has been added in 0.3, which has just been released.

---

### Post by malaprohibita on 2006-12-24
Cubuntu is such a great idea, and I'm experimenting with Raggle as we speak.  I hadn't even heard of it until I came across this thread.  Good stuff!

---

### Post by K.Mandla on 2006-12-29
Hmm. "Temporary failure resolving alecjw.zexxo.net" ... is it down or moved?

---

### Post by alecjw on 2006-12-29
> **K.Mandla said:**
> Hmm. "Temporary failure resolving alecjw.zexxo.net" ... is it down or moved?

I think that the server's temporarily down. I might be getting hosting on devubuntu.com soon.

---

### Post by DecIRC on 2006-12-30
Don't forget to add the wonderfull irssi
The browser is not w3w but w3m

There is also a nice bittorrent client (don't know if it's include in w3m but when I click on a torrent I have a nice torrent ascii interface)

And gftp-text also.

When I'm at work the only contact with my home computer is ssh.

And as there are a lot of restriction from office (no IRC, a lot of sites blacklisted) I'm afficionados from console.

I have also hellanzb to download newsgroups.  But there is no cool interface. (a web one, but not a console one)

Regards
cEd

---

### Post by dotsi on 2007-02-26
So, how does it actually work? I mean, if I install it, does it remove all the packages it doesn't need and preserve only the ones necessary, thus keeping the system truly minimal? That's my intention for the current Dapper install on another computer.

---

### Post by K.Mandla on 2007-03-06
Hmm. Is this link moved or is there a new host?

---

### Post by El Rogueo on 2007-10-08
Has there been any updates about the status of the server or a way to get it other than through the zexxo.net address?

Also, I see it's been said that 0.3 is out, but I only see 0.2. Can anyone tell me where it is?

---

### Post by djringjr on 2008-02-17
We are also trying to get a keyboard driven distro for the blind!

[http://www.murga-linux.com/puppy/viewtopic.php?t=24571&sid=284fe90df919d1327ce503b6dd35f63b](http://www.murga-linux.com/puppy/viewtopic.php?t=24571&sid=284fe90df919d1327ce503b6dd35f63b)

Any help is requested especially from those who have brailler terminals.

Best

David Ring

---

### Post by ek0892 on 2012-04-24
Hi, The New project Cubuntu Is ready.  This version is different, this is Not Console version but Cinnamon version .

The New project Cubuntu Is ready.  100% Ubunut with Cinnamon Gnome and Extras..

Cubuntu enjoy the best of Cinnamon with Ubuntu, Gnome, and Unity + 

With Cubuntu well you will not be lost is a 100% Ubuntu Ultimate Edition.

We added the best without remove. 

My priority was to keep completeness of Ubuntu, do not remove this in order to keep the compatibility, stability and the updates that have made its reputation. We have added your choice of graphical interface between Unity, Gnome, Cinnamon, and many applications update: Chrome, Geany, Radiotray, virtualbox, Skype, VLC, Audacity, Tweak, Filezilla, synaptic + many codecs, MP3, Divx, Flash, etc. .. 

With Cubuntu, you can use all applications designed for Ubuntu Debian and without limitation, software, Ubuntu repositories are enabled by default, you can enjoy all the updates of ubuntu. Cubuntu 12.04-5 RC

The Website is French, Bu Cubuntu is multi-languages : [http://www.cubuntu.net](http://www.cubuntu.net) 

Note : 
Cubuntu n'est pas une variante comme peut l'être Xubuntu ou Kubuntu ou Lubuntu.
Une variante est assez différente de l'original , applications différentes, dépots différents, etc.
Cubuntu c'est un extra  édition "Ultimate", car 100% d'ubuntu original est dans Cubuntu.

_____________________________

En français :

Cubuntu profitez du meilleur d'Ubuntu avec Cinnamon, Gnome, Unity et bien +
Avec Cubuntu vous ne serez pas perdu, c'est 100% Ubuntu dans une édition Ultimate, nous avons ajouté le meilleur sans rien retirer.

Notre priorité a été de garder l'intégralité d'Ubuntu, ne rien retirer, cela afin de garder la compatiblité, stabilité et les mises à jours qui ont fait sa réputation.

Nous y avons ajouté le choix de votre interface graphique entre Unity , Gnome, Cinnamon, et de nombreuses applications mise à jour :  Chrome, Geany, Radiotray, virtualbox, skype, Vlc,  Audacity, Tweak, Filezilla, synaptic + de nombreux codecs, Mp3, Divx, Flash, etc..

Cubuntu is not a variant can be as Xubuntu or Kubuntu or Lubuntu. 
A variant is quite different from the original, different applications, different deposits, etc.. 
Cubuntu is an extra edition "Ultimate" because 100% of original ubuntu is in Cubuntu.

The Website is frensh by Cubuntu is multi-language [here]("http://chromeboot.fr/?q=node/8")

Note : 
Cubuntu n'est pas une variante comme peut l'être Xubuntu ou Kubuntu ou Lubuntu.
Une variante est assez différente de l'original , applications différentes, dépots différents, etc.
Cubuntu c'est un extra  édition "Ultimate", car 100% d'ubuntu original est dans Cubuntu.

---

### Post by ek0892 on 2012-04-24
The New project Cubuntu Is ready.  This version is different, this is Not Console version but Cinnamon version .

---

### Post by Elfy on 2012-04-24
Old thread closed.

---

