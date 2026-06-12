---
title: "The reason Linux will never be popular......."
date: 2007-08-29
forum: The Cafe
---

### Post by liveforever on 2007-08-29
This isnt supposed to bash, its just a fact. You cannot appeal to the majority when installing something as simple as an equivilant to peerguardian is this nonsensical, I dont know if its meant to be this needlessly complicated to keep people from using it, but *snip*.

Installation for Moblock:

Installation & Usage.

Just untar somwhere.
To build MoBlock from sources just do

make

in the directory where you extracted it. If you want to compile using
the old libipq library you must edit the Makefile, on top of it you
will find detailed instructions.

The static version was compiled on Slackware 10.2 with gcc 3.4.5, if you
don't want to install the libnetfilter libraries try it, just rename it
to "moblock".

To start it just launch MoBlock-nfq.sh (if you use the new kernel
interface) or MoBlock-ipq.sh (if you use the old kernel interface) as root,
for example:

./MoBlock-nfq.sh &

By default it will load the block list from /etc/guarding.p2p and
will log its activity to ./MoBlock.log, you can edit the script if you
want to change them.
You can specify a whitelist of ports in the start script as explained
before.
If you want to use new p2p.pdb files change this line in the start script:

./moblock -p /etc/guarding.p2p MoBlock.log

into this:

./moblock -n /etc/p2p.p2b MoBlock.log

or if you want to use ipfilter.dat files:

./moblock -d /etc/ipfilter.dat MoBlock.log

To specify a NFQUEUE queue number:

./moblock -p /etc/guarding.p2p -q 5 MoBlock.log

To stop it:

kill -TERM <MoBlockPid>

While shutting down it will dump some stats to /var/log/MoBlock.stats
To obtain stats about blocked ranges while it's running:

kill -USR1 <MoBlockPid> # write stats to logfile
kill -USR2 <MoBlockPid> # write stats to /var/log/MoBlock.stats

** NEW: to reload the blocklist while MoBlock is running send to it the
HUP signal:

kill -HUP <MoBlockPid> # reloads blocklist and resets stats

Moreover when HUP or USR1 is received the log file will be reopened
to allow log file rotation.

.Credits.

- Thomas Niemann (thomasn at epaperpress.com) for the red/black trees
free implementation, used to store and search ip ranges. You can
find it at [www.oopweb.com](www.oopweb.com)
- Chris Lowth, developer of FTwall ([www.lowth.com/p2pwall](www.lowth.com/p2pwall)), i
took some code and ideas from his FTwall
- Andrew de Quincey (adq at lidskialf dot net) for regular expressions
and command line args patch
- Maximilian Mehnert (clessing at freenet dot de) for logfile rotation
patches, pid file creation, start script, fixes/files for debian packaging

Last Updated: 20/Mar/2006



Why cant someone come up ith an OS alternative for windows without making it *snip* complicated??? I cant be that hard for Linux to package their stuff in a userfreindly way.

Do all that or double click PG2.exe??? I know what I'd rather do, Linux is pretty and fast but no, XP is king. Sorry to offend, but you cannot argue with my logic.

---

### Post by ThrobbingBrain66 on 2007-08-29
Firstly, Moblock/Peer Guardian isn't an application that everyone uses or knows about.  Secondly, you apparently chose the "hard way" as I know there is a repo for Moblock 

*goes off to search for said repo*

The repo is right on the Moblock homepage, under the 'Get It!' heading:
[http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

Therefore, I would argue that installing Moblock and keeping it updated is easier than a Windows-style approach.

I just did argue with your logic, and I win:)

---

### Post by misfitpierce on 2007-08-29
Ummm you realize that its because moblock isnt officially being built anymore its just updated. Not only that but I highly doubt linux wont become popular because of a program to remove bad IP's. Your claim is completely wrong and dumb. :) Sorry

---

### Post by 23meg on 2007-08-29
> Sorry to offend, but you cannot argue with my logic.

Is your logic that because you weren't able to easily install one obscure piece of software, which for some reason isn't packaged for Ubuntu, Linux will never be popular? Not that I couldn't, but I wouldn't argue with it; it's not worth my time.

*yawn*

*submits bug to get Moblock packaged*

