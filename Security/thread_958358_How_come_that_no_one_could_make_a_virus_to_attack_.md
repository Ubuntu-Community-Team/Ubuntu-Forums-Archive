---
title: "How come that no one could make a virus to attack linux OS?"
date: 2008-10-25
forum: Security
---

### Post by LastWho on 2008-10-25
hi,
Isn't it amazing to know that absolutely "No virus" in the WWW is made to attack linux?!!! 

can you please give us some explanations? or articles to read that explains why?
thanks

---

### Post by Duck2006 on 2008-10-25
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)
[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

---

### Post by BDNiner on 2008-10-25
There are viruses made to attack linux, it would however take some misuse ton the users side for the virus to be effective. ie they would have to run a script or program and give that program admin rights on the computer.

Also since there are a lot less linux users than windows or mac users then there is no incentive to write a virus for linux. once the numbers of linux users increases then more and more malicious programs will be written to try and damage linux computers.

---

### Post by bpowell2005 on 2008-10-25
> **LastWho said:**
> hi,
Isn't it amazing to know that absolutely "No virus" in the WWW is made to attack linux?!!! 

can you please give us some explanations? or articles to read that explains why?
thanks

I'm not sure that's entirely true. I think there are several viruses out there that are Linux specific...however, the MAJORITY of viruses out there target Windows systems, because the MAJORITY of computers out there are running Windows. It's logical to assume as the Linux desktop environment grows, and more people start using Linux, the malware writers will shift their efforts towards Linux. However, the best return on investment for the moment is coding towards Windows. IMHO.

---

### Post by igknighted on 2008-10-25
They could, it just isn't worth anyone's time because there would be so few computers for it to attack.  And the increased security (ie, only root can edit system files) makes it more difficult.

For example, if I built a .deb file that only contained a script that ran the command 'sudo rm -rf /', and put it on my website offering it as an application to increase OO.o's compatibility with MS Office, then people might download and install it and my 'virus' would ruin their install.

So it is possible, and the example I gave above is one reason why you should always install from the official repo's unless you really know the source of the packages.

EDIT: if you are bored and want to have fun, try running windows viruses via wine.  I don't recommend doing this on your production system, as I believe some of them actually succeeded.

---

### Post by bpowell2005 on 2008-10-25
> **igknighted said:**
> They could, it just isn't worth anyone's time because there would be so few computers for it to attack.  And the increased security (ie, only root can edit system files) makes it more difficult.

For example, if I built a .deb file that only contained a script that ran the command 'sudo rm -rf /', and put it on my website offering it as an application to increase OO.o's compatibility with MS Office, then people might download and install it and my 'virus' would ruin their install.

So it is possible, and the example I gave above is one reason why you should always install from the official repo's unless you really know the source of the packages.

Great point....installing from the repo's reduces your risk of infection considerably.

Even though there aren't many folks targeting Linux yet, I wouldn't take that as a reason to let the guard down. My computers are all safely behind the routers firewall, I have no ports open that don't need to be, and I run AV on all the computers at home (even the Linux ones).

I've never used the fire extinguisher in my kitchen, but that doesn't mean I don't need it. If you know what I'm sayin! :)

---

### Post by Bucky Ball on 2008-10-25
Apparently someone in the UK slapped some serious money on the counter about 10 years ago for someone to write a bug/virus that could do just this. The money is still sitting on the counter. True story. One of the more experienced heads can probably fill in the details.

Here ya go:

[http://linux.slashdot.org/article.pl?sid=01/10/13/1346243&mode=thread](http://linux.slashdot.org/article.pl?sid=01/10/13/1346243&mode=thread)

Please note that date - 2001, so 7 years and the money is still sitting there.

---

### Post by Bucky Ball on 2008-10-25
> **bpowell2005 said:**
> 
I've never used the fire extinguisher in my kitchen, but that doesn't mean I don't need it. If you know what I'm sayin! :)

I would consider that excellent advice. The other thing to remember is Linux kinda = Unix which was originally used for rock solid security networks and is still used by government, military, institutions etc. Their first concern was security unlike MS. :)

---

### Post by twisted_steel on 2008-10-25
Here's a Symentec page with an overview of a worm that was used to infect Red Hat 6.2 and 7.0 boxes in 2001:

[Ramen worm]("http://www.symantec.com/security_response/writeup.jsp?docid=2001-011713-2000-99&tabid=2")

---

