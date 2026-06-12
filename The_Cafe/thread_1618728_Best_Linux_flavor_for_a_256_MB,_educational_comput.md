---
title: "Best Linux flavor for a 256 MB, educational computer"
date: 2010-11-11
forum: The Cafe
---

### Post by ndefontenay on 2010-11-11
Hi guys,

I'm still working for an association that tries to teach people things like "using a computer" (internet, office and the like for adults, and discovery for kids with stuff like gcompris.

I've just been told by someone from that association that they had 800 computers with 256MB on which he tried to install linux ubuntu but it was too slow.

Do you guys think it would be possible to install ubuntu with a different GUI or do I need to install a complete different flavor of ubuntu on it in order for those machines to work decently?

---

### Post by holiday on 2010-11-11
> **ndefontenay said:**
> Hi guys,

I'm still working for an association that tries to teach people things like "using a computer" (internet, office and the like for adults, and discovery for kids with stuff like gcompris.

I've just been told by someone from that association that they had 800 computers with 256MB on which he tried to install linux ubuntu but it was too slow.

Do you guys think it would be possible to install ubuntu with a different GUI or do I need to install a complete different flavor of ubuntu on it in order for those machines to work decently?

Google on linux system requirements. Ubuntu may not be your best choice. 256 is tiny, but Linux has run on that.

You may have to dig into archived versions, but once you find one you can build it to the association's specs and install it to all the machines. 

Sounds like a really worthwhile project. Good luck with it.

---

### Post by Khakilang on 2010-11-11
> **ndefontenay said:**
> Hi guys,

I'm still working for an association that tries to teach people things like "using a computer" (internet, office and the like for adults, and discovery for kids with stuff like gcompris.

I've just been told by someone from that association that they had 800 computers with 256MB on which he tried to install linux ubuntu but it was too slow.

Do you guys think it would be possible to install ubuntu with a different GUI or do I need to install a complete different flavor of ubuntu on it in order for those machines to work decently?

Have you try Lubuntu? It's pretty lightweight.

---

### Post by TNT1 on 2010-11-11
You will struggle a bit with only 256 RAM and edubuntu. I'd look at something like puppy (which has some good educational stuff, dunno if it has gcompris like anything though) Or try antiX, which has educational suites, and some good Gcompris like stuff. I have only tried Edubuntu and Gcompris on a min 512 machine.

---

### Post by ndefontenay on 2010-11-11
Thanks for the advice guys.

I'm just coming back from a talk with the general director of the association to see their expectations and their needs.

It looks like the association is totally open to Ubuntu. 
They have 40 centres accross the island but not all with computers.
out of those, 2 have computers:
1) A centre with brand new machines financed by embassies of some wealthy countries (not giving names here). Those machines belong wholly to them and they are new so Edubuntu is totally going on it.
2) They have partnered with another computer centric educational organization for the 2nd centre. Except this computer centric organization just partnered last year with A big software company that specializes in desktop computing and is not really good on servers either (Not naming either).

My action has 3 aspects:
1) Replace the pirated windows with Edubuntu for centres that has no legal issues
2) Provide training and a proper administration infrastructure (such as centralize the admin passwords to the HQ) for the maintenance and installation (when required) of those ubuntu machines
3) Help develop a training program for computer litteracy.

The 800 low spec companies belong to the computer centric organization so they are not totally tied to $$oz.

Lots of fun. 

I will try the different flavors mentioned here for the low spec machines :)

A no GUI linux always works well but doesn't achieve much in term of desktop experience!

---

### Post by NightwishFan on 2010-11-11
If you are a moderately skilled Debian administrator a custom Ubuntu or Debian might do the trick. For Ubuntu just use the alternate CD and install a command line only system, then apt-get what you need. XFCE/LXDE/Fluxbox etc.. Then add all the apps you want, being a bit conservative. Once you know everything works well; I believe there are some tools to make a custom image of an install, then you can use this image to put your customized system on alternate machines.

Also, if you have multiple users on a single install (users as in usernames). You can add custom config files to /etc/skel. Place them exactly how they would in a users home folder, and this will change the defaults of every new user. (I am about 90% though I have not done this myself)

---

### Post by P4man on 2010-11-11
You might consider turning those machines in to thin clients if each center has a computer powerful enough to act as server. That would make maintenance a lot easier (once set up properly) and system requirements for the clients would be close to nihil.

Alternatively, lubuntu has already been mentioned, I think that ought to work although its still close to the minimum. You might have better luck with peppermint os (ubuntu based).

---

### Post by ndefontenay on 2010-11-11
That thin client idea is pretty good but it does require a powerful enough server.

Also, keep in mind, I have 800 machines! I need to be able to industrialize that process. How do I go about doing that? Can I install linux from a command line from an image over a network or something along that line?