*(Edit: It seems someone already picked it up: [https://bugs.launchpad.net/ubuntu/+bug/109822](https://bugs.launchpad.net/ubuntu/+bug/109822))*

---

### Post by Het Irv on 2007-08-29
No your logic on that point is sound, sometimes things can be a tad retarded, but I would gladly put up with 5 mins of frustration and have all of the things that Linux has like Package Manager and oh.. yeah SECURITY.

---

### Post by cybrid on 2007-08-29
If you  want to compile it, it's your choice; don't blame linux for it; besides, installing a .deb is a no-brainer.

---

### Post by liveforever on 2007-08-29
> **ThrobbingBrain66 said:**
> Firstly, Moblock/Peer Guardian isn't an application that everyone uses or knows about.  Secondly, you apparently chose the "hard way" as I know there is a repo for Moblock 

*goes off to search for said repo*

The repo is right on the Moblock homepage, under the 'Get It!' heading:
[http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

Therefore, I would argue that installing Moblock and keeping it updated is easier than a Windows-style approach.

I just did argue with your logic, and I win:)


That'd be lovely if the links worked but they are dead, hard was the only way.

---

### Post by liveforever on 2007-08-29
> **cybrid said:**
> If you  want to compile it, it's your choice; don't blame linux for it; besides, installing a .deb is a no-brainer.

Show me a deb install and I'll shout from the rooftops but there arenty any.

---

### Post by Paul820 on 2007-08-29
haha, i love it when you guys find the solution in seconds and prove the op complaining about linux that he/she is wrong. :lolflag:

People need to read and search a bit more.

---

### Post by liveforever on 2007-08-29
> **23meg said:**
> Is your logic that because you weren't able to easily install one obscure piece of software, which for some reason isn't packaged for Ubuntu, Linux will never be popular? Not that I couldn't, but I wouldn't argue with it; it's not worth my time.

*yawn*

*submits bug to get Moblock packaged*

*(Edit: It seems someone already picked it up: [https://bugs.launchpad.net/ubuntu/+bug/109822](https://bugs.launchpad.net/ubuntu/+bug/109822))*

Obscure??? An IP blocker?? One of the most important things you can have on a computer??? What else is the internet for than downloading musci and films????

---

### Post by BoyOfDestiny on 2007-08-29
> **liveforever said:**
> Show me a deb install and I'll shout from the rooftops but there arenty any.

Double click any deb file.

---

### Post by 23meg on 2007-08-29
> **liveforever said:**
> That'd be lovely if the links worked but they are dead, hard was the only way.

No, it works, but it's a Debian repo. It should be packaged in Ubuntu, so that you can install it via a package management tool (Synaptic, APT, Aptitude, etc.).

---

### Post by liveforever on 2007-08-29
> **Paul820 said:**
> haha, i love it when you guys find the solution in seconds and prove the op complaining about linux that he/she is wrong. :lolflag:

People need to read and search a bit more.

Noones found a solition, they've just linked me dead links thats solved nothing.:confused:

---

### Post by Nekiruhs on 2007-08-29
> **liveforever said:**
> That'd be lovely if the links worked but they are dead, hard was the only way.
They ARENT links.
Heres how to install:
```
gksudo gedit /etc/apt/sources.list
```
Add the lines:
```
deb http://moblock-deb.sourceforge.net/debian unstable main
deb-src http://moblock-deb.sourceforge.net/debian unstable main
```
Then:
```
gpg --keyserver subkeys.pgp.net --recv DEDA0559  && gpg --export --armor DEDA0559 | sudo apt-key add -
```
Finally:
```
sudo apt-get update && sudo apt-get install moblock-nfq
```
Done.

---

### Post by Mazza558 on 2007-08-29
> **liveforever said:**
> Show me a deb install and I'll shout from the rooftops but there arenty any.

If you look a few posts up, you'll see that someone's already working on packaging it. :)

---

### Post by 23meg on 2007-08-29
> **liveforever said:**
> Obscure??? An IP blocker?? One of the most important things you can have on a computer??? What else is the internet for than downloading musci and films????

It's not the only IP blocker; it's (apparently) the only one compatible with Peerguardian files, and you seem to have needed that particular functionality. 

You're misplacing the problem. The problem isn't that "things are hard to install in Linux"; it's that this particular piece of software hasn't got packaged for Ubuntu (it's in progress).

---

### Post by liveforever on 2007-08-29
Hmmm why are they not links??? Why not make things easy for people, and thanks for that but heres what the command line told me:

Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Super userfreindly if you ask me.

---

### Post by Lord Illidan on 2007-08-29
Dead links? They work fine here..or are you blocking too many IPs?

To install it, just go on System -> Software Sources -> Third Party -> Add Repo and add these lines one after the other :

```
deb http://moblock-deb.sourceforge.net/debian unstable main

deb-src http://moblock-deb.sourceforge.net/debian unstable main
```

Then, exit the app, the repositories are reloaded, and you can install 
from synaptic. Also, it will be updated regularly.

---

### Post by liveforever on 2007-08-29
> **Mazza558 said:**
> If you look a few posts up, you'll see that someone's already working on packaging it. :)

So what can I use in the meantime, that installs with me having to become a programmer????

---

### Post by Lord Illidan on 2007-08-29
With that attitude, you are going nowhere.

The install instructions are on this page : [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

---

### Post by Lord Illidan on 2007-08-29
> **liveforever said:**
> So what can I use in the meantime, that installs with me having to become a programmer????

Without you having to become a programmer? God, do you know what a programmer is?

---

### Post by Nekiruhs on 2007-08-29
> **liveforever said:**
> Hmmm why are they not links??? Why not make things easy for people, and thanks for that but heres what the command line told me:

Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Super userfreindly if you ask me.
Check my post I added a few lines that might help.

---

### Post by liveforever on 2007-08-29
> **Lord Illidan said:**
> Dead links? They work fine here..or are you blocking too many IPs?

To install it, just go on System -> Software Sources -> Third Party -> Add Repo and add these lines one after the other :

```
deb http://moblock-deb.sourceforge.net/debian unstable main

deb-src http://moblock-deb.sourceforge.net/debian unstable main
```

Then, exit the app, the repositories are reloaded, and you can install 
from synaptic. Also, it will be updated regularly.

How can I block IPs??  I havent got an IP blocker, thats my problem, and what is a repo?? Cant see that in the software sources.

---

### Post by picpak on 2007-08-29
You want double-click? Here you go:

[moblock-nfq_0.8-15_i386.deb](http://moblock-deb.sourceforge.net/debian/dists/unstable/main/binary-i386/net/moblock-nfq_0.8-15_i386.deb)

it's straight from that repo. If it doesn't work, you probably have too many IPs blocked or something.

---

### Post by ThrobbingBrain66 on 2007-08-29
You don't know what a Repository is?

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

EDIT: Actually, I see no reason for this thread to continue.  Reported as needing to be closed.

---

### Post by liveforever on 2007-08-29
> **Lord Illidan said:**
> Without you having to become a programmer? God, do you know what a programmer is?

I dont want to use a thing like dos, I want to doubkle click and thats that, done. Thats not too much to ask is it???

---

### Post by Nekiruhs on 2007-08-29
> **liveforever said:**
> I dont want to use a thing like dos, I want to doubkle click and thats that, done. Thats not too much to ask is it???
Stop arguing and read the posts by the people trying to *help* you. The terminal is not dos, its bash. I'm a programmer and I don't need the terminal except when helping people.

---

### Post by Lord Illidan on 2007-08-29
> **liveforever said:**
> I dont want to use a thing like dos, I want to doubkle click and thats that, done. Thats not too much to ask is it???

No, it's not. Check out a post above, and you can double click all you like. But Linux is not Windows...I bet you can't update your whole Windows system - with most of the programs in it...with 1 or 2 clicks?

---

### Post by 23meg on 2007-08-29
> **liveforever said:**
> I dont want to use a thing like dos, I want to doubkle click and thats that, done. Thats not too much to ask is it???

No it's not, but [SIZE="6"]in this particular case [/SIZE], you'll have to wait for it to get packaged in Ubuntu to be able to do that. Sorry for the inconvenience.

---

### Post by liveforever on 2007-08-29
> **picpak said:**
> You want double-click? Here you go:

[moblock-nfq_0.8-15_i386.deb](http://moblock-deb.sourceforge.net/debian/dists/unstable/main/binary-i386/net/moblock-nfq_0.8-15_i386.deb)

it's straight from that repo. If it doesn't work, you probably have too many IPs blocked or something.

You are the king of kings Where the hell did you find that?? I've been searching for hours, as you can probably tell from my frustration. Also how can I block IPs?? I havent installed moblock yet.

---

### Post by K.Mandla on 2007-08-29
I'm closing this one. The issue was solved several times over, and rehashing the principles behind the repository system or whether one operating system's installation process is easier than another's ... anyway, they are repeated ad nauseum elsewhere on the forum.

---

