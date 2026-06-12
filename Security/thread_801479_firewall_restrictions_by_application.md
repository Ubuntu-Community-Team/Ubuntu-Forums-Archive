---
title: "firewall restrictions by application??"
date: 2008-05-20
forum: Security
---

### Post by nutpants on 2008-05-20
how do i block or allow network access by application or process?

im a newbie going from windows and useing the pop up firewalls there
(kerio personal firewall,commodo,ect) where i allowed or blocked access to the internet by application either as a rule or on a time by time situation.
i want to allow all access for my torrent app
but block access for game one
and allow for game 2
allow for wine app 1
block for wine app 2
etc

some games or applications i want to always or never to have internet access and some i want to decide each time they ask

there is more and more software being made to check for updates or report use statistics.

i know its MUCH more wide spread in windows

but i expect it happens in linux also..

i would like to know whats going on without having to be a master of iptables.

firestarter and kmyfirewall are good but offer no popup notices
for a newbie popup alerts are one of the best ways to provide notice and to give the option to allow or deny..

but i can find nothing for linux that has such ease of use.

and almost every firewall faq i can find is 3 years old and are "how to set up iptables"

nutz

---

### Post by Paqman on 2008-05-26
> **nutpants said:**
> 
there is more and more software being made to check for updates or report use statistics.

i know its MUCH more wide spread in windows

but i expect it happens in linux also..


Generally not. Individual aps don't phone home for updates. All of that is handled by the package manager, which you're probably most familiar with through Synaptic. If you don't want an ap to update, you can lock it's version in Synaptic. However, there's no security risk in allowing them to update, since the package manager always only connects to the same repos to check for updates. Since the repos are a trusted source, it's not a problem.

Which leads in to your second question: aps silently phoning home with stats or other info. This is spyware, and _none_ of the software you'll find in the repos is spyware. One of the benefits of the software being open source is that any user with the right knowhow can get under the hood and examine the program's behaviour. Any package which was secretly spying on you would be loudly and widely condemned, before being shunned and probably dropped from all the repos. Any stats which are sent to third parties (such as those sent by "popularity-contest") are all opt-in. Nothing is being sent out unless you specifically agree to it.

So no, there isn't a firewall package that provides popup alerts. The reason someone hasn't ever written one is because there's not really much to be paranoid about.

---

### Post by nutpants on 2008-05-26
what can i say im still new to Linux and have a healthy paranoia..

i like knowing who and what is connecting to the internet.
i will be using wine a lot until someone writes software to make it unnecessary to use wine.
not to mention most every major game is commercial.

as linux becomes more popular (AND IT IS) 
more people will be creating software for it
and more mays to abuse it.

as much as i dislike the vulnerabilitys of windows 
it was the major advertisers that abused those vulnerabilitys
that created my paranoia and drove me to Linux.

i expect when they see a fat profit in linux they will be here.

nutz

---

### Post by Paqman on 2008-05-27
Well, if Linux market share continues to grow, we'll see change for sure.

I do think the repository system and the open source software will continue to protect us from a lot of the problems you see on Windows. Our system really is better, IMO. Downloading and installing closed software from mysterious third parties is just asking for spyware problems, when you think about it.

As it is, you could leave Firestarter open all the time, or I guess you could use Conky to show the connections in real time on your desktop. There's probably a dozen other ways to achieve what you want, too.

---

### Post by master5o1 on 2008-05-27
> As it is, you could leave Firestarter open all the time, or I guess you could use Conky to show the connections in real time on your desktop. There's probably a dozen other ways to achieve what you want, too.

Isn't Firestarter just a GUI for iptables?
ie. You configure Firestarter (which configures iptables) and then close it?

---

### Post by kpkeerthi on 2008-05-27
> **master5o1 said:**
> Isn't Firestarter just a GUI for iptables?
ie. You configure Firestarter (which configures iptables) and then close it?

Yes. You are absolutely right.

---

### Post by nutpants on 2008-05-27
i really like the repository system.
but sadly it is not an incentive to have the wide variety of software that is found for windows.
if i ever won the lotto i would invest half into funding a opensource project to create software in linux i use now need wine for...