Also skill wise, I'm decent. Whatever has to be done, it will be done. 
I can write scripts in bash for whatever I need.
I'm looking for the best solution at the moment to deploy this easily.

Giving a username per person is really hard in this environment. There's no such thing as a Domain controller. Kids can work on a different PC. What we are going to do, is create just a user account and write the username and password on the whiteboard. Same user, same password for every machines. In fact, anybody coming in should be able to access it easily without asking.

It's good to have a sudoer user known only to the admins everyone else will be a guest.

I've installed Ubuntu a lot now but usually the option "login without asking for a password" defaults with the sudoer account.
Is there a way to change that to a different user?

That way, I turn on the machine, it logs in as user guest. I then log out, type the sudoer account and password and do whatever I need to do.

---

### Post by Paqman on 2010-11-11
The DE doesn't really matter, you can get Gnome down to about 100MB usage if you just install gnome-core only. What will scupper you is the apps. Take a look at what apps you want to run and what dependencies they have and make you choice of DE based on that, not the other way around.

---

### Post by koleoptero on 2010-11-11
Linux Mint Debian Edition.

Lubuntu on computers used to teach people? I think not. It would work great but lxde not a good starting place for people to learn.

---

### Post by NightwishFan on 2010-11-11
In this situation you might want to stick to something long supported and not a variant. Debian, Ubuntu Lucid, or CentOS. If you need to deploy professionally on 800 machines, you might want to talk to someone who has actually done that. Or go to the Ubuntu IRC and Askubuntu for help as well.

