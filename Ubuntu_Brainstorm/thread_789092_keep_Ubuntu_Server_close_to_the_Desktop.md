---
title: "keep Ubuntu Server close to the Desktop"
date: 2008-05-10
forum: Ubuntu Brainstorm
---

### Post by songshu on 2008-05-10
just a feeling,

This is not about a specific application but just some taughts about the general heading of the Ubuntu Server Edition.

There is the idea i get that the server edition is for a big part focussing on getting Ubuntu in the data center, both development as marketing wise.

Maybe i'm wrong in the feeling that it is or that it is not a good idea, but for those willing to read....here it is.

Ubuntu started as a desktop project and is completely adjusted to the gnome release cycle, the complete 6 monthly rebuild is based on presenting this single environment in the best possible way presenting the user with a clean interface usable from the start with a sensible number of applications, one for each task, and with technically unskilled and average users in mind. To make it "just work"
That was a good idea and that focus was what made it shine compared to the other offerings around.
Many jumped on that bandwagon, including myself, the userbase grew, offspring happened with kubuntu, xubuntu, many others and the server edition itself,  expanding the ecosystem around Ubuntu.
Yet another good thing i would say helping out to fix bug #1.

But that particular release cycle seems not to be the most perfect environment for everything else, like for example the problems around the KDE environment LTS, altough they do a good job, they have to deal with an impossible situation.

For other reasons as the KDE example i think it is not suitable for the server edition either, offcourse being based on Debian gives it a great start and an advantage. But there is a reason i think that that Universal Operating System it is based on does not commit itself to a 6 monthly release cycle, if they would stick to a release date at all.

This has to do with there aim of bringing a stable release for all included packages, and being universal means there are a lot of them, and in my opinion to many to have those ironed out within 6 months.

So why try competing in the data center with big boys like Debian, Red Hat, SuSe and FreeBSD handled by technical skilled forces if your own release cycle alone is against you when trying to be universal without having enough time to fuel your spaceship. 

Not saying its all bad, cause it isn't, but i've encountered bugs in stable Ubuntu i would not ever see in stable Debian or FreeBSD.
As happy and convinced i personally am with ubuntu as a desktop solution, i use it with XFCE, there is no way i will consider Ubuntu to be my "all round hit me with all you got because i have a solution anyway" choice when it comes to server tasks.
Once again, this is my personal feeling and i might be wrong.

Ok, nice to be critical about somebody elses hard work, now move along....

Just wait...theres a constructive part as well here and if you managed to read to here you just as well read my view on how Ubuntu can further squash bug #1.

My suggestion is to keep the server edition close to the desktop, both in absolute distance as in user experience.
Not that it should delete everything else but i think there would be a great benefit when keeping the focus close to the original Ubuntu philosophy,
presenting the user with a clean interface usable from the start with a sensible number of applications, one for each task, and with technically unskilled and average users in mind. To make it "just work".

Personally i love the command line and i think its the best way to accomplish what i want, but i get the feeling that most (or at least a lot) do not share the experience, just checking out the server part on the ubuntu forums will show you the following thread.

poster 1:
hi all, 

i just downloaded and installed the server edition and i want to set up some file sharing, what do i do next?

poster 2:
you need to do 
apt-get install ubuntu-desktop
that will make it easier

poster 3:
no don't do that, do
apt-get install xubuntu-desktop
that is a lot lighter.

poster 4:
even better to do
apt-get install xserver-xorg xfce4 synaptic
that will make it really fast ;)


Not kidding here, just have a look.
And to be honest, when i stared at the command line for the first time and saw.
```
darkstar login:
```
for the first time i was lost as well, and if only something like the ebox-platform was available at the time my life could have been different, maybe i could have even done something usefull or spend my time becomming a famous actor or something, instead of spending most my time nowadays behind a black console.
And here i think the Ubuntu Server edition can make a difference

presenting the user with a clean interface usable from the start with a sensible number of applications, one for each task, and with technically unskilled and average users in mind. To make it "just work".

Many good things are being done in this field but i do not see this back in the official goals set by Ubuntu.
I think the server edition should have and advertise something as ebox as their default network solution, maybe something looking as good as zimbra as the default mail solution and asterisk now as the default telephone system...
These are just some examples but these packages are there and available,  all that needs to be done is to make them easy installable and advertised.

Focussing on this kind of offering basically leaves out the lucrative data center target, but then again, it would be closer to the already existing userbase and bug #1.  and i think ubuntu has a better chance competing to windows in the small office then against Debian in the data center.


But then again, maybe i'm wrong.

songshu

---

### Post by nakita on 2008-05-10
your dead right on the remark of the 4 posters. i just installed the server edition and am staring at the cli and asking now what. I am not afraid of the cli but where do i start in learning the commands to make things happen and work. I have been looking in the forums for hours now and have come to the conclusion of putting a gui on the server till i learn the cli commands and going cli only at a later date. I only want a webserver for family and friends and a couple of databases anyway.

---

### Post by danbh on 2008-05-10
I think you are asking for a longer release cycle than 6 months.  You realize then that new releases of software won't be included.  

Maybe you should try debian?  It has a stable branch, which basically has all old software, but it is very stable.  

For learning the CLI, would you check out a project idea I came up with?  
I posted it here: [http://ubuntuforums.org/showthread.php?t=630693](http://ubuntuforums.org/showthread.php?t=630693)

Anyway, take care.

---

### Post by songshu on 2008-05-10
> **danbh said:**
> I think you are asking for a longer release cycle than 6 months.  You realize then that new releases of software won't be included.  

Maybe you should try debian?  It has a stable branch, which basically has all old software, but it is very stable.  

For learning the CLI, would you check out a project idea I came up with?  
I posted it here: [http://ubuntuforums.org/showthread.php?t=630693](http://ubuntuforums.org/showthread.php?t=630693)

Anyway, take care.

first place i think your idea looks pretty good, i will have a look if i can learn a thing or two ;)

second, i'm not asking for a longer release cycle, just suggesting a smaller and balanced set of packages more suited to the already existent user base and complimenting the already strong desktop which also fits that exact recycle.

i have been using the CLI for about 8 years by now and i really love it, it just takes some time to learn it and that learning curve is pretty steep compared to the simple tasks some people would like to perform.

---