but until that day i have to pay 100$ here and 50$ there to get what i need to make my computer as useful as i want (ie memory map, ozi explorer,gloabal mapper,windows pocket pc software, and games).

as as more and more people come to linux and ubuntu
wine will be used more and more until there is native software to full the gaps.

and emulating a insecure spy ware and virus ridden nightmare with out the style of firewalls built to protect those holes makes me feel unsafe.

just about everything in windows phones home for one reason or another.
it is pretty much standard practice. adobe,real player,media players,web browsers, work processors, contact managers,  EVERYTHING phones home in windows. and when these companys start porting their software over it will phone home in linux.

as much as i wish i could live on  open source software alone. i cant.
70% of windows user cannot.
not yet.

i just hope the open source community will be ready to protect the flood of users coming soon.
we all know the big company's will not protect us from them.

firestarter is a good start i can use it some what.
i wish i could use the main windows "active connections" to allow or block applications going in or out.

nutz

---

### Post by dreamer84 on 2008-11-02
nutpants, I totally agree with your opinion, did you find something to suit your needs by now?

I don't understand part of the communities replies, on the one hand they say "oh, you don't need an additional firewall, everything in the repositories is tested and absolutely safe" etc, but on the other hand it's "no, do not deactivate your passwords, do not use root account". ugh. very contradictoire IMHO... (hey, anyone able to reach my pc physically can just as well steal my HDD and have a nice day with it without needing to crack that useless su password)

so, what I actually wanted to say:
there are enough programs NOT in the repos I still want to test and anyway if I'm othertimes recommended to be paranoid, why not also on some program's behaviour when internet is potentially available for them?

I don't now if maybe guarddog or smoothwall offer an application-based acces-controll, but I'll probably test them soon...

---

### Post by nutpants on 2008-11-02
no i have not found what i was looking for yet.
there is a new firewall to me that i just saw..

and then lost.. something like gfw
gnome firewall.. or something like that..

i reinstalled with 810 and forgot to backup my new bookmarks.
DOH!

and yes 99.9% of software from the repos are safe.
and 99.9% of the time you dont need a fire wall
 but then i run wine.
and test as many apps as i can get to work that dont have a  free linux equivalent. 
and that is just not safe.

and sooner or later there will be some smart windows guy that will start dumping free adware and spyware for linux. and newbies will use it not knowing that linux is no better than windows for stopping outgoing unwanted communication.

nutz

---

### Post by Steve1961 on 2008-11-02
You could always give Guarddog a try.  It gives you finer-grained control over what your pc can access from the internet and what other computers can access from your PC.  It's a KDE application but it works fine in Gnome, just remember to launch it with sudo.  Once you've configured it, it creates an rc.firewall script so you don't need the programme to be always running.  It also uses 'zones'.  The internet zone refers to the services your computer can access from the internet, the local zone is your computer, and defines what services other computers can access from your PC.  You can also create additional zones for, e.g. your lan, a dmz, etc.

It's in the repositories, but before you install it do a search for how to's, e.g. the manual is [here]("http://www.simonzone.com/software/guarddog/manual2/index.html").  This is important because by default Guarddog won't let anything in or out of your computer - you can't even surf the web until you've allowed access to http and dns.

It takes a bit of getting used to, but I now use it on all my machines.  here's a quick how to to get you started:

