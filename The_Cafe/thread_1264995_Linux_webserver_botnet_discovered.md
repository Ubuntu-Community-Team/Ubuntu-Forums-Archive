---
title: "Linux webserver botnet discovered"
date: 2009-09-12
forum: The Cafe
---

### Post by Sporkman on 2009-09-12
> The Register writes up a Russian security researcher who has uncovered a Linux webserver botnet that is coordinating with a more conventional home-based botnet of Windows machines to distribute malware.
[QUOTE]"Each of the infected machines examined so far is a dedicated or virtual dedicated server running a legitimate website, Denis Sinegubko, an independent researcher based in Magnitogorsk, Russia, told The Register. But in addition to running an Apache webserver to dish up benign content, they've also been hacked to run a second webserver known as nginx, which serves malware [on port 8080]. 'What we see here is a long awaited botnet of zombie web servers! A group of interconnected infected web servers with [a] common control center involved in malware distribution,' Sinegubko wrote. 'To make things more complex, this botnet of web servers is connected with the botnet of infected home computer(s).'"[/QUOTE]

[http://linux.slashdot.org/story/09/09/12/1413246/First-Botnet-of-Linux-Web-Servers-Discovered](http://linux.slashdot.org/story/09/09/12/1413246/First-Botnet-of-Linux-Web-Servers-Discovered)

Source: [http://blog.unmaskparasites.com/2009/09/11/dynamic-dns-and-botnet-of-zombie-web-servers/](http://blog.unmaskparasites.com/2009/09/11/dynamic-dns-and-botnet-of-zombie-web-servers/)

---

### Post by Ms_Angel_D on 2009-09-12
Well hopefully they can figure out a way to solve this.

---

### Post by SunnyRabbiera on 2009-09-12
> **Ms_Angel_D said:**
> Well hopefully they can figure out a way to solve this.

Give them a few seconds :D

---

### Post by Ms_Angel_D on 2009-09-12
> **SunnyRabbiera said:**
> Give them a few seconds :D

lol no doubt

---

### Post by JillSwift on 2009-09-12
This is fascinating. I hope they discover how these boogers were installed.

I speculate it's social engineering.

---

### Post by stwschool on 2009-09-12
Another article I read on the topic suggests password sniffing, which to me hints at insecure admin practices such as using root passwords on plain-text protocols.

---

### Post by kpholmes on 2009-09-12
wow, really surprising. so would a patch be released from apache?

---

### Post by 3rdalbum on 2009-09-12
Ironically, it looks like the servers' SSH/web-based-administration passwords were sniffed by malware running on Windows machines, that the server admins were using to log in remotely. Then those machines were manually rooted.

---

### Post by 3rdalbum on 2009-09-12
> **stwschool said:**
> Another article I read on the topic suggests password sniffing, which to me hints at insecure admin practices such as using root passwords on plain-text protocols.

Or other such "insecure admin practices" as using a Windows machine to log into a Linux machine :-P

> wow, really surprising. so would a patch be released from apache?

So far there's nothing to suggest that Apache was the method of entry. If burglars gain entry to your home by throwing a brick through your window, then putting bigger locks on the doors will not prevent it happening again.

---

### Post by JillSwift on 2009-09-12
> **stwschool said:**
> Another article I read on the topic suggests password sniffing, which to me hints at insecure admin practices such as using root passwords on plain-text protocols.

D'oh!   #-o

---

### Post by Rainstride on 2009-09-12
probably just a bunch of people running as root non-stop.

---

### Post by kpholmes on 2009-09-12
> **3rdalbum said:**
> Or other such "insecure admin practices" as using a Windows machine to log into a Linux machine :-P

haha

So far there's nothing to suggest that Apache was the method of entry. If burglars gain entry to your home by throwing a brick through your window, then putting bigger locks on the doors will not prevent it happening again.

ya that makes sense. i didnt see the part of where they got the root passwords from a windows machine.

---

### Post by Rainstride on 2009-09-12
> **3rdalbum said:**
> Ironically, it looks like the servers' SSH/web-based-administration passwords were sniffed by malware running on Windows machines, that the server admins were using to log in remotely. Then those machines were manually rooted.

](*,) (sigh....)

---

### Post by MaxIBoy on 2009-09-12
Microsoft charging windmill at full tilt in 3, 2, 1....

---

### Post by stwschool on 2009-09-13
> **3rdalbum said:**
> Ironically, it looks like the servers' SSH/web-based-administration passwords were sniffed by malware running on Windows machines, that the server admins were using to log in remotely. Then those machines were manually rooted.
Ah that makes a bit more sense then. So nothing to patch really, just don't do secure stuff from Windows!

---

### Post by samjh on 2009-09-13
> **3rdalbum said:**
> Ironically, it looks like the servers' SSH/web-based-administration passwords were sniffed by malware running on Windows machines, that the server admins were using to log in remotely. Then those machines were manually rooted.

Do you have a source?  I couldn't find any mention of that in the [original blog post]("http://blog.unmaskparasites.com/2009/09/11/dynamic-dns-and-botnet-of-zombie-web-servers/").

---

### Post by sim-value on 2009-09-13
GO Evil Botnet GO !!!!!

*scnr*

---

### Post by hessiess on 2009-09-13
> which serves malware [on port 8080]

Assuming they wern't using it, why even have port 8080 open, A hardwere firewall would solve that problem as it would be in effected by the computer behind it getting comprised.

---

### Post by gn2 on 2009-09-13
> **3rdalbum said:**
> ~ If burglars gain entry to your home by throwing a brick through your window, then putting bigger locks on the doors will not prevent it happening again.

Sounds like a very compelling reason for getting rid of windows altogether......

---

### Post by etnlIcarus on 2009-09-13
> **JillSwift said:**
> I speculate it's social engineering.

Does the phrase carry some other IT-related connotation I'm not aware of?

---

### Post by Old Marcus on 2009-09-13
I am truly surprised that people on site like the Register haven't gone screaming blue murder about how 'insecure' Apache and Linux is.

Social Engineering in this sense would be tricking idiots into doing something that will allow the malware entry.

---

### Post by dmizer on 2009-09-13
> **samjh said:**
> Do you have a source?  I couldn't find any mention of that in the [original blog post]("http://blog.unmaskparasites.com/2009/09/11/dynamic-dns-and-botnet-of-zombie-web-servers/").

A link to the source article (which discusses the possible SSH attack) is now included in the original post.

> **3rdalbum said:**
> Or other such "insecure admin practices" as using a Windows machine to log into a Linux machine :-P
This is probably not the case. In many cases, it would be easier to hack into poorly secured machines directly. I see ambitious new Linux users constantly making mistakes which would expose them to this. Things like trying to use a remote desktop protocol over the internet, or using weak password authenticated SSH.

---

### Post by samjh on 2009-09-13
> **dmizer said:**
> A link to the source article (which discusses the possible SSH attack) is now included in the original post.
That was the blog post I was talking about.  But there is no mention that in this particular situation, a compromised Windows machine was used to remote-access the affected server(s).  I know that one of the comments mention finding spyware on Windows machines, but there is no evidence to suggest that the discovery is related to the particular botnet the blog poster is talking about. :confused:

---

### Post by dmizer on 2009-09-14
> **samjh said:**
> That was the blog post I was talking about.  But there is no mention that in this particular situation, a compromised Windows machine was used to remote-access the affected server(s).  I know that one of the comments mention finding spyware on Windows machines, but there is no evidence to suggest that the discovery is related to the particular botnet the blog poster is talking about. :confused:

Here's an article which speculates that the inroad is weak password authenticated SSH: [http://www.theregister.co.uk/2009/09/12/linux_zombies_push_malware/](http://www.theregister.co.uk/2009/09/12/linux_zombies_push_malware/)

The "Windows angle" originated here, and is highly unlikely.

---

### Post by juancarlospaco on 2009-09-14
[http://toolbar.netcraft.com/site_report?url=www.applesfera.com]("http://toolbar.netcraft.com/site_report?url=www.applesfera.com")

Web Server Linux nginx/0.7.61 nginx/0.7.17 Apache/2.0.54 Debian GNU/Linux



Windows7Sins.org got these software too, but it seems its Zope, not malware:

[http://toolbar.netcraft.com/site_report?url=windows7sins.org]("http://toolbar.netcraft.com/site_report?url=windows7sins.org")

This is the Malware???, zope is Malware?:

[http://windows7sins.org:8080/]("http://windows7sins.org:8080/")

:)

---

### Post by juancarlospaco on 2009-09-15
*I want a response so...*
**[COLOR="Blue"]Bump[/COLOR]** :)

-Zope is Malware or the notice is Fake???

---

### Post by koenn on 2009-09-15
> **juancarlospaco said:**
> [http://toolbar.netcraft.com/site_report?url=www.applesfera.com]("http://toolbar.netcraft.com/site_report?url=www.applesfera.com")

Web Server Linux nginx/0.7.61 nginx/0.7.17 Apache/2.0.54 Debian GNU/Linux


Windows7Sins.org got these software too, but it seems its Zope, not malware:

[http://toolbar.netcraft.com/site_report?url=windows7sins.org]("http://toolbar.netcraft.com/site_report?url=windows7sins.org")

This is the Malware???, zope is Malware?:

[http://windows7sins.org:8080/]("http://windows7sins.org:8080/")

:)

nginx is a perfectly legit web server. There's no reason for sites not to use it.

port 8080 is a tcp port just like any other tcp port. If someone wants to have a zope login there is no problem whatseover.

all of the above has nothing to do with the fact that the botnet config using nginx on port 8080 seems very plausible, but it would be equally plausible if it was implemented with lighttpd on port 7331


a little knowledge is a dangerous thing.

---

### Post by aesis05401 on 2009-09-16
> **etnlIcarus said:**
> Does the phrase carry some other IT-related connotation I'm not aware of?

Social Engineering?  It is not an IT term, it is a human nature concept.  You know, like when a one-handed man distracts you with one hand while picking your pocket with the other hand that he doesn't have because he is a one-handed man.  Make sense? :)

---

### Post by juancarlospaco on 2009-09-16
I don't understand, can anyone post the link of the malware...?
*i checked a lot of them and usually dont works on the current Ubuntu, only lies...*

---

### Post by physeetcosmo on 2009-09-16
> **Sporkman said:**
> [http://linux.slashdot.org/story/09/09/12/1413246/First-Botnet-of-Linux-Web-Servers-Discovered](http://linux.slashdot.org/story/09/09/12/1413246/First-Botnet-of-Linux-Web-Servers-Discovered)

Source: [http://blog.unmaskparasites.com/2009/09/11/dynamic-dns-and-botnet-of-zombie-web-servers/](http://blog.unmaskparasites.com/2009/09/11/dynamic-dns-and-botnet-of-zombie-web-servers/)

Does anyone know if this is related to the conficker worm? This worm had a SPAM distribution of some kind and ran a botnet.

Even though malware is destructive it is fascinating to see what people can do with code.

---

### Post by koenn on 2009-09-16
> **juancarlospaco said:**
> I don't understand, can anyone post the link of the malware...?
*i checked a lot of them and usually dont works on the current Ubuntu, only lies...*
check the website (link in this thread) of the guy who discovered the botnet. I don't remember if he actually posted botnet member servers, but you can ask.

---

### Post by juancarlospaco on 2009-09-16
It dont work,
*i clicked, downloaded, executed every link here and dont work at all.*

:)

---

### Post by koenn on 2009-09-16
you actually found a link to a zombie web server there ? All I see is links to articles and source documentation.

Besides, the zombies are linux web servers, the malware targets are (presumably) windows systems. What are you running ?

---

### Post by juancarlospaco on 2009-09-16
Ubuntu i run.
*Windows doesnt care at all.*

---