[http://askubuntu.com/](http://askubuntu.com/)
[https://wiki.ubuntu.com/IRC/ChannelList](https://wiki.ubuntu.com/IRC/ChannelList)

---

### Post by P4man on 2010-11-11
Out of curiosity, are those machine identical hardware wise, or is it a mix all sorts of (donated?) machines with widely different hardware?

Anyway, with 800 machines, you are going to have to think this through and test thoroughly, whatever distro you end up with. Once you have decided on your stack, there are several tools to do unattended deployements using PXE and/or you could remaster your own custom ISO (remastersys is one option there).

I dont know how this organisation works exactly, but I suppose there are mentors / teachers / sysadmins in each location? Do they have any knowledge of linux? Perhaps for the deployment you have to think differently here as in a typical corporation. If these people are new to linux themselves, you;ll have to teach them. Teaching them to install and setup ubuntu might be a good first step to introduce them to the OS. Having 20 people test a livecd and install 40 computers each would be madness in a typical corporate environment but could make some sense here.

---

### Post by Shining Arcanine on 2010-11-11
> **ndefontenay said:**
> Hi guys,

I'm still working for an association that tries to teach people things like "using a computer" (internet, office and the like for adults, and discovery for kids with stuff like gcompris.

I've just been told by someone from that association that they had 800 computers with 256MB on which he tried to install linux ubuntu but it was too slow.

Do you guys think it would be possible to install ubuntu with a different GUI or do I need to install a complete different flavor of ubuntu on it in order for those machines to work decently?

Sabayon Linux is probably a better option than Ubuntu Linux for these systems:

[http://www.sabayon.org/](http://www.sabayon.org/)

By the way, you can do a tarball of it, format each computer's drive appropriately, install grub and unpack the tarball on each directory. Sabayon Linux's parent distribution is Gentoo Linux and this is known as a stage 4 tarball on Gentoo Linux. There are instructions available for doing that online:

[http://en.gentoo-wiki.com/wiki/Custom_Stage4](http://en.gentoo-wiki.com/wiki/Custom_Stage4)

Some minor changes might be needed to accommodate Sabayon (e.g. there might be no need to install the portage tree). You could ask the Sabayon people about those.

---

### Post by jhsu802701 on 2010-11-11
Try antiX Linux.  No other distro has its unique combination of speed, superior repository (Debian compatible), AND user-friendliness.  If hardware requirements are an issue, do not count on Ubuntu or any distro based on Ubuntu.  Ubuntu has a record of steadily increasing requirements.  I expect this continue for Ubuntu and for any distro based on Ubuntu.  Ubuntu has its merits, but running on a 10-year-old computer is NOT one of them.

---

### Post by snowpine on 2010-11-11
Definitely the perfect situation for Thin Clients.

[http://sourceforge.net/apps/mediawiki/ltsp/index.php?title=Ltsp_SuccessStories](http://sourceforge.net/apps/mediawiki/ltsp/index.php?title=Ltsp_SuccessStories)

---

### Post by TheNosh on 2010-11-11
Puppy Linux is awesome and small. I've used in on 256 mb of RAM before.

---

### Post by P4man on 2010-11-11
> **snowpine said:**
> Definitely the perfect situation for Thin Clients.

[http://sourceforge.net/apps/mediawiki/ltsp/index.php?title=Ltsp_SuccessStories](http://sourceforge.net/apps/mediawiki/ltsp/index.php?title=Ltsp_SuccessStories)

Thats an interesting page. I cant understand how low the requirements for the server seem to be. Can someone explain how you can serve 50+ clients with a graphical GUI, firefox, OO, etc with a single server with 2 to 4 GB Ram? I can understand CPU requirements are relatively low but how does it work with so little ram per client?

---

### Post by themarker0 on 2010-11-11
Hmm. "Lubuntu" would be my vote. It looks similiar to windows if anyone else uses it, and its fast. No issue.

---

### Post by cascade9 on 2010-11-12
If you reallty wanted to run ubuntu then a minimal install would be easiest way to get a 256MB machine running nicely. 

I'd just run a major distro (probably debian or slackware) with Xfce. Lxde isnt worth it IMO, and some of the other light DEs/WMs can be confusing to a lot of users. Xfce is pretty easy, farily light, and stable. 


> **Shining Arcanine said:**
> Sabayon Linux is probably a better option than Ubuntu Linux for these systems:

[http://www.sabayon.org/](http://www.sabayon.org/)

By the way, you can do a tarball of it, format each computer's drive appropriately, install grub and unpack the tarball on each directory. Sabayon Linux's parent distribution is Gentoo Linux and this is known as a stage 4 tarball on Gentoo Linux. There are instructions available for doing that online:

[http://en.gentoo-wiki.com/wiki/Custom_Stage4](http://en.gentoo-wiki.com/wiki/Custom_Stage4)

Some minor changes might be needed to accommodate Sabayon (e.g. there might be no need to install the portage tree). You could ask the Sabayon people about those.

Ahh, yes, the gentoo/sabayon cheer squad. 

Maybe later versions are better, but I found sabayon slow and sluggish on low ram machines. Its wasnt that quick on much better machines either.....

---

### Post by hhh on 2010-11-12
I've never installed it, but Slitaz gets recommended a lot...
[http://www.slitaz.org/en/](http://www.slitaz.org/en/)
[http://distrowatch.com/table.php?distribution=slitaz](http://distrowatch.com/table.php?distribution=slitaz)
[http://www.slitaz.org/en/](http://www.slitaz.org/en/)

---

### Post by nothingspecial on 2010-11-12
You might want to read the "godfather of old low spec machines'" blog

[http://kmandla.wordpress.com/](http://kmandla.wordpress.com/)

Tons of tips and info on running linux on old computers.

---

### Post by ddnev45 on 2010-11-12
Z[enwalk will run on a system with 256 Mb RAM]("http://www.zenwalk.org/") (I installed it on an old laptop). [SalixOS]("http://www.salixos.org/wiki/index.php/Home") is a similar slackware-based distro.

I think you'd be better off with Debian rather than a variant like Ubuntu. Nothing against Ubuntu, it's just been my experience to get better performance on low-end machines from Debian.

---

### Post by Sylslay on 2010-11-12
Well if You don't need 800 pc with 256MB, just make
400 with 256MB and 200 with 512MBt :

Salx 6.2 is old but my best for speed distro I tryed.

Lubuntu is good choice,

But if You have no time to install it on every machmine,

Linux Mint LDME is Debian base, ready out of box for use with codec for multimedia etc.. same effet and less job. And is snapy too, for latest gnome desktop, I just tested on 8 GB usb steak as portable os.

Installation on USB Key

[http://ubuntuforums.org/showthread.php?t=1596497](http://ubuntuforums.org/showthread.php?t=1596497)
 
and is educational and portable.


And I clonned It to PC-Desktop with [COLOR="Blue"][SIZE="3"]clonezilla [/SIZE][/COLOR]and it works to,
20min for copy all OS from usb-key to desktop, all togheter with all settnigs.

---

### Post by Cpierce on 2010-11-12
My vote would be for Lubuntu as well. It works well on 256MB. I agree with the earlier comment that lxde is a little more complicated, but it does use less resources. Peppermint and Crunchbang are other options. 

I also agree with the clonezilla comment. Install Lubuntu on one of those 800 computers just the way you want it, then make a clonezilla image and away you go. Should only take 10-15 minutes per computer.

---

### Post by armageddon08 on 2010-11-12
Slitaz or Arch......Go for Arch

---

### Post by Gremlinzzz on 2010-11-12
puppy Linux just be sure to  unmute the speakers. for some reason they were muted on first boot. just go to terminal type in alsamixer use arrows to speakers press m to unmute.

---

### Post by The Real Dave on 2010-11-13
> **ndefontenay said:**
> 
Also, keep in mind, I have 800 machines! I need to be able to industrialize that process. How do I go about doing that? Can I install linux from a command line from an image over a network or something along that line?



You could use a [Clonezilla]("http://clonezilla.org/clonezilla-server-edition/") server, a cloning OS, which performs similar to Norton Ghost (but much better IMO)

---