[http://newbiedoc.berlios.de/wiki/Setting_up_a_personal_firewall_on_Debian_using_Guarddog](http://newbiedoc.berlios.de/wiki/Setting_up_a_personal_firewall_on_Debian_using_Guarddog)

---

### Post by coldcoffee on 2008-11-02
I find just the opposite. Linux seems to have more applications than Windows if you ask me. Canonical repositories has over 40,000 packages alone. I think the biggest problem is just learning to use the Linux based applications after using Windows for so long. I have been using Linux for about a year and to me it is worth having to learn some things.

Seems gimp is one of the hardest to adjust to if you like using that type of application. And gaming is another big issue. Linux does have quite bit of good games though. And the more people start using it, the more game programmers will take notice and start to program games that run natively in Linux.

Also, did you know that in Synaptic Package Manager you can search using terms to find a particular type of application and it will give you results you can look through related to your search?

Also, for your Google searching needs you can use [http://www.google.com/linux](http://www.google.com/linux) and you will get only Linux related search results. Stick with it and ask questions. I find the Linux community is amazing when it comes to support. People are so willing to help when you ask for it.

I recommend checking out some Linux related podcasts too. Some good ones are: [http://goinglinux.com/index.html](http://goinglinux.com/index.html) [http://www.linuxreality.com/](http://www.linuxreality.com/) [http://www.linuxbasement.com/](http://www.linuxbasement.com/)

Edit: > as linux becomes more popular (AND IT IS)
more people will be creating software for it
and more mays to abuse it.

You can rest assured anything you download from Canonical repositories is going to be virus, spyware, adware and malware free. Ubuntu would not provide you with software that is harmful in such ways. Most applications you will find outside of Ubuntus repositories will be safe too. If you are ever in doubt though, then don't download software from a source you don't trust. You can trust software in Canonical repositories though. Ubuntu/Canonical is in complete control of all software in there, and they would not allow harmful software. Their reputation depends on that.

---

### Post by Paqman on 2008-11-02
> **nutpants said:**
> no i have not found what i was looking for yet.
there is a new firewall to me that i just saw..

and then lost.. something like gfw
gnome firewall.. or something like that..


That would be gufw.

Ufw (Uncomplicated FireWall) is a nice straightforward front end for iptables that Ubuntu introduced a little while ago to make setting up iptables on servers easier. It's a command-line tool.

Gufw is a nice GUI front end someone has whipped up to make ufw practical for desktops. I'd definitely recommend it over Firestarter now, since development of Firestarter has ceased.

---

### Post by bodhi.zazen on 2008-11-02
The firewall for Linux is iptables.

The "prefered" application to configure your firewall is UFW. If you wish to use a gui tool try GUFW (it is in the intrepid repos).

If you wish to learn about Ubuntu security I suggest :

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

The idea that as Linux becomes more popular it will be a bigger target is, IMO, FUD. Unix and Linux have been in existence for quite some time and are designed from the ground up to be multi user and more secure.

With the modern internet and cracking tools, Security through obscurity is no security at all.

In addition some of the biggest "targets" on the internet are Unix and Linux servers.

Crackers take advantage of holes in the code. Unlike some OS, security updates occur on a regular basis in Linux. On the other hand, Microsoft has not fixed known holes / vulnerabilities in their code for decades.

Windows is more vulnerable due to poor code, not popularity.

---

### Post by kevdog on 2008-11-02
iptables doesn't filter by application name, rather than by port.  Just an FYI.  Often certain protocols/programs run over certain default ports, however these defaults can be changed.

After learning more about things, I would also agree with Bodhi that ufw is the preferred way to configure iptables in ubuntu.  Firestarter has an exceptional gui, however has been unmaintained for a long time.

---

### Post by cariboo on 2008-11-02
One other thing you have to remember about Linux is that the only place you as a user can install anything is in your home directory, to install any application you have to be root. No root user, no program installation. 

The other thing, is that the only way an application can acess the network, is if you specifically allow it to. Applications don't have access to the network like they do in Windows. If you stick to installing programs from the repositories, you will never have a problem with malware.

Jim

---

### Post by q.dinar on 2009-01-18
it would be possible if you can run programs with different "user"s.
see [http://danieldegraaf.afraid.org/info/iptables/outfilter](http://danieldegraaf.afraid.org/info/iptables/outfilter)
and/or [http://ubuntuforums.org/showpost.php?p=6571681&postcount=25](http://ubuntuforums.org/showpost.php?p=6571681&postcount=25) .


28th of january:

[http://ubuntuforums.org/showpost.php?p=6617395&postcount=5](http://ubuntuforums.org/showpost.php?p=6617395&postcount=5) :
[QUOTE=jgoguen]You could instead use iptables to handle this, using the parameters -m owner --cmd-owner <name>. The --cmd-owner parameter accepts a program name, and the iptables rule will match packets coming from a program matching that name.[/QUOTE]

---

