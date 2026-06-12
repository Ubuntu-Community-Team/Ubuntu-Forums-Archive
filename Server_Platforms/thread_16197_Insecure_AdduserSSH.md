---
title: "Insecure Adduser/SSH ?"
date: 2005-02-19
forum: Server Platforms
---

### Post by Slay3r on 2005-02-19
I just set SSH up on Ubuntu and made a new account via adduser from another system and i noticed that user can access and get info from any other users home dir, a few people talked about this on IRC also and the security seems very lame.
So is this something you have to edit yourself to change "default permissions" and if so how or is it something that was missed on the latest build?

---

### Post by daniels on 2005-02-20
If you're giving an account on your machine to someone you don't trust, then this is a horrendously bad idea anyway.  You can make a directory called 'private' and restrict access to it to just yourself, if you like; personally, the only people with accounts on my machines are people that I would trust not to poke around my home directory, and I wouldn't mind if they did anyway.

---

### Post by joobuntjoo on 2005-02-20
Isn't that reverse thinking though, as thats probably one of the reasons its an horrendous idea, when it shouldn't be? (Or does ubuntu kinda get around that by declaring itself to be a single user workstation?)

Linux is typically a multiuser o.s, I must admit it sounds a little odd to have a feature which is pretty standard on thousands of boxes out there and say its a horrendous idea.

Surely it would just be simpler to have rwx------ as default on any user created ? (If its considered a bad idea to addusers, thats even more reason to have it set as that!!)

---

### Post by daniels on 2005-02-20
If your home directory was rwx------, you could not have a user directory on a web server (e.g. foo.bar/~user), because Apache could not traverse your home directory to read public_html.  This and the fact that people generally want to share files with other users, contribute to this.  If you want private files, then just make a private directory that's rwx------ under your home directory.

If you're adding a user you assume to be hostile to your machine, then the next security vulnerability that comes around could quite possibly be root, at which point having a rwx------ directory wins you nothing.  I'm not saying it's not a good idea, but just reiterating that you should probably reconsider who you give accounts to if you're thinking about this sort of thing.

---

### Post by joobuntjoo on 2005-02-20
Hmm you can add access to a public_html folder without giving read access on all other files to anyone in a home dir though, so not really convinced, but nm.

Still seems like reverse thinking for me (but thats just me really). Standard should be private unless made public, not public unless made private. Thats just my philosophy though. Not really sure about the "people generally want to share" thing, I need to meet more people like that hehe.

However I do think its probably more of a case that I'm coming from one background (heavily secure), whereas ubuntu is coming from a solid desktop, generally single user setup type thing (and does a good job too). Just was a little taken aback at first, but I can understand it more I think about it for that.

---

### Post by Slay3r on 2005-02-20
im with joobuntjoo's post i do belive something should be secure not public then secured if/when needed, but stepping away from the question that i posted im getting confused to what Ubuntu actualy is.

1) Backup system ?

2) Singal user system ?

3) Multi user system ?

Although any of the above can be done with some tweaking what is Ubuntu advertised to be ?

---

### Post by joobuntjoo on 2005-02-21
Slowly getting a bit more time to get used to it on my laptop (and tbh only distro which works 1st time on it fully installed (even my pcmcia usb2 card which won't even work on xp hehe), fedora, debian etc all had problems. So in limited time I've had chance on it, I'd say definitely geared towards a complete, working, clean, no need to mess about with odd options, single user desktop setup primarily. I.e no option (I think, might be somewhere but not obvious) to not install gnome etc.  So deffo appears to be aimed at that rather than server, backup end. 

Probably worth reading some of the stuff on the webbie as it gives an idea too.

---