### Post by Bucky Ball on 2008-10-25
> **twisted_steel said:**
> Here's an old worm that was used to infect Red Hat 6.2 and 7.0 boxes in 2001:

[Ramen worm]("http://www.symantec.com/security_response/writeup.jsp?docid=2001-011713-2000-99&tabid=2")

Everyone's gonna click on that twisted_steel! lol

One thing to consider: if you are sharing a network with Windoze machines, the Windoze viruses/bugs will pass straight through if you follow me. Not detected in Ubuntu but if a file has a windoze bug, that will wind up on the windoze machine you are communicating with. That is about the only reason you might want to run a virus checker/program or whatever.

---

### Post by bodhi.zazen on 2008-10-25
It is possible to write a virus for Linux.

The issues are that security is tighter on Linux so it is more difficult. 

Also, viruses take advantage of holes in the code, so in open source updates or fixes aer available much much faster then on say Windows. Windows is vulnerable to viruses and worms that have been know for years and years, Microsoft has yet to patch the code.

with open source, once known holes are often patched within days of their discovery. The known Linux viruses, for example, are long patched.

See these links for Linux security :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

[[all variants] Intrusion Detection - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=919472")

---

### Post by twisted_steel on 2008-10-25
> **Bucky Ball said:**
> Everyone's gonna click on that twisted_steel! lol

It's a Symantec page about the worm :p

---

### Post by Dr Small on 2008-10-25
I've writen a proof-of-concept trojan before that actually works, but one must manually run it for it to create the trojan. With a little social-engineering, you can get someone to run it, but it's not worth my time to ruin other peoples computers.

---

### Post by jerome1232 on 2008-10-25
> **igknighted said:**
> 
For example, if I built a .deb file that only contained a script that ran the command 'sudo rm -rf /', and put it on my website offering it as an application to increase OO.o's compatibility with MS Office, then people might download and install it and my 'virus' would ruin their install.

Sorry but that's just malware, (which is probably what the OP probably meant anyways) in order for it to be a virus it must try and spread to other machines. 

That Linux.Ramen.Worm is actually kind of funny. Serves an html page that says hackers loooooooove noodles...

Honestly security mostly relies on the user to not fall for social engineering imho. There's nothing an OS can do with an uninformed admin clicking on everything they can install.

---

### Post by brian_p on 2008-10-25
> **LastWho said:**
> hi,
Isn't it amazing to know that absolutely "No virus" in the WWW is made to attack linux?!!!

I suspect you mean 'malware' (code which may potentially  harm your machine), not 'virus' (self-replicating code which can spread to other machines).

> can you please give us some explanations? or articles to read that explains why?
thanks

You will want examine the differences between a virus, a trojan and a worm.

Virus: Impossible to have working on a linux system.
Trojan: Relies on being executed by a user. Impossible for any operating system to guard against.
Worm: Attacks a service. Linux is not impervious. Defend against by keeping up-to-date with software.

---

### Post by Dr Small on 2008-10-25
> **brian_p said:**
> Virus: Impossible to have working on a linux system.
Trojan: Relies on being executed by a user. Impossible for any operating system to guard against.
Worm: Attacks a service. Linux is not impervious. Defend against by keeping up-to-date with software.

+1 for the excellent definitions.

---

### Post by bodhi.zazen on 2008-10-25
As long as we are talking social engineering, I am surprised on one posted this link yet:

[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

Although it is a joke, it does give new users a glimpse of how difficult it is to install malware on Linux.

---

### Post by nubdora on 2008-10-25
> **bodhi.zazen said:**
>  Windows is vulnerable to viruses and worms that have been know for years and years, Microsoft has yet to patch the code.


They can't without re-writing the OS. MS was always a one-privilege system until recent times and there are too many integrated dependencies relying on admin privileges and the kernel. If it weren't for the average user, proprietary dependencies, Microsoft's domination on the market because Bill is a businessman, not a great programmer, and Microsoft's luck in the 80s, derived from Corporate need to supply employees with easy-to-use computing for increased work productivity and efficiency, before security became such a hot topic, the name Microsoft would mean nothing. MS might have more vulnerabilities fixed in 2121. 

-1 to MS

---

### Post by LastWho on 2008-10-25
> **igknighted said:**
> They could, it just isn't worth anyone's time because there would be so few computers for it to attack.  And the increased security (ie, only root can edit system files) makes it more difficult.

For example, if I built a .deb file that only contained a script that ran the command 'sudo rm -rf /', and put it on my website offering it as an application to increase OO.o's compatibility with MS Office, then people might download and install it and my 'virus' would ruin their install.

i secured "rm" in my .bashrc file:
```
sudo nano .bashrc
#and i added after 
#some more ls aliases:
alias rm='rm --preserve-root'

```
does that make me safer?

and thank you for all the explanations you gave me follows :popcorn:

---

### Post by jerome1232 on 2008-10-25
I don't see how it would. If you look at the man page for rm it's already default behavior. Or am I missreading this.

```
       --no-preserve-root
              do not treat &#8216;/&#8217; specially

       --preserve-root
              do not remove &#8216;/&#8217; (default)
```

---

### Post by jordilin on 2008-10-25
> **bodhi.zazen said:**
> As long as we are talking social engineering, I am surprised on one posted this link yet:

[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

Although it is a joke, it does give new users a glimpse of how difficult it is to install malware on Linux.
That joke is incredibly funny. With this link, I'm gonna sleep with a huge smile, haha

---

### Post by HermanAB on 2008-10-25
There are some malware for Linux.  I fix one or two hosed web servers per year.  Usually the problem is due to some dumkopf who thought that a 4 character password would be 'cool'.

So, the most important thing is to use long passwords in excess of 8 characters (since common password dictionaries go up to 8 characters).

---

### Post by jordilin on 2008-10-25
> **ghodkiller said:**
> no one bothers to make a virus for linux. linux is fairly used especially by home users. and if you have linux, you must be well over average in computer knowledge.

Well, Linux is used in many servers in many companies as well...and it is not just a Desktop operating system.

---

### Post by LastWho on 2008-10-25
> **jerome1232 said:**
> I don't see how it would. If you look at the man page for rm it's already default behavior. Or am I missreading this.

```
       --no-preserve-root
              do not treat ‘/’ specially

       --preserve-root
              do not remove ‘/’ (default)
```
didn't know it was set by default :p cuz i'd never try the **[COLOR="Red"]Do Not Try This[/COLOR]**: [SIZE="1"]rm -rf /*[/SIZE] (**[COLOR="Red"]Do Not Try This[/COLOR]**) before, of course, because of all the "do not try this" lol

[QUOTE=jordilin]That joke is incredibly funny. With this link, I'm gonna sleep with a huge smile, haha [/QUOTE]
very funny indeed thank you bodhi.zazen :lolflag:

---

### Post by bodhi.zazen on 2008-10-26
Just for clarification (as it has been discussed)

[color=green]rm -rf / # This command will do nothing but give an error message[/color]

But this command will hose your system :

[color=red]rm -rf /* # This command will remove everything but /[/color]

Well, it will stop a bit shy of everything, The difference is 

/ != /*, the * will remove /bin (etc).

The only "safe" environment to test this is when running from a live CD WITHOUT ANY PARTITIONS MOUNTED

---

### Post by hyper_ch on 2008-10-27
> **BDNiner said:**
> Also since there are a lot less linux users than windows or mac users then there is no incentive to write a virus for linux. once the numbers of linux users increases then more and more malicious programs will be written to try and damage linux computers.
> **bpowell2005 said:**
> however, the MAJORITY of viruses out there target Windows systems, because the MAJORITY of computers out there are running Windows. It's logical to assume as the Linux desktop environment grows, and more people start using Linux, the malware writers will shift their efforts towards Linux. However, the best return on investment for the moment is coding towards Windows. IMHO.
> **igknighted said:**
> They could, it just isn't worth anyone's time because there would be so few computers for it to attack.

The number of base installs does not correlate with the number of attacks on any targetted system. This is a common misconception.

As said by bpowell2005, the ROI is the driving force (except if you do something based on your principles). Having an equal amount of linux systems and microsoft system, which one will be attacked more? Very likely the one with worse security (e.g. running constantly as admin...). Now if you shift the balance to 60% linux and 40% windows. Which will it then be? Where do you get the better ROI? Hard to tell, I still think it's windows because if you can manage just just own one process, you can normally own the whole machine. Linux, as a true multi-user system, makes it a lot harder. How aboout 70% to 30%? 80% to 20%? It's hard to tell.

Fact is, that apache is the most deployed websever yet it significantly gets less attacked than IIS. If you just consider the number of base installs then it should be apache that's on the top list there ;)

---

